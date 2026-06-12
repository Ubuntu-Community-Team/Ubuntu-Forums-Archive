---
title: "is Dell Vostro 5480 compatible with 14.04 ??"
date: 2015-10-19
forum: Hardware
---

### Post by ilan3 on 2015-10-19
Hi 
I'm new to this forum. 
i'm considering buying the Dell vostro 5480 and install on it ubuntu 14.04.
iv'e talked to the tech support guys at dell, 
they told me that this model has a driver support for 12.04 and not 14.04.
but checking the ubuntu certified hardware page  
here: [http://www.ubuntu.com/certification/hardware/201408-15449/](http://www.ubuntu.com/certification/hardware/201408-15449/)

this model seems to be checked and certified. 
So i'm a bit confused .. 
will this model work fine with 14.04 ?

---

### Post by oldfred on 2015-10-20
Do not know specifically.
But Dell released Sputnik to add drivers to 12.04. And somewhere I saw that all of that Sputnik was incorporated into 14.04.
Also many kernel, support software, video driver and UEFI/grub updates are in the newer versions of Ubuntu. Now, the point releases of the older LTS versions have many, but not necessarily all of the updates also. 

If it is now the newer Intel chips, you probably need the newest version of Ubuntu. Intel adds many updates to kernel & support software including video drivers. But it takes a while before accepted into Kernel & then a while before new kernels are included in a distribution. Then best to use newest Ubuntu and still may have to add ppa's to get the very latest available drivers.
       
Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
Now older
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

Other systems, but similar hardware type issues:
 Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)
Xubuntu 14.04 - GRUB2 nomodeset brings wrong screen resolution - Acer TravelMate 4740 with Intel HD Graphics
[http://ubuntuforums.org/showthread.php?t=2240620](http://ubuntuforums.org/showthread.php?t=2240620)
kernel 3.19 which is implemented with all needed intel graphic stuff
[http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951](http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951)

---

