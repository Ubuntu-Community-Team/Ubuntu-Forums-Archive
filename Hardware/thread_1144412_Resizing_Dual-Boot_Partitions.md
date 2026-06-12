---
title: "Resizing Dual-Boot Partitions"
date: 2009-04-30
forum: Hardware
---

### Post by iamshawnrice on 2009-04-30
Hi.

I am running Ubuntu 8.10 AND Win XP on a laptop.

I currently have 30 GB devoted to Windows and 80 GB to Ubuntu.
I want to allocate more space to Windows for video editing purposes.
Linux was installed prior to windows.

Is this possible without having to reinstall either OS?

---

### Post by CMJ Tech on 2009-04-30
You may be able to accomplish this with GParted:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

 I suggest backing up everything important before you make any changes.

---

### Post by dmaxel on 2009-04-30
Correct me if I'm wrong, but you could **resize** the Linux partition using gparted, and then use a 3rd party application to resize the Windows partition. Resizing would prevent data loss. It would be best to resize inside Windows as resizing Windows with gparted gives a higher risk of data loss.

---

