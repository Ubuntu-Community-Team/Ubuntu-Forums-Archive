---
title: "Failed to unmount usbdrive Bug"
date: 2009-02-15
forum: Hardware
---

### Post by ridetheteapot on 2009-02-15
I have a sansa fuze (msc mode mp3 player), its volume id is 'SANSA FUZE' and always automounts to /media/SANSA FUZE
If i don't unmount manually before shutdown i will get an error cannot unmount /dev/SANSA20FUZE
It's not handling spaces correctly in this instance

easy fix is change volume id, or mount point, but just thought i'd throw this out there.

---

### Post by Kevbert on 2009-02-15
Spaces are bad news for file and directory names.
In your example mount could be written as /dev/SANSA\ FUSE or /dev/"SANSA FUSE" in order to cope with the space.

---

### Post by ridetheteapot on 2009-02-15
its an automount issue, no problem to mount or unmount manually in bash or through nautilus. (!)

there is a workaround to not uses spaces in vol id's but i still think its broken functionality

---

