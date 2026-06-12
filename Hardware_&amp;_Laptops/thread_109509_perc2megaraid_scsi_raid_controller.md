---
title: "perc2/megaraid scsi raid controller"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by winnetou on 2005-12-28
I can't install ubuntu 5.10 on my PC with Dell Perc2 scsi raid
card (which actually is ami megaraid 467).
Even in expert mode, all 3 drivers with names "megaraid*" don't seem to work.
Any suggestions how to proceed ?
Thanks,
Dan

---

### Post by zagadka on 2006-07-23
I thought I'd reply as I've been having the same trouble making this gear work, with no reply. I see you are having the same trouble. I'm in the same boat. A poweredge 2400 with a PERC2/SC (LSI) SCSI RAID Controller + Backplane.

I think it's been the case for a while. I read somewhere the megaraid module breaks the new kernels. I've forgotten which version that started with, though it was the case with Breezy onward.

FC4 and FC5 don't like it either, even in expert modes.

I have hoary running on it with the following kernels:
2.6.10-10-5-386
2.6.11-1-686-smp
2.6.10-6-686-smp

The card is running the 3.13 (current as far as I am aware) firmware.

Any more info from anyone more knowledgeable on the subject would be terrific!


EDIT:
winnetou, if you are even still subscribed to this thread check this thread out for answers:
[http://ubuntuforums.org/showthread.php?p=1290340](http://ubuntuforums.org/showthread.php?p=1290340)

---

### Post by llbbl on 2006-07-28
> **winnetou said:**
> I can't install ubuntu 5.10 on my PC with Dell Perc2 scsi raid
card (which actually is ami megaraid 467).
Even in expert mode, all 3 drivers with names "megaraid*" don't seem to work.
Any suggestions how to proceed ?
Thanks,
Dan

You might try SUSE 10 (safe mode) or FreeBSD 6.1. I was able to get a PERC2 SCSI card to work using an Adaptec AIC-7889 controller. The only things that worked for me was Ubuntu 5.04 than I upgraded to ubuntu 5.10 and FreeBSD. I heard that SUSE 10 works for some people thou, (not me).

---

### Post by zagadka on 2006-07-30
My problem was mainly the loading of both megaraid modules. If you run the install with the noprobe option and choose all your drivers manually, it may work. But, choose only one; megaraid, not megaraid_mbox.

---

