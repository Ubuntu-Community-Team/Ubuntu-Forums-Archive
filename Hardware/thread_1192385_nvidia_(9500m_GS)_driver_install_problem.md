---
title: "nvidia (9500m GS) driver install problem"
date: 2009-06-20
forum: Hardware
---

### Post by threetwoone on 2009-06-20
OK, so I'm currently dual booting Windows Vista 64-bit and Ubuntu 9.04 64-bit (well windows 7 is on there somewhere but GRUB can't see it...), on an Asus G1Sn-B1 with a nvidia 9500m GS.  I can't seem to get the nvidia driver properly installed.

First, I tried going through System > Administration > Hardware Drivers and tried both the 180 and the 173 version of the nvidia accelerated graphics driver.  Neither worked.  Next I tried using envy that also failed.  I used the KDE gui though because the gnome one doesn't work...but i don't think that would matter.  I think i may have also done it with command line but i don't really remember everything i've tried.  Then I tried using the installer from the nvidia site...that also failed.

The only plus is that is was the same problem every time :mad:.  This pops up after restart every time:

Ubuntu is running in low graphics mode. The following error was encountered:
 (EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
 (EE) Failed to load module "nvidia" (loader failed, 7)
 (EE) No drivers available

I saved the logs but its a giant mess of 8 files and I have no clue what to look for in them.  I'll post them if anyone thinks they could be helpful.

I'm not sure if i did something wrong or if I'm missing something obvious.  I've read just every forum on the problem that i could find here and everything I could find on google, all a big bunch of fail ](*,).

I'm still learning the ropes of Ubuntu/linux in general, my goal is to eventually use it exclusively but I have a pretty bad track record with it.  I failed to get the ball rolling with Dapper (way back when) and Hardy (couldn't even get that one installed :rolleyes:).

P.S. I'm willing to try just about anything, I don't have anything important on this partition, so worst case scenario I just reinstall.

---

### Post by skooter on 2009-07-12
This is a bug in the Linux kernel - if you have more than 2 GB of RAM in your computer... The bug has been reported and hopefully fixed very soon.

> I am almost finished writing the new kernel PCI IOMEM allocation system which will solve these issues. It should land for either mainline .30 or .31, time permitting... Or later ...
Source: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926)

Until then you can patch your kernel yourself. But be careful. Read and post to this thread: [http://newyork.ubuntuforums.org/showthread.php?t=849395](http://newyork.ubuntuforums.org/showthread.php?t=849395)

---

### Post by DystaN on 2010-12-28
Im using Ubuntu 10.10 NetBook edition , I have after installation  and updates  actually downloaded everything to run the graphic goodies from linux as I am very fond of it. ( Special Effects thingie things )

Everything was running slow ( desktop cube and even the programs interfaces ) and my graphic card didnt seem to be used to the full of its extension so here it is my solution :

My computer ASUS G1SN graphic card 9500m GS :

[http://img831.imageshack.us/i/asusgamingjapan.jpg/](http://img831.imageshack.us/i/asusgamingjapan.jpg/)

After trying for many days struggle with command lines and everything I finally figured out ( Trial and Error ) that the problem with my Ubuntu OS installation was a version of the driver.  
Trying from the first one to the last , I finally found out the one that would fit me the best , and here it is what I have downloaded from Synaptic Package Manager:

[http://img8.imageshack.us/i/nvidiaconfig.png/](http://img8.imageshack.us/i/nvidiaconfig.png/)

In case you cannot see the image , I have downloaded every single package I found that was 1.8.0 and it worked perfectly on my laptop. I cannot tell you the ways Ive  been for I have gone from 1.8.5 to 1.7.3  and back again , trying to figure out what would fit me the best and that just happened to be 1.8.0 .

Ive been using Ubuntu and the linux system for only a few days and I cannot help you anymore then this for now , hopefully in the future , this is what I got from my experience.

---

