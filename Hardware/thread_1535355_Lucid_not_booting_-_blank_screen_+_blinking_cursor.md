---
title: "Lucid not booting - blank screen + blinking cursor"
date: 2010-07-20
forum: Hardware
---

### Post by pritchard92 on 2010-07-20
I use(d) on an old Dell laptop really quite succesfully.

However, I boot it up this morning, but it doesn't boot properly - just stuck at a blank screen with no signs of hard drive activity.

I had to wait until after work today to work on it. I've tried reinstalling grub from LiveCD, but it mentions an error to do with embedding, mentioning that I must use blocklists?

Any help would be greatly appreciated.

---

### Post by pritchard92 on 2010-07-21
Spark of Hope!

Managed to boot into my installed environment via the UBCD disk. After this, i attempted to execute: ```
sudo grub-install /dev/sda
```

However, I was confronted with the same error as before, when I tried this whilest chrooted in from the LiveCD - 

>                             ~
/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


Hope this shed a little more light on the problem. And again, any feedback would be greatly appreciated.

---

