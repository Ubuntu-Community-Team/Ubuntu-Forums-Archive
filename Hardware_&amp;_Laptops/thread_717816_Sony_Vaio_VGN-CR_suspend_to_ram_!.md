---
title: "Sony Vaio VGN-CR suspend to ram !?"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by mixandgo on 2008-03-07
Does anyone have a clue how to make this work ? I am running ubuntu 8.04 alpha 2.6.24-11-generic and I'd really like to have suspend to ram working. Any hints would be greatly appreciated.

Thanks

---

### Post by mixandgo on 2008-03-14
it was the uvcvideo module that was causing all the mess, removing it (sudo rmmod uvcvideo) worked like a charm

---

