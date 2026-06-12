---
title: "Intel HD Audio"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by gunavara on 2007-01-19
Hi everybody I've seen lots of people here sharing that they have the same problem as I do. The sound HD Audio doesn't work. Well the strange thing in my case is:  when i boot my ubuntu 6.10 the sound works only on "R" headphone. If i get the jack 1/2 out of the port and move it a bit the both headphones works fine. Ok so far so good, but when I volume up or down or whatever sound manipulation i make, the sound just disappear until the next reboot. It's really a nervous problem.

My motherboard is: "Asus P5LD2 SE".    
Here is my lspci -v:  
-----------------------------------
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller 
(rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 817f
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at dacf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
------------------------------------

If anyone solved this problem, please share it with us. :)

---

### Post by fanta on 2007-01-19
check out this thread: [http://www.ubuntuforums.org/showthread.php?t=231032]("http://www.ubuntuforums.org/showthread.php?t=231032")

Try the fix in post #6 by mcmc

---

