---
title: "EXT4 or Reiser?"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by oboedad55 on 2009-08-01
I was wondering if anyone had an opinion of the advantages of one filesystem over the other. I just installed Ubuntu 9.04 with ext4 and it seems pretty zippy, booting up in about 10 seconds. I normally use Reiser but would appreciate any thoughts.

Cheers,

---

### Post by Arup on 2009-08-01
Sadly due to circumstances Reiser is now officially dead due to the incarceration of its dev, ext4 is your best bet.

---

### Post by x33a on 2009-08-01
i haven't tried reiser, but have been using ext4 since jaunty came out. it is pretty stable (at least for me), and i am really satisfied with it.

---

### Post by ridetheteapot on 2009-08-01
i've been using reiser for a couple years now, its pretty quick and has much lower overhead then ext4

as arup said its pretty much dead. namesys's website is down. but i didnt know reiser4 was officially dead now.

ext4 is backwards compatible? if so go for it. there are so many tried and true ext2 tools.

but watch btrfs in the future.

--- edit---

forgot to mention the nasty down side for reiserfs. repairing, you want a backup. plus a full fsck check can take soooo long.

---

### Post by davidogg on 2010-08-11
> **Arup said:**
> Sadly due to circumstances Reiser is now officially dead due to the incarceration of its dev, ext4 is your best bet.

Only one of it's devs is incarcerated, Ed is still maintaining patches.
[http://www.kernel.org/pub/linux/kernel/people/edward/reiser4/reiser4-for-2.6/](http://www.kernel.org/pub/linux/kernel/people/edward/reiser4/reiser4-for-2.6/)

---

### Post by kerry_s on 2010-08-11
old thread. ;)

---

