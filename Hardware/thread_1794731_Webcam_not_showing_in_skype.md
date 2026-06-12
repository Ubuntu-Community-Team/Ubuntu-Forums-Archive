---
title: "Webcam not showing in skype"
date: 2011-07-01
forum: Hardware
---

### Post by evilbrent on 2011-07-01
My webcam (logitech quickcam fusion) is located at /dev/video0 and when I run vlc v4l2:///dev/video0 I get actually very good video on my monitor.

But when I test it in Skype I still get a black window.

I looked at the man page and ran some commands which were to fix skype, but I got this:

```
brent@doris:~$ skype-cam-fix
libv4l2: error setting pixformat: Input/output error
libv4l2: error turning on stream: Input/output error
```Anyone know why my webcam might not work in skype in ubuntu 11?.

edt: vlc v4l2:///dev/video0 is giving bad results suddenly.
> 
brent@doris:~$ ls /dev/video*
/dev/video0
brent@doris:~$ vlc v4l2:///dev/video0
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x875a8fc] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1309351464)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4523): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
[0xb730939c] v4l2 demux error: cannot set input (Device or resource busy)
[0xb730939c] v4l2 demux error: cannot set input (Device or resource busy)
[0x8b5232c] v4l2 access error: cannot set input (Device or resource busy)
[0x8b5232c] v4l2 access error: cannot set input (Device or resource busy)
[0xb7305c84] main input error: open of `v4l2:///dev/video0' failed: (null)

---

### Post by helphelp on 2011-07-01
Hi
Open a terminal and type in     LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
It will launch skype with the cam working

---

### Post by evilbrent on 2011-07-01
No luck. Video still tests black in skype

Terminal reads:

```
brent@doris:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
libv4l2: error setting pixformat: Input/output error
libv4l2: error dequeuing buf: Device or resource busy
```

---

### Post by evilbrent on 2011-07-01
scratch that.

works now.

I found instruction to go to system>preferences>main menus: applications>skype>properties and changed the command there to
```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```

loads now with video

---

