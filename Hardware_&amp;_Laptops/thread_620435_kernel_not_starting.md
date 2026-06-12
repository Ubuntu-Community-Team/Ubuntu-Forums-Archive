---
title: "kernel not starting"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by travist120 on 2007-11-22
Here is what I get when I try to boot up into my kernel.

```

Starting up . . .
Loading, please wait . . .
/scripts/init-top/brltty: 19: grep: not found
Usage: mknod name {b|c|p} major minor
Usage: mknod name {b|c|p} major minor
svgalib: Cannot open /dev/mem
FATAL: Error inserting capability {/lib/modules/2.6.22-14-generic/kernel/security/capability.ko): Invalid argument
ALERT! /dev/disk/by-uuid/05f29f37-4ee1-4335-a86f-782a07d82a3b does not exist.
Dropping to a shell!
Check your root= boot argument (cat /proc/cmdline)
Check for missing modules (cat /proc/modules), or device files (ls /dev)
(initramfs)
```

---

### Post by Tweenk on 2007-11-22
My wild guess is that it looks like you have deleted grep, which is used in the init scripts. Some more info on when have you encountered this error would be helpful.

---

### Post by travist120 on 2007-11-25
I got this error by turning off my laptop incorrectly by holding the power button. Ubuntu froze, and I was impatient. I reinstalled after backing up all my data, but I would like to know how to fix this in the future.

---

