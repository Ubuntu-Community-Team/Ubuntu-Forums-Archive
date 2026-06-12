---
title: "ubuntu on Dell Inspiron 11&quot; 3000 2-in-1"
date: 2014-09-15
forum: Hardware
---

### Post by tango_ninja on 2014-09-15
Hi folks,
Has anyone completed a successful install on the Dell Inspiron 11" 3000 2-in-1?   (a la [http://www.dell.com/us/p/inspiron-11-3147-laptop/pd?oc=fncwr1204b&model_id=inspiron-11-3147-laptop](http://www.dell.com/us/p/inspiron-11-3147-laptop/pd?oc=fncwr1204b&model_id=inspiron-11-3147-laptop))

I'm looking for a portable, convertible laptop that I can flip 360 degrees for reading + touch.  This seems like it fits the bill but I'm not sure about the drives and compatibility, specifically for  touchscreen,  mousepad, and wifi.

Thanks!
-tn

---

### Post by José Serra on 2014-10-15
Hi, I'm looking for the same thing, have you found some thing about it?
it was supposedly announced moths ago: [http://www.pcworld.com/article/2357621/dell-brings-ubuntu-to-tablets-with-new-inspiron-hybrids.html](http://www.pcworld.com/article/2357621/dell-brings-ubuntu-to-tablets-with-new-inspiron-hybrids.html)

---

### Post by tango_ninja on 2014-11-08
Still haven't gotten any feedback on this one, although I'm sure it would work fine.  I just don't know about the touch drivers for the screen and was hoping someone who had already done it could share their experience.  Both the 11" and 13" version are still available on the Dell website.

---

### Post by José Serra on 2014-11-13
Hi, It has been reported to work out of the box with Ubuntu 14.10 here:

[http://liliputing.com/2014/10/dell-inspiron-11-3000-series-budget-2-1-convertible-review.html](http://liliputing.com/2014/10/dell-inspiron-11-3000-series-budget-2-1-convertible-review.html)

---

### Post by joe149 on 2014-12-07
No, Ubuntu does not work out of the box with this Dell machine.

The touchpad does not shut off when the screen is folded back, which makes using it as a tablet annoying at best. Also, the screen does not rotate when you want to use the tablet in portrait mode.

Guess that is why it doesn't work-

Not a very common option for Ubuntu. (Despite ubuntu being a "Factory" option. ;) )

---

### Post by schok2 on 2014-12-07
can anyone else confirm this? would love to try ubuntu on this machine as well. not that i have any problem with windows 8.1, just miss the feeling of using ubuntu :)

---

### Post by Tristan_Havelick on 2014-12-24
I can confirm that Ubuntu 14.10 works with this laptop. I've had the following issues:

When running off of LiveUSB the wifi doesn't work, however after installing to the harddrive, it worked out of the box.

The accelerometer doesn't work. This means that automatic screen rotation doesn't work, nor do games like Neverball use it, This also  means that the keyboard and trackpad still register inputs.

The Ubuntu UI isn't really obtimized for touch at all. I can "click" things with my finger, but I can't pinch to zoom, swipe to scroll or anything like that. This makes the touch screen of questionable utility within Ubuntu.

With that in mind, I installed Android x86 alongside Ubuntu. I can boot to ubuntu when doing desktop tasks, and boot android when I want to do some dedicated surfing.  Android still has the accelometer issue, but the touch support is very nice

---

### Post by Su_Heng on 2015-02-02
> **Tristan_Havelick said:**
> I can confirm that Ubuntu 14.10 works with this laptop. I've had the following issues:

When running off of LiveUSB the wifi doesn't work, however after installing to the harddrive, it worked out of the box.

The accelerometer doesn't work. This means that automatic screen rotation doesn't work, nor do games like Neverball use it, This also  means that the keyboard and trackpad still register inputs.

The Ubuntu UI isn't really obtimized for touch at all. I can "click" things with my finger, but I can't pinch to zoom, swipe to scroll or anything like that. This makes the touch screen of questionable utility within Ubuntu.

With that in mind, I installed Android x86 alongside Ubuntu. I can boot to ubuntu when doing desktop tasks, and boot android when I want to do some dedicated surfing.  Android still has the accelometer issue, but the touch support is very nice


Do you know how to make accelerometer  works. As it's so stupid to make the keyboard & touchpad register inputs with hinged tablet mode.(actually, my keyboard is not register to input. However, touchpad do register input).  Is there any approach to fix this ?

---

### Post by opensas on 2015-03-01
I can confirm the issues you reported, at least the livecd part of it. It won't work on live mode (although, strange enough I tested it on Elementary Freya beta and it works on live mode)

Has anybody reported this issue with dell? 

On the other hand, is there some workaround for the screen rotation stuff? I mean, at leas a script to manually rotate the screen and disable the touchpad

BTW, I asked this on askubuntu: [http://askubuntu.com/questions/591552/configure-wifi-on-dell-inspiron-11-3000/591584#591584](http://askubuntu.com/questions/591552/configure-wifi-on-dell-inspiron-11-3000/591584#591584)

---

### Post by billy30 on 2015-03-12
i just installed Linux Mint (which is based on Ubuntu) successfully. LiveCD and touchscreen worked fine.

The huge problem i am having, regarding the touchscreen now that it is installed (i never fully tested it in livecd) Touchscreen will work, but in doing so, touchpad stops until a restart. There is also no virtual keyboard, but the regular keyboard will still work with touchscreen. So if you plan on using touchscreen to do things, be advised that you will not have the touchpad until you restart linux. So it is a constant switch between touch and typing. it is annoying. i hope a fix will be found soon...

i can also report no screen rotation.


other than this, no problems so far....

UPDATE: Problem seems to have fixed itself. i did and update and upgrade in terminal. i also installed some 'firmware-addon-dell' in package manager. BUT NOW the topuchpad stops working after a suspension. i know thi sis a common problem though and i am currently researching the fix

Things are still going relatively smoothly. i still cannot find a fix for my touchpad not working after being woken up from suspension/opening my lid. i tried the following solutions:

[http://ubuntuforums.org/showthread.php?t=2250002](http://ubuntuforums.org/showthread.php?t=2250002)

and

[http://ubuntuforums.org/showthread.php?t=2182922](http://ubuntuforums.org/showthread.php?t=2182922)

Oddly, neither worked.

i remember seeing somewhere a method to replace suspension with hibernation when you close your lid. perhaps that will provide a temporary fix.

i bought a bluetooth mouse hoping thatthis will at least be able to keep me from having to restart my laptop every time i open it, but nope. Bluetooth also stops after suspension. im thinking about making a linux mint post soon.

Edit: The bluetooth adapter actually cannot be found at all.

---

### Post by Hulk_Joshua on 2015-03-13
personally i am using Ubuntu 14.10 on a Dell Inspiron 11" 3000 2-in-1 so give it a go it definitely woks

---

### Post by joe149 on 2015-03-13
The touch pad does not turn off while typing, despite there being a checkbox in settings that claims to do so.

"Out of the box" was mentioned above. Is this a joke?

> **Hulk_Joshua said:**
> personally i am using Ubuntu 14.10 on a Dell Inspiron 11" 3000 2-in-1 so give it a go it definitely woks

Are you not getting the problems listed above in this thread?

Are you just ignoring them and giving bad advice?

Mine will not come back from suspend at all. If I close the lid, it essentially shuts it all down. I have to press and hold the power button to fully shut down; then re-press it to turn the computer back on.

---

### Post by kcallis on 2015-04-20
I have been trying to do an install with Mint 17 live boot. My problem is that when I get ready to do partitioning, Mint does not see the Windows partitions and only want to completely blow away the partition and give me a clean system. Also, what is the proper way to backup the Windows stuff, that that when I get everything back in place that I can restore the Win 8.1 crap (albeit with a very small partition) and everything will come back pristine.

---

### Post by snatchell on 2015-04-21
I'm running 14.04.2 with kernel 4.0 and BIOS updated to A05, and have no hickups with the touchscreen or touchpad and this device is now my daily driver. but disabling touchpad while flipped and rotation would still be nice. Or even the Dell OEM image used in the european models.

As of BIOS A03, blacklisting dw_dmac and dw_dmac_core are not required to get suspend/shutdown functions. You can update the bios using the Windows 8 stock install or by making a FreeDOS bootdisk.

@Tristan_Havelick If you want an android rom with rotation, i suggest looking into Exton's Andex ROM. The latest kitkat build has kernel 3.19 with Rotation and BayTrail support.

@kcallis are you booting the LiveCD With legacy boot?

---

### Post by kcallis on 2015-04-21
> **snatchell said:**
> I'm running 14.04.2 with kernel 4.0 and BIOS updated to A05, and have no hickups with the touchscreen or touchpad and this device is now my daily driver. but disabling touchpad while flipped and rotation would still be nice. Or even the Dell OEM image used in the european models.

As of BIOS A03, blacklisting dw_dmac and dw_dmac_core are not required to get suspend/shutdown functions. You can update the bios using the Windows 8 stock install or by making a FreeDOS bootdisk.

@Tristan_Havelick If you want an android rom with rotation, i suggest looking into Exton's Andex ROM. The latest kitkat build has kernel 3.19 with Rotation and BayTrail support.

@kcallis are you booting the LiveCD With legacy boot?

I am at A05 BIOS. I have tried both legacy and UEFI, but each time it shows unknown partitions (which of course are actually the Windows partions), so I tend to back off. I am booting with a thumb drive Mint 17.1 Live-CD, and again, it boots fine, but still the issues with the partitions.

---

### Post by Vladlenin5000 on 2015-04-21
> **kcallis said:**
> I am at A05 BIOS. I have tried both legacy and UEFI, but each time it shows unknown partitions (which of course are actually the Windows partions), so I tend to back off.

... and you should back off. First of all boot in Windows and disable fastboot. Otherwise Windows will hibernate instead a properly shutting down. That's the common cause for what you're seeing with the partitions. However, there are other possible causes, depending on how the Windows partitions where formated in the first place. Also, with UEFI and Windows 8.1 you must (almost always) use Something else and do a manual partitioning for Ubuntu in the unallocated space.

---

### Post by billy30 on 2015-04-21
> **kcallis said:**
> I have been trying to do an install with Mint 17 live boot. My problem is that when I get ready to do partitioning, Mint does not see the Windows partitions and only want to completely blow away the partition and give me a clean system. Also, what is the proper way to backup the Windows stuff, that that when I get everything back in place that I can restore the Win 8.1 crap (albeit with a very small partition) and everything will come back pristine.


i ran into this same problem. What you have to do is partition manually using gparted or windows disk management. 

i used a couple different tutorials, including this one: [http://linux.about.com/od/howtos/ss/How-To-Dual-Boot-Windows-81-And-Linux-Mint.htm](http://linux.about.com/od/howtos/ss/How-To-Dual-Boot-Windows-81-And-Linux-Mint.htm)

i recommend that you follow them carefully and cover all of your bases. i also strongly urge to find a second tutorial. i tried to look for the other tutorial i used. It was an in-depth guide someone posted in the mint forums (could have been ubuntu forums).

It may seem intimidating, but it really isn't. Just follow instructions carefully and make sure you partition your boot swap in the right place.

---

### Post by kcallis on 2015-04-23
> **billy30 said:**
> i ran into this same problem. What you have to do is partition manually using gparted or windows disk management. 

i used a couple different tutorials, including this one: [http://linux.about.com/od/howtos/ss/How-To-Dual-Boot-Windows-81-And-Linux-Mint.htm](http://linux.about.com/od/howtos/ss/How-To-Dual-Boot-Windows-81-And-Linux-Mint.htm)

i recommend that you follow them carefully and cover all of your bases. i also strongly urge to find a second tutorial. i tried to look for the other tutorial i used. It was an in-depth guide someone posted in the mint forums (could have been ubuntu forums).

It may seem intimidating, but it really isn't. Just follow instructions carefully and make sure you partition your boot swap in the right place.

Actually, the tutorial was good to go and so I now have Mint  17.1 in play. But if I am not mistaken, a lot of the functionality of the 2-in-1 is lost. I see that I need to physically tell Mint (via Display) to rotate the screen. I was trying to rotate and see if I could use xvkbd, that wasn't too successful. So should I just look at the 2-in-1 as a netbook sized device or is there some trick to really make use of the 2-in-1 either landscape or portrait?

---

### Post by kcallis on 2015-04-29
> **kcallis said:**
> Actually, the tutorial was good to go and so I now have Mint  17.1 in play. But if I am not mistaken, a lot of the functionality of the 2-in-1 is lost. I see that I need to physically tell Mint (via Display) to rotate the screen. I was trying to rotate and see if I could use xvkbd, that wasn't too successful. So should I just look at the 2-in-1 as a netbook sized device or is there some trick to really make use of the 2-in-1 either landscape or portrait?

So I noticed that I graphic response was somewhat problematic. I was trying to watch a movie via Plex and it seemed like the images was not sharp. I booted back into Windows 8.1 and the video was clear. I tried to upgrade the Intel Graphics Installer, and realized that the drivers are hard coded specifically to Ubuntu 14.04, and definitely not installable on LM 17.1. I tried all of the various methods (renaming /etc/lsb-release and changing to Ubuntu and trusty, and a few other methods) but no go on that.
 
Considering that my normal I7 laptop is on the bench, I have to make this little guy work for me. So the first thing I would like to do it get the graphics working correctly. So if any one has some ideas about this issue, please sound off!

---

### Post by joe149 on 2015-08-24
Is this laptop supported yet?

---

### Post by kcallis on 2015-08-24
I have yet to get things working. For instance, the touchpad, although from the control panel, the touchpad locks down when using the keyboard, the reality is that even if I am typing, if I brush the touchpad it actives and usually causes havoc with the text I am typing. 

I do realize that this is an atom processor. Nevertheless, I don't push system so hard that it system will lock up for 10 seconds to a minute plus. If I had the time, I would install gentoo or arch and see if could  get better response, but as it stands, using Ubuntu allows to be to show geek points but I don't recommend it to anyone.

---

### Post by Seth_Cox on 2015-10-14
Yes.  Installed Mint 17.2 on Dell Inspiron 11 3000 with N3540 quad processor, 4 GigB RAM, 500GigB Drive.  Preferred the lower power processor for battery life.  About 8 hours of use.  6W I think.  Installs with no problem.  All drives work great.  My associate uses this for business.  Prints to the WiFi.  Screen does not rotate automatically.  Can make executable icons that will rotate if needed.  Works great in tablet mode.  Need to install OnBoard touch keyboard.  Works great.  Dell sells these in Africa with Linux installed so I knew it would work.  I'll post a video soon.  Windows 10: Settings / Advanced Install / Boot from USB, etc., Install Mint 17.2 as only OS / wipe Windows off the machine.  F keys for boot manager won't work with Windows installed.  First post.  Hope it helps.  Huge thanks to all the open source people that have helped em for years!    Seth

---

### Post by sokol99 on 2016-01-22
I did a full install of 17.3 by erasing the disk and installing.  BIOS is A1.  I can use touchpad after resuming from suspend but have other issues identified here such as touchpad not deactivating while typing and also inability to restart without a forced poweroff.

---

### Post by billy30 on 2016-01-22
> **sokol99 said:**
> I did a full install of 17.3 by erasing the disk and installing. BIOS is A1. I can use touchpad after resuming from suspend but have other issues identified here such as touchpad not deactivating while typing and also inability to restart without a forced poweroff.


i haven't done a fresh install since 17.3, but i have the same problem with touchpad not deactivation and screen rotation. It powers off and restarts fine though. I don't plan on doing another fresh install until 18 i think. I feel like your poweroff issue might be something you can google and find the answer too though. Doesn't seem like it would be a complicated fix.

---

