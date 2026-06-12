---
title: "Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)"
date: 2009-03-30
forum: Hardware
---

### Post by skotos on 2009-03-30
I have a built in Multimedia Card Reader that I am now checking for the first time since I realized I had one.
Unfortunately, it shows up in many *lspci* outputs, but no one seems to ever have faced the problem.
Here is the question: which device/module should be loaded to have it running?

The *lspci* output is the following
```

09:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
09:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

---

### Post by timcredible on 2009-03-30
have you put a card in?  it's probably already working.

---

### Post by skotos on 2009-03-30
> **timcredible said:**
> have you put a card in?  it's probably already working.
Yes, thank you, I did. I put a Sony SD, but I did not find it with```
sudo fdisk -l
```

---

### Post by skotos on 2009-05-16
Unfortunately I do not remember the link, but I have read that the Sony memory stick cannot  currently be read. The Sony memory stick pro, instead, is reported to be working fine.
I have in the meantime checked an SD card and it just worked out of the box.
This solves my issue because of the current lack of support for the original Sony memory stick.
HTH others

---

