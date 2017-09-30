# version 1.0	initial version

Copyright (c) 2017 Paul van Haastrecht <paulvha@hotmail.com>


## Background
As part of a larger project I am looking at analyzing and understanding the air quality. 
The aim of this project was to better understand the kind of gas-types that are in the air. 

The Grove Multichannel board is highly used, there is a lot of code (mostly for usage on the Arduino). 
It is a relative cheap board that looked to be right one for the project.  
There is good hardware information about the board with the provided EAGLE files.

I have ported the library to C on a Raspberry PI running Raspbian Jessie release. 
Unfortunately apart from the library code, there is hardly ANY explanation nor information available 
about the interaction between the Grove board and the program. The commands are not well explained, 
the code and calculation is unclear on places. 
Next to that the MiCS-6814  data sheet is not rich in documentation and explanations. 
I spend many hours and have seen many, many pages on Internet, but apart from a few, it did not help.

As a result I have spend much more time analyzing the board and software than I originally planned to do.  
I have discovered a number of issues with the board to makes me question the measurement results 
and why this has not been detected before. 

For detailed information about findings, the hardware and software, please read the included mics6814.odt
 
## Software installation

Make your self superuser : sudo bash

BCM2835 library
Install latest from BCM2835 from : http://www.airspayce.com/mikem/bcm2835/

1. cd /home/pi
2. wget http://www.airspayce.com/mikem/bcm2835/bcm2835-1.52.tar.gz
3. tar -zxf bcm2835-1.52.tar.gz		// 1.52 was version number at the time of writing
4. cd bcm2835-1.52
5. ./configure
6. sudo make check
7. sudo make install

Install the gass utility
1. cd /home/pi
2. tar -xzvf multichannel.1.tar.gz
3. cd  gass
4. ./mgass.sh

To run the software you MUST be root/super user given the Linux permission: sudo ./gass

To get help : ./gass -h

