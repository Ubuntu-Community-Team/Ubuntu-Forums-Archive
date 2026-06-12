---
title: "Prevent windows from mounting shared ntfs partition"
date: 2012-12-08
forum: Hardware
---

### Post by smooth_dudes on 2012-12-08
Hi there


I am currently running a dual-boot scenario with 2 harddisks. 1 disk is a 32 gb ssd, on which i have ubuntu installed. The other is a 500gb hdd on which i have 2 partitions, one 50gb on which windows is installed, and another 450gb partition on which i have all my documents, media, etc.

Originally i planned to use this 3rd partition to share stuff between windows and ubuntu. And it works fine, except for the fact, that windows randomly deletes stuff from the partition!!!??? I have never experienced this kind of behavior before, and so to prevent any further data loss, i would like to prevent windows from further accessing this partition. The obvious way would be to just change the format to ext4, but i have alot of stuff on that drive, and it is really bothersome to move all of it back and forth.

So i was wondering, if there is any flag or similar, which can prevent windows from mounting, simply making windows ignore the partition?

Kind regards.
(Sorry if this is the wrong forum by the way - i thought this was somewhat hardware related.)

---

### Post by oldfred on 2012-12-08
Do not know how not to mount a partition in Windows. Of course you change to a Linux format. But then you have to fully backup as that would erase current data.

But the issue of missing files is often caused by Hibernation of Windows. Since Windows is hibernated it does not know about changes made by Ubuntu and then the file seems to disappear in Windows.

---

