---
title: "Ubuntu 10.10 Acer AO751h"
date: 2011-01-17
forum: Hardware
---

### Post by Brynster on 2011-01-17
Hi guys sorry to be a pain but, on the Ubuntu Wiki regarding the installation of GMA500 Poulsbo drivers for previous/current versions of Ubuntu there was a line you could add to the start applications which corrected the missing battery icon. It was something along the lines of

cat/mon/BAT0

However sometime the page has changed and that has been removed, now I have spent a few days hunting high and low for it, does anybody remember or know it 

Thanks in advance

---

### Post by krasny on 2011-03-17
cat /proc/acpi/battery/BAT1/info

hope this help you

---

