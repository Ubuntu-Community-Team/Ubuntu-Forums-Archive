---
title: "fsck: How close to death is my hard drive?"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by tomcalloway on 2007-03-13
I noticed for the first time that the Ubuntu fsck check that happens every 30 boots picked up error(s) a few weeks ago.  I do notice a little more noise from the drive, but I can't say it's the sound of the final gasps or not.

I ran fsck -n from a terminal while my Edgy desktop was up and running.  Do the following errors indicate I should buy my new PC/drive now and transfer my data?  I make regular backups, so not too worried.

Here is a summary of the errors fsck showed:

Pass 1:
Inodes found that are part of corrupted orphan linked list ->
  Inode 245542, 2877957, 2877958, 2877959, 2877960
Deleted inode 2877956 has zero dtime

Pass 2:  Pass 3:  Pass 4:   no errors in these

Pass 5: Group summary info
Block bitmap differences:  lots of these (probably 25 were listed)
Free blocks counted do not match
Free inodes counted do not mach
Inode bitmap differences:  a few

If these are normal errors from a rough system shutdown (only 1 in the last 2 weeks I can remember), let me know, and I won't buy that new drive just yet.

I should note that it seems this laptop goes through a disk drive about every 18 months over the last three years.  It's been only 12 since this most recent one was installed.  I wonder if it's the nature of miniaturization, my use, or bad hardware elsewhere on the machine.

Thanks for the help.

---

### Post by milton1 on 2007-03-13
I have had a few rough shutdowns, and never had these errors. It seems likely that your disk has some problems. Since hard disks are relatively inexpensive, I would say replace it now before it causes you more trouble.

---

### Post by dannyboy79 on 2007-03-13
do you use hdparm? do you use the "find" command a lot? these things can impact the life of a hard drive. temperature as well, you should try getting a laptop cooler for when you set your laptop down and see if your drives last longer? good luck

---

