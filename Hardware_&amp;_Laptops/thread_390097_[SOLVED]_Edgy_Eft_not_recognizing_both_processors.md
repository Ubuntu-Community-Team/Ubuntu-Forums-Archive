---
title: "[SOLVED] Edgy Eft not recognizing both processors"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by magikid on 2007-03-21
This morning I installed Edgy Eft onto my laptop and for some reason it will only recognize one processor even though I've got an Intel Core Duo.  I've been scouring the forums looking for help and I think it might be my kernel but I'm not sure.  When I run uname -a, I get this:```
Linux chrisjones-laptop 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
```  Is that correct for a dual core processor?  I though I might need to switch to the 686-smp kernel so I ran apt-get and installed it and restarted.  There wasn't a new kernel in the list though, so I just booted with the normal kernel.  Any help would be greatly appreciated.

---

### Post by futz on 2007-03-21
> **magikid said:**
> This morning I installed Edgy Eft onto my laptop and for some reason it will only recognize one processor even though I've got an Intel Core Duo.  I've been scouring the forums looking for help and I think it might be my kernel but I'm not sure.  When I run uname -a, I get this:```
Linux chrisjones-laptop 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
```  Is that correct for a dual core processor?  I though I might need to switch to the 686-smp kernel so I ran apt-get and installed it and restarted.  There wasn't a new kernel in the list though, so I just booted with the normal kernel.  Any help would be greatly appreciated.
Use the generic kernel. The generic automatically senses multiple cores and uses SMP. When you do a standard install it puts both the standard kernel and the generic one. Just change your grub menu.lst to point to the generic to boot from it instead of the standard one.

To confirm that you are actually using both cores, start System Monitor (System/Administration/System Monitor) and hit the Resources tab. If there are two CPUs listed, you are in SMP mode.

---

### Post by magikid on 2007-03-21
Thanks.  That did it.

---

