---
title: "How Much RAM?"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by mikes on 2005-03-24
How much RAM will I need to run ubuntu efficiantly? I have 96MB of RAM right now. Will that be enough?

---

### Post by Levander on 2005-03-24
[QUOTE=mikes]How much RAM will I need to run ubuntu efficiantly? I have 96MB of RAM right now. Will that be enough?[/QUOTE]


Probably not if you want to run X with Firefox, etc like a normal desktop.  You're probably going to need 512 MB. 

The bad news is that if your motherboard supports some configuration where 96MB is valid, the motherboard isn't going to support 512 MB of RAM.  Which means you going to have to at least upgrade your motherboard, CPU, as well as RAM.

---

### Post by armitage on 2005-03-25
while more ram (like 512) would be nice, im currently using ubuntu on a bunch of machines with only 128MB, and compensated for by 512 megs of swap. I regularly use gnome, firefox, open office,the gimp, although not at the same time.
 
its not going to run as fast as it could, but it wont be so slow as to be useless.

---

### Post by az on 2005-03-25
Yes, it is enough.

Do not expect things to be speedy, but it is enough.

You can think about running less hungry apps like icewm as a window manager (instead of the whole gnome desktop) and xfe as a file manager (if all you want to do is see and play around with your files)

Installing icewm (menu, too, if it not already brought in) and xfe from universe should be all you need to do.  Change your ligin behaviour to start the icewm session instead of the gnome session and you are off to the races!

Fluxbox and XFCE (ew!) are other alternatives.  XFCE is said to be faster than gnome.  That has not been my experience.  Your mileage may vary, of course.  Try it.

---

### Post by Levander on 2005-03-25
Well, on my box, Firefox right now is taking up 143MB of memory, by itself.  I am running GNOME, I don't know how running it under another window manager would lower Firefox's memory consumption. But I would be surprise if it would lower it the 50 MB he would need to be able to run Firefox by itself without swapping.  And, firefox only, without X (somehow), without a couple of terminals open, etc.

Is true that it would run using swap, but I occasionally run out of physical RAM when I'm running a couple of servers I don't always run and start swapping.  I pretty much notice the second it starts swapping, and have to stop what I'm doing cause it's just to annoying waiting for things to swap out.

Armitage, maybe you make a habit of only running one application at a time.  So, you only wait for the app to start-up using the swap space.  Then, after it's started, that one app is already in memory so there's not as much swapping when you stay inside the same application? I don't think that's a typical user pattern if that is what you're doing.

But, if you're not looking for a desktop, but for a server, like to run apache or mysql, 96MB would be plenty.

---

### Post by mercurus on 2005-03-26
Everything will run, but not speedily.

I have a Duron 700, GeForce 2MX (32 MB Video RAM) and 374 MB of SD RAM and it is just able to keep up. It isn't slow, but sometimes has to think about some operations more than it should.

Give it a whirl, don't expect speedy response times, and look at a lighter window manager than GNOME\Metacity, as others have suggested.

---

### Post by az on 2005-03-26
Linux will use as much ram as it can.  That does not mean that you need to have a lot, just that it will make the most of what you give it.

On my 96 MB ram system, I consistently have about 1 meg free.  The rest is cached.  It will flush cache before it swaps.

---

### Post by slade_slater on 2005-04-09
I run XFCE with Hoary and it isn't unusual for my system to be utilizing 40-80 MB of RAM (of course the rest is in cache).  Right now I'm pushing 160 MB and I have FireFox open with 12 tabs, running a copy operation via ROX/SAMBA, and I have a couple of remote desktops open to other Machines.  So the base system doesn't require much--if you put a lightweight manager such as BlackBox, ICEWM, Rox, or XFCE (my fav), it will probably run pretty nice.  Gnome and KDE will probably run on it, but it won't be fast...

---

