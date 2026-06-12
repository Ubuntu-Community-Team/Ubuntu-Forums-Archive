---
title: "Install 9.04 on / partition"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by raul_7 on 2009-07-25
I have been using ubuntu 8.10. I got separate /home and / partition.
Now I am planning to install 9.04. So my question is it ok that I just format and install / partition and keep same /home partition.
Will it work?

Thanks in advance.

---

### Post by merlinus on 2009-07-25
Yes.  Select manual at the partitioning screen, choose to use /home as ext3 (or whatever it currently is) and its mountpoint, but not to format it.

You might want to write down your current partitions, e.g. sda5 = /home, sda6 = /, beforehand.

---

### Post by stlsaint on 2009-07-25
if you have seperat partitions correctly than yes you will be fine...just do what the above post states and ensure not to format...also just request to have your previous profile inserted while you install new version. may or may not work from  linux to linux but try it!

---

### Post by raul_7 on 2009-07-25
Thnanks for the reply.
Will try the same.
One more thing, is it ok if I choose ext4 for / partition. my /home partition has ext3 filesystem

---

