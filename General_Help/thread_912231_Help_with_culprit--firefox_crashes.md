---
title: "Help with culprit--firefox crashes"
date: 2008-09-06
forum: General Help
---

### Post by clnanderson on 2008-09-06
I'm trying to figure out where to go with a bug report. Firefox randomly crashes on actions like loading webpage, scrolling webpages etc. I just don't know what I'm looking at in the output below and would appreciate any help in filing a bug.

I'm running Kubuntu Hardy fully updated and KDE 4.1.1

Firefox is 3.0.1+build1+nobinonly-0ubuntu0.8.04.3

looks like 

nvidia drivers 169.12+2.6.24.13-19.45  
xserver-xorg                               1:7.3+10ubuntu10.2              r
xserver-xorg-core                          2:1.4.1~git20080131-1ubuntu9.2  
                        
This is the output after the fairly random crashes

The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 1530868 error_code 182 request_code 157 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb64c1767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb64c181e]
#2 /usr/lib/libX11.so.6 [0xb6a48518]
#3 /usr/lib/libXrender.so.1(XRenderFreePicture+0x41) [0xb6af3ce1]
#4 /usr/lib/libQtGui.so.4 [0xb42ae457]
#5 /usr/lib/libQtGui.so.4 [0xb42ae87d]
#6 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x5b) [0xb42a45cb]
#7 /usr/lib/libQtGui.so.4(_ZN7QPixmapD2Ev+0x30) [0xb42a4e60]
#8 /usr/lib/libQtGui.so.4 [0xb42a952a]
#9 /usr/lib/libQtGui.so.4 [0xb42a9f32]
#10 /usr/lib/libQtGui.so.4 [0xb42a8606]
#11 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7c8f084]
#12 /usr/lib/libgdk-x11-2.0.so.0 [0xb662e637]
#13 /usr/lib/libbonoboui-2.so.0 [0xb6246665]
#14 /usr/lib/libX11.so.6(_XError+0xfe) [0xb6a4173e]
#15 /usr/lib/libX11.so.6 [0xb6a48e5c]
#16 /usr/lib/libX11.so.6(_XReply+0x15a) [0xb6a4921a]
#17 /usr/lib/libX11.so.6(XGetGeometry+0x70) [0xb6a263d0]
#18 /usr/lib/libgdk-x11-2.0.so.0(gdk_pixmap_foreign_new_for_display+0x8f) [0xb662f3ff]
#19 /usr/lib/libgdk-x11-2.0.so.0(gdk_pixmap_foreign_new+0x1a) [0xb662f48a]

---

### Post by forger on 2008-09-06
As the message says, can you run:
```
firefox --sync 
```

> To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)

Also, check if there are any crash reports in /var/crash/ directory:
```
dir /var/crash/
sudo dir /var/crash/
```

---

### Post by clnanderson on 2008-09-06
I tried that. It didn't generate anything that I could find. The same message was spat out and the program stopped responding rather than completely shut down. 

Where would I look for the results of the --sync flag?

---

### Post by forger on 2008-09-06
well.. logically that should be it, try report your bug and visit #ubuntu-bugs on IRC (network freenode)- ask if they need more information

---

### Post by bingoUV on 2008-09-06
Before reporting a bug, verify that the same problem surfaces when you run firefox in safe mode. Close firefox windows, and run this from a terminal

```

firefox -safe-mode

```

Try it for some time and tell if it crashes.

---

