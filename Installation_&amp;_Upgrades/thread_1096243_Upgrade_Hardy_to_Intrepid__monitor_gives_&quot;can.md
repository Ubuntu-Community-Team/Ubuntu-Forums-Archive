---
title: "Upgrade Hardy to Intrepid:  monitor gives &quot;cannot display this video mode&quot;"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by sbradley07 on 2009-03-14
I've search this and other forums and can't figure out how to fix my problem.  I have an old Dell Dimension with a 1704fpvt flat screen monitor.  Have been happily running Hardy for quite some time and today decided to upgrade to Intrepid.  After the upgrade, I get "1: Analog Input Cannot Display This Video Mode" and that's where it stops. 

I tried hooking up an old CRT monitor and Ubuntu detected the lower res graphics and adjusted just fine.  

My xorg.conf file after the upgrade was almost empty with just:
 
-"Device" section had "Configured Video Device" with Option "UseFBDev" set to "true" 
-"Monitor" section had "Configured Monitor"
-"Screen" section had "Default Screen", "Configured Monitor" and "Configured Video Device"

I also tried replacing that with the xorg.conf that worked under Hardy...no luck.

Is there a thread I'm not finding that explains all this, or can someone help?  Thanks.

---

### Post by tommcd on 2009-03-14
Try booting the Ubuntu 8.10 live CD and choose the option "**xfix** Fix Video" (or whatever it says). Also, see this page from the wiki:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
If the CRT works but the LCD doesn't then it must not be auto detecting the LCD properly. Hopefully xfix or xrandr can fix it.
A clean install of 8.10 may fix it also if you are up for that.

And welcome to the Ubuntu forums!

---

### Post by sbradley07 on 2009-03-14
xfix (I found that by booting to the recovery mode menu) didn't do anything.

I tried using xrandr and it always resulted in a "Can't open display" message.  I have Intrepid running fine on a couple of Thinkpads, and on those machines, I always get screen resolution information when I type xrandr.  On this Dell machine though, I get the "can't open display" no matter what parms I give to xrandr.  Also, there doesn't seem to be a monitors.xml file in the .config directory....could that be the problem?

This is baffling me because it all worked in Hardy.

---

### Post by tommcd on 2009-03-15
Did you do a dist-upgrade to Intrepid? Or a clean install of Intrepid? If you did a dist-upgrade, then I would try a clean install if you can't find a better solution.

What video card do you have? Make sure the proper driver is being loaded for it.
Also, try googleing your monitor model number +ubuntu to see if there are any reports about your particular monitor and Ubuntu 8.10.

---

### Post by sbradley07 on 2009-03-15
I did a dist-upgrade.  By clean install, do you mean reformat the entire drive and lay down 8.10 brand new?  If so, that's a possibility, but would need to write off a bunch of data. 

The video card is an AGP 2.0...the machine is a pretty old Dell Dimension 4100.

I also googled the monitor and ubuntu, but found nothing concrete to solve this problem.  I did find a reference (in Ubuntu doc I think) about 8.10 dropping support for the ati driver and to disable it before upgrading to 8.10.  I did not do this, so maybe that's part of my problem?

---

### Post by tommcd on 2009-03-15
> **sbradley07 said:**
> I did a dist-upgrade.  By clean install, do you mean reformat the entire drive and lay down 8.10 brand new?  If so, that's a possibility, but would need to write off a bunch of data. 
Yes, that is what I mean. If you have your home directory on a separate partition your data will be safe. Just choose manual partitioning, select your root partition for the install, and select the mount point for your home partition as /home and do not format it. If you don't have home on a separate partition, now would be a good time to repartition and make one. Back up your data first.
> **sbradley07 said:**
> 
I also googled the monitor and ubuntu, but found nothing concrete to solve this problem.  I did find a reference (in Ubuntu doc I think) about 8.10 dropping support for the ati driver and to disable it before upgrading to 8.10.  I did not do this, so maybe that's part of my problem?
I suppose that could be. Do a search for your video card and driver here on the forums. Perhaps a driver upgrade or reinstall will fix it. Post your xorg.conf here.
I have no experience with ati drivers. I have always used nvidia. So I may not be of much help with ati issues.

---

