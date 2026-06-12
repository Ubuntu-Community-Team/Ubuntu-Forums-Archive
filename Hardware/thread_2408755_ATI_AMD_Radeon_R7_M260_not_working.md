---
title: "ATI AMD Radeon R7 M260 not working?"
date: 2018-12-22
forum: Hardware
---

### Post by mightyo8 on 2018-12-22
Hi,

I recently installed the latest release of ubuntu desktop (18.10) and my video card doesn't seem to work, I guess it has something to do with missing drivers. I've read something about recompiling the kernel that might solve the issue, but I'm a novice and still don't understand much about those kind of things. Is there an easy way to fix this problem?

Thanks in advance.

---

### Post by Yellow Pasque on 2018-12-22
> my video card doesn't seem to work
In what way? Be more specific.

> I guess it has something to do with missing drivers.
The correct driver should be installed by default. Most likely, you have a laptop with hybrid graphics (a low-power integrated GPU and the M260 for more intensive apps/games). If you want to run a program on the M260, you need to specify it with DRI_PRIME. Give the output of  these two commands:

```
glxinfo -B
DRI_PRIME=1 glxinfo -B
```

---

