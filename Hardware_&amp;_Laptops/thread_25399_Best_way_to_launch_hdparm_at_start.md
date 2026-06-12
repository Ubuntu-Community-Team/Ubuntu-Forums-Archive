---
title: "Best way to launch hdparm at start"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by ploum on 2005-04-10
Hello,

I want to enable DMA and 32bit at start for my old harddisk.
A way is to write a tiny bash script and to put it in /etc/init.d/

But is there another way to do this in Ubuntu ? Is there simply a config file ?

---

### Post by boo on 2005-04-10
[QUOTE=ploum]Hello,

I want to enable DMA and 32bit at start for my old harddisk.
A way is to write a tiny bash script and to put it in /etc/init.d/

But is there another way to do this in Ubuntu ? Is there simply a config file ?[/QUOTE]
there allready is a hdparm init script in rcS.d, can be configured with /etc/hdparm.conf

---

### Post by ploum on 2005-04-10
thx a lot :-)

---

### Post by darkaudit on 2005-04-10
As another hint here, you may want to move it to a later spot in the boot sequence. The S07 slot rund before modules are loaded, so it might claim your  drives don't exist. I moved mine to S28 instead. Everything sets up fine now.

---

