---
title: "&quot;There is no operating system on this computer&quot;"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by redtom on 2009-04-21
Hi, I've downloaded Ubuntu 9.04 and booted from it, but when I get to the partition editor it says "There is no operating system on this pc" - even tho Windows Vista is already on it.

I'd like to get a dual boot set-up on to my Dell Studio 17 - any ideas?

---

### Post by ronparent on 2009-04-21
Try going to manual partition.

---

### Post by dabl on 2009-04-21
Parted Magic is a pretty good tool for partitioning your hard drive -- you can make a bootable CD, use it, and then boot your *buntu CD and go directly to installing on your new partition(s).

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by jobo1313 on 2009-04-21
If you are dual-booting partition from Vista. You will need to fragment then get a howto like this one: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
But always fragment you dont want to lose anything on the Vista partition.
I did it this way and it worked. BUt i recently made a huge mistake and tried doing from linux and screwed up vista. It wouldnt boot so i went into recovery and it wiped my hard drive.[-X

Have FUn

---

### Post by oldos2er on 2009-04-21
> **redtom said:**
> Hi, I've downloaded Ubuntu 9.04 and booted from it, but when I get to the partition editor it says "There is no operating system on this pc" - even tho Windows Vista is already on it.

I'd like to get a dual boot set-up on to my Dell Studio 17 - any ideas?

 gparted isn't going to care if you've got one, fifty, or zero OSes on your computer.

 Did you run 'Check CD for defects' when first booting from the LiveCD?

---

