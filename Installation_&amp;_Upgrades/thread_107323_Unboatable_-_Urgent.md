---
title: "Unboatable - Urgent"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by dgs on 2005-12-22
Now i've messed it up totally... (NOT blaming ubuntu)

While trying to change my partitions i killed my swap and linux partition.... including grub (on linux partition). I'm sure i can fix this from my xp (primary partition) but the mbr is messed up and so is grub (and grub freezes on start).

If this wasnt enough i cant find my xp cd and have no floppy drive installed so i cant use any boot disks. No cd burning software is available either...

So...

I need to restore the mbr so i can boot xp from primary partition... but i have to do this from my ubuntu live cd (demudi). I now there is a tool called fixmbr in xp but i cant get to the recovery console. Any help appreciated! 

Regards
Dennis

---

### Post by towsonu2003 on 2005-12-22
If you have the install CD, try this one out to revive grub: 

(using install CD) [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)  -> the discussions on this are here: [http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub+rescue](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub+rescue)

or:

(Using install CD) [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

[quote=dgs]but i have to do this from my ubuntu live cd[/quote]
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore) (second one uses live cd)

hopefully these will help... good luck.

---

### Post by dgs on 2005-12-22
Thanks for replying!

I the only way i managed to install grub was to install ubuntu again (and for me im sure it was the fastest way to do it... linux doesn't like ntfs you know) and now my xp booted up so i could fix my mbr from there.

Many thanks! You spared me several hours! Double espresso for you!

Cheers
Dennis

---

