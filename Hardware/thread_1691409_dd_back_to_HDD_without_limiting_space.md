---
title: "dd back to HDD without limiting space"
date: 2011-02-19
forum: Hardware
---

### Post by agreimann on 2011-02-19
Hello, all.

I've got a very quick question for anyone. How can I dd an image from a 7.3 GB disk back to a 40 GB disk without limiting the 40 GB disk to 7.3 GB?

Any ideas?

So far, I can dd if=/dev/sda of=/dev/hda, but that leaves only 7.3/40 GB on the other side when finished.

If anyone has any clue about how to get dd images "out of the box", please let me know (such as if it's possible). All help is **greatly **appreciated. Thank you!

---

### Post by YesWeCan on 2011-02-19
You might find something here [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by agreimann on 2011-02-22
Thank you... but this is not what I was asking. I have been working with Linux for several years now, I've read the man page for dd, and have worked with partitioning with the parted command, however, I'd like to restore a disk for someone using the files I backed up.

The problem is that when I dd /dev/sda (the removable disk) from the root directory (partitions, map, etc.) to the hard disk (/dev/hda), then a 40 GB disk becomes, in effect, a 7.3 GB disk with 32.6 GB shamefully wasted. After using dd, parted will see it but gparted will not.

I'm wondering how I can restore the contents of the removable disk without this limitation.  In other words, restore the 7.3 GB but have the ENTIRE disk be 40 GB, with ~32 GB left over.

Can anyone help me on this, please? Is there any command that can do this?

Thank you, all. :)

---

