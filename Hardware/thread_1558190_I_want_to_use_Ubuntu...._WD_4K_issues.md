---
title: "I want to use Ubuntu.... WD 4K issues"
date: 2010-08-21
forum: Hardware
---

### Post by AtlantaBob on 2010-08-21
Hi guys,

I want to use Ubuntu server (LTS 10.04), but the information on the internet isn't helping. I'm happy to try and writeup a guide for unsophisticated users like me, but I need your help.

I'm trying to install Ubuntu Server Edition LTS 10.04 on a Dell SC 420 with a WD 1TB Green (aka Advanced Format 4K sector) Hard Drive.

I know there are issues with the sector alignment. I tried using the guided partition tool during the installation -- I wanted 10 GB of the disk to be dedicated to the system with the remainder being a data partition (and, if necessary, /swap, /boot, etc.) Ubuntu is going to be the only operating system on this machine. However, I'm just not smart enough to get it to work (or to know that it's working):

The results of sudo -fdisk -lu /dev/sda are (somewhat abbreviated):
                   
                 start       end          system
/dev/sda1     2048          499711           Linux
Partition 1 does not end on a cylinder boundary
/dev/sda2     501758       1953523711        Extended
/dev/sda5     501760       1953523711        Linux LVM

Can someone give me an idea of what I need to do to a.) determine if this is setup ok with the AF issues? b.) create a partition in the extended logical space?

Thanks, please let me know if I didn't include some relevant stuff.

---

