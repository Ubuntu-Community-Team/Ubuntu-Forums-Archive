---
title: "HP Deskjet 1360 in Feisty"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by martin_legion on 2007-05-04
I have an HP Deskjet 1360. In dapper I made it work using the Deskjet 3360 driver, but that trick is not working anymore in feisty.
Using the D1300 series isn't working either. 

PLEASE, I need to make it work as soon as possible!

THANK YOU

---

### Post by johnc4510 on 2007-05-04
This page:

[http://h20180.www2.hp.com/apps/Lookup?h_pagetype=s-001&h_client=S-S-R295-1&h_page=hpcom&lang=en&cc=us&h_lang=en&h_product=236252&h_cc=us&h_query=HP+3600&x=0&y=0](http://h20180.www2.hp.com/apps/Lookup?h_pagetype=s-001&h_client=S-S-R295-1&h_page=hpcom&lang=en&cc=us&h_lang=en&h_product=236252&h_cc=us&h_query=HP+3600&x=0&y=0)

listed the drivers for the 3360 series printer. I believe you can download the driver to your home file, then when you set up the printer, click on install driver button and navigate to the driver in your home file.   Hope this works for ya!

---

### Post by martin_legion on 2007-05-04
My printer is D1360, shouldn't I try the D1360 drivers instead of D3360?

---

### Post by johnc4510 on 2007-05-04
yes, if it's listed, but i didn't see it, and since you said the 3360 driver worked, that's where I led you.

---

### Post by martin_legion on 2007-05-14
That page leads to 3600 not 3360. 
I searched for 3360 and nothing.
There are no drivers for linux.
I tried selecting 3320, 3920, 1300, and deskjet in CUPS, but none worked. How can it be that worked on a previous version of ubuntu and not in the newest? Hardware compat. should be added, not removed...

---

### Post by treak007 on 2007-05-14
The Deskjet 1360 is supported by HPLIP (The official HP linux Printer Drivers) 

You can download it here: 
[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

### Post by mr.lee on 2007-10-05
somehow I've experiencing something different about this. I use HP D1360 on 6.06 before. I use 3640 or 3620 driver, and it's work! Working only until the catrigde is empty, then the problem come.
It can't print black. Then I change the black catridge with the new one....still can't print black. Only colour, but my colour is suddenly empty out. But I never use any colour for my printing...

Then I realize, I tried to move to 7.04, and I'd use 1300 driver for my 1360. Viola!! It's working again. Black and the colour. Both of them

I guess 3xxx driver is not compatible with black catridge for 13xx series. My experience, my conclution. Who knows?

---

