---
title: "USB 'Security Dongle' aka Pen Drive won't mount . . ."
date: 2008-10-06
forum: Hardware
---

### Post by NewDream on 2008-10-06
uname -a : Linux ubuntu 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
  
I have a Safenet Sentinel ultrapro USB dongle, required for GPS software.  The software is installed in VirtualBox (had some issues there but resolved), and VirtualBox is all good, but the GPS program won't start (because it can't read the dongle).  The dongle essentially contains the licenses.  I called the tech support (they support Windows only, of course) and I'm told it should pop up as an external hard drive in My Computer, and you point the program to the licenses.  Safenet issued drivers for these 'dongles' but only for the 2.5 kernels (definitely don't work for me)  Basically, why can't I find this thing !??!  . . 

Relevant lsusb info:
Bus 001 Device 006: ID 04b9:0300 Rainbow Technologies, Inc. SafeNet USB SuperPro/UltraPro

When I plug it in, dmesg gives:
[17315.136204] usb 1-1: new low speed USB device using ohci_hcd and address 7
[17315.298438] usb 1-1: configuration #1 chosen from 1 choice

. .. but that's it.  I can't find this in /dev, hcitool dev gives nothing, not really sure where else to look.  I could have sworn at one point , maybe the first time I ever plugged it in , it popped up on the desktop for a second.  Anyone have an idea where I can go next ?  Some modules I can unload or reload ?   Really at a loss . . . thanks for reading !  Much appreciated the help !

---

### Post by cariboo on 2008-10-07
Have you had a look here:

[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

the section you want is down near the bottom.

Jim

---

### Post by NewDream on 2008-10-07
caribou - 
  Thanks for the reply.  To be specific, WindowsXP (VirtualBox) Does find the USB dongle, I even have inserted the CD from the company that issued the dongle and it 'installs' with drivers and everything.  But it doesn't install as an external drive (I still can't see what's on it, and it doesn't show up in My Computer).  I can only assume because Ubuntu doesn't see it as a Hard Drive, VitrtualBox won't see it as a Hard Drive.  Google says, basically, that something will work in VirtualBox as long as the drivers in the Host OS support it, and right now I don't think Ubuntu Does. Thanks again for the reply, and, yes, I have completed the USB setup for VirtualBox with those exact instructions.

VirtualBox
Host OS:  Ubuntu Hardy
Guest OS: Windows XP Pro SP3
Problem:  USB Security dongle not seen as a pen drive in either OS (which it's supposed to be) . . I can't mount it

---

### Post by NewDream on 2008-10-07
Thanks for the views - 
  Issue is resolved, I convinced the company to send me an alternative license (one that I could download) as this seems to be a common problem for them.  Thanks again.

---

