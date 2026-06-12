---
title: "Convert EXT3 to EXT4"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by orrie on 2009-07-27
I have recently installed and configured Ubuntu 9.04 with ext3.
And I'm thinking about changing to ext4.
According to cfdisk and df -h is /boot ext2 and I want this changed also.

Have been using Gparted before and that's a great program.
But if I'm going to complete the converting, then I'm going to lose the data right?

---

### Post by merlinus on 2009-07-27
Changing filesystems means formatting, and data will be lost.  If you google a bit, there are some methods that can do this without losing data, but it has not worked for everyone.

---

### Post by izizzle on 2009-07-27
I wouldn't count on having your data be saved. The easiest thing to do is to back up your files and do a clean install on an EXT4 filesystem.

---

### Post by whoop on 2009-09-06
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

