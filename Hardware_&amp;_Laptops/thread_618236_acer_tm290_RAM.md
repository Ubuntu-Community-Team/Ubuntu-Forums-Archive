---
title: "acer tm290 RAM"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by Dr. Cox on 2007-11-20
hi there,

i own an old acer tm290 laptop with an intel chipset, intel graphics and 512 megs of ram.

as i'd like to keep using i'd like to add some ram. 

1) does anyone know, what kind of ram that computer needs?
2) what's the max amount i can add?
3) once i've build in the new ram, do i need to change anything in my ubuntu settings?

thanks for the help,

cheers

---

### Post by al_sharpe on 2007-11-20
Hello Dr Cox:

I have the same computer and plan on upgrading ram also.

The computer will support up to 2,  1Gig sticks (200-pin sodimms) of DDR-266 (PC-2100)
 but my machine from Acer had DDR-333 (PC-2700) with CL timing of 2.5

Thus I am going to install Kingston KVR333x64SC25/512 CR. these 1/2 gig ram chips
cost $35 apiece in Canada. 2 for $70 and will give 1 gig vs 512mb now, at a very reasonable price point.

No you do not have to change anything when you install new ram, the BIOS will detect it, and
all will be good. The ram is under the centre of bottom of computer, just 2 screws.

command free -m shows I am using 473 of 487 available megs 

I see no reason to put 2 gig in this old a machine and am hoping doubling the ram will make
things speedier and allow it to assign more ram to video.

Out of curiosity are you able to use xserver-xorg-video-intel, my system is unstable with it and I have to use generic VESA for graphics card. Quite frustrating really, although everything else works perfectly.

Best of luck :)
Al

---

### Post by Dr. Cox on 2007-11-21
> **al_sharpe said:**
> 

I see no reason to put 2 gig in this old a machine and am hoping doubling the ram will make
things speedier and allow it to assign more ram to video.


i was hoping to put 2gig of ram in.  don't you think would make a much bigger difference than just doubling it?

> **al_sharpe said:**
> 
Out of curiosity are you able to use xserver-xorg-video-intel, my system is unstable with it and I have to use generic VESA for graphics card. Quite frustrating really, although everything else works perfectly.

Best of luck :)
Al

no, never tried.  my 1400x1050 resolution is not supported but apart from that everything seemed to work fine.  what advantage is does xserver-xorg-video-intel have? i've just been using whatever worked out of the box?
am i being daft?

---

