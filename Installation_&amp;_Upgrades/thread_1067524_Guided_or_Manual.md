---
title: "Guided or Manual"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Nerd2 on 2009-02-11
My existing system is Windows XP/Pro on a 500GB Drive.  The drive has already been partitioned; XP is on a 300GB partition (which must remain), and there are two partitions of about 100GB.  I want to install Ubantu (current version) on to one of the two empty partitions.
When I start the process, the Guided install recognizes the 3 partitions, but seems to indicate that it is going to use the entire 500GB!  Very bad....so....
I started the Manual Process, but it stops me with a message "No root file system is defined.", and then asks me to use the Partition editor to correct this.  But when I start the partition editor, it indicates that it will destroy the existing partitions....yikes!
Suggestions?

---

### Post by agim on 2009-02-11
If one of the two partitions are COMPLETELY erased, you should be able to choose, "Install in the largest continuous free space", or something like that.

It seems that this is not the case, so go to System->Administration->Partition Editor and choose an empty partition to delete. Let the partitioner delete it, and start the install process over.

---

### Post by Nerd2 on 2009-02-12
I had to delete one of the existing partitions, then I was presented with the option to install into the "free space".  Now it's completed.

Thanks.:KS

---

