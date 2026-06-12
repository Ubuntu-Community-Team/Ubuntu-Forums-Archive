---
title: "Connecting issue"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by ur0b0r0 on 2008-03-09
ok i cant connect to internet, my wireless card is intel pro/set wireless 3945 chipset and yesterday i installed new drivers on my windows xp because the old one wasnt working anymore ,and when i installed the new stuff it worked really good but when i booted linux it didnt connect, well ubuntu said it was connected, the wireless manager said i was conected and my signal ip even mac but i dont receive internet in any application i have none can connect, and when i checked administration/windows wireless drivers there was no driver anymore + i downloaded the same drivers version and for windows and i tryed to install them in windows wireless drivers but nothing happens, what can i do?

---

### Post by oldsoundguy on 2008-03-09
windows drivers don't work in Linux.

You have to get Linux drivers for that chip (if available).

---

### Post by Yellow Pasque on 2008-03-09
> windows drivers don't work in Linux.

Please google and familiarize yourself with "ndiswrapper" before making this claim.

---

### Post by oldsoundguy on 2008-03-09
I know about wrapper .. but he was trying to install the driver itself from what it appears.  And NOT ALL DRIVERS for WinDOZE based chips will work with NDISWRAPPER .. it is not a be all to end all for every card that will not load.  First you look for a Linux driver .. preferable.  THEN you consider the alternatives.

I chose to use atheros based wireless cards and THEY install without any issues.

---

### Post by BooBooNTZU on 2008-03-09
you can download and try Ubuntu 8.04 and also visit the linuxwireless.org website for more information.

you can use ndiswrapper or some form of firmware cutter similar to the the b43-fwcutter

---

