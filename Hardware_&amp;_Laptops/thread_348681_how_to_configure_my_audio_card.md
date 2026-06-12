---
title: "how to configure my audio card"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by nene on 2007-01-29
hi boys I buyed a desktop pc, I immediatly install kubuntu. It recognize my audio card (chipset Via82xx) but this don't work, after many trial I gived up; and then I install a old  PCI audio 
card. This work very well, but if I restart the pc to use windows XP, when I return to linux, Kmix use as preferred audio card via82xx and not PCI card. I set preferred card but, every time  I use window xp kmix set as preferred chipset via82xx. How to set PCI card as preferred??
thank

---

### Post by hal10000 on 2007-01-29
you can blacklist the via driver to prevent it from being loaded at boot time.
Open the file [COLOR="Red"]/etc/modprobe.d/blacklist[/COLOR] (with root permissions) and add the following line at the end of the file:
```

blacklist snd-via82xx

```
Then reboot to check wether it works.
Hope this solves your problem.

---

