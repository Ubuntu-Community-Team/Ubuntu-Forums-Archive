---
title: "Desktop effects not working."
date: 2008-11-12
forum: General Help
---

### Post by Th1eF` on 2008-11-12
I have upgrade to Ubuntu 8.10 (amd64). And when going to activate desktop effects normal or extra i get the following error: "The Composite extension is not available."

In hardware devices i get that: This driver is activated and currently in use.

I use Ati Radeon X1300.

any ideas how to solve this problem?

---

### Post by eternalnewbee on 2008-11-12
Press **ALT-F2**, and enter ```
compiz --replace
```
Hope this helps.

---

### Post by Th1eF` on 2008-11-12
> **eternalnewbee said:**
> Press **ALT-F2**, and enter ```
compiz --replace
```
Hope this helps.

I have try it but nothing, i still got the same problem.

---

### Post by eternalnewbee on 2008-11-12
OK. This may sound stupid, but reboot the sytem and try again.

---

### Post by ellalan on 2008-11-12
Have you installed simple ccsm in synaptics, if not enable it then you can try using custom visual effect.HTH.

---

### Post by Th1eF` on 2008-11-13
reboot but again the same problem.

i have install the simple ccsm but again i get the same problem. :(

---

### Post by Th1eF` on 2008-11-13
when i run compiz-check i get:

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV515 [Radeon X1300]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by Th1eF` on 2008-11-13
Thanks for your help. 
I have solve the problem.

i have just removed from xorg.conf the following lines:

Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

