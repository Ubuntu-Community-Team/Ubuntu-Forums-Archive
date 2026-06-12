---
title: "Fingerprint scanner not working on Lenovo Ideapad v460"
date: 2011-02-24
forum: Hardware
---

### Post by janlan on 2011-02-24
I have Lenovo Ideapad v460. I cant get working fingerprint scanner. I have tried Fingerprint GUI but my scanner was not listed there. I guess there are no drivers for mine. How to solve this?

---

### Post by KnightZero77 on 2011-02-24
Do you know what model of fingerprint scanner is in the notebook?  If lsusb reports that you have a Upek scanner, you'll need to install the libbsapi library.

> sudo apt-get install libbsapi

I have a full guide, plus a link to my source material for fixing this very problem on [my blog]("http://knightzero-insignificant.blogspot.com/2011/02/thinkpad-x201-fingerprint-reader-in.html").  I was specifically working with the Thinkpad X201, but if you have the same fingerprint reader, you might benefit.

---

### Post by janlan on 2011-02-24
I have no idea, which one is the scanner:
```

Bus 002 Device 005: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 1241:1503 Belkin Keyboard
Bus 002 Device 003: ID 062a:0003 Creative Labs 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 064e:f216 Suyin Corp. 
Bus 001 Device 004: ID 1c7a:0801 LighTuning Technology Inc. 
Bus 001 Device 003: ID 0489:e00d Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by janlan on 2011-02-25
Anybody?

---

