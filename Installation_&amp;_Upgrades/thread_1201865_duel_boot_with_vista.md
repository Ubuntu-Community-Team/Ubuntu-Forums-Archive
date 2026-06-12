---
title: "duel boot with vista"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by idproc on 2009-07-01
I have vista and I would like to install ubuntu 9.04. How do I do this? thanks for your help.

---

### Post by raymondh on 2009-07-01
> **idproc said:**
> I have vista and I would like to install ubuntu 9.04. How do I do this? thanks for your help.

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://members.iinet.net.au/~herman546/p17.html](http://members.iinet.net.au/~herman546/p17.html)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

You may want to consider having a separate /home partition.  Its' value is that should you need to re-install or upgrade, your settings, tweaks, etc can be retained ...... as you will only touch the root (/) partition.  If so interested:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntuforums.org/showthread.php?t=1175277](http://ubuntuforums.org/showthread.php?t=1175277)

The second link starts at post # 8.  Note, in that thread, the OP created the partitions first.

Some tips :

Try the liveCD first and see how it reacts to your system specs'.  It is a good indicator of things to come.

1.  back up your personal files and save elsewhere (if able)
2.  Defrag Vista
3.  Use Vista's disk management tool to resize the Vista partition (if you wish to create partitions yourself)

Good luck and post back if you need further assistance.

---

### Post by presence1960 on 2009-07-01
> **idproc said:**
> I have vista and I would like to install ubuntu 9.04. How do I do this? thanks for your help.

first I would suggest you read some and familiarize yourself with what it is you are going to be doing. here are a couple Links to get you started:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a step by step how to on the installation process and much, much more.

When ready back up all your data! Although the partitioning and installation processes run almost flawlessly, there is always the odd chance that something may happen. Don't be the one whining on here that your files are gone/corrupted.

Defrag Vista at least once, maybe twice. This is important, don't try to get around this step. When done use Vista's disk management utility to shrink Vista's partition to create space for the Ubuntu install. 

Boot from the Ubuntu Live CD and choose check disk for defects. if it passes then install Ubuntu. For more specific partitioning schemes you have to tell us what you want to use Ubuntu for, do you want to share a partition between Ubuntu & Vista, etc. Post back and the community will have some suggestions for you.

I know it may seem daunting, but installing an OS requires planning and knowledge of what you are going to be doing. Really it is not hard if you prepare yourself. Installing an OS from scratch isn't the same as recovering Windows from a recovery CDs/DVD or a recovery partition. When doing that the partition scheme and all drivers are preset by the disk. If you have ever installed Windows from a installation CD/DVD you know the difference.

---

### Post by beltoni on 2009-07-01
Hi, I am also trying to install ubuntu, latest version with vista as primary os. I have vista on drive c 160gb with only about 20gb free for ubuntu. I tried the second option in ubuntu install, the one where it says if you want to install as seperate program which can be easily uninstalled like a program. after install and reboot I am faced with vista boot loader with vista as first os and ubuntu as second choice. if i select ubuntu it goes to an unable to load windows screen and asks me to reinsert windows cd. I'm guessing vista has written over the grub for ubuntu rendering ubuntu unbootable. I then boot back into vista and tried doing some research but it's got me stumped, any ideas>:)

---

### Post by Geoff918 on 2009-07-01
You can do all of the above. A really nice option for a newbie who is just trying out Ubuntu is the Wubi installer. It's a couple MB download and it will configure Vista to play nicely with Ubuntu. Also, if you somehow mess up Ubuntu you can just uninstall and reinstall it very easily through Vista. Later if you're convinced you want to stick it out with Ubuntu (and why wouldn't you?) you can go through the more drastic system changes being discussed here. I only advise this because I started with Ubuntu back in January and I messed a few things up at the outset. I'm pretty good now, but my two cents are to play it conservatively. There's nothing that will turn you off to Ubuntu or any other Linux version faster than making a big mess out of your system. It's all pretty easy to use, but until you're really ready for the plunge it's not bad to just get your feet wet. :)

---

### Post by raymondh on 2009-07-01
Well said Geoff918.

If I may add, for the OP, do try out the liveCD first.... and back-up your files.

---

### Post by beltoni on 2009-07-01
Hi, I am also trying to install ubuntu, latest version with vista as primary os. I have vista on drive c 160gb with only about 20gb free for ubuntu. I tried the second option in ubuntu install, the one where it says if you want to install as seperate program which can be easily uninstalled like a program. after install and reboot I am faced with vista boot loader with vista as first os and ubuntu as second choice. if i select ubuntu it goes to an unable to load windows screen and asks me to reinsert windows cd. I'm guessing vista has written over the grub for ubuntu rendering ubuntu unbootable. I then boot back into vista and tried doing some research but it's got me stumped, any ideas>:)

---

