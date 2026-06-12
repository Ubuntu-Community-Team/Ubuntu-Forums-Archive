---
title: "How do I get my graphics card to work with linux kernel 3.2.0-30?"
date: 2012-09-09
forum: Hardware
---

### Post by afruitpie on 2012-09-09
Ubuntu 12.04.1 
Sony Vaio VPCSB11FX 
AMD Radeon HD 6740M 

The open source drivers from xorg don't work with my graphics card, and neither do the fglrx drivers from Jockey. AMD Catalyst worked a few weeks ago on linux kernel 3.2.0-29, but doesn't work with 3.2.0-29. It won't load the desktop, and I have to use my computer through the terminal.

How do I get my graphics card to work?

---

### Post by QIII on 2012-09-09
Did you do

```
sudo aticonfig --initial
```

after installing the driver?  If not, you can still do it from the console if you can't immediately boot to your DE.

For some reason entirely beyond my comprehension, many users have problems when installing the AMD/ATI driver via "Additional Drivers" or synaptic.  

You might try looking at the section "Using the Ubuntu repository, alternate command line method" in the ATI driver wiki in my signature.

Please let me know if that works.

---

