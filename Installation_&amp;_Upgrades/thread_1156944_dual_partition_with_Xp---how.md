---
title: "dual partition with Xp---how?"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by willywonky on 2009-05-12
i installed ubuntu 9.04 on my new laptop with no probs (except no sound!)
as i don't have sound i want to now install xp and ubuntu.
I tried installing xp from cd, thinking i could then install ubuntu as a dual partition afterwards... but when I put in the xp cd, it goes through loading stuff then when its about to start windows, it hangs with a message saying check your hard drive for corruption, do you have any viruses etc.
I guess I should have installed xp first but I was hoping to get by with ubuntu only!  Can anyone help?

---

### Post by willywonky on 2009-05-12
i found the instructions from the ubuntu guide on how to do this.. the first three steps are
1.  create a ntfs partition for windows
2. backup the boot sector eg. dd if=/dev/hda of=/mbr.bin bs=512 count=1
3. install windows

i've downloaded gparted to do step no 1, but don't know how to use it.
I have no idea about step 2
can someone help?
many thanks in advance!

---

### Post by ubunRyan518824 on 2009-05-12
just install windows first

---

### Post by willywonky on 2009-05-12
to update the question.. it looks like a first have to reduce the size of sd1 using gparted in order to free unallocated space in order to create the ntfs parttion.
But when i try to unmount it it says it cannot be unmounted from mount point /, most likely other partitions are using this mount point and you are advised to unmount them manually.
i have no idea at all how to do this!!
at the moment there are three partitions, /dev/sda1, /dev/sda2 and /dev/sda5

help!

---

### Post by willywonky on 2009-05-12
i can't install windows because it crashes if i try to
i can't install windows first because i don't have a time machine... didn't realise it was so much harder this way around!

---

### Post by Mark Phelps on 2009-05-12
> **willywonky said:**
> to update the question.. it looks like a first have to reduce the size of sd1 using gparted in order to free unallocated space in order to create the ntfs parttion.
But when i try to unmount it it says it cannot be unmounted from mount point /, most likely other partitions are using this mount point and you are advised to unmount them manually.
i have no idea at all how to do this!!
at the moment there are three partitions, /dev/sda1, /dev/sda2 and /dev/sda5

help!
You should go to the distrowatch.com website, download the latest GParted LiveCD, and burn it to disc (CD).  You'll find it at the bottom-left of the page under Latest Distributions.

Then, boot with that to do partition work.  It won't automatically mount any partitions.

---

### Post by daftbeaker on 2009-05-12
Alternatively, if you installed Ubuntu with a live cd then put that back in and choose to run Ubuntu from the cd.  Open a terminal, type "sudo gparted" (without the speech marks) and that should open Gparted without mounting the hard drive, letting you alter the partitions.

---

