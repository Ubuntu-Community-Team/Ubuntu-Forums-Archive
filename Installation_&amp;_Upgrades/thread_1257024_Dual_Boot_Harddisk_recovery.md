---
title: "Dual Boot /Harddisk recovery"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by nikhil381 on 2009-09-03
hello

I tried ubuntu few months back using the dual boot option with my win xp . Later on I had to re install win xp and after that the dual booth option for ubuntu dissapeared. I want to know

1. How can i delete the ubuntu installation and recover the hard disk portion.

---

### Post by Bucky Ball on 2009-09-03
Run the Live CD, go to System->Administration->Partition Editor, delete the partitions.

---

### Post by nikhil381 on 2009-09-03
can you tell me what is live cd ?

---

### Post by Bucky Ball on 2009-09-03
The CD you installed Ubuntu with. 8.04 or 9.04, first option is 'Try Ubuntu without changing you system'

---

### Post by nikhil381 on 2009-09-03
i tried that but all i get to see is one partition of 93 GB which is my whole laptop hardrive . I could see the linux partition in PLACES . Could you please help

---

### Post by Bucky Ball on 2009-09-04
Open a terminal, copy/paste this:

sudo blkid

... and post the result back here. Let's see what you have actually got in there.

---

### Post by nikhil381 on 2009-09-04
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="620C461F0C45EE9B" LABEL="WinXP" TYPE="ntfs" 
/dev/sda3: UUID="BA0A40160A3FCDDF" TYPE="ntfs" 
/dev/sda5: UUID="0c4a5744-713b-484d-8d63-4930b05f6815" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="39313aa4-a702-4ce5-9074-d98322f05b25" 
/dev/sda7: UUID="06882A6E882A5C85" TYPE="ntfs" 
/dev/sdb1: UUID="4E24CD2E24CD1A3B" LABEL="FreeAgent Drive" TYPE="ntfs" 
/dev/sdc1: UUID="6A902F95902F6733" LABEL="USBDrive1" TYPE="ntfs" 
/dev/sdc5: UUID="0000-0000" TYPE="vfat" 
ubuntu@ubuntu:~$

---

### Post by nikhil381 on 2009-09-04
is it possible to have XP , 7 and Ubuntu in one machine i mean like triple boot option

---

### Post by Bucky Ball on 2009-09-04
> **nikhil381 said:**
> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="620C461F0C45EE9B" LABEL="WinXP" TYPE="ntfs" 
/dev/sda3: UUID="BA0A40160A3FCDDF" TYPE="ntfs" 
/dev/sda5: UUID="0c4a5744-713b-484d-8d63-4930b05f6815" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="39313aa4-a702-4ce5-9074-d98322f05b25" 
/dev/sda7: UUID="06882A6E882A5C85" TYPE="ntfs" 
/dev/sdb1: UUID="4E24CD2E24CD1A3B" LABEL="FreeAgent Drive" TYPE="ntfs" 
/dev/sdc1: UUID="6A902F95902F6733" LABEL="USBDrive1" TYPE="ntfs" 
/dev/sdc5: UUID="0000-0000" TYPE="vfat" 
ubuntu@ubuntu:~$

Run the Live CD, go to System->Administration->Partition Editor, delete the partitions. 	

Delete sda5 and sda6. Gparted would be showing exactly what you have here. On sda you have five partitions; 1, 3, 5, 6 and 7. sdb has one partition, sdc has one partition and what is sdc5?

I do not understand why you are only seeing one partition in Gparted. Make sure you have the right drive and you should see a list of all the partitions in there.

You could try downloading the Gparted Live CD and booting from that but if you can't see your petitions in Gparted it is something I've never come across.

Incidentally, ideally you should have had three Ubuntu partitions:

/
/home
/swap

Hope you can find them.

---

### Post by nikhil381 on 2009-09-04
i m unable to see partition for sda... for all others i can see ... i have attached the screen shots.

---

### Post by Bucky Ball on 2009-09-04
In the right hand corner of that window where it says:

/dev/sda (93.16GiB)

... can you click the down arrow  to the right of that and look at one of the other drives. Maybe something is mixed up there. Are any of your external drives 100Gb?

---

### Post by nikhil381 on 2009-09-04
sdc and sdb i am able to see the partitions

---

### Post by nikhil381 on 2009-09-04
My drive s are : Laptop on board is 100GB which shows as 93.1 
1 USB External Drive 250 Gb which is coming as SDC
1 Seaget Free agent 500 Gb ...

On my laptop harddisk , i have winxp and win 7 installed , also there is around 19.5 GB on which ubuntu 8.04 is installed. I m trying to recover that . 

Gpart does not show partitions in SDA, i can see in my external drives the partitons

---

### Post by Bucky Ball on 2009-09-04
> **nikhil381 said:**
> My drive s are : Laptop on board is 100GB which shows as 93.1 
1 USB External Drive 250 Gb which is coming as SDC
1 Seaget Free agent 500 Gb ...

On my laptop harddisk , i have winxp and win 7 installed , also there is around 19.5 GB on which ubuntu 8.04 is installed. I m trying to recover that . 

Gpart does not show partitions in SDA, i can see in my external drives the partitons

I can see all that. I really have no idea why you can't see the partitions on sda with Gparted. That has me stumped and I have never seen it before. If I have a eureka moment I'll let you know. Hope someone else has an idea for you. This is from the Live CD, right? Can you boot into Ubuntu and if so, can you see them through Partition Editor (Gparted) in there?

---

### Post by nikhil381 on 2009-09-04
ok ... thanks anyways ...

---

### Post by nikhil381 on 2009-09-04
:frown:

---

### Post by nikhil381 on 2009-09-04
ubuntu@ubuntu:~$ gksudo gparted&
[1] 18994
ubuntu@ubuntu:~$ ======================
libparted : 1.8.8
======================
Can't have overlapping partitions.
ubuntu@ubuntu:~$ 

can any one help

---

### Post by Bucky Ball on 2009-09-04
[http://www.google.com/cse?q=Can%27t+have+overlapping+partitions.+ubuntu&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8](http://www.google.com/cse?q=Can%27t+have+overlapping+partitions.+ubuntu&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8)

Try searching for your error message.

---

