---
title: "CD drive won't open in 10.04"
date: 2010-08-01
forum: Hardware
---

### Post by retter on 2010-08-01
I am having trouble with my CD drive in Lucid.  I have looked through many posts that deal with optical drive issues, but in all of them the drive at least opens.  Mine does not.  

I have an HP desktop, AMD Phenom II processor with a Windows 7/Lucid AMD64 partitioned hard drive.  My hp BDDVDRW CH20L drive works fine in the bios and with windows, but it does not appear in Ubuntu, and I can't even get it to open.  I have tried "mount" with several names (dvd, cdrom1, etc.) without success.  No optical drives appear in fstab.  I have tried unplugging and then plugging the drive back in.   USB drives work fine.  

Apologies if this is a repost or in the wrong place.  Thanks for any help,

---

### Post by Gaygerbil on 2010-08-02
Try going to System -> Administration -> Hardware Drivers and seeing if the OS will read a CD drive in the drivers menu. Usually it can just pick up things on its own.

---

### Post by retter on 2010-08-02
The only driver that appears there is the graphics card driver

---

### Post by nyteryder79 on 2010-10-31
Ubuntu 10.04 and 10.10 do not currently have support for your HP blu-ray drive.  I had to disable the SATA port in BIOS on my Pavilion Elite and install Ubuntu from a flash drive.  I submitted a bug and hopefully it gets looked at and addressed soon as this machine is a popular on as is this blu-ray drive.  Right now I'm using an external dvd-rw drive I had for my netbook.

---

### Post by 73ckn797 on 2010-10-31
Does the drive show up under Places/Computer? If so, a right click over the name ought to have the option to "eject".

---

