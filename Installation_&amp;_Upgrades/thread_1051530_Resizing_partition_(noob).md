---
title: "Resizing partition (noob)"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by exXPusr on 2009-01-26
I know this probably has been covered, but I still cant seem to get a grip on it. I have intrepid installed as dual boot w/XP I have found with VM I no longer need the XP partition. I used Partition manager to delete the NTFS partition. 

The question...Is it possible to expand the Linux partition to back-fill the space without messing up my install? I know what ever I do I will backup first but I reallly don't want to have to reinstall all my apps that I painstakingly worked to get migrated over from XP.

---

### Post by caljohnsmith on 2009-01-26
It really depends on how your partitions are physically laid out on the drive as to whether you can give the newly created space to your Ubuntu partition. How about posting:
```
sudo fdisk -lu
```
So I can get an idea what your present set up looks like.

---

### Post by exXPusr on 2009-01-26
Thanks for the response....as requested 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe79171eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       315066780   490223474    87578347+   5  Extended
/dev/sda5       315066843   483010289    83971723+  83  Linux
/dev/sda6       483010353   490223474     3606561   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00008c0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   490223474   245111706   83  Linux

---

### Post by caljohnsmith on 2009-01-26
OK, great, looks like you're in luck. :) How about booting your Live CD, open gparted (System > Admin > Partition Editor), right-click the sda6 swap partition and select "swapoff", and then you should be able to resize the sda2 extended partition by moving its starting point to the beginning of the drive. After that, click your sda5 linux partition, and you should be able to move its starting point to the front of the drive also. Once gparted is done with the resizing, you should be all set (but please don't forget to back up everything important before using gparted). 

Another idea though would be to make a data partition with all that space that Windows left, because then you could keep your personal files separate from your Ubuntu install. That's probably what I would do, but it's up to you. Good luck and let me know how it goes.

---

### Post by exXPusr on 2009-01-26
Cool Thanks!:D I'm giving it a go.

---

### Post by exXPusr on 2009-01-27
Kudos to Cal! The fact that i am sending this is testament that it worked! 
I an really impressed with Ubuntu. I am now completely off the M$ train with the exception of a VM session running XP for run some proprietary Spice-Sim software.

---

### Post by caljohnsmith on 2009-01-27
Glad to hear your partition changes went smoothly and you're back in your Ubuntu install; just curious, but when you say spice simulations, are you doing circuit simulations? Are you an electrical engineer or student?

---

### Post by exXPusr on 2009-01-27
While I am not a degreed EE, I Been doing electronics for the past 30+ years. I have a small company FXengineering [FXENG.COM]("http://www.fxeng.com"). We design and build high quality guitar effects pedals. I use CircuitMaker 2000 to develop the concepts. Unfortunately CM was purchased by Oracad a few years back...Big$$ to upgrade.

---

