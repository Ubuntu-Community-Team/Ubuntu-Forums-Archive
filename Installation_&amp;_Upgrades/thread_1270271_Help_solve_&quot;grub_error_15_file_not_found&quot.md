---
title: "Help solve &quot;grub error 15 file not found&quot; to a computer I cannot access directly"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by mguidolin on 2009-09-19
Hi all,   I have a 'Error 15: File not found' problem to a computer that I cannot access directly (different country).  I need to know why it is happening so I can guide a non-technical friends by phone  to solve the  problem.  I want to ask if any of you have a previous experience in this situation.    A little of background:    - Three weeks ago I moved the boot directory of the computer from   a partition to another one.   The boot directory was in a too small partition (sda1)   and the root directory was in a large partition (sda2).   I moved the boot directory by comping the file in the    partition where the root directory lie (sd2).   I then remove the entry of the sda1 partition from /etc/fstab.    - I updated grub and the computer was working fine.    - Today, after an automatic kernel update, grub was   giving the 'Error 15 File not found' line.    I think that the problem lie in the fact that I changed the  boot directory partition and somoehow the automatic update messed up grub. But I'm not sure since the update should have worked fine.    Do anyone have a little more experience on that? How can I guide a non-technical friend by phone to fix this problem?  Thanks a million for your help. Michele

---

### Post by AmerNewbieInDE on 2009-09-19
take a look here...

[http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)

---

