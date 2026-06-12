---
title: "Can't acces USB devices after update"
date: 2008-10-19
forum: General Help
---

### Post by tjaf on 2008-10-19
I recently updated my system. I don't recall which packages were updated, but there were a lot of kde packages and also a new kernel (2.4.24-21). Ever since, I cannot access my usb devices, which were working perfectly before. If I insert a memory stick, this is recognized and I get an icon on the desktop, but double-clicking it yields an error "**isCallerPrivileged() failed**". Manually mounting with sudo works fine though. Something similar occurs with my digital camera. I can only access it running sudo digikam, which was not the case before.

Rebooting (as suggested in [_[COLOR="RoyalBlue"]Bug_257028[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/257028")) or reverting to the previous kernel (2.4.24-19) doesn't help.

Anybody experiencing the same problems? Tips/ideas?

---

### Post by tjaf on 2008-10-19
I found the problem. In order to get USB to work in Virtualbox (when I installed that over half a year ago), I had to comment out a section in /etc/init.d/mountdevsubfs.sh:

```
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devgid=1003,devmode=0666,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
```

Commenting these lines, solved my USB problem.

---

