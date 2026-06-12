---
title: "HP PSC 750 needs setting up after each reboot"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by juraj on 2006-09-16
I own a HP PSC 750 (printer and scanner in one). It's connected via USB.

I can get the printing part to run just fine using the ubuntu add printer gui, however I can't get it to scan properly.

If I do this:

```
sudo chmod 777 /dev/usblp0
hp-makeuri /dev/usblp0
```

After that I have two printers available to set up: one "normal" on USB #1 that was available before and the other one: 

```
hp:/usb/PSC_750?serial={a long serial number}
```

If I set up my printer using the later available printer in ubuntu's printing gui, scanning works fine and hp-toolbox recognizes the printer.

All works fine, until the next reboot. To get the printer and scanner working, I have to chmod and hp-makeuri again and then set up the printer again, using the new CUPS uri (hp:/...).

What can I do so I don't have to set up the printer after each reboot?

TIA

---

