---
title: "Too scared to upgrade to Karmic (file corruption)"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by jkounis on 2009-10-30
I was excited when it was announced that Karmic is "ready for prime time." Fortunately, I read the install before upgrading my production system. About 2/3 of the way down, buried in "Other known issues" between a note about needing to update grub if I'm using ext4 and a cautionary note about Ubuntu One is:

> Possible corruption of large files with ext4 filesystem

There have been some reports of data corruption with fresh (not upgraded) ext4 file systems using the Ubuntu 9.10 kernel when writing to large files (over 512MB). The issue is under investigation, and if confirmed will be resolved in a post-release update. Users who routinely manipulate large files may want to consider using ext3 file systems until this issue is resolved. (453579)

YIKES!

Was Ubuntu 9.10 really ready to go from Beta to "production", or did it just happen because the date on the calendar said it was time?

How commonly is this bug encountered? ext4 is the default file system for Karmic, and I can't believe that it could trash any file over 512 MB.

Looking at the bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579")), it appears to only be a problem with the 2.6.31 kernel, but it still makes me nervous.

Our mysql database, which contains all of our customer and financial data, is stored in /var/lib/mysql/ibdata1 -- a multi-gigabyte file. The filesystem was a freshly created ext4 system on Jaunty. I would think that anyone who uses Ubuntu in a production environment would have at least a few critical files larger than 512MB.

---

### Post by jhenager on 2009-10-30
I used the upgrade option, and see that the file system is still ext3.
Maybe you meant upgrade the version by doing a full install. Regardless, you should have full backups of any critical data if it will cause you grief to lose it.

---

### Post by jkounis on 2009-10-30
> **jhenager said:**
> I used the upgrade option, and see that the file system is still ext3.
Maybe you meant upgrade the version by doing a full install. Regardless, you should have full backups of any critical data if it will cause you grief to lose it.

I installed Jaunty  on a freshly formatted ext4 disk, so I think the bug report would apply, since the ext4 file system was created on a new disk.

Of course I make daily backups of my mysql database, plus I keep a binary log on a separate disk. However, what's scaring me is: How will I know if a few records of the multi-gigabyte database have been corrupted? Even if you discover corruption, you can't restore just the corrupted records, you can either

  (1) Restore the database from backup, in which case you lose all updates made since the backup
  (2) Keep running and try to figure out which particular records were messed up and correct them manually -- a big challenge for a multi-gigabyte database
  (3) Restore the database from backup and hope that you have all the binary log files to apply the transactions.
  (4) Wait and don't upgrade to Karmic yet.

I think I'll choose option 4 as the safest path for now.

---

### Post by grandtoubab on 2009-10-30
:lolflag:I don't know if it secures you but I believe the bug is related to ext4 not to Karmic, so if you are still in ext4 have your finger crossed :guitar:

---

### Post by Slim Odds on 2009-10-30
> **jkounis said:**
> Was Ubuntu 9.10 really ready to go from Beta to "production", or did it just happen because the date on the calendar said it was time?

This has been discussed many, many times. Ubuntu uses a TIME BASED release. It doesn't delay the release like some other well known OS's.

If you don't want to use it, don't. Or, install it in a manner that you consider safe. If you want to start your own version of linux, you can do that too.

---

### Post by jkounis on 2009-10-31
> **Slim Odds said:**
> This has been discussed many, many times. Ubuntu uses a TIME BASED release. It doesn't delay the release like some other well known OS's.

If you don't want to use it, don't. Or, install it in a manner that you consider safe. If you want to start your own version of linux, you can do that too.

The beta version of Karmic had the following warning: 

> Note: This is a beta release. Do not install it on production machines. The final stable version will be released on October 29th, 2009.

To me, this implies that once the "final stable version" is released, it probably won't go around surreptitiously trashing your mysql database and any other file you have that is over 512MB. If the "final stable version" had to be released on October 29, shouldn't the default file system have been set to ext3? 

At the very least,  shouldn't the release note have been made more prominent, rather than buried next to things like "Ctrl-Alt-Backspace is disabled"?

---

### Post by Slim Odds on 2009-10-31
> **jkounis said:**
> To me, this implies that once the "final stable version" is released, it probably won't go around surreptitiously trashing your mysql database and any other file you have that is over 512MB. If the "final stable version" had to be released on October 29, shouldn't the default file system have been set to ext3?

Everyone has an opinion about "defaults". Canonical has chosen them, since it's their baby. You can install it with ext3 quite easily, if you like (for me, personally, I'll stick with ext3 for a while more).

As I mentioned, you have choices.

---

### Post by phillw on 2009-10-31
> **jkounis said:**
> I was excited when it was announced that Karmic is "ready for prime time." Fortunately, I read the install before upgrading my production system. About 2/3 of the way down, buried in "Other known issues" between a note about needing to update grub if I'm using ext4 and a cautionary note about Ubuntu One is:


YIKES!

Was Ubuntu 9.10 really ready to go from Beta to "production", or did it just happen because the date on the calendar said it was time?

How commonly is this bug encountered? ext4 is the default file system for Karmic, and I can't believe that it could trash any file over 512 MB.

Looking at the bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579)), it appears to only be a problem with the 2.6.31 kernel, but it still makes me nervous.

Our mysql database, which contains all of our customer and financial data, is stored in /var/lib/mysql/ibdata1 -- a multi-gigabyte file. The filesystem was a freshly created ext4 system on Jaunty. I would think that anyone who uses Ubuntu in a production environment would have at least a few critical files larger than 512MB.


I'd reccomend the way I did it.... I'm w8ing for a week for stability with all the extra stuff I have before I do a 'wipe' to ext4.

As for backing up mysql dbases .... 

mysqldump -u root -pPASSWORD dbasename > whateveryouwant.sql

If you're into MySQL stuff, then a little used bit is lurking here ....  [http://www.vpolink.com/forumdisplay.php?f=300](http://www.vpolink.com/forumdisplay.php?f=300)


Phill.

---

