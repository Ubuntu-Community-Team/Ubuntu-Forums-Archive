---
title: "Lost all files from a external harddrive."
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by niviq on 2007-11-10
I lost all my files, that were on a brand new external USB-drive, formated in JFS as a single whole partition (500GB)
The first problem occurred when I hibernated my laptop. When I then powered it on again series of some kind of "Bad device" scrolled down tty1. I unmounted the partition and tried to mount it again; but mount wouldn't as it said it had a bad superblock. I ran jfs_fsck and even thou it exited with code 0 (nothing wrong - nothing changed) it seemed to fix it, and I was able to mount it again.
Then when I later restarted my computer the external harddrive mounted, but the filesystem was empty. The filesystem was alright - the creation date was still the same.

Is JSF really such a crappy filesystem (first time I use it)? Or is it just bad with external devices?

Is there any way of restoring the lost files? (It will not be worth it if I can't restore the filenames)

---

### Post by scorp123 on 2007-11-10
You shouldn't do such stuff (standby + hibernate) with external drives .... The internal drives obviously can profit from the system's power management and will properly be powered down. External drives however depend on the USB connection, they are not under the control of a laptop's disk controller (as is the case with the internal disks), and if you go into standby or hibernate it will look like a sudden power failure to the external drive --that's a very very bad thing if it happens to a mounted file system-- and hence the filesystem may become corrupt.

Also, I'd recommend Ext3 over XFS or JFS. While XFS and JFS are superb for server work they don't take sudden power failures (as could be the case on a laptop!) too well and tend to corrupt to such a degree that data losses occur. Ext3 --while being a tad slower on very large files than e.g. XFS-- is far more "rugged" and is far more forgiving; even after totally unexpected and unforeseen failures chances are that your data will still be there on an Ext3 filesystem.  I am not saying that XFS or JFS are bad or anything like that (in fact I use XFS myself on many of my servers) ... I personally just wouldn't use them on a laptop or external harddrives.
.
.
.
.
.

---

### Post by niviq on 2007-11-10
I see. Just to get a list: which filesystems, other than ext3, would you recommend for laptops?
I have ReiserFS on my internal harddrive and that has never made any troubles.

---

### Post by scorp123 on 2007-11-10
> **niviq said:**
> II have ReiserFS on my internal harddrive and that has never made any troubles. .... Not yet .... :lolflag:  ... I once lost 750 GB of data thanks to ReiserFS. Since then ReiserFS is off-limits on my machines, regardless what anyone else says. I don't trust it anymore.

Besides ... ReiserFS offers the nasty possibility of an "undelete". If you delete something and then immediately poweroff and then do a "rebuild-tree" on the partition in question, whatever you deleted will be right back where it was. Don't get me wrong ... I have nothing to hide, I am no criminal or anything like that. But I do value my privacy and when I delete something I want to be sure that whatever I deleted *really* is *gone* and cannot be brought back -- especially not by other people not authorised by me to do so.

So if you think that having the possibility to "undelete" is a good thing, then fine, ReiserFS does offer this possibility. Here are detailed instructions:
[http://antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments](http://antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments)
[http://forums.suselinuxsupport.de/lofiversion/index.php/t10781.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t10781.html)

But if however you'd rather be sure that whatever you deleted really is gone, then you'd have to use Ext3 or XFS: both filesystems do a pretty good job at making recovering deleted files a rather complicated matter (it's still not totally impossible but sure more complicated):
[http://en.wikipedia.org/wiki/XFS#Disadvantages](http://en.wikipedia.org/wiki/XFS#Disadvantages)
[http://www.debianhelp.org/node/4970](http://www.debianhelp.org/node/4970)
[http://linvdr.org/mailinglists/vdr/2003/10/msg00612.html](http://linvdr.org/mailinglists/vdr/2003/10/msg00612.html)
[http://www.freelists.org/archives/linuxtrent/07-2003/msg00063.html](http://www.freelists.org/archives/linuxtrent/07-2003/msg00063.html)

---

