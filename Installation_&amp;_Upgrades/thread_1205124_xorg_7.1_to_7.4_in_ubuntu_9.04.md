---
title: "xorg 7.1 to 7.4 in ubuntu 9.04"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by shoutbox on 2009-07-05
I was wondering how to accomplish this. Ati drivers require this version of xorg.

Would someone know a suitable repository?
Is there deb packages available?

Is compiling the only option?

Thnx.

---

### Post by Mark Phelps on 2009-07-07
> **shoutbox said:**
> Is compiling the only option?Thnx.

Quick answer -- yes.  You would have to download all the source and libraries and compile your own Xserver.

But ... before you do that, make sure that your model ATI card/chipset actually works with the current AMD/ATI drivers.  If you have a non-HD card/chipset, or an HD series earlier than the 3x series, you're wasting your time as the current restricted drivers don't support them anyway.

---

### Post by shoutbox on 2009-07-07
thnx for the reply!

I also figured out that the drivers didn't get along with the server kernel.

---

