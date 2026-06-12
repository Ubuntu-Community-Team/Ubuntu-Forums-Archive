---
title: "Wipe Server Keeping Files"
date: 2008-10-20
forum: General Help
---

### Post by mewejo on 2008-10-20
I want to wipe all my server Ubuntu 8.04 to destroy all settings and keep all files.. eg... keep all home direcories and wipe everything else...

HOW?! :(:confused:

Thanks in advance :)

---

### Post by freelinuxhelp on 2008-10-20
If your /home directory is on its own partition, you can just reinstall, formatting all of the partitions except the one /home is on. If it's on the same partition you're looking at a different situation. I've read about moving the /home directory to a different partition, but I haven't tried it.
There's always backup-->reinstall-->restore

---

### Post by mewejo on 2008-10-20
How would I go about restoring EVERYTHING back say 3 days??

Or the nearest point?

That would save my life!

I finaly have Samba working, but it is VERY SLOW. God knows why, both on Mac nd PC, it just slows right down when I open a folder full of files.

Also I deleted a user using userdel and it deleted the home directory of that user.. if I restore... can I get them back, all the files?

Im not a complete noob to Ubuntu as i've learnt a fair bit about it while pulling my hair out with it... if you know what I mean.

Thank a lot in advance :)

Josh

Age 16 :)

---

### Post by freelinuxhelp on 2008-10-20
Well, the method to restore files depends on how you created the backups. If you didn't create a backup three days ago, you won't be able to recover deleted files from three days ago.

---

### Post by mewejo on 2008-10-21
is there any recoverey software available? :confused::confused::confused:

---

### Post by freelinuxhelp on 2008-10-21
Hmm, sounds like you want to undelete, not recover from backup. That's an entirely different situation, sadly, one I can't help you with as I've never done it.

---

### Post by WRDN on 2008-10-21
If you have deleted files on an ext2/3 partition, then you could try using [Disk Internals' Data Recovery Software]("http://www.diskinternals.com/linux-recovery/") to get it back. The software runs on Windows, or you can download a disk image, and boot from the CD.

---

### Post by mewejo on 2008-10-21
Ok, im running that program on the drive as we speak...
it found no 'lost partitions' and its now searching for files..,.

Hopefully it'll be done by morning :)

Thanks :):)

---

