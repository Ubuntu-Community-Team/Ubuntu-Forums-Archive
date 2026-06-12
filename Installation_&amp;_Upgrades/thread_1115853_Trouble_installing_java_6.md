---
title: "Trouble installing java 6"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by daegan_xavier on 2009-04-04
Hi,

I'm having a hard time getting Java to work.  I've got Ubuntu 8.0.4 and Firefox 3.0.8.  

Here's what I have done:
Using Add/Remove I have installed
Sun Java 6 Runtime
Sun Java 6.0 Plugin

However about:plugins does not show the java plugin - should it?

I followed the instructions here
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

When I run java -version I get this:
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

However when I test if Java is installed at java.com it says that JDE is not working.  

Can anyone help?  I'm muddling my way through the instructions but I am reluctant to embark in more complicated processes as I am definitely a beginner at all this.

Thanks,
Daegan

---

### Post by taurus on 2009-04-04
Are you running i686 or x86_64?

Applications -> Accessories -> Terminal
```
uname -m
```

---

### Post by daegan_xavier on 2009-04-04
I'm running i686.

---

### Post by taurus on 2009-04-04
What's the output of this command from a terminal?

```
sudo apt-get install sun-java6-plugin
```

---

### Post by daegan_xavier on 2009-04-04
Output is:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  fenix libjack0.100.0-0 python-pyogg falconseye-data libaccess-bridge-java
  abe-data openjdk-6-jre-headless libboost-iostreams1.34.1 openjdk-6-jre-lib
  circuslinux-data libcal3d12 egoboo-data libfluidsynth1 libcegui-mk2-1
  fenix-plugins-system rhino libcegui-mk2-dev libboost-filesystem1.34.1
  gamine-data ladcca2 libxerces27 libdevil1c2 libxerces27-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by taurus on 2009-04-04
Do you have a site in mind that requires a java plugin that you can check out (besides the testing site from Sun)?

---

### Post by daegan_xavier on 2009-04-04
[http://thinks.com/daily_crossword.htm](http://thinks.com/daily_crossword.htm)
was the motivating site for realizing that Java wasn't working correctly... and it still isn't.

---

### Post by taurus on 2009-04-04
You did reboot, right?

From firefox address field, type this in and post the output (or screenshot) of it.

```
about:plugins
```

---

### Post by daegan_xavier on 2009-04-04
Actually, I hadn't rebooted (oops!) But I just did, and re-tested the thinks.com site, no luck.

Here's the output of about: plugins

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
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
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r159

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
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

---

### Post by taurus on 2009-04-04
I don't see java plugin anywhere on the list.

---

### Post by daegan_xavier on 2009-04-04
Neither do I, I don't know how to install it. From what I understand with the earlier 'sudo apt-get install sun-java6-plugin' it should be installed?

---

### Post by taurus on 2009-04-04
Yes and so does this (unless you are running x86_64).

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

```
uname -m
```

---

### Post by daegan_xavier on 2009-04-04
I ran the two sudo codes, do you want me to post the results?

uname-m still gives i686.

---

### Post by taurus on 2009-04-04
What's the output of this command?

```
ls -la /usr/lib/mozilla/plugins
```

---

### Post by daegan_xavier on 2009-04-04
It gives:
total 8
drwxr-xr-x 2 root root 4096 2009-04-04 09:27 .
drwxr-xr-x 4 root root 4096 2008-04-22 17:56 ..
lrwxrwxrwx 1 root root   37 2008-10-02 06:42 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   39 2009-04-04 09:27 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so

---

### Post by taurus on 2009-04-04
How about

```
ls -la /usr/lib/firefox/plugins
```

---

### Post by daegan_xavier on 2009-04-04
total 8
drwxr-xr-x 2 root root 4096 2009-04-04 09:27 .
drwxr-xr-x 4 root root 4096 2008-10-02 06:42 ..
lrwxrwxrwx 1 root root   37 2008-10-02 06:42 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root   39 2009-04-04 09:27 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

---

### Post by taurus on 2009-04-04
Did you install firefox from the repos or did you install it by hand?

```
ls -la ~/.mozilla/plugins
```

---

### Post by daegan_xavier on 2009-04-04
It was a work setup computer - I imagine they installed from the repos, but I can't be sure.  

latest result:
ls: cannot access /home/idilia/.mozilla/plugins: No such file or directory

---

### Post by marcha23 on 2009-04-06
I think that symbolic link in /etc/alternatives/mozilla-javaplugin.so is broken. Try to fix it by adding manual. So as I have 64 ubuntu and java 6 u 13 I have to add  sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so /usr/lib64/firefox-addons/plugins/ . 

Then you probably have to do 
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386/libnpjp2.so /usr/lib64/firefox-addons/plugins/ 

Any way suggest you to update java to java 6u13.

---

### Post by daegan_xavier on 2009-04-13
Hi Marcha23 -

I tried the 
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386/libnpjp2.so /usr/lib64/firefox-addons/plugins/ 
as you suggested - no luck on any java sites.
I would love to update to java 6u13, but I've had enough trouble setting  up java here - I took the version from the Add/Remove menu because I was never able to get anything I downloaded from the java site to work.

Perhaps this is just out of my league.

---

### Post by daegan_xavier on 2009-04-30
Quick update - I updated to Jaunty and the plugin was there, no problem.  Thanks to all for your help.

---

