---
title: "Driver problem with RocketRaid 622"
date: 2011-10-06
forum: Hardware
---

### Post by xdavid817x on 2011-10-06
Hi everyone, I'm having some issues with the drivers for TR5M-B. 
 
[http://www.sansdigital.com/towerraid/tr5mb.html](http://www.sansdigital.com/towerraid/tr5mb.html)
 
I'm pretty new to ubuntu, and i love to mess with it. But this is the first time i'm completely stumped. I'm using Ubuntu Server 11.04
 
I was following these two links as my guide in trying to make it work.
 
[https://help.ubuntu.com/community/RocketRaid#NOTE](https://help.ubuntu.com/community/RocketRaid#NOTE)
 
[http://ubuntuforums.org/showthread.php?t=1592227](http://ubuntuforums.org/showthread.php?t=1592227)
 
I pretty much got through everything until it ask me to do the build command. I get a error and than it tells me to read the make.log for further details. Which talks about the blkdev_get. I'll post everything on the make.log.
Also i dont know how to recreate squares so i replaced it with []
 
Make.log
 
DKMS make.log for rr62x-1.1 for kernel 2.6.38-11-generic-pae (i686)
Thu Oct 6 18:44:42 EDT 2011
make: Entering directory '/var/lib/dkms/rr62x/1.1/build/product/rr62x/linux'
make[1]: Entering directory '/usr/src/linux-headers-2.6.38-11-generic-pae'
CC [M] /var/lib/dkms/rr62x/1.1/build/product/rr62x/linux/.build/os_linux.o
/var/lib/dkms/rr62x/1.1/build/product/rr62x/linux/.build/os_linux.c: In function []refresh_sd_flags[]:
/var/lib/dkms/rr62x/1.1/build/product/rr62x/linux/.build/os_linux.c:263:7: error: too few arguments to function []blkdev_get[]
include/linux/fs.h:2055:12: note: declared here
make [2]: *** [/var/lib/dkms/rr62x/1.1/build/product/rr62x/linux/.build/os_linux.o] Error 1
make [1]: *** [_module_/var/lib/dkms/rr62x/1.1/build/product/rr62x/linux/.build] Error 2
make [1]: Leaving directory '/usr/src/linux/headers-2.6.38-11-generic-pae'
make: *** [rr62x.ko] Error 2
make: Leaving directory '/var/lib/dkms/rr62x/1.1/build/product/rr62x/linux'
 
 
Any help would greatly be appreciated. I've been trying this for over 2 weeks. and I keep getting the same results :(

---

### Post by coffee412 on 2011-10-06
I had a lot of issues getting a driver to work for a rr622. I went to their website and tried to install their linux version driver and could just "poke my eyes out with rusty forks" I got so mad.

Then what I learned is that the driver for the rr612 is already in linux and all you have to do is install the management software from sandsdigital.

I also didnt have to install the actual card in my computer. I just hooked it an available sata port with the included connector. 

Hope that helps.

---

### Post by xdavid817x on 2011-10-19
Well after several long days. I gave up and went to ubuntu desktop version and downloaded the v1.1 open source drivers. and got it to work. the problem i have now is that after i had it installed and initialized the drive. I can't seem to figure out how to set up that raid 5 as my share drive for the rest of the house through samba. It's 5 500gig hard drives. so i see the 2tb raid 5 volume. And i can access it and create stuff and put stuff there and everything. Everytime i tried to reconfigured the smb.conf file for samba. it wont let me save it in the same file. So i went through terminal to actually change it by doing sudo. but i have no idea what to type when it's path = (blah) to make it match my raid 5 volume. Any help would be appreciated.

---

### Post by coffee412 on 2011-10-19
Make sure you have all the samba stuff installed. As I remember you need to install some extra stuff for samba to actually work. I think I just opened the software center and did a search for samba. 

Here is where google is your friend. Its the first search that came up.

[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

Hope that helps,

coffee

---

### Post by xdavid817x on 2011-10-20
Well after looking through your link. It didnt really helped me but i tried looking through google like you said and i found a link.
 
[http://www.liberiangeek.net/2011/04/share-files-folders-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/share-files-folders-ubuntu-11-04-natty-narwhal/)
 
almost the same. just a few adjustment cause i downloaded the older version of ubuntu. but i've finally got everything up and running!
 
I appreciate your help!
 
 
--------------------------------------------------------------------
 
ok im pretty much done with this thread. How exactly do i make it turned into solved? or delete the thread or something @_@. Or am i suppose to just leave it alone?
Sorry for the nub question im new @_@'

---

### Post by coffee412 on 2011-10-20
> I appreciate your help!

I try. 

Hope you got everything going ok.

---

