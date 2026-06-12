---
title: "[SOLVED] how do you convert ext3 files to fat32?"
date: 2008-08-08
forum: General Help
---

### Post by harryliddic on 2008-08-08
How do you convert ext3 files to fat32 so that you may copy them on a shared drive. I have been having my share of problems with QDVDauthor( sparse file errors, inability to load scenes) and I thought I would try a couple of windows programs, Am I deluding myself or can it be done?

---

### Post by ByteJuggler on 2008-08-08
Your question makes no sense.  To clarify: You can directly copy files housed on an EXT3 partition to a FAT32 partition (or vice versa), whether those partitions are located on an external disk or otherwise.  No "conversion" is needed at all.  If what you're saying is you want to convert an existing **partition **from (say) EXT3 to FAT32, that would involve copying all the files on that partition off onto another partition somewhere, then reformatting the EXT3 partition as FAT32, then copying them back etc.

---

### Post by harryliddic on 2008-08-08
I tried **cp** twice and both times I got a file incompatibility message the **permission denied**

---

### Post by ByteJuggler on 2008-08-08
> **harryliddic said:**
> I tried **cp** twice and both times I got a file incompatibility message the **permission denied**

"Permission denied" is not an incompatibility message, it means what it says, ***permission*** denied.  :) It means your user doesn't have permission to perform the copy operation.  Probably because the effective permissions on either the source or target partition is such that your user can't read or write a file you're attempting to copy.

Try prepending your "cp" command with "sudo" to perform the copy as root, which should have permissions even if you don't.  Alternatively we need to figure out what the permissions problem is (probably a mount permissions problem) and correct that.

Edit:
Did you mount the FAT partition from the command line or via your Gnome desktop?  If from the command line, did you specify permissions/ownership defaults for the FAT32 partition?  If not, then note that by default only root will have permission to write to the mounted partition, which would result in "permission denied" when a normal user tries to write to the FAT32 partition.

---

### Post by pmlxuser on 2008-08-08
please place the command you use and target directory

may be u are not the owner of the mounted file system
you could try
using
```
$ sudo cp file /directory/

```

---

### Post by silkstone on 2008-08-08
If you are not the owner of the files or folders on the Ext3 partition, you may not have permission to do anything with them.

You may need to sudo cp, or gksudo nautilus and then copy them, but please be careful!

---

