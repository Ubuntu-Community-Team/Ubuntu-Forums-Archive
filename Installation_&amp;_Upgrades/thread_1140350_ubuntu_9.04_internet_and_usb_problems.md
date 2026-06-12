---
title: "ubuntu 9.04 internet and usb problems"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by _DoMeN_ on 2009-04-27
Hy. I have upgraded from 8.04 to 9.04 32bit ubuntu on both my laptop and my home computer... After that I installed a fresh copy of 9.04 64bit on my laptop and in all the cases I'm experiencing the same problem...

Computer won't connect to the internet ( wireless and lan ) ( 8.04 did right after fresh install ) and it allso doesn't recognise my usb memory stick ( but usb mouse works fine ).

I don't know if it's the same I/O problem or something but its kindof strange seeing all these "no problems with 9.04" posts while I'm having the same problems on both computers...

Any ideas what might be causing this problems?

Thanks,
Domen

---

### Post by _DoMeN_ on 2009-04-28
Ok I managed to establish internet connection after the internet provider updated the software on the switch that they provided years ago.

Stupid of me that I thought that USB and internet problem were related...

Now there is onli the USB problem left... I have testet them a bit more and USB ports work with my external HDD and usb mouse. But when I connect my mp3 player ( old 1GB Philips ) it fails to mount...

With dmesg command I get this at the end of the output:

[FONT=monospace][  508.660016] usb 7-1: new full speed USB device using uhci_hcd and address 2
[  510.288052] usb 7-1: configuration #1 chosen from 1 choice
[  510.398811] Initializing USB Mass Storage driver...
[  510.398948] scsi6 : SCSI emulation for USB Mass Storage devices
[  510.399052] usbcore: registered new interface driver usb-storage
[  510.399055] USB Mass Storage support registered.
[  510.399236] usb-storage: device found at 2
[  510.399238] usb-storage: waiting for device to settle before scanning
[  523.919849] usb 7-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -71
[  531.923103] usb 7-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -71
[  539.926359] usb 7-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -71



Can anyone help me with what this means and possibly provide a way how to resolve this problem.

Thanks in advance,
Domen
[/FONT]

---

### Post by _DoMeN_ on 2009-04-29
Hy, if anyone has the same usb problem I've found the solution that works for me in post
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682)

Using this two commands solves the problem:

sudo killall gvfs-gphoto2-volume-monitor
 sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor




Should this be reported as a 9.04 bug?

---

### Post by divan0 on 2009-05-03
The same thing. I have a laptop Acer Aspire 5100, external HDD and USB mouse plugged in. When I connect USB mp3-player(Sansa Clip 2GB), the kernel says:
[241410.352054] usb 2-1: new full speed USB device using ohci_hcd and address 10
[241410.551248] usb 2-1: not running at top speed; connect to a high speed hub
[241410.578196] usb 2-1: configuration #1 chosen from 1 choice
[241410.612118] scsi9 : SCSI emulation for USB Mass Storage devices
[241410.614139] usb-storage: device found at 10
[241410.614147] usb-storage: waiting for device to settle before scanning
[241419.352254] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -110
[241427.352265] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -110
[241435.352270] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -110
[244491.476125] usb 2-1: USB disconnect, address 10
[244494.136055] usb 1-1: new high speed USB device using ehci_hcd and address 14
[244509.248054] usb 1-1: device descriptor read/64, error -110

The suggested method
> sudo killall gvfs-gphoto2-volume-monitor
 sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
solved problem for me as well. I do think it's a bug.

---

### Post by TomG on 2009-05-13
Also works for me.
Great Thanks !

---

### Post by mad_max0204 on 2009-05-17
WOW nice work. I was already going nuts with my mp3 player.

Thanks for the info

---

### Post by snaga on 2009-05-19
Once again the Ubuntu forums solve a maddening issue for me. Thanks!

---

### Post by sigmazero13 on 2009-06-03
I've been having a similar problem with my phone (which acts as an MP3 player).  I tried the steps above, and now the phone doesn't mount at all when I plug it in.

This worked fine in 8.10, but not in 9.04.

Any idea how to manually mount my phone?

---

### Post by snaga on 2009-06-03
The first thing I do when I have problems like this is tail /var/log/messages and see if what I am plugging in is getting assigned a device. Unplug the device, tail -f /var/log/messages , then plug it back in. If you can see that its getting a device, then you can do a manual mount. 

mount /dev/<device> /media/<directory I created>

---

### Post by icheyne on 2009-06-20
These problems are due to USB mode issues. Try using [MTP mode]("https://help.ubuntu.com/9.04/musicvideophotos/C/music-portable.html").

I wrote some Sansa Clip instructions [here]("https://help.ubuntu.com/community/SansaClip").

---

### Post by emada on 2009-07-13
> **_DoMeN_ said:**
> Hy, if anyone has the same usb problem I've found the solution that works for me in post
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682)

Using this two commands solves the problem:

sudo killall gvfs-gphoto2-volume-monitor
 sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor




Should this be reported as a 9.04 bug?

worked for me tyvm

---

### Post by Aemaeth on 2009-11-09
Exactly right Icheyne, good call. All issues that I had encountered were linked to the default usb mode setting. apparently the auto config setting for the sansa player does not work well with jaunty or karmic...

Cheers!

---

### Post by Loevborg on 2011-10-03
Just a note that on all my current Ubuntu 10.10 installations, the SanDisk Sansa Clip 2GB failed to mount, even though it worked fine on a Mac. dmesg was giving me:

[INDENT][  970.740048] usb 1-1: device descriptor read/64, error -110
[  985.956031] usb 1-1: device descriptor read/64, error -110
[  986.172021] usb 1-1: reset high speed USB device using ehci_hcd and address 16[/INDENT]

The method above, disabling gvfs-gphoto2-volume-monitor, note in the post [http://ubuntuforums.org/showpost.php?p=7173964&postcount=3](http://ubuntuforums.org/showpost.php?p=7173964&postcount=3) worked perfectly. So apparently this has to do with gphoto volume monitor. I can't remember if I updated the firmware or changed the settings when I bought the mp3 player, a few years ago. In any case, many thanks to the reporters.

---

