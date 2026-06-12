---
title: "How to release USB device?"
date: 2010-12-13
forum: Hardware
---

### Post by rijidij on 2010-12-13
I'm trying to use my Line6 PODxt under TinyXP running in a VirtualBox machine.
The PODxt shows up in a list of USB devices, but is greyed out because it is still connected in the host (Linux) system.
How do I release a USB device in Linux so I can use it on the client (TinyXP) machine?

Thanks.

---

### Post by daqron on 2010-12-30
Well, stupid question, but you've tried unmounting it using umount or the "eject" icon in Nautilus? In my experience it is not necessary to do this, though. When I had the grayed-out device problem it was because I hadn't installed the [4.0 Extension Packs]("http://forums.virtualbox.org/viewtopic.php?f=24&p=164806"). I also had to create a [USB device filter]("http://itknowledgeexchange.techtarget.com/server-virtualization/using-usb-device-filters-with-sun-xvm-virtualbox/") for my device. Now, whenever my Windows guest loads in VB, it takes over the USB device, and when I exit VB the device re-mounts in Ubuntu.

Hope that helps.

---

