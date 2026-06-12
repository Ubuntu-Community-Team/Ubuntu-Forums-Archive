---
title: "Cannot restart 11.04 Ubuntu after Kernel upgrade"
date: 2011-09-22
forum: Hardware
---

### Post by MalcolmH on 2011-09-22
Hi 

I accepted a set of upgrades last night - which involved kernel headers and maybe kernel (didn't look) - set of upgrades was 72MB in total.  The upgrade required a restart but the restart only ended up with the system not finding a kernel and defaulting to 'grub'.  I am running 11.04 with Classic front end (8-year old laptop - not enough memory to run Unity).

The system has been fully kept up to date with all previous updates installed as offered.

Is there anything I can do to complete the restart, failing that is there anyway to reinstall without losing my current data?

Thanks

Malcolm

---

### Post by garvinrick4 on 2011-09-22
Do not choose to boot from the new kernel boot the previous kernel at menuentry.
That is why most keep an extra kernel or 2 so as to have one that you know will boot.
If its one that you know to keep failing go to Synaptics and remove it.
In search window type in kernel:
2.6.39-10 
as an example and will go to that kernel in synaptics so can remove.
```
grep menuentry /boot/grub/grub.cfg
```will give you list of kernels in menu entry.
## I have not had a kernel fail me for a long while though.
[COLOR=Red]EDIT[/COLOR]: I am sorry I miss read you can not get to the grub menu, my mistake.
Put in a Live Cd (install CD using Try Ubuntu and boot off of it)
Find your linux partition
```
sudo fdisk -l
``` (lower case L)
I will use sda5 use yours. and open a terminal and copy and paste these one at a time.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo reboot
```

---

### Post by manishraj2011 on 2011-09-22
>  is there anyway to reinstall without losing my current data?


You can back up all your data by accessing them via a Ubuntu Live CD.

---

### Post by staticd on 2011-09-22
> failing that is there anyway to reinstall without losing my current data

The scenario requiring a reinstall is very very very unlikely in your case. Fear not.

Are getting a "grub>" prompt and and a black screen.
Or are you getting a grub boot menu with the first choice unbootable? Do tell us. both have relatively easy solutions.

BTW, do you have a bootable CD handy? If you have an old laptop that has trouble running the latest live CD we can do without it but what to do next will depend on wha you tell us.

Good luck.

---

### Post by MalcolmH on 2011-09-22
Hi

I get the 'grub>' prompt

I'm currently burning a CD if I need it

Thanks

Malcolm

---

### Post by staticd on 2011-09-22
will get back to you an hour. I have to attend a lecture.

---

### Post by staticd on 2011-09-22
[COLOR=Red]**EDIT:**[/COLOR] type these at the grub> prompt
If you have a separate boot partition then you should change the following commands to (hd0,mdos2)/vmlinux-xxxxxblah not (hd0,mdos2)/boot/vmlinux-xxxxxblah

Ok try these commands:
```

ls

```will give you a list of partitions availible.
(hd0,msdos1) is /dev/sda1

try to look for the /boot directory in the partition where you installed linux
```
ls (hd0,msdos1)/boot
```you should see a file vmlinuz-xxxxxxxblah and initrd-xxxxxxxblah.
 do 
```

>linux (hd0,msdos1)/boot/vmlinux-xxxxxx root=/dev/sda1
>initrd (hd0,msdos1)/boot/initrd-xxxxxxx
>boot

```just type vmlinu and press tab to get a list of kernels. choose the last but one. Same for initrd.
Then once you boot into ubuntu follow the instructions of [garvinrick4]("http://ubuntuforums.org/member.php?u=899097").

---

### Post by MalcolmH on 2011-09-22
Pure magic!

Logged in again

Thanks for all your help - and to garvinrick4, brilliant

Malcolm

---

### Post by garvinrick4 on 2011-09-22
> Thanks for all your helpYou are welcome. 
Here is a couple of links worthy of keeping in bookmarks to read when time permits. Enjoy your Ubuntu and Welcome to the Forum MalcomH.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11274757"]https://help.ubuntu.com/community/HowtoPartition
[/URL]

---

