---
title: "netbook-launcher problem after UNR install"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by Uejji on 2009-05-16
Hello everyone.  I did some searching to see if this problem had been posted before, but I wasn't able to find it, so please forgive me if I'm asking something that's been resolved here before.

I'm a 10 year Slackware Linux veteran, though new to Ubuntu, so I know my way around a Linux system pretty well.

I ordered a Lenovo Ideapad S10e to replace my faithful, but aged, laptop -- a Toshiba Satellite Pro with a Pentium 3 700, 192 MB RAM and a 800x600 screen.  I've heard and seen a lot of good things about Ubuntu Netbook Remix, and I wanted to try it on my netbook when it gets here.  In the meantime, I wanted to put it on my laptop to try it out in the meantime, and plus if the laptop ran well with it I'd keep it on it as the primary OS.

I didn't realize before that UNR was pretty heavily dependent on GNOME, so I started with Xubuntu 9.04 (thinking that the lower requirements of Xfce would help out on this sytem).  After the installation, I let the package manager upgrade all the packages with no errors, then I ran 'sudo apt-get install ubuntu-netbook remix' and when that was all said and done, rebooted the laptop and logged into the GNOME session.

Things came up as expected, although I'm unable to interact with netbook-launcher with the mouse.  If I click on it, I'm able to navigate using the arrow keys, tab and enter, and all functions work as expected, though without mouse support, it's pretty much useless to anyone at this point.

I ran through a pretty lengthy process of rebuilding netbook-launcher from source (including installing several dev packages), but no change whatsoever.

If necessary, I can download the regular Ubuntu 9.04 CD and try it from that, but if there's any way to resolve this without another reinstall, that would be great.

I'll also note that the laptop is unable to boot from USB and only has a CD drive, so the complete UNR images will not work for me.

EDIT: I forgot to mention that if I launch netbook-launcher from a terminal, I receive several error messages "(netbook-launcher:32130): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion 'id < id_pool->array->len' failed".  I've used gconf-editor and forced netbook-launcher to run in low graphics mode but with the same result.  Is this possibly a problem in clutter?

---

### Post by Uejji on 2009-05-17
Sorry to double post.

The laptop uses the savage driver in 16-bit color (as is necessary to enable DRI).  I tweaked xorg.conf a bit to change the accelmethod to EXA (default is XAA; UXA is not supported on savage) but with no change.

Does anybody have any suggestions?

---

### Post by snowpine on 2009-05-17
Here are the system requirements for Ubuntu:

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

The netbook launcher is an extra layer on top of Ubuntu Gnome, so inflate the above requirements upward if you want NBR. The lowest-spec netbook on which NBR is tested is the original Asus eee, which is a 900mhz celeron with 512mb of ram.

For an old Pentium 3 laptop with only 192mb of ram, I would not recommend Ubuntu (or any distro based on it). Personally, I would try Debian with the LXDE or Xfce environment, though if you are experienced with Slackware, that might be worth a try too. 

ps Mouse not working sounds like an xorg.conf problem.

---

### Post by Uejji on 2009-05-17
Thanks for the reply.

The mouse is working fine.  I am just unable to interact with netbook-launcher using the mouse.  I am able to interact with all other components of GNOME and all other launched software using the mouse just fine.  If launched from a terminal, netbook-launcher begins to spit out the mentioned clutter error when attempting to interact with it using the mouse.

Is anyone familiar enough with clutter or the netbook-launcher codebase to know if either of them require some degree of video acceleration to operate that savage just does not provide?

In other words.  Ubuntu runs great on the laptop except for netbook-launcher, which is a huge anomaly in this situation.

---

### Post by Brandon Williams on 2009-05-17
Are you running compiz or metacity as the gnome window manager? UNR does not work well with compiz, but the UNR install will probably have set you up such that your window manager is metacity. Still, it's worth double checking.

---

### Post by Uejji on 2009-05-17
Hey.

Metacity is the window manager in use, and compositing in metacity is turned off (I doublechecked in gconf-editor).

---

### Post by Uejji on 2009-05-18
Hey everyone.  I pretty much gave up on netbook-launcher and created a little hybrid system where I run without netbook-launcher.  My ideapad came in today and I set it up with the same system.

I made a youtube video on the ideapad to demonstrate.  Maybe someone else will see it and think it awesome enough to use it for themselves too.

[http://www.youtube.com/watch?v=DlDKoU-VeRw](http://www.youtube.com/watch?v=DlDKoU-VeRw)

---

### Post by madmax1735 on 2009-11-15
ahh did anyone figure out a solution to this one.... i am facing the same issue on ubuntu 9.10 while using gnome-shell.

check my post here

[http://ubuntuforums.org/showthread.php?t=1313808](http://ubuntuforums.org/showthread.php?t=1313808)

---

### Post by Uejji on 2009-11-15
Hey man.  People were generally unhelpful about this problem.

The best I can gather (and I'm not even 100% sure about this) is that Clutter requires certain graphics drivers to operate properly.

What graphics card does your computer have?

---

### Post by richandcreamy on 2009-11-16
I can't launch anything by mouse clicking either! Any tests we can do to help figure this problem out?

---

### Post by J V on 2009-11-17
This bugs been around for a while now... it has to do with graphics drivers is all I know...

You'd think they would make the most important part of the distro a bit more dependable woulden't you?

Edit: Bug has been filed: [https://bugs.launchpad.net/netbook-remix/+bug/460849](https://bugs.launchpad.net/netbook-remix/+bug/460849)

---

### Post by gavintlgold on 2010-03-13
I know I'm bumping an old thread, but I'm getting the same problem. Very frustrating as I was counting on the netbook-launcher being a nice interface for my less-geeky family.

I assume no one has found a solution to this problem that involves the launcher working.

---

