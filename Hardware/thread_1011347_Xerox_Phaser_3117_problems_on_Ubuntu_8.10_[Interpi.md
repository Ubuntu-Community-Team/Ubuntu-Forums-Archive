---
title: "Xerox Phaser 3117 problems on Ubuntu 8.10 [Interpid Ibex]"
date: 2008-12-14
forum: Hardware
---

### Post by feriender on 2008-12-14
I experienced some problems with my Xerox Phaser 3117 after upgrading Ibex. Printing wasn't work at all, however worked fine on 8.04.
Printer was autodetected and installed by Ibex automatically. 
Error messages:
"Can't create temporary file", when trying a test-page printing
Solution:
#1 It is caused by a permission conflict of cups and /tmp, because cups is not able to write there due 755 permission is set after upgrading Ibex.
Change the permission to 777 by typing from console

```

sudo chmod 777 /tmp

```

#2 Use the Samsung ML-1710 driver for Phaser 3117. It can be set by typing 

system-config-printer

than select the Phaser 3117, and change "make and model" to samsung ml-1710, foomatic/gdi

---

