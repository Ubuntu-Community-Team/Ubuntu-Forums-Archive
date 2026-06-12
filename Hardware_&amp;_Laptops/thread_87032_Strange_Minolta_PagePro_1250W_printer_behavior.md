---
title: "Strange Minolta PagePro 1250W printer behavior"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by muchio on 2005-11-07
Hi, I'm having problems with Minolta PagePro 1250W printer - I'm able to detect it correctly, but can't specify appropriate port (USB in this case). So, no luck to print anything. 
I'm running Ubuntu 5.10 with Gnome on AsusA2500L laptop. 
lsusb output:
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0686:3006 Minolta Co., Ltd
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 001 Device 001: ID 0000:0000

I've tried to delete it and add a new printer using *sudo gnome-cups-add* in console, but got the same results as using System->Administration->Printing: I can add printer but can't print. In addition using sudo gnome-cups-add returned some errors at the end:
*(gnome-cups-add:8806): GLib-GObject-WARNING **: invalid cast from `GnomeDruidPag eStandard' to `GtkWindow'*

Any suggestions?
P.S. I've also tried  *sudo chmod a+rw /dev/usb/lp0*. It didn't help. :(

---

