---
title: "Cannot mount volume."
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by michaelfougnie on 2008-03-12
I have Windows Vista, which is an upgrade from XP, one one hard disk, and Ubuntu on another. I mostly use Ubuntu, but sometimes I use Vista for stuff. My external hard disk, which I use for media, wont mount sometimes, and I have to switch out the internals and load Vista. When I switch back, it works. What is this problem?

---

### Post by prshah on 2008-03-12
> **michaelfougnie said:**
> I have Windows Vista, which is an upgrade from XP, one one hard disk, and Ubuntu on another. I mostly use Ubuntu, but sometimes I use Vista for stuff. My external hard disk, which I use for media, wont mount sometimes, and I have to switch out the internals and load Vista. When I switch back, it works. What is this problem?

From Windows, if you hot-unplub the USB device (remove without using the "Safely remove device"), the ntfs partitions will be marked dirty and Ubuntu will not mount them.

You can use the --force switch to mount them anyway but THIS IS NOT RECOMMENDED.

```
dmesg | grep -i dirty
``` will tell you if this is actually the problem.

Cheers,
PRShah

---

