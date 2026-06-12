---
title: "Cant install to my usb!"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by kmaster228 on 2009-05-17
hey Guys

i made my kubuntu 9.04.iso into a bootable usb from 
System>Administration>USB Startup Disk Creator and it was sucessful
however when i reboot. the kubuntu menu pops up

try kubuntu, install kubuntu, memory check, etc. i i goto install kubuntu option
and i enter my language , timezone, keyboard orientation and when i come to the drive partitioner there is no option to install to my usb... i dont know what to do! please help!
thank you :D
PS. i am dualbooting vista with ubuntu and i want to put kubuntu on my usb.

---

### Post by jerrrys on 2009-05-18
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Carl Hamlin on 2009-05-18
By the by, installing to a USB Flash drive will *drastically* shorten the life of the drive, being that Flash is capable of a finite amount of write/erase cycles before doing the big firework. If you *do* install to a flash drive, don't store anything critical on it.

---

### Post by kmaster228 on 2009-05-18
i have tried pendrive linux, and i come to the same problem! when at the install menu their is no option to install to my usb! please help!

---

### Post by kmaster228 on 2009-05-18
> **Carl Hamlin said:**
> By the by, installing to a USB Flash drive will *drastically* shorten the life of the drive, being that Flash is capable of a finite amount of write/erase cycles before doing the big firework. If you *do* install to a flash drive, don't store anything critical on it.

I know its just a way for me to hide the uglyness of windows when i go around, its not going to be like my main operating system

---

### Post by Mighty_Joe on 2009-05-19
> **Carl Hamlin said:**
> By the by, installing to a USB Flash drive will *drastically* shorten the life of the drive, being that Flash is capable of a finite amount of write/erase cycles before doing the big firework. If you *do* install to a flash drive, don't store anything critical on it.

I don't think it's that bad.  You get about 100,000 write-erase cycles before the memory starts to wear ([source]("http://en.wikipedia.org/wiki/Flash_memory#Memory_wear")).  There are also steps you can take to mitigate the wear, like moving logging and cache to tmpfs and turning off swap.  
I used these instructions to [install]("http://beastie.cs.ua.edu/cs150/usb-install.html") and [configure]("http://beastie.cs.ua.edu/cs150/configuration.html") an install a full install and it takes those steps.
kmaster228, the way I read your problem, you've placed the Live CD image onto a USB drive, rebooted and now you are trying to install onto that same drive?  My gut reaction is that it can't be done.  Have you tried booting the Live CD (from a CD) then installing to the flash drive?

---

### Post by kmaster228 on 2009-05-19
Ok i burnt the Iso to a CD and then booted from it, but in the ubuntu partitioning menu there is no option to use my usb, even in manual option it is only dev/sda1 and dev/sda2 and those are ntfs which are probably my windows stuff and i dont want to mess with those.

---

### Post by Mighty_Joe on 2009-05-21
That's odd.  Does your drive get mounted?  If not, it sounds like a problem with the USB driver/hub/controller.

---

### Post by kmaster228 on 2009-05-22
but when i plug my usb in , it mounts it and i am able to look at all the folders and files

---

### Post by Mighty_Joe on 2009-05-22
Did you plug in your drive before you started the installation wizard?  I tried both the Kubuntu and Ubuntu live cd's and both detected the 3 flash drives I have.
I have seen problems with various installers if the USB drive doesn't have a partition table [(see here)]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865").  You may want to use fdisk or gparted to delete the existing partition and create a new one, which will create the table

---

### Post by kmaster228 on 2009-05-30
no i plugged it in after i booted from the live cd

---

