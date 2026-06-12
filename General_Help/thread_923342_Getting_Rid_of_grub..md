---
title: "Getting Rid of grub."
date: 2008-09-18
forum: General Help
---

### Post by War_Hero on 2008-09-18
A few days ago, I was messing with the partitions on my XP/Ubuntu dual boot computer. I was on the windows side, and I misread ext3 as empty(it was 3am), so I turned both ubuntu partitions into NTFS drives. Now when I start the computer, GRUB 1.5 has error 17 and I cant get into XP to fix the problem. Also, my ubuntu CD freezes when it is trying to start the partitioner. I have no windows cd, but I was hoping that there is a way to fix it while booting from my ubuntu live cd.

---

### Post by howefield on 2008-09-18
try loading up the Ubuntu live cd and use gparted from the system > administration menu to turn your former ubuntu partitions into ext3 or whatever format you had previously.

Then install Ubuntu into them.

Or, there are utilities you can download which you can install to USB stick or floppy which will allow you to fix your mbr and allow you to boot back back into xp. If you have an xp startup disk (assuming you have a floppy drive) boot from it and type fdisk /mbr at the command prompt. That should get you back to windows.

---

### Post by phidia on 2008-09-18
The fixmbr command (in windows or dos) is the method for resetting your MBR master boot record back to what it was. There is a way to do this in linux too-check the thread [here]("http://ubuntuforums.org/showthread.php?t=339433") (last entry) for an explanation.

---

### Post by phidia on 2008-09-18
The windows/dos command _is not_ fdisk anything! It's fixmbr.
You can try [this guide]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php") also.

---

### Post by War_Hero on 2008-09-18
Thak you, but I am a little confused here.
"install-mbr -i n -p D -t 0 /dev/your-hard-drive (example hda)"
I am not sure what to put in the "your-hard-drive" part. I tried hda, and c, but neither of those worked. c was nonexistant, and hda was read only.

---

### Post by caljohnsmith on 2008-09-18
Did you first install the "mbr" package? That's the package that has the install-mbr program. If not, do this first:
```
sudo apt-get install mbr
```
Then run the following command, but replace "sda" with your HDD if it is different (it might be hda for example):
```
sudo install-mbr -i n -p D -t 0 /dev/sda
```
I think that is all it should take. Let me know how it goes.

---

### Post by War_Hero on 2008-09-18
Yea, I used apt-get to install it, but everytime I try to use it:

ubuntu@ubuntu:~$ install-mbr -i n -p D -t 0 /dev/hda
install-mbr: Failed to open /dev/hda: Read-only file system
ubuntu@ubuntu:~$ install-mbr -i n -p D -t 0 /dev/sda
install-mbr: Failed to open /dev/sda: Permission denied

I'm on a live cd. Also, I was unable to just use gparted to fix my partitions from here.

---

### Post by caljohnsmith on 2008-09-18
Notice the "sudo" in front of the command from my previous post... :)

---

### Post by War_Hero on 2008-09-18
if it doesn't say anything, does that mean it worked?

ubuntu@ubuntu:~$ sudo install-mbr -i n -p D -t 0 /dev/hda
install-mbr: Failed to open /dev/hda: Read-only file system
ubuntu@ubuntu:~$ sudo install-mbr -i n -p D -t 0 /dev/sda
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-09-18
Looks like it probably worked; reboot and find out. :)

---

