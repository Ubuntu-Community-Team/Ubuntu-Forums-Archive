---
title: "External drive access denied"
date: 2008-07-05
forum: Hardware
---

### Post by katsuma on 2008-07-05
Hi there, since i am using ubuntu 8.04 and windows xp, occured to me a strange problem...

Before i could have full access to the external drive on ubuntu and winXP, but now i have full access on ubuntu and not on winXP, there are some folders that say :

"G:\blabla is not accessible. Access Denied" .

So i think is related to some permissions of ubuntu put on the folders... it's just my thought.

Hope someone has a solution to this :D.

Thanks.

---

### Post by LinuxRocks713 on 2008-07-05
Is  your external drive formatted with FAT or NTFS?

To check, use ```
fdisk -l
```.

---

### Post by katsuma on 2008-07-05
sorry i forgot to mention it.
it's in NTFS format

---

### Post by LinuxRocks713 on 2008-07-06
> **katsuma said:**
> sorry i forgot to mention it.
it's in NTFS format

Well, then are your documents in your NTFS Drive owned by root? If so, then you need to go into Windows XP as Administrator, right click on your NTFS Drive, go to permissions tab and give everyone "Full Control".

---

