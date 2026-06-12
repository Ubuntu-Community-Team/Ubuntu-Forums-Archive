---
title: "installing a built-in webcam"
date: 2008-05-16
forum: Hardware
---

### Post by balagosa on 2008-05-16
so my friend and i have troubles on our Asus webcams.

one day, reading "nicedude"'s post about updating PCI IDS via

```
sudo update-pciid
```

I decided to try them for myself (only with my USB IDS). so i did
```
sudo update-usbids
*downloading*
lsusb
``` to my surprise, my webcam already had a name (it was now recognized as "Syntek"). so i tried it out with Ekiga(previous tries with Ekiga failed), and it worked. even tried it with cheese.

my problem is, how did it work? i know i have done something right but i dont know what. i am 100% sure i didnt download any drivers. to the people out there who have experienced built-in webcam installation, can you enlighten me on this? because i also want to help my friend whose camera isnt working(but recognized as Asustek Webcam). before i did the "sudo update-usbids", i tried to get my wifi working. so i **reinstalled linux-restricted-modules-(kernal #)**. so please, anyone could tell me where i got it right?

NOTE: i had previous ventures on getting my webcam to work, but it proved a fault. the websites i found by research stated that my cam isnt supported.

---

### Post by balagosa on 2008-05-16
*bump*

---

