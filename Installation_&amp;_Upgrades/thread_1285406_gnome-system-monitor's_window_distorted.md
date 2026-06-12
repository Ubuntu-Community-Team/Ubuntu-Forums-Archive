---
title: "gnome-system-monitor's window distorted"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by foureyesboy on 2009-10-07
I have done an upgrade to 9.10 beta from 9.04 recently on a Thinkpad X22.  Every thing seems all right except for gnome-system-monitor.  I notice that it was upgraded to version 2.28 but now every time I invoke it, the window shown looks like this:
[IMG]http://img15.imageshack.us/img15/6240/screenshotsystemmonitor.png[/IMG]

I've tried a complete remove of the gnome-system-monitor and reinstalled it again, but the problem persists.  I've also forced a fsck and everything seems fine.  I don't think that this is a bug as it seems that this problem only happens to it, other applications work fine so far.

I believe that a fresh re-installation of the entire system may solve the problem, but I want to keep this as the last resource.  Have anyone come across a similar problem like this?  Or would anyone please kindly give me a hand on this?

Thanks a lot.

---

### Post by mac9416 on 2009-10-07
Same thing here. I reported a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/440608](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/440608)

The same thing happens with both Gnome-Do and notify-osd.

---

### Post by foureyesboy on 2009-10-07
Thanks for letting me know.  I've searched launchpad for "corrupted display", "distorted display"; just haven't thought of "display static".  Haha.  Thanks.

---

### Post by mac9416 on 2009-10-08
Another related bug: [https://bugs.edge.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/208570](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/208570)

Apparently a graphics driver issue?

---

### Post by foureyesboy on 2009-10-11
> **mac9416 said:**
> Another related bug: 

Apparently a graphics driver issue?

I'm still in doubt if it's a graphics driver issue as it seems to affect only a couple of particular apps.  Or is it a rare feature that only these apps out of the many others use?

---

### Post by tedrogers on 2009-10-30
Same here on a T42.

Just done the update tonight, and a couple of weird things are happening (as expected) but this is the weirdest.

Lucky it still senses top-right X for close!! :)

Hope there is a fix soon.

---

### Post by Risasi on 2009-10-31
Same here, also on an X-22. I also notice the garbage in the awn-manager.

---

### Post by steveneddy on 2009-10-31
Try downgrading one version on the video driver.

What video drivers are everyone using that seems to be causing this issue?

---

### Post by tedrogers on 2009-11-01
I don't know if this is related...looks like it is. My OSD at bootup looks like this. Afterwards it doesn't show up at all.

[IMG]http://i77.photobucket.com/albums/j58/fiddybux/osdcorruption.jpg[/IMG]

I've looked at my drivers and I'm not using any OEM proprietary drivers.

How can I find out what driver I'm using and how can I downgrade one version?

---

### Post by mac9416 on 2009-11-01
I found out that I'm using Radeon drivers by running "lsmod | grep 'radeon'". It gives me several results.

The problem seems to occur only on Thinkpads. I have a T30.

steveneddy, how does one downgrade the driver? Thanks.

---

### Post by tedrogers on 2009-11-02
I'm also using a Radeon...which works fine in glxgears and glxinfo reports all is okay too.

Can't imagine why it is causing this problem?

Anyone?

---

### Post by tedrogers on 2009-11-03
I installed Karmic on my iMac at work, and it works fine. Interestingly this also uses a Radeon gfx card, but there are no issues with corruption that are being discussed.

---

### Post by fuquaforlife on 2009-11-03
Same problem on a Thinkpad T40!

---

### Post by tedrogers on 2009-11-03
I don't think I've ever had an Ubuntu install that doesn't have a problem on Thinkpad's.

And yet, Fedora has always worked fine, in almost every way. I prefer Ubuntu though.

What is it? Solution, not fix please!?

---

### Post by wyclif on 2009-11-04
Same exact problem here. GNOME-Do, System Monitor, &c.

---

### Post by tedrogers on 2009-11-04
> **wyclif said:**
> Same exact problem here. GNOME-Do, System Monitor, &c.

What computer are you using wyclif? T -series?

---

### Post by fuquaforlife on 2009-11-04
> **fuquaforlife said:**
> Same problem on a Thinkpad T40!

Oh, and if it helps, it seemed like it was fine when I did a fresh install, but went bad when I did an update.  I really don't know enough about Linux though to be able to figure out what happened though.

---

### Post by tedrogers on 2009-11-04
Just reading the bug reports about this issue, and if you turn on compiz, i.e. set the SYSTEM > PREFERENCES > APPEARANCE > VISUAL EFFECTS to the option NORMAL (therefore enabling some of the basic visual effects) then the problems go away...at least they do for me.

This is not ideal because it slows my machine down, but it works in the interim.

---

### Post by mac9416 on 2009-11-04
How would one enable that kind of configuration in, say, Fluxbox? I have tried enabling compositing in metacity without results. I have also installed Compiz and run 'compiz --replace', but I get errors. Then I tried Emerald. When I run 'emerald --replace', the whole desktop turns to static.

So, I'm still pulling my hair out over this. Fortunately, none of these apps are critical, so I can keep pluggin' along without them until we find a fix (one that works in Fluxbox anyway). :)

---

### Post by childresspta on 2009-11-04
This is not just a thinkpad issue, I am using a compaq desktop and am having the same problem.

---

### Post by tedrogers on 2009-11-05
> **mac9416 said:**
> How would one enable that kind of configuration in, say, Fluxbox? I have tried enabling compositing in metacity without results. I have also installed Compiz and run 'compiz --replace', but I get errors. Then I tried Emerald. When I run 'emerald --replace', the whole desktop turns to static.

So, I'm still pulling my hair out over this. Fortunately, none of these apps are critical, so I can keep pluggin' along without them until we find a fix (one that works in Fluxbox anyway). :)

[http://ubuntuforums.org/showthread.php?t=678487](http://ubuntuforums.org/showthread.php?t=678487)

A little off topic, but this would seem to suggest its problematic.

So it is an issue on Compaq's...good to know it's not limited to IBM's. It might lend more weight to the issue now that other machines are affected too.

---

### Post by mac9416 on 2009-11-05
Thanks, tedrogers! Maybe that will fix it. I'll go through it as soon as possible.
Something I found out: my Thinkpad has a Radeon Mobility 7500. If you want to find out what yours is, install and run "sysinfo", go to "Hardware" and set the dropdown on the right to "Graphic card".

---

### Post by speedy44 on 2009-11-05
> **mac9416 said:**
> Thanks, tedrogers! Maybe that will fix it. I'll go through it as soon as possible.
Something I found out: my Thinkpad has a Radeon Mobility 7500. If you want to find out what yours is, install and run "sysinfo", go to "Hardware" and set the dropdown on the right to "Graphic card".
Hi,
I have a DELL Latitude c640 with a  Radeon Mobility 7500 and I see the same issues as you.
It looks like it is related to the graphic card - driver relationship and independent of the notebook model.
Regards

---

### Post by fuquaforlife on 2009-11-05
> **tedrogers said:**
> Just reading the bug reports about this issue, and if you turn on compiz, i.e. set the SYSTEM > PREFERENCES > APPEARANCE > VISUAL EFFECTS to the option NORMAL (therefore enabling some of the basic visual effects) then the problems go away...at least they do for me.

This is not ideal because it slows my machine down, but it works in the interim.

This solves the problem on the T40.

---

### Post by mac9416 on 2009-11-05
> **tedrogers said:**
> [http://ubuntuforums.org/showthread.php?t=678487](http://ubuntuforums.org/showthread.php?t=678487)

A little off topic, but this would seem to suggest its problematic.

I tried the process outlined on the Fluxbox wiki ([http://fluxbox-wiki.org/index.php?title=Transparency](http://fluxbox-wiki.org/index.php?title=Transparency)), but when running 'xcompmgr -c &' to enable transparency the whole desktop turns to gobblety-gook.

Also, I have been told that Gnome-Do works with Compiz on most machines. Apparently just not on Radeon Mobility 7500s.

---

### Post by tedrogers on 2009-11-05
> **mac9416 said:**
> I tried the process outlined on the Fluxbox wiki ([http://fluxbox-wiki.org/index.php?title=Transparency](http://fluxbox-wiki.org/index.php?title=Transparency)), but when running 'xcompmgr -c &' to enable transparency the whole desktop turns to gobblety-gook.

Also, I have been told that Gnome-Do works with Compiz on most machines. Apparently just not on Radeon Mobility 7500s.

No idea. Maybe if you post on the other thread someone can assist.

---

### Post by mac9416 on 2009-11-05
> **tedrogers said:**
> No idea. Maybe if you post on the other thread someone can assist.

It is very likely they would not be able to help. This is a driver problem limited to Radeon Mobility 7500s, and more pertinent to this thread than the other.

Since neither Compiz nor xcompmgr have helped, my only hope is downgrading the driver. I have posted another thread asking how here: [http://ubuntuforums.org/showthread.php?t=1315815](http://ubuntuforums.org/showthread.php?t=1315815)

Please tolerate my problems, though they are slightly different from others' in this thread. My problem is very similar.

---

### Post by jlh on 2009-11-06
I have the same problem on a Thinkpad T30, after doing an upgrade from 9.04.

The System>Preferences>Appearance>Visual Effects fix doesn't work for me. If I try to switch from None to Normal, my graphics card won't support the change.

---

### Post by foureyesboy on 2009-11-09
As it turns out, I found that specifying the use of the vesa driver in Xorg works around the problem.  All the gnome-system-monitor, notify-osd and even cairo-dock come back.  But of cuz there will be no hardware acceleration if using the vesa driver.

Here is my /etc/X11/xorg.conf:
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

So, perhaps it's the xserver-xorg-video-ati that comes with Xorg 6.4 in 9.10 that causes the problem?

Hope this helps a bit.

---

### Post by mac9416 on 2009-11-09
Thanks, foureyesboy, that worked perfectly! All three apps are back to normal. 
So, what are the disadvantages of going to the "vesa" driver. You menioned losing hardware acceleration, but what does that mean? Am I losing some kind of performance, such as gaming?

---

### Post by foureyesboy on 2009-11-09
Unfortunately yes, using the vesa driver will lose some graphical performance.

If you do a "glxinfo | grep renderer", it will show it changes to "OpenGL renderer string: Software Rasterizer" when using vesa.

---

### Post by tedrogers on 2009-11-09
Try running glxgears in the terminal now you have the VESA driver running, and compare it with the previous driver.

You should notice that frame rates are much slower.

In a nutshell and very simple explanation, this is what hardware acceleration does. It uses special chips on the graphics card to do "the hard work" of making graphics happen on screen, as opposed to VESA which does it though software and makes your computers CPU do all "the hard work".

Hardware acceleration is more fancy and thus better :) for me...windows appear faster, close faster, can fade etc. and you can play games.

In VESA I wouldn't try and play games, and I doubt most of the graphics heavy ones will even start because they will detect "no hardware acceleration".

P.S. Thanks for the temporary fix foureyesboy, but in this case why would enabling the compiz features for me solve my problems...I'm even more accelerated that usual!

---

### Post by foureyesboy on 2009-11-10
> **tedrogers said:**
> 

P.S. Thanks for the temporary fix foureyesboy, but in this case why would enabling the compiz features for me solve my problems...I'm even more accelerated that usual!

Sorry that I've forgotten to update about compiz.  

Mine is an X22 which is quite shabby and only equipped with Radeon Mobility M6.  So in the past I could not turn on Visual Effects at all.  Every time I tried to turn it on, it said "Desktop effects cannot be enabled".  I thought my display was too old for compiz.

Your kind reminder motivates me to try again.  I found that the compiz can be turned on _if_ I reduce the color depth to 16 bits.  But it is not without flaw.  Some colored lines may intermittently appear across the screen randomly.  Even with this flaw, I can see that compiz does solve the problem and let gnome-system-monitor & notify-osd come back.

So I think it's because my display does not have enough memory to let compiz run.  Unfortunately those lines are sometimes quite numerous (just like what mac9416 has described) and I can't find any mean to increase the video RAM from system memory in the BIOS. 

So your compiz solution works much better.  But too bad that I have to stick to the vesa workaround.

Thanks anyway, Ted.  ^^

---

### Post by mitoe on 2009-11-11
I am currently having the same issue with my Toshiba Satellite 1905-S301, equipped with a Mobility M6 LY.  I have never been able to get compiz working on this machine, despite trying every HOWTO and configuration option. Now, after the update to 9.10, I am having same issues pictured above, as well as similar issues with notification pop-ups from network-manager and rythmbox.  

This may be unrelated to this thread, but if I run gnome-appearance-properties from a terminal, here is the list of errors I get when I try to enable visual effects:

> (gnome-appearance-properties:2911): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 

(gnome-appearance-properties:2911): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2911): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: 
(gnome-appearance-properties:2911): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 

(gnome-appearance-properties:2911): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: 
(gnome-appearance-properties:2911): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 456: /usr/local/bin/compiz: not found

(gnome-appearance-properties:2911): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

The last line repeats about 50 times.

I'm especially confused by "/usr/local/bin/compiz: not found" part.  /usr/bin/compiz is complaining that it can't find /usr/local/bin/compiz?  If I make a symlink from /usr/bin to /usr/local/bin, it just loops and crashes when I try to start compiz.  

Bleh.  

If anyone could help me with this, you'd be my hero.  Thanks in advance!

---

### Post by foureyesboy on 2009-11-11
when you do > grep 'WW\|EE' /var/log/Xorg.0.log does it show anything like > 
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 12288 kB of video memory needed at this resolution and depth.
(WW) RADEON(0): Direct rendering disabled


This is what I get on my X22 which is also equipped with Radeon Mobility M6.

The display utilizes system memory for video RAM, and I found that it allocates only 8MB.  So I guess there's not enough video RAM for features that needed by compiz.

I've looked into the BIOS of my Thinkpad but there's no entry to change the size of video RAM allocation.  I'm not sure about Toshiba.  Maybe you can take a look.

The only workaround that I can find for the time being, is to use vesa driver instead as in an earlier post (#29) of this thread.  At least you can get back gnome-system-monitor & notify-osd.

---

### Post by mitoe on 2009-11-11
Thanks for the quick reply!

I am not seeing those specific errors, but I am seeing this:
> 
(WW) RADEON(0): LVDS Info:
(WW) RADEON(0): LCD DDC Info Table found!
(WW) RADEON(0): WARNING: Using the AGPFastWrite option is not recommended.
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xf3fff000 is: 0xf3fff000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xedffec00

As far as using the vesa driver, the slow-down isn't worth it.  I don't use or need system-monitor, so it's not a show-stopping bug, but it would be beautiful if I could get it fixed.  Also, I would love to get compiz working if at all possible.  

Thanks again!

---

### Post by foureyesboy on 2009-11-11
> **mitoe said:**
> Thanks for the quick reply!

I am not seeing those specific errors, but I am seeing this:


As far as using the vesa driver, the slow-down isn't worth it.  I don't use or need system-monitor, so it's not a show-stopping bug, but it would be beautiful if I could get it fixed.  Also, I would love to get compiz working if at all possible.  

Thanks again!


Could you capture the output of:
```
glxinfo | grep 'vendor\|render'
```

---

### Post by tedrogers on 2009-11-12
I have compiz enabled, and the output from ```
glxinfo | grep 'vendor\|render'
``` is as follows:

[COLOR="Blue"][B]direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R100 (RV200 4C57) 20090101 AGP 4x x86/MMX/SSE2 TCL[/B][/COLOR]

I have also tried disabling my compiz, and then adding both 16, 24 and 32 bit depths [DefaultDepth] in xorg.conf. But none of them make a difference, and 32 bit depth just crashes out X windows on a pretty monumental scale! :)

Don't know if any of this helps at all...maybe it will as mine works with compiz and yours doesn't.

---

### Post by foureyesboy on 2009-11-13
Yes, mitoe, as tedgogers suggests, maybe try 16-bit color depth.

---

### Post by tedrogers on 2009-11-16
> **foureyesboy said:**
> Yes, mitoe, as tedgogers suggests, maybe try 16-bit color depth.

Just to add to this....going to 16 bit made no difference for me, nor did 24 bit...and 32 bit crashed X windows.

Where to from this? No idea.

Karmic does some other unusual stuff I've noticed too, like the Bluetooth icon going black or not showing at all sometimes for no reason I can see. I guess Karmic is just more bleeding edge than the last release.

---

### Post by Toehead on 2009-11-16
Same problem on my compaq AMD 64 3400 with radeon card.

---

### Post by morsel on 2009-11-16
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/429295](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/429295)
worked on a thinkpad x31:

xorg.conf -> Device Section:
Option "RenderAccel" "false"

fixed the osd, system monitor and gnome-do issues but not the glitches with visual effects enabled though :/

---

### Post by tedrogers on 2009-11-16
Good man! I want to buy you a beer. :)

Worked like a charm on a T42.

Love this community! ;)

These other glitches with visual effects enabled that you mention, are you experiencing the same odd stuff as I do, i.e. bluetooth icon going black, purple lines under taskbar when coming out of hibernate etc?

---

### Post by Veloteuton63 on 2009-11-19
> **tedrogers said:**
> Good man! I want to buy you a beer. :)

Worked like a charm on a T42.

Love this community! ;)

These other glitches with visual effects enabled that you mention, are you experiencing the same odd stuff as I do, i.e. bluetooth icon going black, purple lines under taskbar when coming out of hibernate etc?

I join in for the beer - it saved my day ...
I encountered this problem on an X32 after upgrading to 9.10.

On an other machine (ASUS sthgorother) the upgrade failed and the machine never reached the end of the boot phase (or X11 startup - I don't know). 
However even after a 'clean' install I encounter the same problem.

---

### Post by dargaardms on 2009-11-19
Sounds great but there is no xorg.conf or am I missing somthing?

> **morsel said:**
> [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/429295](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/429295)
worked on a thinkpad x31:

xorg.conf -> Device Section:
Option "RenderAccel" "false"

fixed the osd, system monitor and gnome-do issues but not the glitches with visual effects enabled though :/

---

### Post by zainka on 2009-11-19
> **dargaardms said:**
> Sounds great but there is no xorg.conf or am I missing somthing?

...Only xorg.conf but this can be created. I had to do this myself and was required to add the section as follow (this is actually my entire xorg.conf file) youst be aware that these setting was those working for me, your system MIGHT need other settings (unsure? try it, worst case is that ubuntu will start up in terminal mode after reboot. Then just remove the xorg.conf created).

```
# To avoid unreadable windows.
Section "Device"
	Identifier	"Radeon7500"
	Driver	"ati"
	BusID	"PCI:1:0:0"
	Option	"RenderAccel" "false"
EndSection
``` 
Now, save and reboot and prepare to put a big green on your face...

Reason for why you could not find the file is this that xorg.conf is by default not needed as X may run perfectly without, but if default settings is to be tweaked this is where to do it, as far as I understand.

However, what scares me is that this feature which was working in 9.04 now is not working in 9.10. Only possible explanation to this is that the default value in 9.04 for render accelerator has been changed from FALSE to TRUE so that in 9.10 the accelerator is on by default. 

Also I do not understan WHY the rendering accelerator is not working, this has to be a defect or missing feature in xorg driver, afaik.

However, for the moment thing works and I am happy, its just a bad feeling to know there are unused resources available... 

time for another :popcorn:

---

### Post by foureyesboy on 2009-11-22
Well, for someone likes me who can't turn on compiz via System>Preferences>Appearance>Visual Effects.  There is yet another workaround that may work by enabling the compositing feature of Metacity.

Just install ubuntu-tweak from Package Manager.  Inside Ubuntu Tweak, find Desktop > Windows and check Enable Metacity's Compositing feature under Compositing Manager.

On my X22, Visual Effects can't be turned on, but enabling the Metacity's Compositing feature also solve the display problem.

---

### Post by tedrogers on 2009-11-27
Thanks for sharing that...that is good to know for those in your situation.

---

### Post by efflandt on 2009-11-27
I noticed the crosshatching when I was trying various distros to see what worked on an old PIII 550 w/320 MB RAM and lower end Radeon AGP card (I think w/32 MB RAM).  Actually with Xubuntu 9.10 I could not even get into X once I did the first set of updates unless I installed xorg-driver-fglrx before doing any updates.  But even with that the crosshatch continued for System Monitor and OSD for wireless or networking up.

I don't remember if the crosshatch was in Ubuntu 9.10.  But that would not even initially go into X unless I logged into Failsafe GNOME.  And from there I was able to install xorg-driver-fglrx.

Jaunty ran fine with its default modules.  I ended up installing Qimo 4 kids (based on Ubuntu 8.10) for my niece's twin 4 year old boys, and that works fine.

The Radeon card on my desktop (Athlon64 3200+ 2 GHz 1024K cache) had no problems with default modules and no xorg.conf in fresh 64-bit 9.10 install.  64-bit flashplugin sometimes crashed FireFox (fixed with lahf plugin), and screensavers sometimes crashed (maybe for same missing lahf on my cpu), so I just use blank screen:

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
    Subsystem: VISIONTEK Device 1910
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at ff4f0000 (64-bit, non-prefetchable) [size=64K]
    Region 4: I/O ports at c000 [size=256]
    Expansion ROM at ff4c0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] AGP version 3.0
        Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
        Command: RQ=32 ArqSz=2 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Kernel modules: radeon
```

---

### Post by nxDan on 2009-11-27
Hi,
had the same problem here with Karmic on an IBM T42 after upgrading from Jaunty and installing something which broke the notify-osd and gnome-do.
I was unable to install activate compiz (normal visual effects), but when I connected to my pc with freenx it worked.
So I created a second user and it worked fine. 
So something is wrong in one of the settings in the /home folder. I googled a bit, but behalve this thread I couldn't find anything.

As I tweaked more arround I "fixed" the things that finally I decided to reinstall it (it's easy for me, as my home is on its own partition).
After reinstalling Karmic it was still not working (as I'm still using the same home folder), but was able now to activate the "normal" visuals and gnome-do and notify are finally working again.

Maybe this can help to find a hint to fix this.

---

### Post by rcastles on 2009-12-28
I've got the same problem on my desktop.

I have a Raedon card that worked fine with Jaunty.  Adding "vesa" to xorg.conf did allow the system monitor to work but at the cost of not being able to set the resolution of my display to any 16:9 OR 16:10 aspect ratio or anything else using the display settings tool from the panel.

---

### Post by mac9416 on 2009-12-28
rcastels,

Setting the driver to "vesa" worked for me too, but at the expense of some performance. Have you tried zainka's xorg.conf modification described in [post #46]("http://ubuntuforums.org/showpost.php?p=8349820&postcount=46")? It worked like a charm for me; maybe it will solve your aspect ratio settings problems.

---

### Post by rcastles on 2009-12-30
I just tried it and it does seem to work. Thanks to both of you.

---

### Post by tedrogers on 2009-12-30
> **rcastles said:**
> I just tried it and it does seem to work. Thanks to both of you.

I can also confirm that the xorg.conf modification described in post #46 worked for me brilliantly.

---

### Post by zeroandone on 2010-01-05
I have the same problem with my Dell Latitude C610. Very frustrating! I finally installed KDE System Monitor (ksysguard), and it works very well. 

When can this annoying problem be fixed? As far as I know, the problem still exists in Lucid Lynx Alpha 1.

---

### Post by tedrogers on 2010-01-06
Didn't the xorg.conf modification work for you?

---

### Post by zeroandone on 2010-01-06
> **tedrogers said:**
> Didn't the xorg.conf modification work for you?
I didn't try. I am fine with KDE System Monitor, so I am patiently waiting for the fix if there will be any in the future.

---

### Post by tedrogers on 2010-01-06
> **zeroandone said:**
> I didn't try. I am fine with KDE System Monitor, so I am patiently waiting for the fix if there will be any in the future.

Right o! :)

---

### Post by butters stotch on 2010-01-09
Adding the xorg.conf solves my problem!!
Mine is Thinkpad T40, with Radeon 7500.
Thanks!

After I installed 9.10, I had the same problems with Gnome-do, system-monitor, and notify-osd. I had to open compiz.
Then I lost direct rendering. (compiz disabled that, don't know how and why)
Now, I can have both.

---

### Post by tedrogers on 2010-01-09
> **butters stotch said:**
> Adding the xorg.conf solves my problem!!
Mine is Thinkpad T40, with Radeon 7500.
Thanks!

After I installed 9.10, I had the same problems with Gnome-do, system-monitor, and notify-osd. I had to open compiz.
Then I lost direct rendering. (compiz disabled that, don't know how and why)
Now, I can have both.

Good to hear...well done for finding this thread dude!

---

### Post by fredthomke on 2010-02-25
I, too, have a Dell Latitude C610 laptop.  Just installed Xubuntu 9.10, with the resulting crosshatched windows (the System Monitor window, for example) as well as the blacked-out Notification pop-ups for NetworkManager and such.  I can absolutely confirm the solution is to create the /etc/X11/xorg.conf file from scratch as mentioned in message #46.  Reboot, and the problem is solved!

- - fred

---

### Post by ExPatTyke on 2010-04-19
Many thanks zainka (post #46) - the display on my Dell C510 hasn't worked properly since I made the mistake of upgrading to 9.10.  It appears to be working fine now, thanks to your advice, without the hatching that I saw in common with several other posters. 

The other main problem I had was the menu bar and items in the menus on amsn being "blurred out" - anyone else have this?  Resolved now anyroad.

The annoying thing about the upgrade is that I left it for sometime after the 9.10 release for things to stabilise - I need this laptop for work and run it with Ubuntu for its "works out the box" rather than my usual Debian Testing.

---

