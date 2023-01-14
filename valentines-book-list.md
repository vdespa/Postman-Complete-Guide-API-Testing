# Simple Grocery Store API

This API allows you to place a grocery order which will be ready for pick-up in the store.

The API is available at `https://simple-grocery-store-api.glitch.me`

Alternative URL: `http://simple-grocery-store-api.online/` (HTTP only!)

## Endpoints

- [Status](#Status)
- [Books](#Products)
  - [Get a book list](#Get-all-products)


## Status

**`GET /status`**

Returns the status of the API. Example response:

```
{
    "status": "UP"
}
```

Status `UP` indicates that the API is running as expected.

No response or any other response indicates that the API is not functioning correctly.

## Books

### Get a book list

**`GET /books/lists`**

Returns a list of books 

**Parameters**

| Name        | Type    | In    | Required | Description                                                                                                                                          |
| ----------- | ------- | ----- | -------- | ----------------------------------------------------------------------------------------------------------- |
| `api-key`   | string  | query | Yes      | Specifies API key.                                                                                          |
| `list`      | string  | query | Yes      | Specifies the list you want to retrieve. Must be one of: favourite-books, non-fiction, wishlist, fiction.   |
| `page`      | integer | query | No       | Specifies the page you wish to retrive from the entire result set.                                          |

**Status codes**

| Status code | Description |
|-----------------|-----------------------------------------------------|
| 200 OK          | Indicates a successful response. |
| 400 Bad Request | Indicates that the parameters provided are invalid. |

Example response:

```
{
    "status": "OK",
    "num_results": 17,
    "page": 1,
    "total_pages": 4,
    "results": [
        {
            "title": "Crush It!: Why NOW Is the Time to Cash In on Your Passion",
            "category": [
                "non-fiction"
            ],
            "type": "audio",
            "author": "Gary Vaynerchuk",
            "release_year": 2010,
            "rating": "7"
        },
        ...
    ]
]
```


## API Authentication

Some endpoints require authentication. 

The endpoints that require authentication expect a bearer token sent in the `Authorization` header.

Example:

`Authorization: Bearer YOUR TOKEN`