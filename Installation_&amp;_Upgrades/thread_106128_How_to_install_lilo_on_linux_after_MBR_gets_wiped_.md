---
title: "How to install lilo on linux after MBR gets wiped out by Windows"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by dalmeida on 2005-12-19
The instructions below are also found at [https://www.roguelinux.com/forum/modules/newbb/viewforum.php?forum=1](https://www.roguelinux.com/forum/modules/newbb/viewforum.php?forum=1)

If you already have lilo intalled, just login on single user mode and re-run the lilo command, if you have grub, I'd suggest downloading a fresh copy of the latest lilo version.

1- Create a folder called lilo and download lilo from my site , or just look it up on google
2- cd lilo
3- tar xzvf lilo-22.7.1.bin.tar.gz (this will unpack all the files into this lio directory. Just copy the files from the folders below as shown)
4- cp boot/* /boot/
5- cp sbin/* /sbin/
6- cp usr/* /usr/
7- vi /etc/lilo.conf
8- Just copy my sample below, of course changing the file names to match what yours are.

##### /etc/lilo.conf starts below. Don't copy this line ###

boot=/dev/hda
map=/boot/map
compact
prompt
timeout=80

other=/dev/hda2
label=windows

image=/boot/vmlinuz-2.6.10-4-386
label=linux
root=/dev/hda3
initrd=/boot/initrd.img-2.6.10-4-386
read-only

---

### Post by matthewv on 2005-12-20
You wan't to install lilo... What for? Is there any reason why you can't use grub??

---

### Post by dalmeida on 2005-12-29
I couldn't figure out how to re-install grub, so I went with lilo, which I'm more confortable using, plus it is much easier to configure.

---

