---
title: "[SOLVED] Stream won't play. Help"
date: 2008-09-18
forum: General Help
---

### Post by ManyBeers on 2008-09-18
[http://www.ksl.com/index.php?nid=21]("http://www.ksl.com/index.php?nid=21") I can't get one of the streams on the 
right to play in Firefox 3.0.1 with these plugins


    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
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
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
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

Can somebody help. Make one of the streams work. I always
use Winamp in WindowsXP and use the mp3 stream.But I'll use whatever stream will work.
ps I'm not talking about the video stream running in the small window.

---

### Post by ManyBeers on 2008-09-18
Anybody got any ideas?

---

### Post by mb_webguy on 2008-09-18
You say you can't open one of the streams...  Which one can't you open?  I can open the first one on the page (the Windows media stream that opens in its own window) using the Totem plugin in Firefox, and I can open the mp3 streams using VLC.

---

### Post by TeXtonyx on 2008-09-18
[http://www.howtogeek.com/howto/linux/installing-flash-player-in-firefox-on-ubuntu-gutsy/](http://www.howtogeek.com/howto/linux/installing-flash-player-in-firefox-on-ubuntu-gutsy/)

That explanation covers the previous version of Ubuntu, but I think the idea of a manual install will work for 8.04 also. Some of the 
commands may require root privileges before they will execute, and often sudo (followed by password) will work. At least its an idea.

---

### Post by mb_webguy on 2008-09-18
As far as I can tell, none of the streams on that page require Flash.  However, the best way to install the most recent version of Flash is to use the backports repository.

---

### Post by ManyBeers on 2008-09-18
> **mb_webguy said:**
> You say you can't open one of the streams...  Which one can't you open?  I can open the first one on the page (the Windows media stream that opens in its own window) using the Totem plugin in Firefox, and I can open the mp3 streams using VLC.

Well i click any of he links and then an d I choose "browse" and find rhythmbox
  and select it to play the stream ,but it doesn't. It plays none of them

---

### Post by ManyBeers on 2008-09-18
> **TeXtonyx said:**
> [http://www.howtogeek.com/howto/linux/installing-flash-player-in-firefox-on-ubuntu-gutsy/](http://www.howtogeek.com/howto/linux/installing-flash-player-in-firefox-on-ubuntu-gutsy/)

That explanation covers the previous version of Ubuntu, but I think the idea of a manual install will work for 8.04 also. Some of the 
commands may require root privileges before they will execute, and often sudo (followed by password) will work. At least its an idea.
Those are audio streams and don't require Flash.

---

### Post by mb_webguy on 2008-09-18
> **ManyBeers said:**
> Well i click any of he links and then an d I choose "browse" and find rhythmbox
  and select it to play the stream ,but it doesn't. It plays none of them

You shouldn't get an "Open with" window when clicking on the first link.  It should open in its own window.  The other Windows media stream should open in the web browser using the Totem plugin, which you apparently have installed.

I'm not familiar with Rhythmbox and its capability to open streams, but the mp3 streams open fine with me using Amarok.  Do you have mp3 support installed on your system?  I think it's in the ubuntu-restricted-extras package.

---

### Post by ManyBeers on 2008-09-18
> **mb_webguy said:**
> You shouldn't get an "Open with" window when clicking on the first link.  It should open in its own window.  The other Windows media stream should open in the web browser using the Totem plugin, which you apparently have installed.

I'm not familiar with Rhythmbox and its capability to open streams, but the mp3 streams open fine with me using Amarok.  Do you have mp3 support installed on your system?  I think it's in the ubuntu-restricted-extras package.
I just installed Ubuntu-restricted-extras but now whiptail is running and it
is causing my processor to run at 100%. Whiptail didplayed a box to 
configure Debian fonts and asked for an ok but when I clicked onthe ok
button nothing happened. So I just closed the Window. I think I needed to
Tab the ok button to flash blue. Because it was flashing Red and maybe that is 
why it wouldn't accept my OK.How do I stop Whiptail? end process or kill process?

---

### Post by mb_webguy on 2008-09-18
First thought:  What the heck is whiptail???

Second thought, after a bit of research:  Why the heck would whiptail be using 100% of your CPU?

Open the terminal and type "killall whiptail" to kill all whiptail processes.  I don't see any reason why installing ubuntu-restricted-extras should have anything to do with whiptail whatsoever.  Whiptail seems to just be a means of producing pop-up GUI messages from the command-line processes.

---

### Post by lswb on 2008-09-18
> **mb_webguy said:**
> First thought:  What the heck is whiptail???

Second thought, after a bit of research:  Why the heck would whiptail be using 100% of your CPU?

Open the terminal and type "killall whiptail" to kill all whiptail processes.  I don't see any reason why installing ubuntu-restricted-extras should have anything to do with whiptail whatsoever.  Whiptail seems to just be a means of producing pop-up GUI messages from the command-line processes.

Some packages use whiptail dialogs to prompt the user for information used for installation.

---

