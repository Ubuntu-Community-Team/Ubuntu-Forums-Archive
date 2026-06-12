---
title: "[SOLVED] Ubuntu / Debian partitions help"
date: 2008-08-11
forum: General Help
---

### Post by Cool Javelin on 2008-08-11
Hello all:

I don't know how unique this situation is, but, I have 2 hard disks, one, Wn98 on sda, the other I would like divided into 2 parts, 1/2 Debian Etch, and 1/2 Ubuntu Hardy.

hdb is 25.5 GB. I note Debian calls them hda and hdb where Ubuntu calls them sda and sdb. Do we know why? (unimportant.)

I had Debian working and wanted to install Ubuntu. During the install, I wanted to resize the Debian partition to make room for Ubuntu.

It was unclear during the resize how to do it, and I may have screwed up the Debian part as it no longer boots.

Anyway, Ubuntu is working fine, and using GParted 0.3.5 I have the following partitions on dev/sdb:

dev/sdb1 ext3 12.5GB used 500MB       (I think I want my Debian here)
dev/sdb2 extended
 dev/sdb6 ext3 / 11.8GB used 2.35GB   (and the Ubuntu here)
 dev/sdb7 swap 580MB
 dev/sdb5 swap 698MB

My previous Debian install had the following (I recorded these by hand during the Debian install)...
all on hdb
#1 primary 279MB /
#5 logical 5GB /usr
#6 logical 3GB /var
#7 logical 740MB swap
#8 logical 403MB /tmp
#9 logical 18GB /home

When in GParted, there are some keys near the sdb2, sdb6, and sdb7 partitions. I assume these keys mean the partitions are locked? Maybe it means these partitions are being used by Ubuntu (active?)

Note there are 2 swap partitions one with the keys symbols (sdb7) and the other without (sdb5) If I rightclick on sdb5 there is a "swapon" option, and if I rightclick on the sdb7, there is a "swapoff" option implying Ubuntu is using sdb7 for the swap.

My guess is somehow the previous Debian partitions got screwed up, the previous /usr partition somehow got renamed to swap, and is now unused.

I don't care to save the Debian install, but I do want to reinstall Debian. Problem is, what do I do now?

Question 1, What are the advantages to having separate partitions for the /usr, /var, /home, and /tmp? It seems to me, when one fills and the others are empty, it is an inefficient use of disk space requiring manual intervention to fix it.

Question 2, Can I use the same place on the drive for the swap partition? (both Ubuntu and Debian use the same swap space) Assuming Ubuntu and Debian are not running at the same time.

Question 3, If I do have separate partitions for /tmp, /usr. /var, and /home, can these be shared between the 2 OS.s as in question 2?

Question 4, During the Ubuntu install, I really didn't get the opportunity to answer the partitioning questions. Is there a way to do that in future Ubuntu installs?

Question 5, What stuff usually gets put into the 4 partitions /usr, /var, /tmp, and /home. (I guess I understand /home OK, it kinda like the My Documents folder in older windoz.)

Whew, that was long. Thanks folks for your help.

Mark.

---

