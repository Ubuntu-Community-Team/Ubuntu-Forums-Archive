---
title: "Random USB Mouse Freeze with NVIDIA"
date: 2009-11-26
forum: Hardware
---

### Post by gvvsss on 2009-11-26
Hello

I am a system administrator, but little new to Linux.

I have a desktop system (Personal) with the following configuration.

AMD Phenom X4 9550, ASUS M3N78-VM Motherboard (NVIDIA GeForce 8200), 2 GB RAM, Logitech USB Mouse, Logitech PS/2 Keyboard

I have recently installed Ubuntu Karmic erasing all my previous jaunty installation.

Since then, I am facing frequent random mouse hangs and everything else is working fine. Even when mouse freezes everything seems to work with keyboard. I am able to do a normal soft reset with Ctrl+Alt+Del, but it has become so regular and annoying.

All my system works fine when I put the same HDD in another system with ATI or Intel Graphics, so it seems to have something to do with NVIDIA.

It also works fine when I put the same HDD in an NVIDIA system with PS/2 mouse.

I have no choice on my Motherboard to use a PS/2 mouse, so I am locked up.

Is there any way I can isolate the issue, what is causing the freeze (any software package),or if it a real bug yet unsolved,, any test or log etc?

---

### Post by gvvsss on 2009-11-27
Somebody please help...

---

### Post by 16777216 on 2009-12-05
I have been having the same problems, I have an Asus M3N78-PRO motherboard And a cheap USB keyboard and mouse.

Both the mouse and keyboard hang on me at random though the mouse hangs more.  

I also have an USB HP printer that as far as I can tell doesn't hang but it does have it's USB connection reset every few seconds to minuts, and while the KB and mouse don't hang on Win7 the printer still does the connection reset thing.

While I am not sure I belive it is related to the motherboard.


After a hang typeing "lsusb" in a console gets me nothing the program just hangs.

Yesterday while chating with a friend the keyboard hung ay the exact moment I hit the "H" key, this resulted in a never ending string of "hhhhhhhhhhh" so I am not sure of what happened there.

Resetting the computer seems to be the only fix.

I hate this makes me want to use another distro.

I wish I at least knew how to reset the USB sistem without having to reset the whole computer

---

### Post by gvvsss on 2009-12-07
Although I did not find a working solution, I have been out of the problem with a little expensive workaround,

I have put two USB Mice (both logitech) to two different ports and when one mouse hangs the other one is working for me. Very rarely I see both hanging up.

Again,

This is nowhere a solution, and I seriously need a solution.

Somebody Please help..

---

### Post by gvvsss on 2009-12-17
Any Idea????

---

### Post by chewearn on 2009-12-17
I think I have seen this problem a long time ago, in a computer with nvidia chipset.  If I am remembering correctly, I managed to solve it by going into BIOS and turn OFF the setting for "USB keyboard/mouse legacy support".

---

### Post by gvvsss on 2009-12-17
Tried switching off compiz, still the same problem.

In my BIOS Legacy USB option is not available.

---

### Post by 16777216 on 2009-12-20
I updated the BIOS to ver 1301 and turned the high precision timer ( can't remember the exact name ) off.

The result has been only one lock up sense my last post.

---

### Post by gvvsss on 2009-12-21
Where should I turn off the high precision timer?

---

### Post by buteomont on 2009-12-21
I have the same problem, but my mouse seems to always freeze just as I'm trying to view my webcam.  Only once has it frozen otherwise, and that was when I was booted from the karmic koala live CD (while trying to fix a different problem).

Also, I'm having trouble getting anything USB to work.  My USB keyboard seems fine, but just about anything else I plug in will not work.  Sometimes (but not always) lsusb will hang.  When it doesn't hang, it shows the device I have plugged in just fine (such as a bluetooth dongle or webcam), but the device still doesn't work.  Sometimes the webcam will work, but then I lose my mouse when I try to view it. :confused:

Does anyone know how to reset the USB subsystem without having to reboot?

---

### Post by 16777216 on 2009-12-21
What I was talking about is the HPET [High Precision Efficient Timer]option in the power section of the BIOS setup screens.

I am not sure if this was the answer or if it was the updated BIOS or both but I still have only had one lock up.

I found a [Wiki article]("http://en.wikipedia.org/wiki/High_Precision_Event_Timer") on HPET though the article calls it the "High Precision **Event** Timer" I am still sure my motherboard says "Efficient"

---

### Post by 16777216 on 2009-12-21
> **buteomont said:**
> I have the same problem, but my mouse seems to always freeze just as I'm trying to view my webcam.  Only once has it frozen otherwise, and that was when I was booted from the karmic koala live CD (while trying to fix a different problem).

Also, I'm having trouble getting anything USB to work.  My USB keyboard seems fine, but just about anything else I plug in will not work.  Sometimes (but not always) lsusb will hang.  When it doesn't hang, it shows the device I have plugged in just fine (such as a bluetooth dongle or webcam), but the device still doesn't work.  Sometimes the webcam will work, but then I lose my mouse when I try to view it. :confused:

Does anyone know how to reset the USB subsystem without having to reboot?
Sorry, I still haven't found a way to reset the USB system.

---

### Post by Laryllan on 2009-12-22
I own the same MB and would like this problem solved. But:

This seems to be a common issue with the Asus M3N78 series. The problem is not Linux specific, as all kinds of users complain. Just google for "asus m3n usb problem"...

UPDATE:
I just found a thread in the Nvidia support forum about the problem:
[http://www.nvnews.net/vbulletin/showthread.php?t=123583](http://www.nvnews.net/vbulletin/showthread.php?t=123583)

The one guy has a sollution, which might work. It seems the be a IRQ issue. He passes the kernel boot option "pci=nomsi" to grub (standby will work he states) and enables "PnP aware OS = YES" in BIOS. This way the interrupts are selcted by the OS instead of the boards BIOS. I'm trying these two now...

---

### Post by buteomont on 2009-12-22
I'm not convinced that it's an Nvidia problem.  My mouse would hang even when booting from the live CD, without the Nvidia driver being loaded.  The keyboard would still work though.  However, the mouse would hang ***every time*** I tried to view a live image from my webcam.

I upgraded my kernel to version 2.6.31-17, and now it doesn't hang when I view a webcam.  I've had one hang since upgrading, and this time it was both the keyboard and the mouse.  I think it's USB related, because that part of my setup still seems wonky.  Maybe the new kernel fixes one problem and introduces another.  Or maybe there was more than one problem all along.

---

### Post by Laryllan on 2009-12-22
Sorry if this one wasn't clear in my post:
It's *not* a Nvidia problem, it's an interrupt problem that affects the USB controller - or at least a problem of the BIOS/USB driver.

It seems it has nothing to do with graphics.

---

### Post by 16777216 on 2009-12-22
I found this a few minuets ago.

[http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html)

If you are using grub2 the steps may be different.

---

### Post by gvvsss on 2009-12-22
I too need a way of resetting USB system without having to totally reboot.

As far as I observed, I could very well manage with two mice running parallel, as one stops moving, the other works fine for at least 2 to 3 hours ( Happens with both, independent of order)

---

### Post by 16777216 on 2009-12-22
> **gvvsss said:**
> I too need a way of resetting USB system without having to totally reboot.

As far as I observed, I could very well manage with two mice running parallel, as one stops moving, the other works fine for at least 2 to 3 hours ( Happens with both, independent of order)
Are you saying that you can and/or have had two mice plugged in and when one stops the other still works?
Or, *if* you had two plugged in would one work if the other stopped?

Because as far as my specific issue goes I have tried to plug in another mouse after a lockup with no luck. As well as to have two plugged in concurrently only to have both lock up simultaneously.

---

### Post by 16777216 on 2009-12-22
> **gvvsss said:**
> I too need a way of resetting USB system without having to totally reboot.

As far as I observed, I could very well manage with two mice running parallel, as one stops moving, the other works fine for at least 2 to 3 hours ( Happens with both, independent of order)
Are you saying that you can and/or have had two mice plugged in and when one stops the other still works?
Or, *if* you had two plugged in would one work if the other stopped?

Because as far as my specific issue goes I have tried to plug in another mouse after a lockup with no luck. As well as to have two plugged in concurrently only to have both lock up simultaneously.

---

### Post by gvvsss on 2009-12-22
In my case, I do keep both my mice plugged in (always), I use one mouse and if it freezes the other still works.

I tried playing with both randomly and that led to both mice freezing, So presently, what I am doing is using one mouse as long as it works, and when it freezes (usually 5 to 15 min from startup), use the other mouse and it works for almost 2 to 3 hrs from then without problem.

Although I do not find any reason/logic behind this, and I know that this is not a solution, I do not have another solution yet.

---

### Post by buteomont on 2009-12-22
> **16777216 said:**
> I found this a few minuets ago.
 
[http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html)
 
If you are using grub2 the steps may be different.
 
I tried this. I first tried it by editing the startup commands during bootup in grub, and it did seem to help some, but didn't completely fix the problem. So I went ahead and followed the instructions for grub2, since I'm using the wubi version of karmic.
 
Now my ubuntu installation is scrambled beyond repair, apparently as a result of the infamous grub2 update problem, which I thought I had licked. 
 
I decided to try Ubuntu when I bought a new computer and had Vista 64 forced upon me. The computer came with a promise of Windows 7, but when it arrived it was also the 64 bit version only. There are no drivers for anything 64-bit in the windows world, and Microsoft won't allow folks to write their own or use 32-bit drivers on a 64-bit system. I don't know why, but I'm sure it has to do with money somehow. So I decided to either purchase the 32-bit version of Win7 or switch to Linux. I decided to go with Linux since it's cheaper and I could still use my 8 GB memory that I bought with this PC. With Win7-32 I'd be limited to about 3 GB.
 
So after having spent over three weeks trying to get ubuntu to work, I give up. I guess the more expensive option is all I have left. I've had more trouble trying to get Ubuntu to just *work* than I *ever* had with XP. I can't tell you how many times I've had to reboot and try different things just to get simple things like the USB ports to work. I've rebuilt from scratch twice, and spent hours on forums like this one trying to dig out _any_ magic incantation that would allow my PC to do what it's supposed to do. It's all just too much.
 
It's a shame, too. I really like the Ubuntu look and feel, and the Linux/GNU paradigm. Beats the heck out of the money grubbers at MS.

---

### Post by 16777216 on 2009-12-24
> **buteomont said:**
> I tried this. I first tried it by editing the startup commands during bootup in grub, and it did seem to help some, but didn't completely fix the problem. So I went ahead and followed the instructions for grub2, since I'm using the wubi version of karmic.
 
Now my ubuntu installation is scrambled beyond repair, apparently as a result of the infamous grub2 update problem, which I thought I had licked. 
 
I decided to try Ubuntu when I bought a new computer and had Vista 64 forced upon me. The computer came with a promise of Windows 7, but when it arrived it was also the 64 bit version only. There are no drivers for anything 64-bit in the windows world, and Microsoft won't allow folks to write their own or use 32-bit drivers on a 64-bit system. I don't know why, but I'm sure it has to do with money somehow. So I decided to either purchase the 32-bit version of Win7 or switch to Linux. I decided to go with Linux since it's cheaper and I could still use my 8 GB memory that I bought with this PC. With Win7-32 I'd be limited to about 3 GB.
 
So after having spent over three weeks trying to get ubuntu to work, I give up. I guess the more expensive option is all I have left. I've had more trouble trying to get Ubuntu to just *work* than I *ever* had with XP. I can't tell you how many times I've had to reboot and try different things just to get simple things like the USB ports to work. I've rebuilt from scratch twice, and spent hours on forums like this one trying to dig out _any_ magic incantation that would allow my PC to do what it's supposed to do. It's all just too much.
 
It's a shame, too. I really like the Ubuntu look and feel, and the Linux/GNU paradigm. Beats the heck out of the money grubbers at MS.
I am sorry that Ubuntu has given you so much trouble.
Have you tried a a dual boot install? ( no wubi ) I have had nothing but problems from wubi no mater what computer I have used it on.

But, unfortunately Ubuntu and Linux in general on some hardware configurations is nothing but trouble.

---

### Post by buteomont on 2009-12-24
Thanks for the sympathy. :) Glad to know the problem is not just me.

I actually am ahead of you on this one. I decided to give it one more shot, since there's no hope to get my stuff working on 64-bit Windows with this machine.  At least there's some hope with Ubuntu.  I bought a new hard disk, and installed Ubuntu Karmic Koala on it in a dual-boot configuration.  I wanted to bypass the boot loader selection altogether and select which OS to load in the BIOS, but Ubuntu went ahead and loaded Grub2 on the other (old) disk drive anyway.  Grrr.

So far, the dual boot setup seems a lot more stable that wubi was (I hope I didn't just jinx myself).  My mouse hasn't hung at all yet!  But I'm still having trouble with USB, Bluetooth, my Intel Play microscope, and Thunderbird, to name the few things I've had time to try.  I'm keeping my fingers crossed.

---

### Post by 16777216 on 2009-12-24
@ buteomont

That's not a bad idea I think you can quick pick a drive to boot from with F8. :confused:

But you may want to update the BIOS because I believe that is what has fixed it for me. Well I have had only one lockup in the past 5 days and that was on the same day but no more after that if you want to call that fixed. :P

you can find the BIOS [here on ASUS's website]("http://usa.asus.com/product.aspx?P_ID=DVvm9CU0G1bCC4gp") on the download tab choose Vista 32bit as your OS and expand the BIOS listing and download version 1301.
Unzip it and put the .bin file on a thumb drive or a CD-RW ( don't want to waste a CD-R on just a few megs. ) go into the BIOS and use the EZ-Flash option to flash the BIOS from the drive.

I also turned off the HPET in the power section of the BIOS setup but I don't know if this was of any effect.

---

### Post by kenm_uk on 2010-01-08
To cut a long story short, I too am having this problem with the ASUS M3NH-HDMI.  I bought this board a long time ago and had issues with the mouse freezing so gave it to a friend who wanted to build a Windows system.  The friend has given me back this system and I have put Ubuntu 9.10 on it (for a HTPC) only to discover the mouse freeze problems are still there.

I originally wrote about this problem way back here (when I was a Fedora 9 user)
[http://forums.fedoraforum.org/showthread.php?t=188757](http://forums.fedoraforum.org/showthread.php?t=188757)

There appear to be a few new suggestions in the forum here which I will try this weekend.  If anyone else has managed to figure out a solution not posted, please share.

Thanks,
Ken

---

### Post by kenm_uk on 2010-01-09
> **16777216 said:**
> @ buteomont
I also turned off the HPET in the power section of the BIOS setup but I don't know if this was of any effect.

I updated the BIOS on my M3N-H/HDMI to the most recent release. I also turned OFF HPET.  I turned on USB 2.0 and turned on USB Legacy. I turned on Plug&Play.

I also updated the grub2 boot command as in:
[http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html)

At the moment I have not had a mouse crash for 30 minutes and counting... already much better! :D  I think the trick was turning off HPET.

---

### Post by plutonia on 2011-05-20
Happened to me in 10.04, 10.10 and now 11.04. Tried everything... and ended up blaming BIOS/mobo in the end.  

Later, just choose the basic (non-effects) vesion of the GDM at the bottom of the login screen (hard to see until you look down there). Now no problems at all - its the effects that break the graphics card and cause it to upset the interrupts or the memory used by USB devices (on my system anyways). YMMV- beware and good luck :)

---

### Post by Laryllan on 2011-05-20
I'm not using Compiz, too.
But my problems were gone after a BIOS update a while ago.

---

### Post by 16777216 on 2011-05-20
I haven't had this problem for a long time now.  I can't say what the fix was, BIOS update? Kernel fix? Who knows. I plan to keep this open as it seems others are still having this problem. All I can say is try all of the above someone will find the true combination that works.

BTW my BIOS is ASUS M3N78 PRO ACPI BIOS Revision 1402

Kernel Linux 2.6.38-8-generic

---

### Post by drinkwaterpaulie on 2011-06-24
I had exactly the same problem, which became more frequent when I upgraded to 11.04 Natty Narwhal. I upgraded my PC's BIOS to the latest version and I've had no freezing since.

---

### Post by 16777216 on 2011-06-24
So the fix seems to be the BIOS up date and not any of the settings.

---

### Post by save2 on 2013-04-21
I solved it but it cost me 20$
ubuntuforums.org/showthread.php?t=2136506&p=12612114

---

