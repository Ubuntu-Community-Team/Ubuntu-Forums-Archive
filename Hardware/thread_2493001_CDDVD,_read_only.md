---
title: "CD/DVD, read only"
date: 2023-11-30
forum: Hardware
---

### Post by kvids on 2023-11-30
I'm from Czech Republic. Mum Ubuntu Ubuntu 22.04.3 LTS. Kse, very satisfied. I am waiting for the next LTS in April 2024. The only problem: the CD/DVD drive. Connect and burn OK. But when DVD-R:TSSTcorp CDDVDW SH (DB04) is blank, it cannot be written to. Writes: /dev/sr0 (read only). Please advise how to solve. Thank you.

---

### Post by sudodus on 2023-11-30
There could be either a hardware problem (the CD/DVD drive, or the disk) or a software problem (some bad burning tool) or bad matching between driver and hardware.

It can help us understand the problem, if you tell us about the hardware: brand name and model number of the computer and of the CD/DVD drive and the [optical] disk. Please tell us also which burning tool that you are trying (for example k3b or Brasero).

Could there be a problem because you are trying to copy from a copy-protected DVD disk?

[hr][/hr]
The CD/DVD technology is more or less replaced by other ways to store and/or copy/play data nowadays. Please tell us if you might be able to use some other method/tool/hardware to replace CD/DVD, for example with a USB drive or memory card or even storage in the internet cloud.

---

### Post by Yellow Pasque on 2023-11-30
```
sudo apt-get install libcdio-utils
```
With blank CD in drive, get info:
```
cd-info
```

---

