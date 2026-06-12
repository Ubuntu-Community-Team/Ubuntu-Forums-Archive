---
title: "LVPM transfer, want to get rid XP partition"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by soule on 2009-04-21
Hi,

I have just installed ubuntu 8.10 on my PC via an LVPM transfer about 2 weeks ago, and I want to get rid of my XP partition (60GB) in favour to give my ubuntu partition all my space. However, as seen in the screenshot, it seems my XP partition is flagged as boot under Gparted and might get my system unbootable if i remove the XP partition. My alternate method is to wipe out my HD and install ubuntu fresh, but I have got some precious files and config i don't want to sacrifice.

Thanks, soule. (screenshot below)
[IMG]http://souleiman.com/files/dev-sda_GParted.png[/IMG]

---

### Post by ajgreeny on 2009-04-21
I believe that's because windows has to have a boot flag to do anything, whereas ubuntu will boot provided grub points to the correct partition.  Don't worry about it anyway, grub can easily be restored if needed.  Just make sure you delete the correct partition, and before you do anything, BACKUP.

---

### Post by soule on 2009-04-21
Ok, I hope all goes well. Thanks, although I might aswell just make a fresh install. Thanks. Although should I make a super grub disk as often reccommended in situations alike mine?

---

### Post by ajgreeny on 2009-04-21
I've never used supergrub, so can't really say, but I know the grub restore works and have used it a few times.

---

### Post by soule on 2009-04-22
Ok, however, do you know how to expand my unallocated space? I am left without a clue as the resize buttons are greyed and un-clickable. There's a screenshot below showing this, if it'll help. 

Thanks, soule. (screenshot below)
 
[IMG]http://souleiman.com/files/unallocated_space-forum.png[/IMG]

---

### Post by unutbu on 2009-04-22
Your posted image shows sda2 is mounted at /. That means you are running GParted while booted into Ubuntu using sda2. You can't modify a mounted partition like sda2, and you can't unmount it while it is running Ubuntu.

So boot the LiveCD, and run GParted from there.
Then sda2 should not be mounted, and the Resize/Move button should be usable.

---

### Post by soule on 2009-04-22
> **unutbu said:**
> Your posted image shows sda2 is mounted at /. That means you are running GParted while booted into Ubuntu using sda2. You can't modify a mounted partition like sda2, and you can't unmount it while it is running Ubuntu.

So boot the LiveCD, and run GParted from there.
Then sda2 should not be mounted, and the Resize/Move button should be usable.

Oh yeah, forgot. Thanks. SOLVED.

---

