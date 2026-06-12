---
title: "Ubuntu 6.10 on Dell C400"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by tempest130 on 2006-11-16
Hi everybody,

I have a fresh install of Edgy on my Dell Latitude C400 laptop.  I am working on setting up suspend/resume on the laptop.  The suspend works with no problems.  However when I try to resume (ie open the lid), I am taken back to the login screen. It's as if I typed CTRL-ALT-BACKSPACE to restart the xserver.  Can help anyone provide some advice as to how I could being to troubleshoot this?  The drive used in my xorg.conf file is 'i810'. I am using ACPI for power management.  Thanks.

Sean

---

### Post by petit_prince on 2007-01-10
See if the fixed xserver-xorg-core Package does the job:
[https://launchpad.net/ubuntu/+source/xorg-server/+bug/61746](https://launchpad.net/ubuntu/+source/xorg-server/+bug/61746)

---

