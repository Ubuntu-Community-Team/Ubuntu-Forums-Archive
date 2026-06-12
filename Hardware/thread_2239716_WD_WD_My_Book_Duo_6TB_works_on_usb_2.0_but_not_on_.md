---
title: "WD WD My Book Duo 6TB works on usb 2.0 but not on 3.0"
date: 2014-08-15
forum: Hardware
---

### Post by look4terry on 2014-08-15
I see several posts about devices working on usb 2.0 port and not on usb 3.0 but can't seem to find a resolution.  Here is my situation:

[LIST]
[*]Using a Fit Pc3 that has 2 2.0 usb ports and 2 3.0 usb ports.
[*]I've just installed and updated 14.04 server 64 bit.
[*]The device I am using is [WD My Book Duo 6TB dual-drive, high-speed premium RAID storage.]("http://www.amazon.com/gp/product/B00KU686JQ/ref=oh_aui_detailpage_o00_s01?ie=UTF8&psc=1")
[*]I have in plugged into one of the usb 2.0 ports and it is working fine.  Put an entry into /etc/fstab and it mounts on boot.
[*]When I plug it into a 3.0 plug it is not recognized.  /dev/sdb* is not created.  It halts my boot with a prompt since it is not there.  Plugging it in after the boot has the same issue, not recognized.
[/LIST]

Any solution to this?

Thanks,

Terry

---

### Post by em3raldxiii on 2014-08-16
This is not really a fix, but I have read in another forum about USB 3.0 plugs/hubs not providing enough power to the plugged-in device.  Of course, this doesn't apply if the device has an external power adapter.  Anyhoo ... just to rule out a couple of simple things, do you have a shorter or higher-quality USB cable to try?  If you're using a hub, can you try with it plugged directly into the computer?

---

### Post by KY_WD on 2014-08-18
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Hellolook4terry, 

First of all, I would like to ask have the USB 3.0 portsrecognized the WD My Book Duo or any other device before the update14.04 server 64 bit?
 You could try the steps, suggested byem3raldxiii, and change the data cable between the WD My Book andyour Fit Pc3. Have you tried to plug another device to the USB 3.0ports? Does it get recognized? 
Sometimes the drive is not recognizedcorrectly unless USB 3.0 root hub and host controller drivers areinstalled. You could check if they are up to date.
 I also want to askone more thing. Does your My Book Duo get recognized when you plug itinto a USB 3.0 port on another PC?
 Please come and share whathappened. Thank you.

 KY_WD [/FONT][/COLOR]

---

### Post by look4terry on 2014-08-19
Thanks, em3raldxiii, it is a powered drive, I am using the usb cable that came with the drive but good thought.  The cable is a 3.0 cable.  No hub being used.

---

### Post by look4terry on 2014-08-19
> **KY_WD said:**
> [COLOR=#000000][FONT=Ubuntubeta]Hellolook4terry, 

First of all, I would like to ask have the USB 3.0 portsrecognized the WD My Book Duo or any other device before the update14.04 server 64 bit?
 You could try the steps, suggested byem3raldxiii, and change the data cable between the WD My Book andyour Fit Pc3. Have you tried to plug another device to the USB 3.0ports? Does it get recognized? 
Sometimes the drive is not recognizedcorrectly unless USB 3.0 root hub and host controller drivers areinstalled. You could check if they are up to date.
 I also want to askone more thing. Does your My Book Duo get recognized when you plug itinto a USB 3.0 port on another PC?
 Please come and share whathappened. Thank you.

 KY_WD [/FONT][/COLOR]

Thanks KY_WD,

2.0 devices are recognized on the 3.0 ports right now.  This is a new machine, so I suppose it could be hardware on the machine (at least the 3.0 part).

I have not tried a new cable yet.  The drive does work on a 3.0 port on a laptop under Windows.

Since posting this I have found:  [https://bugs.launchpad.net/ubuntu/+bug/1242321 ]("https://bugs.launchpad.net/ubuntu/+bug/1242321")

I'm not sure how to check the root hub and host controller drivers.

Terry

---

