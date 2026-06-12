---
title: "Firefox not loading"
date: 2008-07-11
forum: General Help
---

### Post by hopefull on 2008-07-11
HI

The problem that I have is that when I click on firefox I get the following message and firefox does not load:

Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system

No processes appear to be working, form what I can see, and I have restarted and the same problem continues. The cause of the problem is probably a failed attempted to install Tor. Any suggestions on how to shut firefox down from command line etc

Cheers

Hopefull

---

### Post by tuxxy on 2008-07-11
run terminal > killall firefox

now open Firefox

Also I recommend Opera, atleast worth a try :)

---

### Post by hopefull on 2008-07-11
dear Tuxxy

Tried killall and nothig has happened?
Opera is a good alternativ, though I cannot get it to play music from the BBC website, but I need to really access the bookmarks I have on Firefox

Hopefull

---

### Post by tuxxy on 2008-07-11
type at the prompt;

aid@Ubuntu~$ killall firefox

In firefox type about: plugins (no spaces) into browser address bar and paste the output please ;)

If you wanna do it in Opera type Opera: Plugins

---

### Post by MasterXandrex on 2008-07-11
Try 
```

sudo killall firefox

```
it may be running as a different user for some reason.

Also, if all else fails and you need Firefox right now run it with the no-remote flag and start a new instance.

```

firefox --no-remote

```


Xan

---

### Post by hopefull on 2008-07-12
Tuxxy

Cannot do that in firefox because I cannot run it. for Opera here is the read out:

Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/flashplugin-nonfree/libflashplayer.so

QuickTime Plug-in 6.0 / 7video/quicktime	qt,mov
video/x-quicktime
image/x-quicktime
application/x-quicktimeplayer
/usr/lib/mozilla/plugins/gecko-mediaplayer-qt.so

Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/flashplugin-alternative.so

Windows Media Player Plug-in*/*	*
audio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi
application/asx	
video/x-ms-asf-plugin	
application/x-mplayer2	
video/x-ms-wm	wm
audio/x-ms-wma	wma
audio/x-ms-wax	wax
video/x-ms-wvx	wvx
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
video/msvideo
application/x-ms-wmv
audio/x-ms-wmv
video/x-ms-wmp
application/x-ms-wmp
application/x-drm-v2
/usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so

DivX Browser Plug-Invideo/divx
video/vnd.divx
/usr/lib/mozilla/plugins/gecko-mediaplayer-dvx.so

RealPlayer 9application/x-rpm	rpm
application/smil	smi,smil
application/x-pn-realmedia	rm
audio/x-pn-realaudio	ram,ra
video/vnd.rn-realvideo	rv
application/vnd.rn-realmedia
application/vnd.rn-realaudio
audio/x-realaudio
audio/x-pn-realaudio-plugin
/usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so

gecko-mediaplayer 0.6.0video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
video/mp4	mp4,mpg4
audio/mpeg	mp3,mp2,mpga
audio/mp3	mp3
audio/x-mpegurl	m3u
audio/basic	au
audio/midi	midi,mid
video/3gpp	3gp
video/x-mpeg
video/x-mpeg2
audio/x-mpeg
audio/mpeg2
audio/x-mpeg2
video/x-m4v
audio/mpeg3
audio/x-mpeg3
application/x-ogg
audio/ogg
audio/x-ogg
application/ogg
audio/flac
audio/x-flac
video/fli
video/x-fli
video/x-flv
video/vnd.vivo
application/x-nsv-vp3-mp3
audio/x-mod
audio/x-basic
audio/x-scpls
/usr/lib/mozilla/plugins/gecko-mediaplayer.so

Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/iceweasel/plugins/flashplugin-alternative.so

QuickTime Plug-in 6.0 / 7video/quicktime	qt,mov
video/x-quicktime
image/x-quicktime
application/x-quicktimeplayer
/usr/lib/iceape/plugins/gecko-mediaplayer-qt.so

Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/iceape/plugins/flashplugin-alternative.so

Windows Media Player Plug-inaudio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi
application/asx	
video/x-ms-asf-plugin	
application/x-mplayer2	
video/x-ms-wm	wm
audio/x-ms-wma	wma
audio/x-ms-wax	wax
video/x-ms-wvx	wvx
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
video/msvideo
application/x-ms-wmv
audio/x-ms-wmv
video/x-ms-wmp
application/x-ms-wmp
application/x-drm-v2
/usr/lib/iceape/plugins/gecko-mediaplayer-wmp.so

DivX Browser Plug-Invideo/divx
video/vnd.divx
/usr/lib/iceape/plugins/gecko-mediaplayer-dvx.so

RealPlayer 9application/smil	smi,smil
audio/x-pn-realaudio	ram,ra
video/vnd.rn-realvideo	rv
application/vnd.rn-realmedia
application/vnd.rn-realaudio
audio/x-realaudio
audio/x-pn-realaudio-plugin
/usr/lib/iceape/plugins/gecko-mediaplayer-rm.so

gecko-mediaplayer 0.6.0video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
video/mp4	mp4,mpg4
audio/mpeg	mp3,mp2,mpga
audio/mp3	mp3
audio/x-mpegurl	m3u
audio/basic	au
audio/midi	midi,mid
video/3gpp	3gp
video/x-mpeg
video/x-mpeg2
audio/x-mpeg
audio/mpeg2
audio/x-mpeg2
video/x-m4v
audio/mpeg3
audio/x-mpeg3
application/x-ogg
audio/ogg
audio/x-ogg
application/ogg
audio/flac
audio/x-flac
video/fli
video/x-fli
video/x-flv
video/vnd.vivo
application/x-nsv-vp3-mp3
audio/x-mod
audio/x-basic
audio/x-scpls
/usr/lib/iceape/plugins/gecko-mediaplayer.so

QuickTime Plug-in 6.0 / 7video/quicktime	qt,mov
video/x-quicktime
image/x-quicktime
application/x-quicktimeplayer
/usr/lib/firefox/plugins/gecko-mediaplayer-qt.so

Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/firefox/plugins/flashplugin-alternative.so

Windows Media Player Plug-inaudio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi
application/asx	
video/x-ms-asf-plugin	
application/x-mplayer2	
video/x-ms-wm	wm
audio/x-ms-wma	wma
audio/x-ms-wax	wax
video/x-ms-wvx	wvx
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
video/msvideo
application/x-ms-wmv
audio/x-ms-wmv
video/x-ms-wmp
application/x-ms-wmp
application/x-drm-v2
/usr/lib/firefox/plugins/gecko-mediaplayer-wmp.so

DivX Browser Plug-Invideo/divx
video/vnd.divx
/usr/lib/firefox/plugins/gecko-mediaplayer-dvx.so

RealPlayer 9application/smil	smi,smil
audio/x-pn-realaudio	ram,ra
video/vnd.rn-realvideo	rv
application/vnd.rn-realmedia
application/vnd.rn-realaudio
audio/x-realaudio
audio/x-pn-realaudio-plugin
/usr/lib/firefox/plugins/gecko-mediaplayer-rm.so

gecko-mediaplayer 0.6.0video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
video/mp4	mp4,mpg4
audio/mpeg	mp3,mp2,mpga
audio/mp3	mp3
audio/x-mpegurl	m3u
audio/basic	au
audio/midi	midi,mid
video/3gpp	3gp
video/x-mpeg
video/x-mpeg2
audio/x-mpeg
audio/mpeg2
audio/x-mpeg2
video/x-m4v
audio/mpeg3
audio/x-mpeg3
application/x-ogg
audio/ogg
audio/x-ogg
application/ogg
audio/flac
audio/x-flac
video/fli
video/x-fli
video/x-flv
video/vnd.vivo
application/x-nsv-vp3-mp3
audio/x-mod
audio/x-basic
audio/x-scpls
/usr/lib/firefox/plugins/gecko-mediaplayer.so

---

### Post by hopefull on 2008-07-12
MasterXandrex

I tried your suggestions but nothing happened.

---

### Post by drs305 on 2008-07-12
Run this command to try to find the file which shows firefox is running. Adjust the directory if the firefox profile is not somewhere on your root partition. If you find the file 'parentlock', delete it:
```
sudo find / -type f -iname .parentlock
```

---

