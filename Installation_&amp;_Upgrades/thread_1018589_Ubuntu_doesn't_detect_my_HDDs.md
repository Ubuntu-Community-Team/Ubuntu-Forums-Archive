---
title: "Ubuntu doesn't detect my HDDs"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by erobertwald on 2008-12-22
Okay, I've looked around for the past week but can't seem to find anything that's getting me past this problem, despite it being what seems like a common problem...

I am trying to install Ubuntu Server and it isn't detecting either of my hard drives. I tried all the drivers in the list that comes up, to no avail.

This is a brand new install, all parts are straight out of the box. I'm running 64 bit Athlon on an XFX 8200 GeForce board with 4GB ram. The drives are Western Digital Caviar SE16 500GB SATA.

I'd appreciate any help on this. Please bear in mind that the only thing newer than my hardware is my own experience with setting up Linux. This is my first try.

Thanks in advance!

E

---

### Post by namdung on 2008-12-22
Is the BIOS detecting the HDD?

---

### Post by erobertwald on 2008-12-22
Oops. I knew I'd forget a detail.. Yes. BIOS is picking up both HDD.

---

### Post by taurus on 2008-12-22
Do you have a LiveCD handy?  Can you boot from it and then post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by erobertwald on 2008-12-22
Tried booting the LiveCD. Got the status bar and Ubuntu logo, then a prompt that says (initramfs)

---

### Post by erobertwald on 2008-12-22
Okay, did some reading and removed the 'quiet splash' as suggested. Seems to be going through boot now.

---

### Post by erobertwald on 2008-12-22
Tried booting the LiveCD and got a long scroll of data, now a blank screen.

---

### Post by erobertwald on 2008-12-22
Ugh.. Sorry.. Not a blank screen... Gets to [   97.5936231] Uniform CD-ROM driver Revision:3.20 and then the (initramfs) prompt again.

---

### Post by erobertwald on 2008-12-22
Okay, finally made it. Got rid of quiet splash, added iommu=noaperture and als added all_generic_ide at the boot line and got through to the desktop.

Here's the results of sudo fdisk -l:

Disk dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
units=cylinders of 16165 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
units=cylinders of 16165 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by taurus on 2008-12-22
How would you like to partition your new 500GB?  Do you want to have three partitions:  /, /home, & swap?  Open gparted (System -> Administration) from the LiveCD and partition your drive first if you want.  Then when you install it, pick the Manual option and mount one partition as / and the other as /home.  The installer should know what to do with the swap partition.

---

### Post by erobertwald on 2008-12-22
Not exactly sure, maybe you can offer some advice...

I'm going to be running an OpenSim grid from this machine, as well as a wiki and possibly a website. All of these are going to be limited access. It's mainly for collaboration with a friend of mine and experimentation with Linux.

I will also be running Apache, PHP, MySQL and all the other goodies to run this as a server.

Is there a minimum set of partitions, minimum/maximum partition sizes that Ubuntu prefers?

---

### Post by taurus on 2008-12-22
Use gparted from the LiveCD and create three primary partitions (you can only have four primary partitions and if you want more than 4, you need to convert one of those primaries into extended partition and then create a bunch of logical partitions):  one for /, one for /home, and one swap.

/ (root filesystem) = 250GB
/home (where you store all your personal files) = 230GB
swap = 2GB

If you put / and /home partitions next to each other, it would be easier if you need to shrink one partition and give that space to the other.

---

### Post by erobertwald on 2008-12-22
Okay, used gparted and formatted/partitioned both drives identically using the defaults, naming them as you suggested. When I put the install disc in again, still not recognizing any drives and I'm stuck on the driver selection screen again. :(

---

### Post by erobertwald on 2008-12-22
Got frustrated with the server install and opted to try installing from the LiveCD. Everything seemed to go smoothly but now I'm back to getting the aperture warning and then the (initramfs) prompt again.

Any suggestions? This is getting a little frustrating.

---

### Post by erobertwald on 2008-12-25
Still no joy getting the server edition up and running. Can anyone help?

---

### Post by erobertwald on 2008-12-28
Anywhere else I might look or ask about this issue?

---

### Post by erobertwald on 2009-01-24
Okay. Guess it will be a Windows machine after all. Thanks.

---

