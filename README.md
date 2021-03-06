# geo-me

# Description
The Geo-me service performs self-geolocation of a platform (the target) using a set of observations from the platform to a predefined set of landmarks (the asset(s)). The service provides a re-sectioning function commonly used in overland navigation scenarios in the absence of global positioning system (GPS) effects. This service is capable of fusing any combination of angles to or ranges from known landmarks (the assets) and can handle erroneous measurements. Output of the service is a geolocation estimation latitude and longitude, a circular error of probability (CEP) provided as elliptical parameters (length, width and rotation). The service can provide an optional formatted kml file containing the computing scenario and result (this kml may be plotted on various geospatial interface systems).

# Inputs
Inputs are provided in the following json format:
```
{
    "observation": [
        {
            "assetId": "<string>",
            "meas": <double - range in [metres] or angle in [radians] according to the type>,          
            "id": <int>,
            "type": "<'range' or 'aoa'>",
            "lat": <double - latitude in decimal degrees -90 to 90>,
            "lon": <double - latitude in decimal degrees -180 to 180>
        },
        ...
    ],
    "target": {
        "name": "<string>",
        "id": "<string>"
    },
    "provide_kml_out": <boolean, optional, default: false>
}
```
An optional simulation tool is provided for ease of validation - the tool generates a set of observations in the required format for any arbitrary geometry of platforms/targets and landmarks/assets. See: https://github.com/tgotech/geo_me_simulator
  
# Outputs
Outputs are returned in the following json format:
```
{
	"lat": <double - latitude [decimal degrees]>,
	"lon": <double - longitude [decimal degrees]>,
	"elp_long": <double - [metres]>,
	"elp_short": <double - [metres]>,
	"elp_rot": <double - [radians]>,
	"residual": <double>
	"status_svc": "<string - 'ok'>",
	"statusMessage_svc": "<string, returned only if status is not 'ok'>",
	"kml_out": <string>
}
```
# Detailed Guide
For more detailed instructions see the userguide.md
