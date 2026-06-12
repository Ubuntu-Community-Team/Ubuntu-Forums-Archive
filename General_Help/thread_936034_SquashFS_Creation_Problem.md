---
title: "SquashFS Creation Problem"
date: 2008-10-02
forum: General Help
---

### Post by lhauckphx on 2008-10-02
I'm trying to use Squashfs to create a compressed backup image of a rather large directory (80gb).

The process will run for a while (using cpu and memory, and creating the squashfs file), and then stop working.  

While running top at the same time the mksquashfs process is running I've been able to see the machine run out of memory (both real and swap) during the process.

The mksquashfs process will then still be be in the process table, but not using any cpu or memory, the squashfs archive will not increase in size, and nothing further will be written to the log file.  At this point the size of the squashfs file is usually around 3gb.

The machine has 4gb of memory, and the directory I'm trying to create a squashfs image of is around 80gb.

I've tried both types of compression (lzma and zlib).

I've created 4 - 10 gb squashfs images in the past (not on this machine however).

So to get to the point of my questions:

Is there a limit to the size of a squashfs image that can be created that is constrained by memory?

Is there a limit in squashfs that is related to the length of the directory/filename that I'm trying to archive?

Anyone have any ideas what I should try next?

---

