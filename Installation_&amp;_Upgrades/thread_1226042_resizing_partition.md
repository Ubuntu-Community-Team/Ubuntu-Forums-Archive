---
title: "resizing partition"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by graphicsxp on 2009-07-29
Hi,

I need to do something that I feel is going to break everything... 

I have installed Ubuntu on my hard drive. There's 2 partitions :

/ 100 Gb
Swap 2Gb

There's no space left on the disk for another partition. But the problem is that now I need to install Windows Server 2008 and I need to free 40 Gb for the installation.

How can I :
1. resize / so that I free up 40 Gb
2. create a new ntfs partition with the new available space
3. install Windows Server and make sure that GRUB will offer multi-boot 

I realize I may have to format my hdd completely and start from scratch, but I hope not.

Thanks

---

### Post by Partyboi2 on 2009-07-29
Hi, you can boot a Ubuntu live cd and use gparted (System>Admin>Partition Editor) and use the resize option to shrink down your / partition (providing you have enough free space on that partition to shrink down 40 gig) then with the newly unallocated space create a ntfs partition and install windows.
When you have finished installing windows you will need to restore grub which can be done by booting the Ubuntu live cd and following [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by graphicsxp on 2009-07-29
It seems very straighforward and safe ! Could that be true ??? I'll give it a go then..
Thanks !

---

### Post by Partyboi2 on 2009-07-29
It is safe, but in saying that its always wise to backup your important stuff before working on partitions.

---

