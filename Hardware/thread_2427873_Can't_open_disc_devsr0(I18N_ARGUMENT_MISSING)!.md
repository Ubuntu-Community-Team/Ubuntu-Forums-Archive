---
title: "Can't open disc /dev/sr0(I18N_ARGUMENT_MISSING)!"
date: 2019-09-26
forum: Hardware
---

### Post by goemonburo on 2019-09-26
I have an ongoing problem when trying to access my dvds.  I am on Lubuntu 18.04LTS.  This error message keeps popping up:

Can't open disc /dev/sr0(I18N_ARGUMENT_MISSING)!

Sometimes this is resolvable by opening and closing the DVD drive.  Other times, I have to entirely shut down the system and reboot for this to resolve.  It's maddening, and I have scoured the internet for answers but haven't found much.  Am I the only one with this issue?!

It's NOT the DVD itself, at least, not often.  In rare cases this same message pops up when a DVD is damaged.  But usually, after repeated attempts to get it to work, I shut down the system (which I hate doing, Linux shouldn't need that!) and reboot and bingo, that solves it.

I would love to know what is causing this and how to resolve it without rebooting.  Anyone know?

---

### Post by #&amp;thj^% on 2019-09-26
Give this a try:
```
sudo ln -s /dev/sr0 /dev/dvd
```

---

### Post by goemonburo on 2019-09-27
Thanks, @1fallen.  I am seeing "....dvd -> sr0" when I look at what's already in /dev, so I don't think that's the issue.  Also, if it needed that symlink, wouldn't it fail consistently?  

I suspect (anyone know more about this than I do?) it might be due to automounting?  Or maybe a program is not releasing the DVD when I'm done, preventing new DVDs from being read/accessed?

Otherwise why would it work fine after reboot...then fail?

---

### Post by #&amp;thj^% on 2019-09-27
Had the same problem as you, and that fixed it on 16.04. (With Automount)
I Just ran the command on my system with NO ill effects.
Is there a lock in play?
```
hdparm -L 0 /dev/sr0

```
will remove that lock.
Also when this happens, will this work?:
```
sudo eject /dev/sr0
```

---

