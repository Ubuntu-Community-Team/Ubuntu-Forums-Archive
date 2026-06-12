---
title: "troubles with laptop wireless..."
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by chernymechty on 2005-08-27
i am having a problem installing the drivers for my wpc54gs wireless card for my laptop.  i have done my research and downloaded ndiswrapper, as well as a variety of drivers that are supposed to work, including files such as lsbcmnds.inf and wmp54gs_20050406.exe.  unfortunately, i am stuck on the same step with each driver.  here is the process:

sudo ndiswrapper -i path/drivername

sudo ndiswrapper -l
drivername           invalid driver!

sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


any suggestions?

---

### Post by John.Michael.Kane on 2005-08-27
Your card is based on the Broadcom chipset
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)
[http://www.opendrivers.com/categorycompany/1113/1685/network-linksys-free-driver-download.html](http://www.opendrivers.com/categorycompany/1113/1685/network-linksys-free-driver-download.html)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#List_.28alphabetically.29](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#List_.28alphabetically.29)

hope this helps

---

