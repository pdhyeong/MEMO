# API 문서

# [USER]

### POST [http://15.165.204.25:5050/](http://15.165.204.25:5050/)[user/enroll/?wallet=](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑){wallet}

- 지갑 등록 API
- 응답 예시

```json
{
	"status": "success",
	"name": "이름",
	"faucet": true / false,
	"cnt": "튜토리얼 단계"
}
```

### PUT [http://15.165.204.25:5050/user/chname/?wallet=](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑){wallet}

- request.body

```json
{
	"name": "변경하고 싶은 이름"
}
```

- 이름 수정 API
- 수정하려는 이름으로 DB를 수정한다.
- 응답 예시

```json
{
	"status": "success",
	"name": "변경하고 싶은 이름"
}
```

### PUT [http://15.165.204.25:5050/user/faucet/?wallet=](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑){wallet}

- FAUCET 제공 API
- 50 ETH를 딱 한 번 제공하고, 한 번 제공받으면 DB에 받은 내역을 bool 값으로 저장한다.
- 응답 예시

```json
{
	"status": "success",
}
```

### GET [http://15.165.204.25:5050/user/position/?wallet=](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑){wallet}&offset={offset}&limit={limit}

- 특정 지갑 주소에 대한 거래내역 일부를 제공하는 API
- 페이지네이션 범위에 해당하는 모든 데이터를 전송한다.
- 응답 예시

```json
[
{
	”id”: “인덱스”
	”user_wallet” : "투자자 지갑 주소”,
	”order”: ”구매/판매/배당금”,
	”price”: ”토큰 1개당 가격”,
	”amount”: ”거래량”,
	”fee”: ”수수료”,
	”createdAt”: ”저장날짜”,
	”updatedAt”: ”수정날짜”
},
{
	”id”: “인덱스”
	”user_wallet” : "투자자 지갑 주소”,
	”order”: ”구매/판매/배당금”,
	”price”: ”토큰 1개당 가격”,
	”amount”: ”거래량”,
	”fee”: ”수수료”,
	”createdAt”: ”저장날짜”,
	”updatedAt”: ”수정날짜”
},
{}, {}, {} ...
]
```

### GET [http://15.165.204.25:5050/user/mypage/?wallet=](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑){wallet}

- 유저 정보 전송 API
- 응답 예시

```json
{
	"name": "이름",
	"faucet": true / false,
	"cnt": "튜토리얼 단계"
}
```

### GET [http://15.165.204.25:5050/user/personaldividend/?wallet=](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑){wallet}

- 특정 유저의 각 토큰 별 지급받은 배당금의 총액을 전송해주는 API
- 응답 예시

```json
{
	"ENTAToken": 0.017345496845033524,
	"BEBToken": 0.021847759090056067,
	"LEOToken": 0.0082385903847581
}
```

# [COMPANY]

### POST [http://15.165.204.25:5050/company/vote](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)

- 배당금 투표 API
- request.body

```json
{
	"name": "토큰 이름",
	"ratio": "선택한 배당률",
	"user_wallet": "투자자 지갑 주소"
}
```

- 투자자가 선정한 배당률 투표를 거래내역 테이블에 저장하고 그 값을 반환해준다.
- 응답 예시

```json
{
	"status": "success",
}
```

### GET [http://15.165.204.25:5050/company/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)pdisclosure/?name={name}

- 기업 공시 (기업 정보) 전송 API
- 토큰 이름을 쿼리로 추가하여 요청시 해당 토큰에 대한 기업의 정보를 클라이언트에게 전송해준다.
- 응답 예시

```json
{
	"name": "토큰 이름",
	"income": "최신 당기 순이익",
	"dividend_ratio": "최신 배당률",
	"dividend": "최신 배당금",
	"voted_ratio": "투표 결과 선정된 배당률 변동률"
}
```

# [CHART]

### GET [http://15.165.204.25:5050/c](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)hart/enta/?offset={offset}&limit={limit}

### GET [http://15.165.204.25:5050/c](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)hart/beb/?offset={offset}&limit={limit}

### GET [http://15.165.204.25:5050/c](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)hart/leo/?offset={offset}&limit={limit}

- 토큰 별(ENTA, BEB, LEO) 누적된 모든 가격변동 데이터 전송 API
- 모든 가격 데이터를 offset, limit에 기반한 페이지네이션 범위에 해당하는 모든 데이터를 전송한다.
- 응답 예시

```json
{
	"priceinfo": [
	  {
		  ”createdAt”: "10:30:38",
		  ”open”: 1.2,
		  ”close”:1.154394778075832,
		  ”high”:1.210819347780187,
		  ”low”:1.154394778075832,
		  ”totalVolTo”:123,
		  ”totalVolFrom”:123
	  },
	  {
		  ”createdAt”: "10:30:38",
		  ”open”: 1.2,
		  ”close”:1.154394778075832,
		  ”high”:1.210819347780187,
		  ”low”:1.154394778075832,
		  ”totalVolTo”:123,
		  ”totalVolFrom”:123
	  },
		{}, {}, {} ...
	],
	"totalLength": “총 데이터 개수”
}
```

# [TOKEN]

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)enta/buy

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)beb/buy

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)leo/buy

- request.body
    
    ```json
    {
     ”price”: ”토큰 가격”,
     ”amount”: ”토큰 개수”,
     ”wallet”: ”투자자 지갑”,
    }
    ```
    
- 토큰 구매 API
- 토큰을 구매할 경우 이더를 거래소에게 전송하고, 거래소는 해당 토큰을 투자자에게 전송해 준다. 이때 수수료는 포함한 이더 만큼 전송된다.
- 응답 예시
    
    ```json
    { "status": "success" }
    ```
    

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)enta/sell

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)beb/sell

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)leo/sell

- request.body
    
    ```json
    {
     ”price”: ”토큰 가격”,
     ”amount”: ”토큰 개수”,
     ”wallet”: ”투자자 지갑”,
    }
    ```
    
- 토큰 판매 API
- 토큰을 판매할 경우 토큰을 거래소에게 전송하고, 거래소는 해당 토큰에 가격에 대한 이더를 투자자에게 전송해준다. 이때 수수료를 제외한 이더만큼 전송된다.
- 응답 예시
    
    ```json
    { "status": "success" }
    ```
    

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)enta/staking

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)beb/staking

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)leo/staking

- request.body
    
    ```json
    {
    	"wallet": "유저 지갑 주소",
    	"price": "스테이킹 당시 토큰 가격",
    	"amount": "스테이킹 한 토큰 개수",
    	"txin": "스테이킹 실시한 트랜잭션의 해시값"
    }
    ```
    
- 스테이킹 내역 저장 API
- 스테이킹을 실시할 경우 해당 내용을 거래내역테이블(position_his)에 저장하여 투자자가 거래내역에서 내용을 확인할 수 있도록 한다.
- 응답 예시
    
    ```json
    { "status": "success" }
    ```
    

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)enta/reward

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)beb/reward

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)leo/reward

- request.body
    
    ```json
    {
    	"wallet": "유저 지갑 주소",
    	"price": "보상 당시 토큰 가격",
    	"amount": "보상 받은 토큰 총 개수",
    	"txout": "보상을 수행한 트랜잭션의 해시값"
    }
    ```
    
- 스테이킹 보상금 인출 내역 저장 API
- 스테이킹 보상을 수취할 경우 해당 내용을 거래내역테이블(position_his)에 저장하여 투자자가 거래내역에서 내용을 확인할 수 있도록 한다.
- 응답 예시
    
    ```json
    { "status": "success" }
    ```
    

# [RTD]

### GET [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)rtd/enta

### GET [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)rtd/beb

### GET [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)rtd/leo

- 실시간 토큰 가격 전송 API
- 1초마다 변동하는 토큰 가격에 대해서 클라이언트가 매 초에 변동된 가격 데이터를 요청하면 서버쪽에서 해당 가격 데이터를 전송해준다.
- 응답 예시
    
    ```json
    {
    	"chartDataENTA": {
    	  ”createdAt": "변동 날짜",
    	  ”open”: "시가",
    	  ”close”: "종가",
    	  ”high”: "고가",
    	  ”low”: "저가",
    	  ”totalVolTo”: "최소 누적 거래량",
    	  ”totalVolFrom”: "최대 누적 거래량",
    		"totalCurrentPrices": {
          "enta" : "",
          "beb" : "",
          "leo" : "",
      },
    	"restrictToggle": true
    }
    ```
    

### POST [http://15.165.204.25:5050/](http://43.201.113.177:5050/user/enroll/?wallet={투자자지갑)rtd/restrict

- 거래 제한 API
- 거래제한 버튼 클릭시 1초 마다 갱신되는 가격 변동이 1분간 중지되며, 모든 토큰의 거래가 제한되어 토큰 및 이더 전송이 제한된다.
- 응답 예시
    
    ```json
    { "status": "successfully restriced the token" }
    ```
