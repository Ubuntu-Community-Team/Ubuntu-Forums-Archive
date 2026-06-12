---
title: "How to check the Linux partition on my old HD for errors"
date: 2010-08-24
forum: Hardware
---

### Post by Exp HP on 2010-08-24
After dropping my laptop, many problems popped up with my HD.  I ended up buying a new HD, and just recently I got a USB enclosure for my old HD so that I could transfer data.

Checking the Windows partition on it for errors was easy.  Right after plugging it in, Windows recognized it as an external HD and gave me a prompt to use CHKDSK.

As for my old Ubuntu partition... well...  I thought fsck would work.

```
mike@mike-lt-ub2:~$ fsck /media/5740932a-040f-43d0-90c8-c949bd364d9a
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Is a directory while trying to open /media/5740932a-040f-43d0-90c8-c949bd364d9a

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```I guess that old Ubuntu partition would be UFS, right?  If that's the case, it looks like I'm not supposed to use fsck for this.  So what should I do?

---

### Post by Exp HP on 2010-08-24
D'OH!

The moment I post it, I notice that ".ext2" was appended to "fsck" in the program output, apparently by default.

So the program I'm looking for is probably **fsck.ufs** from package **ufsutils**, right?


**Edit:** Or then again, maybe I'm going about this the wrong way, and I should be giving fsck something else (like the device's name in /dev)?  If so, where would I find that?

---

### Post by dabl on 2010-08-24
Smartmontools how-to:  [http://kubuntuforums.net/forums/index.php?topic=3097029.0](http://kubuntuforums.net/forums/index.php?topic=3097029.0)

The Parted Magic Live CD (or USB stick) has a GUI front end for smartmontools that makes it very easy, too.

In addition to smartmontools, here's a good suite of test tools:  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

