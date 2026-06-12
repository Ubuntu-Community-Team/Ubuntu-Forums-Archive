---
title: "Avermedia AVerTVHD MCE A180"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by Cresho on 2008-03-04
Hello!  (running hardy heron alpha4)

I seen posts about this card working great but I have a problem.

if I do a dmesg, i get

Device:	01:06.0
Class:	Multimedia controller
Vendor:	Philips Semiconductors
Device:	SAA7133/SAA7135 Video Broadcast Decoder
SVendor:	Avermedia Technologies Inc
SDevice:	AVerTVHD MCE A180
Rev:	d1


and If I do a lspci -vnn, i get

01:06.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
	Subsystem: Avermedia Technologies Inc AVerTVHD MCE A180 [1461:1044]
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at fc005000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>


and  ls -l /dev/dvb/adapter0 
total 0
crw-rw----+ 1 root video 212, 4 2008-03-04 12:04 demux0
crw-rw----+ 1 root video 212, 5 2008-03-04 12:04 dvr0
crw-rw----+ 1 root video 212, 3 2008-03-04 12:04 frontend0
crw-rw----+ 1 root video 212, 7 2008-03-04 12:04 net0


and finally......dmesg | grep dvb
[   56.545267] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...



The drivers do not load!!!!!!!  that is my problem.  I downloaded the firmware, extracted it and placed it into the /ib/firmware directory, changed the modprobe with the something-dvb and now I still get this error.....does anybody have any idea what is going on?  I read in another post that someone had to downgrade ubuntu to edgy from feisty to get this card to work!

thanks!

---

### Post by Cresho on 2008-03-05
never mind, i needed to drop the file in /lib/firmware/and the linux kernel i am using.

now when I do a dmesg, i get 
[   47.599223] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   47.636815] nxt2004: Waiting for firmware upload(2)...
[   49.176445] nxt2004: Firmware upload complete

---

### Post by Cresho on 2008-03-05
Hello all!  I just managed to get my HDTV Tuner running under Hardy Heron, using ME TV, and Avermedia AVerTVHD MCE A180.

Ill post a full tutorial from driver install, channel scan creation of channel.conf, and software usage.  TOok me a total of 16+ hours reading stuff and got all working under 30 minutes.

---

### Post by Cresho on 2008-03-06
Here is the tutorial.  Ill be cleaning this sooner or later.



to start off!
make sure you have dependencies installed.

Build dependencies

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



or use this in one line in terminal and install...answer all questions as well.

sudo aptitude remove automake1.4


sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev





Installing the AVerTVHD MCE A180 Driver
********************************************************************************
********************************************************************************
********************************************************************************

terminal, line by line
----------------------------------------------------------------------
sudo apt-get install linux-doc-2.6.24
cd /usr/share/doc/linux-doc-2.6.24/Documentation/dvb
sudo gzip -d get_dvb_firmware.gz
sudo chmod +x get_dvb_firmware
sudo ./get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware/2.6.24-11-generic (this is your kernel(wich can be seen in system->prefference->system monitor and use the system tab or you can view it in that directory.)

modprobe saa7134-dvb (this command activates it)
----------------------------------------------------------------------

sudo gedit /etc/modprobe.d/blacklist
and add these 2 lines to it
--------------------
#makes this useless
blacklist saa7134


sudo gedit /etc/modules
and add this to it
--------------------
saa7134-dvb


reboot for good measure!

just to make sure everything is fine, do this.
********************************************************************************
********************************************************************************
********************************************************************************
dmesg in terminal and should see some things like a

Device: 01:06.0
Class: Multimedia controller
Vendor: Philips Semiconductors
Device: SAA7133/SAA7135 Video Broadcast Decoder
SVendor: Avermedia Technologies Inc
SDevice: AVerTVHD MCE A180
Rev: d1

and

[   47.599223] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   47.636815] nxt2004: Waiting for firmware upload(2)...
[   49.176445] nxt2004: Firmware upload complete
---------------------------------------------------------------
and If I do a lspci -vnn, i get

01:06.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
Subsystem: Avermedia Technologies Inc AVerTVHD MCE A180 [1461:1044]
Flags: bus master, medium devsel, latency 32, IRQ 21
Memory at fc005000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
---------------------------------------------------------------
and ls -l /dev/dvb/adapter0

total 0
crw-rw----+ 1 root video 212, 4 2008-03-04 12:04 demux0
crw-rw----+ 1 root video 212, 5 2008-03-04 12:04 dvr0
crw-rw----+ 1 root video 212, 3 2008-03-04 12:04 frontend0
crw-rw----+ 1 root video 212, 7 2008-03-04 12:04 net0
---------------------------------------------------------------
then everything is in order driver and hardware wise!
********************************************************************************
********************************************************************************
********************************************************************************

software install
********************************************************************************
********************************************************************************
********************************************************************************
Just a note before we get started:
I had a little problem here.  If I installed a fresh me-tv 0.5.24 on a new os installation, I could not get it to run due to "Unable to initiate video driver."  So what I did to rectify this problem was install me-tv through add and remove programs in ubuntu and reinstall the 0.5.24(without uninstalling anything).  This fixed my problem.

for me tv, download [https://launchpad.net/me-tv/+download](https://launchpad.net/me-tv/+download) the latest one.  download it to your desktop and extract it.  Then you cd into your directory "cd /home/yourname/Desktop/me-tv-0.5.24

in terminal you

./configure
make
sudo make install

now for the dvb utilities.  me tv helps you with everything but dvb utilities actually works better in detecting channels.

sudo apt-get install dvb-utils
directory is here!  /usr/share/doc/dvb-utils/
do a 

mkdir /home/yourusername/.azap
and this creates a very needed directory

in terminal do this next line
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf

in your folder browser you can navigate to this location while the scan is taking place (nake sure you have view->hidden files in your browser so you can see the invisible directory).  It will take a while and will see errors bot its normal till the channels start coming in.  After scan terminal says done, open the channel.conf in the /home/yourusername/.azap directory with a text editor and save it as channels.conf on your desktop UTF-8 encoded(the option is available in the save feature so don't sweet it.

copy that channels.conf into the /home/yourusername/.me-tv and do not try using the my-tv channel scanner because it is not as good as the dvb-utils.

Launch the application and you can now record, watch.....ohh yeah, you can change the channels with right click and select the broadcasted name.


------------------------------------------------

---

### Post by non-poster on 2008-03-26
Also see [http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTVHD_MCE_A180](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTVHD_MCE_A180)

---

### Post by sc0g on 2008-06-11
Thanks for your input on this topic. I was able to get my AVerMedia TVHD MCE A180 working on my digital signal coming from Charter Communications here in Alabama.

However, it seems that I am having trouble finding which signal settings to use when scanning... I have signed up for Schedules Direct who I will be using as a source for my channel listings...

Do you guys have any suggestions where to begin? I would show some logs, but at this time I do not know what specifics you guys would need. It seems that I was able to pick up a few channels when scanning under:
Cable High
QAM-256
5_1 and 5-1

I'll let you know about my progress concerning this... Help would be very much appreciated!!!

---

### Post by sc0g on 2008-06-18
Okay so I have made some tremendous progress on scanning for channels for Charter Communications, Charter Digital Cable, Charter HD (had to reference all of these because people may search for different phrases when on the Gooogle)

Anyways...

I have mapped my programming schedules I receive from Schedules Direct to the channels that I have found using the following scanning parameters:

- Full Scan
- Cable High
- QAM-256
- 51 NONE (on the channel separator)

The channels I now have working for my Charter Digital Cable subscription in Birmingham, Alabama are as follows (I will continue to add channels as I find more):

103#2 ESPN-HD
103#3 Create ?
103#4 CBS
85#1 ESPN2-HD
85#4 CSPAN
12080 - 1008 Peachtree-HD (Atlanta Braves baseball, I think)
77#3 GameShow Network
93#1 CBS-HD
93#2 ABC-HD
93#3 APT-HD
100#1 G4
92#7 ESPN-Classic?
90#4 NBC13-Weather Plus
90#3 NBC13-HD
90#2 ABC3340 Weather
90#1 FOX6-HD

I'll keep you posted.

---

### Post by Cresho on 2008-06-19
wow.  You have hd through cable?  That is great.  Thanks for your post, it should help others like myself in getting hd cable running on the pc.


BTW, I was referencing this post to another person and just happened to miss your post 1 week ago.  I posted a thanks to you for the info. :)



One more thing and this is important, are you using me-tv to scan for the channels or are you using azap?  if you change this line

scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf

to

any of the ones in this directory, /usr/share/doc/dvb-utils/examples/scan/atsc/

you can probably find more  channels.


list directory of

/usr/share/doc/dvb-utils/examples/scan/atsc/

is
us-ATSC-center-frequencies-8VSB                 
us-Cable-EIA-542-HRC-center-frequencies-QAM256  
us-Cable-EIA-542-IRC-center_frequencies-QAM256  
us-Cable-HRC-center-frequencies-QAM256          
us-Cable-IRC-center-frequencies-QAM256          
us-Cable-Standard-center-frequencies-QAM256     
us-CA-SF-Bay-Area
us-ID-Boise
us-MA-Boston
us-NTSC-center-frequencies-8VSB
us-MI-Lansing
us-NY-TWC-NYC
us-PA-Philadelphia


if your azap is being used, try this line and see if you get more channels.

scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-HRC-center-frequencies-QAM256 > ~/.azap/channels.conf

or  
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-EIA-542-IRC-center_frequencies-QAM256  > ~/.azap/channels.conf

---

### Post by sc0g on 2008-06-21
I am using MythTV to scan for channels. Sorry that I forgot to mention that. By the way

```

# scan us-Cable-Standard-center-frequencies-QAM256 > /home/dscogin/us-Cable-Standard-center-frequencies-QAM256-channels.conf
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 57000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 63000000:QAM_256 (tuning failed)
etc...etc...

```

```

# scan us-Cable-HRC-center-frequencies-QAM256 > /home/dscogin/us-Cable-HRC-center-frequencies-QAM256-channels.conf
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 73753600:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 73753600:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 55752700:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 55752700:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 61753000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 61753000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 67753300:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 67753300:QAM_256 (tuning failed)
etc...etc...

```

```

scan us-Cable-EIA-542-HRC-center-frequencies-QAM256 > /home/dscogin/us-Cable-EIA-542-HRC-center-frequencies-QAM256-channels.conf
scanning us-Cable-EIA-542-HRC-center-frequencies-QAM256
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 73753600:QAM_256

WARNING: >>> tuning failed!!!
>>> tune to: 73753600:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 55752700:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 55752700:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 61753000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 61753000:QAM_256 (tuning failed)

```

How long should I let these scans run?

---

### Post by Cresho on 2008-06-21
scans should be left alone until it tells you it is finished.

---

### Post by sc0g on 2008-06-22
It seems that the output file produced by these scans are empty... It looks as though the only channels I have been able to find when scanning are when scanning through MythTV.

Oh well...

---

