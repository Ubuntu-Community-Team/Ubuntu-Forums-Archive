---
title: "Partition type that can be shared among major OS?"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by kartal on 2008-12-12
Hi

Is there any partition format that can beb shared among, Ubuntu, Macos and Windows? I am thinking to create a  seperate data partition that can be shared among all.

thanks

---

### Post by Therion on 2008-12-12
FAT 32 is the short answer but you'll run into the 4GB filesize limitation.

---

### Post by cariboo on 2008-12-12
I would suggest NTFS, so that you don't run into the 4Gb limit. Ubuntu has good read/write support for NTFS. I would also suggest installing ntfs-progs, several ntfs utility programs. NTFS-progs can be installed using Add/Remove Programs, Synaptic Package Manager and of course the command line.

Jim

---

### Post by kartal on 2008-12-12
Hi

thanks for the answers. Is there any linux based partitions that can be shared as well?

---

### Post by Therion on 2008-12-12
NTFS is fine for Windows/Linux compatibility but the Mac OS doesn't support *writing* to NTFS.  

FAT 32 is the only format that will support full R/W access between all three OS'es.

---

### Post by Partyboi2 on 2008-12-13
Is it possible to read/write to ntfs from a mac by using  ntfs-3g and macfuse?

---

### Post by networm1230 on 2008-12-13
fat32 work for both ubuntu and windows us partition editor

---

### Post by cloudslayer on 2009-01-01
Hi

Sorry for bringing up this old post, but I'm having a similar question to this one, and it hasn't really been answered here...

The problem with FAT32 is the file size limit... I'm planning to make a shared data partition as well (but only shared between Windows and Linux).

I currently see a few possibilities:

FAT32: Filesize limit, so really a no go for a data partition... If I'm not mistaken files on a very large FAT32 partition tend to take MUCH more disk space than necessary because of the limited allocation table...
NTFS: works on linux (according to cariboo907)
EXT3: This is a linux filesystem and windows drivers can be found for it (but i'm not sure whether they're very stable as I've only rarely used them. I don't know about mac support)
ReiserFS: same thing as the previous one... never used it though so I REALLY don't know about this one

I wonder: which is best: linux support for NTFS or windows support using the EXT3/ReiserFS drivers (and which one of those two would be best?)
If there isn't much difference concerning those, which of the three would be fastest/most secure?

---

### Post by snova on 2009-01-01
> **cloudslayer said:**
> Sorry for bringing up this old post, but I'm having a similar question to this one, and it hasn't really been answered here...

It's not that old...

> I wonder: which is best: linux support for NTFS or windows support using the EXT3/ReiserFS drivers (and which one of those two would be best?)
If there isn't much difference concerning those, which of the three would be fastest/most secure?

Define "secure".

Perhaps transparent encryption? I know of no Linux filesystem that has this, and I doubt that the NTFS driver supports it.

---

### Post by stderr on 2009-01-01
I tend to go with ext3 and NTFS as I don't need Mac support. I've had ext3 running fine under Windows, and NTFS now natively runs fine under Ubuntu (and without too much difficulty on other distros). However, I prefer ext3, and am (still...) slowly migrating my drives from NTFS.

Some people use a/some small FAT32 partitions, just as a dump for transferring files between OSs. I mean, everything can read/write FAT32. I would propose that as a solution - if you have enough HDD space.

> **Partyboi2 said:**
> Is it possible to read/write to ntfs from a mac by using  ntfs-3g and macfuse?

I was wondering the same thing the other day. I would have thought it would be possible.

edit: I was just thinking about it as I clicked Post, and it struck me that Macs should have very little difficulty in reading/writing to ext3. A 1 second Google proves me right :) I see no reason not to use ext3, in that case. E.g. first link: [http://forums.macosxhints.com/archive/index.php/t-61597.html]("http://forums.macosxhints.com/archive/index.php/t-61597.html")

---

### Post by cloudslayer on 2009-01-02
With security I was actually referring to safe storage as in smallest risk of data loss

So ext3 with windows drivers is the way to go (probably for sharing with Mac too). I'll be reformatting my disk later today.

Thanks

---

### Post by RansomStark on 2009-01-02
I use this too occasionally access my ext3 partition from Windows when I need a few files etc.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Its pretty good and freeware.

---

