---
title: "postinst hook script [update-grub] bug?"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by echo6 on 2009-06-28
I'm not sure if this is a bug in the postinst hook script for [update-grub].  Everytime I use apt-get postinst wants to update my grub and fails.  I have an encrypted swap partition which produces warnings, not sure if this is related.

```
Using mkinitramfs-kpkg to build the ramdisk.
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/mapper/sda6_crypt
                     UUID=9440f96a-08f0-4563-a2b6-53c7c41ed2c5
cryptsetup: WARNING: target sda6_crypt has a random key, skipped
```


```
User postinst hook script [update-grub] exited with value 20
dpkg: error processing linux-image-2.6.28.9-custom (--configure):
 subprocess post-installation script returned error exit status 128
```

---

### Post by echo6 on 2009-06-29
Any one? Even a pointer what I should be looking at to fix this?

DoH! apt-get purge nvidia-common appears to have resolved this issue.

---

### Post by echo6 on 2009-10-16
A new installation and I have the same error, only this time removing nvidia-common has not resolved it.

If I update-grub manually it completes with no errors.

I'm stumped on this because the errors produce no indication what the issue is and how to resolve it.

---

### Post by diesch on 2009-10-16
Please file a bug report. See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) if you don't know how to do this.

---

