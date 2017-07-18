# Asterisk13LTS-Ringfree
The Ringfree branch of Asterisk 13 LTS for use in PBX OS 14

1) Pull source code from github (https://github.com/ringfreejohn/Asterisk13LTS-Ringfree)
----------------------------------------------------------------------------------------
 
2) Untar and run the following configure:
-----------------------------------------

$ ./configure --libdir=/usr/lib64 --with-pjproject-bundled --disable-xmldoc

3) Set compilation options
--------------------------

$ make menuselect

There are some options we want to set here to ensure that Asterisk is suitably compiled to run on the Ringfree distributed container platform:

- Remove all SOUNDS as these are distributed and maintained by the framework instead of Asterisk compilation deployment.
- Turn on LOW_MEMORY compilation flag
- Turn off BUILD_NATIVE compilation flag
- Turn on DONT_OPTIMIZE
- Turn on format_mp3 

4) Stop Asterisk and remove all previous Asterisk modules:
----------------------------------------------------------

$ fwconsole stop 
$ rm /usr/lib64/asterisk/modules/*

5) Compile
----------

$ make 
$ make install

6) Start Asterisk
-------------------------------

$ fwconsole start