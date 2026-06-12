---
title: "Add SATA HD to Ubuntu system"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by grsing on 2006-05-28
I just wanted to know if anyone knows if there would be any problems adding an SATA HD to a system that already has 2 IDE HDs (mobo supports it I think, just wanted to make sure that Ubuntu wouldn't have any problems).  Running Breezy now, probably going to Dapper soon.

---

### Post by chrestomanci on 2006-05-28
[QUOTE=grsing]I just wanted to know if anyone knows if there would be any problems adding an SATA HD to a system that already has 2 IDE HDs (mobo supports it I think, just wanted to make sure that Ubuntu wouldn't have any problems).  Running Breezy now, probably going to Dapper soon.[/QUOTE]
My system is running from a SATA drive, so I don't think you will have a problem.

You do need to make sure that you are running a 2.6 series kernel, as the 2.4 series did not support SATA, (uname -a), but it is very likely you are.

Your new drive will appear as "/dev/sda", which may break any links you have setup to a USB stick, so you might have to edit your /etc/fstab to get USB storage to work again.

---

### Post by grsing on 2006-05-28
Cool, sounds good.  Editing fstab shouldn't be that hard.

---

