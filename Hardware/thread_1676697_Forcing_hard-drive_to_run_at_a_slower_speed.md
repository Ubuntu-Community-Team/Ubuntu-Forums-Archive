---
title: "Forcing hard-drive to run at a slower speed?"
date: 2011-01-27
forum: Hardware
---

### Post by khughitt on 2011-01-27
Hi all,

I have a laptop with a 7200rpm hd, which at the time of purchase seemed like a great idea. I've since then realized that the faster HD not only drains the battery very quickly, but also causes the laptop to get really hot.

I know there are some options in the power settings to specify that the hard-drive should spin down at times, but does anyone know if it is possible to get the hard-drive to permanently run at 5400rpm?

Thanks!

---

### Post by tgalati4 on 2011-01-27
I doubt it.  The controller, buffers, address bus, etc, are all optimized to run at 7200 rpm.  Some drives will spin to 5400 to save power, but spin up to read and write data.  There may be some parameters that you can adjust with hdparm, but you will have to google your particular drive to find out what settings are available.

You could buy a usb enclosure and purchase a new 5400 rpm drive and copy the installed drive onto the external drive.  Then swap the drives.  That gives you a backup and a functional external drive.

---

### Post by khughitt on 2011-01-28
That's probably not a bad idea. Thanks for the suggestion!

---

