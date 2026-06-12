---
title: "Can AMD Athlon XP 3000+ run flash?"
date: 2012-08-29
forum: Hardware
---

### Post by gaiusross on 2012-08-29
Hi, ive got Ubuntu to finaly work on my machine, but flash will not work. I have tried every fix I can find to make flash work. Installing the flash plugin etc to using a command line to install flash. Nothing works. Youtube has a black box in Firefox and chrome says it could not load shockwave flash. If i disable flash in chrome youtube works but says that it has to be downloaded, however any other site that uses flash videos do not work.

I'm quite new to linux so things will have to be explained to me as a newbi.

Thanks for your help.

---

### Post by Vicolaships on 2012-08-29
First of all, close all internet browsers
Open a terminal ; run 
```
sudo apt-get remove -y swfdec-mozilla mozilla-plugin-gnash gnash flashplugin-nonfree
sudo apt-get install -y flashplugin-nonfree
```
This will re-install the official Flash Player

Try again and tell us more if this doesn't work

---

### Post by gaiusross on 2012-08-31
I did it, but it didn't work.
Still same problem as before.

---

### Post by uconvert on 2012-10-22
I have spent the past two weeks trying to solve this issue. I listed my desktop PC with an Athlon XP Barton 2800+ CPU and installed Zorin 6.1 lite and then discovered the flash issue. I cancelled my ebay listing and I tried every current *buntu distro to no avail. I tested the RAM using memtest86 and it tested fine. I then concluded that one time when I overclocked the CPU, I must have somehow damaged the CPU and decided to scrap the system. I began disassembly (even removing the CMOS battery) and I then ran across a Puppy &#8220;Racy&#8221; CD which I had previously successfully tested due to a contrary b43 wireless issue on the same PC &#8211; I decided to make one last-ditch effort to save the PC, I plugged in a CD-ROM drive, and my wireless card and a stick of RAM, I booted Puppy and to my surprise, flash worked!

After some googling on the athlon CPU, I found these this bug report:[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/968759](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/968759)

and this thread: [http://askubuntu.com/questions/122306/flash-does-not-work-with-the-latest-updates](http://askubuntu.com/questions/122306/flash-does-not-work-with-the-latest-updates)

The last reponse #184 by Bernard Decock is what helped me and saved my PC from being tossed in the alley for garbage pickup. 

I copied libflashplayer.so to both /usr/lib/flashplugin-installer
and /usr/lib/mozilla/plugins and flash is working like it did two years ago. Hope this helps!

---

### Post by Troon2 on 2012-12-10
I'm a bit late to this thread, but I know the answer, which is referred to in uconvert's post above but is worthy of an explicit explanation here.

No, you cannot run the latest Linux version of the Adobe Flash plugin on an Athlon XP. This is because the plugin requires a CPU instruction set extension called SSE2, which the XP does not support.

I spent many hours trying to find out what was wrong with my system, nearly-identical in software setup to my son's P4 3.06 HT machine (yes, we are both state-of-the-2003-art!).

Your only solution is to dig out an old non-SSE2 version of the plugin - 10.2 works fine here. Adobe are not likely to fix this problem.

---

### Post by jcabello on 2012-12-24
Thanks Troon2.  I've also spent a lot of time with this same problem, and you saved me some more.=D>

---

### Post by jstauf86 on 2013-01-03
Is it time to retire my Athlon XP 2800+?

The older version of Adobe Flash Player (10.3 r183) runs good but should I be worried about security?
 
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_Flash_Player_versions_for_developers]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_Flash_Player_versions_for_developers")


BTW I have Chromium "old plugin" security warning disable.




I would like to thank all the members of Ubuntuforums.org for all the great support!!!

---

### Post by mastergunner on 2013-01-29
So if I follow the instructions in post 4 I will get flash to work in my old HP with an AMD XP-M CPU?

---

### Post by mastergunner on 2013-01-29
> **jstauf86 said:**
> Is it time to retire my Athlon XP 2800+?

The older version of Adobe Flash Player (10.3 r183) runs good but should I be worried about security?
 
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_Flash_Player_versions_for_developers]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_Flash_Player_versions_for_developers")


BTW I have Chromium "old plugin" security warning disable.




I would like to thank all the members of Ubuntuforums.org for all the great support!!!

How did you disable the "old plugin" security warning in Chromium?

---

