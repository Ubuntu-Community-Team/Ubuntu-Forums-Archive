---
title: "Kernel Panic - Missing initrd.img in /boot &amp; menu.lst"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by songstruck on 2009-01-21
Today I tried to upgrade to 8.04 from the Update-Manager. At the terminal, I noticed some errors and then, on reboot, received a Kernel Panic message.

I re-started and booted an old kernel, then used terminal to view my /boot and /grub/menu.lst. I noticed that there is no initrd.img for the new kernel (2.6.24-23-generic) in /boot and, therefore (I guess), no initrd entry in menu.lst.

I'm assuming that I need an initrd.img-2.6.24-23... to go with the new kernel, but I can't tell why this error occurred and I don't know what to do to create the needed file. 

I tried upgrading to 8.10 and that failed. Booting the old kernel runs, but things don't work quite right (e.g., I can't launch many of the applications from the menus). I've searched the issue online and others seem to have had it, but the solutions I've seen don't work for me. I've tried sudo dpkg blah-blah-blah and sudo apt-get upXXX etc., etc.

Questions:
1) Should I try to roll back to an old kernel and re-install? Is that possible? 
2) Is there any point to studying log files? I'm pretty new at this.
3) The initrd.img file is needed, yes?
4) Is there any way to easily create the missing initrd.img file?

I'd appreciate any ideas to try. I put off upgrading because previous upgrades have been hard to recover from and this is par for the course.

Thanks for any help you can offer.

---

### Post by Dieseler on 2009-01-21
I wouldn't do anything drastic.
Try this, its called a symlink and will boot the latest kernel that is installed. Just copy paste it to the top of your menu.lst entries and edit the line behind root and kernel to match your root partition in the places I bolded.
Maybe someone else can come in and get you straight about the kernel entry. This can't hurt anything, all it will do is boot the latest kernel you have and then you can check it from there.

> title        Ubuntu **Whatever**
root         (**hd0,0**) 
kernel       /vmlinuz root=/dev/**hda** ro quiet splash
initrd       /initrd.img
boot

---

### Post by songstruck on 2009-01-21
D,
Thanks for the suggestion. I first tried df -l from a terminal. It shows
/ mounted on /dev/sdb2. 

Then I looked at the current menu.lst. The old working kernels all have the line: 
root (hd1,1)

So, using your suggestion, I added as first in the list of kernels:
title   Ubuntu Experiment
root    (hd1,1)
kernel  /vmlinuz root=/dev/**** ro quiet splash
initrd  /initrd.img
boot

I tried several iterations for the "****" after /dev/. I tried hda, hdb, sda, sdb, sdb2, hd1, etc. Whatever I try, I get the same message from grub:

Error 15: File not found

Is there something I'm not doing right?

---

### Post by songstruck on 2009-01-22
Anyone with any ideas?

---

### Post by tehtrk on 2009-02-06
I'm having a similar issue.

I was running on 2.6.27-9 kernel to test stability for one of my servers. I remember installing updates which included a kernel update, which seems to have hosed my boot process when booting the default option, "Ubuntu 8.04.2, kernel Default". The latest non-testing linux kernel image I am seeing in Synaptic is version 2.6.24-23, so I'm not sure why my menu.lst reads the way it does. The first and second options are invalid, obviously. 

I would say post the output of ls -l /boot and contents of your menu.lst.

Here's mine

```
 
ls -l /boot/
total 150607
-rw-r--r-- 1 root root  422607 2008-04-10 11:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  422667 2008-05-01 12:59 abi-2.6.24-17-generic
-rw-r--r-- 1 root root  422667 2008-05-28 21:39 abi-2.6.24-18-generic
-rw-r--r-- 1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rw-r--r-- 1 root root  422838 2008-11-24 16:47 abi-2.6.24-22-generic
-rw-r--r-- 1 root root  422838 2009-01-25 22:30 abi-2.6.24-23-generic
-rw-r--r-- 1 root root  507735 2008-11-11 12:54 abi-2.6.27-9-generic
-rw-r--r-- 1 root root   79964 2008-04-10 11:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   80071 2008-05-01 12:59 config-2.6.24-17-generic
-rw-r--r-- 1 root root   80071 2008-05-28 21:39 config-2.6.24-18-generic
-rw-r--r-- 1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
-rw-r--r-- 1 root root   80062 2008-11-24 16:47 config-2.6.24-22-generic
-rw-r--r-- 1 root root   80051 2009-01-25 22:30 config-2.6.24-23-generic
-rw-r--r-- 1 root root   91364 2008-11-11 12:54 config-2.6.27-9-generic
drwxr-xr-x 2 root root    1024 2009-02-02 08:12 grub
-rw-r--r-- 1 root root 7697034 2008-05-23 03:51 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7266163 2008-05-23 03:30 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 7737364 2008-06-12 08:13 initrd.img-2.6.24-17-generic
-rw-r--r-- 1 root root 7697497 2008-05-27 08:43 initrd.img-2.6.24-17-generic.bak
-rw-r--r-- 1 root root 7738404 2008-06-12 08:16 initrd.img-2.6.24-18-generic
-rw-r--r-- 1 root root 7738349 2008-06-12 08:16 initrd.img-2.6.24-18-generic.bak
-rw-r--r-- 1 root root 7739569 2008-08-28 08:13 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7739599 2008-08-12 08:30 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7722476 2008-11-07 08:18 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7737142 2008-11-05 11:29 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root 7721025 2008-12-08 14:15 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 7719802 2008-12-01 08:41 initrd.img-2.6.24-22-generic.bak
-rw-r--r-- 1 root root 7721258 2009-02-02 08:12 initrd.img-2.6.24-23-generic
-rw-r--r-- 1 root root 7721101 2009-01-20 08:32 initrd.img-2.6.24-23-generic.bak
-rw-r--r-- 1 root root 7579647 2009-01-20 11:26 initrd.img-2.6.27-9-generic
-rw-r--r-- 1 root root 7579693 2009-01-20 10:00 initrd.img-2.6.27-9-generic.bak
drwxr-xr-x 2 root root   12288 2008-05-23 03:27 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rw-r--r-- 1 root root 1096181 2008-11-11 12:59 System.map
-rw-r--r-- 1 root root  899892 2008-04-10 11:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root  905012 2008-05-01 12:59 System.map-2.6.24-17-generic
-rw-r--r-- 1 root root  905012 2008-05-28 21:39 System.map-2.6.24-18-generic
-rw-r--r-- 1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root  905617 2008-11-24 16:47 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root  905809 2009-01-25 22:30 System.map-2.6.24-23-generic
-rw-r--r-- 1 root root 1096181 2008-11-11 12:54 System.map-2.6.27-9-generic
-rw-r--r-- 1 root root 2238352 2008-11-11 12:59 vmlinuz
-rw-r--r-- 1 root root 1904248 2008-04-10 11:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921944 2008-05-01 12:59 vmlinuz-2.6.24-17-generic
-rw-r--r-- 1 root root 1921528 2008-05-28 21:39 vmlinuz-2.6.24-18-generic
-rw-r--r-- 1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 1921176 2008-11-24 16:47 vmlinuz-2.6.24-22-generic
-rw-r--r-- 1 root root 1922904 2009-01-25 22:30 vmlinuz-2.6.24-23-generic
-rw-r--r-- 1 root root 2238352 2008-11-11 12:54 vmlinuz-2.6.27-9-generic

```
```

less /boot/grub/menu.lst
<snip>
## ## End Default Options ##

title           Ubuntu 8.04.2, kernel Default
root            (hd0,0)
kernel          /vmlinuz root=/dev/md0 ro quiet splash
quiet

title           Ubuntu 8.04.2, kernel Default (recovery mode)
root            (hd0,0)
kernel          /vmlinuz root=/dev/md0 ro single

title           Ubuntu 8.04.2, kernel 2.6.27-9-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.27-9-generic root=/dev/md0 ro quiet splash
initrd          /initrd.img-2.6.27-9-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.27-9-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.27-9-generic root=/dev/md0 ro single
initrd          /initrd.img-2.6.27-9-generic

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.24-23-generic root=/dev/md0 ro quiet splash
initrd          /initrd.img-2.6.24-23-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-23-generic root=/dev/md0 ro single
initrd          /initrd.img-2.6.24-23-generic
<snip>

```The 5th and 6th options are the correct ones for the latest kernel, and the first and second ones are hosed. Note: I didn't edit this (yet). This was changed by the update-manager and whatever backend it uses (apt-get? aptitude?)

---

