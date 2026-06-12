---
title: "Pioneer DVD-ROM drive and Generic Monitor issues"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by smpb on 2006-10-21
Greetings everyone.
I just installed the desktop edition of Ubuntu 6.06.1 LTS and i've run into a few woes. There are two that i can't seem to figure out at all, and so i've decided to ask the community's help. I'll address them in order.

First off there's a problem with my DVD-ROM drive. I have a Pioneer DVD-ROM drive (DVD-120S) as a Secondary Slave in my system. As a Primary Slave i have a NEC DVD-RW (ND-3520A). And as Primary and Secondary Masters i have two hard drives.
I installed Dapper using the Live CD in my NEC drive. All went well except that my Pioneer drive apparently doesn't work. It's detected and present when i access all the drives available to me in Gnome, but, when i insert a disc in it nothing happens. When i insert a disc in the DVD-RW drive it works fine, the drive is mounted, Gnome opens a window showing me the contents of the disc, etc. The usual. In the case of the DVD-ROM drive nothing happens at all. The system just stops accessing the disc and does nothing more. Trying to mount the drive manually also doesn't help as mount just hangs doing nothing at all. I can't seem to find anything anywhere to help me. Any ideas?


My second problem is related to my monitor. As it happens with many people, Dapper's defaults insist in having the refresh rate of the monitor i'm using set at 60Hz. I have a 17-inch CRT that fully supports a 1024x768@75Hz mode. Now, a bit of research showed me that many people recommend that one should run the configuration for Xorg again inserting manually the horizontal and vertical frequency ranges as specified my the monitor's manufacturer. My problem is, this is an old monitor that fits 100% in the idea of a Generic Monitor. It has no brand at all associated with it and so, i have no idea who the manufacturer was. Much less the monitor's designation (the Windows XP installation present in this machine also sees it has a generic monitor). So i'm left without any ideia how to set the refresh rate at 75Hz.

Any help in any of these issues would very appreciated. Thank you all for your time.

---

### Post by Xizorbg on 2006-11-13
Hello there-

A temporary fix was reinstalling the HAL package from synaptic - but now my Pioneer (the same one) has stopped automounting. So, the drive is capable of cooperating, but something when it Ubuntu starts up is the problem.  Restarting HAL did NOT help.

Let me know if you come across any answers...good luck!

-X

---

### Post by Wim Sturkenboom on 2006-11-13
With regards to the monitor:

If you're sure that it can do 1024x768@75Hz, your monitor should also be able to do at least 60kHz horizontal refresh (I used [http://zaph.com/Modeline/](http://zaph.com/Modeline/) to calculate that value and came to 59.925; see below (relevant values bold))

```
[FONT="Courier New"]
Horizontal
        Pixels          *1024*
        Frequency       **59.925** kHz
        Sync            1.06 uS
        Blanking        3.17 uS
        Ratios          FP:1.0 Sync:4.0 BP:7.0
 
Vertical
        Pixels          *768*
        Frequency       ***75.0*** Hz
        Sync            50.1 uS
        Blanking        517.3 uS
        Ratios          FP:1.0 Sync:1.0 BP:10.0
 
General
        Dot Clock       75.75 MHz[/FONT]
```

You can edit /etc/X11/xorg.conf (need root permissions)
Search for VertRefresh and change the high value to 75. Next locate HorizSync. The high value for HorizSync must he greater than or equal to 60. Save the changes, logout and restart X.

PS Incorrect (too high) values might damage your monitor if it does not have a protection (which often is the case on old monitors). For that reason, stick to the value of 60 for the HorizSync.

---

