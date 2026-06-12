---
title: "After shutdown no power off"
date: 2009-02-21
forum: Hardware
---

### Post by sjoewert300 on 2009-02-21
Hi,

When I want to power off my laptop (Acer Aspire 7520) I have to wait until the splash bar is empty.
Then I have to press a key (doesn't matter which one (on the keyboard or the regular power button)) to turn off my machine..

Please help, because this is really annoying!!

Cheers,
sjoewert

(P.s. Sorry for my English ;))

---

### Post by whoop on 2009-02-21
try acpi=force in your kernel line
[http://ubuntuforums.org/archive/index.php/t-416645.html](http://ubuntuforums.org/archive/index.php/t-416645.html)

---

### Post by sjoewert300 on 2009-02-22
> **whoop said:**
> try acpi=force in your kernel line
[http://ubuntuforums.org/archive/index.php/t-416645.html](http://ubuntuforums.org/archive/index.php/t-416645.html)

Thanks for the fast reply.
But I've already done that and it didn't work out :(.
My menu.lst (ubuntu part) is like this:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		89188859-753f-4efb-91f0-e31be472926d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=89188859-753f-4efb-91f0-e31be472926d ro quiet splash vga=792 **acpi=force**
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```

Any other ideas?

Cheers,
sjoewert

---

### Post by sjoewert300 on 2009-03-13
Has this forum died or something.?? Am I the only one in the world who has this problem??

---

