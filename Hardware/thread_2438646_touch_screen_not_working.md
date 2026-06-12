---
title: "touch screen not working"
date: 2020-03-15
forum: Hardware
---

### Post by tilsvenson78 on 2020-03-15
[Acer Swift 5 (SF514-54T)]("https://mobilespecs.net/laptop/Acer/Acer_Swift_5_SF514-52T-82WQ.html") touch screen not working
Just installed Ubuntu 18.04.4 in a brand new machine but the touch screen does not work (worked fine under Windows 10).

---

### Post by mörgæs on 2020-03-18
Hi, welcome to the fora.

New hardware needs new software. I suggest that you try a live boot of 19.10 and if that does not work then 20.04 (thought the latter is not formally released yet).

---

### Post by lostdata2 on 2021-02-01
On the swift 5 you should be able to fix this by adding the following command to your kernel boot parameters.


[LIST]
[*]usbcore.quirks=2386:433b:bk to enable touchscreen (2386:433b is the ID for the touchscreen from lsusb
[/LIST]

---

