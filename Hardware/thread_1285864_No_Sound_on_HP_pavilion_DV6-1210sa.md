---
title: "No Sound on HP pavilion DV6-1210sa"
date: 2009-10-08
forum: Hardware
---

### Post by Woody1987 on 2009-10-08
I have no sound on my HP Pavilion DV6-1210sa. It works fine on Windows so its not a hardware problem.

```

lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

```

Its the first one (Azalia) i want to get working. Any help appreciated.

---

### Post by Woody1987 on 2009-10-09
Anyone?

---

### Post by modsaid on 2009-10-25
Same problem here.. on hp dv6 1280

> ~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

---

### Post by dv3500ea on 2009-10-25
See if the fix in [this thread ]("http://ubuntuforums.org/showthread.php?t=1258788")works for you.

---

