---
title: "Upgrading to 9.10 or Re-install...."
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by Gausian on 2009-08-16
So, what's going to be the procedure for going from 9.04 to 9.10?

GRUB is going to GRUB 2.  Not a good idea to upgrade that i suppose.

Ext3 is going to Ext4 by default as well.  Cant imagine that would be pain free upgrading either.

How are you guys/gals planning to go from 9.04 to 9.10?

I think im going to start backing up files soon and do a full install of 9.10.

---

### Post by slakkie on 2009-08-16
The grub to grub2 migration is actually pretty (or surprisingly) easy. Just follow the steps mentioned [here](http://ubuntuforums.org/showthread.php?t=1195275), although the installer will guide you throw most parts with ease. 

As for ext4 vs ext3, I don't have an opinion on that yet, although I would like ext4 to mature a bit more before I run it, but that is just me. If you want ext4, you could migrate your current ext3 partition (no experience there, so no clue how easy/hard it is). 

If you want grub2 only upgrade. If you want grub2 + ext4, I think I would go for the clean install. That would be the only reason for me to actually clean install to go jaunty+1, because of ext4. 

But actually googling ext3 to ext4 shows me that converting ext3 to 4 is pretty easy:

[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)
[http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

I'm currently running Karmic, I broke my grub2 yesterday after playing with it. The migration from grub to grub2 went successful, but I was playing with some of the files and managed to break it. Restored my old Karmic image (thanks to clonezilla).

---

### Post by earthpigg on 2009-08-16
i do a clean install every 6 months regardless.

---

### Post by running_rabbit07 on 2009-08-16
Though Karmic does may do the EXT4 by default, it is backwards compatible and will work with EXT3.

---

