---
title: "External HD taking a long time to unmount"
date: 2010-05-09
forum: Hardware
---

### Post by NMFTM on 2010-05-09
About seven hours ago before I went to bed I transferred about 130GB of data onto an external HD formatted to NTFS using esata and went to shut down my computer (running Lucid) without unmounting it. I just woke up and my computer is still on and at the Ubuntu progress bar a screen. I felt the hard drive and it's very hot, so it must be doing something. When I tried to unmount from within the OS using the GUI I got an error message. Which is why I just went to shut down with it mounted. I figured that it might unmount the HD that way. Should  I just turn off my HD manually and hit the restart button on my computer?

Is actual data being transferred to the HD or is it just checking the integrity (like hashing) of the files that I transferred? I know that Linux likes to delay allocate data to hard drives, but when the actual file transfer progress bar says data is being copied. Is it actually necessary to safely remove/unmount the drive?

Also, I've noticed that drives (HD or flash) that are partitioned with NTFS seem to take a lot longer to unmount or safely remove than drives formatted to FAT32. Why is this?

---

### Post by P4man on 2010-05-09
I remember having terrible performance writing to ntfs volumes that had a too small cluster size. In my case that was due to converting the filesytem from fat32 to ntfs in windows without reformatting. It would cause very high cpu usage and transfer speeds would start reasonably with large files, but drop to a few kbs per second after a while and eventually it would stop doing anything. 

Formatting the drive to ntfs from within linux fixed that, without causing any trouble in windows.

Not sure that is the issue you are having, but figured Id post anyway.

---

### Post by NMFTM on 2010-05-09
It's now been going for 11 hours. I'm just going to hit the off button on my computer.
> **P4man said:**
> I remember having terrible performance writing to ntfs volumes that had a too small cluster size. In my case that was due to converting the filesytem from fat32 to ntfs in windows without reformatting. It would cause very high cpu usage and transfer speeds would start reasonably with large files, but drop to a few kbs per second after a while and eventually it would stop doing anything.
It probably has to do with having to convert the files between Ext4 and NTFS block sizes. Because stuff would transfer at about 50MB/s when I was transferring from Ext4 to NTFS but about 90MB/s from NTFS to NTFS. I also noticed it used an abnormally high amount of CPU power.

EDIT: It only used a lot of CPU power when I transferred from NTFS to NTFS, not Ext4 to NTFS. Which I find strange.

---

