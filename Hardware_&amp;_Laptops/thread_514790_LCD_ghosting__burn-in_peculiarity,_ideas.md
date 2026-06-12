---
title: "LCD ghosting / burn-in peculiarity, ideas?"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by HarryHaller on 2007-08-01
Hi,

My system:
**ATI Radeon Sapphire 9600SE 128MB**
Asus P4P800 Deluxe
P4 3.0GHz

I'm having a strange problem wherein ghost images of the Ubuntu / Gnome desktop will persist when I boot into Windows afterwards and for a few hours form then on.  I first noticed that the top Gnome desktop bar (with clock etc.) would ghost over the windows desktop, but have noticed it with other little things too since I've been troubleshooting.

I'm convinced it's an Ubuntu problem, as the reverse will not happen with the windows start bar or other GUI elements, plus I now have a 2min wait screensaver in Ubuntu and no screensaver for Windows and the problem is ongoing.  

My theory is that whatever the default driver used by Ubuntu  for my ATI card (card details above) is responsible, interfacing incorrectly with the card and then the signal-range output by the card is leading to the "burn-in".  The weird thing is that I've never experienced ghosting with LCDs and didn't know it even occurred until after a bit googling.  

But I couldn't find anyone having the same problem with Ubuntu.  Has anyone experienced this, or does anyone have any ideas on how I could resolve it?

Many thanks.

---

### Post by fredj on 2007-08-01
You don't get burn in with lcds in the same way that you do with crt monitors but you can get
something called image persistence if you leave the same image on the screen for a long time.
You should set ubuntu to run a screensaver.
Try displaying a completely white screen on your lcd for an hour or so and see if this gets rid of it.

---

### Post by HarryHaller on 2007-08-02
Thanks, for the reply Fred,

I do realise that burn-in doesn't really happen for LCDs and probably should've called it image persistence, but I have been running a screensaver without luck in stopping the problem, altough it *does* go away after a couple of hours, so it's persitent in that it's ongoing and reproducible, rather than constant.

Basically I wanted to know if it could damage the screen over the long term and any ideas on fixing it permanently 'cause I haven't had the problem in using the same screen and graphics card with windows drivers for 3 years.

thanks

---

### Post by deadite66 on 2007-09-06
having the same problem atm, now running a white screen when i watch podcasts all week but doesn't seem to be helping :(

---

