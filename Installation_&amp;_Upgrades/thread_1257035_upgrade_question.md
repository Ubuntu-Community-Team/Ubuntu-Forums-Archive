---
title: "upgrade question"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by wildman4god on 2009-09-03
I have never had the opportunity to upgrade ubuntu using the update manager, I have heard that with ubuntu's default partitioning options (one for everything and one for swap) upgrading to the next version of ubuntu can seriously break your system. Is this true and if it is I have also heard that putting your home directory on a separate partition from root upgrading will then "be a enjoyable experience" can anyone confirm or deny this? and if it is true why doesn't ubuntu focus on fixing the upgrade process or change the default install so it puts the home directory on its own partition?

---

### Post by imhotep59 on 2009-09-03
Hello,

I have made several upgrades with Ubuntu (from 8.04 to 8.10 and from 8.10 to 9.04) and I had no problem.
To do this in a secure way, you can save your /home on an extrenal drive.

---

### Post by wojox on 2009-09-03
I've upgraded 8.10 to 9.04 no problem with everything on one partition. If you want to create a new partition for home this site is nice:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by snowpine on 2009-09-03
Hi Wildman, if you are *upgrading*, it does not matter whether you have a separate /home. It's a 99% chance the upgrade will go fine, but of course, all software has bugs, so there is a small chance something will go wrong.

If you are *reinstalling*, having a separate /home is very helpful... you can keep all your old user settings and documents. This is true whether you are reinstalling the old version or doing a fresh install of the new version. (I won't post instructions here because there are excellent tutorials elsewhere.)

Always backup your important data before doing a reinstall, major update, changing partition size, or anything else that could potentially go wrong. That's just common sense, regardless of whether you have a separate /home.

Hope that clears is up.

---

### Post by wildman4god on 2009-09-03
thanks

---

