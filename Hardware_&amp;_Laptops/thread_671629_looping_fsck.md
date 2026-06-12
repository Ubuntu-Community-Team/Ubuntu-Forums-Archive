---
title: "looping fsck"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by nebulus-design on 2008-01-18
I've got an ext3 partition on an external usb drive that has some file system errors and I'm trying to fix it.
I run "fsck.ext3 -y /dev/sdc2" and it starts of happily fixing the problems which look like:

Group 754's inode table at 24707079 conflicts with some other fs block.
Relocate? yes

Group 754's block bitmap at 24707072 conflicts with some other fs block.
Relocate? yes

There are a load of them, eventually it seams to scan the drive, then outputs a load of lines that look like this:

Error allocating 1 contiguous block(s) in block group 754 for block bitmap: Could not allocate block in ext2 filesystem
Error allocating 1 contiguous block(s) in block group 754 for inode bitmap: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 754 for inode table: Could not allocate block in ext2 filesystem

Then starts from scratch again, it doesn't seam to do anything at all just sit in this endless loop.

I thought it might be fixing some small piece each time so I left it going for a while, but it never seams to actually do anything.

I've tried pointing it to different superblocks but that shows the same results...

Any ideas anyone?

---

