---
title: "ATI 8.42.3 driver issues"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by voided3 on 2007-10-24
Hello, I just setup the new 8.42.3 drivers on my computer with an x1300 pro in it. A few issues I have noted:

1) Brightness for most games is not adjusted from switching between the desktop and the game unlike before so some are very dark; for example, quake 3's brightness control doesn't affect anything w/ this driver in place.

2) I can't take a screen shot of it, but I get  a few blotchy lines that show up after a little while on my desktop. Logging out makes them go away, but they eventually return again. Also, I tried to take a screen shot of it and it wouldn't show up so I can't really show you exactly what it looks like (it essentially looks like a bunch of dead LCD pixels in the lower right hand corner).

Any ideas on how to fix this or should I wait for 8.43? Thanks!

---

### Post by drachenstern on 2007-10-24
Did you enable the xserver-xgl module (think synaptic)?

Once I did that and then enabled Compiz, that little problem disappeared.

Oh, BTW - you're not crazy, it is a problem

---

### Post by mcdull2k on 2007-10-24
> **drachenstern said:**
> Did you enable the xserver-xgl module (think synaptic)?

Once I did that and then enabled Compiz, that little problem disappeared.

Oh, BTW - you're not crazy, it is a problem

is xserver-xgl still needed for compiz? I hope not.

---

### Post by voided3 on 2007-10-24
I have all desktop effects disabled though... hmm. I'll try adding it anyway though.

---

### Post by ubuntu dave on 2007-10-24
The 8.42.3 drivers have AIGLX support (for the first time) - so xserver-xgl ***is not needed***.

Problem 2 sounds like a watermark issue - I don't personally know a way around it though I did get the problem on the last driver but not this (8.42) driver.

---

### Post by subvertigo on 2007-10-24
Anyone knows if this new driver support Suspend to RAM and Hibernation with kernel 2.6.22 (Gutsy default) ?

---

### Post by Canalzo on 2007-10-24
> Anyone knows if this new driver support Suspend to RAM and Hibernation with kernel 2.6.22 (Gutsy default) ?

Nope, it doesn't work :( still buggy with SLUB.

---

### Post by subvertigo on 2007-10-24
> **Canalzo said:**
> Nope, it doesn't work :( still buggy with SLUB.

Bah.... are you sure?! 

Tell me how a user owning a lapton with ATI could use Gutsy.... This is madness! Sparta!!!!

---

### Post by Canalzo on 2007-10-24
I just tried with the new driver and it didn't work.  I switched to vesa...it worked.  Now compiling a custom kernel with SLAB instead of SLUB to check if it works....

---

### Post by Neo4 on 2007-10-25
the normal issues with compiz where...
and some pixel problems like around the mouse icon scratches, and sometimes on the desktop

---

### Post by drachenstern on 2007-10-25
that was why I suggested putting xserver-xgl, it made the scratches disappear.

if anyone has a better solution, I'm all ears

---

### Post by voided3 on 2007-10-26
I installed xserver-xgl and now desktop effects work fine, and I haven't seen the watermarks yet. Scrolling is slow though, as is cursor movement while something is loading. We'll see how it goes.

---

