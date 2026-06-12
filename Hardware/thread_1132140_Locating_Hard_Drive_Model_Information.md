---
title: "Locating Hard Drive Model Information"
date: 2009-04-21
forum: Hardware
---

### Post by CarlosinFL on 2009-04-21
I am running 8.10 on my machine and have no GUI available. I need to cat / grep for the exact make / model info for my S-ATA drives that my system is running. Can someone please tell me how or where I can determine the exact make and model info of my drives installed on Ubuntu?

---

### Post by dabl on 2009-04-21
Try running "dmidecode" in a console window.  Another nice utility for this purpose is hwinfo.  You'll have to install it:

```
sudo apt-get install hwinfo
```

Then you can just enter hwinfo.

---

