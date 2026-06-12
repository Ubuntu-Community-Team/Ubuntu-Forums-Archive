---
title: "libc segfaults after upgrade to 9.10"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2009-11-12
I started to get the same segfault in various processes seemingly at random when upgrading to 9.10.

For example:
kernel: [ 2891.050533] evolution-data-[6390]: segfault at a ip b6bac9fb sp b5afec50 error 4 in libc-2.10.1.so[b6b3f000+13e000]

or

glxinfo[6991]: segfault at bf8ad000 ip b76a4006 sp bf8a2d28 error 6 in libc-2.10.1.so[b762f000+13e000]

Sometimes it totally freezes my computer, sometimes it still works after this.

Do I have a hardware problem? Does anyone else have this?
And what is located at libc-2.10.1.so+13e000?

---

