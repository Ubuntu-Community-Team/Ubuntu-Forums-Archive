---
title: "Wireless 54g PCI"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by marcus_krantz on 2005-05-09
Hi all!

I have a Belkin 54g wireless pci card which isn't working at all. 
It is listed in the device manager but nothing more than that...

Does anybody have a similar card working?

regards marcus

---

### Post by Zelut on 2005-05-09
unfortunately 54g isn't supported as of yet under linux.  There are more than a few 11b cards supported but those of us with 54g are out of luck.  I've got a emachines notebook with 54g on-board (broadcom chipset) that just wont work either.  That is the only reason I haven't switched over the notebook too.

Here is a list of supported wireless hardware:

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

---

### Post by gil-galad on 2005-05-09
You might be able to use the ndis wrapper to use it.  That is able to use windows drivers for some wireless cards.  

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

I have never used it personally, but it is supposed to work well.

---

### Post by stupiduglyfool on 2005-05-10
[QUOTE=gil-galad]You might be able to use the ndis wrapper to use it.  That is able to use windows drivers for some wireless cards.  

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

I have never used it personally, but it is supposed to work well.[/QUOTE]

I have a belkin 54g, based on broadcom and have it succesfully working with ndiswrapper and ubuntu, however it wouldn't work with the apt-get ndiswrapper-utils, i downloaded the latest source and compiled that instead.

---

