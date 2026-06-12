---
title: "Monitor flickering"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by foxy123 on 2005-09-30
The monitor on my NEC Versa M400 flickers every now and then It changes either the contrast or brightness (I cannot figure it out). I wonder if it is a software or hardware problem I bought this laptop second-hand and I have never had anything but Ubuntu on it. Any way to check what it is?

---

### Post by KingBahamut on 2005-09-30
Typically screen flicker isnt a good sign. Specially on a laptop. Your probably looking at a bad screen. 
Thatd be my first guess. When you change video modes what happens? screen refresh?

---

### Post by foxy123 on 2005-09-30
[QUOTE=KingBahamut]Typically screen flicker isnt a good sign. Specially on a laptop. Your probably looking at a bad screen. 
Thatd be my first guess. When you change video modes what happens? screen refresh?[/QUOTE]
what do you mean by video modes?

---

### Post by KingBahamut on 2005-09-30
when you change from 800x600 , or 1024x768 in the Screen resolution module under Administration......what happens? 

what about refresh rates?

---

### Post by foxy123 on 2005-09-30
[QUOTE=KingBahamut]when you change from 800x600 , or 1024x768 in the Screen resolution module under Administration......what happens? 

what about refresh rates?[/QUOTE]
The thing is that I have never been able to change neither the resolution nor refresh rate. I've got only 1024x768 and that's all. It also bothers me because I thought that it is possible to switch to lower resolution.

---

### Post by KingBahamut on 2005-09-30
Sounds like a very unhappy monitor/screen.

---

### Post by foxy123 on 2005-09-30
[QUOTE=KingBahamut]Sounds like a very unhappy monitor/screen.[/QUOTE]
I doubt if the monitor cares at all. It is me who is truly unhappy with it....

---

### Post by CompShrink on 2005-12-09
My laptop, a Dell Inspiron 5100, has the same problem.

It happens on Windows, Ubuntu, and Suse, it's not a software issue.

I find it's rarely a problem, but often happens if I close the screen part way through hibernating (in Windows) it will flicker at the first 5 seconds of startup and go as dark as physically possible for it, which is REALLY dark. Fool around with opening and closing the lid, unplugging and repluggin in the power cord, and it flickers back to normal.

Also just random flickers on some rare occations.

Seems to be a (relatively) common problem with Dell laptops sold around fall/winter of 2003.

Can't garentee that's your problem, but most likely yours is similar to mine.

As for changing the resolution, generally you don't want to. Anything other than the native resolution on laptops usually doesn't look so great.

---

### Post by ukripper on 2007-05-17
> **foxy123 said:**
> The monitor on my NEC Versa M400 flickers every now and then It changes either the contrast or brightness (I cannot figure it out). I wonder if it is a software or hardware problem I bought this laptop second-hand and I have never had anything but Ubuntu on it. Any way to check what it is?


I had the same problem just sorted it now by reconfiguring xserver xorg and selecting my correct driver which is SIS instead of VESA and setting Horrizontal to 32-100 and vertical 55-110 hope that helps for u too. And checked in screen resolution which is giving me 85 hz now with other modes too.

---

