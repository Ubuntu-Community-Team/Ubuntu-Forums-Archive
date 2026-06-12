---
title: "cryptsetup map doesn't stick"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by jsgarvin on 2009-10-06
I've got an encrypted partition that I have setup to auto mount on login with pam-mount when I boot into Hardy.  I did a fresh install of Karmic and I can't get the mapping to the encrypted partition to stick, so it won't automount on login.

When I run ```
sudo cryptsetup luksOpen /dev/sda3 sda3
```, this creates a /dev/mapper/sda3 entry that I can mount. I only ever ran this once in my Hardy install and the /dev/mapper/sda3 entry stays there from boot to boot (still there even now and working fine).  However, when I run this in Karmic, and then reboot, the entry disappears and I have to manually re-run the command to get it back.

Anybody have any idea what's going on?

---

### Post by jsgarvin on 2009-10-06
bump

---

