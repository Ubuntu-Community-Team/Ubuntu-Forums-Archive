---
title: "[SOLVED] GRUB Error 17 after LiveCD Freeze while mounting"
date: 2008-08-11
forum: General Help
---

### Post by DeathOnJuice on 2008-08-11
SOLVED!
Well, I figured this would be pushed off the front page too quickly to get any answers, and I knew that the issue was a corrupted filesystem... So I took the plunge and did a fsck -t ext3 /dev/sda1. After a bit of waiting, I was greeted with a prompt to fix an error. I pressed enter, hoping to bypass it, but it took that as a yes. Another error came up, and I decided that if I had been wrong to start fixing them, I had probably already screwed something up. So I put a CD on enter and went away for a few minutes as thousands of errors were fixed. My experimental/stupid side decided to hit one no, but it's OK (at the end, it said errors remained. I'm guessing that's what caused the next sentence). When I restarted, the Ubuntu splash screen came up, and it did another fsck. It fixed more error(s), probably the one I said not to fix earlier, restarted one more time, and booted into Ubuntu!

I was trying to mount my main system/data partition on a LiveCD, when it froze. This had happened several times before, and the only solution seemed to be a hard reset.

This time, after booting into the LiveCD, no 160GB Media showed up in the Places menu. When I reset, GRUB gave error 17 before even giving the option to press Esc to see the menu. Mount asks for the file system type, and GParted shows that this filesystem is of an unknown type.

Any ideas for what to do? I had a lot of un-backed-up data on that drive that I would hate to lose... Please help. Whether it becomes bootable or just has recoverable data, I will be happy. I'm guessing that I should try a fsck -t ext3 /dev/sda1 first, but I'm treading carefully.

More info:
```

/dev/sda1: Formally root and ext3 (146GB)
/dev/sda2: Extended (3GB)
    /dev/sda5: Swap (3GB)

sudo fdisk -l:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

```

EDIT: I found this topic ( [http://ubuntuforums.org/archive/index.php/t-5134.html](http://ubuntuforums.org/archive/index.php/t-5134.html) ) with the suggestion to do a: sudo e2fsck -b 32768 /dev/hda2

However, that's ext2. I'm pretty sure mine was ext3 (it was just whatever Ubuntu picks as default), so should I possibly try that exact command but with e3fsck instead of e2?

Thanks so much!

---

### Post by DeathOnJuice on 2008-08-11
Solved, for the record. See the first post for an explanation.

---

