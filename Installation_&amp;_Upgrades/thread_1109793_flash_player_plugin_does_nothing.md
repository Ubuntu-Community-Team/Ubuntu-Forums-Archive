---
title: "flash player plugin does nothing"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by HughJarse on 2009-03-29
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")
I'm trying ubuntu for the first time so visiting some of my favourite websites - most of them need flash.
I have tried the .deb package, installs fine, except, no flash.
Also tried installing via terminal using
**sudo dpkg -i install_flash_player_10_linux.deb**

Trying **about: plugins** it doesn't appear...
```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
```

---

### Post by zvacet on 2009-03-29
Go to the terminal and type 

```
gksudo gedit /etc/apt/sources.list
```

and add 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

Now in sys>admin<synaptic in search box type adobe-flashplugin and when synaptic find it just install it.

---

### Post by wpshooter on 2009-03-29
Instead, I would go to the REAL Adobe site (not one of those fake ones) and download the tar version of the latest release of Adobe Flash Player and install it from the tar version after you have EXTRACTED it.

Write if you need further instructions.

---

### Post by HughJarse on 2009-03-30
Gonna try this when I get home

[http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

Installation instructions for tar.gz

       1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by HughJarse on 2009-03-30
Ok. Having all sorts of hardware trouble. PC booted after about 5 attempts but that's another issue!!

Downloaded the tar.gz file to the desktop and unpacked it.
Went to terminal as it suggests.
**sudo ./flashplayer-installer**

Then I got asked:
[SIZE="2"][FONT="Courier New"]Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): ./usr/lib/mozilla

WARNING: /home/barberj/Desktop/install_flash_player_10_linux/./usr/lib/mozilla is not a directory.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox-3.0b5

----------- Install Action Summary -----------

Adobe Flash Player 10 will be installed in the following directory:

Browser installation directory = **/usr/lib/firefox-3.0b5**

Proceed with the installation? (y/n/q): y

Installation complete.
[/SIZE][/FONT]



Still no joy :(
Wrong path?
Any ideas?

---

### Post by HughJarse on 2009-04-02
Fixed by reinstalling ubuntu 8.04.
Then installed the latest firefox version direct from mozilla's site. I manually installed 3.0.8 using their installation instructions, rather than using any automatic updaters.

Did the same for the flash player plugin on adobe's site and this is now working.

Both times I got the tar.gz files.

---

