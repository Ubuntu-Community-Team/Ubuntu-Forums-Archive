---
title: "Usb-serial adapter recommendations?"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by joeljkp on 2005-11-05
I'm looking for a good-quality usb-serial adapter that will work out of the box with Ubuntu. I have a Keyspan right now, but it needs some non-free firmware that Ubuntu doesn't include.

Anyone have any recommendations?

---

### Post by riggsd on 2005-11-05
The [SerialIO USB/RS-232]("https://serialio.com//store/product_info.php?cPath=54_61&products_id=30") adaptor works great for me. It lists for $20. I've also got an old Belkin unit laying around that works with Linux, but didn't work with some exotic RS-232 microcontroller projects I was working on, but worked fine syncing up a PDA.

---

### Post by joeljkp on 2005-11-06
[QUOTE=riggsd]The [SerialIO USB/RS-232]("https://serialio.com//store/product_info.php?cPath=54_61&products_id=30") adaptor works great for me. It lists for $20. I've also got an old Belkin unit laying around that works with Linux, but didn't work with some exotic RS-232 microcontroller projects I was working on, but worked fine syncing up a PDA.[/QUOTE]

The SerialIO looks good. How does Ubuntu detect it? Is there any configuration involved?

---

### Post by riggsd on 2005-11-06
[QUOTE=joeljkp]The SerialIO looks good. How does Ubuntu detect it? Is there any configuration involved?[/QUOTE]

Plug it in, hotplug loads the usbserial driver. Check dmesg to see what device it's loaded as, eg. /dev/ttyS14

---

