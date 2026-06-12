---
title: "ATI Radeon Xpress 200M proprietary driver"
date: 2011-01-16
forum: Hardware
---

### Post by shatanas on 2011-01-16
This has started off as a problem with frame rates whilst running WoW on Wine, but I am reinstalling WoW at the moment so I'll post a thread about that later (if need be).

I looked at some other posts, but hardly understood anything and the ATI website expects a lot of knowledge to install the driver. This is what raised my concern:
> Are you getting this slow frame rate all the time? Or only when attempting to run games in Wine? IF the latter, what video card/chip are you using?  If it's one of the  "legacy" ATI cards/chips, you're using the open source drivers and  you're not going to get decent gaming frame rates   (the latter for me)

Can anyone explain what I need to do to get a functioning driver for ATI Radeon Xpress 200M series to run WoW smoothly?

1.6Ghz x2
1gb Ram (256mb for graphics)
Ubuntu 10.10

---

### Post by bailbath on 2011-01-16
I don't think that chipset is suited to gaming. You may spend a lot of time trying to find out you will get nowhere.
[http://www.notebookcheck.net/ATI-Radeon-Xpress-200M.2175.0.html](http://www.notebookcheck.net/ATI-Radeon-Xpress-200M.2175.0.html)
Sorry to be negative but I would prefer some one to tell me the truth if I was asking.
Ian

---

### Post by efflandt on 2011-01-16
Is that an old laptop?  Many legacy ATI cards in desktops are serviceable with the default drivers.  A 200M may be fine for general use, but for gaming, the only thing that will speed it up is different video (ie, a newer computer).

For example my old Athlon64 3200+ (2 GHz) desktop with ATI X1300 is not fast enough for something like alien arena, but works fine for things like supertuxkart.  An old Sempron 3300+ laptop (really 2.2 GHz) gets video tearing in supertuxkart.  Although, that might have been because I borrowed some RAM from it, so it only had 512 MB with some of that shared for video.  While not a good general video benchmark, glxgears gives some example of the difference between these:

Athlon64 w/ATI X1300 default video drivers
glxgears 64-bit Lucid
9189 frames in 5.0 seconds
9831 frames in 5.0 seconds
9847 frames in 5.0 seconds
9847 frames in 5.0 seconds
9848 frames in 5.0 seconds

Sempron w/ATI 200M default video drivers
glxgears 32-bit Lucid
2178 frames in 5.0 seconds
2205 frames in 5.0 seconds
2092 frames in 5.0 seconds
2111 frames in 5.0 seconds
2127 frames in 5.0 seconds

---

### Post by shatanas on 2011-01-16
> **bailbath said:**
> I don't think that chipset is suited to gaming. You may spend a lot of time trying to find out you will get nowhere.
[http://www.notebookcheck.net/ATI-Radeon-Xpress-200M.2175.0.html](http://www.notebookcheck.net/ATI-Radeon-Xpress-200M.2175.0.html)
Sorry to be negative but I would prefer some one to tell me the truth if I was asking.
Ian

Thanks, but I am only enquiring because it has worked fine for me under Windows XP. To break it down further:
I experienced no lag in outdoor PVE and dungeons, but had trouble in populated places such as SW
This was the same in Northrend.

I suppose my graphics card (or RAM) are not quite up to standard, but they managed to run the game smoothly in windows, why is this not so in Ubuntu? -it really was not as ridiculous as the 3fps I am experiencing at the moment.

---

### Post by bailbath on 2011-01-17
> **shatanas said:**
> Thanks, but I am only enquiring because it has worked fine for me under Windows XP. To break it down further:
I experienced no lag in outdoor PVE and dungeons, but had trouble in populated places such as SW
This was the same in Northrend.

I suppose my graphics card (or RAM) are not quite up to standard, but they managed to run the game smoothly in windows, why is this not so in Ubuntu? -it really was not as ridiculous as the 3fps I am experiencing at the moment.

Well I guess the answer to that is windows xp is the most popular os in the world if it didn't work WOW would not be as popular as it appears to be! I don't know enough about the game to say but can you reduce some of the effects etc to get higher frame rates?
The real answer is to treat yourself to a nice new computer:D

---

### Post by shatanas on 2011-01-17
Ahah, if only I had the money, come the day of my birth- maybe. I did try reducing the options etc. but it hardly had any effect.

To further ado, I have recently discovered that quite a few programs don't work- I assume because I don't have the driver for my graphics card- such as kartuxracer (or whatever it's called) and 3D chess. Intuitively I think this is due to the system not being able to render 3D or something?

How do I install the driver for ubuntu!? 

~gahhhhhhh

---

### Post by shatanas on 2011-01-20
Bump

---

### Post by Yellow Pasque on 2011-01-20
Did you try to install the proprietary ATI driver (aka Catalyst)? If so, follow this to fix your graphics: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by shatanas on 2011-01-20
urmm no, I haven't actually googled ATI catalyst for ubuntu, just proprietary drivers ATI and couldn't understand a thing on their website...

I have actually checked right now and got this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
what do they mean that the open-source driver will not as fast as the closed source and what is better dual-head support!?

Also, is it better to install the closed-source one, as I really do not want laggy graphics

Sincerely, ubuntu noobie

---

### Post by shatanas on 2011-01-20
urmm no, I haven't actually googled ATI catalyst for ubuntu, just proprietary drivers ATI and couldn't understand a thing on their website...

I have actually checked right now and got this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
what do they mean that the open-source driver will not as fast as the closed source and what is better dual-head support!?

Also, is it better to install the closed-source one, as I really do not want laggy graphics

Sincerely, ubuntu noobie

---

### Post by shatanas on 2011-01-20
urmm no, I haven't actually googled ATI catalyst for ubuntu, just proprietary drivers ATI and couldn't understand a thing on their website...

I have actually checked right now and got this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
what do they mean that the open-source driver will not as fast as the closed source and what is better dual-head support!?

Also, is it better to install the closed-source one, as I really do not want laggy graphics

Sincerely, ubuntu noobie

---

### Post by shatanas on 2011-01-20
urmm no, I haven't actually googled ATI catalyst for ubuntu, just  proprietary drivers ATI and couldn't understand a thing on their  website...

I have actually checked right now and got this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
what do they mean that the open-source driver will not as fast as the closed source and what is better dual-head support!?

Also, is it better to install the closed-source one, as I really do not want laggy graphics

Sincerely, ubuntu noobie

---

### Post by shatanas on 2011-01-20
urmm no, I haven't actually googled ATI catalyst for ubuntu, just  proprietary drivers ATI and couldn't understand a thing on their  website...

I have actually checked right now and got this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
what do they mean that the open-source driver will not as fast as the closed source and what is better dual-head support!?

Also, is it better to install the closed-source one, as I really do not want laggy graphics

Sincerely, ubuntu noobie

---

### Post by shatanas on 2011-01-20
urmm no, I haven't actually googled ATI catalyst for ubuntu, just   proprietary drivers ATI and couldn't understand a thing on their   website...

I have actually checked right now and got this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
what do they mean that the open-source driver will not as fast as the closed source and what is better dual-head support!?

Also, is it better to install the closed-source one, as I really do not want laggy graphics

Sincerely, ubuntu noobie

---

