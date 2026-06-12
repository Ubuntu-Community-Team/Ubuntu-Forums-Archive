---
title: "Boot stall: Checking root filesystem status..."
date: 2008-11-03
forum: General Help
---

### Post by jwhendy on 2008-11-03
Hi,


I'm trying to compile kernel 2.6.27.4 and under several configurations, I'm getting a stall during boot progress for 30s-2min at whatever line is right before these two:
```

Testing root filesystem status: read-only filesystem
Remounting root device with read-write enabled

```

It appears at slightly different points in the boot message depending on my kernel config, but I have pinpointed that the stall is always right before them. The message prior to them stays on the screen alone, there is no progress for 30s-2min, and then those 2 lines appear and everything carries on as usual. I'm not ruling out other possibilities, but given that it's always these two lines that appear after the stall, I'm pretty sure that the problem has to do with them.

Lastly, the only posts I've found online about this message suggests problems with formatting, fstab, or other disk issues. The commonality is that they all show:
```

Testing root filesystem status: read-only filesystem
Checking root filesystem:
fsck 1.39 (29-May-2006)
Remounting root device with read-write enabled

```

I don't have the fsck lines in mine, just the first and last, so I don't think it's related to these other posts.

Hardware: White MacBook (not Pro) 2,1 (late 2006 model), Intel Core 2 Duo, 80GB SATA Atheros 5418 wireless, 2GB Ram, and Intel 950 Integrated graphics card.

Thoughts? I'm clueless. My root partition is only 15GB so I don't think it's just taking that long to check through it...

Thanks for the help.


-John

P.S. My dmesg: [http://jw.hendy.googlepages.com/dmesg](http://jw.hendy.googlepages.com/dmesg)

---

