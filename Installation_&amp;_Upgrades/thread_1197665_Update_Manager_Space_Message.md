---
title: "Update Manager Space Message"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2009-06-26
Occasionally an update is large enough that Update Manager complains that there is not enough space on the / partition and requests the user to empty the Trash and run apt-get clean.

Wouldn't it be more considerate if the Update Manager merely asked for permission to perform those operations, rather than requiring the user to start up a terminal session to issue a command-line operation?

---

### Post by cmwslw on 2009-06-26
If your hard drive was that full, I suppose running those two commands should be the least of your worries. I guess a feature like that would be nice for some people though. Definitely don't do it automatically because sometimes apt-get clean wipes out desired packages.

---

### Post by jcobban on 2009-07-02
> **cmwslw said:**
> If your hard drive was that full, I suppose running those two commands should be the least of your worries. I guess a feature like that would be nice for some people though. Definitely don't do it automatically because sometimes apt-get clean wipes out desired packages.
But it is not my hard-drive that is full, just the / partition.  I do not understand the rationale behind the way that the Ubuntu installation partitions the disk, but in my case it divided the disk into a /dev/sdb1 partition of 8GB and a /dev/sdb2 partition of 49GB.  The /dev/sdb2 partition is further divided into a 45GB ext3 filesystem (identified as /dev/sdb6) and two 2GB swap files. (FYI /dev/sda is a Windoze C: drive with an NTFS partition).  Then along came a monster update, including files identified as kernel ...-13, and there just wasn't enough room left in the /dev/sdb1 partition, even though there was lots of space in /dev/sdb2.  Looking at /etc/fstab /dev/sdb1 is mounted at /.  I don't see any mount referring to the ext3 filesystem at /dev/sdb6.

I got the update to install by rebooting into the stand-alone gparted, shrinking the /dev/sdb2 partition by 2GB, which required moving every allocated byte of the ext3 filesystem, and expanding the /dev/sdb1 partition to take up the freed space.

In any event I didn't suggest that the tool should do a clean automatically, just that it would be simpler for the user if the procedure did not require starting a terminal session to issue that command.  It is just as much under the user's control if the user has to click on a GUI button to authorize the command.  Consider that users who are coming from either Windoze or Mac have generally never issued a command from a terminal window.

---

### Post by merlinus on 2009-07-02
When installing, what method did you select at the partitioning screen?  No way ubuntu would create two /swap partitions on its own, for instance.

---

### Post by jcobban on 2009-07-03
> **merlinus said:**
> When installing, what method did you select at the partitioning screen?  No way ubuntu would create two /swap partitions on its own, for instance.

I think I understand how I screwed up now.

The problem would appear to be that I ran the Ubuntu installation TWICE.  This created two Linux installations, and the two swap files.  I would now like to remove the second Linux installation, which is using a lot of space for no good purpose.  It was the space taken up by that second installation that restricted the size of the first installation and required me to use gparted to move the boundary between the two partitions before I could install the -13 update.  The only thing is that the second installation pointed the grub boot-record at itself. So before I can delete that partition I believe that I must first point grub back at the first partition.

I think all I have to do is:

title Install GRUB
root	(hd1,0)
setup   (hd1)

But I haven't got up the nerve yet for fear I will leave the system unbootable.

BTW on my system (hd0,0) is WinXP.

---

