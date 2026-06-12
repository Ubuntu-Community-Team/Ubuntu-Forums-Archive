---
title: "Format for Backup Hard Drive"
date: 2010-09-09
forum: Hardware
---

### Post by 8oluf7 on 2010-09-09
I have invested £55 in a 1TB WD Elements external hard drive from Amazon to hold backups of the various computers in our household, all of which run Linux. 

The drive comes pre-formatted NTFS. I believe that any glitches there were with the early Linux NTFS software have now been ironed out - certainly,  I've never had any problems handling NTFS with Linux. So, the questions are: 
[list][*]What are the advantages/disadvantages of re-formatting to a Linux file system?
[*]If I re-format, which is the best file-system to use, bearing in mind that the primary purpose of the drive is to hold backups, so not losing data is important?[/list]

Mike G.

---

### Post by howefield on 2010-09-09
> **8oluf7 said:**
> What are the advantages/disadvantages of re-formatting to a Linux file system?

I can only give you an opinion, my preference is to back up to the same file system as the source, my backup drive has two partitions, one ext4 and one ntfs.

That's not based on anything scientific, just seems to make sense. 

In your case, I'd format it with ext4.

One disadvantage is that if you wanted to transfer files to another computer that wasn't compatible with the file system, it would make life difficult.

---

### Post by srs5694 on 2010-09-09
If the only OSes you use are Linux, then using NTFS in almost any capacity is a Bad Idea (note the capitalization). The problem is that Linux lacks good NTFS maintenance tools, and it won't mount an NTFS drive that's unclean. Therefore, as soon as there's a power outage, the cat takes a swipe at the cable and disconnects the drive, or some other uncontrolled shutdown occurs, the drive will become inaccessible in Linux. You'll need to either resort to low-level tools like TestDisk to recover your files or find a way to use Windows to fix the disk (the latter is likely to be simpler, especially with a removable disk).

As to what filesystem is best for backups, that depends in part on how you're making them. If the backups will be in a carrier file of some sort, such as a tarball or a disk image file, then it doesn't really matter very much, so long as the filesystem you're using can support big enough files and is reliable. (All Linux filesystems are OK on this score, at least up to the 1 TB disk size you mention.) All the critical data -- filenames, timestamps, etc. -- will be stored in the carrier file.

If you'll be doing a file-level backup (using "cp -a" or the like), then the target filesystem must support the critical filesystem data structures of the original. This is another reason to avoid NTFS, since it doesn't support the standard Linux file metadata, such as ownership and permissions. Linux filesystems all support the same basic features, so you'll be OK backing up any Linux-native filesystem (ext2/3/4, ReiserFS, XFS, JFS, Btrfs) to any other, at least in terms of basic features. A few advanced features, such as ACLs, differ or are optional, so you could lose some information if you rely on such features in the source but the target doesn't support them. There might also be subtle effects relating to the amount of disk space used by files, the order in which files are read from directories, etc.

---

### Post by kpkeerthi on 2010-09-09
ext4. what else?

---

### Post by 8oluf7 on 2010-09-10
> **srs5694 said:**
> [...] Linux lacks good NTFS maintenance tools, and it won't mount an NTFS drive that's unclean. Good point. I'll reformat - ext4 seems to be the recommended choice.

> **srs5694 said:**
> As to what filesystem is best for backups, that depends in part on how you're making them. If the backups will be in a carrier file of some sort, such as a tarball or a disk image file, then it doesn't really matter very much, so long as the filesystem you're using can support big enough files and is reliable. (All Linux filesystems are OK on this score, at least up to the 1 TB disk size you mention.) All the critical data -- filenames, timestamps, etc. -- will be stored in the carrier file.

If you'll be doing a file-level backup (using "cp -a" or the like), then the target filesystem must support the critical filesystem data structures of the original. This is another reason to avoid NTFS, since it doesn't support the standard Linux file metadata, such as ownership and permissions. Linux filesystems all support the same basic features, so you'll be OK backing up any Linux-native filesystem (ext2/3/4, ReiserFS, XFS, JFS, Btrfs) to any other, at least in terms of basic features. A few advanced features, such as ACLs, differ or are optional, so you could lose some information if you rely on such features in the source but the target doesn't support them. There might also be subtle effects relating to the amount of disk space used by files, the order in which files are read from directories, etc.I have been using 'Simple Backup' onto a shared area on one machine and then copying the files onto an external hard drive - so, a bit of both. Another reason for choosing ext4.

Thanks for all your insights.

Mike G.

---

