---
title: "SDHC 16GB &quot;no medium found&quot;"
date: 2009-01-07
forum: Hardware
---

### Post by mathfeel on 2009-01-07
I have an EEEPC900, and I am positive that the SD slot is SDHC capatible. In fact, the last time I used the card in question I booted a livecd off of it to reinstall ubuntu.

But today, I plugged in the same card and try to mount the device and I was given a "no medium found" message. dmesg does not have any new entry regarding the card got plugged in. I can still use the card through a USB SDHC card reader.

Not sure what is going on. Any help?

p.s. I tried a NON-SDHC 256MB card and dmesg immediately responded:
```
[ 2178.943415] sd 2:0:0:0: [sdc] 498176 512-byte hardware sectors (255 MB)
[ 2178.948024] sd 2:0:0:0: [sdc] Write Protect is off
[ 2178.948024] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 2178.948024] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 2178.956041] sd 2:0:0:0: [sdc] 498176 512-byte hardware sectors (255 MB)
[ 2178.958445] sd 2:0:0:0: [sdc] Write Protect is off
[ 2178.958445] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 2178.958445] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 2178.960347]  sdc:
```

---

