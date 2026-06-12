---
title: "Update ISO for all updates"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by KayakJim on 2009-10-05
Is it possible to update an Ubuntu release .iso to contain all of the updates released since the .iso was created?

This is similar to slipstreaming a service pack with a Windows XP install.

---

### Post by orange-wedge on 2009-10-06
I think this might be what you are looking for:

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

Its not fun.

---

### Post by slakkie on 2009-10-06
Do a netinstall. See [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You have a 10MB image, you boot from it, it installs some packages then downloads the rest from the web and you are done. No further updating required after installation.

LTS releases do have point releases where a new ISO is generated at such a point release. So downloading 8.04.3 ISO is the same as installing 8.04 from the release date + all updates up to point release 3.

---

