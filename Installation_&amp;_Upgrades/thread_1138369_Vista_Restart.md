---
title: "Vista Restart"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by WBAC88 on 2009-04-26
I just installed Ubuntu 9.04 on a partition on my 500GB hdd. I was planning on dual-booting with Vista (something I've had up and running before on a previous computer), but this time I've hit a snag. Ubuntu is running wonderfully, but now, when I reach the boot menu during startup and I choose Vista (which now reads "Vista (Loader)" ), the computer restarts again at the BIOS. I've tried this several times, and it's occured to me I may have missed one of the steps to make dual boot work during installation of Ubuntu.

All of the data in the Vista partition is there, and I can still access it all through Ubuntu, but for some reason, Vista just won't start. I've tried looking through the forums, but the search terms are so vague, I come up with all sorts of posts totally unrelated to my problem. Any thoughts?

---

### Post by Triptol on 2009-04-26
I hope you have installed Ubuntu "behind" windows and you didn't move the windows partition to the end of the disk. If you did, you probably need to reinstall windows, although a vista guru might know how to fix it.

I'm trying to say that if windows was installed on partition 1, it should be on partition 1 after the upgrade as well. If it was on partition 3, it should be on 3 after the upgrade.... etc.


If Windows is still on the first partition you should be able to boot it with the following lines in your /boot/menu.lst (Windows is on the third partition of the first drive (sda) in this case):

```
title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
savedefault
makeactive

```

---

### Post by Mark Phelps on 2009-04-26
Is Ubuntu sharing the same physical drive with Vista? If so, how did you shrink Vista to make room -- Gparted (Ubuntu installer) or Vista Disk Management?

If you did the first, it's probably not booting because there's a known problem with GParted in that it sometimes corrupts the Vista OS partition during resizing.  If that happened, you will need to boot from a Vista DVD and run Startup Repair.

---

### Post by WBAC88 on 2009-04-26
Thanks for the help, let's see: Ubuntu is indeed installed behind Vista, with Vista coming first. They're installed on separate partitions of the same physical hdd, the partitions of which I created with GParted. I have a friend who has his Vista DVD, even if it's not the same license as mine, could I use the Startup Repair off of it? Mine came pre-bundled with my computer.

Triptol, Vista is still on partition 1, where it was before the install, I didn't touch it, and took all of the space for Ubuntu from a pre-existing partition (from a defunct install of ubuntu to be exact). Where would I find boot/menu.1st? Sorry, I've never gotten too far into the Linux experience, yet. Thanks again.

Andy

---

### Post by Mark Phelps on 2009-04-27
> **WBAC88 said:**
> Thanks for the help, let's see: Ubuntu is indeed installed behind Vista, with Vista coming first. They're installed on separate partitions of the same physical hdd, the partitions of which I created with GParted. I have a friend who has his Vista DVD, even if it's not the same license as mine, could I use the Startup Repair off of it? Mine came pre-bundled with my computer.

Yes, the repair functions are essentially all the same, so you can use any Vista DVD to run Startup Repair.  After you do that, though, you will overwrite GRUB in the MBR, so you will have to reinstall GRUB to get access back for Ubuntu.

---

### Post by Triptol on 2009-04-27
> **WBAC88 said:**
> Where would I find boot/menu.1st? Sorry, I've never gotten too far into the Linux experience, yet. Thanks again.

Sorry, that file is /boot/grub/menu.lst (that is a "L" not a "one" ;-) )

---

