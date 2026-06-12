---
title: "UDF (Mount Rainier) support for DVD+RW"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by kevin1 on 2005-10-30
Under Breezy I can read and write ISO CDs and DVDs.
I can also read DVD+RW disks formatted by Nero INCD under Windows, which allows them to be used as large floppy disks.
However, I have not found a way for Breezy to format blank disks in this way, and if I try to write to a disk formatted under Windows it becomes unuseable, both under Linux and Windows.

I am in the process of attempting the cdmrw.c & udftools solution from [http://www.thehaus.net/AltOS/Linux/ht-mtrainier.shtml]("http://www.thehaus.net/AltOS/Linux/ht-mtrainier.shtml") but have just noticed that my system has a /dev/cdrw device listed which does not appear in /etc/fstab. I now wonder whether I just need to change a configuration setting to get UDF write support.

The relevant line from my /etc/fstab is:
/dev/hdc   /media/cdrom1   udf,iso9660 user,noauto     0       0

When an INCD formatted disk is mounted, the /etc/mtab entry is:
/dev/hdc /media/cdrom1 udf rw,noexec,nosuid,nodev,user=kevin 0 0

Thanks for any advice,

Kevin

---

### Post by jis on 2006-10-14
I think you don't have to change the configuration setting, but I suppose you are allowed to do it. /etc/cdrw is probably a link to block device in the same /dev/ directory. You can check it by command ```
ls -all /dev/cdrw
```

Are you sure you have a DVD-RW drive that suppors Mount Rainier?
Have you got Mount Rainier working? I have, as I have explained in [here]("http://www.ubuntuforums.org/showthread.php?t=196951").
For non-mrw packet writing, there is a how-to at [this thread]("http://www.ubuntuforums.org/showthread.php?t=129093").

---

