---
title: "Lucid Lynx eats more power ?"
date: 2010-05-05
forum: Hardware
---

### Post by hlxshady on 2010-05-05
Hi all,

This is a general question / survey, to see if any one of you have the same feeling as mine ...

My laptop:
Lenovo T400
Dual OS: Windows XP & Ubuntu 10.04

I just upgraded to 10.04 few days ago, and found that it eats a lot more power than 9.10.

In WinXP, I can watch a movie using P2P streaming service for more than 2 hours nearly 3 hours on battery.

And in Ubuntu 9.10, documentation works including internet could last more than 3 hours as well.

But having upgraded to 10.04, my laptop can barely last for 2 hours, and I wasn't doing any resource demanding work, but browsing some website without flash(in fact, the system was almost in an idle status).

Through the sensors-applet, when system is idle, I can see both cores of my CPU have a temperature roughly 6 ~7 celsius higher than 9.10.

I think this is a significant performance issue, but not sure if my laptop is a special case ...

---

### Post by hlxshady on 2010-05-06
seems I'm the only one suffering this problem ... ?

I tried again last night, the battery last < 2 hours while I was just using pidgin ...

---

### Post by weemanosd on 2010-05-06
Hi,

I have the same problem with 10.04.

In Win 7 my Thinkpad T400 can run for about 2,5-3 hours on battery but in Ubuntu the battery lasts less then 2 hours.

/weemanosd

---

### Post by bvanaerde on 2010-05-06
> **weemanosd said:**
> In Win 7 my Thinkpad T400 can run for about 2,5-3 hours on battery but in Ubuntu the battery lasts less then 2 hours.
*[COLOR="Gray"](That's not the same problem, as the tread starter is comparing Ubuntu 9.10 with Ubuntu 10.04.)[/COLOR]*
edit: Sorry, I have misread that part.. he's also comparing it with windows.

I've always noticed that Windows uses less battery power on my laptop though... but that maybe caused by power saving software that is enabled by default on Windows. There are a lot of people that claim Ubuntu to last longer on their laptop too. I guess it all depends on what you're running at that time. Power saving software makes a really big difference too.

---

### Post by hlxshady on 2010-05-06
Thanks for you guys' replies :)

About my laptop environment, I actually don't use any power saving software, either in Windows XP or Ubuntu.

Even a comparison within Ubuntu, I never used any power saving software in 9.10 too.
To make the battery run longer, I just switched off the bluetooth at boot (disable it in /etc/rc.local). And I seldom use the CD driver either.
That is all what I did to save power.

In 9.10, without using flgrx driver for my ATI video card, I couldn't turn on the 3D desktop effect. However, this third party driver caused a significant use of CPU when there is any graphical operations (such as multi-media and flash).
But my T400 could still run for 3 hours for documentation or programming work.

In 10.04, I was surprised that I don't even need to use flgrx and the desktop effect runs smoothly, without much use of CPU either!
Therefore I expected an even longer time that my T400 can run on battery. But the fact is, it is even shorter, even I was just using pidgin.

Comparing between ubuntu and Windows is not my point here.
The reason I mentioned Windows was to prove that my battery is completely healthy.
I actually am trying to compare the battery performance of 9.10 and 10.04.

---

### Post by P4man on 2010-05-06
Phoronix ran some simple tests and the results are pretty damning if you ask me:
[http://www.phoronix.com/scan.php?page=article&item=linux_windows_part2&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_windows_part2&num=2)

I dont think thats enough data or enough experimenting to draw any firm or general conclusions, but clearly its possible ubuntu drains your battery a whole lot faster. Hope they fix this.

---

### Post by psdk on 2010-05-24
Hi all,
I just want to second the comments about the excessive 'power drain' with Luicid 10.04.

I have a three day old brand new sony vpc EB1Z0E/B (Intel Core i5). Luicid installed like a dream and is lightning fast.

However today I had to do some work without mains power and using the battery. I nearly came unstuck. 

Under Windows 7 I get about 2 hours + battery life.
I was testing Skype with video (very slick).
After about 5 minutes the battery had dropped from 100% to 84%!
That gives me an estimated <1 hour battery life.

I also have two Macs. The batteries last from 4 to 5 hours!!

Are there any software apps to reduce the power consumption on Ubuntu?


Thanks,
Peter

---

### Post by farbird on 2010-05-24
sudo apt-get install laptop-mode-tools


[more here](http://bit.ly/cRfZKI)

---

### Post by farbird on 2010-05-24
u shd also use gconf-editor.. .search under apps, gnome-power-manager.

play around with the backlight and disks parameters.

---

### Post by bittner on 2010-06-08
I just wanted to confirm that I am also experiencing significant power life shortage with Ubuntu Lucid. Actually, there is now a popup sometimes telling me that my battery was kind of broken. That's why - before I read this thread - I believed the battery really was at the end of its life time (as of hardware). I'm running Lucid on a HP-Compaq 6735S which is about a year old.

Let me note that the screen is much brighter than it was with Karmic and that it now goes to maximum brightness when plugged in (that wasn't this way in Karmic by default, and that was terrible as you had a hard time reading stuff on the dark screen). So, the plain power management settings may already have an impact.

I don't know a solution (sorry for the bad news!), but I here is another hint if you want to try and analyse your power (mis)usage: PowerTOP
```
sudo apt-get install powertop
```
Also, there is some background reading on their project website ([LessWatts.org]("http://www.lesswatts.org/projects/powertop/")). Maybe someone of you finds it helpful.

---

### Post by docsmooth on 2010-06-22
cross-posting the results of my testing - comparing apples to apples, Lucid is definitely worse, and the "laptop-mode" and "powertop" suggestions aren't the complete answer.

[http://ubuntuforums.org/showthread.php?t=1515186](http://ubuntuforums.org/showthread.php?t=1515186)

---

### Post by philobyte on 2010-08-28
I just got an Asus 0721/Gateway LT32, (AMD Nile platform... athlon II Neo K125) and it is really sweet every thing except the ethernet driver worked out of the box, and the driver was a straightforward download and compile.  Performance with ATI 42xx is fabulous with open source drivers (that is a first for me...) so very happy... except... battery life sucks.  vendor claimed 6, I get 3 being very careful.

I thinking about returning it, as three hours is a bit of a downer, but it might not be huge deal.  On the fence...  but if I can fix, it will be perfect!


downloaded powertop, and started at around 18 watts.

-- dimmed display, and set cpu-governor to power save, now down to 17 watts.  I see the wakeups look really high to me.


< Detailed C-state information is not P-states (frequencies)
                                        1.71 Ghz     0.0%
                                        1300 Mhz     0.0%
                                         800 Mhz   100.0%



Wakeups-from-idle per second : 841.6    interval: 10.0s
Power usage (ACPI estimate): 16.9W (2.0 hours) (long term: 20.5W,/1.6h)

Top causes for wakeups:
  25.0% (215.4)D  chromium-browse
  26.3% (226.6)   PS/2 keyboard/mouse/touchpad interrupt
  16.5% (142.1)   npviewer.bin
  12.6% (108.7)   pulseaudio
   6.3% ( 54.4)   [kernel scheduler] Load balancing tick
   5.5% ( 47.0)   [ehci_hcd:usb1, ehci_hcd:usb2, ehci_hcd:usb3, ath9k] <interrup
t>

Any ideas how to:
   -- tune the mousepad to be less interrupty?
   -- I can close web pages to bring chrome and npviewer down, but any time I type, it seems to wake up 200 times per second.  Just seems a bit much. gets me down to 16 W :-)


power top also tells me that a bunch of devices are active 100%
of the time.  It says to press a key to fix, but the same message comes up later... ideas?

It came with 3 G of RAM for windows 7... I'm thinking about removing 1G to help with battery life?

---

