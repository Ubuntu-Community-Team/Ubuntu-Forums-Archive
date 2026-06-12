---
title: "Permissions in External Drives"
date: 2010-03-16
forum: Hardware
---

### Post by J Bratton on 2010-03-16
Hi- I'm having a bit of difficulty working with an external hard drive. I have music on it, and my music collection is large enough that I need to use an external drive. I have a Squeezebox wireless music networking device. When I go to the part of the software that allows me to choose where the Squeezebox looks for music, the external drive does not show up. 

I suspect it is a problem with permissions. But maybe it is the file structure?

When I right click on the hard drive, and then select- Properties -- Permissions, it shows that the owner can create and delete under the folder access, but under the file access, there are just three dashes. The "others" section of permissions gives folder access as "none" and the three dashes again for file. If I try to use the pulldowns to change permissions, it doesn't "stick"- it immediately reverts to whatever it was, either none or the three dashes. 

Filesystem type is "msdos". This drive was previously used with a Windows Vista computer; most of the files are from that time. The drive mounts fine, and I can in fact add and delete files. I can listen to music using Rhythmbox. I just don't know how to change the permissions so that another device/group/user can access the files (namely, the Squeezebox software). I'm using Karmic Koala. The device appears to be named /dev/sdc

Any help would be greatly appreciated. It all works fine on my internal drive. Thanks!

---

### Post by mikewhatever on 2010-03-16
How does Squeezebox accesses the drive (wireless/USB)?

---

### Post by J Bratton on 2010-03-16
> **mikewhatever said:**
> How does Squeezebox accesses the drive (wireless/USB)?

Wirelessly to a router, which is then plugged in via USB. There is also Squeezebox software on the computer.

---

### Post by mikewhatever on 2010-03-16
> **J Bratton said:**
> Wirelessly to a router, which is then plugged in via USB. There is also Squeezebox software on the computer.

A router is plugged in via USB? Are you sure?

---

### Post by J Bratton on 2010-03-17
> **mikewhatever said:**
> A router is plugged in via USB? Are you sure?

I think I misspoke. It is an Actiontec DSL modem with wireless capability. It was plugged in via ethernet, but with the new setup (internet and phone via cable from comcast), the ethernet plug on the computer is plugged into the cable modem, so the Actiontec modem needed a different way to be plugged in. USB seems to work. Even though it is slower than ethernet, it is good enough for the throughput of music. The DSL modem is only used to provide wireless to the squeezebox, and has no internet function in the new setup.

---

### Post by J Bratton on 2010-03-17
Fixed the problem via the instructions on this page:
[http://wiki.slimdevices.com/index.php/MusicOnLinuxUSBHardDrives](http://wiki.slimdevices.com/index.php/MusicOnLinuxUSBHardDrives)

---

