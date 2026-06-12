---
title: "Internet adapter intstallation problem?"
date: 2012-02-19
forum: Hardware
---

### Post by bbno3 on 2012-02-19
I brought a Netgear n150 wireless adapter for ubuntu 11.0 but after putting in the driver disk*uh oh...* it appears the disk is windows only, i have tryed to run it in wine and i get back "access denied" when i installed it in windows it worked, and didn't say access denied, i have the feeling that the disk is windows only..

I am using Ubuntu 11.10 64bit. Please help. :confused:

---

### Post by grahammechanical on 2012-02-19
First of all drivers for hardware devices being used in the Windows operating system will not work on a Linux operating system any more than a Windows program would work on Linux.

Second, it might be possible for some windows programs to work when run through the wine program but not device drivers. The wine program does not directly access the hardware.

Here are a couple of links

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

[https://answers.launchpad.net/ubuntu/+source/ndisgtk/+question/151449]("https://answers.launchpad.net/ubuntu/+source/ndisgtk/+question/151449")

Regards.

---

### Post by dandnsmith on 2012-02-20
How about trying for ndiswrap, since you have it working under Windows?

---

