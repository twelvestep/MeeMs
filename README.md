# MeeMS 1.0 Specification

*1/2/2017*

## Contents

- [What is MeeMS](#whatIsRss)
- [About this document](#aboutThisDocument)
- [Data Models](#dataModels)
- [Required properties](#requiredProperties)
- [Optional properties](#optionalProperties)
- [License and authorship](#licenseAndAuthorship)

# What is MeeMS?

MeeMS is a web content format specification designed to be used by 12-step groups (designed originally for Alcoholics Anonymous meetings).

Its name is an acronym for 

**Mee**ting **M**etadata **S**pecification

MeeMS is a JSON specification and all APIs must be valid JSON, as published on the World Wide Web Consortium (W3C) website.

# About this document[ ](undefined)[![img](http://cyber.harvard.edu/rss/images/leftArrow.gif)](http://cyber.harvard.edu/rss/rss.html#aboutThisDocument)

This document represents the status of MeeMS as of the Fall of 2016, version 1.0.0. First we document the three established data models **Meetings**, **Groups**, and **Locations** and the relationships between them.

# Models

| **Model** | **Description**                          |
| :-------- | ---------------------------------------- |
| Meeting   | **Meeting**s are the central model of the API. A **Meeting** is an object containing name, time, and format metadata for specific 12-step meetings. |



## Meeting

#### Example JSON:

```json
[
    {
        "name": "Sunday Serenity",
        "slug": "sunday-serenity",
        "day": 0,
        "time": "18:00",
        "end_time": "19:30",
        "location": "Alano Club",
        "group": "The Serenity Group",
        "notes": "Ring buzzer. Meeting is on the 2nd floor.",
        "updated": "2014-05-31 14:32:23",
        "url": "https://intergroup.org/meetings/sunday-serenity",
        "image": "https://intergroup.org/assets/img/locations/alano-club.jpg",
        "types": [
            "O"
        ],
        "address": "123 Main Street",
        "city": "Anytown",
        "state": "CA",
        "postal_code": "98765",
        "country": "US",
        "region": "Downtown"
    },
    ...
]   
```



# Required Fields

### Basic Information

*All of these fields are Required*

| **Field**  | Type                | **Description**                          |
| :--------- | :------------------ | :--------------------------------------- |
| `name`     | String              | This should be the meeting name, where possible. Some areas use group names instead, although that's more abiguous. 255 characters max. |
| `slug`     | String              | This is the unique Identifier of the Meeting |
| `day`      | Int / Array of Ints | An integer or an array of integers 0-6, representing Sunday (0) through Saturday (6). |
| `time`     | String              | Five-character string in the `HH:MM` 24-hour time format. |
| `end_time` | String              | Five-character string in the `HH:MM` 24-hour time format. |


### Address Information

*Each of these fields is individually optional, but a valid address is required (made up of the combination of these fields)*

| **Field**  | Type                	| **Description**                          |
| :--------- | :------------------ 	| :--------------------------------------- |
| `address`     | String            | Strongly suggested. Street address |
| `city`     | String              	| Strongly suggested. City of the meeting |
| `state`      | String 			| State (province or region internationally) for the meeting |
| `postal_code`     | String        | Poscal Code (International postal codes are ok.) |
| `country` | String              | Country for the meeting. |


### Optional Fields

| **Field** | Type      | **Description**                          |
| :--------- | :------------------ | :--------------------------------------- |
| `location` | String     		   | is an optional string and should be a recognizable building or landmark name.
| `group` 	 | String		       | is an optional string.
| `notes` 	 | String		       | is an optional long text field. Line breaks are ok, but HTML will be stripped.
| `updated`  | String / UTC timestamp | is an optional UTC timestamp in the format `YYYY-MM-DD HH:MM:SS`.
| `url` 	 | String		       | is optional and should point to the meeting's listing on the area website.
| `image`  	 | String		       | is an optional url that should point to an image representing the location. We recommend an image of the building's facade. Ideally this is a JPG image 1080px wide by 540px tall.
| `types` 	 | String		       | is an optional array of standardized meeting types. See the types section below.
| `region` 	 | String		       | is an optional string that represents a geographical subset of meeting locations. Usually this is a neighborhood or city. District numbers are discouraged because they require special program knowledge to be understood.


MeeMS is offered under the terms of the MIT License.

The authors of this document are Daniel C. and Josh R. For questions, comments, please open an issue at https://github.com/twelvestep/MeeMs/issues.
