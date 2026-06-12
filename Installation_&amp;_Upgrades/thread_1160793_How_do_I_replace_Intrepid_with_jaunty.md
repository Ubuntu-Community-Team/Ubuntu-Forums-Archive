---
title: "How do I replace Intrepid with jaunty?"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by jdunn on 2009-05-16
How do I completely replace Intrepid with Jaunty without disturbing my Vista partitions.

I currently have two Windows Vista partitions and one partition with Ubuntu 8.10 installed.  I wish to replace 8.10 with 9.04 on the Ubuntu partion while keeping the two Vista partitions as is.  I'm afraid of upgrading because I've heard its messy...I'd rather do a clean install.  I tried a clean install from CD but the "mixed install" option doesn't completely remove 8.10...It only allows me to resize the partition (with the slider) to make room for 9.04.  No matter how much room I make for Jaunty, It still leaves about 9 GB for Intripid.

---

### Post by pbpersson on 2009-05-16
Backup all critical data on your machine!

You would do a clean install of Jaunty

Use manual partition setup

Choose as your root partition the current 8.10 partition and tell it to format as ext3

Choose the current swap partition as the new swap partition (it will find this automatically if you don't tell it)

Install

---

### Post by jdunn on 2009-05-16
> **pbpersson said:**
> Backup all critical data on your machine!

You would do a clean install of Jaunty

Use manual partition setup

Choose as your root partition the current 8.10 partition and tell it to format as ext3

Choose the current swap partition as the new swap partition (it will find this automatically if you don't tell it)

Install

Thanks.  I had a feeling that was the way to go.  I already backed up everything I wanted from the 8.10 install.  but I really can't back up the Vista partitions.

---

### Post by pbpersson on 2009-05-16
> **jdunn said:**
> Thanks.  I had a feeling that was the way to go.  I already backed up everything I wanted from the 8.10 install.  but I really can't back up the Vista partitions.

Why can't you grab the most important data?

The data you cannot live without should always be backed up in case of a drive crash anyway.

When you are installing Jaunty, one wrong click and one of those partitions could be gone.  It is up to you.....

---

### Post by jdunn on 2009-05-16
> **pbpersson said:**
> Why can't you grab the most important data?

The data you cannot live without should always be backed up in case of a drive crash anyway.

When you are installing Jaunty, one wrong click and one of those partitions could be gone.  It is up to you.....

There is no "most important data" on my Vista partition.  My computer is a laptop that came with Vista preinstalled + vista 10GB backup partition.  All I keep on there is Vista, openoffice, virus and firewall software.  I keep vista installed in the event I'll need to use MS Visual Studio/C++.  Anyway, its a huge harddrive.

---

### Post by jdunn on 2009-05-16
Great Success!!  it worked flawlessly.  Thanks pbpersson.

---

### Post by lisati on 2009-05-16
> **jdunn said:**
> Great Success!!  it worked flawlessly.  Thanks pbpersson.

That's good to hear.

I can relate to your initial apprehension: after a muckup making a backup of a recovery partition on one of my machines, in anticipation of being able to delete it and restore it later if I choose to (and wasting a couple of DVDs) I'm seeing if the set of recovery CDs I made when I first purchased the machine are still in working order. If one of them turns out to be a dud, the machine will immediately become a candidate for "Ubuntu only"!!!!

No doubt many aspects of keeping your installation(s) the way you like it will become less nerve-taxing over time.

---

