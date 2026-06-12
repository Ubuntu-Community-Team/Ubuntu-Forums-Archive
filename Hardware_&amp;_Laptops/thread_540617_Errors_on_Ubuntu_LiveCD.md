---
title: "Errors on Ubuntu LiveCD"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by LooieENG on 2007-09-01
[http://208.100.59.74/ubuntu](http://208.100.59.74/ubuntu)

Also, it takes like 20-30 minutes for the desktop to fully load. The mouse isn't lagging or anything, and it doesn't freeze, just programs won't open.

Check the pics in that folder.

PC specs:

ASRock P4i65G
Intel Celeron D 2.8Ghz (overclocked to 3.5Ghz (And tried without it overclocked))
255MB PC3200 Micron RAM
1MB onboard VRAM (tried increasing to 32MB and still sluggish)
Seagate 80GB 7200RPM
NEC 3500AG (I *think* this is the problem)

I also tried the other installer (the CLI one and it froze at the programs bit before the bootloader setup), and when I booted it up, there was no GUI, just like a giant terminal, aswell as trying 2 CD's a friend burnt (he has Ubuntu working perfectly)...

Any solution? I'm getting another 512MB RAM soon, but I'd like it get it installed asap.

Thanks.

---

### Post by LooieENG on 2007-09-02
Maybe I could use PCLinuxOS to make a SWAP partition it can use?

---

### Post by LooieENG on 2007-09-02
Bump

---

### Post by merlinus on 2007-09-02
You do not have enough RAM to install from the live cd.

And it sound as though the installation went fine with the Alternate cd, but now you are having video card problems.

Try this at the command line after booting:

sudo dpkg-reconfigure -phigh xsever-xorg

Then select vesa as your video driver and use the space bar to select the resolution.

Then reboot.

-merlin

---

### Post by LooieENG on 2007-09-02
The 1GB SWAP partition did the trick. It's installing now.

---

