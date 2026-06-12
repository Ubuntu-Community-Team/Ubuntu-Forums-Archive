---
title: "swap file"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by high elf on 2006-01-20
What do I ned to do for the swap file?  I'm setting it up as a dual booting system, windows XP and Ubuntu.  Does the swap file need to be Primary or logical and does it need to be at the beginning or end of the disk?

---

### Post by dueY on 2006-01-20
[QUOTE=high elf]What do I ned to do for the swap file?  I'm setting it up as a dual booting system, windows XP and Ubuntu.  Does the swap file need to be Primary or logical and does it need to be at the beginning or end of the disk?[/QUOTE]

My Linux swap is a Primary between the NTFS and ext3 partitions.
Here is a pretty picture illustrating this:
[[IMG]http://img30.imageshack.us/img30/2535/partcrap6ye.jpg[/IMG]](http://imageshack.us)

---

### Post by hillbilly on 2006-01-20
It doesnt matter where your swap is. Swap is used by the system, when your RAM runs out of memory. So when RAM is full, the unused data is written into swap space. 
I guess you can survive without swap if you have copious RAM. Iam not sure whether theres bound to be any impact though :-/

In fact, during ubuntu installation if you select automatic partitioning, it will create a swap parition automatically.

---

### Post by high elf on 2006-01-21
I just ran the Linux installer, partitioned the disk and let the installer do its thing, Ubuntu boots to the login screen, I log in the music starts and then the mouse freezes and a few notes of the music just repeat themselves, i booted into the Ubuntu recovery mode and that didn't do anything to help (maybe theres commands I need to know?), I know the disc works, I installed ubuntu on to a laptop last week, any ideas?

---

