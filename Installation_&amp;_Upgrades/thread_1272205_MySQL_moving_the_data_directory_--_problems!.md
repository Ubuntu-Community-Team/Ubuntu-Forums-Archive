---
title: "MySQL moving the data directory -- problems!"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2009-09-21
Hi,

I just installed a system with / as XFS.  In general, the system is extremely fast (of course, the i7 might have something to do with that, especially compared to my old P4)

I installed mysql as well, and discovered that using our create/insert scripts the new box is several times slower than my old P4!  So much so, that the first few times I killed it because I thought the process was hung.

So I did some research, and discovered that XFS comes in second to last for myql.  So I made a quick 100g partition with Reiser, which is what seems to win in most categories.  Then I shut down mysql, copied (-prd) the /var/lib/mysql directory to /reiser/var/lib/mysql, and restarted.

Ok, this is mostly just a test, I can think of a better name for the directory later.

Anyway, mysql fails to start.  I switch the my.cnf back to the original, and it works fine.

Anybody know right off what I'm missing?

This is a brand new system, just got it booting yesterday:

Intel i7 920
Asus P6T motherboard.
6g/750g
Ubuntu 9.0.4 Jaunty.
/boot is ext2, 500 m (I mess with a lot of kernels)
/ is XFS, 200g, defaults
/reiser is reiserfs, 100g, defaults

The same options are used mounting both filesystems.  The /reiser fs mounts fine, seems to have the same permissions.

Thanks.

/var/log/messages segment pertaining to this:
Sep 21 20:53:11 thor kernel: [   23.776744] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
Sep 21 20:53:11 thor kernel: [   23.776754] ReiserFS: sda5: using ordered data mode
Sep 21 20:53:11 thor kernel: [   23.780527] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Sep 21 20:53:11 thor kernel: [   23.780787] ReiserFS: sda5: checking transaction log (sda5)
Sep 21 20:53:11 thor kernel: [   23.791679] ReiserFS: sda5: Using r5 hash to sort names
Sep 21 20:53:11 thor kernel: [   24.394019] type=1505 audit(1253584390.727:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2582
Sep 21 20:53:11 thor kernel: [   24.417073] type=1505 audit(1253584390.751:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2586
Sep 21 20:53:11 thor kernel: [   24.417121] type=1505 audit(1253584390.751:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2586
Sep 21 20:53:11 thor kernel: [   24.417144] type=1505 audit(1253584390.751:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2586
Sep 21 20:53:11 thor kernel: [   24.417165] type=1505 audit(1253584390.751:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2586
Sep 21 20:53:11 thor kernel: [   24.481739] type=1505 audit(1253584390.816:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2591
Sep 21 20:53:11 thor kernel: [   24.481813] type=1505 audit(1253584390.816:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2591
Sep 21 20:53:11 thor kernel: [   24.517910] type=1505 audit(1253584390.851:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2595
Sep 21 20:53:11 thor kernel: [   24.531179] type=1505 audit(1253584390.863:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2599
Sep 21 20:53:12 thor kernel: [   26.280691] type=1503 audit(1253584392.615:11): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/reiser/var/lib/mysql/thor.lower-test" pid=3015 profile="/usr/sbin/mysqld"

---

### Post by 1clue on 2009-09-21
Never mind, I figured it out by myself.

It's apparmor, the my.cnf file has warnings about it.  Took 2 minutes to fix, if you start the clock when I posted this thread.  Couple hours before that for some reason.

---

### Post by 1clue on 2009-09-21
By the way, the speed improvement is immense.

I didn't time the old way, but I'm guessing 5 minutes or more to create my db and populate it using grails.  Now, it comes in just shy of 1m11s.

This is from XFS to Reiser.

---

