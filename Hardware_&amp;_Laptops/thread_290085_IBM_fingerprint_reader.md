---
title: "IBM fingerprint reader"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by spotslayer on 2006-10-31
I have seen where several folks have gotten the fingerprint reader working but I have not had such good luck. Everything compiles fine, but when I run ./Sample the following error is returned. Does anyone have any ideas?

Vendor: UPEK, Inc.
Module ID: {5550454b2054464d2f45535320425350}
Device ID: 0x00000000
BioAPI_ModuleLoad failed, BioAPI Error Code: 6477 (0x194d)

David

---

### Post by hady on 2006-11-04
- try running the command as root: sudo ./Sample
- otherwise try uncommenting the line that starts with BioAPI_SetGUICallbacks

hope this helps...

---

### Post by spotslayer on 2006-11-04
Thank's hady for the reply, but I have already tried both of those options as well arunning ./Sample as root. I have followed all the instructions exactly. It seems like I must be missing something and I am still looking for ideas.

David

---

