---
title: "USB devices hanging"
date: 2014-01-20
forum: Hardware
---

### Post by lz1dsb on 2014-01-20
I'm running an Ubuntu 12.04 with kernel 3.2.0-58-generic. 
Recently I've noticed that from time to the devices connected to the USB ports of my laptop stuck! What do I mean by that. For example a smart card reader I use, does not work. I also found that Firefox does not launch because of USB card reader that is stuck. So, what happens when I plug it off, I still can see it in the output of the command lsusb!! 
With the USB mouse I use it's a little bit different, it works, but when this happens with the reader, the moment I plug it off, it's not recognizable anymore. And even if it's plugged off, I can still see an entry for it in the lsusb output!
Has anyone come across a similar issue? Is there a way on how to troubleshoot that?

---

### Post by lz1dsb on 2014-01-21
Bump... 
I've noticed this again today. It seems like after the machine has worked for several hours, the USB interface get stuck. The USB mouse is again showing the same behavior, it works without any issues but when I plug it off, it does not work anymore. Listing all USB devices with lsusb shows USB devices which are no longer connected! When this issue happens, connecting new USB devices does not work at all, no matter of the type. 
The only workaround I have found so far is to reboot the system...

---

### Post by lz1dsb on 2014-01-30
It just happened again today. I tried udevadm monitor... But strange enough, it does not output any kernel message when a USB device is plugged in or out. It's the same with udevd, I also checked the loggs, nothing related to USB. 
Does that mean that there's something terribly wrong with udev on my system? it's like at some point, the external USB devices are not recognized anymore...

---

