---
title: "New Computer Build Problems"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by thundaraptor on 2009-07-14
I know that this is an ubuntu forum but since I have just built a computer for ubuntu I am posting my problem here.  

I just put together a full system, silverstone sg03 case, amd chip, asus mb and so on.  all the parts should be in good interoperable order so lets not talk about that.  however, i put everything together, including the graphics card (which might have been a mistake to install before a system was up and running) and I thought that I would be able to get a boot screen and use a usb key with bootable files on it.  

I powered up and system was reading usb key but nothing displayed on monitor.  I tried to take out graphics card and use only on board graphics unit but I feel like the graphics card won't come out naturally and don't want to force it.  

Any ideas on how to proceed?  why did nothing come up on monitor and what are some likely troubleshooting steps to take next?  

Thanks 

TR

---

### Post by Sef on 2009-07-14
1) What graphics card do you have?

2) Have you tried to boot from a Live CD?

---

### Post by thundaraptor on 2009-07-14
I have the ATI radeon HD 4670 with dual HDMI.  The motherboard has also an ATI HD 3100 with vga/hdmi interface.  I didn't buy an optical drive as I am trying to keep costs down and this is complement to laptop which is full featured.  Actually, i am not sure if I even formatted the usb key correctly for boot.  Some of the directions I read at ubuntu showed using the syslinux stuff.  I basically unpacked the iso of the current 64 bit jaunty onto the usb and put it in the slot.  (i know, not very sophisticated.)

Any help greatly appreciated.

---

### Post by Shaoline on 2009-07-14
> **thundaraptor said:**
> I have the ATI radeon HD 4670 with dual HDMI.  The motherboard has also an ATI HD 3100 with vga/hdmi interface.  I didn't buy an optical drive as I am trying to keep costs down and this is complement to laptop which is full featured.  Actually, i am not sure if I even formatted the usb key correctly for boot.  Some of the directions I read at ubuntu showed using the syslinux stuff.  I basically unpacked the iso of the current 64 bit jaunty onto the usb and put it in the slot.  (i know, not very sophisticated.)

Any help greatly appreciated.

You should try "unetbootin" (google it), it's a program to assist you in making a bootable usb drive. It can read ISO files, or it can download the preferred ISO straight off the internet and build your usb drive.
The program runs on Linux aswell as Windows.

Quite sure the iso to usb thing you did, didn't turn out well.

As for your graphics card; it should be okey as it is. But if you really need to remove it, there may be a small clip thingy at the "end" of the slot, which should be tilted some to allow the card to be removed. Some security tap. Not all motherboards comes with it.
Never use brute force to remove a card, unless you are really, _really_, sure there is nothing holding it in place.

---

### Post by thundaraptor on 2009-07-14
Shaoline, thanks.  I have notice the clip on the card and was using.  I think the issue was the actual dimensions of my box make the video card a bit touchy.  Will download that application and try it again.  Thanks.

---

### Post by thundaraptor on 2009-07-14
> **Shaoline said:**
> You should try "unetbootin" (google it), it's a program to assist you in making a bootable usb drive. It can read ISO files, or it can download the preferred ISO straight off the internet and build your usb drive.
The program runs on Linux aswell as Windows.

Quite sure the iso to usb thing you did, didn't turn out well.

As for your graphics card; it should be okey as it is. But if you really need to remove it, there may be a small clip thingy at the "end" of the slot, which should be tilted some to allow the card to be removed. Some security tap. Not all motherboards comes with it.
Never use brute force to remove a card, unless you are really, _really_, sure there is nothing holding it in place.

Creating usb now, how do I know that the machine is entering the bios once I have this all square?

---

### Post by master_kernel on 2009-07-14
You should hear a beep when you press your power button; if not that you should at least see the BIOS screen on the monitor.

---

### Post by thundaraptor on 2009-07-14
have created boot usb but still not getting a signal on monitor.  connected main onboard vga out to monitor and tried booting without usb in and usb in but not finding a way to enter bios.  have asus M3A78-CM board with AMD phenom core and 4 gigs 1066 ram.  Video card is ATI Radeo HD 4670 and onboard video is ATI HD 3100.  Trying to install Jaunty 9.04 64bit arch.  Thanks for help

---

### Post by thundaraptor on 2009-07-14
No seeing anything on monitor.  It seems straight forward, putting all this stuff together but maybe I have made a mistake somewhere.  Are there some common troubleshooting steps I should be looking at?

---

### Post by Ra-Hoor-Khuit on 2009-07-14
Okay, so you boot the PC and then what?  

You probably won't be able to boot from USB without configuring your BIOS first, so we need to make sure the machine is at least passing POST. 

So... is it POST'ing successfully?  Do your CPU and  video card fans spin up when you power-on?  Is there hard drive activity? Do you seee anything on your monitor at any time indicating any kind of activity whatsoever?

---

### Post by thundaraptor on 2009-07-14
CPU and Video Card fans are spinning.  Not sure about HD, LED for HD activity is getting one light but then nothing.  Not seeing anything on the monitor to indicate any kind of activity other than Acer interface window "no signal".  Again, not sure if that fact that I installed the external video card is impacting this but can't seem to take it out either.

---

### Post by gzigoris on 2009-07-14
> **Ra-Hoor-Khuit said:**
> Okay, so you boot the PC and then what?  

You probably won't be able to boot from USB without configuring your BIOS first, so we need to make sure the machine is at least passing POST. 

So... is it POST'ing successfully?  Do your CPU and  video card fans spin up when you power-on?  Is there hard drive activity? Do you seee anything on your monitor at any time indicating any kind of activity whatsoever?

Follow those instructions and and make your PC the minimum to work. Remove your video card and use the on board video. use the minimum amount of memory. Even remove hard drive. Just boot up to your bios and see if the display works then. If you get a display then add one item at a time and see where your problem is.

Remember to turn off your on board video if you add a video card. Go through your BIOS setup and make sure everything is set the way you want it. Remember the secret of troubleshooting is the KISS method
Keep I Simple Stupid. That works every time.

George

---

### Post by Ra-Hoor-Khuit on 2009-07-14
> **thundaraptor said:**
> CPU and Video Card fans are spinning.  Not sure about HD, LED for HD activity is getting one light but then nothing.  
Okay, so we can deduce from this that your power supply is in fact supplying juice and that the critical components are getting power.  That's a good start.

> **thundaraptor said:**
> Not seeing anything on the monitor to indicate any kind of activity other than Acer interface window "no signal".  Again, not sure if that fact that I installed the external video card is impacting this but can't seem to take it out either.
If I had to guess, the reason you're not getting any output on the monitor is because the onboard video is deferring to the installed video card since the slot is reporting to the BIOS that it has been populated with a video card.  If you haven't already, make double-sure the video card is properly seated in its slot and that any auxiliary power connectors have been plugged in.  Then move the monitor cable *from* the on-board video chip-set connector *to* the installed video card connector and then reboot.  See if your monitor is detected this way, it should be.  If it is, watch for the keystroke sequence to enter BIOS setup.  Most likely it will be the DELete key or the ESCape key, F8 or something like that.

---

### Post by thundaraptor on 2009-07-14
Ok, thanks.  This is about what I thought was the issue.  First go through last night was monitor connected to installed video card.  will try again and see what happens.  How to know if video card has any kind of secondary power connection?  i didn't see anything nor does the manual have information of this type.  Really super appreciate these posts guys.  Part of why I am becoming die hard linux fan.  

Thanks

---

### Post by thundaraptor on 2009-07-14
Have taken out external video card and now was able to enter bios.  I added usb to priority list in 1st position. save and exit bios.  now reboot but no activity other than basic splash screen for mother board, can still enter bios on reboot but nothing happening with usb key.

if i put the usb key in from the beginning of the boot, the splash screen will also come and then go, then screen says "reboot and select proper boot device or insert boot media in selected boot device and press a key"  but with usb in nothing happens.  

the splash screen, coming and going with the usb key in both cases inserted is dependant in which frontside or backside usb port i use.  if use backside splash screen comes and goes, it frontside splash screen freezes.

---

### Post by Ra-Hoor-Khuit on 2009-07-15
Well that's progress.  

When you burned the .iso to the USB thumb drive, did you burn it as an image file?  I ask because it appears the machine IS trying to boot from the USB drive but it's not finding it to be a bootable device.  If you just copied over the .iso instead of making the drive itself bootable, that would be the problem.

---

### Post by thundaraptor on 2009-07-15
I actually followed the instruction for the netbooten usb configuration app.  I think I did it correctly but not entirely sure.  The iso copy was my very first go around but have since "progressed" to more sophisticated measures, like begging at ubuntu forums.

---

### Post by Ra-Hoor-Khuit on 2009-07-15
I don't know where you got your instructions from, but the few times I've used Unetbootin I've followed this tutorial for building the bootable thumb-drive:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by thundaraptor on 2009-07-15
Yes, I have followed the same tutorial.  I think I followed instructions correctly but not entirely sure.  Is there a way to verify that the usb is good?

---

