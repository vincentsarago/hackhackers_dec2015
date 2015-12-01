
![](/img/Pres.jpeg)

# hackhackers_dec2015
links and infos given during my "Nouvelles tendances en cartographie" presentation

[Event](http://www.meetup.com/fr/HacksHackersMontreal/events/227012288/)

Imagery
-------
![](/img/respercost.png)
source: http://satsummit.github.io/landscape/#capture

New players:
- [PlanetLabs](https://www.planet.com)
- [Urthecast](https://www.urthecast.com)
- [SkyBox Imaging (google)](http://www.skyboximaging.com)
- [Dauria Aerospace](http://dauria.ru)

Access
-------
- [EFFIGIS](http://effigis.com/solutions/satellite-images/) (Order high resolution images)
- [EarthExplorer](http://earthexplorer.usgs.gov) (Landsat dataset + others)
- [Nasa Worldview](https://earthdata.nasa.gov/labs/worldview/) (Visualise and share MODIS dataset)
- [Libra by DevelopmentSeed](http://libra.developmentseed.org) (Landsat 8)
- [RemotePixel](http://remotepixel.ca) (Landsat 8 and MODIS)
- [Fetch Astro Digital](https://fetch.astrodigital.com) (Landsat 8)
- [OpenAerialMap](http://openaerialmap.org) (Landsat 8 and UAV)
- [Sentinels Scientific Data Hub](https://scihub.esa.int) (Sentinel)
- [GeoBrowser by Sat Catapult](https://geobrowser.satapps.org) (Sentinel)
- [Landsat on AWS](https://aws.amazon.com/fr/public-data-sets/landsat/)

Process
-------
- [QGIS](http://www.qgis.org)
- [Arcgis](http://www.esri.com/products/arcgis-capabilities/imagery)
- [GDAL](http://www.gdal.org)
- [Landsat-Util](https://github.com/developmentseed/landsat-util)
- [Rasterio](https://github.com/mapbox/rasterio)
- [SnapSat](http://snapsat.org) (Landsat 8 color composite)
- [Gimp](https://www.gimp.org)
- [ImageMagick](http://www.imagemagick.org/script/index.php)
- [Generating map tiles with GDAL2Tiles](http://blog.thematicmapping.org/2008/03/generating-map-tiles-with-gdal2tiles.html)
- [Dan's GDAL scripts](http://www.gina.alaska.edu/projects/gina-tools/)

Example: Rio Doce after Samarco Dam Breach (Nov. 2015)
#Download data
landsat download LC82160732015309LGN00 -b 4,3,2
landsat download LC82160732015325LGN00 -b 4,3,2
#process data
1) Create color natural composite
gdalbuildvrt -separate ~/LC82160732015309LGN00_rgb.vrt /Users/vincentsarago/landsat/downloads/LC82160732015309LGN00/LC82160732015309LGN00_B{4,3,2}.TIF
gdalbuildvrt -separate ~/LC82160732015325LGN00_rgb.vrt /Users/vincentsarago/landsat/downloads/LC82160732015325LGN00/LC82160732015325LGN00_B{4,3,2}.TIF
gdalwarp -t_srs EPSG:4326 -r cubic -srcnodata 0 -dstnodata 0 ~/LC82160732015309LGN00_rgb.vrt ~/LC82160732015309LGN00_rgb.tif
gdalwarp -t_srs EPSG:4326 -r cubic -srcnodata 0 -dstnodata 0 ~/LC82160732015325LGN00_rgb.vrt ~/LC82160732015325LGN00_rgb.tif
2) Open geotiff in QGIS
3) choose an area of interest
4) Adjust color histogram
5) Create Map Tiles 
- gdal2tiles.py -n -z 0-13 LC82160732015309LGN00_rgbR.tif before
- gdal2tiles.py -n -z 0-13 LC82160732015325LGN00_rgbR.tif after


Display / Distribute
-------
- [Fetch Astro Digital](https://fetch.astrodigital.com) (Publish Landsat 8)
- [Leaflet](https://fetch.astrodigital.com) (Publish Landsat 8)
- [MapBox](https://www.mapbox.com)

More
-------
- [Satellites in Global Development](http://satsummit.github.io/landscape/) 
- [Derek Watkins - gdal-cheat-sheet](https://github.com/dwtkns/gdal-cheat-sheet)
- [Jacques Tardie - Remote Sensing ressource](https://github.com/jacquestardie/remote)
- [Processing Landsat 8 Using Open-Source Tools](https://www.mapbox.com/blog/processing-landsat-8/)
- [Putting Landsat 8’s Bands to Work](https://www.mapbox.com/blog/putting-landsat-8-bands-to-work/)
- [Introduction to the geo command line](https://developmentseed.org/blog/2015/08/27/geo-command-line-introduction/)
- [Optimizing Landsat-util](https://developmentseed.org/blog/2015/03/28/twice-as-fast)
- [Gdal CookBook](https://pcjericks.github.io/py-gdalogr-cookbook/raster_layers.html)
- [Landsat 8 Band Combinations (ENVI)](http://www.exelisvis.com/Home/NewsUpdates/TabId/170/ArtMID/735/ArticleID/14305/The-Many-Band-Combinations-of-Landsat-8.aspx)
- [Landsat 8 Band Combinations (ArcGIS)](http://www.exelisvis.com/Home/NewsUpdates/TabId/170/ArtMID/735/ArticleID/14305/The-Many-Band-Combinations-of-Landsat-8.aspx)


Who to follow
-------
- [@Effigis](https://twitter.com/Effigis) 
- [@Mapbox](https://twitter.com/Mapbox) 
- [@Developmentseed](https://twitter.com/developmentseed ) 
- [@hotosm](https://twitter.com/hotosm) 
- [@astrodigitalgeo](https://twitter.com/astrodigitalgeo) 
- [@cartoDB](https://twitter.com/cartoDB) 
- [@SurreySat](https://twitter.com/SurreySat) 
- [@BlackBridgeCorp](https://twitter.com/BlackBridgeCorp) 
- [@planetlabs](https://twitter.com/planetlabs) 
- [@DigitalGlobe](https://twitter.com/DigitalGlobe) 
- [@AirbusDS](https://twitter.com/AirbusDS) 
- [@eoPortal](https://twitter.com/eoPortal) 
- [@MDA_Geospatial](https://twitter.com/MDA_Geospatial) 
- [@SatAppsCatapult](https://twitter.com/SatAppsCatapult) 
- [@ESA_EO](https://twitter.com/ESA_EO) 
- [@NASA_Landsat](https://twitter.com/NASA_Landsat) 
- [@USGSLandsat](https://twitter.com/USGSLandsat) 
- [@RemotePixel](https://twitter.com/RemotePixel) 
- [@DisastersChart](https://twitter.com/DisastersChart) 

