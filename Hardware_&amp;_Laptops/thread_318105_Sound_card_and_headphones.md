---
title: "Sound card and headphones"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by cimnik on 2006-12-13
I have a HP Pavilion dv6000 and I have installed Ubuntu 6.10 on it. Every piece of hardware works properly in linux with little work.

However the sound card is the only piece of hardware that must have not installed properly. Sound works, just only through the integrated speakers. If I plug my headphones in, it just keeps on playing through the speakers and ignores my headphones. There must be some kind of software switch that the linux drivers aren't picking up.

I had the same problem in Windows Vista on a fresh install, but that was quickly resolved by doing a quick driver update. (I can't recall what drivers it installed), but I no longer have windows on my laptop and I don't want to dual boot just for sound. ](*,) 

Has anyone else experienced similar problems? Or have any way to fix this?

Thanks in advance.

---

### Post by cimnik on 2006-12-13
Right, forgot. lspci tells me that this is my sound card:
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable
```

---

### Post by cimnik on 2006-12-13
Okay. it seems that, from my research on the internet, that I have to update alsa. ubuntu installs 1.0.11 alsa stuff, and apperantly its been fixed in the newer releases. I can't find a package to install alsa 1.0.14 (or .13) stuff, and so I tried to compile it myself only to find my computer failing to boot ubuntu (sticks at 3%). I can't find coherent instructions to install it

---

### Post by Brian_X7 on 2006-12-14
Where'd you get the updated alsa?  I have the same problem with my Sony Vaio and was able to compile and install alsa, but the problem hasn't gone away yet.

Brian

---

### Post by olavjunior on 2007-02-14
I updated to the latest alsa as described in an article. Didn't help at all!

And I'm still kind of new to the whole linux thing. Heard someone updated the kernel...-how do you do that?
Anyone found a smart solution? I'm using my lapp for mainly multimedia, so I'm in need of a working jack!

Help is appreciated :)

I have an hp dv2130

---

### Post by isenalim on 2007-02-17
Same problem here.
Vaio FE41M, no output form headphones. Everything silent when plugged in. No volume bar or headphones option on gnome-volume-manager.

Help!

Thank you all.
Giuseppe

---

### Post by xavivars on 2007-03-04
I have the same problem. Anyone has the clue?

---

