---
title: "Nvidia Riva TNT 16 MB - Slow"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by Sniper PT on 2005-07-24
I have a Nvidia Riva TNT 16 MB and i have install nvidia-glx, nvidia-settings....

But there is a problem, when i use ubuntu and when i'm using windows, etc. is too slow, sometimes i think i have a 386 PC....  :-? 

My drivers version is 1.0-7174..

What i must do to solve that?

Thanks!

---

### Post by evilghost on 2005-07-24
Specifically, what application are you using when it's slow?  Note, your card is very old, and it's probably time for an upgrade **depending** on what you use it for.

---

### Post by Sniper PT on 2005-07-25
I use simple programs... like firefox... and when i scroll to see some page that have delays.... or simple changing in tabs...

---

### Post by az on 2005-07-25
I would guess that you have less than 128 megs of system memory?

I do not think that your graphics card has much to do with how fast windows are rendered.  A video card will help out for Games and other applications that need hardware acceleration (like 3d stuff) and none of that is needed for a basic desktop.

How fast is your CPU and how muchmemory do you have?

---

### Post by evilghost on 2005-07-25
You may want to try using the "nv" driver instead of the "nvidia" driver, if you are using "nvidia".

There are rumors of 7667 and earlier drivers producing slow 2D peformance.  While I've not experienced it, it appears certain chipsets are affected.

Check it out here for more information:
[http://www.nvnews.net/vbulletin/showthread.php?t=53712](http://www.nvnews.net/vbulletin/showthread.php?t=53712)

---

### Post by Sniper PT on 2005-07-26
I have a PIII 450 Mhz with 128 MB of RAM!

But i just need change in xorg.conf file "nvidia" to "nv"?

Thanks!

---

