---
title: "File System (Linux and Windows)"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by sprucio on 2006-11-20
I recently bought a new USB drive for backing data files. I'm looking for a file system that will be able to read and write in both Linux and Windows.

To most, the obvious choice would be FAT32. The problem with this is this is that this FS has a size limitation.

Currently, I have a 500GB drive that I would like to partition at 500GB and not split into multiple partitions.

I have done some research and found EXT2 IFS for Windows. Has anyone used this and does anyone have any ideas on what other file systems might be a better choice?

---

### Post by KhaaL on 2006-11-20
I use ext2 IFS and it works excellently with both ext2 and ext3. The only limitation is that it wont store the right permissions. also I don't know how it handles links, but it still works fine. Just follow the instructions on how to unmount the device before physically disconnecting it.

---

