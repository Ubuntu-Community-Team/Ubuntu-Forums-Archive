---
title: "Install boo boo regarding partitions"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by Spidergirl on 2009-02-18
Hello there. I was running a version of MacOSX86 on my computer and I decided to partition the drive to make room for Ubunutu. This required disabling the journal on the partition. The install was a success and I am coherently working in Ubuntu. Unfortunately I can no longer get back in to my Mac partition. I have editing the boot/grub/menu.lst and added 

```
title		osx86
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

But that has shown me the error

```
starting Up
H00000
HFS+ Partition Error
```

When booting. I want to think I should have to enable the journal again but I am at a stand still at how to do that. This is what my curent drive looks like

```
/dev/sda1	fat32
/dev/sda2	hfs+	(Mac OSX86)
/dev/sda3	ext3
/dev/sda4	ext3
/ev/sda5	linux-swap
```

Basically I need to boot the second partition. Can anyone assist me on this?

Thank you kindly in advance.

---

