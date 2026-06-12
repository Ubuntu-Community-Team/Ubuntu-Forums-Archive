---
title: "Kernel Panic - not syncing: VFS"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by GeorgeOfTheBush on 2009-07-09
I was running Ubunu 9.04 2.6.28.13. The last run Ubuntu Update Manager corrupted something I guess, after a restart Ubuntu does not boot because of this error.

Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)

```

GeorgeOfTheBush@ubuntu:~$ dpkg --list | grep linux-image
ii  linux-image-2.6.28-11-generic              2.6.28-11.42                                            Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-13-generic              2.6.28-13.45                                            Linux kernel image for version 2.6.28 on x86
ii  linux-image-generic                        2.6.28.13.17                                            Generic Linux kernel image

```


But I am able to boot if I stop the linux boot sequence by pressing Escape and select 2.6.28.11.

Please let me know how I could fix the errors with 2.6.28.13.

Thanks.

---

