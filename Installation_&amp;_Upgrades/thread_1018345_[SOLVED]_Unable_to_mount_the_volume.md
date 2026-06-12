---
title: "[SOLVED] Unable to mount the volume"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-12-22
I have vista-ubuntu dual booting.
I want use an external hard-disk,I already put somethings on it by using vista, now I am trying to use the same external hard-disk with ubuntu, i am getting Unable to mount the volume the error.
with a long error message.
$ log file indicated uncleaned shutdown(0,0) failed to mount dev/sdf1....
NTFS is marked to be in use....
options.
1.disconnect the window.....
2. you can use force option mount -t ntfs.....
my problem as i am suing dual bootking i don't know weather i should use the proposed command.

---

### Post by jpkotta on 2008-12-22
If you mount it readonly, there shouldn't be any chance of corrupting the filesystem.  ```
mount -o ro /dev/sdXX /media/blah/
```

It is probably OK to do whatever the error message said.  It's been a while, but I remember getting messages like that the last time I mounted an NTFS fs.  I did what they said, and it eventually worked.

If the messages make you nervous (they made me nervous), you should copy the data off and reformat as (V)FAT.  FAT is the lingua franca of filesystems, everything supports it.

---

### Post by vanadium on 2008-12-22
The error message is clear. The ntfs volume was not properly disconnected from Windows. In that case, Ubuntu will not automatically mount the disk for safety.

Solution: boot again into Windows, then disconnect the drive using the "Safely remove hardware" icon. Alternatively, shut down Windows completely (no hibernate).

@jpkotta: There is nothing to be nervous about. As long as you have also Ms-Windows on your system (or, in case of a removable drive, available on another computer), it is perfectly safe to use ntfs with Ubuntu.

Ubuntu will mount healthy, clean ntfs file systems only. Just make sure you keep it that way (disconnect properly, check regularly under MS Windows).

Only for users using only Linux do I recommend to reformat to ext3.

---

### Post by suhtek on 2008-12-29
I have had this dirty-mount problem with a removable drive several times and found that remounting/dismounting under windows did nothing for me. The solution that worked easiest for me was a program called ntfsfix. It's part of the ntfsprogs package in the repositories. 
Once you've added this package you can simply enter the command:
sudo ntfsfix /dev/sd??   
where ?? should be your drive designation (ie sda1 sdb2 whatever)

---

