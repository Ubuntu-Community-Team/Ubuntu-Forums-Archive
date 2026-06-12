---
title: "Lenovo EasyCamera I/O error. (12.04 LTS)"
date: 2013-09-15
forum: Hardware
---

### Post by roelf2 on 2013-09-15
Hello,

I have an Lenovo Ideapad Y500 running 12.04.3 (using the xorg-server (because the nvidia driver won't work properly otherwise) and linux-image-generic (so the non-lts/mainline stuff)).
Other than having to install the binary nvidia driver (the OSS one wasn't picking up on my external screen), I've never had to install any extra driver.
Today, after running this thing for months with Ubuntu, I've had the need to use the webcam for a videoconference (rare occasion).
Fired up my conference software and... no image.
Same for cheese and vlc.
So I decided to check the command line.
All programs have one thing in common, this error:
libv4l2: error turning on stream: Input/output error
I've tried the LD_PRELOAD=/usr/lib/...compat.so trick (can't be bothered to copy & paste that because it's really long)
I've installed the mainline kernel because some google-fu said that it might work (it did fix something unrelated, I can now (finally) use my usb keyboard to login).

Now for some info:
```

$ lsusb
roelf@laptop02:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 04f2:b331 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 050d:0119 Belkin Components F5U120-PC Dual PS/2 Ports / F5U118-UNV ADB Adapter
Bus 001 Device 004: ID 0cf3:3004 Atheros Communications, Inc.
roelf@laptop02:~$ cheese

(cheese:22115): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:22115): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:22115): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:22115): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:22115): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:22115): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel
libv4l2: error turning on stream: Input/output error

** (cheese:22115): WARNING **: Error starting streaming on device '/dev/video0'.


** (cheese:22115): WARNING **: Could not negotiate format
^C
roelf@laptop02:~$ ls /dev/video*
/dev/video0
roelf@laptop02:~$ uname -a
Linux laptop02 3.5.0-40-generic #62~precise1-Ubuntu SMP Fri Aug 23 17:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
roelf@laptop02:~$ luvcview
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: MJPG
  Frame size:   640x480
  Frame rate:   30 fps
libv4l2: error turning on stream: Input/output error
Unable to start capture: Input/output error
Error grabbing
Cleanup done. Exiting ...

```
(Sorry for the length, this forum doesn't support spoilers or other ways of hiding long waths of text)

The only thing I haven't tried was something called gspca (and only because I couldn't find any documentation).
For now I'm stuck using a crappy <240p usb camera that doesn't focus properly (never has).

Can somebody help?

PS. I'm not a new user, but my old account got stuck in the move to SSO (even though I used it with SSO before the move). So yeah. The forum software assigned me this account.

---

