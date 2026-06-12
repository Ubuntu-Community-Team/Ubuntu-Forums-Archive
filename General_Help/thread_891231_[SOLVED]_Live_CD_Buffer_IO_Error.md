---
title: "[SOLVED] Live CD Buffer I/O Error"
date: 2008-08-15
forum: General Help
---

### Post by TreeFinger on 2008-08-15
I am attempting to run the Live! CD from ubuntu-8.04.1-desktop-amd64.iso

I first did the disc integrity check and was getting errors..

```

XXX.XXXXXX Buffer I/O Error on fd0

```

where X is an integer.

I then tried to boot onto the Live! Desktop and was receiving the same errors. Did I burn a bad disc?

I'm running an Intel Q6600 Processor.. Did I download the wrong iso?

md5check sum is good.


---edit

To solve this problem I did like someone suggested in a post below. Disabled my floppy drive in bios

---

### Post by TreeFinger on 2008-08-15
bump

---

### Post by TreeFinger on 2008-08-16
bump

---

### Post by todak on 2008-08-16
More than likely your disc burn was bad. Try to burn again, possibly with a different brand of media.

---

### Post by TreeFinger on 2008-08-16
> **todak said:**
> More than likely your disc burn was bad. Try to burn again, possibly with a different brand of media.

I have burnt an ubuntu live CD with this media before but I will try burning another one.

---

### Post by cariboo on 2008-08-16
You are getting:

> Buffer I/O Error on fd0

because you don't have a floppy drive installed, and it is probably still enabled in your bios. You can ignore that error. Your boot problem is probably something else. Have you tried booting in safe graphics mode? to do this, at the menu hit F4 and select safe graphics mode and hit enter. this should get you going.

Jim

---

