---
title: "Toshiba U205 screen resolution problem"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by ohrock on 2006-09-21
I just got this laptop for my wife, and basically X is acting up on me.

Somehow is detecting everything -right resolution and all, 1280x800 - but when X gets up and running it shows a resolution of about 1024x728 that acts as kind of a window for the rest of the space.  When you move to the side it automatically scrolls to display the rest of the desktop.

Anyway,  I played around with xorg.conf file, adding modelines I found in google searches, I specified displaySize - in mm, - and even played with 915 resolution, but nothing seems to work.

Has anyone seen a problem like this?  Can someone maybe think of something I haven't?

Thank you!

---

### Post by dpider on 2006-11-02
I have the same problem, i search and search but i don't find nothing........

only using driver vesa, i can view the screen 1280x800

---

### Post by penvzila on 2006-11-11
I have the same problem, I'm stuck using VESA.

---

### Post by penvzila on 2006-11-16
I'm pleased to report this was an easy fix with Fedora Core 6.  I'll try the next version of Ubuntu, but for now I've got pretty much everything working in FC that I had in Ubuntu, plus the video issue which obviously was not working.

I'll definitely try out future versions of Ubuntu, though.  The multimedia support in particular is very good.  I still consider it the best flavor of Linux, but I need a fully functional linux system RIGHT NOW, and I have to go with what works right now.

---

### Post by dpider on 2006-11-16
VESA not is the solution, because we are lost the optimal work. 945 is a good graphical card, vesa has lost that 945 don't has. I probe using gentoo, debian etch and ubunto edgy, but i have the same problem, i change the bios to old version, new vesion but i don't can resolve the problem.

---

### Post by penvzila on 2006-11-17
I'm holding out hope that this will be fixed in the next release.

---

### Post by brainsurgeon on 2006-11-17
I have a same problem. I have ASUS W3A. I mounted 2 OS: XP on first partition. Ubuntu on second partition. Ubuntu good working but except a few problem. One of them I didn't change screen resolution. Becouse Ubuntu recognized my screen card as 850. but My computer graphic card is Intel 915.

---

### Post by dpider on 2006-11-24
I could,:p :-D . I was read to much, but, I was have that ,i810 run in toshiba u205 s5002 to 1280x800 with driver i810 NO VESA. I put my file here

Only rename xorg.conf.txt to xorg.conf and put in /etc/X11 and enjoy.

---

### Post by penvzila on 2006-11-29
I'll try this in my U2005 tonight.  I see you used a  custom modeline.  I tried that for a while, but I couldn't figure out the exact specs of the LCD.

---

### Post by penvzila on 2006-11-29
It works perfectly.  Wow, I can't thank you enough for posting that.

---

### Post by dcalp on 2006-12-13
Thanks a lot dpider!! Works perfectly for me too. I tried several distros without success, but I always wished to keep Ubuntu. 
WinXP, bye bye in few days :-D 

Thanks again!

Diego

---

### Post by BattleStarJesus on 2007-10-01
HEY!
UBUNTU = Self Sustainability
I to am using a Toshiba Satellite U205-S5002!

I have not been able to properly configure and utalize the monitor port.  Will some provide me with some guidence?

UBUNTU!!!!

---

