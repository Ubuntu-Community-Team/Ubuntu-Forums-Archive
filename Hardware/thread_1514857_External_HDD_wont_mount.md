---
title: "External HDD wont mount"
date: 2010-06-21
forum: Hardware
---

### Post by marin123 on 2010-06-21
Hi guys, i have a big big problem. I have an external hdd (usb) and it wont mount. I tried manual mount but it wont work. The problem is that it fell off the table and after that it was working but then suddenly stopped. I HAVE to get that data back, there's at least 100 GB of music there. Please help!
I opened terminal and typed "lsusb" and i see it there, and "testdisk" was scanning the disk but found no partitions. Its western digital my book and it was ntfs formatted.
Disk utility in ubuntu has this disk but it says it has 2.2 TB of storage, but its actually 1 TB.
Is there any way to recover the files? At least a part of the files?
Thanks!

---

### Post by Joe of loath on 2010-06-21
Was it running when it fell off the table?

---

### Post by marin123 on 2010-06-22
it was connected but i dont know if it performed read/write actions...
today i took out the disk out of the box and now i just have to find a computer with sata disk to try it out. i think something's wrong with power supply because windows recognize it and lsusb sees the disk, but it just cant be mounted...
i'll connect it to a desktop and see if its working...

---

### Post by GenLinux on 2010-06-22
So in win2 you can explore the device without problems? If so, you should try connecting it on Ubuntu 10.04 Live CD and test if it works, If it works the problem is with your installation/configuration, something you did and now your hdd hates you (Joke:lolflag:)

---

### Post by marin123 on 2010-06-23
no, no...
win 7 says its installing 2 drivers for the disk (cant remeber what exactly, standard mass storage drivers) and installs 1st entry but 2nd driver cant be installed (its just spinning like its installing but doesnt finish after couple of minutes)...
i even tried second laptop (thought something was wrong with mine) and a desktop, and everywhere is the same...
i just have to tinkle bit with the desktop (it cant find master hdd, so it wont start), it has sata disk already inside, i'll disconnect it and connect this one and boot from live cd... then i'll know whats wrong (if disk doesnt work, the disk is the problem, else i have to change the power supply)...

---

### Post by marin123 on 2010-06-23
okay, the disk is borken, at least read/write part of the disk, because its spinning but computer doesnt recognize it... i tried every combination to get it working...
now i have another idea... :D
is it possible to take the part where the data is written (magnetic disk) and put it into another case? or am i just watching too many csi? :)

---

### Post by dave_man137 on 2010-06-23
Had a problem like this on my 2 tb external it was fragmented. I fixed it by runing defragment program on windows. ntfs has problems with mounting on linux if the drive is fragmented.

---

### Post by marin123 on 2010-06-23
i took it to a pc service, ill see tomorrow is there hope :)
btw how did your disk get fragmented? fell down or something else?

---

### Post by linux-hack on 2010-06-23
For the future try using the disk in ext3 or 4 that way you have more compatibility on linux. and even the repair of the HDD on linux is much easier .... (juste an advice)

---

### Post by dave_man137 on 2010-06-23
no thats how ntfs is designed it has something to do with repairing/restore setup
read this if you have time [http://www.ntfs.com/ntfs_optimization.htm](http://www.ntfs.com/ntfs_optimization.htm)best of luck.

---

### Post by dave_man137 on 2010-06-23
> **boogy9 said:**
> For the future try using the disk in ext3 or 4 that way you have more compatibility on linux. and even the repair of the HDD on linux is much easier .... (juste an advice)


+1  I have had so many problems with ntfs in the past. ext4 is way better

---

### Post by marin123 on 2010-06-23
i intended to make 2 partitions one ext4 and ntfs or fat32 because i share it on network with windows machines, but i didnt want to mess around because i dont have a place to put 200 GB files that are alredy on it... if the disk can be repaired, i will do this...
nobody commented my idea to put the head into another disk.. is that possible?

EDIT: i did connect the disk to windows and went to Computer -> Manage -> Storage, and i saw the disk but i couldnt initialize it (right click - Initialize)... today i connected it to a computer directly via sata cable to the motherboard but computer couldnt find it... (i was looking in bios and booted xubuntu from live cd).... so there must be physical malfunction, i guess...

---

### Post by dave_man137 on 2010-06-23
> **marin123 said:**
> i intended to make 2 partitions one ext4 and ntfs or fat32 because i share it on network with windows machines, but i didnt want to mess around because i dont have a place to put 200 GB files that are alredy on it... if the disk can be repaired, i will do this...
nobody commented my idea to put the head into another disk.. is that possible?

EDIT: i did connect the disk to windows and went to Computer -> Manage -> Storage, and i saw the disk but i couldnt initialize it (right click - Initialize)... today i connected it to a computer directly via sata cable to the motherboard but computer couldnt find it... (i was looking in bios and booted xubuntu from live cd).... so there must be physical malfunction, i guess...
  


You need power and a sata cable to run off the motherboard and as for the idea to put the head into another disk no ideal . I may be wrong but I don't think it's a physical malfunction.

---

### Post by BbUiDgZ on 2010-06-23
you should try and use the "dd" command and create an iso of your broken h/d (if its shown in /dev)

---

### Post by marin123 on 2010-06-23
i wrote that i did connect it to a motherboard... i removed the main hdd (the one that i have ubuntu on) and replaced with this hdd and nothing... like i didnt connect anything, but the disk was spinning... thats why i think its a physical malfunction...

---

