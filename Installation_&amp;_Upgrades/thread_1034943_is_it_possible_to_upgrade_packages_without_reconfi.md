---
title: "is it possible to upgrade packages without reconfiguration?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2009-01-09
Good day!
I's a system administrator and I make unattended postinstall cd with necessary packages, updates, etc. Some upgrade packages, like 'console-setup' go interactive doing 'dpkg-reconfigure' after installation. I want installation to be completely automatic and do not want to reconfigure anything. Is there a chance to avoud reconfiguration on package upgrade? Thank you!

---

### Post by lemming465 on 2009-01-10
This should be possible if you [preseed the debconf answers]("http://blog.hjksolutions.com/articles/2007/07/27/unattended-package-installation-with-debian-and-ubuntu")

---

