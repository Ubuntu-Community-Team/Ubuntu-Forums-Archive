---
title: "[SOLVED] Help with GRUB on an EEE PC"
date: 2008-10-08
forum: General Help
---

### Post by Bugsysservant on 2008-10-08
I've tried to install [ubuntu eee]("http://www.ubuntu-eee.com/") on my EEE PC 2 GB surf. It seems to have gone okay, except I now can't boot. I get a message along the lines of "GRUB Loading stage 1.5 please wait... Error 15." I've looked around, and that seems to indicate that it can't find a file, but I really don't even know how to start to fix this. Also note: I don't have an optical drive for my EEE PC, so anything that gets done has to be done via flash drive (the live cd is on a flash drive). Thanks in advance

---

### Post by caljohnsmith on 2008-10-08
OK, from the Ubuntu Live CD on your flash drive, open a terminal (Applications > Accessories > Terminal), and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -l /mnt/boot/grub
cat /mnt/boot/grub/menu.lst
```
And also do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Reboot, and let me know if it changes anything, and be sure to post the output of all the above commands. We can work from there. :)

---

### Post by Bugsysservant on 2008-10-09
```
Disk /dev/sda: 2000 MB, 2000388096 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907008 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc89ec89e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3903794     1951866   83  Linux

Disk /dev/sdb: 2004 MB, 2004877312 bytes
191 heads, 11 sectors/track, 1863 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e7a50

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1     3915775     1957887+   b  W95 FAT32
```

after mounting, I discovered there is no /boot/grub. This is the contents of my /boot folder:
 ```
ubuntu@ubuntu:/mnt/boot$ ls -l
total 12864
-rw-r--r-- 1 root root   67648 2008-08-22 20:03 config-2.6.24-21-eeepc
-rw-r--r-- 1 root root 5111601 2008-09-04 11:14 initrd.img-2.6.24-21-eeepc
-rw-r--r-- 1 root root 5111267 2008-08-24 16:35 initrd.img-2.6.24-21-eeepc.bak
-rw-r--r-- 1 root root  103204 2008-08-22 20:03 memtest86+.bin
-rw-r--r-- 1 root root  879903 2008-08-22 20:03 System.map-2.6.24-21-eeepc
-rw-r--r-- 1 root root 1850200 2008-08-22 20:03 vmlinuz-2.6.24-21-eeepc

```

Also, neither of the grub> find commands returned anything but an error 15: File not Found, so I couldn't do the next step.

---

### Post by caljohnsmith on 2008-10-09
That's really strange that Grub at least seems to have been installed to the MBR (Master Boot Record) of your 2 GB drive, yet you have no Grub folder or files in your /boot directory. 

Try this from your Live CD on the flash drive in order to install Grub to your sda drive:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
apt-get install grub
update-grub
exit
```
If you get any errors with any of the commands, stop and don't continue. Also, the "apt-get install grub" command will require that you have an internet connection, unless the command says you all ready have the grub package installed. Let me know how it goes.

---

### Post by Bugsysservant on 2008-10-09
This is what I got:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
/dev/sda does not have any corresponding BIOS drive.
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# apt-get install grub
Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
root@ubuntu:/# 
```

As I recall there should be about 200 MB free on the EEE PC, as its supposed to only require 1800 MB and I installed withoug swap. Is GRUB really that large?

---

### Post by caljohnsmith on 2008-10-09
While you still have sda1 mounted on /mnt, do:
```
df
```
And you should see how much free space is on sda1. If you still have free space, then try:
```
sudo grub-install --root-directory=/mnt /dev/sda --recheck
```
And see if that works this time.

---

### Post by Zoasterboy on 2008-10-12
This sounds like a different problem, but I've had something similar.

Basically, when you installed from USB flash, the USB flash drive was known as hd0 to the Ubuntu installer, since it was drive 0, or the drive booted from. The drive you installed to (internal flash I assume) was some other drive (probably hd1).

Now that you are trying to boot from the internal flash where Ubuntu is installed, the internal drive is known as hd0, but GRUB is set to load Ubuntu from hd1.

You will have to go in and modify GRUB's menu.lst file and change hd1 to hd0. If you need any help with that just let us know.

---

### Post by Bugsysservant on 2008-10-12
Yeah, the solution was to set the bootloader to install to the correct device from the installation menu. Now if I can just figure out why it says I have no disk space (can't even log in) when the installation is only supposed to take up 1.8 out of 2 GB...

---

