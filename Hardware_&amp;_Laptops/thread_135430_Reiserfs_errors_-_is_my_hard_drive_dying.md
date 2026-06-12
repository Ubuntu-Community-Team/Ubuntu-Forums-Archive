---
title: "Reiserfs errors - is my hard drive dying?"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by Ububurns on 2006-02-23
Recently I had some trouble removing some files from my computer.  I could not remove them as myself, or by using sudo, as root.  I managed to do so in the end with the help of a live cd - but with much difficulty.

In response to this problem I checked out, in System Log, any error messages that might show what the problem is.  To my complete surprise, I found I'm often receiving, fifty or more times a minute, the same messages, repeated again and again:

[SIZE="1"]ReiserFS: hda5: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [188 20743 0x0 SD]
ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [188 20735 0x1 DIRECT], item_len 320, item_location 2648, free_space(entry_count) 65535
ReiserFS: hda5: warning: vs-5150: search_by_key: invalid format found in block 0. Fsck?[/SIZE]

These three messages, as I said, are constantly  repeated.  No figures change , so it seems to be identifying the same problem.

I am very concerned about this problem, as my previous hard drive's reiserfs partition corrupted not long ago, leaving me with huge problems.  Any help, or information about these errors, would be greatly appreciated.

---

### Post by pestilence4hr on 2006-02-23
Are you using hdparm?

---

### Post by Ububurns on 2006-02-23
I haven't changed anything with hdparm, except for enabling DMA for the cdrom (which was weeks ago).

---

### Post by ShiftyPowers on 2006-05-24
Ububunrs, did you ever find out what hte problem was?  I have a similar issue and warning when trying to delete a particular file.

---

