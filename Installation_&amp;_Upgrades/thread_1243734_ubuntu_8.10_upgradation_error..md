---
title: "ubuntu 8.10 upgradation error."
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by pinku80 on 2009-08-18
Hi,
After I upgraded ubuntu 8.10 and installing the updates I am unable to log in to my system after restart. This is the following problem I'm having.
 
[FONT=Times New Roman][SIZE=3]**Boot from (hd0,9) ext3 9557a59a- ff9f -451b -95cd –b51fcd5c99dc**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**Starting up…**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**Loading, please wait…**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**usplash: Setting mode 1152×864 failed**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**usplash: Using mode 1024×768**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**Gave up waiting for root device. Common problems:**[/SIZE][/FONT]
[FONT=Times New Roman]**[SIZE=3]-[/SIZE]         [SIZE=3]Boot args (cat/proc/cmdline)[/SIZE]**[/FONT]
[SIZE=3][FONT=Times New Roman]**   -Check root delay= (did the system wait long enough?)**[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**   -Check root= (did the system wait for the right device?)**[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]**-   Missing modules (cat/proc/modules; ls/dev)**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**ALERT! /dev/disk/by-uuid/9557a59a- ff9f -451b -95cd –b51fcd5c99dc does not exist. Dropping to a shell!**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**BusyBox v1.10.2 (ubuntu1:1.10.2-2ubuntu7) built-in shell(ash)**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**Enter ‘help’ for a list of built-in commands.**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**(initramfs)**[/SIZE][/FONT]
 
 
Please help me out with the problem.

---

### Post by fela on 2009-08-18
The upgrade must have messed up the UUIDs of the disk or something. Try booting off a Ubuntu livecd and running:

```
sudo fdisk -l
```

Note down the /dev/sd* or hd* of the Linux boot partition (probably the same one as the root partition). From here on I'm referring to the boot partition as /dev/sda1, of course change it for your setup. Now, mount the partition like so:

```
sudo mkdir /mnt/disk && sudo mount /dev/sda1 /mnt/disk
```

If it mounts successfuly, continue (use gedit instead of nano for a graphical editor):

```
sudo nano /mnt/disk/boot/grub/menu.lst
```

Now, scroll down to where all the boot entries are, and at the bottom add your own one - I'm referring to the partition as hd0,0 but change it for your setup. In grub language, hd0,0 means /dev/sda1 or /dev/hda1, hd1,3 means /dev/sdb4 or /dev/hdb4, etc.:

```
title Ubuntu 9.04 test grub entry
root (hd0,0)
kernel /boot/vmlinuz-(whatever your kernel is) ro splash vga=791
initrd /boot/initrd.img(kernel version)
quiet
```

Now reboot and test the new grub entry.

---

### Post by pinku80 on 2009-08-19
when I'm using the code:
 
sudo fdisk-1
 
It's showing 
/bin/sh:sudo: not found
 
what to do?

---

### Post by Partyboi2 on 2009-08-19
> **pinku80 said:**
> when I'm using the code:
 
sudo fdisk-1
 
It's showing 
/bin/sh:sudo: not found
 
what to do?
sudo fdisk -l is with a lowercase L not the number 1, also make sure there is a space between fdisk and -l

---

