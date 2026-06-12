---
title: "one partition windows the other ubuntu"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by roxycotton on 2009-10-06
i mainly use my computer for gaming, and because of that i am mainly a windows user. now i have become sick of windows and want to have ubuntu on my computer. the only problem is that ubuntu doesn't play all the games that widows does.

can someone please tell me how i can have windows inside of one partition for example c: drive, and ubuntu on a completely separate partition for example d: drive all inside the same harddrive?

and i know that i could do a duel boot, but i don't want that. i would rather them each have their own separate partitions.

thanks in advance.

---

### Post by Partyboi2 on 2009-10-06
Hi, when you dual boot you can install the os to its own partition. So if you want to dual boot XP/Ubuntu you can follow [[COLOR=Blue]this[/COLOR]]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm").
If you want to dual boot Vista/Ubuntu follow [[COLOR=Blue]this[/COLOR]]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") one.

---

### Post by ajgreeny on 2009-10-06
Lots more info in these two sites as well.
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Bartender on 2009-10-06
> **roxycotton said:**
> and i know that i could do a duel boot, but i don't want that. i would rather them each have their own separate partitions.

Your choice of wording is confusing.  Unless you're using wubi, Windows and Linux are going to use separate partitions.  That's a given, regardless of whether you have one hard drive or two.  You mean separate hard drive's, right?

Watch your PC closely when it first boots up.  I've been checking mine.  A BIOS screen appears for a second or two.  The three PC's that I've checked all display two different keys - one to get into BIOS, the second key for getting into what I call the "quickboot" option.

If you have the quickboot option, it's easy to install Ubuntu completely to the second drive, then tap the right key during start-up, then choose the device you want to boot to.  This changes boot for just that start-up.  It does not make permanent changes.

You'll see various methods to install ALL of Ubuntu to a second drive.  I'm just gonna stick to what I think is the simplest and most fool-proof.  Physically  disconnect the Windows drive.  In step 5 of the Ubuntu install, make sure the installer sees only the target hard drive.  Ubuntu will install the entire bootloader to that drive, and the Windows drive will be untouched.

---

### Post by roxycotton on 2009-10-06
thank you for all the responces. they were most helpful, now im going to try to apply them.

---

### Post by Noobalot on 2009-10-06
I have 2 hard drives in my laptop so I installed vista on 1 and ubuntu on the other using the installation discs.

wasn't gonna bother with vista but couldnt get eve online to work.

---

