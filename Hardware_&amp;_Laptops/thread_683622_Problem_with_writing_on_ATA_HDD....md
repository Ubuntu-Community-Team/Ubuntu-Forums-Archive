---
title: "Problem with writing on ATA HDD..."
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by firedevilbg on 2008-01-31
Hi, to everyone. (I am sorry, if I have problems with English language, I don't know it very well...)
I am a new in Ubuntu so I have a problem.
My computer is:
AMD Athlon 2500+ 
1GB DDR RAM
mb ECS KT-600 a 
graphic card ATI RADEON 9200 SE 128MB
one SATA HDD 80 GB
second ATA HDD 320GB

The little HDD (80 GB HDD) have installed  Windows XP SP2 and Ubuntu 7.10.
With Ubuntu installation I installed GRUB boot manager. When I started Ubuntu I install a NTFS Config Tool from Synaptic. The second HDD (the big one... 320 GB) is splitted on two partitions (160 GB each one of them) in ext3 format. When I  tried to write some files on one of the big partitions, the system show me 
a popup with message that says me that I don't have a permission to write on that label. (I have to be "root" )   But how to be root, and how to write on that partiotions. How to made the  "User" to have permission to write on that labels.  Please help me for the problem, if it can, 
tell me the easy way...

---

### Post by taurus on 2008-01-31
How do you mount that ntfs partition?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

