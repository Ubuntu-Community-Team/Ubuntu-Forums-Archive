---
title: "Activate SATA during installation fails"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by Bear Knuckle on 2008-12-12
Hi,

since my Vista installation ruined itself during an autoupdate, I decided to switch back to linux.

So I downloaded the netboot image from Intrepid Ibex (8.10) of my favourite linux distribution.

Yesterday I tried to install it on my machine, using a Gigabyte GA-P35-DS3 ( [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2544](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2544) ) motherboard and two Samsung 500GB hdds in SATA Raid Mode 1 (Mirrored).

During the installation process, the wizards asks (after detection of disks) if the SATA Raid should be activated. Choosing "Yes" results in an error and the installation refuses to proceed. Choosing no results in the raid is not used and the disks are in an corrupted state after an installation.

How can I activate sata raid during the installation, so the raid disks are used properly?

edit: The solution? I did nothing, but creating the raid in die raid controller a second time, after that, the graphical installer recognized one 500GB hdd, like it should be. Installation was flawless.

---

### Post by Bear Knuckle on 2008-12-12
Bump 1 time...

---

### Post by Bear Knuckle on 2008-12-15
One last bump... anyone? Any hints? Need more infos?

---

