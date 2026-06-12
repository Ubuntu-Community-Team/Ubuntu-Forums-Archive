---
title: "Overwritten inodes on ext3 partition"
date: 2010-05-15
forum: Hardware
---

### Post by phoenix.bg on 2010-05-15
On one disc, (ext3 partition on External USB HDD), was executed the command:
```
e2fsck /dev/sdc1
```
Message is displayed:
```
Group 2485's block bitmap at 81428480 conflicts with some other fs block
```... and many similar others;

Then I entered:
```
e2fsck -y /dev/sdc1
```
... and waited to complete the restoration of inodes.

When the partition is already mount and open normally, he seems empty - all files and folders missing!

Is it possible to restore the previous version of inodes or something else to be done, to have again access to the files :confused:

What are the options?
----------------------------------------------------------------------------------------------------------------------------------------------------------
Problem cannot be solved;
Thread closed.

---

