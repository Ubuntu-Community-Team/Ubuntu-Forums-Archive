---
title: "Device busy for scanner"
date: 2019-02-17
forum: Hardware
---

### Post by raleigh3 on 2019-02-17
I am trying to scan a document. I get this error message and do not know what it means.

```
andy@7_~/Downloads/$ scanimage -d "pixma:04A91760" --format=tiff 
scanimage: open of device pixma:04A91760 failed: Device busy
```

---

### Post by col48 on 2019-02-18
The scanner thinks another program has not finished using the device.

It could be that the last use did not finish cleanly so although the program has shut down the scanner remains unaware.
Have you tried shutting down the computer completely, then powering off the whole system for at least a minute?
This may clear it.

For other ideas, look at an internet search on "scanner device busy".  It seems to vary according to the brand of computer and of scanner.

---

### Post by slickymaster on 2019-02-18
*Thread moved to **Hardware**.*

---

