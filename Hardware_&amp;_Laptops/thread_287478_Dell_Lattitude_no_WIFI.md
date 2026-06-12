---
title: "Dell Lattitude no WIFI"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by Branta on 2006-10-28
6.10 Edgy

PC install was fine.

Dell Latitude laptop with a working _D-Link DWL-G630_ wireless card was detected but NO ESSID listed though _92% signal_ from an AP 2 feet from it.

All is gray until I click 'enable this connection' box but No SSID on pull down.  Can't pull down anything when all is gray.

The AP is good as other Lattitude with Dapper works fine.  

This Latitude and this DWL-G630 worked fine with Dapper before Edgy install.


--- Bob ---

---

### Post by brn on 2006-10-29
This may not help but on my Dell I found that I have to issue "sudo cardmgr" to activate the PC card slots.

---

### Post by Branta on 2006-11-01
> **brn said:**
> This may not help but on my Dell I found that I have to issue "sudo cardmgr" to activate the PC card slots.

My download of 6.10 took 12 hours and had defects in the file.  After I found one the downloaded in 25 minutes the installation and function has been perfect.

But, _**what do I have to install to to have  'cardmgr**_?  Is it in either gnome-devel or build-essential?

--- Bob ---

---

### Post by dbeltr1 on 2006-11-01
I had a similar problem with a Dell Inspiron 6000 intel wifi card. The ESSID wasn't listed. I typed in the ESSID and Network password and it worked.

---

