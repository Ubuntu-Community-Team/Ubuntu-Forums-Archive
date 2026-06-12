---
title: "intel graphics problem (?)"
date: 2010-11-04
forum: Hardware
---

### Post by fedorjj on 2010-11-04
Hi!

I'm new to linux, and I've just installed xubuntu 10.10. 

My specs:

256MB DIMM DDR2
Intel Celeron M 1.5 Ghz
Mobile 915GM/GMS/910GML Express Graphics Controller

OS loads pretty fast (less than 1 minute), but everything on screen is running very slow. I see rendering lines, it sooo slow. 

glxgears show average 15 FPS

Is it supposed to be like that? My computer is too slow for xubuntu? Is there anything I can do about it?

Thanks for help.

---

### Post by mastablasta on 2010-11-04
probably this is due to poor graphics driver. add to that some low ram and you get a disaster.
 
have you tried regular Ubuntu or Lubuntu?

---

### Post by fedorjj on 2010-11-04
> **mastablasta said:**
> probably this is due to poor graphics driver. add to that some low ram and you get a disaster.
 
have you tried regular Ubuntu or Lubuntu?

Nope, I haven't. Is there anything I can do with driver? I followed instructions about troubleshooting intel card (ubuntu wiki) and everthing seems fine.

What OS do you recomend for me? I tryed puppy linux, it runs much faster, but it's not so user friendly.

---

### Post by shof2k on 2010-11-04
There is a bug with the intel driver in Maverick, so the default install only gives you a basic vesa complient display. You can manually activate the driver, but performance will still be poor.

---

### Post by mastablasta on 2010-11-05
> **shof2k said:**
> There is a bug with the intel driver in Maverick, so the default install only gives you a basic vesa complient display. You can manually activate the driver, but performance will still be poor.
 
Does this mean user will solve this issue if he uses 10.04? 
 
 
---
 
I use Ubuntu 10.04 (but i dont' have intel, i think it's S3 or something). also very old computer wiht 256 MB ram.
 
Lubuntu uses lower resource LXDE (should use about 80 MB ram while Ubuntu uses 120-130 mb ram). Another good one based on LXDE (but uses more ram) is Linux Mint LXDE. The creator/compiler of this one also made Peppermint OS which is realyl light ment for cloud computing if i understand correctly.
 
Another low resource linux is Slitaz. haven't tried it myself but looks nice. 
 
DSL was promissing worked extremely fast on my old notebook, however it's old system and development seems to have stalled.
 
there is also one based on enlightenment desktop (cant remember the name). really low resource and very nice system. however live is free while to install it you owuld have to pay (a little).

---

