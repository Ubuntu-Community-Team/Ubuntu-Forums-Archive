---
title: "xserver-xorg-video-radeon freezes for ATI RV710/M92 [Mobility Radeon HD 4330]"
date: 2013-05-02
forum: Hardware
---

### Post by barna on 2013-05-02
Hi,
Ubuntu 11.10 was the last release that I could install on my Dell Inspiron 1564, with this graphics card:
```

02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710/M92 [Mobility Radeon HD 4330/4350/4550]

```
All releases after 11.10 froze once in 2-3 days, with color stripes on the screen. ATI's proprietary driver fglrx does not anymore support this graphics card, and xserver-xorg-video-radeon is seemingly buggy. 13.04 was worse, it froze already at the login screen. The 'solution' was to remove xserver-xorg-video-radeon, so that the system falls back to vesa, I believe. 

This is already my second notebook with an ATI graphics card, with the same fate (i.e. I can not upgrade the op.system due to problems with the graphics driver xserver-xorg-video-radeon). 

If there is a known workaround, or if there is any way I can feed back useful information, let me know. Otherwise I will go like this, and not buy a computer with an ATI graphics card again. 

BTW the vesa driver is 95% satisfactory (I am using my notebook for work, and not to see fancy window effects). It could output video to HDMI - but I think for this you need to boot your machine with the HDMI already plugged in. When I just tried to plug in the cable when the system was already running, it did not recognize this. The only thing I am lacking is the 'present windows' feature of kde.

---

### Post by Mark Phelps on 2013-05-02
Sorry, nothing newer than 12.04.1 is going to work, not even 12.04.2.  Ubuntu upgraded the X-server version starting with 12.04.2 -- and that version is incompatible with the AMD drivers for video cards older than the HD 5x series.

You should be able to install the AMD restricted drivers with 12.04 -- but if you just grab that these days, you will most likely get 12.04.2 -- which will not work with the restricted (fglrx) drivers.

---

### Post by Yellow Pasque on 2013-05-03
You can still get 12.04.1 here: [http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)
Once 12.04.1 is installed, you have to be careful when updating. You should not install any kernel other than 3.2 and you should not install the xserver-xorg-lts-quantal package (or any xserver-xorg-lts package other than xserver-xorg-lts-precise). That should allow you to use fglrx/Catalyst.

---

### Post by barna on 2013-05-04
Hi, Thanks for the responses. I have now 13.04 running without any problem, after I have removed the xserver-xorg-video-radeon driver. I will live without the fancy effects, and not try to downgrade to some earlier version. And my next notebook will not have an ATI card :-)
Daniel

---

### Post by barna on 2013-05-07
Well, life is not so nice as I thought. Every now and then some programs freeze, they do not respond anymore to mouse or keyboard events. But otherwise the system is running. Newly started programs run fine. Can it also be related to some X problems? What should I check? Thank you.

---

### Post by Bashing-om on 2013-05-07
barna;

In a situation like random freezes it is recommended to examine your log files to get an indication of what is faulting.
Look at /var/log/syslog, /var/log/Xorg.0.log and in your home directory is the hidden log file .xsessions-errors.
[INDENT=2]
just what I would do

[/INDENT]

---

### Post by barna on 2013-05-07
I checked it right after a freeze (which now happens about every half an hour). /var/log/syslog and /var/log/Xorg.0.log do not contain anything suspicious. .xsession-errors might, I don't know (see below).
```

tail  /var/log/syslog
May  7 19:38:54 nbad11 40grub2: debug: parsing: # the 'exec tail' line above.
May  7 19:38:54 nbad11 40grub2: debug: parsing: ### END /etc/grub.d/40_custom ###
May  7 19:38:54 nbad11 40grub2: debug: parsing: 
May  7 19:38:54 nbad11 40grub2: debug: parsing: ### BEGIN /etc/grub.d/41_custom ###
May  7 19:38:54 nbad11 40grub2: debug: parsing: if [ -f  $prefix/custom.cfg ]; then
May  7 19:38:54 nbad11 40grub2: debug: parsing: source $prefix/custom.cfg;
May  7 19:38:54 nbad11 40grub2: debug: parsing: fi
May  7 19:38:54 nbad11 40grub2: debug: parsing: ### END /etc/grub.d/41_custom ###
May  7 19:38:54 nbad11 50mounted-tests: debug: /usr/lib/linux-boot-probes/mounted/40grub2 succeeded
May  7 19:38:54 nbad11 linux-boot-prober: debug: linux detected by /usr/lib/linux-boot-probes/50mounted-tests

```

```

tail -20 /var/log/Xorg.0.log
[ 21029.030] (II) modesetting(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[ 21029.242] (II) modesetting(0): EDID vendor "INL", prod id 10
[ 21029.242] (II) modesetting(0): Printing DDC gathered Modelines:
[ 21029.242] (II) modesetting(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[ 21029.442] (II) modesetting(0): EDID vendor "INL", prod id 10
[ 21029.442] (II) modesetting(0): Printing DDC gathered Modelines:
[ 21029.442] (II) modesetting(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[ 21029.650] (II) modesetting(0): EDID vendor "INL", prod id 10
[ 21029.650] (II) modesetting(0): Printing DDC gathered Modelines:
[ 21029.650] (II) modesetting(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[ 21029.734] (II) modesetting(0): EDID vendor "INL", prod id 10
[ 21029.734] (II) modesetting(0): Printing DDC gathered Modelines:
[ 21029.734] (II) modesetting(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[ 21029.886] (II) modesetting(0): EDID vendor "INL", prod id 10
[ 21029.886] (II) modesetting(0): Printing DDC gathered Modelines:
[ 21029.886] (II) modesetting(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[ 23581.698] (II) modesetting(0): EDID vendor "INL", prod id 10
[ 23581.698] (II) modesetting(0): Printing DDC gathered Modelines:
[ 23581.699] (II) modesetting(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[ 23936.011] (II) XKB: reuse xkmfile /var/lib/xkb/server-AB53A95B759B6F14D2DA04E6F5ECD4E02289A588.xkm

```

```

tail -20 .xsession-errors
polkit_qt_listener_initiate_authentication_finish callback for  0x9856190 
kbuildsycoca4 running...
found error while replying QDBusError("org.freedesktop.DBus.Error.NoReply", "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.") 
plasma-desktop(2019)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
KUrl("file:///home/barna/asacusa/ELENA/extraction-beamline/deflector/one-device-different-angles/Cylindrical-deflector-77.4deg-smooth_bendingangle=77.4deg.pdf") KUrl("") 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Object::connect: No such slot KDEBrowser::teardown()
Object::connect:  (sender name:   'Bookmarks')
This is the current thread id for Activities 2973760320 QThread(0x8a1cb50) 
Object::connect: No such slot KDEBrowser::teardown()
Object::connect:  (sender name:   'Bookmarks')
This is the current thread id for Activities 2973760320 QThread(0x8a1cb50) 

(process:12106): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
plasma-desktop(2019)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
QGridLayoutEngine::addItem: Cell (0, 1) already taken
plasma-desktop(2019)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
plasma-desktop(2019)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 

```

---

### Post by Bashing-om on 2013-05-08
barna;

I do not perceive anything that alarms me... but I do not run KDE (plasma) such that I am not at all familiar with what I should be looking at. (EE's and WW's in the log outputs),
I agree that the QDBussError indicates a condition worthy of investigation; What remote applications are you running such that the system awaits a response from the remote ?
[INDENT=2]
we be look'n

[/INDENT]

---

### Post by barna on 2013-05-08
Hi, nothing as far as I know, but who know what kind of background services are started by these overcomplicated desktop systems. I was probably looking at a local pdf file, maybe editing some C++ source file, that's all.

---

### Post by Bashing-om on 2013-05-08
barna;

Dbus interrupts are a bit over my present knowledge level, but this I find suspicious :
> l("file:///home/barna/asacusa/ELENA/extraction-beamline/deflector/one-device-different-angles/Cylindrical-deflector-77.4deg-smooth_bendingangle=77.4deg.pdf") KUrl("") from the ,xsessions-error log .
Maybe some process you started still trying to source ??? Maybe QThread is related ??
[INDENT]
wiser heads can provide better guidance

[/INDENT]

---

