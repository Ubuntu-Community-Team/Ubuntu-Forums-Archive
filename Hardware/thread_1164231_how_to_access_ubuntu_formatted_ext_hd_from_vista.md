---
title: "how to access ubuntu formatted ext hd from vista"
date: 2009-05-19
forum: Hardware
---

### Post by sonaural on 2009-05-19
need to know how to access my ubuntu formatted external hd from windows (or even mac os x).  is there any program that allows that?  dual boot?  live cd?

there was an earlier post that might have been a solid fix but all the ntfs, ext3, smd, jargon kinda lost me.  please help?
[http://ubuntuforums.org/showthread.php?t=504690](http://ubuntuforums.org/showthread.php?t=504690)

---

### Post by utnubuuser on 2009-05-19
Having a "Shared" folder on the HDD doesn't cut it?

---

### Post by sonaural on 2009-05-19
i can't even get windows to recognize the hd.  by "shared" folder do you mean dual boot and then create a folder which both can access?

not sure i know how to do that can you link to a tutorial?

---

### Post by coffeecat on 2009-05-19
By external drive, I presume you mean a USB drive. I'm afraid you're going to have to learn a bit about filesystems (ext3, ntfs, etc) so let's take it slowly.

FAT32 is an old Microsoft filesystem. Advantage - every OS can read and write to it out of the box. Disadvantage - it has a maximum filesize limit of 4GB, so could be a problem if you want to store things like video files.

NTFS is a newer Microsoft filesystem. Both Windows (naturally) and Ubuntu can read and write to it out of the box. By the way, the link you posted is 2 years old and talks about installing ntfs-3g drivers in Ubuntu. That's no longer necessary. NTFS has a much larger filesize limit than FAT32 and is journalled (which is an advantage). One disadvantage - MacOS can only read NTFS. You can install ntfs-3g in MacOS so that it can write to NTFS, but that's a complication.

Ext3 is the most common Linux filesystem, and the one your Ubuntu installation probably runs on. Since Windows won't recognise your drive, I guess you've formatted it ext3. There are ext3 drivers for Windows but personally I wouldn't use them. MacOS won't be able to read your ext3 drive, and I don't know whether there are ext3 drivers for MacOS.

HFS+ is the MacOS filesystem. Linux can... No, let's not go there. Keep it simple. :)

What I would suggest is to format your USB drive with either FAT32 or NTFS depending on the size of files you might want to store. I prefer NTFS, but bear in mind that MacOS can only read it. If you want to create a NTFS partition in Gparted, you need to install ntfsprogs from Synaptic.

---

### Post by utnubuuser on 2009-05-20
By shared I meant: right click folder, then select "share folder", but that's only for for files ON the hd.  I don't think you can do that with an entire drive.

I'm currently in Debian Lenny, and in that system, you can select the desktop hd icon, richt-click, go to "properties" and select "shared", in the same way you can select "share folder" in Ubuntu.

---

