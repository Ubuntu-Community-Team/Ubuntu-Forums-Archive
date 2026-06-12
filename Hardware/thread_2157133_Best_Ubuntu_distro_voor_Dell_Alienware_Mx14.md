---
title: "Best Ubuntu distro voor Dell Alienware Mx14"
date: 2013-06-24
forum: Hardware
---

### Post by Onno_vdS on 2013-06-24
Hi,
I have a Dell Alienware MX14 laptop. Designed for MS Windows 7. Now I was thinking about running dual boot with Ubuntu. What is the best Ubuntu distro to use for this? I thought I try the recommend 64 bits ubuntu-12.04.2-desktop-amd64.iso, my machine is fairly new so I thought this could work. This however turned out to be not the right distro for me. This version fails to boot succesfully almost without exception. I see some messages in the consoles, a login prompt which disappears. Then there is a cursor blinking on a black screen. There is a mouse pointer which I can move. I can press all keys, return key, esc, cntrl alt delete, no matter, the screen remains black. At times I do see the Ubuntu login screen. I can enter my username and password and login succesfully. This is the exception however. On average I will see black screen 9 out 10 times. So It basically doesn't work as I don't want to hard reset my machine that often just for the purpose of starting Ubuntu.

Shut down is also a very complicated affair. Pulling the plug seems the only way.

So ubuntu-12.04.2-desktop-amd64.iso seems to be the wrong choice. What is recommended for my machine? Will 32 bits work? Should I use a previous version of Ubuntu? Which? Or is my machine just not supported? How can I find out.
Thanks in advance.

---

### Post by oldfred on 2013-06-24
The 64 bit version is probably the correct version, but you may have video issues or need other boot parameters. That is works sometimes is unusual and makes it more difficult to resolve. 

Does it have a dual video system? Specs I found show the dual video which often is an issue. Can you set it for either Intel or nVidia.

 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)
Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)
The problem was caused by another technology by Intel called the Integrated Network Interface Controller (NIC) that was conflicting with my USB controller that prevented my LiveUSB from working

The new nVidia driver only has some support for Optimus and I think you can only get it working with the very newest (still in development) 13.10 as that has the kernel that works with it.
Many have just installed with Bumblebee and that works for them.

---

### Post by Jack_Yuan on 2013-08-03
I have the alienware m14x r1. I've got it set up with a partition for windows, a partition for ubuntu and a data partition. Pretty much everything installs and runs out of the box in 13.04. My only issue is getting hdmi output and installing the nvidia drivers. I've followed the instructions on [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html) but I'm still having issues. It works but as soon as I reboot I'm stuck and it doesn't work anymore. Also when I plug in my usb hug that has my keyboard and mouse the io seems to seriously lag and stutter. It's really weird. I've reinstalled quite a few times trying to get everything to work but still no success with my current setup. On the other hand, if it's just the laptop with no hdmi out for a second monitor then everything else pretty much works out of the box and is pretty good. Hopefully this helps.

---

### Post by Yellow Pasque on 2013-08-03
alienware m14x has optimus/hybrid graphics: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

