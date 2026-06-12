---
title: "External Hard Drive"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by Hoosier205 on 2007-03-23
Well, I just installed Edgy last night. Everything is going fine and I'm enjoying it.

Now, when I plugged in my external hard drive via USB...it shows up on my desktop. I can open it, view files, open files....but I can't move anything to it. It's read only....

How do I fix this?

---

### Post by daynah on 2007-03-23
Check the formatting of the external drive (Dapper had a "Disks" app, but I don't know where it is in Edgy. Try installing Kdisks. It's a general all around good thing to have). If it's Ext2, that's a microsoft format that Linux can't write on. No way, no how. If it's NTFS then by default Linux can't write on it, but we can change that.

NTFS-3g is a program that allows Linux to write to NTFS drives, and the guide is right here... [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

If it's Ext2, I suggest backing your stuff up (wince) somewhere else, reformatting it, THEN doing NTFS-3g, testing it out, making sure it worked, then putting all your stuff on your harddrive. If it's NTFS, you SHOULDN'T have any data loss (I haven't heard of it), so I wouldn't worry about putting it somewhere else, since you don't have to reformat.

To reformat, use gpartition

---

