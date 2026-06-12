---
title: "USB installer for Windows 7 and Ubuntu"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by Hagablog on 2009-04-05
Here's a question: I have a pendrive I use as an installer for Ubuntu (made using the bootable live usb installer) and I want to also put an Windoze 7 installer on there.  Will I have to repartition it, in which case do I have to make the ubuntu partition 4.4gb even though only 665mb is actually used; or can I put them on the same partition in which case how do I chose which to boot.  

Also, all the instructions to make a windows 7 installer are for windows, which I don't have, anyone know a way to do this in linux?

On a side note, is there actually a reason why two operating systems can't reside on the same partition?

---

### Post by Mark Phelps on 2009-04-06
> **Hagablog said:**
> Here's a question: I have a pendrive I use as an installer for Ubuntu (made using the bootable live usb installer) and I want to also put an Windoze 7 installer on there.  Will I have to repartition it, in which case do I have to make the ubuntu partition 4.4gb even though only 665mb is actually used; or can I put them on the same partition in which case how do I chose which to boot.  

Also, all the instructions to make a windows 7 installer are for windows, which I don't have, anyone know a way to do this in linux?

For Windows 7 questions, you would do better going to the Windows 7 forum at the following link:

[http://www.sevenforums.com/]("http://www.sevenforums.com/")

> 
On a side note, is there actually a reason why two operating systems can't reside on the same partition?
If you're asking about having both Ubuntu and Seven on the same partition, the answer is simple:  No because they required totally different native filesystems (Ubuntu: Ext3 or Ext4; Seven: NTFS).

As to the more generic question, Operating Systems exist in the form of kernels and supporting files.  In Linux, for example, it's not unusual for more than one kernel version to reside in the same partition.  As to having completely different kinds of kernels (e.g., MS Windows, Linux, Mac OSX), you're back to native filesystem formats again.

---

