---
title: "Can't use a Samsung M2070FW scanner wireless"
date: 2015-11-26
forum: Hardware
---

### Post by Yahoé on 2015-11-26
On 15.10, I can print wirelessly to this Samsung M2070FW multi-function printer/scanner, but can't scan. I tried different suld versions, added the relevant tcp 192.168.xx.xx to /etc/sane.d/xerox_mfp.conf, but to no avail. The scanner is detected by the scanning tool, but when scanning is initiated wirelessly, the scanner wakes up, hums for about 20 seconds before idling again and an error is returned by simple scan.

Any help would be appreciated.

---

### Post by ajgreeny on 2015-11-26
And the simple-scan error is what?  That may help us.

---

### Post by Yahoé on 2015-12-01
Translated from French, Simple-Scan returns "Scanning failure - Cannot start scanning" then offers two buttons "Close" "Change scanning device".

---

### Post by Yahoé on 2015-12-01
Xsane, running from the console, returns a floating point exception... Same symptoms, the scanner is initiated wirelessly until the error is generated, then stops.

---

### Post by Yahoé on 2015-12-14
Bump

---

