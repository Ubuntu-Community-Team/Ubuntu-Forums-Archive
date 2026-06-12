---
title: "udev, hal, soundmodem and permissions"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by non-poster on 2008-03-26
When I run soundmodem, it creates /dev/soundmodem as a link to /dev/pts/X, where X is a number.  The permissions of /dev/pts/X are 620.  I want it to be either 660 with a certain group, or 666.  How do I create a (udev?) rule for this?

---

