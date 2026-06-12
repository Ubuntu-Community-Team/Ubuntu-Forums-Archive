---
title: "USB cannot found."
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by wcks48 on 2006-02-14
may i know how to make my kubuntu detect the 256mb Pendrive USB drive after i mounted the stick on? :-k 
besides that, the 3rd partition of my HDD cannot been detected both in WINDOWS and KUBUNTU. How am i going to get the remaining space back?:confused: 

thanx. with the assistance from the members of this foru, i succeassfully run my first time of Kubuntu on my laptop.

---

### Post by taurus on 2006-02-14
If you don't see your USB stick with "df -h" command (means type that command at a terminal), then perhaps you need to mount it by hand as

sudo mkdir /media/usb
sudo mount -t vfat /dev/sda1 /media/usb
sudo cd /media/usb
ls -la

I assume it's the 3rd partition of the first harddrive!  And do you know what format that partition is it, vfat (fat32), ntfs, ext2, ext3, etc.?

---

### Post by wcks48 on 2006-02-15
my hdd got 4 partitions:
1- reserved for my windows OS. already set by windows as NTFS
2- used for storing my own files that hope could be used both in wondows and linux. i put it as FAT32
3- Swap
4- Only for kubuntu as root partition. of coz, FAT32.

I'm not so clear bout the sudo command. where i need to use the command given? in the console? thanx.

---

