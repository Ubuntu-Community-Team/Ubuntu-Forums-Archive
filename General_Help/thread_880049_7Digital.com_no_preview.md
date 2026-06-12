---
title: "7Digital.com no preview"
date: 2008-08-04
forum: General Help
---

### Post by CarlWalters on 2008-08-04
I'm running Ubuntu 8.04 and have previously downloaded .mp3 files through 7digital.com under windows. If I now try to access 7digital.com using Firefox 3.01 under Ubuntu 8.04 I can no longer play any .mp3 previews. I don't know if I'm missing a plugin of some sort (it doesn't complain about it - just doesn't playback anything). Any .mp3s on my hard drive play back OK so I'm a bit confused.

---

### Post by quibbler on 2008-08-05
> **CarlWalters said:**
> I'm running Ubuntu 8.04 and have previously downloaded .mp3 files through 7digital.com under windows. If I now try to access 7digital.com using Firefox 3.01 under Ubuntu 8.04 I can no longer play any .mp3 previews. I don't know if I'm missing a plugin of some sort (it doesn't complain about it - just doesn't playback anything). Any .mp3s on my hard drive play back OK so I'm a bit confused.
type about:plugins in the addressbar in firefox and tell us what plugins you have.

Regards quibbler

---

### Post by quibbler on 2008-08-05
> **CarlWalters said:**
> I'm running Ubuntu 8.04 and have previously downloaded .mp3 files through 7digital.com under windows. If I now try to access 7digital.com using Firefox 3.01 under Ubuntu 8.04 I can no longer play any .mp3 previews. I don't know if I'm missing a plugin of some sort (it doesn't complain about it - just doesn't playback anything). Any .mp3s on my hard drive play back OK so I'm a bit confused.

type about:plugins in the addressbar in firefox and tell us what plugins you have.

Regards quibbler

sorry for the double post

---

### Post by CarlWalters on 2008-08-07
OK - been away for a bit - if I type in about:plugins then I get the information as below (sorry about the formatting). Am I missing something do you think?


```

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes
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
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
```

---

### Post by quibbler on 2008-08-08
It works for me and the only differents in plugins are:
I have java6 plugin and the vlc multimedia plugin.

You can install java through Synaptic manager look for
sun-java6.

You have the vlc plugin (compatable with Totem) but not the vlc plugin from
vlc itself. I take it you don't have the vlc player installed. I do
and it gives you another vlc plugin for multimedia.

You can this also install via Synpatic, look for vlc.

Hope it works.

quibbler

---

