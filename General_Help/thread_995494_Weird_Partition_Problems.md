---
title: "Weird Partition Problems"
date: 2008-11-27
forum: General Help
---

### Post by The_Lost_World on 2008-11-27
Alright, here's my annoying, recursive, and yet to be completed journey with installing Ubuntu Linux.

First I downloaded the ISO from the MIT Media Lab mirror. I burned it onto a disk, and checked the disk to make sure everything was right. Everything was in order, so I proceeded to installing it.

Before I had started installing it, I had two partitions on my Windows Vista system, C: and D:. The D: partition was empty, the C: partition had Windows installed. I deleted the D: partition, and this left 68.56 GB of unallocated space on my 160 GB hard drive. Excellent, now I can use the "Use largest continuous free space" option in the Ubuntu installer and it will create a boot and swap partition for Ubuntu automatically using the unallocated space, and leave the Windows partition alone, as well as install the GRUB bootloader.

Unfortunately, when the installer was at 22%, it stopped and have me an error, something about either my install disk was bad, or my system was overheating. So it quit and I went to the Windows partition manager to find that the installer had already created the Ubuntu partitions. So I deleted them and tried the install again in a more cool area. Same error. Again I deleted the partitions that Ubuntu would have used.

Then I noticed that my install disk had a few nasty scratches, so I got a nice new shiny disk and burned a new image, made sure it was done right, etc.

I decided to try and see if this new disk will work. But when I selected the "Use largest continuous free space" option again, something just didn't seem right. The installer seemed to say it was going to use my whole disk for Ubuntu (and in that case, I'd lose my Windows) and that's not what I wanted, I wanted to double boot. Here is an image.

[img]http://i538.photobucket.com/albums/ff341/the_cake_is_a_lie/huh.png[/img]

See the little "before" and "after" bars up there? They look the same on the "Use largest continuous free space" option (which it is on in the image) as they do on the "Use entire disk" option. It says that it's going to use "100%" of the disk for Ubuntu. And that is not what I want.

I've checked the partition manager on both Ubuntu and Windows and it says that the only partitions are two NTFS (one big one, one small one, I'm guessing the big one is for Windows, the small is for swap) and the rest as unallocated.

So my question is, why does it want to supposedly use my entire disk on the "Use largest continuous free space" option now? Isn't largest continuous free space supposed to be unallocated? I have 68.56 GB of it! That's plenty of room.

Oh, and the other question is, am I right about it wanting to use all my whole hard drive, or am I looking at it wrong and it's not actually doing that? lol

---

### Post by psusi on 2008-11-27
Wow, that is really strange.

---

### Post by caljohnsmith on 2008-11-28
How about instead just simply click the "manual" option instead of "guided", and you should be able to install Ubuntu to the unused space just like you want. Let me know if that helps or if you still run into problems. :)

---

### Post by The_Lost_World on 2008-11-28
Yep, I've already decided I'll be going with manual. However there are a lot of options there. What kind of partition, what to name it... all I know is that I need a "swap" and "/" partition, and the "swap" needs to be double my RAM.

Could you show me the steps to a manual install?

---

### Post by caljohnsmith on 2008-11-28
You might also want to do a "/home" partition so you can keep your personal data separate from the main Ubuntu partition, but it's up to you. Here is a guide that I think will help you install Ubuntu via the "manual" partitioning:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

Let me know how that goes.

---

### Post by The_Lost_World on 2008-11-28
Isn't that guide for Hardy Heron and Gusty Gibbon? Didn't the graphical installer change when Intrepid Ibex came out?

---

