---
title: "ubuntu 11.04 wireless driver for dell vostro 1510 - wirless card: BCM4312 802.11"
date: 2011-05-13
forum: Hardware
---

### Post by Daniell_dante on 2011-05-13
hi
i installed a fresh version of natty on my vostro 1510. I'm not able to use my wireless card driver i searched the live CD and i found a package i install it after rebooting my wireless card worked good but for making it work every time i restart my computer i have to turn on the switch of my card and wait till the ubuntu fully boots, if i don't do that i won't be able to use  my wireless card till i reboot and turn on the sitch again. it seems like the driver won't start until the next reboot. i searched a lot in forums i even tried the main way of ubuntu in the following link:
[http://ubuntuforums.org/showthread.php?t=1471028](http://ubuntuforums.org/showthread.php?t=1471028)
i used maverick before i had problem in that to but after reinstalling the bcwm-kerne.... it worked great. i did that in natty but it steal fails. i tried firmware-b43-installer but it contains error.
i appreciate any suggestions thanks guys

---

### Post by Daniell_dante on 2011-05-14
no answer?:(
OK i found new thing it seems like there is no problem with the driver. maybe natty is not able to find my wireless card although it gives me the proper address of it but when i turn the switch on it can't find the wireless somehow i think it is disabled or something like this.
thanks

---

### Post by Daniell_dante on 2011-05-15
as nobody answered me:(
i found the solution my self! so the best way is to install the maverick driver in natty, i read somewhere that upgrading will do the trick too after upgrading i will mark the post as solved

---

### Post by Daniell_dante on 2011-05-18
i didn't managed to upgrade the core but the 10.10 driver worked great no need to upgrade the post is solved by the one who asked thanks to the other members that never helped

---

### Post by fox-mulder on 2011-05-20
> **Daniell_dante said:**
> i didn't managed to upgrade the core but the 10.10 driver worked great no need to upgrade the post is solved by the one who asked thanks to the other members that never helped

since you solved it maybe you could tell us how you did it step by step?

:popcorn:

---

### Post by Daniell_dante on 2011-05-30
ok so if you want to know I'll tell ya buddy. i attached the ubuntu 10.10 driver so you may download it. 
1-open synaptic package manager search for bcmwl kernel source. 
2-mark it as a complete removal. then click on apply.
3-double click on the package you just download it. it will install it. 
4-you have to go to synaptic package manager and search again for bcmwl kernel source(just type bcmwl and you'll find it) click on the package you just installed it then from package menu choose " lock version" this will help you to keep the correct version of package even after upgrading. it's done

I hope it would help others
p.s. : download the package from the link below:
[http://www.4shared.com/file/jvWCLLDq/bcmwl-kernel-source_5604836bdc.html](http://www.4shared.com/file/jvWCLLDq/bcmwl-kernel-source_5604836bdc.html)

---

