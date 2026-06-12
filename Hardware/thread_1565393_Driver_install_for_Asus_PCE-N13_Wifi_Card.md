---
title: "Driver install for Asus PCE-N13 Wifi Card"
date: 2010-08-31
forum: Hardware
---

### Post by vegetarianshrimp on 2010-08-31
Hi all,

I've been having some trouble installing the driver for my new wifi card (see title) in Ubuntu 10.10 Alpha 3 64-bit. I put in the driver CD and went into the "Linux" directory. The driver is a tarball (which I extracted), but for some reason, ./configure, make, and make install aren't working (specifically ./configure, I get "bash: command not found" or something like that).

Any help would be greatly appreciated.
Thanks!
-vegetarianshrimp

P.S. I attached the README file from the driver CD.

---

### Post by vegetarianshrimp on 2010-09-01
bump

---

### Post by vegetarianshrimp on 2010-09-01
bump

---

### Post by vegetarianshrimp on 2010-09-04
anyone!?

---

### Post by dhimmels on 2010-10-06
I am having the same problem with the 64 bit Release Candidate of Ubuntu 10.10 (Maverick Meerkat). In Ubuntu 10.04 the Asus PCE-N13 is automatically detected out of the box and works well. Unfortunately it is not recognized in 10.10 even after updates. I unsuccessfully tried compiling the driver that comes on the CD.

Should I expect this issue to be resolved with the official release, future updates, or kernel upgrades? If I upgrade from 10.04 instead of a clean install of 10.10 will the wireless work?

Thanks!

---

### Post by dhimmels on 2010-10-06
Found a solution on another thread which worked for me:

I had the same problem with this card, but I finally figured it out. Apparently the rt2800/rt2x00 modules are problematic (not mature?). To fix this problem, all I needed to do was blacklist them in /etc/modprobe.d/blacklist.conf

Code:
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

---

### Post by Reishtak on 2011-01-10
My wireless card also doesn't work (same model).  

I tried putting the code into the file suggeted in the post above, and now I have no display output!!!!!

I see the bios and the os select screen, but then the screen goes blank and I hear the umBongos sound effect but no image at all.

Ehh????

---

### Post by SESteve on 2011-03-01
> **dhimmels said:**
> Found a solution on another thread which worked for me:

I had the same problem with this card, but I finally figured it out. Apparently the rt2800/rt2x00 modules are problematic (not mature?). To fix this problem, all I needed to do was blacklist them in /etc/modprobe.d/blacklist.conf

Code:
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

This worked for me with 10.10 on a 64-bit AMD machine. But it doesn't see my 802.11n network, only my 802.11g network.

---

