---
title: "Give a non-root user access to USB device"
date: 2015-03-16
forum: Hardware
---

### Post by actionmystique on 2015-03-16
_**Ubuntu 14.10**_

I cannot access an external USB SSD as a normal user belonging to group "samsung-ext4" (access as root is OK), despite a udev rule defined in /etc/udev/rules.d:

_**30-usb-devices.rules**_
```
# Granting access to USB Samsung-Ext4 to all the group samsung-ext4
SUBSYSTEM=="usb", ATTR{idVendor}=="174c", ATTR{idProduct}=="55aa", MODE="0666", GROUP="samsung-ext4"
```

Any advice to make it work?

---

### Post by ajgreeny on 2015-03-16
It looks as if the USB is partitioned with an ext4 filesystem which means that you probably need to change the permissions of the mountpoint as well as having that udev rule, about which I admit I know almost nothing.

I have a USB drive partitioned with a single ext3 partition on it.  The partition was made (as root) and then I used a chown command to make the mountpoint belong to me as a normal user, so, of course, I can read and write to it.  When it is plugged in to my wife's computer she can also read and write to it as user, using her own username, not mine, so I imagine the user is identified by using a UID of 1000, not the actual name.

Perhaps your situation is different as the users (on the same machine?) will all have different UIDs, in which case your addition of all users to the samsung-ext4 group, and making sure the mountpoint is read/write for that group should do the trick.

---

### Post by actionmystique on 2015-03-17
> [COLOR=#000000]change the permissions of the mountpoint[/COLOR]

Thanks, that was enough to solve it.

---

### Post by ajgreeny on 2015-03-17
Great!

PKLease mark as SOLVED from the Thread Tools menu at the top of the thread.

---

