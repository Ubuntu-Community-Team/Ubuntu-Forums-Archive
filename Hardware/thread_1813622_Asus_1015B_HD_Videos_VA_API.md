---
title: "Asus 1015B HD Videos VA API"
date: 2011-07-28
forum: Hardware
---

### Post by helixum on 2011-07-28
Hi 

I installed today xubuntu on my new Asus eeePC 1015B 
and have only this one mayor issue left.
(Sorry for the double post the first one was in the wrong section)

Could not get the HD playback wokring right now.
in the 1015B there is a ATI HD6250 build in

I installed the properitay driver 11.7 Catalyst.
(followed the Ubuntu Natty Installation Guide from [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)) 

Then I installed libva1 from PPA: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
and its modified vlc player. Also installed [http://www.splitted-desktop.com/~gbe...8.0-1_i386.deb](http://www.splitted-desktop.com/~gbe...8.0-1_i386.deb)

When playing a Video my CPU goes to 100 so I guess the hardware acceleration does not work..
```

vlc --ffmpeg-hw
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8845914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setenv("ORBIT_SOCKETDIR", "/tmp/orbit-cmp", 1)
Warning: call to srand(1312055660)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:5447): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
xvba_video: XVBA_GetSurface(): status 2
[0x8cc793c] avcodec decoder: Using VA API version 0.32 for hardware decoding.
[0x88e0544] signals interface error: signal 17 overriden (0x3af14c0)
[0x88e0544] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
...

```

Xorg.log has no errors in it.
VLC has its option set to use Hardware acceleration. 
What can I do?

---

