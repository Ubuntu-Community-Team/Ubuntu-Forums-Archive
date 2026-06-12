---
title: "external hdd enclosure"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by marcomiani on 2006-05-18
hi,
 I have an external HDD enclosure USB/SATA ( it is an [ICY BOX ib-351-stus]("http://www.raidsonic.de/en/pages/products/external_cases.php?we_objectID=3769") ) with a 300GB Maxtor HDD SATA.

When I connect the enclosure with USB all works fine, but when i connect the enclosure with the SATA nothing happens.

I have 2 SATA controllers ( onboard ICH5 and a pci controller with Sil3112 ) and both don't work when I connect the external drive while the system is running.

I have Breezy Badger, but a test with a live CD of Dapper gave me the same results.

Any ideas ?

thank you in advance.


marco

---

### Post by pellgarlic on 2006-06-22
[QUOTE=marcomiani]both don't work when I connect the external drive while the system is running.[/QUOTE]

as far as i know, sata drives need to be connected from boot-time (i.e. they are not "hot-pluggable"). try plugging it in before you turn the computer on.

---

