---
title: "New install verses upgrade"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by DavidFourer on 2009-06-01
I've been upgrading Ubuntu on my home computer every six months since Breezy Badger.  Are there benefits to doing a new install at some point?  This is a pretty boring setup, pretty much the way it comes out of the box.  A few apps would have to be re-installed.  One thing that needs help is multi-media applications, where there are many choices and none work well.  I've been backing up my photos, bookmarks, addressbook, and other files to a USB stick.  This is a single-boot setup.  It's my only computer, a Dell notebook.  I use it for Internet, mail, watching DVD's, FTP, and GIMP

Thanks

---

### Post by apjone on 2009-06-01
Take a look @ [http://ubuntuforums.org/showthread.php?t=514049](http://ubuntuforums.org/showthread.php?t=514049) there are also other threads like this in the The Community Cafe of this forum

---

### Post by Mark Phelps on 2009-06-02
Everyone's approach is different, but the one I've been using is to have two physical drives, each containing a different version of Ubuntu -- the most current, and the prior one.

When a new version comes along, I wipe the oldest version and install the new one over the top of it.

This allows me some options that an upgrade or clean install don't easily provide, as follows:
1) If the new install is a disaster, I have a working version to still use
2) After installing all my apps, I still have the configuration files contained in the old OS and can often get all the apps configured simply by copying those files over to the new OS
3) With a clean install, don't have to worry about "cruft" lying around from my relentless hacking of the older version
4) Can take my time customizing the new version because I still have a working version to use on a day-to-day basis
5) Once the new version is customized, I just switch the boot defaults in the menu.lst file and use that version from then on.

If there was a simple, one-click method of doing "rollback", I'd probably not use this approach, but until that exists, I'll continue doing it this way.

---

### Post by presence1960 on 2009-06-02
Pretty good approach Mark. Based on what I have been reading on the forum lately it seems a lot who opted to upgrade to Jaunty are experiencing a lot of problems. For whatever reason the upgrade process to Jaunty is missing the mark. I also keep 2 versions so if something happens I have one to fall back on.

---

### Post by raymondh on 2009-06-02
> **Mark Phelps said:**
> Everyone's approach is different, but the one I've been using is to have two physical drives, each containing a different version of Ubuntu -- the most current, and the prior one.

When a new version comes along, I wipe the oldest version and install the new one over the top of it.

This allows me some options that an upgrade or clean install don't easily provide, as follows:
1) If the new install is a disaster, I have a working version to still use
2) After installing all my apps, I still have the configuration files contained in the old OS and can often get all the apps configured simply by copying those files over to the new OS
3) With a clean install, don't have to worry about "cruft" lying around from my relentless hacking of the older version
4) Can take my time customizing the new version because I still have a working version to use on a day-to-day basis
5) Once the new version is customized, I just switch the boot defaults in the menu.lst file and use that version from then on.

If there was a simple, one-click method of doing "rollback", I'd probably not use this approach, but until that exists, I'll continue doing it this way.

+1 on this method

---

### Post by Sef on 2009-06-02
> When a new version comes along, I wipe the oldest version and install the new one over the top of it.

This allows me some options that an upgrade or clean install don't easily provide, as follows:
1) If the new install is a disaster, I have a working version to still use
2) After installing all my apps, I still have the configuration files contained in the old OS and can often get all the apps configured simply by copying those files over to the new OS
3) With a clean install, don't have to worry about "cruft" lying around from my relentless hacking of the older version
4) Can take my time customizing the new version because I still have a working version to use on a day-to-day basis
5) Once the new version is customized, I just switch the boot defaults in the menu.lst file and use that version from then on.


I have thought building a computer with two hard drives and do exactly that.

---

