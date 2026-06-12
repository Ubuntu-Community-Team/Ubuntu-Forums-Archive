---
title: "Temperature is OK but System Freezes Randomly"
date: 2008-06-23
forum: Hardware
---

### Post by xp_newbie on 2008-06-23
I built a new system, made of the following components:

**OS**: Ubuntu 8.04
**Motherboard**: ABIT IP35 Pro (LGA 775), BIOS ver. 14
**CPU**: INTEL Core 2 Quad Q6600 Kentsfield 2.4GHz 2x4MB L2
**Heatsink**: Thermalright Ultra-120 Extreme
**RAM**: 8GB, made of 2 x G.SKILL 4GB (2 x 2GB) P/N F2-8000CL5D-4GBPQ
**Video**: **[COLOR="Red"]ASUS EN8600GT SILENT/HTDP/256M[/COLOR]**
**HDD**: 2 x SAMSUNG SpinPoint T Series HD501LJ
**DVDRW**: ASUS DRW-2014L1T
**PSU**: CORSAIR CMPSU-550VX 550W
**Case**: Antec Solo Black/Silver

I actually managed to successfully complete Ubuntu 8.04 installation.

But as soon as I get into doing something productive (browsing the net using Firefox, for example), the system FREEZES.

This doesn't happen when Vista is running on the same exact hardware (dual-boot).

I described my problem in detail in the following thread:

[http://tinyurl.com/458she](http://tinyurl.com/458she)

So far, I couldn't find a solution to the problem. It's not the mouse, it's not the KVM switch, it's not memory... Some suggest it is the graphics card, but how could I verify this? and if it is, how do I solve the problem. Surely the hardware is not defective (it works flawlessly with Vista), so this must be a driver problem, right? If so, where do I find the bug-free driver for my graphics card (**[COLOR="Red"]ASUS EN8600GT SILENT/HTDP/256M[/COLOR]**)?

Thanks,
Alex

---

### Post by Odrodzona-Sarmacja on 2008-06-23
There is entire list of bugs freezing Ubuntu. Memory issue. Swap partition issue. Gamin server issue. Flash plugin issue. Power Manager issue. They all are fixable more or less. Also you need uninstall lots of network software from Ubuntu and any overflow of screensavers and such programs. Then you can use Ubuntu without freezes when you boot up your Ubuntu without networking. If you boot up with networking, then be sure you will get freeze eventually, but not so often. Also booting up without networking and enabling it then makes freezes less frequent too. Also having more graphic memory on video card makes freezes also less frequent. Also changing programs on Ubuntu using rendering for programs, which do not use rendering makes also freezes much less frequent of some reason.

---

### Post by xp_newbie on 2008-06-23
> **Odrodzona-Sarmacja said:**
> There is entire list of bugs freezing Ubuntu. Memory issue. Swap partition issue. Gamin server issue. Flash plugin issue. Power Manager issue. They all are fixable more or less. Also you need uninstall lots of network software from Ubuntu and any overflow of screensavers and such programs. Then you can use Ubuntu without freezes when you boot up your Ubuntu without networking. If you boot up with networking, then be sure you will get freeze eventually, but not so often. Also booting up without networking and enabling it then makes freezes less frequent too. Also having more graphic memory on video card makes freezes also less frequent. Also changing programs on Ubuntu using rendering for programs, which do not use rendering makes also freezes much less frequent of some reason.
You're kidding, right? :)

Indeed I noticed that freezes occur mostly in combination with mouse Firefox accessing the internet and some mouse movements.

Please don't tell me that I need to replace the entire computer (or Ubuntu 8.04) in order to have a useful system (I need it for work, not gaming).


Thanks!

---

### Post by Tomatz on 2008-06-23
Open a terminal and type:

```
metacity --replace
```

This will disable compiz temporarily (till next boot). So we can see if the problem is with compiz, :)

---

### Post by xp_newbie on 2008-06-23
> **Tomatz said:**
> This will disable compiz temporarily (till next boot). So we can see if the problem is with compiz, :)
Hmmm... I am not sure I am using compiz. This is because when check System > Administration > Hardware Drivers I see only one item there:

> NVIDIA accelerated graphics driver (latest cards) - not enabled - not in use

Which tells me:
[LIST=1]
[*]My Out-of-the-Box Ubuntu 8.04 (plus updates) is using the nVidia drivers packaged with Ubuntu, not the ones from nVidia
[*]It seems that I am not utilizing any 3D functionality (compiz?)
[/LIST]

How do I check if I am using compiz?

Update: I just enabled that nVidia "restriced driver" - Wow! I like the effects (is this the so called "compiz"?)

No freezes yet (touch wood). I am attaching an image of my temperature sensors:

[IMG]http://img55.imageshack.us/img55/823/tempstc0.png[/IMG]

the temperature values (left-to-right) correspond to the following sensors (top-to-bottom):

[IMG]http://img366.imageshack.us/img366/4935/screenshotsensorsappletyb2.png[/IMG]

Thanks!

---

### Post by Tomatz on 2008-06-23
> **xp_newbie said:**
> Hmmm... I am not sure I am using compiz. This is because when check System > Administration > Hardware Drivers I see only one item there:



Which tells me:
[LIST=1]
[*]My Out-of-the-Box Ubuntu 8.04 (plus updates) is using the nVidia drivers packaged with Ubuntu, not the ones from nVidia
[*]It seems that I am not utilizing any 3D functionality (compiz?)
[/LIST]

How do I check if I am using compiz?

Thanks!


Enable your graphics drivers to see if this sorts the issue if not post back ;)

PS If your drivers aren't enabled/installed then compiz won't be enabled

---

### Post by xp_newbie on 2008-06-23
> **Tomatz said:**
> Enable your graphics drivers to see if this sorts the issue if not post back ;)
I did - and updated my post above. It's nice! :)

And... I think that it solved the freezing problem... touch wood. Too early to declare victory but you can trust that I will post an update if this didn't really solve the problem.

BTW, I downloaded the newest drivers from nVida but haven't installed them yet because... "if it ain't broke, don't fix it". :)

:guitar:

---

### Post by Tomatz on 2008-06-24
> "if it ain't broke, don't fix it".

Your learning ;)

It's always better to use apps/drivers out of the repos unless they are seriously out of date or broken.


If you want to play with compiz in a terminal type:


```
sudo apt-get install compizconfig-settings-manager
```

Then go to ***system, preferences, advanced desktop effects settings***

You can enable your cube and other cool effects then.


:guitar:

---

### Post by Odrodzona-Sarmacja on 2008-06-25
> **xp_newbie said:**
> You're kidding, right? :)

Indeed I noticed that freezes occur mostly in combination with mouse Firefox accessing the internet and some mouse movements.

Please don't tell me that I need to replace the entire computer (or Ubuntu 8.04) in order to have a useful system (I need it for work, not gaming).


Thanks!

This RDI (rendering issue) is something that happen because of networking, if you fixed all the other freezing giving issues like swap, memory and gamin. I solved my freezings by removing network-manager and adding two lines in interface in /etc/network/interfaces and if i have any problem with working internet i just do "sudo ifup eth0" to get connection back. Here is my solution:
[http://ubuntuforums.org/showthread.php?t=840686](http://ubuntuforums.org/showthread.php?t=840686)

---

