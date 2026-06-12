---
title: "SCSI scanner sound conflict"
date: 2010-02-15
forum: Hardware
---

### Post by amoht on 2010-02-15
Hi,

I installed Ubuntu 9.04 and to enable XSANE to use my HP 4P SCSI scanner I followed [http://jhansonxi.blogspot.com/2009/08/writing-udev-rules](http://jhansonxi.blogspot.com/2009/08/writing-udev-rules).... and wrote 45-scsi-scanner.rules in /etc/udev.rules.d/. I created a scanner group and added myself to that group. That enabled XSANE to use my scanner but it has conflicted with sound as now no system sounds occur and I cannot play any music CD's. 
I have an AudioExcel sound card.
I need advice as to how to get my Scanner and sound card working together.

Alan

---

### Post by amoht on 2010-02-17
Problem solved.

When typing the rules for 45-scsi-scanner.rules I didn't type them on one continuous line. Once I corrected this both sound and scanner are working.
Hope my mistake may alert anyone else who has to install a SCSI scanner.

Alan

---

