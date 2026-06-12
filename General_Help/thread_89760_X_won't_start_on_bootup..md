---
title: "X won't start on bootup."
date: 2005-11-13
forum: General Help
---

### Post by nageeb on 2005-11-13
I actually just posted this in the Desktop Support section, but realised that it'd be better in the main forum... 

I've had Breezy installed for just over 2 weeks now and am loving it.

This morning, i rebooted in order to check something on my windows drive (dual-boot XP/Ubuntu) and when i rebooted in Ubuntu, Gnome wouldn't start properly.

The computer boots up like normal, the black screen comes up with the ubuntu logo and the startup tasks and then it flashes blank, then my display goes half black, half white (split horizontally across the middle) and i get the terminal login prompt. It seems to even crash out of the usual "Failed to star X server... " so i can't even see a log.

I know somehting like this is hard to diagnose for someone not directly at the computer, so i'm just looking for some guidance on where i can start looking (i.e. log files etc) .

I'm running a P4 2Ghz/512Mb with an Nvidia 5500 on twinview. My graphics have been working 100% since i set them up (dual monitors) so i'm quite sure that's not my problem. I even restored the xorg.conf to the default setup and still no dice.

Any help would be appreciated.

---

### Post by Teroedni on 2005-11-13
sudo gedit /var/log/Xorg.0.log 

Gives you a log over the x window ststup sequence
This will be able to tell you what went wrong

If you want help you could post it on [www.pastebin.com](www.pastebin.com)
or in this forum
Remeber to post the whole xorg

---

### Post by nageeb on 2005-11-13
Thanks.  I grabbed the file but couldn't see readily where anything was going wrong... 

Here's my Xorg.0.log file
[http://pastebin.com/427923](http://pastebin.com/427923)

---

### Post by Teroedni on 2005-11-13
#
(**) |-->Screen "Screen0" (0)
#
(**) |   |-->Monitor "Secondary"
#
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5500]"
#
(EE) Screen Screen1 doesn't exist: deleting placement

heres the error 
your xorg.conf is wrongly configured

I see your sing xinerama
You got 2 monitors connected to that card right?

paste xorg.conf in the pastebin
the whole file

sudo gedit /etc/X11/xorg.conf

---

### Post by nageeb on 2005-11-13
[QUOTE=Teroedni]#
(**) |-->Screen "Screen0" (0)
#
(**) |   |-->Monitor "Secondary"
#
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5500]"
#
(EE) Screen Screen1 doesn't exist: deleting placement

heres the error 
your xorg.conf is wrongly configured
[/QUOTE]

Wow that's weird,  didn't change anything in my video settings or my xorg.conf file...   anyway, here it is.

[http://pastebin.com/428375](http://pastebin.com/428375)

---

### Post by nageeb on 2005-11-13
Well well. I edited my xorg.conf and nothing happened.  I looked back at my Xorg.0.log and noticed a line where it said something about unknown chipset in video card at pci.0.0.1.  On a whim, i recompiled and reinstalled my video drivers and  Poof!  i'm back in business.

Thanks for the help guys!

---

