---
title: "Resume from SD-Card fails"
date: 2012-02-06
forum: Hardware
---

### Post by OLFDB on 2012-02-06
Hi,

I'm a newbie with Ubuntu, working with SuSE at the job and now installed a Lubuntu 10.04 on my EEEPC 701.

I have a problem with resuming from the Swap partition located on an SD card in the EEEPC.  At the time the resume should take place, the /dev/sdb has not been mounted by the kernel.

The dmesg shows it is being detected and mounted right after the failed resume.

How can I delay the resume operation, or make it depending on the availability of the /dev/sdb ?

Best Regards

Olaf

---

