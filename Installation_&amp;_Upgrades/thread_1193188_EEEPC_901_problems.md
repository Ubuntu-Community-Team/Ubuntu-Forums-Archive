---
title: "EEEPC 901 problems"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by gno1209 on 2009-06-21
Hi, I am new to Ubuntu.  I just installed Ubuntu Netbook remix 9.04.  After installation, it was working fine, I switched to Desktop mode and installed all updates, after rebooting, there was nothing but the background on the screen (I left it on for 20 minutes and still nothing).  So I reformatted again and this time I only updated Firefox and rebooted, same thing happened.  Any ideas how I can get it to work?  Thanks for any suggestions.

---

### Post by CoffeaRobusta on 2009-06-27
I am experiencing very similar problems. Installed Jaunty 9.04 UNR on to a eeepc 900a. I also switched to the regular ubuntu desktop. Worked beautifully, except for flash content even after doing all the install firefox promted me for. Well the update manager kept popping up and asking if I wanted to do the updates (some of which were important, some only reccomended). I picked through and unselected the ones that seemed relavant (I don't have bluetooth for example). Nearly 100 MB later, I restart only to find the desktop background....no bar on top....no icons...nada. Right-click still pulled up a menu and I could create folders. Function key (F3 i think) pulled up the help window but it looked a little funny.

Restarting and going into the grub menu I saw that I now had the choice of 2 different kernels, as well as recovery options on both. Tried to load the newest kernal in recovery mode....but all options yeilded the same result. Tried to load the older kernel with same result.

I guess I could solve the problem by not doing the updates, but I would really like to get flash working on here. Any help out there?

I am a windows refugee that has only recently tried linux. The only other linux-based OS I have tried is puppy (installed on an old pII gateway solo, dualing booting with win 98se. So far, I have been very impressed with ubuntu until now. I would really like to get ubuntu running on my netbook.

thanks,
bill

---

### Post by nc_jed on 2009-06-27
at the risk of getting too far off topic, I have to agree with gno1209.  I found the UNR to be slow and just not quite ready for prime time (at least on my slow little 900).  i went to cruncheee instead (very lightweight GTK based Ubuntu variant).  Anyway, there's a live USB image of it if you want to give it a spin.

---

### Post by CoffeaRobusta on 2009-06-28
Ok, so  I reinstalled UNR from usb again. This time went straight to the terminal and did the sudo apt-get update and sudo apt-get upgrade thing. I turn off the update manager to do this because it would keep popping up after entering the sudo apt-get update command.

This time, on restart it was just fine. Had to still download some plugins to get flash and other media to play on firefox. Most of the time the system seems fine, but it's knd of glitchy playing back web content. I this something tweakable?

---

### Post by gno1209 on 2009-06-28
Thanks for some suggestions...I did some extensive research and found out there was a bug on the desktop-switcher...I downloaded it and installed it...and it works...I haven't found anything wrong so far...but I finally get to use the classic desktop...here is the link for the bug and download...
[https://bugs.launchpad.net/ubuntu/jaunty/+source/desktop-switcher/+bug/349519](https://bugs.launchpad.net/ubuntu/jaunty/+source/desktop-switcher/+bug/349519)

---

