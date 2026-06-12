---
title: "Can't install Samsung SCX-1770F printer"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by snowboard975 on 2007-01-21
I have a samsung printer. It's model name is SCX-1770F and only sold in South Korea. 
I can't make it working. I searched all the threads related to samsung printer, but couldn't find any solution that can have it work. 

First, I tried running System>Administration>Printing and add new printer. It detected USB connection of the printer and detected its model name, but couldn't find its driver. It recommended me to install SI-630A driver that is incorrect. I chose it anyway, but the printer didn't work. 

Second, I tried to install the Samsung Unified Printer driver from the samsung website. But there was no unified printer driver for this model. Anyway, I downloaded the unified printer driver for another model and installed. But it also didn't include a driver for my model. 

Third, I tried installing generic printer driver (PCL3, 5e, 7, and PostScript driver) only to fail. 

I'm frustrated and on the verge of giving up installing the printer. 
Plz help me if you have any idea.

---

### Post by snowboard975 on 2007-01-21
I figured it out how to install it!!!!

I used HP Officejet 5600 driver and it amazingly solved the problem!!!

In summary, I did like this.

System>Administration>Printing -> Add New Printer (when the printer is connected) -> Choose SCX-1770F -> Choose HP Officejet 5600 for its driver

I think some Samsung printers are licensed by HP. My Samsung inkjet cartridge has a HP logo behind it. 
So I visited HP website and and found exactly same printer, Officejet 5600, in appearance. 
And the driver of HP model is completely compatible with my printer. 

And I also found out that Samsung doesn't provide linux drivers for most inkjet printers so far. 
Samsung only provides linux drivers for laser printers.

---

