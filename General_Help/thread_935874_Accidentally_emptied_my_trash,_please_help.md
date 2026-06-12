---
title: "Accidentally emptied my trash, please help"
date: 2008-10-02
forum: General Help
---

### Post by fancyl on 2008-10-02
I did a google search and searched the forums here, but couldn't find exactly what I need. And I'm kinda freaked out. I spent the past 2 days working on several OOo documents on my ubuntu Hardy desktop. I try to keep all my documents backed up on a flash drive. So I plug in my flash drive and deleted the contents and emptied the trash, and then copied the contents of my folder onto my newly emptied flash drive. But only AFTER doing this, did I realize that I deleted the wrong folder and copied the contents FROM my flash drive TO my desktop!

Am I screwed? Most of the forum posts and help blogs I found were all about recovering lost partitions and failing hard drives.

I haven't restarted my computer, and aside from searching the net for answers, I haven't written anything to the drive. And I don't have the knowhow or the materials to open up the case and plug the disk in elsewhere. 

Any help would be GREATLY appreciated. Thanks in advance! PLEASE!?!

---

### Post by iaculallad on 2008-10-02
Testdisk would probably be the suggested utility in the forums/thread you had read. Try using [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") instead.

An Excerpt from their website:

> Photorec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (thus, its 'Photo Recovery' name) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted.

PhotoRec is free, this open source multi-platform application is distributed under GNU Public License. PhotoRec is a companion program to TestDisk, an app for recovering lost partitions on a wide variety of filesystems and making non-bootable disks bootable again. You can download them from this link.

For more safety, PhotoRec uses read-only access to handle the drive or memory support you are about to recover lost data from. Important: As soon as a pic or file is accidentally deleted, or you discover any missing, do NOT save any more pics or files to that memory device or hard disk drive; otherwise you may overwrite your lost data. This means that even using PhotoRec, you must not choose to write the recovered files to the same partition they were stored on. 

---

### Post by iponeverything on 2008-10-02
Good luck.  I would be interested to hear if it takes you longer pick up the scattered pieces on your drive that it would be to start over.

Something that I did once.  Install a second hard drive and mount it:

dd if=/dev/sda1 of=/mnt/second-drive/bigfile

then use "less", "grep", or the tool of your choice to dig through the pile of bits in "bigfile"

When I did the above, it was to recover evidence. Quite time consuming, but effective.

---

### Post by fancyl on 2008-10-02
Well, I effed it up. Not thinking, and in a panic. I installed Photorec and ran it. As it was running, I realized 2 things. It was recovering ALL the lost files still in the drive, and I didn't have enough disk space for all that. That made me realize that the recovered files were overwriting my deleted documents as they were recovered. So not only do I now have 5 gigs of useless text files and whatnot, but my desired documents are thoroughly overwritten now.

*facepalm*

---

### Post by davidryder on 2008-10-02
"Thoroughly overwritten"

Sorry about your loss, but this did make me giggle a bit.

---

