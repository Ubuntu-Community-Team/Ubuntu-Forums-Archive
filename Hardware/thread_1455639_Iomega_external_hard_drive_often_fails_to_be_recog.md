---
title: "Iomega external hard drive often fails to be recognized by the OS"
date: 2010-04-16
forum: Hardware
---

### Post by meanburrito920 on 2010-04-16
I've noticed recently that whenever I plug my Iomega external drive into my  computer, it often will not immediately recognize that the drive has been attached. 

On most occasions, I will have to run "sudo fdisk -l" or "sudo lshw -class disk" in order for the disk to be recognized. Both these methods will fail sometimes and claim that the device is not attached. Only by running them repeatedly can I get them to see the HD. Furthermore, they often hang while attempting to read from the external HD.

I have fsck'd the external HD and there appears to be nothing wrong with it. I have attempted to connect it using other cables, and that has no effect. I have another external Iomega (which is a few years older) which recognizes almost immediately after being plugged in.

Can anyone possibly shed any light on this issue? I would really appreciate it.

---

