---
title: "Can't change folder/drive icons on vfat partitions"
date: 2008-10-17
forum: General Help
---

### Post by peterbuldge on 2008-10-17
I'm not quite sure to post this considering I'm using the Kubuntu Ibex beta... but this has been a recurring problem for me ever since Kubuntu Feisty so here goes

I have a dual boot system with xp and Kubuntu installed.  I have two hard drives.  An ide with an ntfs partition for XP and a fat32 partition for docs and music and such that is to be shared with the linux install.

My other drive is a sata drive which has a partition for my linux install, a swap file and another fat32 docs/media partition.

I've reinstalled kubuntu on this machine a bunch, usually whenever a new version comes out I prefer to back up data and start from scratch rather than upgrade, but I've never changed the partition setup.

My problem is that even though my partitions seem to be set up fine and I can write to them and execute files, I can't change any icons on the fat32 drives.  This has been a recurring issue for me.  I only remember finally fixing it once but I can't remember what I did... I think it involved changing fstab.

In /media the only drive that actually shows a drive icon automatically is the ntfs one. The two fat32 drives only show a folder icon that can't be changed.
[IMG]http://img.photobucket.com/albums/v122/peterbuldge/snap02.png[/IMG]

If I browse to the the Documents folder on the fat32 drive, the music, pictures, and videos folders (which I usually put links to in my home and on my desktop in kubuntu) show no icons at all.  Again these cant be changed.
[IMG]http://img.photobucket.com/albums/v122/peterbuldge/snap03.png[/IMG]

Although, if I go ahead and link the folders in the home or desktop the links DO show icons without me having to do anything.  They are just the wrong icons... the KDE crystal icons... which I'm not even using.  Once again, they can't be changed.
[IMG]http://img.photobucket.com/albums/v122/peterbuldge/snap01.png[/IMG]

my fstab is as follows:
UUID=1D56-190C /media/sda1 vfat user,auto,exec,uid=1000,gid=1000,umask=000 0 0
UUID=e361b276-d242-487e-8b30-a06b3b3c39cc swap swap sw 0 0
UUID=87f76b2a-ef7c-4076-a323-ecd7b68578fa / ext3 defaults 0 1
UUID=142C77262C770252 /media/sdb1/ ntfs-3g auto,user,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
UUID=98C0-9C6F /media/sdb5 vfat user,auto,exec,uid=1000,gid=1000,umask=000 0 0
/dev/scd0 /media/cdrom0/ udf,iso9660 user,ro 0 0
/dev/scd1 /media/cdrom1/ udf,iso9660 user 0 0

This isnt really a huge issue because so far the drives work fine.  It just bugs me that I cant have links with the right icons on my desktop.  I've done a lot of reading and poking recently to see if I could find out how to fix this once and for all.  I saw something somewhere about how sometimes a drive can end up still being owned by and old install.  I get no permission errors on my fat drives.

Otherwise I figure its just a mistake in fstab.  Anybody have any ideas?

---

### Post by klickverbot on 2009-11-05
There is a bug at KDE bugzilla on this: [https://bugs.kde.org/show_bug.cgi?id=208855](https://bugs.kde.org/show_bug.cgi?id=208855)

---

