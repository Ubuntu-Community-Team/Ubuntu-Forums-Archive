---
title: "meta package for LAMP stack?"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by sdlinux on 2009-07-30
Is there a meta package for a LAMP stack? I have 9.04 desktop edition. I just want to have a home web server.

I found this tutorial [http://ubuntuforums.org/showthread.php?t=1171123&highlight=meta+package](http://ubuntuforums.org/showthread.php?t=1171123&highlight=meta+package), but it is not a meta package.

Also, is it okay to do this with the desktop edition or do I need the server edition?

Should I just use xampp for linux?

---

### Post by birdwin on 2009-07-30
Tasksel is good for this.

'sudo tasksel' -> select 'LAMP server'.

---

### Post by birdwin on 2009-07-31
> **sdlinux said:**
> Is there a meta package for a LAMP stack? I have 9.04 desktop edition. I just want to have a home web server.

I found this tutorial [http://ubuntuforums.org/showthread.php?t=1171123&highlight=meta+package](http://ubuntuforums.org/showthread.php?t=1171123&highlight=meta+package), but it is not a meta package.

Also, is it okay to do this with the desktop edition or do I need the server edition?

Should I just use xampp for linux?
You can run tasksel using either the Desktop or Server editions, and it's an even easier installation than XAMPP. All it asks for is the MySQL root password, and you're set.

---

### Post by sdlinux on 2009-08-02
Is there a security guide for setting up LAMP in ubuntu? I did tasksel, but I don't know what settings to change to make sure everything is secure.

---

