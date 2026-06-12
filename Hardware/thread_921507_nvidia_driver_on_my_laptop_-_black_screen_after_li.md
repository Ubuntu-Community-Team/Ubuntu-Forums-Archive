---
title: "nvidia driver on my laptop - black screen after lid close&amp;open"
date: 2008-09-16
forum: Hardware
---

### Post by lokster on 2008-09-16
The title pretty much says it...
I have an MSI M670 Notebook with GeForce Go 6100 video card.
I use the latest nvidia driver - 177.
Everything works fine, except that when I close the lid and then open it, the screen does not turn on. Its _almost_ completely black. "Almost", because when I view the display from specific angle, I can see the opened windows, and even login/logout etc. As if only the backlight of the display is off.
Switching terminals or pressing ctrl+alt+backspace does not solve the problem.

---

### Post by in-dust-rial on 2008-09-16
as long as it did work with the free drivers, i would guess this is not ubuntu related.

you should give it a try.

good luck.

(did you look into nvidiea forums?)

> so i mean shortly change ....xorg.conf ...device...driovers ="nv" ... try it ... switch back 

---

### Post by lokster on 2008-10-01
> **in-dust-rial said:**
> as long as it did work with the free drivers, i would guess this is not ubuntu related.

you should give it a try.

good luck.

(did you look into nvidiea forums?)

No, I don't want to use the free nv driver - it is a lot slower.

---

### Post by xPirate on 2008-11-04
I have the same problem. When my display turn off after screensaver and i go back to my laptop and move the mouse, it's come to "black screen" like after lid close&open. I'm also with MSI m670

---

### Post by apocalyp_sys on 2008-12-18
This problem doesn't seem to be related with nvidia drivers, i've tried switching from 'nvidia' to 'nv' and it didn't help.

Looks like an X or kernel issue to me. There was no such problem with 8.04 distro, 8.10 does have it.

gnome-power-manager captures lid open-close events (shows em on the power history diagram), but there is nothing in acpi logs since uprgading. Are there any other logs that might help to track the problem? I also can't find gnome-power-manager scripts for closing/opening laptop lid, where are they?

I've tried to find some X controls to manage backlight, but looks like there is no such thing for MSI laptops.

P.S. Runnung ubuntu 8.10 on MSI M670 (nvidia 6100)

---

### Post by gnaag on 2009-01-07
On my MSI M670 I encounter exactly the same behaviour. I am using the latest nvidia 177.80 driver through ubuntu driver service. Earlier on hardy, there were other problems with suspend and lid close, but now the main problem is this one.

---

### Post by Switch_Zero on 2010-01-13
*bump*
 
Any updates on this? Anybody testing this with the newer 9.xx releases?
Because,...I'll be installing the latest Ubuntu release sometime this week and since I have the exact same laptop would like to know if this has been resolved or not so I can keep it in mind and adjust my settings right after installing the OS.
 
(and since I'm a newb with Ubuntu... :P )

---

### Post by Snaer on 2010-01-13
I have the same problem too, but I have 9.10 karmic koala on an acer laptop with an ATI card. There is also a similar(or perhaps the same) problem when I try to continue after hibernate and suspend.:(

---

### Post by BigBananaMan on 2010-01-19
I'm having the same problem.  I look through the crack when I close the lid, the backlight will turn off for less than a second and come back on.  Then a few seconds later it will turn off and never come on again.  Magic system request K does not even have any visible effect.  REISUB or a hard restart brings it back to normal.

So far my workaround is to close the lid on a book or pen and hope to god nothing bumps it and breaks the screen.  It would be nice if there were an option to have no action when the laptop lid closes so that the screen just stays on.

Ubuntu 9.10
Dell Lattitude C840
Proprietary drivers not in use

Edit:  I tried typing sudo vbetools dpms on in a terminal before closing the lid and then hitting enter then blind typing my password when I want to open it.  Turning the back light back on is clearly not the answer as it split the screen in half horizontally.  The bottom half is where the whole screen was pushed down to and the top half was a phantom screen that could be used to interact with the real screen on the bottom.  When I click where the applications/places/system tabs at the top would be, I see them open on the lower half of the screen.  Couldn't interact with things on the lower half by clicking them, I had to guess where they would be on the upper screen.  Also had to shut down CLI since the power button was hidden off screen.  Oddly enough the terminal opened in the upper screen and worked as normal.

---

### Post by MindZEye on 2010-05-09
Weirdly I seem to be getting this issue with 10.04 and with an Intel chipset.

---

