# FreeLib-Djatoka

This project is a fork of the aDORe-djatoka JP2 image server.  It was created in an attempt to simplify the image server's use.  In the process, additional caching and image management options were added.  The OpenSeadragon UI was also added as the project's preferred user interface.  FreeLib-Djatoka can be used on its own or it can be integrated into an external digital asset management system.  It's currently tested with Islandora.

The original aDORe-djatoka requires Sun's 1.6 JDK.

The freelib-djatoka project can be used with any JDK (OpenJDK or OracleJDK), 1.7 or later.

### Getting Started

To run freelib-djatoka, just download the project, change into the project's directory, and type:

    mvn jetty:run-forked

That's it.  You should then be able to go to the freelib-djatoka test page to confirm that the server is up:

    http://localhost:8888

When you want to stop the server, type the following from within the project's directory:

    mvn jetty:stop

### File System Ingest Configuration

FreeLib-Djatoka can load images in two different ways: the first way is by loading TIF images from the file system and converting them into JP2 in batch mode and the second way is by loading images on demand, as they are requested through the user interface. 

To load images from the file system, there are four configuration options defined in the pom.xml file.  To override these, it's best to create a settings.xml file and assign new values to them in there.  TODO: more details

	<djatoka.ingest.data>/usr/local/data/images/tiffs</djatoka.ingest.data>
	<djatoka.jp2.data>/usr/local/data/images/jp2s</djatoka.jp2.data>
	<openurl.cache.dir>/usr/local/data/images/tmpcache</openurl.cache.dir>
	<djatoka.view.cache>/usr/local/data/images/cache</djatoka.view.cache>

### Dynamic Image Ingest Configuration

TODO: Explain how this is different from the adore-djatoka way here.

### Tile Cache Utilities

Something that I added for the GDAO project but never documented was the tile pre-generation utility.  It can be run from the command line to pre-generate tiles for images listed in a CSV file.  You pass in the CSV file containing the IDs of the images (and titles, etc.), and the OpenSeadragon tiles would be auto-magically generated for you.  Run it by typing:

    mvn exec:java -Dexec.mainClass="info.freelibrary.djatoka.TileCache" -Dexec.args="src/test/resources/id_map.csv 2"

The "exec.args" would of course be changed to your CSV file and the position of the ID in the (1-based) column order (i.e., start counting columns at 1 not 0).

### Running freelib-djatoka at Port 80

http://www.eclipse.org/jetty/documentation/current/setting-port80-access.html

### Project Status

[![Build Status](https://travis-ci.org/ksclarke/freelib-djatoka.png?branch=fedora)](https://travis-ci.org/ksclarke/freelib-djatoka)

### License

This package, freelib-djatoka, like its upstream project, adore-djatoka, is available under the LGPL license (version 2.1 or later).

It contains the Kakadu binaries which are provided under a NON-COMMERCIAL USE ONLY license.  See the [adore-djatoka page](http://djatoka.sourceforge.net/ "The aDORe-djatoka Home Page") for more details.

### Contact

If you have questions about the freelib-djatoka project, feel free to <a href="mailto:ksclarke@gmail.com">email me</a>, Kevin S. Clarke, or to [file an issue](https://github.com/ksclarke/freelib-djatoka/issues "GitHub Issues Queue") in the GitHub issues queue.