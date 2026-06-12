---
title: "Swap partition doesn't work! What do I do?"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2009-01-17
My /etc/fstab looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=436bd366-bfea-4274-9458-26addfb383d8 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3  swap  swap pri=1 0 0
```


And here's a screenshot:

[IMG]http://i41.tinypic.com/ri9rsz.png[/IMG]

And here's swapon -s
```
joh@Johs-zepto ~ $ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda3                               partition	6144852	0	1

```


Why won't the swap work? I tried running something called uswsusp and it said that I had no active swap partition

---

### Post by theozzlives on 2009-01-17
Mine wouldn't work either so I said screw it. I allocated it back to the system.

---

### Post by Fzang on 2009-01-17
I need swap for hibernate so I can't really just screw it...

---

### Post by Fzang on 2009-01-18
Bump, please help

---

