---
title: "USB install??"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by shalamabobbi on 2009-01-19
I have XP with ntfs on my internal drive. I'm afraid to attempt an install of ubuntu to share that drive. Can it be installed to a usb 8Gb thumbdrive and add programs etc to that? Or can it be installed to an external usb hard drive? In the latter would I have to boot from the CD drive with a live CD then add programs to the external drive? My bios doesn't support usb booting I don't think.

---

### Post by ssorc on 2009-01-19
If you don't want to do a full installation on the XP drive, consider [WUBI]("http://wubi-installer.org/") - it is easy to install and remove, and will not affect your partitions etc.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by blackened on 2009-01-19
> **ssorc said:**
> If you don't want to do a full installation on the XP drive, consider [WUBI]("http://wubi-installer.org/") - it is easy to install and remove, and will not affect your partitions etc.

[http://wubi-installer.org/](http://wubi-installer.org/)

In order to do what you're asking (boot from usb with persitence), you would have to create the usb installation from within an existing Ubuntu install. As mentioned, Wubi is the better solution in your case.

---

### Post by vanadium on 2009-01-19
An normal dual boot installation is far more robust and reliable. In your situation, you would need no more than 10 GB of free space: you can easily keep all your user data on the Windows partition and access it quickly and safely from within your Ubuntu home using links.

---

