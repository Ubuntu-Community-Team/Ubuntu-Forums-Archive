---
title: "Dual-booting XP and 8.10: Partioning Error"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by DeltaVictor on 2009-03-17
I'm trying to dual boot 8.10 on to my old desktop. I managed to free up enough space on my harddrive to get both on and now I'm trying to shrink down the Windows partition. Right now, this is what the drive looks like:
[IMG]http://i2.photobucket.com/albums/y34/ArgonDestroy/ubuntu/partitioncurrent.png[/IMG]

And this is what I'm trying to get it to be:
[IMG]http://i2.photobucket.com/albums/y34/ArgonDestroy/ubuntu/partitionwant.png[/IMG]

I get an error every time I try to do this, and since I'm totally new to ubuntu, I don't know what it means. I attached the error file that GParted gave me.

I'd really rather not completely reformat this hard drive and reinstall windows, but if it comes to that I can.

---

### Post by Mark Phelps on 2009-03-18
The error line that says a feature is not yet supported is a concern.

Despite what some in the Linux community may say, GParted is not the best tool for managing NTFS partitions.  All you have to do is read their notes, FAQs, and release notes to find things that have been "fixed" and other things that still don't work.

However ... the newer version you use, the better it will work.

So, download and burn a new GParted LiveCD, boot from that, and see if it will work without the error message you got.  Maybe the current version now supports this feature.

You can get the GParted LiveCD, and a LOT! else, at distrowatch.com.

---

