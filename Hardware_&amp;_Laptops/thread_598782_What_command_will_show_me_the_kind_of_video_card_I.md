---
title: "What command will show me the kind of video card I have in my PC?"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-10-31
I am trying to help someone get Compiz Fusion up and running on their PC.  All we know about the video card is that it's an nVidia, which is using the restricted drivers that were automatically installed when ubuntu 7.10 was installed.  For some reason though, it won't allow him to enable compiz via Appearance>Visual Effects.  So I'm trying to narrow down the cause of the problem by determining if the video card is or isn't supported.

Thanks for the help!

---

### Post by Wicca on 2007-10-31
Hello,

Try:

```
lshw -C display
```

Good luck.

---

