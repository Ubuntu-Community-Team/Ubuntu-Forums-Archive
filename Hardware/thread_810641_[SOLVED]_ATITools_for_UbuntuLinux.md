---
title: "[SOLVED] ATITools for Ubuntu/Linux?"
date: 2008-05-28
forum: Hardware
---

### Post by lightwarrior on 2008-05-28
Hi, I have a laptop Dell Latitude D610 with Ubuntu, PCLinux and WinXP Pro.  Lately I started to have mostly random freezing and some video corruption on all tree OSs.  On WinXP I found that my dedicated video card ATI mobile Radeon X300 is operating by default at memory speeds above specs (216Mhz instead of 200Mhz).  I was able to bring down this frequency with ATITools, which at startup I was able to set to 196Mhz and everything has been fine for WinXP, not a glitch.  Do you know if there is a similar tool in Linux/Ubuntu that will allow me adjust the settings on the video card internal GPU/Memory Frequencies?  Thanks!

---

### Post by zgornel on 2008-05-28
The solution is a bit more radical than in Windows. It involves lowering core, memory clocks and also voltages applied to the video card. To view what powerstates you have, do :
```
aticonfig --lsp
``` There should be 3 or 4 (the current one is marked with a '*'). To change to powerstate 2 for example, you should write:
```
sudo aticonfig --set-powerstate=2
```. Check again to be sure the powerstate was changed.

---

### Post by lightwarrior on 2008-05-29
Thanks a lot!!!
This is what I was looking for.

---

### Post by zgornel on 2008-05-30
You're welcome. You can put the commands in a script that is automatically launched during the boot process and also while resuming from suspend/hibernate, I don't think the changes stay after rebooting/powering off.

---

### Post by estyles on 2008-07-06
Hey,

My ATI card also runs too hot at default speeds.  I always underclocked it in windows with ATI Tool.  I have an X800 and it only shows 1 speed, 398/398 MHz (default).  Is there a way to slow it down if it doesn't show any other possible powerstates?

---

### Post by zgornel on 2008-07-06
> **estyles said:**
> Hey,

My ATI card also runs too hot at default speeds.  I always underclocked it in windows with ATI Tool.  I have an X800 and it only shows 1 speed, 398/398 MHz (default).  Is there a way to slow it down if it doesn't show any other possible powerstates?

The answer is on the second post. You have to use the proprietary fglrx dirver for it to work.

---

### Post by pietjanjaap on 2008-07-06
> **estyles said:**
> Hey,

My ATI card also runs too hot at default speeds.  I always underclocked it in windows with ATI Tool.  I have an X800 and it only shows 1 speed, 398/398 MHz (default).  Is there a way to slow it down if it doesn't show any other possible powerstates?

Clean your pc.
Renew the thermal paste of your videocard cooler.
Check your pc if it is cool enough, maybe more fans.

---

### Post by estyles on 2008-07-06
So... no then?  I've already taken apart the video card, cleaned it out, made sure it had a good connection with the heat sink.  I have vacuumed out the entire computer, and I have plenty of fans.

Zgornel, I read your post, that was what I was asking about.  I'm using the fglrx driver.  I did atitest --lsp, and like I said in my post, it only shows one possible powerstate.  There's no way to tell it to run at a different speed?  I usually use 333 MHz in Windows.

---

### Post by zgornel on 2008-07-07
> **estyles said:**
> So... no then?  I've already taken apart the video card, cleaned it out, made sure it had a good connection with the heat sink.  I have vacuumed out the entire computer, and I have plenty of fans.

Zgornel, I read your post, that was what I was asking about.  I'm using the fglrx driver.  I did atitest --lsp, and like I said in my post, it only shows one possible powerstate.  There's no way to tell it to run at a different speed?  I usually use 333 MHz in Windows.

I understand now, it is a standalone graphics card. I thought it was a mobile one, my bad ;). You can try using **rovclock** to underclock it if your card is supported. More info at [http://www.thinkwiki.org/wiki/Rovclock](http://www.thinkwiki.org/wiki/Rovclock) .

---

### Post by estyles on 2008-07-07
Thanks, I'll give that tool a try.  Have been considering buying a new GFX card (nVidia, specifically, since they seem to be supported better in Linux), but the X800 is not quite old enough for me to justify that with my budget, since any new one that I'd buy would probably be around $150, and I don't play games all *that* much to be buying a new card every 2 years.

---

### Post by zgornel on 2008-07-07
No probs, hope it works. As for graphics performance, I have a X1350 (128MB, 64bit DDR2) but I play only glxgears ;) .

---

