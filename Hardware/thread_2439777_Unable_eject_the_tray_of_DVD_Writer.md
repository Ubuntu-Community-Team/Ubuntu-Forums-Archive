---
title: "Unable eject the tray of DVD Writer"
date: 2020-04-01
forum: Hardware
---

### Post by satimis on 2020-04-01
Hi,

Ubuntu 18.04

I have a spare PC having an old DVD writer which hasn't been used for long time.  Just discovered that I couldn't eject the tray manually.  The LED green light was on for a while.

Then on Terminal running following commands
$ eject```

eject: unable to eject, last error: Inappropriate ioctl for device

```
$ sudo eject```

eject: unable to eject, last error: Inappropriate ioctl for device

```
$ sudo eject /dev/sr0```

eject: unable to eject, last error: Inappropriate ioctl for device

```
$ sudo eject -i off```

CD-Drive may be ejected with device button

```

Non of them can work.

Please advise how to fix the problem.  Thanks

Regards
satimis

---

### Post by CatKiller on 2020-04-01
There should be a teeny tiny hole in the front of the drive that you can poke an unfolded paperclip into for just that situation.

---

### Post by satimis on 2020-04-01
> **CatKiller said:**
> There should be a teeny tiny hole in the front of the drive that you can poke an unfolded paperclip into for just that situation.
Hi,

Thanks for your advice.

I have tried your suggestion before posting. Also it didn't work.  The green LED was on a while.  I heard some noisy inside.

This trick worked for me in the past

Regards
satimis

---

### Post by CatKiller on 2020-04-01
In that case: new DVD writers are cheap. It's not responding to commands, and you're unable to use the hardware override. I hope there wasn't anything important inside.

---

### Post by Yellow Pasque on 2020-04-01
If you can't use a paper clip, the tray is probably broken. If you have a disc in there, you may be able to open the drive by taking the cover off. Heck, you might even find a simple fix like removing an object/disc that is jammed in there. I wouldn't get my hopes up, but if you're going to toss/recycle the drive anyway, there's little to lose by digging into it. It's a learning experience if nothing else.

---

### Post by satimis on 2020-04-01
Hi all,

Your comment agreed.  Today the price of an internal DVD writer is very cheap.  It is only for curiosity to continue.   Maybe I'll dismantle it to check, trying to learn something.

satimis

---

