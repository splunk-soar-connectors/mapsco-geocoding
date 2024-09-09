[comment]: # "Auto-generated SOAR connector documentation"
# Geocoding Maps Co

Publisher: Unapproved Pty Ltd  
Connector Version: 1.0.0  
Product Vendor: My Maps Inc  
Product Name: Geocoding by Map Maker  
Product Version Supported (regex): ".\*"  
Minimum Product Version: 6.2.1  

Forward and Reverse Geocoding

# Splunk> maps.co

Welcome to the open-source repository for Splunk> Phantom's mapsco-geocoding App.

Who doesnt like free data that enhances your telemetary. I was just after some interpritations of my lat's and long's and didnt want to have to pay. I found that at [MAPS.CO](https://geocode.maps.co) 

## Legal and License
This Phantom App is licensed under the Apache 2.0 license. Please see our [Contributing Guide](https://github.com/Splunk-SOAR-Apps/.github/blob/main/.github/CONTRIBUTING.md#legal-notice) for further details.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Geocoding by Map Maker asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base_url** |  required  | string | Base URL for service (use default)
**api_key** |  required  | password | API Key (eg: 1234asdf2345)

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[forward geocode](#action-forward-geocode) - Convert human-readable address to coordinates  
[reverse geocode](#action-reverse-geocode) - Convert coordinates to human-readable address  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

Ensures that a firewall is not blocking conections to the base URL.
Base URL should not be changed unless your are using paid API access in which case an alternative base url will be provided.

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'forward geocode'
Convert human-readable address to coordinates

Type: **investigate**  
Read only: **True**

Forward Geocoding process permits two forms of an address.
1) Convert street address to coordinates.
EG: 1 Apple Park Way. Cupertino, CA 95014. United States

2) Convert a location name to coordinates.
EG: Statue of Liberty.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**address** |  required  | Address | string |  `street address` 

#### Action Output
DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.address | string |  `street address`  |  
action_result.status | string |  |   success  failed 
action_result.data.\*.\*.lat | numeric |  `latitude`  |  
action_result.data.\*.\*.lon | numeric |  `longitude`  |  
action_result.data.\*.\*.display_name | numeric |  |  
action_result.message | string |  |  
action_result.summary | string |  |  
summary.total_objects | numeric |  |  
summary.total_objects_successful | numeric |  |    

## action: 'reverse geocode'
Convert coordinates to human-readable address

Type: **investigate**  
Read only: **True**

To reverse geocode, provide both the latitude and longitude parameters to the /reverse endpoint, e.g:

Convert coordinates to human-readable address.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**latitude** |  required  | Latitude coordinate | string |  `latitude` 
**longitude** |  required  | Longitude coordinate | string |  `longitude` 

#### Action Output
DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.latitude | string |  `latitude`  |  
action_result.parameter.longitude | string |  `longitude`  |  
action_result.data | string |  |  
action_result.summary | string |  |  
action_result.status | string |  |   success  failed 
action_result.message | string |  |  
summary.total_objects | numeric |  |  
summary.total_objects_successful | numeric |  |  