---
title: "file system crash (LVM). now what?"
date: 2008-11-03
forum: General Help
---

### Post by Cruz on 2008-11-03
Hi there,

it's probably the worst nightmare of a sysadmin what just happened to me. The file server makes a small and silent yank and then it goes blank. It doesn't respond to any requests and boots up only to a grub error 2.

I punched in a knoppix CD and all the drives and partitions are still listed like they used to be. There are 3 partitions I'm worried about. 

The first one is ext2 and I can't mount it. I get an error saying ```
mount: unknown filesystem type 'jbd'
``` no clue what to do with that. Can anyone help?

The other two are LVM partitions joined together to one large logical volume. pvscan shows me that there is only 8 MB free of the second volume. I don't quite believe that, but I can't be 100% sure if it's true or not. Anyways, I can't mount the logical volume either. mount tells me to choose a file system type, but I don't remember which type I chose when I created the file system. I tried mounting anyways with ext2, ext3, jfs and xfs. None of those worked, but one of them MUST be right because I never used any other file system. How can I find out which file system is the right one? And then how do I fix it?

Thanks
Cruz

---

