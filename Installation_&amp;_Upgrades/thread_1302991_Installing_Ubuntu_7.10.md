---
title: "Installing Ubuntu 7.10"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by coldzero24 on 2009-10-27
hello everyone

i have ubuntu 7.10 CD and i need to install it on computer p4 2.67 GHz , 1 GB RAM, 40 GB HD

here are the steps that i think i should do and please correct me if i'm wrong :

1- i have 4 partitions one NTFS for XP and three FAT32

2- create 10 GB free space by resizing one of my FAT32 partitions, i will use paragon partition manager for this.

3- insert ubuntu CD and click install then i select specify partitions manually 

4- create 9 GB EXT3 partition Type: Primary Location: END Mount Point: /

5- create 1 GB swap patition Type: Logical

6- Continue...


Thank you for your time :popcorn:

---

### Post by ubername on 2009-10-27
> **coldzero24 said:**
> hello everyone

i have ubuntu 7.10 CD and i need to install it on computer p4 2.67 GHz , 1 GB RAM, 40 GB HD

here are the steps that i think i should do and please correct me if i'm wrong :

1- i have 4 partitions one NTFS for XP and three FAT32

2- create 10 GB free space by resizing one of my FAT32 partitions, i will use paragon partition manager for this.

3- insert ubuntu CD and click install then i select specify partitions manually 

4- create 9 GB EXT3 partition Type: Primary Location: END Mount Point: /

5- create 1 GB swap patition Type: Logical

6- Continue...


Thank you for your time :popcorn:

Looks about right. You can combine steps 2,4 and 5 using the partition manager (gparted) which the install uses, and there's a bit more to it than 'click install' as I'm sure you know, but it's easy enough.

---

### Post by coldzero24 on 2009-10-27
> **ubername said:**
> Looks about right. You can combine steps 2,4 and 5 using the partition manager (gparted) which the install uses, and there's a bit more to it than 'click install' as I'm sure you know, but it's easy enough.

Thank you ubername,

you are absolutely right but i like to use paragon partition manager i don't want to lose any date on my partition, and i have used it before and it worked great maybe gparted is better but i never used it before.

and yes there are other steps but this is the part which scares me most :p , thank you

---

### Post by ubername on 2009-10-27
No problem, use the tools you like the most.

Good luck and enjoy!

---

