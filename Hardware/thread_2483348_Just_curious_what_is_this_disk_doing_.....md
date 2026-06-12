---
title: "Just curious what is this disk doing ...."
date: 2023-01-27
forum: Hardware
---

### Post by michael351 on 2023-01-27
I have a recently failed OS boot hard drive (2TB OS & data disk). My data is backed up, but I wanted to recall the directory structure.
I mounted the data partition and began to copy a few key directories over to another drive. I noticed the transfer speed is all over the place, but mostly 0 bytes/sec.
Every few tens of seconds there would be a spurt of transfers approaching many megabytes per second, then kilobytes/sec, then nothing. A few seconds later, another burst.

After awhile, many of my files were showing up and when I opened them (images), they were perfect - no problems.

What is the drive doing that makes it so slow even though the superblock and filesystem were repaired? Just curious how it is managing to copy.

(I just assumed the data would be no good. What a surprise.)

---

### Post by Paddy Landau on 2023-01-28
The most likely explanation is that the system is trying to recover data. This might mean having to read the same block many times, over and over, until it is satisfied that what it has read is OK. A file might contain many such blocks, meaning that this is being done multiple times for a single file. That's why the rate drops to zero.

Nevertheless, you should **not** trust the data from your failed disk unless you can verify it somehow. I've had situations where the system thinks that it has recovered the data OK, but it hasn't; maybe most of the data is OK, but some parts are corrupted. Your backed-up data is the better option. Use your failed drive only for data (such as recalling your directory structure) that isn't available on your backup.

Good luck!

---

