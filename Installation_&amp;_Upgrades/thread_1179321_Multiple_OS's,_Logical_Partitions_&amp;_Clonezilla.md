---
title: "Multiple OS's, Logical Partitions &amp; Clonezilla"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by nesnfsn on 2009-06-05
I know that we are limited to 4 primary partitions per disc, but can I install multiple linux distributions on multiple logical partitions?

Reason is that I want to use Ubuntu 9.04 32-bit for VDR and MythTV, with linux-server kernel so that I can access all 8GB RAM. I also want to use the next version of Ultimate amd64 version once released, Fedora 11 when it is released next week, and I want to play with other distributions. 

Currently, I have set up MS Win XP SP3 as Primary Partition 1, Linux Swap as Logical Partition 5, Ubuntu 9.04 as Logical Partition 6 with ext4, have set up Logical Partitions 7, 8, 9 and 10 (the last logical partition being smaller and intended to use with Clonezilla).

When I archived an image of Ubuntu 9.04 the other night, and went to write over Partition 6 the next AM, it seemed to work, but then froze with some message about expecting unary message, all in response to writing boot-grub (or something akin to that name). Concerned that Clonezilla cannot handle logical partitions.

Can someone with Clonezilla experience and/or experience of using multiple linux distributions (more than just MS Win on 1, Linux Swap on 5, and 2 OS Distros in Primary Partitions 6 and 7) on the same hard drive address these issues? Want to plan in advance for UU2.2 amd64 once released, as Fedora is to have its next version out this coming week. That would be MS Win XP and 3 Linux OS and 1 Swap partition so far, if possible (5 partitions).

---

### Post by logos34 on 2009-06-05
which, version of clonzilla are you using, stable, testing or ubuntu-based?

---

