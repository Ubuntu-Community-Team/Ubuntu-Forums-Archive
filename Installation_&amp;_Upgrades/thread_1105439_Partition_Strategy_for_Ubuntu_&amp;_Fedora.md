---
title: "Partition Strategy for Ubuntu &amp; Fedora"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by pcaluori on 2009-03-24
I'm new to Ubuntu and really like it and intend to keep it as my primary OS.  I've already installed Ubuntu 8 & Fedora 10 multiple times, but not to my satisfaction.

This installation is on an older Pentium 4 computer with 2 hard drives: 60GB (primary, master) and 80GB (primary, slave.)

What is the best partition strategy?

I did an fres install of Fedora 10 and created a 10GB /var partition only to find that updates for OpenOffice fail due to lack of space in /var.

What should I do?  Do I even need to make separate /var, /usr & /tmp partitions?

Thanks!!!

---

### Post by louieb on 2009-03-24
Are you sure /var is 10GB in size? I give Ubuntu 10GB  for / (root)  and have a separate /home.  Have 4 machines running Linux  / (root) partition  has no more that 5 GB used on any of them. 
What does the ```
df -h
``` show?

---

### Post by pcaluori on 2009-03-24
The partitions were setup during the Fedora 10 install, but I did confirm the /var partition was indeed 10GB.

I thought that would be more than enough too, but it would not allow me to upgrade OpenOffice.  When I checked, there was 3GB+ of free space in /var, but that was not enough. I don't know where the remaining 6+Gb went, but there were lots of subfolders in /var, before I blew it away.

I can't run the command you suggest as I have already blown away that configuration and reinstalled Unbuntu.

Now I'm waiting for the collective wisdowm on how to proceed.

Thanks!

---

