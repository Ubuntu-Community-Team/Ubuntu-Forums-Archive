---
title: "Compaq EVO N610C acpi"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by Skumpic on 2007-01-06
Hi, some days ago i posted here: [http://www.ubuntuforums.org/showthread.php?t=332160&highlight=evo+suspend](http://www.ubuntuforums.org/showthread.php?t=332160&highlight=evo+suspend)
how to make suspension to ram works on compaq evo n610c using apm.

I would like to ask if someone is able to make suspension works with acpi, as this notebook should be acpi 2.0 compliant
Thanks in advance
Skumpic

---

### Post by greg.hagen on 2007-01-12
I had the exact same problem as yours with my Thinkpad x24. It worked fine until I installed Beryl, so I think that the screen blanking problem may be caused by the "dbe" module I added to xorg.conf. If you aren't using double buffering for anything important, you could comment it out and see if it works. If I find a solution that doesn't require me to remove dbe I will post it [here.]("http://ubuntuforums.org/showthread.php?t=336801")

---

