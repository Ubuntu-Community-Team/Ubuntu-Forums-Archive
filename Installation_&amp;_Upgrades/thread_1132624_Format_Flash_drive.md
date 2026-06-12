---
title: "Format Flash drive"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by frozenfire0808 on 2009-04-22
How do you format a flash drive to FAT32?   I'm using a 1 Gig that i dont care about before I try to format a 500 gig external hard drive to FAT32 so my Playstation 3 will recognize it

---

### Post by niqmk on 2009-04-22
use gparted

---

### Post by frozenfire0808 on 2009-04-22
where does gparted show up at? I have already searched applications and system tools

---

### Post by niqmk on 2009-04-22
**System->Administration->Partition Editor**

for install:
sudo apt-get install gparted

---

### Post by frozenfire0808 on 2009-04-22
I did that but the following showed up and i still don't know where to look



Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libswt3.2-gtk-java libitext-java
  libswt3.2-gtk-jni linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
paul@office:~$

---

### Post by niqmk on 2009-04-22
> 
**System->Administration->Partition Editor**


for manual visit:
[https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions](https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions)

---

### Post by frozenfire0808 on 2009-04-22
thanks gparted showed up using   sudo gparted in the terminal

---

### Post by Denigris on 2009-04-22
SystemRescueCD has all the tools to handle every imaginable task, including gparted. It's a must have. Forgive the vanity link:

[http://www.teamtuxedo.com/?s=rescue](http://www.teamtuxedo.com/?s=rescue)

---

