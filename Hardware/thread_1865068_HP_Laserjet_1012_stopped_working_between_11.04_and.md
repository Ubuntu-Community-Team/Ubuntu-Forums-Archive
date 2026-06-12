---
title: "HP Laserjet 1012 stopped working between 11.04 and 11.10"
date: 2011-10-19
forum: Hardware
---

### Post by JohnAdamTurnbull on 2011-10-19
When I upgraded from 11.04 to 11.10, my HP Laserjet 1012 would not print.

What worked: 

- Choose System Settings (top right) > Printing > HP-Laserjet-1012
  (this may work for other printers too)
- Right click and choose "Properties"
- Choose "Settings" on the left
- On the right, beside "Device URI:" click "Change ..."
- Wait a moment (note the loading graphic in the lower left)
- Choose "Current Device ..."
- Click Apply
- Click OK

At this point, your printer should spew all the test pages that you put in the queue while you were trying to remember how to fix this.

If this does not work, you'll have to look for documentation on "CUPS" which is the library that controls printing.

---

