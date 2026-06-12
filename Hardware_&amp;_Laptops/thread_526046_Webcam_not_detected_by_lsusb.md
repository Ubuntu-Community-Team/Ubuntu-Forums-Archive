---
title: "Webcam not detected by lsusb"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by cokhavim on 2007-08-15
My logitech quickcam express webcam is plugged in, the webcam light is on, but lsusb shows no webcam:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

What's even weirder is dmesg (tail end):

[ 1683.304000] usb 2-1: new full speed USB device using ohci_hcd and address 15
[ 1683.484000] usb 2-1: device descriptor read/64, error -62
[ 1683.768000] usb 2-1: device descriptor read/64, error -62
[ 1684.048000] usb 2-1: new full speed USB device using ohci_hcd and address 16
[ 1684.456000] usb 2-1: device not accepting address 16, error -62
[ 1684.632000] usb 2-1: new full speed USB device using ohci_hcd and address 17
[ 1685.040000] usb 2-1: device not accepting address 17, error -62

Not only that, the webcam was detected only a few days ago, and now there's nothing.  My other usb devices are detected with no problems.

What's going on, and how can I fix this? 

Thanks.

---

### Post by w4ett on 2007-08-16
Try to connect the webcam in a different usb port.  Oftentimes, the fix for a disappearing usb device can be as simple as unplugging it and plugging it back in.

---

### Post by cokhavim on 2007-08-16
Nope.  That didn't work.    Please help!

---

### Post by dabl on 2007-08-16
Which version of Ubuntu are you running.  In Edgy, I had to build a gspca driver to use my Logitech QuickCam.  In Feisty, it "just works".  Here's the link to instructions to build your driver, if that's what you need to do:

[http://ubuntuforums.org/showthread.php?t=303330&highlight=howto+webcam](http://ubuntuforums.org/showthread.php?t=303330&highlight=howto+webcam)

---

### Post by w4ett on 2007-08-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77358](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77358) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It's looking to me like a bug in the usb chipset driver, If I'm reading your post and the Bug Reports correctly.

---

### Post by cokhavim on 2007-08-17
i'm using feisty, and i don't have the same problem as that bug report.  my other usb devices are fine.  

I can't use that how-to because it's not a driver problem.  it's that my webcam doesn't even show up on lsusb.

---

### Post by ArchVile on 2007-08-18
I have a similar problem with my logitech quickcam connect. it is detected, gspca nominally handles it, but it just doesn't work. on plugging in, the led flickers shortly, but then it's dead.

```
[ 2235.832000] usb 5-3.1: new full speed USB device using ehci_hcd and address 4
[ 2235.936000] usb 5-3.1: configuration #1 chosen from 1 choice
[ 2235.936000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
```

this occurs both with my via chipset usb pci card and the onboard nvidia usb chipset. however, on my notebook (acer with some older usb chipset), it works fine when plugged in.

so my question is rather: with which usb chipset does it work?

---

### Post by Tibe on 2007-08-18
i have a problem with my acer orbicam(logitech) its on usb in windows
what can i do? help plz
tibe@ubuntu:~$ lsusb
Bus 005 Device 004: ID 5986:0100
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 002: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 004: ID 06b9:4062 Alcatel Telecom
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

---

### Post by ArchVile on 2007-08-18
what IS the problem? maybe you should plug the cam out, then in again, and post the last few lines (maybe 10 if you're not sure which lines are cam-related) of ```
dmesg
``` output. thus we can see whether it is detected at all (and how).

---

### Post by ArchVile on 2007-08-18
well, those who have this or a similar problem with gspca-supported cams could try the pclinuxos live cd. my camera actually WORKS with that. so, the problem is provably fixable. i'll take a look at mod/lib versions in the two distros and post any findings. might take a while, however.

EDIT: this is driving me insane! now, with the feisty amd64 live cd, the cam actually works... i'm installing it right now to check whether it works then, too. (well, it did NOT work with the AMD64 alternate installation i made this afternoon.)

---

### Post by ArchVile on 2007-08-24
to wrap it up: i installed tribe 4 of gutsy (amd64), and the cam worked perfectly. after a few days of occasional use, it stopped working again. lsusb lists it, but the v4l device is simply gone. so far, feisty and gutsy have been a TOTAL mess for me.

---

