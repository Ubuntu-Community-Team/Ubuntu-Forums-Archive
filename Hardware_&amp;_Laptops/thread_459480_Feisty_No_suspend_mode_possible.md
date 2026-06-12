---
title: "Feisty: No suspend mode possible"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by UJones on 2007-05-30
Hi all!

After not getting any response on my thread in the German forum I give it a try here. Thus I hope anyone of you can help me.

First, my hardware specifications of my notebook:
cebop HEL750, 1024MB RAM, Pentium M750 1.86GHz, Intel 915GM graphics chip, Ubuntu 7.04 (Feisty Fawn Final)

I'm using Feisty since the beta version was released and upgraded it then day-by-day to the final. Before I was using Dapper Drake, where all suspend modes - as well as Suspend-to-RAM as Suspend-to-Disc - were working out-of-the-box.
Two weeks ago, I was using the suspend modes for the first time. Didn't work, I had also in mind that there was lately an update of HAL:
- hal_0.5.9-1ubuntu2~feisty1_i386.deb
- hal-device-manager_0.5.9-1ubuntu2~feisty1_all.deb
- hal-info_20070402-1ubuntu1~feisty1_all.deb
If I'm not mistaken, is the power management connected to this. But my hardware didn't change from 6.06, so why should the new HAL be incompatible to the same hardware??!

It doesn't matter which suspend mode I'm using, placing the notebook in a suspend mode works fine. Independent of the kind of suspend mode it's always the same behaviour when waking the system up:
The loading symbol for the mouse pointer is showing up (circle with moving points) and the CPU cooler of the notebook runs up (=high CPU load) but nothing is happening. I don't see any login screen.
The only thing helping in this situation is pressing the power button of the notebook to shutdown the system (you hear the shutdown sound but when the splash screen comes up it looks like some kind of graphic malfunction).

Also the indication of the battery isn't working properly since some time (start moment could be approximately the time of the HAL update but I can't say it for sure). It's showing that I'm in mains operation although I'm using my battery ... I already reinstalled the packet gnome-power-manager but this didn't help either.


Anyone who's got an idea for the reason(s) ?
As mentioned above the boot splash isn'nt shown correctly when shutting down (only visible in Suspend-to-Disc).
So could it be the graphics driver? My graphics chip is already biased (Intel GMA915 --> resolution problem).

I'm thankful for any help or hint how to come behind this behaviour to solve the reason.


Best regards,

Johannes



Link to the syslog of Suspend-to-RAM: [http://www.ubuntuusers.de/paste/11127/](http://www.ubuntuusers.de/paste/11127/)
Link to the syslog of Suspend-to-Disc: [http://www.ubuntuusers.de/paste/11128/](http://www.ubuntuusers.de/paste/11128/)

---

### Post by pipatron on 2007-06-07
I had about the same problems with my X40. The problems were in the SD-card reader modules. After removing them:

rmmod sdhci
rmmod mmc_block
rmmod mmc_core

and installing 'uswsusp', and running

s2ram -f -a3

it worked. Now trying to find how to make this happen in the most 'ubuntu' way.

---

### Post by UJones on 2007-06-07
Hi pipatron,

thanks for your post. Strange thing: Although I have an SD-card reader the modules were not running. (message: *ERROR: Module xxx does not exist in /proc/modules*)

Then I played with s2ram and s2disk and both work fine. Only thing with s2disk is that the resolution is not correct when waking up. It has 1280x1024 instead of 1680x1050. Could be a problem with my intel GM915 graphics chip.

So it's a bug in Ubuntu? Is Ubuntu using the wrong command??!

---

