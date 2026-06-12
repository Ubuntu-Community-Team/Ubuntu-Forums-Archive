---
title: "TRIM, Discard &amp; Fstrim --&gt; SSD"
date: 2012-07-26
forum: Hardware
---

### Post by WanchoPiskado on 2012-07-26
Hello!

So i have a question about discard in FSTAB and the fstrim command.
I have a laptop with OCZ Petrol 128 Gb installed with Ubuntu 12.04. I edited the FSTAB file and included the discard. I did the test and got the whole bunch of 0000000's to verify TRIM is enabled.

Now this.

With the discard in my FSTAB, my SSD should TRIM automatically right? But, when I run the:

sudo fstrim -v /

command in terminal, i still get:

/: 114228342784 bytes were trimmed

[Edit: It should be: '/: 0 bytes were trimmed', right?]

What gives?

---

### Post by WanchoPiskado on 2012-07-29
Got my answer here:

[http://forums.fedoraforum.org/showpost.php?p=1568303&postcount=2](http://forums.fedoraforum.org/showpost.php?p=1568303&postcount=2)

---

### Post by celsdogg on 2013-01-24
thanks for posting your resolution!

---

### Post by linuxnuube on 2013-03-27
two things folks need to know about SSD's

1, Never Ever intentionally write 0's to the drive.

2, there is no way to verify Trim is working, not with Hex editors, fancy tools etc etc..  if the drive supports it, the SATA controller supports it, and the controller's driver supports it and trim is enabled by the Operating System, then Trim should be functional.  In the big scheme of things Trim does very little anyhow.

Why the paranoia about trim?

---

