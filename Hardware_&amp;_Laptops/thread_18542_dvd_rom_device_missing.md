---
title: "dvd rom device missing"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by llama on 2005-03-07
hi i wonder if anyone can help me out.

i have two ide dvd drives master and slave on ide0, an ide HD master on ide1 and a sata HD master on ide2 (enhanced mode in BIOS, tried installs with it as a seperate RAID controller but the same problem occurs)

worty is installed on the IDE HD, and XP on the SATA both boot fine from GRUB.

the IDE HD is /dev/hdc, the second dvd is /dev/hda and the SATA HD is /dev/sde.
the problem is the first IDE dvd rom (master on ide0) doesnt show as a device. so i can't mount it. kinda stage as thats the drive i install ubuntu from.

im guessing its a udev problem? but i dont really know anything about the device rules etc..

the motherboard is a Abit AI7 (i865 chipset) if thats any help.

---

### Post by llama on 2005-03-08
ok i fixed it. i turned the drive off in the BIOS.. now its detected fine in ubuntu and windows. very strange...

---

