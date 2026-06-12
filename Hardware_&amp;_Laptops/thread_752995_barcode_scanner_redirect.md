---
title: "barcode scanner redirect"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by whelanp on 2008-04-12
hello all

I have a barcode scanner that shows up as a secondary keyboard I was wondering is there a way for linux/ubuntu to not always direct the input from this device to standard in. 

For example if i am on a web page i'd like to be able to scan and not have the barcode data appear on screen but if i type at my normal keyboard that it would appear on screen.

Thanks a million

Pablo

Sorry about my english.

---

### Post by whelanp on 2008-06-17
I ended up using the evdev keyboard driver in x and then restricted input to x for my attached keyboard.

---

