---
title: "Toshiba satellite webcam?"
date: 2010-02-18
forum: Hardware
---

### Post by pstrbrc on 2010-02-18
Machine: Toshiba Satellite
OS: Xubuntu 9.04
problem: I can't find, much less use, my built-in webcam. Is there a terminal command to tell me if my os "sees" my webcam? I don't find anything under {file system/dev/}.  I went ahead and added camorama, but it doesn't locate the webcam, either. It's looking for it at dev/video0. Help!

---

### Post by pstrbrc on 2010-02-20
Anybody? Help?

---

### Post by kr0b1t on 2010-02-20
Check that the web cam is attached to a device:
```
ls -l /dev/video*
```

You should be able to see video0 listed

To test that it is working properly, you most likely will like to install something as skype, but an easy way to double check is using luvcview

```

# luvcview &

```

This works for me , using Ubuntu 9.10 64 bits in a Toshiba Satellite A500-01x

---

### Post by pstrbrc on 2010-02-20
Thanks! That helps.

---

