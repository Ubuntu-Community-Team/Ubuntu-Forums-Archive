---
title: "error 17"
date: 2008-09-29
forum: General Help
---

### Post by amruth on 2008-09-29
hi 
i have two os ubuntu &windows xp and there was a free space in my lapttop hdd so i formatted it to the windows xp and named that two new drives as new volume j & k of file system FAT32
and i turned off my system after some time i turned my laptop on during grub loading it shows the message grub loading please wait..
error 17
i am scared of it so i want the help from you how to overcome this error
please tell me as early as possible

---

### Post by caljohnsmith on 2008-09-29
Did you get the Grub error 17 before you got the Grub menu on start up, or after you got the menu and selected an OS to boot? It sounds like yours is the former case, but I just want to be sure. 

Please boot your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, if you got the Grub error 17 prior to getting the Grub menu, then follow these steps:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y), for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Reboot, and let me know what happens on start up.

---

### Post by Uchiha_madara on 2008-09-29
> **amruth said:**
> hi 
i have two os ubuntu &windows xp and there was a free space in my lapttop hdd so i formatted it to the windows xp and named that two new drives as new volume j & k of file system FAT32
and i turned off my system after some time i turned my laptop on during grub loading it shows the message grub loading please wait..
error 17
i am scared of it so i want the help from you how to overcome this error
please tell me as early as possible

at first ubuntu doesn't work on FAT32 ....

i face the same problem ... i am not sure that 
the error 17 means there is no OS in your Laptop

to be sure open new post and ask about the 
List of these error messages and what does each error means?

good Luck

---

### Post by adept_king on 2008-09-29
same error here.  at first, grub was completely gone but i used super grub or something and now grub shows up, i have a dual boot and windows comes up when i boot it, but for some reason ubuntu still offers the error 17.

---

### Post by adept_king on 2008-10-01
fdisk does nothing
fsck modifies the partition
super grub disc "succeeds"
gparted assigns 'boot' tag to the partition

and still, no booting into linux.

---

### Post by caljohnsmith on 2008-10-01
Adept_king, are you getting the Grub error 17 after you select Ubuntu from the Grub menu, or do you get the error 17 before even seeing a Grub menu? If it is the former case, most likely all you have to do is modify your Grub's menu.lst. Let me know which is your case and we can work from there.

---

### Post by adept_king on 2008-10-01
grub lists all the operating systems but upon selecting ubuntu, i get the (t)error 17 message.  i have conducted supergrubdisc fixes three times, as well as fsck.  neither changed a thing.

i dont think it has anything to do with my ubuntu partitions or menu.lst (that is unless menu.lst resided in the MBR)

i can only theorize (since actually *knowing* would preclude that i have spent years planted in front of linux boxes, losing my hair) that windows xp wrote over the MBR on my hard drive that contained both xp and ubuntu.  grub was originally gone as well, i brought it back with SGD.  but now grub does not see ubuntu.  menu.lst was not changed by windows xp just because i erased a logical partition at the end of my drive.  this would mean that xp went into the linux partition, found menu.lst, and altered it.  windows erased grub's way of seeing the partitions.  it sees xp just fine, but xp destroyed all references to ubuntu in the MBR.  thats my theory.

---

### Post by caljohnsmith on 2008-10-01
Adept_king, it sounds like you just need to correct the Ubuntu entries in your menu.lst. How about booting your Live CD, open a terminal, and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure out which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Please post the output. Also, do you have multiple HDDs? If you do, let me know which one you are booting from on start up.

---

### Post by adept_king on 2008-10-02
i was unable to edit menu.lst from within the livecd environment because i did not know how to mount my ubuntu partition with root permission in order to replace the menu.lst file.

somehow, the menu.lst file got rewritten somewhere along the way and the reason grub was not seeing the root was because grub was being told to refer to the wrong partition.

the way i fixed my mess was 

1) use SuperGrubDisc to restore GRUB
2) try all the internet suggestions in the book
3) fail at all of them
4) simply use the 'e' key during the grub bootloader to edit the entry to the proper partition and 'b' to boot, all within the grub bootloader itself.
5)  after booting into my linux (finally) i changed menu.lst with a new menu.lst that i made, using root permission.  i was able to edit out the boot options i dont use such as my stillborn freebsd installation, as well as change the location of the root partition (ubuntu) to reflect accuracy.

thanks for the help ubuntu!

---

