---
title: "Why do some modules disobey the blacklist file?"
date: 2008-10-07
forum: General Help
---

### Post by pytheas22 on 2008-10-07
Most of the time, when you want the system to ignore a module, you can simply add it to your /etc/modprobe.d/blacklist file and it will no longer be loaded.  However, I've noticed a few situations where certain modules seem to disobey the blacklist file.

The most common example (well known to those of us who try to provide support in the networking subforum) is where a user wants to blacklist the b43 and ssb modules in order to use a different wireless driver for his or her Broadcom card.  Usually this works, but on machines which also have a Broadcom-based ethernet card using the b44 driver, ssb will continue to load even if it's on the blacklist.

More confusing, even if b44 itself is placed on the blacklist along with ssb and b43, b44 (and consequently ssb) continues to load no matter what.  The only way to remove b44 on Hardy seems to be to write a boot script.

I'm wondering if anyone familiar with the underlying workings of the kernel can explain this behavior.  It causes a lot of confusion for new users who want to use alternative wireless drivers for Broadcom cards.  It's also dumb that we have to manually rmmod b44 (thereby breaking ethernet) in order to get wireless working.

I know how to work around all of these issues, but I've just always been curious as to why the blacklist doesn't always do what it's supposed to, and whether there's a logical reason behind it or a flaw in the design of modprobe/blacklist.

---

### Post by frenkel on 2008-10-16
I have the same problem. The weirdest thing is it loads modules I don't need, like cpufreq_ondemand and it ignores the blacklist.

---

