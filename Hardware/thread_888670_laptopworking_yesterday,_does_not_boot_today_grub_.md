---
title: "laptop*working yesterday, does not boot today: grub error 18"
date: 2008-08-13
forum: Hardware
---

### Post by nexx on 2008-08-13
My LG LU20 subnotebook was booting perfectly well (though slowly) when suddenly yesterday this grub error 18 happen. Could it be related to my old phoenix bios. My LG LU20 is a very crappy laptop, it is very fragile, in three years I had to change the sound card, the processor and the fan. The fan is again making a lot of noise and the processor heats a lots when playing videos. The only positive points is that ubuntu runs very well on it and the machine is so light and slim.

Any ideas on how to repair that grub thing witout having to reinstall ? Is this computer simply dying ? 

Anyway I am seriously considering buying a SONY VAIO,

---

### Post by jmontelius on 2008-08-17
I had a similar problem. After having had problems with bad memory and a corrupt disk that I resolved I got Grub Error 18. I booted from the live CD and ran grub to set the boot sequence right but I still got Error 18. After having saved what I needed I made a clean install of Kubuntu 8.04 and still got Error 18. 

Only after doing a partitioning of the drive with a /boot partition of 512Mbyte as the first partition did it work. Very strange since the machine has worked with Edgy and Feisty and then also with Hardy. Some how even with the clean install the boot segments were placed in a location where they could not be read.

What you should do first is to boot from the Live CD and try to restore grub:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by nexx on 2008-08-17
I did a clean install. Made a boot partition of 300 Mb at the beginning of the hard drive, then a swap partition, then the main partition. Now after reinstalling, everything seems to work fine (except for a few internet station that I cannot open even with all the codec installed, it is strange because befor reinstalling I could listen to these streams).

---

