---
title: "Brother MFC-7820N printer will not print"
date: 2010-02-20
forum: Hardware
---

### Post by tractor on 2010-02-20
I finally convinced my brother to try Ubuntu, and installed 9.10 last weekend. All went well except for his Brother MFC-7820N printer. I've installed Ubuntu on about 15 diffferent machines, and have had no printer problems with HP, Samsung, Konica-Minolta, and Canon. When I connected his printer, it installed just like the others, and said it was ready for use. However, when trying to print a test page, the attachment here shows all I am getting on the first page, and then it keeps printing out blank pages forever until I pull out the paper tray. I've tried changing the drivers through cups, I've downloaded the drivers from Brother and installed them and followed there instructions as best I could, and all I end up with is what you see on the attachment, or with nothing happening at all. I have things back to what they were when it was first setup. The same problem still exists. Also, I tried printing a page in Firefox, and got exactly the same printout. My brother was not anxious to try Ubuntu. He is less than impressed. Any help you can give would be apprecaited!!!!!!!


Thank you!

---

### Post by tractor on 2010-02-21
This issue was resolved by downloading the PPD file for this printer from openprinting.org, and installing through the cups localhost:631.

---

