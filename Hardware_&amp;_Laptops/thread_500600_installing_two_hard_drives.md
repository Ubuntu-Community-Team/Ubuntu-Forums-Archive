---
title: "installing two hard drives"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by lunamystry on 2007-07-14
Hello, I just bought a second hard drive and i was wondering if it will be possible for me to boot Feisty on it then also install some other Operating system like Opensuse on the other old one without them affecting each other, I hope make sense. i know nothing about computer, (I am using that as an excuse) so i don't know how to partition a hard drive and how to dual boot if thats what i have to do. if anyone can at least point me in the right direction i would really appreciate it. 

Thank you for your valuable time

---

### Post by vanadium on 2007-07-14
I am a bit surprised that you wan to go for two operating systems when your "know nothing about a computer". In your case, I would go for one (Ubuntu is very suited for less experienced users), get to learn it, play around with it, until I knew more about computers and wanted to try other distributions or operating systems. Then, what you want to do will be perfectly and easily possible (as long as you do not have MS Windows as the other OS: that one will claim your system only for itself).

---

### Post by ajgreeny on 2007-07-14
I agree generally with the comments of vanadium, but don't be totally put off by them.  It is certainly worth getting to know linux a bit before you try to run more than one, but it is also quite easy to have several linux distros  on your machine, just looik out for problems with partitioning, as you can only have 4 primary partitions on a hard disk.  I have both ubuntu and pclinuxOS, together with windows XP on my two hard disks and all run brilliantly, though I seldom use windows at all, unless I need my scanner which is useless in linux (too old and parallel interface).

If you really want to go ahead, make sure windows is the first one installed, if you've got it, then install the "other" linux, then ubuntu.  The reason for this order of installation is that many other linux ditros are not very good at finding linux already installed, whereas ubuntu is very good and will undoubtedly find your opensuse, or whatever without a problem and add it to the menu.lst file for inclusion in grub.  Then at boot you just chose which OS you want to use that time.

---

### Post by LaRoza on 2007-07-14
The easiest and safest way to do this, would be to install the OS to the first drive, remove it, and then install the other OS to the other drive. Then attach both hard drives. When you boot, you will have to manually select which hard drive to boot from, whatever boot loader you use will not know of the other harddisk.

Are these SATA or PATA drives?

---

### Post by lunamystry on 2007-07-14
> **vanadium said:**
> I am a bit surprised that you wan to go for two operating systems when your "know nothing about a computer". In your case, I would go for one (Ubuntu is very suited for less experienced users), get to learn it, play around with it, until I knew more about computers and wanted to try other distributions or operating systems. Then, what you want to do will be perfectly and easily possible (as long as you do not have MS Windows as the other OS: that one will claim your system only for itself).

I don't have anything against windows, I just Don't like it, so no worried about using ms and i am using two OS because I am still trying to find one that works great fro me. You,re Ubuntu was relatively easy to learn and i am still learning it. But this is what I also plan to do: I wanna test things like beryl and fusion and any untrusted applications on the one then if they don't give me any trouble I download them into the other OS. I may change my mind on this but thats the plan at the moment. 

THANK YOU VERY MUCH FOR THE ENCOURAGEMENT!1.:)

---

### Post by lunamystry on 2007-07-14
> **ajgreeny said:**
> I agree generally with the comments of vanadium, but don't be totally put off by them.  It is certainly worth getting to know linux a bit before you try to run more than one, but it is also quite easy to have several linux distros  on your machine, just looik out for problems with partitioning, as you can only have 4 primary partitions on a hard disk.  I have both ubuntu and pclinuxOS, together with windows XP on my two hard disks and all run brilliantly, though I seldom use windows at all, unless I need my scanner which is useless in linux (too old and parallel interface).

If you really want to go ahead, make sure windows is the first one installed, if you've got it, then install the "other" linux, then ubuntu.  The reason for this order of installation is that many other linux ditros are not very good at finding linux already installed, whereas ubuntu is very good and will undoubtedly find your opensuse, or whatever without a problem and add it to the menu.lst file for inclusion in grub.  Then at boot you just chose which OS you want to use that time.

I dont know how to partition. Do you know of any site that can give me a step by step guide? or should i yahoo it? maybe google...

Thank you for your time

---

### Post by lunamystry on 2007-07-14
> **LaRoza said:**
> The easiest and safest way to do this, would be to install the OS to the first drive, remove it, and then install the other OS to the other drive. Then attach both hard drives. When you boot, you will have to manually select which hard drive to boot from, whatever boot loader you use will not know of the other harddisk.

Are these SATA or PATA drives?

I think they are SATA i am not really sure, but the vendor on the properties menu is written ATA the other is SATA thats what I asked for when i bought it. 

Thank you, i think i will do what you said, it sounds simple and I was thinking of the same thing.

---

### Post by ajgreeny on 2007-07-14
> I dont know how to partition. Do you know of any site that can give me a step by step guide? or should i yahoo it? maybe google...
Get yourself a copy of **gparted liveCD** (google for where to find it) and use that to resize any partition on your disks.  It's a brilliant CD to keep handy and is only a 30MB download; I use it any time I need to do any partition work.  Once you have reduced existing partition size you can use the unallocated space for your next install.  distros do vary in the detail of their default set up, so it's not easy to say exactly what is best for your next installation, but if you don't know any better, just allow the installer to do the default, but make sure you install it to the correct part of the disk and don't wipe an existing OS you want to keep.

---

### Post by lunamystry on 2007-08-03
I need a program to move or access files on one hard drive running Kubuntu Gusty gibbon to another hard drive running Kubuntu feisty fawn. Does it exist? and

I cant dual boot the two kubuntus. everytime i want to use the other i have to disconnect the other, is it the way I connect them to the hard drive or something?

thank you

---

