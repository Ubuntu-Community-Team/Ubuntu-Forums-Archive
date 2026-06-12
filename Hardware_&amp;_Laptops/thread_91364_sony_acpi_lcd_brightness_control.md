---
title: "sony_acpi lcd brightness control"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by mahalram on 2005-11-17
used to work with hoary .....
just had to do echo "x" > /etc/acpi/sony/brt 
(with x between 0 and 8)

with breezy /proc/acpi/sony/brt is MISSING  but theres a new  .../sony/brightness
instead of brt


to get it working 

do
sudo chmod +w brightness

---

