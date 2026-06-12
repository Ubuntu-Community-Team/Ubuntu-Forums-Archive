---
title: "How can I probe for scsi devices?"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by dryder on 2008-04-19
Hi,

I tried using
sudo echo "scsi add-single-device 2 0 5 0" > /proc/scsi/scsi
to probe for a scanner that was not turned on when I booted. Howver, I get the message: 
bash: /proc/scsi/scsi: Permission denied

What am I doing wrong please and if that is not the correct syntax to probe can anybody tell me what it is please?

Many thanks
David

---

