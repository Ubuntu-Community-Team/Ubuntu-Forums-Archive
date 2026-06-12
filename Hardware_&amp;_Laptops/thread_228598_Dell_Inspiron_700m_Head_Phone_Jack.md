---
title: "Dell Inspiron 700m Head Phone Jack"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by Foot33333 on 2006-08-03
Hello, I am relativley new to linux and so far I have been very pleased with ubuntu.  I have gotten almost everything working on my laptop except for my current problem.  The sound on my Dell Inspiron 700m works just fine through the speakers but when i plug in my head phones the volume is always on its maximum level and cannot be changed.  when i run lspci it i get the following information for my sound card:

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Dell: Unknown device 018d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>


Does any one have any suggestions?

---

### Post by jstueve on 2006-08-03
the headphone volume isn't linked to the sound volume on the toolbar, you have to change it individually (or at least I do) using the Open Sound Controls after right-clicking the volume icon on the toolbar.

---

### Post by Foot33333 on 2006-08-04
easy solution thanks a lot!

---

### Post by TopRamen on 2006-08-18
Hey guys, is it possible to link headphone and master volume settings so that when I adjust the volume via the built in keyboard function keys, it will modify both? I hate having to open the sound control whenever I have headphones or external speakers plugged into the headphone jack just in order to change the volume. It's starting to become an annoyance. Any help would be GREATLY appreciated here. Thanks guys!

---

### Post by crimsun on 2006-08-18
> **TopRamen said:**
> Hey guys, is it possible to link headphone and master volume settings so that when I adjust the volume via the built in keyboard function keys, it will modify both?

No, but it is possible to use an ac97 quirk to only adjust the headphone control element. I've applied countless such patches to our linux-source.

Please e-mail me (you'll find the contact info on Launchpad) the output from ``lspci -nv'' and note clearly in the subject "[UBUNTU lspci -nv for possible hp_only quirk]".

Thanks.

---

### Post by TopRamen on 2006-08-18
> **crimsun said:**
> No, but it is possible to use an ac97 quirk to only adjust the headphone control element. I've applied countless such patches to our linux-source.

Please e-mail me (you'll find the contact info on Launchpad) the output from ``lspci -nv'' and note clearly in the subject "[UBUNTU lspci -nv for possible hp_only quirk]".

Thanks.

Not sure if I am looking in the right place or not. I haven't looked at Launchpad before. I went to launchpad.net and searched for lspci and had no results. Is there a direct link you could provide me with? Thanks in advance!

---

### Post by TopRamen on 2006-08-19
So guys, any idea on where to start fixing this problem? It's really a big annoyance more than anything but there's gotta be a way to fix it. Thanks in advance!

---

