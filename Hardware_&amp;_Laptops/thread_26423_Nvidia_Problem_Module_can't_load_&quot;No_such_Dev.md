---
title: "Nvidia Problem: Module can't load &quot;No such Device&quot;"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by joaoeb on 2005-04-12
I can't install the Nvidia Drivers. I'm using a Nvidia VantaLT  grafics board. 
sudo modprobe nvidia return this:

```

FATAL: Error inserting nvidia (/lib/modules/2.6.10-5-386/kernel/drivers/video/nvidia.ko): No such device

```

Apt-get don't worked (instructions from ubuntuguide)
I even recompiled the kernel (2.6.10-5-386) and used the Nvidia installer but it don't work.

Someone have the same problem? Or any sugestion?

Tanks.

---

### Post by Nis on 2005-04-24
The VantaLT is not supported by the Nvidia Linux driver.  You'll have to go with the open source nv driver.  You probably woundn't see any difference on the Vanta board anyway.

---

