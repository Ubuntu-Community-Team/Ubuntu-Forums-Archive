---
title: "Adaptec 1405, SAS Hardware support"
date: 2012-10-23
forum: Hardware
---

### Post by big_blue on 2012-10-23
Hi.

I´m still using an Atom mainboard as my private homeserver. Now i just want do some backup to an Ultrium 3 SAS drive. So i want to get a cheap, out of the Box supported, SAS controller to connect the Ultrium drive. In the past i used the Adapted SCSI controllers and they worked very well. So please let me know if the Adaptec 1405 controller is a good one to connect the Ultrium drive to my system. If not, please give me an alternative.

thx
big_blue

---

### Post by AdaptecBill on 2012-10-23
Greetings from Adaptec!

A series 1 host bus adapter sounds like the right solution for what you're trying to do, the main question is whether your tape drive is internal or external. If it's internal, then the 1405 would be the card you want. If it's external, then you'd want to get a 1045. The driver for either card should be in-box, but if you have driver-related issues, the Linux driver source code is available on our site.

If you know what make/model tape drive you have, I can let you know whether we've tested it for compatibility or not, or you can see if your drive is on our compatibility report at [http://download.adaptec.com/pdfs/compatibility_report/compatibilityreport_1405_1045.pdf](http://download.adaptec.com/pdfs/compatibility_report/compatibilityreport_1405_1045.pdf) under the non-DASD section.

If your drive isn't on the compatibility report, that doesn't mean it won't work with the 1405/1045, that just means we haven't specifically tested that model drive.

If you have any further questions, please don't hesitate to contact our Technical Support directly through our support website at [http://ask.adaptec.com](http://ask.adaptec.com)

Regards,

--
Bill C.
Adaptec by PMC Technical Support

---

### Post by big_blue on 2012-10-23
Thank you very much for your support. The ultrium drive (HP StorageWorks Ultrium 920) is an internal, so the 1405 will be the correct one.

THX
big_blue

---

