---
title: "Dual Booting"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by cadefy on 2009-10-09
Hi guys, I have Ubuntu installed and it's the best OS I've ever freaking used, but then the only reason I want to dual boot XP with Ubuntu is my games, there's a laggy slow cursor in world of warcraft that just ticks me and i've searched everywhere and theres no fix

so I'm going to game on XP and use Ubuntu for everything else.

Does anyone thnk it's easier if I install XP First or Ubuntu first THEN xp ?

Also my MBR is kinda screwed up, when I start up the computer it has

something like

Ubuntu
Ubuntu something
Ubuntu something something
Windows Vista
Ubuntu 
Ubuntu something
Ubuntu something

I reinstalled ubuntu because of the 5mb free space i had the first installation on my "File System"

so the question is, if I format my hdd and install xp then ubuntu would it be easier than if i already had ubuntu on here then dual boot xp
and how would I clear my MBR so it's clean again :P

(Data on my drive doesn't worry me because it's already all backed up on an external)

Any help would be appreciated, thanks

---

### Post by Partyboi2 on 2009-10-10
If you have 2 installations of Ubuntu you can boot a ubuntu live cd and use gparted (System>Admin>Partition Editor) and remove the Ubuntu installation you do not want to keep.
Then go ahead and reinstall Vista, then you will need to boot the Ubuntu live cd and restore grub again by following [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by kiridude on 2009-10-10
Starting from the beginning, install Windows first then Ubuntu.

The whole booting process will be handled automatically by Ubuntu.

---

### Post by raymondh on 2009-10-10
> **kiridude said:**
> Starting from the beginning, install Windows first then Ubuntu.

The whole booting process will be handled automatically by Ubuntu.

Either way would work.  Even if you install Ubuntu then XP, re-installing GRUB is a quick process (and a good learning experience as well).

Regards,

---

