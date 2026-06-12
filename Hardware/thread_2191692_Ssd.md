---
title: "Ssd?"
date: 2013-12-03
forum: Hardware
---

### Post by grier-devon on 2013-12-03
Hello everyone,
I am interested in getting an SSD in my next notebook and I was curious if there is  anything I should be cautious of? I only am asking cause I thought I have heard of people of people messing up the install of there distro and I heard something about SSD trimming. Any info is appreciated, thanks.

---

### Post by oldfred on 2013-12-03
I liked the user who posted that he buys a better laptop but with hard drive and a separate SSD. Then he removes the hard drive with Windows and just installs Ubuntu to SSD to make a fast computer. Then if he wants to sell it later he just re-installs the hard drive & it has a brand new Windows on it.

       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization](http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization)


 You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.
Info on trim and ext4 without journal 
[http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/](http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

I changed from using discard to a cron task that runs every day.
      
 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)


 Ubuntu Aims To TRIM SSDs By Default
[http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY)

---

### Post by grier-devon on 2013-12-04
Thank you so much!

---

