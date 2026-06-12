---
title: "(Yet another) Asus laptop suspend problem with Karmic"
date: 2009-11-28
forum: Hardware
---

### Post by zadehas on 2009-11-28
Hello,
I know there are already plenty of suspend issues threads, but I think my problem is different and I was unable to find any other similar reports on the forums.

I run Kubuntu 9.10 karmic on a Asus X50GL notebook (nvidia 8200M video), after upgrading from 9.04. Suspend to ram worked just great with 9.04, using 2.6.29 kernel. After upgrading however, the following started to happen:

1. Turn on computer;
2. Put computer to sleep - works perfectly;
3. Resume computer - no problem;
4. Put computer to sleep again - it works, but after about 1 sec it comes out of suspend without any apparent reason. The os is fully operational (no freeze or graphics / wireless problems)

So it seems I can only suspend to ram once after booting.
I tried reverting to the old kernel - no luck. I tried upgrading to the newest nvidia driver - no effect. I tried newer kernels - it got worse, seems some future kernels have regressed to not having support for my acpi keys...

My hope is that there is a really simple fix for this that somebody with a better knowledge of the os will be kind enough to provide me with (like unloading a module, a boot option. etc), as the suspend process does actually seem to work.

Thank you!

---

### Post by DLGandalf on 2009-12-29
I have a same problem with a desktop board having a nvidia geforce 8300.

Many bugs in the past with suspend working only once, seem to have a common profile due to a nvidia gfx card. But no real solutions :(

---

### Post by zadehas on 2010-01-08
Latest kernel upgrade from 2.6.31-16 to 2.6.31-17 seems to have solved it. Hopefully there will be no regressions when the next release arrives.

---

