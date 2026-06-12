---
title: "Radeon x200M - new user"
date: 2009-11-20
forum: Hardware
---

### Post by The Beej on 2009-11-20
New to Ubuntu (9.10-64bit) and am trying to setup my Gateway Laptop MX7118.  Having trouble getting my graphics to work, namely, whenever a window pops up and I move a window around, I get ghosting on the desktop.  I'm really looking for a nice step-by-step guide on how to get it to play nice and look all pretty because I'm not familiar at all with the terminal other than the sudo command.  Laptop is using Radeon Xpress 200M graphics.

I've been searching for days for guides and tutorials, but I only think I've made my freshly installed copy rife with extraneous apps and extras that aren't needed.  The only program I've managed to properly install is QuickSynergy.  I'm looking to get it to run at the login screen but I have not found a complete and practical step-by-step guide on how to do it.

Could those who have the knowledge to help please assist? Thanks!

---

### Post by Richardarkless on 2009-11-21
Ive had many problems with that graphics card but the community have really tried their best to bring compatibility to it by default and its still not perfect

try going to system, administration and hardware drivers and check if there is a proprietary driver and install it and restart

if there isnt a driver or there is but it doesnt work then you can try enabling vsync which reduces your fps but illiminates most of the ghosting left over when you move a window, etc

under ubuntu software center which is under applications and look for

"advanced desktop effects settings (CCSM)"

and look also for "simple compizconfig settings manager"

and install each, once you have done that go to system, preferences and compizconfig settings manager then go to general options up the top, display settings and tick sync to vblank and see if that improves things and also changing the refresh rate to the refresh rate to what it is under adminstration and display

I havent tried this with my old pc because it is my families pc and they are "used" to windows ](*,) 

but I have tried it with other graphics cards and this fixes the ghosting problem alot

---

### Post by The Beej on 2009-11-21
Thanks.  Tried it, but to no avail.  It actually created more ghosting and made the workspace cube glitchy (workspaces disappear after moving the cube too much, not fast, just too much).

Still seeking a guide or solution for the drivers.  I'm wondering if it may just be the outdated card itself...meaning it might be time to make it a Windows only machine.

---

