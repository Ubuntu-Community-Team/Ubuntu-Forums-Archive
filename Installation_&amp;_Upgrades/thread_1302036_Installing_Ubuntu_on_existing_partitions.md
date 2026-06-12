---
title: "Installing Ubuntu on existing partitions?"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by second.exodous on 2009-10-26
For some reason Linux, no matter what distro, freezes on formatting a 1TB disc I have.  What I needed to do for Sabayon and Fedora is pre-format the drive with gparted and then install using those existing partitions.

So I have Sabayon installed on one HD and can boot into that to format the drive through gparted.  I need to know how to format for Ubuntu 9.10.  I noticed that it puts the boot and swap at the end of the drive before it froze, is this correct?

Also, once I have the drive formatted is it possible to use existing Partitions so the installer doesn't have to do the partitioning?

Thanx,
Stan

---

### Post by fancypiper on 2009-10-26
> **second.exodous said:**
> 

So I have Sabayon installed on one HD and can boot into that to format the drive through gparted.  I need to know how to format for Ubuntu 9.10.  I noticed that it puts the boot and swap at the end of the drive before it froze, is this correct?
It doesn't matter where the partitions are, just that they exist.
I suggest 3 partitions:
/ - 10-20 GB depending upon amount of software installed.
swap - 2 GB (probably too much, but I have a 1 TB drove)
/the rest of the empty drive space
If you have other drive(s), I put on /pub, /storage or some such.

> **second.exodous said:**
> Also, once I have the drive formatted is it possible to use existing Partitions so the installer doesn't have to do the partitioning?
Yes, choose the last option, manual partitioning and edit your existing (and possibly formatted) partitions.

---

### Post by second.exodous on 2009-10-26
I put my first partition to 2 GB of swap and then the rest just as '/', does that sound good?  It didn't look like Ubuntu uses a /boot partition and I didn't make my home directory a separate partition.

---

### Post by fancypiper on 2009-10-26
Without a separate /home partition, you have a much better chance of hosing your system and losing your valuable stuff that you had in /home.  With a separate /home, it is a snap to install another distro or do a quick re-install if you get frustrated trying to fix a broken system.

I strongly suggest having a separate /home partition.

---

### Post by second.exodous on 2009-10-26
Oh man, I already installed.  I always have two distros installed in case one borks, I just copy the /home directory with the other distro.  Not as good as a separate /home directory, maybe I'll try that once I try another distro.

Just out of curiosity, can two distros use one home directory?  I'd get a another drive so I have 3, one for /home for both distros and one for each distro.  I've never tried because I never knew if it would break something.

---

### Post by fancypiper on 2009-10-26
Yes, but the numbers assigned to the user account may be different for different distros.  Just use a different username for each distro. Then you can copy files from the other users directory as root or sudo, then:
chown -R <username>.<username> /home/<username>

---

