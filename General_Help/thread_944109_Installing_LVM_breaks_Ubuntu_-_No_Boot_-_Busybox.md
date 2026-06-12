---
title: "Installing LVM breaks Ubuntu - No Boot - Busybox"
date: 2008-10-11
forum: General Help
---

### Post by daniel.armbrust.list on 2008-10-11
So, I had a rather bad experience with Ubuntu 8.04 tonight.

Had previously set the system up on a single harddrive.  Few partitions on it - sda1 - sda3.  Ubuntu configured all of these in fstab and the grub menu.lst file using UUID strings.

Then, tonight, I add another old harddrive - and install the lvm2 package.  I create an LVM volume on the newly added drive - in the next few days, I'll add more disks to that LVM, but thats beside the point.

Created it, mounted it up.  Everything was just peachy.

Then I rebooted.  

Ubuntu was no more.

All I got was a busybox prompt.

Ctrl + Alt + F1 showed me that the primary error was:

Mounting /dev/sda1 on /root failed.  Device or resource busy.

Far too long later, I discovered that I could mount root within busybox if I did this:

mount /root /dev/mapper/sda1

Then type exit, and Ubuntu would (mostly) boot.

However, it still failed to mount all of my other drives from fstab.

I had to rewrite every fstab entry so that instead of using UUID labels, now they are of the form /dev/mapper/sda1, etc.  

Then I had to rewrite all of the grub menu.lst entries to use the /dev/mapper paths instead of UUID values.

Why did this happen?  Why did installing LVM make my harddrive (which is not part of any LVM volume) unmountable?

Have I implemented the correct fix?  Or have I implemented a hack?

Is there any advantage / disadvantage to using the /dev/mapper mount points versus using the UUID values?

Is this going to blow up again next time I do and update, and pull down a new kernel?

Is this filed as a bug somewhere?  Because this was rather sour experience.

---

