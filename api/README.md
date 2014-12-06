Couchbasket API
===
>Couchbasket is a generic online store engine made on Node.Js and uses CouchDB  database engine as data store. 

---


### General notes


#### API Responses

Successfully executed requests against the Couchbasket REST API comes with _application/json_ reply where result object has at least three fields, _status_ that equals to _result_ in case if request was processed with no errors and it will be equal to _error_ if there is an error occured. Actual request execution result comes in _data_ field, and _executionTime_ will tell you how long it took to process your request.

```
{
	"status": "result",
	"data": ""
	"execTime": 0.00
}
```

In situations when there is an erorr occured, _status_ field is marked to _error_ and _data_ field usually contains detailed enough information on the error.

```
{
	"status": "error",
	"data": "error_details"
	"execTime": 0.00
}
```

----

### API methods

#### Categories

API end-point to collect all the categories

```
GET /categories
```

Create a new category

```
PUT /{categories}/{category_id}

Request Body:
{
	"published": true|false,
	"items": [ ]
}
```

Returns result or error object

```
{
	"status": "result|error",
	"data": ""
	"execTime": 0.00
}
```

Modify existing category

```
POST /{categories}/{category_id}

Request body:
{
	"published": true|false
}
```

Delete a category and all its products

```
DELETE /{categories}/{category_id}
```


#### Products

Getting product details

```
GET /{category}/{product_id}
```

Creating new product listing

```
PUT /{category}/{product_id}

Request body:
{
	"published": true|false,
	"sku": "",
	"createdOn": "",
	"createdBy": "",
	"updatedOn": "",
	"updatedBy": "",
	"title": "",
	"shortDescription": "",
	"longDescription": "",
	"images": [ ],
	"price": 0.00,
	"taxable": true|false,
	"dimensions": 
		{
			"width": 0.00,
			"height": 0.00,
			"length": 0.00
		},
	"packaging": 
		{
			"width": 0.00,
			"height": 0.00,
			"length": 0.00
		},
	"allowComments": true|false
}
```

#### Search

Search for product by keywords

```
GET /search/{criteria}
```

Returns result or error object in the following format:

```
{
	"status": "result",
	"data": 
	[
		{
			"sku": "",
			"title": "",
			"price": 0.00
		}
	]
}
```
