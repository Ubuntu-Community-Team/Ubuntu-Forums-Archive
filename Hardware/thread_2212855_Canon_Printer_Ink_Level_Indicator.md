---
title: "Canon Printer Ink Level Indicator"
date: 2014-03-23
forum: Hardware
---

### Post by davethesteam on 2014-03-23
I have Ubuntu 12.04 LTS running on 64 bit system.
My Printer (Canon Pixma iP4950) works but I am unable to get information on print levels the printer deatil in Systems Settings states:
'Marker levels are not reported for this printer'

Could you please advise on how to correct this ??
Many thanks in advance

---

### Post by pdc on 2014-03-23
we installed a CLI programme called Ink

in the terminal the command > [COLOR="#FF0000"]sudo ink -d /dev/usb/lp0[/COLOR] tells us the ink levels

(if your setup is home computer and home printer joined by usb cable ..........)

I imagine you could set up a launcher to do that; (ie so you don't open a terminal)

_____________

the other way is install turboprint; they have a free version that would surely give you ink levels

---

