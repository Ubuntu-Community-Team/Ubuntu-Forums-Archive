---
title: "External drives automount in readonly mode"
date: 2008-07-30
forum: General Help
---

### Post by Hashi on 2008-07-30
Hi, everyone,
  This has only happened since I upgraded to 8.04, it worked fine in 7.10. I have two USB external hard drives, which are mainly used for backup, and so only plugged in when necessary.

  Both of them automount as read only. One is FAT32, the other NTFS (historical reasons), but they used to automount in read/write mode previously, ie Gutsy.

  Is there anything I can do to fix this? Any hints much appreciated.

Thanks,
Jon

---

### Post by drs305 on 2008-07-30
If you are interested in trying a gui fstab configuration tool, try pysdm. A tutorial and '3 Minute Guide' are available through the link in my signature.

The tutorial looks really long but the top section can get you set up fairly quickly.

---

### Post by cdtech on 2008-07-30
Who has ownership of the drives when their plugged in? (ls -l /media/)

**Update::.**

A FAT partiton has no ownership or permission information in the filesystem so these are determined on who mounts them. When a FAT filesystem is automounted and when the icon is on the desktop, the files will be owned by you. Now the ext3 (and other Linux filesystems) have genuine ownership and permission info and is in fact writable, all you have to do is make a directory within the partition (which will be owned by you) and you can start writing to that directory.

---

### Post by Hashi on 2008-07-30
Thanks, I'll try it when I get home (at work now) and report back tomorrow.
Jon

---

### Post by mc4man on 2008-07-30
If there is _no current fstab entry (entries_) for the drive(s) then they should mount by default to /media/<volume name>. Root will own that but what would be of more interest is the mount options of the volume. That can be checked by r. clicking of the drive icon either on the desktop or in places -> computer, and going properties -> volume. A typical ntfs is shown below in screenie.

What would also be interesting is what is shown for removable drives in system -> admin -> authorizations -> storage -> mount file systems from removable drives. The implicit should show - active console - yes. You could try granting yourself explicit authorization with no constraints. Not sure if this affects, controls usb hdd's but seems it should. (hence interesting)

side note; in the case of internal drives (ie. other partitions) that aren't automounted at boot( no fstab) giving yourself explicit in the setting for internal drives takes care of rw, mount and unmount issues not matter what the fs, simply d. click to mount, r.click to unmount.

---

### Post by Hashi on 2008-07-30
Hmm, interesting. There are no entries in fstab, as I would expect. The drives are auto mounted as /media/sdbx, and appear as icons on the desktop. I will definitely try what you have suggested (I don't get home for another 4 or so hours) and post the results.

Further interestingly:
  If I plug in my USB phone (Nokia N95 8GB), it is recognized, and I can write to it without any problems. Granted, it is probably more like a USB memory stick than a hard drive, but still.

  Just in case anyone asks, I have tried all permutations of drive -> USB port, ie I have 2 drives and 3 USB ports, same result no matter where I plug them in. I didn't think it would matter, but you just never know......

Jon

---

### Post by mc4man on 2008-07-31
> There are no entries in fstab, as I would expect. The drives are auto mounted as /media/sdbx
That's interesting in itself, did you name  the drives sdbx at some point? (set a volume label). If not and if there is no fstab entries then 'what's' telling them to mount at media/sdbx? 
As I mentioned they should mount at /media/<volume name>, (the label).
Did you have them connected when you upgraded or listed in the fstab of 7.10?
Also try giving yourself explicit on internal drives. (you never know)

---

### Post by Hashi on 2008-07-31
I will check. I'm leaving for home shortly, so I'll be back on this thread in about, oh, 2-3 hours.

Thanks for the help!
Jon

---

