---
title: "Problem detecting the scanner"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by scourge on 2005-08-09
I have a Canon CanoScan FB 630P scanner connected to the LPT port. Xsane doesn't detect it, it just reports "no devices available". But when I look at the supported hardware list on the Sane website it says that support for my scanner is "good", "complete" being the highest level of support.

When I plugged in the scanner and booted in Windows XP, I didn't see the good ol' "New hardware found" dialog, and the scanner doesn't show in the device manager. So I installed the drivers from the driver CD, rebooted (again in Windows) and still the scanner doesn't show anywhere. I tried running the CanoCraft scanning software anyway; it told me that no scanners were found. But strangely enough, when I hit the "Scan" button, everything worked and I got some photos scanned.

So what could be wrong here? Both Windows XP (even the scanning software) and Ubuntu Hoary are telling me that no scanners are plugged, but in Windows it still somehow works.

---

### Post by tom-ubuntu on 2005-08-09
Did you check on which version of Sane your scanner was marked as good? Perhaps Ubuntu does not provide the right version, meaning an older one.

---

### Post by scourge on 2005-08-09
I have version 1.0.15 of the Sane library. The support for my scanner is supposed to be "good" in that version, so that's not the problem.

---

