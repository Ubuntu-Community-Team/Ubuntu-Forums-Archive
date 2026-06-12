---
title: "Compaq presario r3000 boot issues after wireless update"
date: 2012-04-24
forum: Hardware
---

### Post by nicocuve on 2012-04-24
Help!! 11.10 installed on a Compaq laptop.
 
I had some wireless issues but installing b43 drivers fixed it.
However, boot up for 11.10 (with Unity) is very random. When it boots,  everything works fine but sometimes I need to reboot the PC 3 or 4 times  before it kicks in. 
When it doesn't boot, I am left with, either, a purple screen or a black  screen (with a flashing cursor in the top left hand corner) and the  laptop doesn't respond to any combination of keys pressed.
Laptop is a Compaq Presario R3200 series with NVIDIA GeForce4 420 graphics.
 
Live CD's always boot but once I have installed.
Usually, after install, when prompted to restart, the laptop fails to  boot first time.I have tried new nvidia drivers (96) with no change.
In order to boot I go in recovery mode and launch several checks and continue boot process.
 
I did'nt find any solutions on other forum but the problem seems to affect presario r3000 in general.
[http://askubuntu.com/questions/87187...presario-r3000]("http://askubuntu.com/questions/87187/11-10-randomly-fails-to-boot-on-compaq-presario-r3000")
[http://askubuntu.com/questions/92344...cursor-on-boot]("http://askubuntu.com/questions/92344/ubuntu-11-10-black-screen-with-blinking-cursor-on-boot")
 
This problem seems to be related to this issue :
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/192720]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720")
But I don't use the legacy drivers (only b43) and the issue should be fixed in 11.10...
 
I follow the instructions below as my broadcom card model is a BCM4318:
[https://help.ubuntu.com/community/Wi...ng_b43_drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers")
 
 
I'm new on Ubuntu and so far it'is pretty interesting but I really have no clue on the boot problem...
And if my laptop boots only when it wants, it wont be easy to use...

---

### Post by wildmanne39 on 2012-04-24
Hi, I seriously doubt it is the b43 driver it is most likely the nvidia driver, which one do you have installed and how did you install it.
Thanks

---

### Post by nicocuve on 2012-04-24
Hi,

I started to reinstall everithing from the beginning since my Ubuntu session only start every 10 times.
For now, the Nvidia driver is the 96 and I can select another one (96-updated).
How can I know the full driver version ?

I also found this :
[http://joeslifewithubuntu.blogspot.ca/2011/09/update-on-that-nvidia-96-driver-for.html](http://joeslifewithubuntu.blogspot.ca/2011/09/update-on-that-nvidia-96-driver-for.html)
But I don't understand what is Synaptic [FONT=&quot]package manager and how to use it to:
"[/FONT][FONT=&quot]search for NVIDIA 96 then mark the package to be installed . [/FONT]
[FONT=&quot] -Click apply and Synaptic will download & install. Reboot and there you go"

I also look for "Fix Suspend and Hibernation if you use a NVIDIA 96 driver" which might solve my problem but I'm not sure.
[/FONT][http://webcache.googleusercontent.com/search?q=cache:_7jt5ZTOSn0J:joeslifewithubuntu.blogspot.com/2010/12/how-to-fix-suspend-and-hibernation-if.html+&cd=1&hl=fr&ct=clnk&gl=ca&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:_7jt5ZTOSn0J:joeslifewithubuntu.blogspot.com/2010/12/how-to-fix-suspend-and-hibernation-if.html+&cd=1&hl=fr&ct=clnk&gl=ca&client=firefox-a)

---

### Post by wildmanne39 on 2012-04-24
Hi, that is an old card but it is supported with the 96 driver, in 11.10 synaptic is not installed but you can use software center to see what nvidia drivers are installed you only want the 96 driver, then make sure it is activated in additional drivers.

If it does not boot correctly with that driver then you may have to set nomodeset to make it boot right.

Here is a link for that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by nicocuve on 2012-04-26
Hi,
 
Thanks for your answers.
 
Actually it was a nvidia 96 driver issue.
I manage to resolve it by following this:
[http://thierrymachet.lescigales.org/opensource/procedure-linux_6005_Optimisations_Sleep-suspend/Optimisations_Sleep-suspend.html](http://thierrymachet.lescigales.org/opensource/procedure-linux_6005_Optimisations_Sleep-suspend/Optimisations_Sleep-suspend.html)
 
I also reinstall b43 drivers and it seemed to work fine.
 
I just tried to hybernate last night and today the computer does not boot anymore.
I don't even have the operating system selection panel...
 
Can I repare this by booting on the installation DVD ?

---

### Post by wildmanne39 on 2012-04-26
Hi, maybe but you should mark this thread solved and open a new thread with a descriptive title in the general or install and upgrade section.
Thanks

---

### Post by nicocuve on 2012-04-27
OK,
I went to the Ubuntu 12.04 Launch event in Montréal yesterday.
Everithing was working fine actualy.
 
Ubuntu on Compaq Presario R3000 is know perfectly running.
 
I can start to use it.
 
Thanks for your support ):P

---

### Post by wildmanne39 on 2012-04-27
Hi, I am glad you have it working good.
Enjoy

---

