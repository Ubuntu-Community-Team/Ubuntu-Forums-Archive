---
title: "Problems using vlc 0.9.2 under Kubuntu 710"
date: 2008-09-24
forum: General Help
---

### Post by rrozman on 2008-09-24
Hi,

I desperately need to run newest release of vlc (0.9.2)... On Videolan page it says, that it can be updated via apt-get, but this didn't work for me. Therefore I followed this procedure :
> 
apt-get install autoconf automake build-essential libtool checkinstall libdbus-1-dev libmad0-dev libavcodec-dev libavformat-dev libpostproc-dev liba52-dev libfribidi-dev libqt4-dev

wget [http://vlc.mirrors.adc.am/vlc/0.9.2/vlc-0.9.2.tar.bz2](http://vlc.mirrors.adc.am/vlc/0.9.2/vlc-0.9.2.tar.bz2)

tar jxfv vlc-0.9.2.tar.bz2

cd vlc-0.9.2
./configure --prefix=/usr
make


make install


Now do have few problems :
1. when I run vlc I get those weird errors :
> [00000001] main libvlc warning: could not open plugins cache file /home/tinia/.c
ache/vlc/plugins-04041e.dat for reading
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000026] main module warning: cannot find symbol "vlc_entry__0_9_0m" in file `
/usr/lib/vlc/gui/libncurses_plugin.so' (/usr/lib/vlc/gui/libncurses_plugin.so: u
ndefined symbol: _vlc_entry__0_9_0m)
[00000034] main module warning: cannot find symbol "vlc_entry__0_9_0m" in file `
/usr/lib/vlc/audio_filter/libfloat32tou8_plugin.so' (/usr/lib/vlc/audio_filter/l
ibfloat32tou8_plugin.so: undefined symbol: _vlc_entry__0_9_0m)
[00000057] main module warning: cannot find symbol "vlc_entry__0_9_0m" in file `
/usr/lib/vlc/audio_filter/libs16tofixed32_plugin.so' (/usr/lib/vlc/audio_filter/
libs16tofixed32_plugin.so: undefined symbol: _vlc_entry__0_9_0m)
[00000059] main module warning: cannot find symbol "vlc_entry__0_9_0m" in file `
/usr/lib/vlc/audio_filter/libs16tofloat32_plugin.so' (/usr/lib/vlc/audio_filter/
libs16tofloat32_plugin.so: undefined symbol: _vlc_entry__0_9_0m)
[00000060] main module warning: cannot find symbol "vlc_entry__0_9_0m" in file `
/usr/lib/vlc/audio_filter/libfixed32tos16_plugin.so' (/usr/lib/vlc/audio_filter/
libfixed32tos16_plugin.so: undefined symbol: _vlc_entry__0_9_0m)
[00000061] main module warning: cannot find symbol "vlc_entry__0_9_0m" in file `
/usr/lib/vlc/audio_filter/libs16tofloat32swab_plugin.so' (/usr/lib/vlc/audio_fil
ter/libs16tofloat32swab_plugin.so: undefined symbol: _vlc_entry__0_9_0m)


Anyone got a hint what is wrong ?

2. 0.9.2 release won't let me to run vlc as root. That's probably ok, but now as novice user I do have problems how to run it safely, but still get functionality of RTSP server and other things (it should act as Video On Demand
 server for my local lan - receiving UDP MPEG2 streams and serve them further to my lan via RTSP protocol).

I do this :
```
vlc-wrapper -vvv --color -I Dummy --rtsp-host 0.0.0.0:5554 --vlm-conf /root/Install/VLC/vlm.conf

```
as ordinary user, but it seems that a lot of stuff is "permission denied":
> [00000401] main vod server debug: net: listening to 0.0.0.0 port 5554
[00000401] main vod server error: socket bind error (Permission denied)
[00000401] main vod server error: cannot create socket(s) for HTTP host
[00000404] main http server debug: waitpipe: object killed
[00000401] vod_rtsp vod server error: cannot create RTSP server (0.0.0.0:5554)
[00000401] main vod server debug: TIMER module_Need() : 0.829 ms - Total 0.829 ms / 1 intvls (Avg 0.829 ms)
[00000397] main vlm daemon error: cannot find vod server
[00000397] main vlm daemon error: Load error on line 4: new: could not create media
[00000001] main libvlc warning: error while loading the configuration file


so it seems I still don't have enough permissions to run this application. I did setuid bit on vlc-wrapper binary, but this seems not to be enough...

Is there any guidance how to run vlc as safely as possible, but still get its functionality of VOD server ? VLC team just simply removed root possibility, but I could't find any more info how to run vlc more safely ....

Please be gentle - I'm novice...

Thanks in advance,

regards,
Rob.

---

