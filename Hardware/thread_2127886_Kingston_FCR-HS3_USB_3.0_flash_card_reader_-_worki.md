---
title: "Kingston FCR-HS3 USB 3.0 flash card reader - working in Ubuntu?"
date: 2013-03-21
forum: Hardware
---

### Post by Fraoch on 2013-03-21
Google searches aren't locating anything relevant, so I'm wondering if anyone is using this USB 3.0 card reader in Ubuntu?  Does it work OK?

[http://www.kingston.com/en/support/technical/products?model=fcr-hs3]("http://www.kingston.com/en/support/technical/products?model=fcr-hs3")

Seems fast and gets good reviews.  It would be nice to use with some new UHS-1 SD cards I have that can actually take advantage of the speed, but I've had problems with USB 3.0 devices in Ubuntu before.

Anyone?  Bueller?

---

### Post by mike.mikowski on 2013-12-18
Apparently, it works "perfectly under linux"[URL="http://www.amazon.com/Kingston-Memory-Card-Reader-FCR-HS3/product-reviews/B005ES0YYA/ref=cm_cr_pr_top_link_next_2?ie=UTF8&pageNumber=2&showViewpoints=0&sortBy=byRankDescending"]
http://www.amazon.com/Kingston-Memory-Card-Reader-FCR-HS3/product-reviews/B005ES0YYA/ref=cm_cr_pr_top_link_next_2?ie=UTF8&pageNumber=2&showViewpoints=0&sortBy=byRankDescending[/URL]

---

### Post by Fraoch on 2013-12-18
I did end up getting one and yes, it does work properly under Linux with the right USB 3.0 controller on the motherboard.

It does NOT WORK with an ASMedia 1040:

[https://bugzilla.kernel.org/show_bug.cgi?id=43279](https://bugzilla.kernel.org/show_bug.cgi?id=43279)

Note: this is a first-generation USB 3.0 controller, superseded by the ASMedia 1042.

It works fine with the VIA VL805 which is a much newer USB 3.0 controller.

---

### Post by mike.mikowski on 2013-12-18
Thanks for the feedback.  I will be certain to avoid that controller :)

---

