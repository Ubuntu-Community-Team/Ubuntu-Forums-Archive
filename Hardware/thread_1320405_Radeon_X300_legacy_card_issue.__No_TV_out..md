---
title: "Radeon X300 legacy card issue.  No TV out."
date: 2009-11-09
forum: Hardware
---

### Post by irishnewguy on 2009-11-09
Hey there folks. 

Ok, as the name suggests I'm a bit of a Linux newbie, but hey, rather be a linux newbie than all the windows time in the world right?

I also see a LOT of threads about ATI cards and Linux, the news is not good however.
Well, I'm using an old Dell Inspiron 6000 with an ATI Radeon X300, it's a piece of crap but an upgrade is just not justifiable. Might as well get a new PC. 

So.... I've down loaded the ati-driver-installer-9-10-x86.x86_64.run file from AMD.

I run it and I get a new folder on my desktop, fglrx-install.fc4a5k   but it's empty. (No hidden files either I checked) 

I tried the howto file using Gatos link but, something went wrong and I'm just not experienced enough to troubleshoot the process. The opening get library's bit failed, all of them, but when I went ahead with the thing anyway every other command most of the way down worked, so I'm guessing they are already installed. 

Anyway, here's the thing, I just want the TV out to work! Couldn't give a damn about anything else, soooo.......

If anyone could give me a hand, be much appreciated. 

Peace!!!!!!

---

### Post by grandtoubab on 2009-11-09
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-driver-ati/+question/87069](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-driver-ati/+question/87069)

Open a terminal
cd to the directory where atli is at then (could be your desktop : cd Desktop)
 ```
sudo sh ./ati-driver-installer-9-10-x86.x86_64.run
``` Type your password.
When the installer screen asks you what you want to do just hit enter,  same with the license. 
When it finishes close the window and in terminal
 ```
sudo aticonfig --initial
``` reboot again

---

### Post by irishnewguy on 2009-11-10
Hey there. 

Ok, I went with

sudo sh ./ati-driver-installer-9-3-x86.x86_64.run
As the driver download is 9-3 now. But.....

All i got was, extracting and all that, version not correct disto, set with --iscurrentdistro.

Thanks again for all the help!!!

---

