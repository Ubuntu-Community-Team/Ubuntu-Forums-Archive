---
title: "After laptop Natty upgrade display turns off during boot"
date: 2011-04-03
forum: Hardware
---

### Post by anypundit on 2011-04-03
I upgraded my Acer Aspire laptop to 11.04 beta 1, and now my display shuts off right after displaying the "ureadahead terminated" message.  I've tried acpi=off, noapic, and noapm.  I can boot all the way to Unity just fine if I choose the old kernel in grub2.

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

```

Edit: This is a duplicate of [http://ubuntuforums.org/showthread.php?p=10635480#post10635480](http://ubuntuforums.org/showthread.php?p=10635480#post10635480)
Fixed with the patch provided at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611)
Now my screen only goes blank for 30 seconds during boot.

---

