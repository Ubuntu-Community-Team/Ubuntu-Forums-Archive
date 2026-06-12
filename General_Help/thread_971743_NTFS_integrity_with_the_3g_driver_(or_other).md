---
title: "NTFS integrity with the 3g driver (or other)"
date: 2008-11-05
forum: General Help
---

### Post by jdackle on 2008-11-05
Hi everyone,

I'm thinking of sharing the Windows Vista Documents folder with Intrepid.I.e.:
(*Ubuntu 8.10*)/home/user/Documents -> (*Windows Vista*)C:\Users/user/Documents
In yet another way to put it(!), I'll be writing my Linux produced documents onto the Vista's NTFS Documents folder.

I've poked a bit around the forum and noticed on several threads people mentioning that NTFS write-support is not 100% reliable (or at least as reliable as onto FAT32).
I've also noticed those threads are not very recent though...

Now for my personal experience: I've used NTFS-3g in the past (several months ago) and there was this safe-procedure to always check the NTFS after writing to it from Ubuntu...
I've also checked the NTFS-3g FAQ and noticed several chkdsk's complaints are actually chkdsk bugs!...

**So my question is: can I nowadays safely write to Vista's NTFS without concerns regarding its post-write integrity?**
Note this will be the Ubuntu Documents folder I will continuously write to and read from everyday...

Please also note I will NOT grant Windows access to any ext3 partition on my system, thank you! :p

---

### Post by jdackle on 2008-11-06
Bump ?

---

### Post by mssever on 2008-11-07
As far as I know, read/write actions with NTFS-3G are perfectly safe these days, which is why it's now the default in Ubuntu. Because NTFS is journaled, you could make a case that it's safer than FAT32--although FAT32 is better-understood.

---

### Post by soro2005 on 2008-11-07
At some point, word was that the ntfs-3g driver was safer and more secure than the ones used by Windows. I think it is very well tested and stable, and of course also used by many people. So one would hear a quickly were there any major problems.

I've had problems with Windows writing to an ext partition. So if sharing it is, the NTFS will have to be the choice that gets my full confidence. Of course, you cannot define permissions.

---

### Post by jdackle on 2008-11-09
Thanks for the replies, guys! :)


> **mssever said:**
> As far as I know, read/write actions with NTFS-3G are perfectly safe these days, which is why it's now the default in Ubuntu. Because NTFS is journaled, you could make a case that it's safer than FAT32--although FAT32 is better-understood.

Regarding NTFS journalising, the Wikipedia says (as of October 20th 2008 ):
> NTFS-3G does not yet support full NTFS journaling, so unexpected computer crashes or power loss can leave the file system in an inconsistent state.
Of course, FAT32 does not deal better with "unexpected computer crashes or power loss"...
But just to confirm what you were saying, you were probably referring to NTFS being safer under Windows, right, mssever? Then again, soro2005, you've mentioned ntfs-3g was said to be safer and more secure than the Windows original ones so...
Still regarding the Wikipedia word, I've asked about it in the NTFS-3G home's forum two days ago - still no reply. Will share it with you guys once I do get one though. ;)

For the moment, I'm thinking I will be creating a "third" partition (besides Windows and Ubuntu's system partitions (and corresponding swaps which I don't use directly of course) to save the user data to. And it will be NTFS.

But still looking for more info on this though...

Cheers!

---

### Post by cariboo on 2008-11-09
No file system is 100% safe, always have a good backup plan if your data is important to you.

Jim

---

### Post by jdackle on 2008-11-09
> **cariboo907 said:**
> No file system is 100% safe, always have a good backup plan if your data is important to you.

Jim

Not that I actually needed that advice but it IS a GOOD ADVICE! Thanks! ;)

---

### Post by mssever on 2008-11-09
> **jdackle said:**
>  But just to confirm what you were saying, you were probably referring to NTFS being safer under Windows, right, mssever?I wasn't specifically referring to Windows, since I didn't know that NTFS-3G doesn't fully support journalling. I don't put valuable data on NTFS--I use ext3. After all, I wouldn't deal with valuable data in Windows, anyway. :)
> Then again, soro2005, you've mentioned ntfs-3g was said to be safer and more secure than the Windows original ones so...
As far as security goes, I assume you're referring to things like permissions or NTFS encryption. Because the Windows permissions model is completely different--and incompatible--from the Linux one, the NTFS-3G driver ignores NTFS permissions. As far as encryption goes, I really have no idea whether NTFS-3G supports NTFS encryption. But there are a number of possible options for encryption if you want it.

---

### Post by soro2005 on 2008-11-09
> **mssever said:**
> As far as security goes, I assume you're referring to things like permissions or NTFS encryption. Because the Windows permissions model is completely different--and incompatible--from the Linux one, the NTFS-3G driver ignores NTFS permissions. As far as encryption goes, I really have no idea whether NTFS-3G supports NTFS encryption. But there are a number of possible options for encryption if you want it.

Actually, I was referring to the reliability of read/write operations, and to the odds to get your fs screwed because of a bug in the driver. At some point several years ago, about the time when the ntfs driver for Linux went from experimental to stable, there was word that it was tested so thoroughly, and that ntfs had been reverse engineered so carefully, that the linux driver produced less errors than the Windows one. Again, this is from years ago, and Microsoft isn't sleeping, either. It just goes to say that there was a lot of confidence that the project had reached a very sturdy and mature state.

I don't know about encryption, but the permissions stuff obviously doesn't work. So, to share the drive among several users, go ext3 or whatever.

---

### Post by jdackle on 2008-11-09
Thank you both soro2005 and mssever for bringing this up.

I do realize Linux UID/GID have no meaning in NTFS (or FAT32 for that matter).
I also believe file/directory ownership in Windows (however it keeps track of and uses it) means nothing to Linux either - but it would be super if it did!

Now, I also do realize ext3 (or another native Linux fs) will be more secure than NTFS et al Windows fs's.
BUT my point is that Linux is safer than Windows as OS's are concerned. Hence it should be easier for someone to get access (remote or locally-wide) to my machine from a running Windows on my machine than from a running Linux.
With this in mind, I prefer to grant Linux access to an "Windows partition" than the other way around.

Now I do realize the ext3-fs-driver for Windows mentioned in some threads in the forum can be configured to access this partition and not that one (I think even this directory and not the others).
Still, can't this configuration be rewritten, specially from someone with access to my machine (a notebook) but also remotely?

---

### Post by jdackle on 2008-11-10
Regarding the Wikipedia claim about NTFS-3G not fulling supporting journaling, szaka, lead developer of NTFS-3G confirms. But he/she also says it is no big issue because with today disk/disk-controlers caches, data-loss can occur with a sudden crash or power-failure regardless of journaling.
[http://forum.ntfs-3g.org/viewtopic.php?t=999](http://forum.ntfs-3g.org/viewtopic.php?t=999)

---

### Post by mssever on 2008-11-10
> **jdackle said:**
> Now I do realize the ext3-fs-driver for Windows mentioned in some threads in the forum can be configured to access this partition and not that one (I think even this directory and not the others).
Yes, the ext3 driver simply maps a given partition to a given drive letter, ignoring the permissions. So if the driver is installed, it just takes a quick trip to the control to get full rw access to all ext3 partitions. Ultimately, though, the only way to have true security is to use some form of encryption.

---

### Post by jdackle on 2008-11-10
On another issue regarding sharing between Windows an Linux, from the NTFS-3G forum, I had confirmation that Interix style Windows weblinks (included in Vista or available as download inside the Windows Services for Unix) are supported by the ntfs-3g driver and Windows junctions compatibility is being worked on. :)

---

