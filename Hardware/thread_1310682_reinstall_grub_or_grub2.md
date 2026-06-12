---
title: "reinstall grub or grub2"
date: 2009-11-02
forum: Hardware
---

### Post by jarrah-95 on 2009-11-02
i have recently installed karmic and i used to have grub2 but now it gives me gurb1 when o try to boot and it wont boot ubuntu. i have tryed super grub and all it has done is given me the boot: prompt witch doesnt help.i can boot from a live cd but only the 9.04 one
thanks

---

### Post by kohei on 2009-12-10
> **jarrah-95 said:**
> i have recently installed karmic and i used to have grub2 but now it gives me gurb1 when o try to boot and it wont boot ubuntu. i have tryed super grub and all it has done is given me the boot: prompt witch doesnt help.i can boot from a live cd but only the 9.04 one
thanks

I had a problem with grub (i installed grub in primary master disk mbr and xubuntu in
a slave disk partition, but i lost grub after windows re-installation) and i didn't boot 
xubuntu again after grub reinstallation (it seems that grub can't detect slave disk via
some BIOS service).  Nevertheless i have could to run xubuntu again booting from floppy
disk with a supergrub image that i copied into it (you can google 'supergrubdisk' and you
must find it)

---

