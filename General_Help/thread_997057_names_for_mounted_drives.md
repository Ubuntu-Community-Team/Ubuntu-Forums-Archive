---
title: "names for mounted drives"
date: 2008-11-29
forum: General Help
---

### Post by chris_tikva on 2008-11-29
I've got a partition on my hard disk to mount into /media/ubunutu and up pops an icon on the desktop but it has an anonymous sounding description as "47.2GB media". It would be much nicer if it could have a chosen name. Is there a way of doing that?

When I plug in a usb drive and it automounts, some drives mount with a name regardless of which usb port is used, some mount to disk-n and are hard to find as they are different at different times.

Any way of simply allocating a name to a drive?

Thanks,

Chris

---

### Post by lswb on 2008-11-29
You can give a partition a label that the automounter will display. See the man page for tune2fs for details of the label name format and other capabilities of tune2fs. The command for example to name partition /dev/sda2 to "hardy" would be

sudo tune2fs -L "hardy" /dev/sda2

---

