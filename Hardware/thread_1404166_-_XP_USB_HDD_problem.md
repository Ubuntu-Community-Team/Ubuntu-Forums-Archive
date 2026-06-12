---
title: "- XP USB HDD problem"
date: 2010-02-11
forum: Hardware
---

### Post by charg3r on 2010-02-11
Hi everyone,

First up, im a real newbie to linux so hopefully there is a simple solution. I'm running Ubuntu 9.10 on an Asus G1S laptop. I connect USB hard drives to it that work fine, the problem is when i then connect the same hard drives to a computer running windows XP. The machine running XP cant read any of the files or folders on the hard drives after they have been connected to the laptop running ubuntu. When i open the drive i cant see any files or folders under XP, only a recycle bin folder. When i open the drive in Ubuntu I can see all the files and folders in the drive (about 20ish).

You should also know that the drive was originally only ever connected to an XP machine and worked fine. It was only when i put Ubuntu on my laptop and connected the drive to it that this happened. I have a feeling it is because i didn't "safely remove the drive", so im doing that from now on but im not sure how to get it working again in XP.

Thank you,

---

### Post by SecretCode on 2010-02-11
What file system is on the drive? I'm assuming either ntfs or fat32.

(Also, how many drives? And do you mean flash-memory sticks or real spinning hard disk drives? What sizes are the drives and hwo full are they?)

You definitely need to unmount, eject or safely remove drives in Ubuntu, just as you do in Windows.

How to recover the drives already 'damaged' depends on the file system.

---

### Post by charg3r on 2010-02-11
> **SecretCode said:**
> What file system is on the drive? I'm assuming either ntfs or fat32.

(Also, how many drives? And do you mean flash-memory sticks or real spinning hard disk drives? What sizes are the drives and hwo full are they?)

You definitely need to unmount, eject or safely remove drives in Ubuntu, just as you do in Windows.

How to recover the drives already 'damaged' depends on the file system.

Number of drives: 3
File system: all ntfs
Type: all "real spinning" hard drives
Size: 100-250gb ish pretty much full

Ive used getdataback for NTFS to "recover" some files into XP. I just thought since i could view the files in Ubuntu there may be some other issue involved. Im really looking for a way of making the files viewable in XP again, rather than spending alot of time recovering files. I'm also looking for confirmation that it was because I did not "safely remove the drive" that this issue occurred, so i can be assured it wont happen again.

Thanks for the help so far,

---

### Post by SecretCode on 2010-02-11
Not safely removing the drive is quite likely to be the cause. But whether it might happen again for some other reason ... make sure you have backups. Anything can happen on a writeable file system!

Unfortunately you're talking about quite a lot of data. I was going to suggest copying the files elsewhere and reformatting.

Even though it's a lot of data you should try to copy the data elsewhere - we don't know exactly what the error is and it's possible it could get worse.

When you connect the drives to XP do you get a drive letter assigned? If so, try
```
chkdsk x: /f
```
if x: is the drive letter.
Preferably on the drive with the least valuable data / one with all the data backed up elsewhere.

If you can't do that, try **ntfsfix** in Ubuntu (part of ntfsprogs - **ntfsfix -h** for help). This will fix what it can and mark the drive for a scan next time it's used in Windows (not sure if that only applies if the drive is attached at boot time).

---

