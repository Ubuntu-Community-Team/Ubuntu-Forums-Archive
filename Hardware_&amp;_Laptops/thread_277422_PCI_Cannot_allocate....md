---
title: "PCI: Cannot allocate..."
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by Jerrac on 2006-10-14
I just added a ten gig hard drive to my system. When I try to boot up, it hangs right after mounting the root file system. Then it says something along the lines of > "[4294671.152000] PCI: Cannot allocate resource region 3 of device 0000:05:0 ALERT! /dev/hda3 does not exist. Dropping to a shell!" I also installed Windows XP pro on the small disk while I had the linux disk disconnected. 

I have the disk with ubuntu installed as the master and the ten gig as the slave, set to cable select. 

So, what can I do?

---

### Post by Jerrac on 2006-10-14
OK, well, I got it working. Had to switch the ports the ide cables were plugged into on the motherboard. Go figure.

Now I just need to figure out what to put in grub to allow me to boot to the second hard disk.

---

### Post by MrSoussey on 2007-01-14
try a bios update... worked for me

---

