---
title: "Graphics driver problems on TimelineX 5820TG lucid"
date: 2010-08-24
forum: Hardware
---

### Post by brickhead248 on 2010-08-24
Hey Ubuntu Forums, I'm starting a few threads for problems with my laptop's Ubuntu install.

I have an Acer Aspire TimelineX 5820TG-524G50MN dual-booting W7-64 and Ubuntu 10-4 64

A very strange thing happens when i try to open up a TTY (don't know the correct terminology, but you know what i mean... ctrl-alt-f2 etc.): everything freezes, i get this strange artefacting all over the screen (each occurrence of a certain colour is replaced by boxes of colours like pink/green/blue/red... pretty hard to describe and i can't take a screen shot). It's not just a frozen display, because when i blindly log on to the terminal and try a command like sudo reboot (without forgetting to type in my password!), nothing happens. Everything is returned to normal when i crtl-alt-f7 though.

This same kind of artefacting happens right when Ubuntu boots, (green rings around the loading dots), but this only lasts for a few seconds until it loads something which fixes the artefacting and everything is fine (until i try ctrl alt f2).

I'm running the normal drivers for the graphics cards because when i enabled the proprietary drivers (AMD/ATI proprietary FGLRX graphics driver) it actually nerfed my install and it wouldn't boot. I had to re-install.

Any ideas would be greatly appreciated! I don' really have the experience in this kind of thing to know where to start.

cheers!

---

### Post by brickhead248 on 2010-08-25
Another bit of information:

it turns out that I have two grapihcs card chips:  
    -> a low-powered intel chip
    -> an OP radeon HD 5650 1024mb.

what do?

---

### Post by SmSpillaz on 2010-08-25
Try booting with kernel flags "i915.modeset=0"

---

### Post by pemasu on 2010-08-26
[http://ubuntuforums.org/showthread.php?t=1495123&page=9](http://ubuntuforums.org/showthread.php?t=1495123&page=9)

that thread has solutions to 4820tg and (5820tg) BIOS/ACPI problem. The solutions and Trevinos hacked kernel works fine with 5820tg and lucid 64. There is another hacked kernel to offer if I remember right.You will get working battery status, you can switch ATI off to save battery and so on.

There is also ubuntu.it forum where Trevino has .sh scripts to switch between graphics. Use google and google translator with trevino and ubuntu.it

Ok. I did it: [http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266](http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266)
You need chrome browser to translate easily.

---

### Post by brickhead248 on 2010-08-30
> **SmSpillaz said:**
> Try booting with kernel flags "i915.modeset=0"
How would one go about doing that? thanks.

---

### Post by brickhead248 on 2010-08-30
> **pemasu said:**
> [http://ubuntuforums.org/showthread.php?t=1495123&page=9](http://ubuntuforums.org/showthread.php?t=1495123&page=9)

that thread has solutions to 4820tg and (5820tg) BIOS/ACPI problem. The solutions and Trevinos hacked kernel works fine with 5820tg and lucid 64. There is another hacked kernel to offer if I remember right.You will get working battery status, you can switch ATI off to save battery and so on.

There is also ubuntu.it forum where Trevino has .sh scripts to switch between graphics. Use google and google translator with trevino and ubuntu.it

Ok. I did it: [http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266](http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266)
You need chrome browser to translate easily.
I.
LOVE.
YOU.

Best bit of help I have ever been given on this forum.

---

### Post by pemasu on 2010-09-01
You are welcome. It took me some time to find right answers and there really isnt many threads in the world where 5820tg problems has been fixed.

If you someday find new tricks to 5820tg let me know.

---

### Post by pemasu on 2010-09-08
Bios 1.18 seems to fix acpi problem.

---

