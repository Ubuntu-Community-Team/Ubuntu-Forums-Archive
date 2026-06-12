---
title: "Freescale i.MX51 (ARM) doesn't boot with Ubuntu 11.10"
date: 2011-10-16
forum: Hardware
---

### Post by ntarnane on 2011-10-16
Hi,

It just tried to install Ubuntu 11.10 preinstalled desktop image according to this wiki:

[https://wiki.ubuntu.com/ARM/MX5/QuickStart](https://wiki.ubuntu.com/ARM/MX5/QuickStart)

Unfortunately my i.MX51 EVK [1] does not boot at all, the monitor and serial port just stay black. The board acts like there wasn't an SD card attached at all. The board comes with Ubuntu 9.10 on an SD card, with that the board works just fine, so the board is not broken.

I assumed this preinstalled desktop image would work with i.MX51 board, but maybe I'm wrong. Could someone please point me to the right direction how to get Ubuntu 11.10 working with my board?


I used a Xubuntu 11.04 laptop with the following command to write the image to an SD card:

```
zcat ubuntu-11.10-preinstalled-desktop-armel+mx5.img.gz | sudo dd of=/dev/sdb bs=4M

```

After that the SD card has two partitions

55MB partition:

drwx------ 2 nt nt     512 1970-01-01 02:00 .
drwxr-xr-x 6 root root    4096 2011-10-16 18:15 ..
-rw-r--r-- 1 nt nt     262 2011-10-12 20:08 boot.scr
-rw-r--r-- 1 nt nt     190 2011-10-12 20:08 boot.txt
-rw-r--r-- 1 nt nt 2919712 2011-10-12 20:08 uImage
-rw-r--r-- 1 nt nt 4962559 2011-10-12 20:08 uInitrd


2.2GB partition:

drwxr-xr-x  22 root root      1024 2011-10-12 22:08 .
drwxr-xr-x   6 root root      4096 2011-10-16 18:15 ..
drwxr-xr-x   2 root root      5120 2011-10-12 21:49 bin
drwxr-xr-x   2 root root      1024 2011-10-12 21:35 boot
drwxr-xr-x   4 root root      3072 2011-10-12 20:42 dev
drwxr-xr-x 127 root root      5120 2011-10-12 21:49 etc
drwxr-xr-x   2 root root      1024 2011-10-09 10:33 home
lrwxrwxrwx   1 root root        42 2011-10-12 20:37 initrd.img -> /boot/initrd.img-2.6.38-1401-linaro-lt-mx5
drwxr-xr-x  21 root root      4096 2011-10-12 21:23 lib
drwx------   2 root root     12288 2011-10-12 21:56 lost+found
drwxr-xr-x   2 root root      1024 2011-10-12 20:31 media
drwxr-xr-x   2 root root      1024 2011-10-09 10:33 mnt
drwxr-xr-x   2 root root      1024 2011-10-12 20:31 opt
drwxr-xr-x   2 root root      1024 2011-10-09 10:33 proc
drwx------   2 root root      1024 2011-10-12 21:32 root
drwxr-xr-x   7 root root      1024 2011-10-12 21:09 run
drwxr-xr-x   2 root root      7168 2011-10-12 21:49 sbin
drwxr-xr-x   2 root root      1024 2011-06-21 21:59 selinux
drwxr-xr-x   2 root root      1024 2011-10-12 20:31 srv
-rw-r--r--   1 root root 536870912 2011-10-12 21:47 SWAP.swap
drwxr-xr-x   2 root root      1024 2011-07-14 08:18 sys
drwxrwxrwt   2 root root      1024 2011-10-12 21:33 tmp
drwxr-xr-x  10 root root      1024 2011-10-12 20:31 usr
drwxr-xr-x  13 root root      1024 2011-10-12 21:04 var
lrwxrwxrwx   1 root root        38 2011-10-12 20:37 vmlinuz -> boot/vmlinuz-2.6.38-1401-linaro-lt-mx5


[1] [http://www.freescale.com/webapp/sps/site/prod_summary.jsp?code=MCIMX51EVKJ](http://www.freescale.com/webapp/sps/site/prod_summary.jsp?code=MCIMX51EVKJ)

---

### Post by armandoccanto on 2011-10-31
Hi

I am having problems installing the new release for i.MX53 (Mx5) when I run the command:
$ zcat oneiric-preinstalled-desktop-armel+mx5.img.gz| sudo dd of=/dev/mmcblk0 bs=4M
as mentioned on the wiki instructions, it says there is no enough space. I'm trying to install on a micro SD card 4Gb and also on a spare hard drive with 250Gb
I just installed 11.10 on a laptop computer with 3gb of ram (normal installation) 

it copies about 1.6GB and then the error shows up.

Any help will be highly appreciated.

Thanks

---

### Post by TechZilla on 2012-03-12
I hope i'm very wrong, but everything I've read indicates that 'mx5' does not include i.MX51.  I'm very upset about this, and really want something newer than Lucid 10.04 for my Ecafe EX.  Truthfully I'm fine waiting until 12.04, the next LTS.   At that point it will hurt even more.

I actually think it's misleading that 'mx5x' does not include 'mx51' as the '1' would be part of that 'x'.  Being subjugated to 'unsupported' status, before my netbook was delivered to my house is ridiculous.

---

