---
title: "Video Card compatibility in Laptops"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by jasonbrisbane on 2007-12-19
Hello

I am getting a new laptop and wish to use the 3d Capabilities of a laptop to get some of those cool programs, games, etc (quake3) etc for Linux.

I have not determined which laptop to buy, but want to restrict myself to a Sub $1000 laptop (base cost) and no more than $1300.

Which Laptop Video card is easiest to set up under Ubuntu 7.04 and 7.1 (I have the CD but haven't installed it yet)?

NVidia
ATI
Intel GMA
??

And which models of the brands are working?
(If I get a new laptop I dont want "that" model to be the only one that doesnt have 3d working as yet - I'd rather get a more expensive laptop with a confirmed 3d working Video card.

Models of Video card that I appear to be in common use here in Australia are:
Intel 950GMA
ATI Radeon Xpress 1150
Nvidia GeForce 8400M
Intel GMA X3100
Intel 945GM
NVIDIA GeForce 7150M


I have found little useful information in the forums (I dont have time to sort through hundreds of pages of forums details to find out that someone spend 18 hours and finally got a video card driver to work but no-one else has!)

Would someone be able to have ticks next to these - Easiest to hardest - fully supoorted (3d) to not supported in Ubuntu 7.10?

Or is there already an area that has this information (the off mubuntu sites listing 5 year old nvidia cards is not a suitable options - the 6800 is listed multiple times, suggesting that the page is incorrect.)


Thanks.

---

### Post by igknighted on 2007-12-19
All intel cards will be fully functional by default.  The 945/950 etc. are, however, probably the worst cards you list.  The Intel x3100 is better than the others, but not really that good.  Also it has fairly major bugs in its drivers when used with certain popular software (compiz-fusion, for example).

The nvidia cards tend to do very well.  I think th 8400m is probably the best card you list, and the 7150 is very close to the 7000m I have (it runs very well).  Both need you to install the nvidia drivers (ubuntu does this through the restricted driver manager nearly automatically so you really don't actually have to do anything...) to give ample 3d.  Mine required me at install to switch and use the very basic vesa driver, but after install and loading the nvidia proprietary driver it worked perfectly.

The Radeon Xpress is not a terrible card, but linux support is hit/miss.  There are several revisions of that card and you never really know which one you have until you try and install Ubuntu on it, and of the revisions, some work very well and others are a complete disaster.  So I would avoid them where possible, unless the rest of the laptop is such a good deal.

Whats wrong with a 6800?  Many people still use them... hell, I still use an FX5200 on one computer.  Just because something isn't brand new doesn't mean there aren't people who still want to know if it works on linux.  Welcome to a world where hardware only becomes obsolete when it actually physically dies.

---

### Post by bigmista on 2007-12-31
> **igknighted said:**
> All intel cards will be fully functional by default.  The 945/950 etc. are, however, probably the worst cards you list.  The Intel x3100 is better than the others, but not really that good.  Also it has fairly major bugs in its drivers when used with certain popular software (compiz-fusion, for example).

The nvidia cards tend to do very well.  I think th 8400m is probably the best card you list, and the 7150 is very close to the 7000m I have (it runs very well).  Both need you to install the nvidia drivers (ubuntu does this through the restricted driver manager nearly automatically so you really don't actually have to do anything...) to give ample 3d.  Mine required me at install to switch and use the very basic vesa driver, but after install and loading the nvidia proprietary driver it worked perfectly.

The Radeon Xpress is not a terrible card, but linux support is hit/miss.  There are several revisions of that card and you never really know which one you have until you try and install Ubuntu on it, and of the revisions, some work very well and others are a complete disaster.  So I would avoid them where possible, unless the rest of the laptop is such a good deal.

Whats wrong with a 6800?  Many people still use them... hell, I still use an FX5200 on one computer.  Just because something isn't brand new doesn't mean there aren't people who still want to know if it works on linux.  Welcome to a world where hardware only becomes obsolete when it actually physically dies.

Peachy. My Gateway has the Intel 950. Will it still work with Compiz & Beryl?

---

