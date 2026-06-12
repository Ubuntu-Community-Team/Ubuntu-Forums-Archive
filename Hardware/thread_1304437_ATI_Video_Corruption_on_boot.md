---
title: "ATI Video Corruption on boot"
date: 2009-10-29
forum: Hardware
---

### Post by frogotronic on 2009-10-29
Hello,

  Decided to try Karmic - didn't work out for me.  When I did I had to use the opensource ATI radeon drivers.  They were unstable on my machine.  Went back to Intrepid, BUT...

  Sometimes when I boot, I get a corrupted video display.  This is **before** the BIOS flash screen.  It looks like vertical red/blue/green lines about 1/4 inch (0.5 cm) apart accross most of the screen.  Curiously, there is a one inch border (2.54 cm) one third of the way in from the right hand side of the screen.

  I'm using a laptop (Mobility Radeon x2300).  The problem only occurs when I switch from booting in single monitor mode to booting into a dual monitor mode (external monitor plugged in via the VGA port, or on a docking station (also a VGA port)).

  I suspect the problem is that the ATI hardware buffer is not being flushed properly on shutdown.  This only happened after trying out Karmic and the open source drivers.

  Several posts talk about video corruption with ATI cards.  My question:  How do I "reset" the buffers to factor settings, or rather flush the buffer?

Thanks,
CH

---

### Post by MaxTesla on 2009-10-30
Ok dude


I had the some problem with the ATI Mobility Radeon X2300 HD


And I got lucky and a smart dude told me what to do


But this was for the 9.04 and I got the advice some time ago but I wrote it all down but I do not remember all details just that it worked and if it fails you might have to do a complete reinstall so save all your stuff and do this


After every line press enter


[SIZE=3]Applications > Accesories > Terminal[/SIZE]


[SIZE=3]sudo apt-get install git-core[/SIZE]


[SIZE=3]sudo apt-get build-dep libdrm mesa[/SIZE]


[SIZE=3]git clone git://anongit.freedesktop.org/mesa/mesa[/SIZE]


[SIZE=3]cd mesa[/SIZE]


[SIZE=3]git checkout -b radeon-rewrite origin/radeon-rewrite[/SIZE]


[SIZE=3]./autogen.sh --prefix=/usr (Not needed)[/SIZE]


[SIZE=3]gedit configs/linux-dri[/SIZE]


[SIZE=3]Remove i810 i915 i965 mach64 mga r128 r200 s3v \ savage sis tdfx trident unichrome ffb swrast only r300 and radeon should stay take out the slash too only ---> DRI_DIRS = r300 radeon <--- left[/SIZE]


[SIZE=3]sudo apt-get install python-qt3-gl python-qt4-gl freeglut3[/SIZE]


[SIZE=3]sudo apt-get install qt3-dev-tools qt4-dev-tools[/SIZE]


[SIZE=3]sudo apt-get install xorg-dev[/SIZE]


[SIZE=3]sudo apt-get install build-essential libstdc++5[/SIZE]


[SIZE=3]make linux-dri-x86[/SIZE]


[SIZE=3]sudo cp lib/lib* /usr/lib && sudo cp lib/*_dri.so /usr/lib/dri[/SIZE]




[SIZE=3]sudo mkdir /usr/local/lib/dri && sudo cp lib/*_dri.so /usr/local/lib/dri[/SIZE]


[SIZE=3]Restart computer[/SIZE]

---

### Post by frogotronic on 2009-10-30
Hi MaxTesla,

It's a board failure - getting a new MB from HP.

Thanks

---

### Post by MaxTesla on 2009-10-30
Ahh yes a new computer is of course a better solution.
 
 
If I may speak frankly the 2000 series for ATI/AMD are all crap indeed only the 4000 series are something and something quite good, the universally popular 4650/70 cards are very popular indeed.
 
 
And of course if you get a new computer you might as well get a stationary since laptops always mess everything up.
 
 
But either way if you want a cheap and stable and popular, and thereby highly worked around and patched and fixed card make sure you have the 4650 or 4670 cards since there are so extremely popular and well used.
 
 
If you go for nvidia then the 210 or 220 cards are the popular ones over there

---

### Post by frogotronic on 2009-10-31
> **MaxTesla said:**
> Ahh yes a new computer is of course a better solution.
 
 
If I may speak frankly the 2000 series for ATI/AMD are all crap indeed only the 4000 series are something and something quite good, the universally popular 4650/70 cards are very popular indeed.
 
 
And of course if you get a new computer you might as well get a stationary since laptops always mess everything up.
 
 
But either way if you want a cheap and stable and popular, and thereby highly worked around and patched and fixed card make sure you have the 4650 or 4670 cards since there are so extremely popular and well used.
 
 
If you go for nvidia then the 210 or 220 cards are the popular ones over there

I agree with you and you are completely correct about the 2000 series cards - they are total crap.  Unfortunately, this is a work machine and so its their call - which means HP will likely put the *same* motherboard & video card in the laptop.

Overall, the HP machines aren't too bad - the quality is pretty poor; but I think that's an across the board *made in China* quality issue.  The thing that bothered me the most was that the video card that HP put in the 6910p was dropped by ATI for the FGLRX support six months after the machine was released to market.

Really piss-poor support for a "current" card - and the radeon drivers are simply not developed for the R5xx series cards.

- CH

---

### Post by M20554443 on 2009-11-04
> But either way if you want a cheap and stable and popular, and thereby highly worked around and patched and fixed card make sure you have the 4650 or 4670 cards since there are so extremely popular and well used.

Karmic: fglrx is not working for me with a HIS HD 4670 (in an Optiplex 740 from Dell); radeonhd driver is working, but it's still without 3D support. Not the first time having trouble with ATI fglrx and this card (while the other PC with NVIDIA is going 3D right away) ...

---

