---
title: "HP 5300C Scanner: A little tip"
date: 2009-09-23
forum: Hardware
---

### Post by JC Cheloven on 2009-09-23
I was unable to use my hp5300c scanner with xsane in ubuntu. It was recognized, it even did a preview when requested, but when scanning it stopped and hanged in about one fourth of the scan. I had to hard-close the application (and then the scanner wasn't recognized until the next reboot).

I tried a number of things, including compliling the latest version of the avision driver from the project page, and installing the latest libusb, with no avail. Only disabling calibration worked, but this is not an option, of course. It was the same in ubuntu 8.10 and 9.04.

By pure hazard, I've found a workaround last monday. **If I set the scanning resolution to a multiple of 100 (100, 200, 300, 400) it works !!** (it happened to be 350 by default)

Hope this may help someone searching these forums in the future.

---

### Post by elvisd on 2009-11-26
Hi JC. Thank you for sharing your experience. You saved me the night! :P
I can confirm that the trick works like a charm!

Muchas gracias.

---

### Post by JC Cheloven on 2010-01-07
> **elvisd said:**
> Hi JC. Thank you for sharing your experience. You saved me the night! :P
I can confirm that the trick works like a charm!

Muchas gracias.
Hey, finally this served to someone!

De nada :-)
(You're welcome)

---

