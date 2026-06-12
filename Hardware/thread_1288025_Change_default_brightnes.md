---
title: "Change default brightnes"
date: 2009-10-10
forum: Hardware
---

### Post by Shamess707 on 2009-10-10
I am unable to adjust the brightness of my laptop display under ubuntu, is there a way that I can change it so it doesnt default to 100%?

---

### Post by urmish on 2010-04-22
i added the following line in 
/etc/init.d/rc.local

echo -n 20 > /proc/acpi/video/GFX0/DD03/brightness 


this should set default brightness to 20%

---

