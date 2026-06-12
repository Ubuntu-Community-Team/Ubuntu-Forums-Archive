---
title: "Best way to get portable Ubuntu on USB Drive?"
date: 2012-10-15
forum: Hardware
---

### Post by j814wong on 2012-10-15
What is the best method to put Ubuntu 12.04 on a USB Drive so that it can run on different computers yet also allow me to store data on it (persistence)?

---

### Post by Lyfang on 2012-10-15
I found this documentation: [LiveCD/Persistence - Community Ubuntu Documentation]("https://help.ubuntu.com/community/LiveCD/Persistence") and [LiveUsbPendrivePersistent - Ubuntu Wiki]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").

---

### Post by j814wong on 2012-10-15
I know of those, thanks.  But is there a method that is optimal in terms of performance?

---

### Post by Lyfang on 2012-10-16
Yes, with an ext4 filesystem without a journal, but that can cause problems. See also: [Ubuntu 10.04 & SSD TRIM]("http://ubuntuforums.org/showthread.php?t=2071826") and [SSD hårddisk med ext4 filsystem utan journal]("http://www.linuxportalen.se/forums/2011/01/27/ssd-h-rddisk-med-ext4-filsystem-utan-journal") (in Swedish)

---

### Post by oldfred on 2012-10-16
It depends on settings. 

Do not install any proprietary video drivers as that may conflict with another computer.

See also this thread:

[http://ubuntuforums.org/showthread.php?t=2071852](http://ubuntuforums.org/showthread.php?t=2071852)

---

### Post by j814wong on 2012-10-17
I think I'll go with C.S.Cameron's method here.   [http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

---

