---
title: "First time Ubuntu user - nothing but grubs across the screen"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by Dangerdj on 2009-03-23
My first reboot showed Error 18, I changed my HDD type in my bios to normal and now when I boot I get  grub grub grub scrolling across the screen in an infinite loop. Looking for advice or perhaps a link to another thread simply because I haven't found the exact same issue in the forum. 

Single boot, 250 GB HD has been formatted.

---

### Post by meierfra. on 2009-03-23
The "Grub Grub Grub .." is usually caused by wrong settings in the bios. So revert  to the previous setting.  Do your bios have a setting for  "LBA mode"?  That might  cure  error 18.

Grub error 18 usually means that your bios are not able to read the whole hard drive and your boot files are out of reach of the Bios.

If  you could not  cure error 18 by playing with the setting in the bios,  I suggest to reinstall but this time create a separate boot partition at the beginning of the drive (size 200MB, format "ext 3", mount point /boot)

Let me know if you need detailed instruction for this.

(I'm assuming assuming that this is a fresh install, if not you can also follows this  [tutorial]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition") to create a separate boot partition without reinstalling.)

---

### Post by Dangerdj on 2009-03-23
Thanks for the reply meierfra. I changed the HDD settings to Normal which stops the Error 18 but then I get the scrolling grub grub grub screen (infinite loop), tried a fresh install but still getting the same error. 

DJ

---

### Post by meierfra. on 2009-03-23
> tried a fresh install but still getting the same error. 

Don't use the "normal" setting. 
Did you create a separate boot partition?

---

### Post by Dangerdj on 2009-03-24
Deleted all partitions and reformatted with Boot and Nuke, reinstalled Ubuntu and now everything works great.

---

### Post by meierfra. on 2009-03-24
> now everything works great.
Good news.

 Just curious. Which setting in the bios works?  Both? Or does "Normal" mode still get you "Grub Grub ...." Or does the other mode still give you "Grub error 18"?

---

### Post by Dangerdj on 2009-03-24
The normal mode gets rid or error 18 but not the grub grub grub. If I have it set to Auto or anything but normal I get Error 18.

---

