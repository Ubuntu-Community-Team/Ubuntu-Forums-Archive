---
title: "Promise SATA300 TX4"
date: 2009-11-01
forum: Hardware
---

### Post by iMisspell on 2009-11-01
Currently i have this (_[Promise SATA300 TX4]("http://www.promise.com/product/product_detail_eng.asp?product_id=139")_) card installed with a single _[drive]("http://www.wdc.com/en/products/products.asp?driveid=551")_ and booting Ubuntu 9.04 off it, everything is working fine.

A couple of questions.
How can i check that it is running at 3Gb/s ?
How to check the driver version ?

If a driver update is needed, how pain full will it be and what should i watch out for ?

Thanks for any guidance.
_

---

### Post by iMisspell on 2009-11-02
> **iMisspell said:**
> How can i check that it is running at 3Gb/s ?

Found this to be help full for that.
```
sudo hdparm -tT /dev/sda
 Timing cached reads:   1174 MB in  2.00 seconds = 586.53 MB/sec
 Timing buffered disk reads:  312 MB in  3.01 seconds = 103.77 MB/sec

```

Compared the results from the drive in question to two other drives which are SATA I and the SATA II drive reads about twice as fast, so thats good.


Still looking on how to get the SATA-Cards driver info.

_

---

