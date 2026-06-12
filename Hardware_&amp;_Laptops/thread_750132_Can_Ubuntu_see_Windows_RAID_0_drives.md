---
title: "Can Ubuntu see Windows RAID 0 drives?"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by ZedMan on 2008-04-09
So I have Ubuntu and Windows on the same hard drive, obviously different partitions. I also have 2 SATA drives set up in RAID 0 where I keep all my media files etc.

I did have to set up the RAID in the BIOS, although I did then partition the drive(s) using the tools in Windows Vista.

Now my question is, what do I need to know/do to allow Ubuntu (actually I'm running Kubuntu, but I'm guessing no different for this situation) to see these drives as a RAID and therefore be able to access the data.

I have a Gigabyte GA-K8N Pro-SLI motherboard, which has Nvidia CK804 SATA RAID drivers. If that helps. Also, I tried to modprobe sata_sil, but that didn't help.

Thanks in advance for any help.

---

### Post by charles_s45 on 2008-04-09
Hi,

I've got the same problem, with an Intel Matrix RAID drive. Tried dmraid, but that doens't work  (yet). Hope someone knows how i can access my existing raid drive from ubuntu.

---

### Post by SirKhan on 2008-04-11
ZedMan if it's a fake raid then you will need to set up with dmraid, then mount the disk with correct parameters (ntfs, etc.). Google fake raid you'll find plenty of solutions for Ubuntu also. I had to do the same for my laptop a few times, it's not hard. GL

---

