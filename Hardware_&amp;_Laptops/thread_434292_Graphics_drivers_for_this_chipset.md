---
title: "Graphics drivers for this chipset?"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by ZZT16 on 2007-05-05
Hey. Are there any existing drivers for this chipset:
Mobile Intel 915GM/GMS 910GM Express Chipset
If not, is it possible to use graphics drivers from Windows under Linux?

---

### Post by Fitzy_oz on 2007-05-05
> **ZZT16 said:**
> Hey. Are there any existing drivers for this chipset:
Mobile Intel 915GM/GMS 910GM Express Chipset
If not, is it possible to use graphics drivers from Windows under Linux?

Intel's drivers are open source therefore they are included (or should be) in Ubuntu...

---

### Post by ZZT16 on 2007-05-05
Thanks for replying.

It's possible, but Starcraft, a game which runs perfectly on a 400mhz machine, runs really slowly on my 1.9Ghz Pentium M machine :(

---

### Post by Fitzy_oz on 2007-05-05
> **ZZT16 said:**
> Thanks for replying.

It's possible, but Starcraft, a game which runs perfectly on a 400mhz machine, runs really slowly on my 1.9Ghz Pentium M machine :(

Thats not necessarily you're graphics card - Check you're wine settings - Turn things like pixel shader off and run wine from the command line with the WINEDEBUG="-all" wine "you're starcraft path".  THis will suppress all of the errors wine generates and generally gives a healthy speed boost

---

### Post by ZZT16 on 2007-05-05
Didn't help much... oh well ;( No other suggestions?

---

### Post by Fitzy_oz on 2007-05-06
> **ZZT16 said:**
> Didn't help much... oh well ;( No other suggestions?

type glxinfo in a terminal and paste the output if that okay.

---

