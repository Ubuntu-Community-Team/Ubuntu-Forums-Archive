---
title: "Duel boot"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by arckeda on 2006-02-07
I want to duel boot XP and Ubuntu, I have 200 GBs and 512 MB DDR SDRAM.
What should i put swap and stuff?
Where is a guide that can help?
What is a free program that can back up files?
Thx.

---

### Post by arckeda on 2006-02-07
I think i have NTFS and FAT32 partions already, is their anyway to maek sure?

---

### Post by Sutekh on 2006-02-07
This is the best guide that I know of.  It will deal with issues such as resizing Windows partitons, 'swap and stuff' and with lots of pretty pictures.

[Install Ubuntu with Windows (NTFS) - by]("http://users.bigpond.net.au/hermanzone/p3.htm")[ Herman]("http://ubuntuforums.org/member.php?find=lastposter&t=125673")

PS This guide shows you how to let the installer set the amount of swap space to be used.  Generally it is quoted that around 1.5 to 2 times your RAM is sufficient.  So you'd want around 750MB - 1GB of swap space.

---

### Post by arckeda on 2006-02-07
OK i have a NTFS for my 200GB drive, and a FAT32 for my "backup drive" that came with my computer what do i do?

---

### Post by Sutekh on 2006-02-07
Ok so Windows occupies the 200GB drive?  How much space does it take up?  And how much space are you willing to commit to installing Ubuntu?

And what's the 'backup drive'?  Is it a second *physical* drive or is it part of your 200GB drive?

---

### Post by arckeda on 2006-02-07
backup is a 8 gig hard drive that i dont want to mess with, came with my computer and it is FAT32, but what i want to knwo is if i should make a new FAT32 for my other harddrive which as NTSF, willing to give 20gig for Ubuntu, or whatever i should, and the rest to windows, but do i have to make ANOTHER p-thing (dont know how to spell it) after that?

---

### Post by Sutekh on 2006-02-07
[QUOTE=arckeda]backup is a 8 gig hard drive that i dont want to mess with, came with my computer and it is FAT32, but what i want to knwo is if i should make a new FAT32 for my other harddrive which as NTSF, willing to give 20gig for Ubuntu, or whatever i should, and the rest to windows, but do i have to make ANOTHER p-thing (dont know how to spell it) after that?[/QUOTE]
You don't need to create another FAT32 partition unless you wish to read/write files between Ubuntu and Windows easily.  If you want to have this is doesn't need to be too big, unless its for storage 5GB should be heaps.

20GB for Ubuntu should be sufficient.

---

### Post by arckeda on 2006-02-08
k, but if i do and i already have a FAT, and i create a new one will it foobar up?
and what about some backup programs...

---

### Post by Sutekh on 2006-02-08
[QUOTE=arckeda]k, but if i do and i already have a FAT, and i create a new one will it foobar up?
and what about some backup programs...[/QUOTE]

No there shouldn't be an problem creating another FAT32 partition.  My comment goes to something you said earlier...
[QUOTE=arckeda]but what i want to knwo is if i should make a new FAT32 for my other harddrive which as NTSF[/QUOTE]

To which I wanted to say, there is no *need* to create another FAT32 partition.  But if you *wish* to create another one, then go right ahead.


As for backup programs, that's not something I ever think about.  I usually just put important stuff on CD/DVDs.  But I'm sure there is plenty of info lying around the forums to help you.

Here is a link on a way to manually backup Ubuntu.
[Ubuntu Forums - HOWTO: Backup And Restore Your System - by ]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+programs")[A-star]("http://ubuntuforums.org/member.php?u=8798")

---

