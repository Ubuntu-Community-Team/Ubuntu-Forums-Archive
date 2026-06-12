---
title: "Reinstalled Vista and now Ubuntu wont load"
date: 2008-07-29
forum: General Help
---

### Post by phil81uk on 2008-07-29
Ahhh!

I had a dual boot system with Vista and Ubuntu running. It booted using the Vista Bootloader (I used a tool called Easy BCD to set it up).

I couldn't get Vista to reduce its own partition size any further (because of unmovable system files) so I deleted the partition using GParted, resized it, and reinstalled Vista. Now the Ubuntu partitions seem to be damaged and EasyBCD doesn't recognise the Ubuntu installation. It just doesn't appear in the EasyBCD options as it normally does.

I used an OpenSuse Live CD to try to recover my data from the Ubuntu partition. But Suse sees the partition but it doesn't appear in the My Computer menu (and I don't know how to use Suse, so I didn't try to mount it).

Is there any way that I can recover the data from the Ubuntu partitions at least? I don't mind reinstalling Ubuntu.

Or is there a way of doing an assisted bootup which can then fix the Ubuntu installation?

---

### Post by NilsE on 2008-07-29
> **phil81uk said:**
> Ahhh!

I had a dual boot system with Vista and Ubuntu running. It booted using the Vista Bootloader (I used a tool called Easy BCD to set it up).

I couldn't get Vista to reduce the partition any further so I deleted it and reinstalled it. Now the Ubuntu partitions seem to be damaged and EasyBCD doesn't recognise the Ubuntu installation. It just doesn't appear in the options.

Is there any way that I can recover the data from the Ubuntu partitions at least? I don't mind reinstalling Ubuntu.

Or is there a way of doing an assisted bootup which can then fix the Ubuntu installation?You can boot up with the live CD and potentialy see what is wrong with the Ubuntu installation with the partition manager.  Or worst case possibly get all your data off it

---

### Post by phil81uk on 2008-07-29
I've booted off the Ubuntu Live CD and opened GParted. It sees all my old Ubuntu partitions (root and swap) as one space. I've decided to cut my losses and reinstall.

Sorrt for my panicky post.

---

