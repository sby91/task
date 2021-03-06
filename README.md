## 부동산 정보를 설계하고 조회, 생성, 수정 및 삭제하는 API를 작성합니다.

## 요구사항

- 한 주소에 원룸건물이 한개씩 존재한다고 가정합니다.
- 임대인은 여러개의 원룸건물을 소유할 수 있습니다.
- 이 건물은 여러개의 층이 있으며 각 층에는 3~4개의 방이 존재할 수 있습니다.
- 각 방은 여러가지의 가격을 가질 수 있습니다. 예컨대 303호는 (보증금1000, 월세40) 또는 (보증금 2000, 월세30)을 계약시에 선택할 수 있습니다. 월세는 0일수 있습니다. 가격은 보증금과 월세로 정렬이 가능해야 합니다. 보증금과 월세는 각각 deposit, monthly로 표현합니다.


## 참고사항
- 데이터베이스, 언어, 프레임워크 또는 에디터 설정등에 제약은 없습니다. 선호하시는 것으로 작성해 주시면 됩니다.
- 엔티티에 심한 제약이 따로 없는 만큼 자유롭게 스키마를 작성하시면 됩니다.
- 제출은 압축파일로 전달해 주시거나, 원하는 공유 git 저장소에 작성하고 공유해도 됩니다.

---

## API 예시

- 모든 응답은 JSON 형태로 내려와야 합니다. HTML 작성할 필요 없습니다.

### API 1. 생성
```
    request
        POST / HTTP/1.1
        (payload)

    response
        (자유롭게)
```

### API 2. 수정
```
    request
        PUT /:id HTTP/1.1
        (payload)

    response
        (자유롭게)
```

### API 3. 삭제
```
    request
        DELETE /:id HTTP/1.1

    response
        (자유롭게)
```

API 4. 조회
```
    request
        GET / HTTP/1.1

    response 
        [{
            id: 1,
            address: ‘서울특별시 강남구 대치동 821',
            ...기타정보들,
        }, {
            id: 2,
            address: ‘서울특별시 송파구 삼전동 110',
            ...기타정보들,
        }]
```

API 5. 집계

각 방의 제일 높은 월세를 기준으로 전체 평균을 구합니다. 하나의 방이 (보증금1000, 월세40) 또는 (보증금 2000, 월세30) 의 가격을 가진다면 (보증금1000, 월세40) 을 계산에 사용합니다.
```
    request
        GET /avg HTTP/1.1

    response 
        {
            average: {
                deposit: 1000,
                monthly: 40,
            }
        ]
```
