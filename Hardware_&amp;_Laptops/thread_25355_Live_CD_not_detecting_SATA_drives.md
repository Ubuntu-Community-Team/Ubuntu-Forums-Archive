---
title: "Live CD not detecting SATA drives"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by Jump on 2005-04-09
I'm a complete Linux newbie so I have no idea how to fix this. I'll start with some specs:

MSI K8N Neo2 Platinum S939 (Chipset: nForce3 ULTRA)
AMD 64 3500+ S939 90nm
2X200GB Seagate SATA HDD 8MB 7200RPM

My CD ROM and DVD ROM show up on the desktop. It also shows New Volume which is an external USB drive I have.

I've also tried the Knoppix LiveCD and it detects both drives no problem. Something about Ubuntu just doesn't want to recognize these drives. I assume installing the distro will be impossible until I can resolve this.

Again, I'm a total newbie here so I'm probably doing something wrong.

---

### Post by Jump on 2005-04-10
Actually I tried sudo fdisk -l and it does show up. Is it possible to mount the drive using the Live CD?

---

### Post by jobezone on 2005-04-10
This is a trick I use. 
Boot from the LiveCD, which automatically configures fstab for your other partitions(Warty live cd does, haven't tried with Hoary).

Mount your home partition inside the Live CD, create a empty text file and paste there the lines from /etc/fstab on the Filesystem partition (which is actually a virtual filesystem, located in ram(?).

Reboot back to your installed linux, and just copy the lines you have to your own fstab. Just remember to delete "userid=xxxx", this, I think, would restrict acess of the partition to the user xxxx.

---

### Post by jobezone on 2005-04-10
Or go to [http://ubuntuguide.org/](http://ubuntuguide.org/) , there's a section that shows what to add into fstab.It's a good guide!

---

