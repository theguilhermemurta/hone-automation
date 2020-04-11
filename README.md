#Device Registry Service

##Usage 

All responses will have the form

```json
{
	"data": "Mixed type holding the content of the response",
	"message": "Description of what happened"
}
```

Subsequent response definitions will only detail the expected value of the "data field"

### List all devices

**Definitions**

`GET /devices`

**Response**

_ `200 OK` on success

```json
[
	{
		"identifier": "floor-lamp",
		"name": "Floor Lamp",
		"divice_type": "switch",
		"controler_gateway": "198.1.68.0.2"
	},
	{
		"identifier": "samsung-tv",
		"name": "Samsung TV",
		"divice_type": "tv",
		"controler_gateway": "198.1.68.0.9"
	}

]
```

### Registering a new device

**Definitions**

`POST /devices`

**Arguments**

_ `"identifier": string` a globally unique identifier for this divice
_ `"name": string` a friendly name for the device
_ `"type": string` the device type
_ `"controler_geteway": string` ip adress of the device

**Responses**

_ `201 created` on success

```json
{
	"identifier": "samsung-tv",
	"name": "Samsung TV",
	"divice_type": "tv",
	"controler_gateway": "198.1.68.0.9"
}
```

## Lookup device details

`GET /device/<identifier>`

**Response**

_ `404 Not Found` if the device does not exist
_ `200 OK` on success

```json
{
	"identifier": "samsung-tv",
	"name": "Samsung TV",
	"divice_type": "tv",
	"controler_gateway": "198.1.68.0.9"
}
```

## Delete a device

**Definition**

`DELETE /devices/<identifier>`

**Responses**

_`404 Not Found` if the device does not exist
_`204 no content` on success