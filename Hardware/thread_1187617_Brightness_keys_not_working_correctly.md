---
title: "Brightness keys not working correctly"
date: 2009-06-14
forum: Hardware
---

### Post by greenie9 on 2009-06-14
Hi,

i have an extremely weird issue with my laptop
> 
dell studio 15
Radeon 4570
1920x1200 screen

i have installed ubuntu on it (doesnt come pre-installed in aus) and have hit a weird bug
with the live CD i am able to adjust the brightness with no issues, but post install, i am only able to change the brightness during the boot/splash screen (ie when it has the loading bar)
Any other time, on the login screen, during actual usage it just sits there and flashes at me like the brightness is at it's highest/lowest

I dont have the ATI drivers installed, as the first time i attempted that, it killed my system (refused to open up login page, just got static) and I had to do full re-install

Obviously it is rather annoying, and it is the one thing issue i have left to fix

Can anyone help?

Thanks heaps

---

### Post by greenie9 on 2009-06-15
can anyone help me with this?

the only other thing i was able to find was this:
[http://ubuntuforums.org/showthread.php?t=1037992](http://ubuntuforums.org/showthread.php?t=1037992)

i have since installed the ATi drivers and now screen seems to be stuck on brightest setting (rather annoying) 

i have worked my way through all the dell keyboard with no success

what happens is this:
i press the either brightness button and it flashes this:
[ATTACH]117755[/ATTACH]

then goes back to this:
[ATTACH]117756[/ATTACH]

im a relative newbie to this, so any/all help would be greatly appreciated

EDIT: going into power management does nothing, nor does the brightness widget, in fact, even when the lid is fully close, the screen stays on

---

### Post by Maheriano on 2009-06-16
I'm pretty sure those function keys work through their own progressive logic controller (PLC) and work via the BIOS/board drivers rather than anything to do with the operating system. That's why they work as soon as you turn on the machine and you don't have to wait for the operating system to load.

What you'll need to do is load all the BIOS drivers again which requires a lot of hacking or simply installing Windows. Or you can pop the drive out and put it into another Windows machine.

---

### Post by greenie9 on 2009-06-16
> **Maheriano said:**
> I'm pretty sure those function keys work through their own progressive logic controller (PLC) and work via the BIOS/board drivers rather than anything to do with the operating system. That's why they work as soon as you turn on the machine and you don't have to wait for the operating system to load.

What you'll need to do is load all the BIOS drivers again which requires a lot of hacking or simply installing Windows. Or you can pop the drive out and put it into another Windows machine.

the thing is, it works fine in windows (vista x64/ubuntu x86 dual boot) so i dont see how that could be an issue... unless it is a conflict between 32 and 64 bit drivers, in which case, why does it just stop working 30-40 seconds after log in?

---

### Post by thinkpet on 2009-06-17
hi . i have the same problem ... on my thinkpad SL500... 
may the lenovo bios updated versions work? 
thanks...

win XP 32 .. works normaly
ubuntu 9 32 ...after using the fn+ up or down brightness key the value gets pemanently stuck on minimum...  

please help how to fix it... 

SL500 nvidia 9300  hm...

---

### Post by Maheriano on 2009-06-17
Seems like the BIOS drivers are getting loaded correctly but then the operating system is loading its own drivers once it fires up which is causing it to not work. Do you have a separate /home partition? I would just reinstall fresh if I were you, mine works with a fresh install no problem.

Otherwise I'm out of ideas and am out of this thread.

---

### Post by Maheriano on 2009-12-09
After about 8 month with this laptop here's what I found out:

- Dell is one of the worst companies on the planet
- They'd have a lot more happy customers if their support employees understood English better

Aside from that, here's my good points with the laptop:
- all functionality seemed to work such as screen brightness, backlit keyboard, eject button, volume buttons.
- Paying the extra money for the backlit keyboard and slot load CD drive was a no brainer. They're 2 of the best features I've had on a laptop to date and I'd never get another without them.
- All software ran  no problem, bluetooth worked fine and Wi-Fi worked on both G and N channels without problems.
- Plugging things in was a breeze like a flash drive, wireless mouse, Blackberry, SD card or secondary VGA monitor.
- integrated webcam worked great.
- mouse touchpad worked great including tap-click and also up/down and side/side scrolling.

Bad things:
- Sometimes the CD drive would randomly try to eject a non-existent CD for 10 minutes straight, just over and over and over......
- speaker volume was very low until installing 9.1, now it's good and loud.

Things I haven't tried yet:
- HDMI output on the ATI HD3450 card
- e-SATA port

---

