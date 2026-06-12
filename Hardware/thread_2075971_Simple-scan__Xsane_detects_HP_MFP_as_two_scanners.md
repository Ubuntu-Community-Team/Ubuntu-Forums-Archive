---
title: "Simple-scan / Xsane detects HP MFP as two scanners"
date: 2012-10-25
forum: Hardware
---

### Post by Lexus45 on 2012-10-25
Hello all.

I noticed that  Simple-scan / Xsane in Ubuntu often detect Hewlett-Packard MFPs as two scanners.

Can anybody tell me, how one of them can be deleted ?

---

### Post by Lexus45 on 2012-10-25
Solved.
Commented out "hpaio" in /etc/sane.d/dll.d/hplip and last line (also "hpaio") in /etc/sane.d/dll.conf

---

