---
title: "External SATA HD"
date: 2008-10-10
forum: Hardware
---

### Post by 4-PackDad on 2008-10-10
Hey;

Still fighting the same battle.

I think my problem is my "Antique" (10yr old) Deck-Top PC.

Had to format the External SATA using a new PC running XP Pro in NTFS.

My "Antique" Ubuntu PC will not mount the External HD

I get the Following error:
DBus error org.freedesktop.DBus.Error.NoReply:

Also:
Cannot mount volume.
$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdc1': 
Operation not supported Mount is denied because NTFS is marked to be in use


I tried the following option that was suggested...
mount -t ntfs-3g /dev/sdc1 /media/Back Up -o force

That command line didn't work either...

Is it because my "Antique" PC doesn't support SATA...?

Thnx...

---

### Post by cariboo on 2008-10-10
How are you connecting you esata drive, are you using an adapter card? If so, does the card need a driver of some sort? A little more info would be helpful.

I have two esata drive that work quite well hot plugging even works

Jim

---

### Post by 4-PackDad on 2008-10-11
Hey;

I'm using an external HD case that supports IDE & SATA.
IDE's work with no problems.

Thnx

---

