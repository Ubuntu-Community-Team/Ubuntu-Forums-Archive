---
title: "having alot of trouble installing linux"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by Biceptoid on 2009-07-10
hey i have a asus g50v laptop. ive been trying to install linux for 2 or 3 days now and im starting to get frustrated. ive looked at alot of forums and manuels on how to instal. and the only issue im really having is partitions. whenever i have windows installed somehow when i go to install linux that partition is deleted or wiped ive tried do a manuel partition but again somehow it gets deleted. i wish to duel boot vista with linux. i have used the alternative live cd for 8.04 and it finally installed, yet again deleted windows. but couldnt install grub. so at the moment im at a loss if i should just find a way to boot and install grub and just leave windows out for a bit. or what the best course of action is. please help.

---

### Post by geekity2 on 2009-07-10
Hi Biceptoid,

First off, if you haven't already I'd defragment the Windows, to be on the safe side. Then you would probably be best off getting a live cd of a partitioner, like gparted (uses a very nice graphic user interface), or repartition in Windows, to make an empty new partition of the size you want to use for your Ubuntu. Once you have that you should be able to use the manual partitioner on the live cd install to either format the new, empty partition or use it straight out (if it's marked as free space) and use the free space from it to make a root (mounted at /) and a swap partition. And that should have you installed.

Hope that helps.

EDIT

Apparently, just found out you shouldn't use gparted to make a new partition, since it doesn't agree with Vista. Instead you should use Vista Disk Management utility to make a new, empty partition while booted in Windows.

---

### Post by Mark Phelps on 2009-07-10
You don't need to use the Vista Disk Management utility to create a new partition for Ubuntu, instead, if you want to retain Vista intact, you MUST use it to shrink the Vista OS partition.

You can then boot from the Ubuntu Live CD and use the Partition Editor to format the unallocated space as an Ext3 or Ext4 partition to hold Ubuntu.

---

### Post by WoRoN on 2009-07-10
Hello!

Try to install ubuntu (if you have disk with 9.04) inside windows. Load your windows (xp, 7, wista), enter the disk and start the autorun with ubuntu. And here you can see the menu with 3 objects. One of them - that what you need. Enjoy!

P.S. if you wanna to have windows & linux together, don't install through BIOS. So you can, if you can create individual partion for your Ubuntu system.

---

### Post by ajgreeny on 2009-07-10
Not sure what WoRoN means, but I think I disagree with him.  I suggest strongly that you do what Mark Phelps says, that is, shrink your windows partition, after defragging, using the vista disk management, not gparted or anything else, then install ubuntu on the free space.

It definitely works well, and quickly that way, I have recently done it exactly as described.  You can even make a partition on the free space with gparted on the live CD if you wish, but it's not necessary, the installer will do it all in one go.

---

### Post by merlinus on 2009-07-10
WoRoN appears to be suggesting wubi wubi doo...

---

### Post by Biceptoid on 2009-07-10
thanks for all the replys but just to clarify. since i have to reinstall windows visita. im going to make one large bulk of my hard drive so when i install ubuntu 9.04 i can shrink that into 2 partions, half which will still remain vista, and half of which would be used for ubuntu. which of the half for ubuntu i will make a 4 g swap partition,  and make a root partition and boot partition.  is there a special way to labe these> such as i make the book a primary correct. and all the new partioins are going to be ext3. 
im new to the whole linux system and im determined to understand and be able to do this. thanks

---

### Post by merlinus on 2009-07-10
Lots of excellent info here:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by raymondh on 2009-07-10
and these:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

A couple of thoughts:

1.  Remember that you have a 4 primary (or 3 primary + 1 Extended) partition limit.  With that in mind, how many partitions do you have as of the moment (with Vista installed)?  

This question is also in relation to your preference to create /boot.  200mb is enough for boot files.  If you want to create /boot, which will be in front of the drive, that will require advance planning (before installing Vista) and will be a primary partition on it's own ...  It still is possible though ..... /boot + Vista + Vista Recovery + Extended (to house '/' and SWAP).

2.  Back up your files before doing any partitioning work.
3.  Defrag Vista and use its' disk management tool to shrink Vista.  You may encounter a situation where Vista will not shrink as much as you wish.  

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

4.  1.5GB swap is OK IMHO ... unless you use heavy, resource intensive apps and suspend a lot.

A simpler approach to dual booting is to 

1.  Install Vista.
2.  Defrag Vista, close and then exit windows
3.  Boot into the liveCD
- Check CD for defects
- Try out Ubuntu without any changes (to see how it reacts to your system specs & hardware
4.  If OK, install
5.  When you get to the partitioning stage (step 4, I think), choose GUIDED RESIZE
6.  Grab the center of the slider and "slide-away"  to establish partition sizings for both Vista and Ubuntu.
6.  Continue with the install ... letting the installer do it automatically.

This won't create /boot though.  

Again, your preference.  Good luck.

---

### Post by Biceptoid on 2009-07-10
alright i got the partioning thing down. did it with disk manager and once in ubuntu install gues guided resize to make them 50 50, now when i actually install. it come us with error ext3. file error. what could cause this.

---

### Post by raymondh on 2009-07-10
as you have already shrunk Vista ... choose GUIDED USE largest continous free space.

If you choose GUIDED RSIZE (partition 1), you will resize Vista FURTHER.

---

### Post by Biceptoid on 2009-07-10
alrighty and due to the error i recieved in the 3d instal version. im gona go ahead and try the alternative text version cause it has worked before. now will this install grub? or how will i boot into it once its finished with all the instaltion. i had susscessully installed it once, yet it deleted vista, and i couldnt figure out how to boot into it.
edit'
well just tried the text version. it wants to use the entire disk. which i dotn want. so im gona go back and figure out the other regular. lets hope this works. but still as u were saying earlier. it doenst create a boot, which ill need to get into the system on a regualr basis. how would i go about doing this? i ran the software without changing system and it worked fine.

---

### Post by WoRoN on 2009-07-10
> **ajgreeny said:**
> Not sure what WoRoN means, but I think I disagree with him.  I suggest strongly that you do what Mark Phelps says, that is, shrink your windows partition, after defragging, using the vista disk management, not gparted or anything else, then install ubuntu on the free space.

It definitely works well, and quickly that way, I have recently done it exactly as described.  You can even make a partition on the free space with gparted on the live CD if you wish, but it's not necessary, the installer will do it all in one go.

sry I did'nt understand, what he want to do =) I'm newbe...

---

### Post by Biceptoid on 2009-07-10
no biggie neither do i which is why im asking. ive been trying for 3 days to get it to work. as in installed on seperate partitions and bootable. but no luck so far. i feel like im close though. thanks for helping though

---

### Post by Biceptoid on 2009-07-10
alrighty i got it installed and able to boot it at start up. i appericate the help everyone

---

### Post by Biceptoid on 2009-07-10
ugg i feel dumb. i know what i set my username and password 2 bu tthey arnt working is there a way i can add a new user to get in the system to tweak the old one. or do i jus thave to reinstallagain. i feel stupid. but i know what i put and i cant figure out whatelse it might be

---

### Post by merlinus on 2009-07-10
Select recovery at the opening menu.  When the system is booted up, select drop to shell (the last choice of the four at that menu).

Then type:

ls /home

and press Enter

which will give your username.

then:

passwd username

and press Enter

which will allow you to enter a new password.

Remember to replace username with the actual name.

---

### Post by Biceptoid on 2009-07-10
sigh more issues. finnally have installed and in system with user name. cannot connect to wireless internt in my house. it doesnt bring it up on the list of connections. only offers wired and point to point. also screen resolution is 800x600 when supposed to be like 1200x 1000 or something. how do i get ubuntu to detect system devices and wireless?

---

