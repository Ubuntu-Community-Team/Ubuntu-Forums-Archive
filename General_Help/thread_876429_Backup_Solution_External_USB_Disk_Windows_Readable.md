---
title: "Backup Solution External USB Disk Windows Readable?"
date: 2008-07-31
forum: General Help
---

### Post by Fynn on 2008-07-31
Hi all,

I've a headless Ubuntu server running Samba / SVN / Apache / BlueDragon / MySQL / SqueezeCenter / Postfix etc.  I'm trying to put together a backup regime which will use an external 500GB USB disk.  One interesting problem is that I might need to access the files directly from my XP laptop (via USB, not Samba) when I'm away.

Two questions then:
  - What would be the best filesystem to use?
  - Where do I need to start looking in terms of software / scripts?

I'm fairly new to Linux (6 months or so) so any pointers welcome.

---

### Post by sarang on 2008-11-19
I would use ext3 on the external drive and install stuff in windows to make it readable in windows. This is because I am not sure if FAT32 or NTFS would preserve permissions on the backed up files, which is important for backups. [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows) might be useful for this.

Also, my article '[HowTo: Automatically launch a backup when a particular external drive is connected]("http://ubuntuforums.org/showthread.php?t=984671")' could be useful for script pointers.

---

### Post by Fynn on 2009-04-12
OK, so this conversation makes an Ent Moot look like a dialogue from the West Wing...

Definitely right about using ext3, though.

Something very weird has just happened...

My /etc/fstab file creates a mount point for /dev/sdc1 (the disk in question) at /mnt/backup

The backup script ran whilst /dev/sdc1 was umounted and disconnected.  I assumed that it would fail gracefully, but 

a) I appear to be able to browse data in /mnt/backup (it's still not mounted?!)

and 

b) I'm out of disk space.

Any ideas?

---

### Post by Fynn on 2009-04-12
All back to normal, seems fairly clear what happened, but still surprised that attempting to write to an unmounted volume apparently caused the mount point to be silently moved elsewhere, rather than failing completely. Can anyone explain this behaviour?  What would've happened had I not deleted the existing /mnt/backup folder before re-mounting the external disk?

---

