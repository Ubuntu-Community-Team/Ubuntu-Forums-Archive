---
title: "catalyst 11.4 how to switch GPU?"
date: 2011-05-07
forum: Hardware
---

### Post by puchaty on 2011-05-07
Hi.

Im using HP DM3-1105ew with 2 GPU units.

ATI 3200 and ATI 4330. Both of them are controlled by PowerXpress.

How to switch GPU?

I have installed 11.4 catalyst. It works fine for 3200 and only 3200.

I can't find switch option. 

In Windows OS switching is possible in ati catalyst suite. In Linux ati catalyst suite i cant find anything about powerXpress.

---

### Post by puchaty on 2011-05-07
looks like this version supports switching intel/ati. not ati/ati


I hate u ATI.

---

### Post by lyka on 2011-05-30
i have a similar problem: AMD 4200HD and AMD 5470HD...

did you find the solution?

---

### Post by puchaty on 2011-06-05
nope, no solution for ati/ati

---

### Post by lyka on 2011-06-05
with fglrx
PowerXpress options:
  --px-list-active-gpu
  --pxl **List current activated GPU**
  --px-dgpu **Activate discrete GPU (High-Performance mode), must re-start X to take effect**
  --px-igpu **Activate integrated GPU (Power-Saving mode), must re-start X to take effect**

> sudo aticonfig --px-dgpu
:)

---

### Post by puchaty on 2011-06-06
that works but i have black screen on power-saving mode.



Its really hot in europe today so i dont want to use high power card (it heats up my laptop really bad).

Any solution?

---

### Post by Yellow Pasque on 2011-06-06
I'd recommend upgrading to 11.5 (or waiting for 11.6 to come). They're working on it (supposedly).

> I hate u ATI.
You're the one who bought a hybrid graphics system for Linux use when there are warnings all over the interweb not to do that..

---

### Post by puchaty on 2011-06-06
> **Temüjin said:**
> I'd recommend upgrading to 11.5 (or waiting for 11.6 to come). They're working on it (supposedly).


You're the one who bought a hybrid graphics system for Linux use when there are warnings all over the interweb not to do that..
im already at 11.5 :)

I am the one who bought laptop with windows but when i had free time i tried ubuntu (10.10) now i think ubuntu/linux is awesome and I want to switch to the ubuntu. :) And Windows bores me so much.

And I can't sell my laptop now [leasing..] :)

Anyway will wait for next catalyst. Im glad that they included powerxpress support anyway ;-).

The main problem is that I can't see what is going on. When i have some kernel problems i just look at the screen or dmesg and i know what is going on.

Are there any logs for X server?

---

### Post by Yellow Pasque on 2011-06-06
> Are there any logs for X server?
/var/log/Xorg.0.log
~/.xsession-errors

---

### Post by puchaty on 2011-06-07
log looks clear. I think HP changed something.

at windows i can use HDMI when im at high performance mode only.

aticonfig says Im on high performance and still no hdmi output.

When I used vga switcheroo hdmi worked.


Well I just have to wait 5 months till my leasing ends and buy another laptop ;P.

---

