---
title: "windows 7 and ubuntu 9.04 dual boot - help needed"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by trojanworrier on 2009-09-06
i made following partitions of my hard drive:

/dev/sda1 - ntfs  : 19.67 GB <-----windows 7
/dev/sda2 - extended  : 24.11 GB <-----
          /dev/sda5 - ext3  : 15.63 GB <----- linux ubuntu 9.04
              /dev/sda6 - linux-swap  : 8.48 GB <----- linux-swap
/dev/sda4 - ntfs  : 68.01 GB <----- DATA

now while installing:
i chose -- specify partitions manually(advanced) which led me to new window: "prepare partitions": i tried installing it "/dev/sda5" but i got a msg "No root file system is defined,  please correct this from the partitioning manu"

please advice what should I do? should I install grub? i was trying to install grub again and used command "find boot/grub/stage1" but got a msg "no file found"

please advice. I really need help...
Thanks alot...

---

### Post by Moop on 2009-09-06
You need to set the mount point of sda5 as / (root) to install Ubuntu there.

---

### Post by trojanworrier on 2009-09-06
Thanks a lot Finally, Ubuntu 9.04 successfully installed. 
Thanks:popcorn:

---

### Post by adam.d.clemons on 2009-09-09
I just installed windows 7 lastnight on a fresh hard drive, and then installed ubuntu. but ubuntu did not add windows 7 to my grub menu. how do i make windows 7 show up?

my partitions are as follows.

/dev/sda1 <-widnows 7
/dev/sda3 <-ubuntu 9.04
/dev/sda4 <-linux swap

how can i add windows 7 to the boot menu? i really dont want to have to call microsoft to reactivate my key so i can reinstall windows 7.

---

### Post by Zimmer on 2009-09-09
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

A scroll down to the GRUB part might help you... depends where you installed GRUB ...

---

