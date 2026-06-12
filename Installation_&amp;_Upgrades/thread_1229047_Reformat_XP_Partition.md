---
title: "Reformat XP Partition?"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by jfinner1 on 2009-08-01
I have my computer dual booted with XP and Ubuntu. Over the past few days, XP has been giving me lots of problems. I was trying to fix it, but I guess I was trying the wrong things, because this morning, XP crashed. Now it freezes at the loading screen, and won't even boot into safe mode. So what I'd like to do is reformat the partition and reinstall XP from scratch. But I'm not sure how to do this without hurting Ubuntu. Could someone please let me know? Thanks in advance.

PS. This is kinda a rush order, because I need XP fixed by Monday for college.

---

### Post by merlinus on 2009-08-01
You sholuld be able to reinstall xp into its existing partition using the install cd.  It probably won't even see the linux partitions.

But you can gparted, either on the ubuntu live cd or its own, to reformat it.

In any case, be sure to not let xp use the entire hdd!

---

### Post by swerdna on 2009-08-01
At the XP install screen, select the existing xp partition and delete it then remake oit and choose to format it -- all part of the installation. That won't hurt the Ubu partitions except it will wipe out the Grub boot loader.  Not a problem. Reinstate the Grub loader like this ===>

Suppose Ubuntu had it's boot folder on, say for illustration sda7. In grub speak you call that (hd0,6) [6 is 1 less than the 7 sda7=(hd0,6)]

You reinstall Grub as the bootloader after xp has installed by doing this:
Boot the Ubuntu installation cd.
Open a Gnome-terminal window and enter this: sudo grub
Then you'll get the Grub prompt like this: grub>
Do these things next:
[html]You enter this ---------------- root (hd0,6)
Computer returns like this ---- Filesystem type is ext2fs, partition type 0x83
You enter this ---------------- setup (hd0)
You see 4-5 lines like this --- Checking if /boot/grub/stage1 exists ... yes
Computer finally returns this-- Succeeded.......Done
You enter this ---------------- quit
You enter this ---------------- sudo reboot[/html]

That should reboot you back to the Grub menu you were used to before xp cracked up.

FFI on this method go here and see the item called ["Reinstall Grub in the Master Boot Record and link it to the existing Grub menu]("http://opensuse.swerdna.org/susebootfive.html#linkmbr")"

That's written for openSUSE but the actions are exactly the same for Ubuntu.

If you can't figure out which sdax to use, see the linked article where it says to do the following at the grub prompt: grub> [HTML]You enter this ---------------- find /boot/grub/menu.lst
Computer returns like this ---- (hd0,6)[/HTML]

Whatever it says instead of (hd0,6) is what you use.

---

