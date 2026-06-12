---
title: "Live CD Crashed while partitioning, destroyed my hdd?"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by GodsDead on 2009-10-28
I cant belive this just happened, i was partitioning my HDD into two segemnts, so i could have all my documents on one partition and the OS on the other, 6 mins left, and the whole live CD freezes. I had no other option but to restart the machine, and bringing up the Partition editor, dousnt even pick up my HDD now.

This is a massive problem. its my main HDD, on my main computer.

I have no idea how to fix this, please can someone help!

I dont get why the disk crashed at all, its a fast DVD drive, 2GB ram Duel 3.2GHz processors.
I used the ubuntu 8.10 live disk.

---

### Post by dabl on 2009-10-28
Setting aside that "destroyed my hdd" is way lurid and overblown, what is the real problem?  Is there valuable data, not backed up, that needs to be recovered from the drive, or is it just that you need to know how to partition the drive?

---

### Post by presence1960 on 2009-10-28
Not to be a wise guy, but did you read any material about installing Ubuntu (or any OS for that matter) and/or partitioning. If you did you would have seen one of the top suggestions is to back up your data before attempting such operations. it is a sound suggestion for many reasons, the most notable being Murphy's law- **** can & will happen, we just can't predict when.

Now if I were you I would boot the Live CD and use testdisk to try and recover your files. You can go to the [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") home page to find out more info about testdisk.

Other suggestions you may find helpful after trying to fix your problem are:

1. **_ALWAYS_ back up data**
2. Before resizing windows defrag at least two times.
3. Turn off system restore and your page file until after the windows partition is successfully resized.
4. Never resize Vista with anything other than Vista's own disk management utility. See [here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") for an as yet unresolved bug report when using an outside partitioning tool to resize Vista.

I would suggest you read some here prior to trying to install Ubuntu paying attention to #3 & #4 : [https://help.ubuntu.com/8.10/switching/index.html](https://help.ubuntu.com/8.10/switching/index.html)

---

### Post by earthpigg on 2009-10-28
are you having problems restoring your backup, repartitioning, or the subsequent operating system(s) install?

---

