---
title: "[SOLVED] Run OS with Boot Magic?"
date: 2008-08-28
forum: General Help
---

### Post by azTom on 2008-08-28
Boot Magic works great for XP, BUT am unable to get Ubuntu to run or be recognized as an OS.  Boot Magic says just to direct BM to the operating partition.  Forget that it doesn't work.

Anyone running Ubuntu through Boot Magic?  If so just how were you able to add it to BM?

---

### Post by mb_webguy on 2008-08-28
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=155809").

---

### Post by phidia on 2008-08-28
There are methods for using the windows bootloader to boot linux. One HOWTO on doing that is [here]("http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why").
I don't know anything about boot magic but since it's designed for windows unless it specifically states linux support it probably doesn't.

---

### Post by azTom on 2008-08-28
It (BM) does support Linux.

---

### Post by azTom on 2008-09-03
Could never figure out that thread, am now able to boot to Ubuntu but not XP Pro.

---

### Post by azTom on 2008-09-17
Went with GRUB, after changing XP's address in GRUB all OK!

---

