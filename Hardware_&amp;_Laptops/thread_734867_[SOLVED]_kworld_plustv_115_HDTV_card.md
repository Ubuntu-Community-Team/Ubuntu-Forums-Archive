---
title: "[SOLVED] kworld plustv 115 HDTV card"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by Cresho on 2008-03-25
here is my small tutorial.  I already posted a avermedia one which works fine.  Both cards work the same. I'm  Posting this because I kept loosing track of where is where and information is scattered through out the net.  :lolflag:

********************************************************************************
kworld atsc 115 version on ubuntu hardy heron.**********************************
********************************************************************************
to start off!
make sure you have dependencies installed.


    * autotools-dev
    * cdbs
    * debhelper (>= 5)
    * libglade2-dev
    * libgnet-dev
    * libgnome2-dev
    * libgnomeui-dev
    * libgtk2.0-dev (>= 2.12)
    * libxine-dev
    * libxml-parser-perl
    * libxml2-dev
    * libxtst-dev
    * pkg-config

Build dependencies so in terminal, we will do the following first.

we need to fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.  refresh with button on top.  Also add third party software and source software sources.  in add and remove programs, under show, select "all available applications"
--------------------------------------------------------
sudo aptitude remove automake1.4
--------------------------------------------------------

secondly, 

--------------------------------------------------------
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev
--------------------------------------------------------

this prepares us to install the software needed.




********************************************************************************
Installing the kworld atsc 115 Driver*******************************************
********************************************************************************

terminal, line by line

--------------------------------------------------------
sudo apt-get install linux-doc-2.6.24 (get the one closest to your kernel look for it in synaptic "linux-doc")
cd /usr/share/doc/linux-doc-2.6.24/Documentation/dvb
sudo gzip -d get_dvb_firmware.gz
sudo chmod +x get_dvb_firmware
sudo ./get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware
--------------------------------------------------------

reboot!  After the reboot, you can type dmesg in terminal and look to see if it loaded.  It should look like this but look carefully.

--------------------------------------------------------
dmesg
--------------------------------------------------------

and you should see this.

--------------------------------------------------------
[   44.492291] nxt2004: Firmware upload complete
--------------------------------------------------------

we are done with driver install
********************************************************************************
checking if it all works!*******************************************************
********************************************************************************
dmesg in terminal and should see some things like a

and

--------------------------------------------------------
[   47.599223] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   47.636815] nxt2004: Waiting for firmware upload(2)...
[   49.176445] nxt2004: Firmware upload complete
--------------------------------------------------------

and If I do a

--------------------------------------------------------
lspci -vnn, i get
--------------------------------------------------------

you get

--------------------------------------------------------
01:06.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
	Subsystem: KWorld Computer Co. Ltd. Unknown device [17de:7352]
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at ec005000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
--------------------------------------------------------

and

--------------------------------------------------------
ls -l /dev/dvb/adapter0
--------------------------------------------------------

you get

--------------------------------------------------------
total 0
crw-rw----+ 1 root video 212, 4 2008-03-04 12:04 demux0
crw-rw----+ 1 root video 212, 5 2008-03-04 12:04 dvr0
crw-rw----+ 1 root video 212, 3 2008-03-04 12:04 frontend0
crw-rw----+ 1 root video 212, 7 2008-03-04 12:04 net0
--------------------------------------------------------

and finally...

--------------------------------------------------------
dmesg | grep dvb
--------------------------------------------------------

you get

--------------------------------------------------------
[ 56.545267] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
--------------------------------------------------------

then everything is in order driver and hardware wise!
********************************************************************************
software install****************************************************************
********************************************************************************
try installing the me-tv software through add and remove application in start menu of ubuntu.  Some reason, works better.  Then you will need to download the updated version and install it without uninstalling the older version.  Don't ask why but it works better (I was expiriencing driver issue when the drivers are loaded correctly.  Having the old version and installing the new one over it worked for me).  Download [https://launchpad.net/me-tv/+download](https://launchpad.net/me-tv/+download) the latest one. download it to your desktop and extract it. Then you cd into your directory "cd /home/yourname/Desktop/me-tv-0.5.24

in terminal you

./configure
make
sudo make install

now for the dvb utilities. me tv helps you with everything but dvb utilities actually works better in detecting channels.

sudo apt-get install dvb-utils
directory is here! /usr/share/doc/dvb-utils/
do a

mkdir /home/yourusername/.azap
and this creates a very needed directory

in terminal do this next line
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf

in your folder browser you can navigate to this location while the scan is taking place (nake sure you have view->hidden files in your browser so you can see the invisible directory). It will take a while and will see errors bot its normal till the channels start coming in. After scan terminal says done, open the channel.conf in the /home/yourusername/.azap directory with a text editor and save it as channels.conf on your desktop UTF-8 encoded(the option is available in the save feature so don't sweat it.

copy that channels.conf into the /home/yourusername/.me-tv and do not try using the my-tv channel scanner because it is not as good as the dvb-utils.

Launch the application and you can now record, watch.....ohh yeah, you can change the channels with right click and select the broadcasted name.

---

### Post by Cresho on 2008-03-25
I have a kaffeine version as well.  Not posting it since me-tv worked better right off the bat.

---

### Post by non-poster on 2008-03-26
More info: [http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_115](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_115)

---

