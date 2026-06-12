---
title: "Can't Upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Bbman90 on 2009-11-02
I was trying to upgrade to 9.10 but I needed more space in \var. I deleted the contents of the cache folder to save space. Apparently that was a bad idea because now I can't upgrade at all. Here's the output from the terminal:

```

brandon@brandon-laptop:~$ sudo apt-get dist-upgrade
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```

Of course it can't find or write to anything, I deleted it! Help?

---

### Post by Bbman90 on 2009-11-03
I hate to bump this, but it's been 16 hours and I really need help.

---

### Post by wilee-nilee on 2009-11-03
The general advice is a clean install of Karmic. If you don't have a way to back up the home or put it on another partition. Even if you get an answer to upgrade could still lose you important data, and even if the update works you will still be in ext3, which shouldn't be upgraded to ext4v without a backup. Be careful not to let your want of 9.10 override the logic in making sure you don't lose stuff, and get the benefits of a clean install of this version. You should make sure as well that it runs on a live CD as well.

---

### Post by Bbman90 on 2009-11-03
My home is a separate partition, that's not the issue. I need to know how to get my cache files back, or have everything work fine without them.

---

