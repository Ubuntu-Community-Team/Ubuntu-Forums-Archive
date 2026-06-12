---
title: "sil3132 (sil3124) performance"
date: 2009-08-08
forum: Hardware
---

### Post by rhuddusa on 2009-08-08
I installed a new sil3132 controller (Rosewill RC-211) [http://www.newegg.com/Product/Product.aspx?Item=N82E16816132008](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132008) and have 2 hard drives attached. when i read from either drive individually, i see ~ 100 MB/s from each. But when i read from both simultaneously, my speed drops to ~70 MB/s for each, ~140 MB/s aggregate. What's up with that? from what I understand, pci-e x1 should support 250 MB/s, and the card claims to support ( Supports 1-lane 2.5Gbps PCI Express) and (Transfer Rate 3.0Gbps) [http://www.rosewill.com/products/462/productDetail.htm](http://www.rosewill.com/products/462/productDetail.htm) i'm running on an intel dq45cb with jaunty server. So where is my bandwidth limitation coming from?

---

### Post by istodorov on 2009-12-30
Sil3132 is SATA 1a compliant. Read/Write speeds are up to 150 Mb/s

---

