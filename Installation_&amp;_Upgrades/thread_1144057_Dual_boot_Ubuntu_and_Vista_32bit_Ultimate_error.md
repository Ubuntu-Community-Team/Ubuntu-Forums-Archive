---
title: "Dual boot Ubuntu and Vista 32bit Ultimate error"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Mareshalu on 2009-04-30
Hey guys I'm having some hard time installing Ubuntu on my PC. I first partitioned my 2 sata hard drives as one big partition C, and then I resized that partition and gave linux 20GB unallocated space. When the partition manager in ubuntu starts it says "you have no OS installed, do you want to use all the space?". After that I formatted that 20GB partition to NTFS and I get the same thing, I'm thinking it has to do with the way EASEUS Partition Manager stretched the primary partition over 2 hard drives and one. 
Any help would be much appreciated.

Screenshot of Disk Management :
[[img]http://www.pixhost.org/thumbs/179/253387_untitled.png[/img]](http://www.pixhost.org/show/179/253387_untitled.png)

---

### Post by mikewhatever on 2009-04-30
Hope I understand you, but it seems you are trying to install Ubuntu on a 20 GB ntfs formatted partition. If that's the case, Ubuntu can't be installed on ntfs, use ext3 instead. It should also be noted, that creating a partition with whatever file system, and installing an operating system, are not the same things. Please review the installation guide before proceeding. [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Mareshalu on 2009-04-30
My problem is why doesn't Ubuntu recognize that I have already an OS on the hard drives. And I only get 2 options to format Guided use entire disk and Manual.

---

### Post by mikewhatever on 2009-04-30
I am not certain why that's the case, nor why it is a problem. You should be able to install using the manual option, just don't try installing on an ntfs partition.

---

### Post by Mareshalu on 2009-04-30
So I should give ubuntu some 20GB unallocated space on my HD? And then try to install>?

---

