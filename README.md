# Mapping Society Hill

This project will develop a multimedia, map-based website for documenting the urban renewal of Philadelphia’s Society Hill neighborhood during the 1950s-70s. By aggregating historical photographs across time, alongside site-level data from the census, city directories, planning documents, and oral histories, the site will begin to reconstruct the reconstruction of a neighborhood.

This is designed to be a simple map created using Javascript and the ArcGIS API in an html page that can be embedded into any larger website.


## Getting Started


To add the map to your website, download both files and upload to the server hosting your current website.  `index.html` is a complete copy of the code for the map page. `shstyle.css` contains all the style information.

### Prerequisites

This project uses [ArcGIS API for Javascript version 4.4](https://developers.arcgis.com/javascript/latest/guide/release-notes/4.4/index.html), as well as the accompanying stylesheet.  Current documentation available on ESRI's website is for version 4.6 but there appear to have been few changes between 4.4 and 4.6.  You should NOT use anything from version 3.22 as it is very different from 4.4.

WORKING WITH ARCGIS ONLINE
This code gets data from a webmap in ArcGIS online, which serves as the database.  All parcel layers should be generated in ArcGIS for Desktop as shapefiles, compressed into zip files, and loaded into a map in the user's account on ArcGIS Online.  For the map to be viewed by the public, all layers and the map itself must be made public using the sharing settings in ArcGIS Online.

To get a raster into ArcGIS Online, you need to publish it as a hosted tile layer.  To do this you must have privileges to publish a hosted tile layer.  Information about this can be found here: http://doc.arcgis.com/en/arcgis-online/manage-data/publish-tiles.htm.  This map used the option to build and share a tile package in ArcMap.   

Styling should also be done in ArcGIS Online.  When styling the parcels, if you just want a parcel's outline, the intuitive thing to do seems to be to set its fill color to No fill.  However, if you do this, to ArcGIS it will be as though the parcel's interior doesn't exist and the popup won't appear when you click on it.  If you want the parcel's interior to be invisible but still clickable, choose any fill color and then set its transparency to 100%.  You can then select a color for the outline.  

To link to a map, the webmap ID, which can be found at the end of the URL in ArcGIS Online, needs to be referenced as the portalItem when a new webmap is created.  The map's layers also need to be referenced using findLayerById.  All layers that are set as visible in ArcGIS Online will appear on the map as soon as you link to the webmap as a portal item, but the individual layers must also be input.  The layer's IDs will be printed in the console.  A layer's ID will contain its name in ArcGIS Online but will also contain words and/or additional numbers that aren't necessarily evident in ArcGIS Online.  

There is a limited amount of editing, such as adding features or modifying existing features, that can be done in ArcGIS Online.  Images can be deleted and reordered; however an image's date, if you wish to display it, must always go in the field immediately after the image.  Spreadsheet data and other fields can also be edited.  Other changes such as adding fields is best done in ArcGIS for Desktop. You will then need to re upload the layers, which will mean they will have new IDs that need to be changed in the code.

CONFIGURABLES
Because ArcGIS Online limits shapefiles to 1000 features, this code is designed to take as input a dataset that is split across multiple layers.  There can be as many or as few layers as the user desires.  For layers with data, each layer's ID needs to be included in the array listOfLayerIds.  For layers without data, each layer's ID needs to be included in the array parcelsWithoutDataIDs.  If there is only one layer, just include the one layer.  

The IDs of a modern and historic basemap can also be input.

For spreadsheet data, all field names need to be in the proper ArcGIS format (13 characters or less, first character is a letter, no spaces, - or other special characters except _ ) before the spreadsheet is added to ArcGIS.  The names of the spreadsheet fields that you wish to display in the popup should be input into the array spreadSheetFields.  These names should exactly match the fields in the spreadsheet and in ArcGIS Online.  To control the names that are actually displayed for the field names, use the array spreadSheetFieldsAliases.

The field to be used for the popup's title can be input in the variable titleField.  Right now it's the Name field from PhillyHistory but in the future it will be the parcel's address as input by Sarah and Meredith.


## Built With

[ArcGIS API for Javascript version 4.4](https://developers.arcgis.com/javascript/latest/guide/release-notes/4.4/index.html)


## Authors

* **Rachel Cohen** - *Project Developer*

## Acknowledgments

The ArcGIS API for Javascript 4.4 API Reference website was essential for the creation of this site:
https://developers.arcgis.com/javascript/latest/api-reference/index.html
