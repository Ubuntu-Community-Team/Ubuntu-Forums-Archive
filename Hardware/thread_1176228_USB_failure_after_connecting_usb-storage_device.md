---
title: "USB failure after connecting usb-storage device"
date: 2009-06-02
forum: Hardware
---

### Post by golemix on 2009-06-02
Hi!

I bought and mounted a new desktop computer a few days ago and installed Ubuntu (Jaunty Jackalope). The problem is that when I plug a usb-storage device (tried with digital camera and a flashdrive) my other usb devices become unoperable (sometimes it's mouse, the other time it's keyboard). It happens just a few seconds after I plug the usb-storage device - at the beginning averything seems to be OK, the device is detected and mounted, I can access the files - but then my usb mouse (or keyboard) stops functioning and every program that tries accessing the usb drive hangs - and it can't be killed even by "kill -9". When I run "lsusb" it still says that the usb-storage device is connected, but after removing the device the things get worse and then even "lsusb" hangs every time I run it. Then it is time to hard-reset the system because it can't even reboot. 

I already tried to disable USB 2.0 controller leaving only USB 1.1 on in BIOS configuration but it didn't help.

My hardware:
 Asus M3N78-VM GeForce 8200 / AMD Phenom Quad-Core 9650

I attach the output of dmesg, which (I think) looks OK:
```
...
[ 4627.636270] usb 2-5: new full speed USB device using ohci_hcd and address 3
[ 4627.852732] usb 2-5: configuration #1 chosen from 1 choice
[ 4627.905722] Initializing USB Mass Storage driver...
[ 4627.905916] scsi6 : SCSI emulation for USB Mass Storage devices
[ 4627.906040] usb-storage: device found at 3
[ 4627.906046] usb-storage: waiting for device to settle before scanning
[ 4627.906051] usbcore: registered new interface driver usb-storage
[ 4627.906056] USB Mass Storage support registered.
[ 4632.906189] usb-storage: device scan complete
[ 4632.913168] scsi 6:0:0:0: Direct-Access     MSI      MS-551X          0001 PQ: 0 ANSI: 4
[ 4632.929159] sd 6:0:0:0: [sdb] 250880 512-byte hardware sectors: (128 MB/122 MiB)
[ 4632.936143] sd 6:0:0:0: [sdb] Write Protect is off
[ 4632.936147] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 04
[ 4632.936151] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4632.963212] sd 6:0:0:0: [sdb] 250880 512-byte hardware sectors: (128 MB/122 MiB)
[ 4632.970353] sd 6:0:0:0: [sdb] Write Protect is off
[ 4632.970358] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 04
[ 4632.970361] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4632.970370]  sdb: sdb1
[ 4632.980349] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 4632.980444] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 5209.065047] usb 2-5: USB disconnect, address 3
```Any ideas how can I fix that?
THX

---

### Post by yarko on 2009-06-08
I too just setup a Asus M3N78 Pro, with a Phenom x4 (9500 in my case).

I've tried several installs, and played w/ bios settings a bit... (I did _not_ try upgrading or downgrading the bios - leaving this for last ditch efforts).

Most of the threads, hints on this I've decided to watch but ignore for this simple reaason:

Fedora-11 amd64 live-disk worked for a long time, including w/ various usb drives attached / detached / mounted / tested; on installation of Fedora 11, upgrades, networks, etc. all seem to be alive and well.

I've looked thru logs and messages ... (logs have something about complaining to bios vendor).  Bottom line:  the board works w/ Linux (I would have tried Fedora 10, but 11 is out in 2 days...).

This tells me one thing:  The board / chipset works (the first update of 158 packages while watching the system monitor was interesting ... looked good).  Now - what is Fedora doing that is significant that Ubuntu is not; that's the question.

- Yarko

---

### Post by yarko on 2009-06-10
A little more insight / info:

somewhere I saw a comment from someone that the 403 bios worked for them;

- I tried the following:

- bios 0403 + ubuntu-64 live;   no screen display for x;
- bios 0701 + ubuntu-64 live;   this was my mobo default: usb problems;
- bios 1003 + ubuntu64 live:   usb problems go away;  networking locks up after a short time;

- bios 1003 + ubuntu (usb boot of "my config" w/ 32 bit) - boot hangs 1/2 way.

----  Fedora11 preview still runs "forever", w/ bios1003 (and 703)

Boot log and dmsg viewable here:

[http://docs.google.com/View?id=dcv3z6cp_296gm38hhgq](http://docs.google.com/View?id=dcv3z6cp_296gm38hhgq)
[http://docs.google.com/View?id=dcv3z6cp_297gmd5cwfx](http://docs.google.com/View?id=dcv3z6cp_297gmd5cwfx)

---

