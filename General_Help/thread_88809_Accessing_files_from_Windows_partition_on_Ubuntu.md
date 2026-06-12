---
title: "Accessing files from Windows partition on Ubuntu?"
date: 2005-11-11
forum: General Help
---

### Post by Ravager on 2005-11-11
Hey folks!
Long time Windows user here and I decided to try out Linux for the first time today at home, and I must say I'm extremely impressed with the quality of this OS and all the free goodies that come with it.

However, I installed this OS on my hard drive that also has Windows XP on a separate partition. My other third partition contains all my photos and music and is formatted as an NTFS partition. Is there any way for Ubuntu to recognize this third partition and make all my music and pictures accessible to me?

I'd really enjoy this cross-platform compatibility.

---

### Post by El_Boti on 2005-11-11
Hi, did you try mounting the partititon ??

If not here is a link that can help you.

[http://www.ubuntuguide.org/#windows]("http://www.ubuntuguide.org/#windows")

I hope that this can help you.

---

### Post by farfargoth on 2005-11-11
if the partition you want to access is called hda2 (first disc, second partition), then you should add this to your /etc/fstab:
/dev/hda2  /media/ntfs  ntfs auto,users,ro,gid=ntfs 0 0
then you create the group ntfs and add every user you want to be able to access the files to that group. 
Then you create /media/ntfs and then you use 'mount /media/ntfs' to mount the partiotion. You only need to do this once.

---

### Post by capcorn on 2005-11-11
Hi Ravager,

I am a long time window user like you who just started using linnux.

If you are using ubuntu, you can use DISKS to mount your windows partition. It has a nice GUI for mounting windows partition. Try it out! You should be able to find it in the menu.

DISKS will show you the all the partitions in your hard disk. Enjoy!

---

### Post by cedjo on 2005-11-11
NTFS filesystem is actually supported as a read-only filesystem, so you'll not be able to write on your XP partition, only read...

---

### Post by Ravager on 2005-11-11
[QUOTE=cedjo]NTFS filesystem is actually supported as a read-only filesystem, so you'll not be able to write on your XP partition, only read...[/QUOTE]

Why is it "read only"?

---

### Post by bonzodog on 2005-11-11
um...because of MS and the fact that they won't give anyone the protocols for writing to NTFS. It's worth noting that you can't read or write an NTFS partition from a FAT32 (win98 etc) either. There was a project running for a while attempting to work out how to write to NTFS from linux, but it's difficult, unstable, and can damage NTFS partitions.

---

