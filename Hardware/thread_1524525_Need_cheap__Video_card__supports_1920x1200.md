---
title: "Need cheap  Video card  supports 1920x1200"
date: 2010-07-05
forum: Hardware
---

### Post by jdougmoore on 2010-07-05
I have wasted over 4 hours trying to get this damn Fx 5500 256meg to work with ubuntu and have had it.  Have tried every darn suggestion  I can google and it won't give me more than 1024x768.

What cheap video card can I buy that will be seen by 10.04 LTS and will let me have 1920x1200?  I have a SyncMaster 244T and using the VGA port. No DVI for me.

Tried:
Option "ModeValidation" "NoMaxPClkCheck"
running 96 nvida drivers
running 176 nvidia drivers
manual install of nvidia drivers from terminal with no X-server running.

All I want is a simple < $20.00 video card I can put in this old HP P4 to get 1920x1200 over a VGA port.

My time is worth more than trying to screw around getting this "free Fx 5500"  card working.  Guess it was "free" for a reason.  

Being new to Ubuntu and linux, I don't want to run out an buy another video card that is going to have the same problems.  Suggestions?  I have accounts with Amazon and NewEgg.  Want "plug and play" for Ubuntu 10.04 LTS. :)

---

### Post by jdougmoore on 2010-07-05
39 views and no suggestions? wow, i don't feel so stupid now.. ;)

> **jdougmoore said:**
> I have wasted over 4 hours trying to get this damn Fx 5500 256meg to work with ubuntu and have had it.  Have tried every darn suggestion  I can google and it won't give me more than 1024x768.

What cheap video card can I buy that will be seen by 10.04 LTS and will let me have 1920x1200?  I have a SyncMaster 244T and using the VGA port. No DVI for me.

Tried:
Option "ModeValidation" "NoMaxPClkCheck"
running 96 nvida drivers
running 176 nvidia drivers
manual install of nvidia drivers from terminal with no X-server running.

All I want is a simple < $20.00 video card I can put in this old HP P4 to get 1920x1200 over a VGA port.

My time is worth more than trying to screw around getting this "free Fx 5500"  card working.  Guess it was "free" for a reason.  

Being new to Ubuntu and linux, I don't want to run out an buy another video card that is going to have the same problems.  Suggestions?  I have accounts with Amazon and NewEgg.  Want "plug and play" for Ubuntu 10.04 LTS. :)

---

### Post by djinnkeeper on 2010-07-05
Did you ever figure out a solution / replacement?

I'm assuming you're dealing with PCI and/or AGP?

Make sure you're plugged in to the right "card", considering you probably have onboard + something down in a slot.

Also, please check out this thread[]("http://ubuntuforums.org/showthread.php?t=1524316") ( [http://ubuntuforums.org/showthread.php?t=1524316](http://ubuntuforums.org/showthread.php?t=1524316) ) and see if they're discussing your problem.. not sure based on my cursory glances.

---

### Post by jdougmoore on 2010-07-06
Thanks for the reply. It will be PCI due to the age of the machine.  No, I have not received any suggestions for a cheap Video card that doens't requires 50 unemployed NASA rocket scientists and a supercomputer to figure out the damn Xorg.conf file settings. :)  

Hell, Windows xp/vista/7 have no issues with this card and monitor.  This is the Achilles heel of Linux, video cards.

Yep, saw that thread. Sadly didn't do anything to help me.

> **djinnkeeper said:**
> Did you ever figure out a solution / replacement?

I'm assuming you're dealing with PCI and/or AGP?

Make sure you're plugged in to the right "card", considering you probably have onboard + something down in a slot.

Also, please check out this thread ( [http://ubuntuforums.org/showthread.php?t=1524316](http://ubuntuforums.org/showthread.php?t=1524316) ) and see if they're discussing your problem.. not sure based on my cursory glances.

---

### Post by cascade9 on 2010-07-07
The FX5500 should be using the 173.xx drivers. They should be just a quick GUI poke and restart away with ubuntu (system->administration->hardware drivers). 

As for a PCI video card for $20....er...not new, and even 2nd hard $20 wouldprobably get you something worse than a FX5500. PCI cards have never been cheap. :| 

$40 should get you a PCI 8400GS at newegg, but that isnt going to be 'plug and play' either. But the same as above, its just a quick poke + restart to get the drivers.

---

### Post by jdougmoore on 2010-07-07
I am using the 173.xx drivers, but getting errors galore. Have tried all tricks to get this thing to run at 1920x1200 with zero results. my latest error is that it can't "find"  a nvidia driver.  Any idea where I can post to get some help with this crappy card.  I have manually added the drives from console, edited xorg.conf  with suggestions dating back to 2007, with zero results in getting anything better than 1024x768.

> **cascade9 said:**
> The FX5500 should be using the 173.xx drivers. They should be just a quick GUI poke and restart away with ubuntu (system->administration->hardware drivers). 

As for a PCI video card for $20....er...not new, and even 2nd hard $20 wouldprobably get you something worse than a FX5500. PCI cards have never been cheap. :| 

$40 should get you a PCI 8400GS at newegg, but that isnt going to be 'plug and play' either. But the same as above, its just a quick poke + restart to get the drivers.

---

### Post by cascade9 on 2010-07-08
I dont know what has happened for sure, but I would have to guess that either you've had some hardware failure, or somewhere, something has gone wrong in your attempts to get the video driver installed. 

The FX series should support higher than 1920x1200. I know that I can get 1920x1440 from older GF4 Ti cards as soon as I install the drivers. I cant be sure about widesceen as I dont use the yucky thing. 

> Dual RAMDACs (up to 400 MHz) for display resolutions up to and including 2048×1536 @ 85Hz

[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)

---

### Post by braiamp on 2010-07-08
You check your monitor max resolution? Perhaps yes, you say that windows dosen't have the problem. It´s only an idea, but maybe your video card driver, dosen't work correctly trying to guest the most preferable resolution for your monitor, or your monitor isn't supported by the driver? Maybe, you are searching the problem where is not, try another monitor.

---

