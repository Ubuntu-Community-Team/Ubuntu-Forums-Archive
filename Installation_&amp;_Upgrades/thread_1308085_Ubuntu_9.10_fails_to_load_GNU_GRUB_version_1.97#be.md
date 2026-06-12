---
title: "Ubuntu 9.10 fails to load GNU GRUB version 1.97#beta4"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by overkill1 on 2009-10-31
Ubuntu 9.10 fails to load GNU GRUB version 1.97#beta4 in either generic or recovery mode

I get error no such device: 24aa1599-117b-4bb3-be61-698b49136add everytime grub loads

9.04 worked prefectly on my Dell Latitude c610 laptop

---

### Post by overkill1 on 2009-11-01
No love in this forum, am I the only one with this?

Ubuntu youve really messed it up this time round. :(

---

### Post by cariboo on 2009-11-01
You have several threads about the same problem in this [thread]("http://ubuntuforums.org/showthread.php?t=1305583") there is a link to documentation that should help you solve your problem.

---

### Post by exXplode on 2009-11-11
> **overkill1 said:**
> Ubuntu 9.10 fails to load GNU GRUB version 1.97#beta4 in either generic or recovery mode

I get error no such device: 24aa1599-117b-4bb3-be61-698b49136add everytime grub loads


**confirmed work around to be able to boot**: [http://ubuntuforums.org/showthread.php?p=8292225#post8292225](http://ubuntuforums.org/showthread.php?p=8292225#post8292225)
please note that you have to further interact in order to really fix the problem as this procedure has to be repeated every time you boot. take a look at [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408/comments/10](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408/comments/10) for ideas how to do that.

hoping for a fix via updates...

greetings pklaus

---

