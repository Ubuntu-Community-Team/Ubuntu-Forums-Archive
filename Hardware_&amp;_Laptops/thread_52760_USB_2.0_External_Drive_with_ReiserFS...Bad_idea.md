---
title: "USB 2.0 External Drive with ReiserFS...Bad idea?"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by navilon on 2005-07-28
The following drives are formatted with NTFS (With compression enabled) inside USB 2.0 external enclosures
[list=1]
[*]250 GB
[*]200 GB
[*]80 GB
[/list] 

The following drives are formatted with ReiserFS inside USB 2.0 external enclosures
[list=1]
[*]200 GB
[*]200 GB
[/list]

I have been trying to transfer files from the NTFS drives over to the ReiserFS drives . Here a the list of problems i have been having: 

[list]
[*]Recently, when it reaches around the 20th file, the transfer come to a hault and no error is displayed. (It appears to be copying files over to the other drive but it never progresses to the next file)
[*]A few days ago, I would get the following error on a per file basis, "Could not copy the file, 'Generic I/O error'"
[*]There is one file that i copied over that I am not able to remove. If I attempt to, I get a permission denied message
[/list]

The only reasons i could think of that might have something to do with the errors I'm getting are listed as followed
[list]
[*]The compression on the NTFS drives?
[*]The drives being interfaced with USB
[/list]
Any help/comments/solutions/advice/ideas?

---

### Post by jasmuz on 2005-07-28
[QUOTE=navilon]The following drives are formatted with NTFS (With compression enabled) inside USB 2.0 external enclosures
[list=1]
[*]250 GB
[*]200 GB
[*]80 GB
[/list] 

The following drives are formatted with ReiserFS inside USB 2.0 external enclosures
[list=1]
[*]200 GB
[*]200 GB
[/list]

I have been trying to transfer files from the NTFS drives over to the ReiserFS drives . Here a the list of problems i have been having: 

[list]
[*]Recently, when it reaches around the 20th file, the transfer come to a hault and no error is displayed. (It appears to be copying files over to the other drive but it never progresses to the next file)
[*]A few days ago, I would get the following error on a per file basis, "Could not copy the file, 'Generic I/O error'"
[*]There is one file that i copied over that I am not able to remove. If I attempt to, I get a permission denied message
[/list]

The only reasons i could think of that might have something to do with the errors I'm getting are listed as followed
[list]
[*]The compression on the NTFS drives?
[*]The drives being interfaced with USB
[/list]
Any help/comments/solutions/advice/ideas?[/QUOTE]
 Both the compression on the NTFS and the USB interfaces might be your issue.

I recommend you try sticking with EXT3 partitions, as it seems that Ubuntu likes more EXT3 than ReiserFS.

---

### Post by navilon on 2005-07-29
[QUOTE=jasmuz]Both the compression on the NTFS and the USB interfaces might be your issue.

I recommend you try sticking with EXT3 partitions, as it seems that Ubuntu likes more EXT3 than ReiserFS.[/QUOTE]

I would love to use Ext3 but it takes a whopping 9GB out of my 200GB dirves. I cant afford to loose that much  :-| 
Is there anyway to turn that off?

---

### Post by jeremy on 2005-07-29
I have a USB HD 160GB using ReiserFS, no problems at all.

---

### Post by navilon on 2005-07-30
[QUOTE=jeremy]I have a USB HD 160GB using ReiserFS, no problems at all.[/QUOTE]
 Is their anyway to make Ext3 not take up so much space for journaling?

---

### Post by heimo on 2005-07-30
[QUOTE=navilon]Is their anyway to make Ext3 not take up so much space for journaling?[/QUOTE]

I haven't tried it, but there seems to be -J size flag/option for mkfs.ext3, which lets you decide how many megabytes will be used for journal. And there's always the ext2, which is basicly ext3 without journaling.

---

### Post by navilon on 2005-07-30
[QUOTE=heimo]I haven't tried it, but there seems to be -J size flag/option for mkfs.ext3, which lets you decide how many megabytes will be used for journal. And there's always the ext2, which is basicly ext3 without journaling.[/QUOTE]
 Ext2 might be the way to go
Would you reccomend Ext2 even if it is old technology?

---

### Post by heimo on 2005-07-30
[QUOTE=navilon]Ext2 might be the way to go
Would you reccomend Ext2 even if it is old technology?[/QUOTE]

It's proven and matured technology. ;) It lacks journaling, but for most purposes it's good enough. The most probable difference that you'll notice is that if your system goes down uncleanly, fsck (filesystem check) will take longer. Ext3 is mayby a bit more safe, but ext2 is definitely not unsafe. It's always a tradeoff between things like space, speed and how the filesystem handles different filesizes. There's no "one and only" filesystem which is best for everything.

You can always convert ext2 to ext3 later, if neccessary - so why not? If you think about data security, you should never trust only to the filesystem you use, frequent backups are the most important, raid arrays save you from downtime caused by failing hardware and so on. If your main concern is the amount of space, I'd probably use ext2 and tune the block size according the expected avarage file size. (but I'm definitely not an expert on this, check man mkfs.ext2) Check the -m option, which determines the percentage that's reserved for super user, on large volumes it's too big by default.

---

### Post by hewhocutsdown on 2005-09-25
I'm having an identical problem. I have about 5 external drives; 2 are in the reg. 3.5" enclosures, the 3 others are minute drives, about the size of a large wallet, drawing power through USB, and each holding 80GB.

Currently I'm only using the 3 smaller ones. Two are older, and are formatted into 3 FAT32 partitions/drive.  (i've been using them between windows/unix) The last I just formatted as ext3, and have been trying to copy files over from the other 2 FAT32 drives.

It will copy about 100MB-1GB before it will stop, and the time remaining will just jump; I left it running last night and it told me it would take 800+ hours to copy the 32GB, and it was on the 11th file. I have to restart nautilus and unmount/remount the drives to get anything to work, and often get I/O disk error messages if I try and reboot with this going on. 

On occasion I have also seen the ext3 drive unmount itself, with no user input. 

To say the least, it's depressing and downright infuriating, I've been busting my head at this for a couple days with no solutions.  Any help would be greatly welcomed.

---

