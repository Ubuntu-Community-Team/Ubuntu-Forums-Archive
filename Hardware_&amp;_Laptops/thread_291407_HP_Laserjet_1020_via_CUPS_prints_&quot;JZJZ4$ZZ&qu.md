---
title: "HP Laserjet 1020 via CUPS prints &quot;JZJZ4$ZZ&quot;"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by inzpektor on 2006-11-02
My HP Laserjet 1020 is connected to my server, but I always work (and print) on my laptop. If I print directly from the server, everything works fine, but if I print from my laptop, it prints "JZJZ4$ZZ" on the top of the first page and then keeps spitting out empty pages until I turn it off and back on again.

I've configured the printer on my laptop this way:

In gnome-cups-manager - New Printer.
Printer Type: Network Printer (CUPS Printer (IPP))
URI: http://<server>:631/printers/LaserJet-1020
Manufacturer: HP
Model: LaserJet 1020
Driver: foo2zjs (recommended) (Suggested)

Both my server and my laptop are running Ubuntu 6.06. This worked on Ubuntu 5.10 and it works from a Windows box.

Out of frustration, I've installed the latest foo2zjs driver on both systems (giving some extra features in the printer-properties dialog, like Resolution and N-up Orientation, whatever that is) with no success.

Also, the LaserJet 1020 icon in the gnome-cups-manager shows a printer-rack instead of just a small, standalone printer-icon - not that it bothers me, but it didn't use to be this icon.

Any help appreciated!

BTW: I posted this msg in another thread, but got no replies.

---

