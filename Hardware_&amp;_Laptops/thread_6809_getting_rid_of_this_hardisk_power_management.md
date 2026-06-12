---
title: "getting rid of this hardisk power management"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by ghostrifle on 2004-12-01
Hi,

I don't want ubuntu to shutdown my harddisk (for power management reasons) in any mode (laptop or whatever). Could anyone tell me how I can do this ?

Bye, Alex

PS: ubuntu is running without any hassles on my acer ferrari 3000 ;)

---

### Post by julien on 2004-12-03
You need to edit the file /etc/acpi/power.sh and set the value of the "S" option of hdparm to 0:
```
$HDPARM -S 0 /dev/hda
```
You can find more information about the different hdparm options in "man hdparm"

---

### Post by ghostrifle on 2005-05-01
Thanx a lot !

---

