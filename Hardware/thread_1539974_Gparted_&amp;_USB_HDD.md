---
title: "Gparted &amp; USB HDD"
date: 2010-07-27
forum: Hardware
---

### Post by SagnaB on 2010-07-27
I am having a bit of trouble figuring out how to use Gparted to resize an NTFS partition to include 48Gb of unallocated space. The unallocated space came from the resize of a FAT32 partition on the same drive (iomega 300Gb USB).
I have included an image to help you understand what I mean a bit better.

Thanks for any/all input

---

### Post by VH-BIL on 2010-07-27
Here is a youtube video on how to do it
[http://www.youtube.com/watch?v=out5gC_C5E8](http://www.youtube.com/watch?v=out5gC_C5E8)

by the way, you have to unmount to make changes to a device.

---

### Post by SagnaB on 2010-07-27
Thanks VH-BIL and yeah I figured out I had to unmount before making changes, thats how I resized the FAT partition
--
Okay I watched that vid and it was pretty straight forward, but as you can see in the image I attached depicting my own circumstance, this is not a simple resize.
What I would like to do (if it's even possible(but I think it is)) is "move" the unallocated 48GB to the left and "merge" it with the 220GB NTFS partition.
The problem seems to be the FAT is in between the unallocated and the NTFS.

The Gparted Documentation doesn't seem to contain information reflecting my circumstances either (but why would it lol).

---

### Post by VH-BIL on 2010-07-27
Did you manage to resize the NTFS partition?

---

### Post by SagnaB on 2010-07-27
oh sorry, no I haven't managed to resize it yet. I have posted in the gparted forums also.
Oh and yes, I did search before I posted lol :wink: quite thoroughly and found lots and lots of info about resizing and NTFS and NTFS errors etc, but nothing (that I could decipher) that would assist me with my task.
Hmm

---

### Post by VH-BIL on 2010-07-27
Did the youtube video help at all?

---

### Post by SagnaB on 2010-07-27
Not really. It was very long for what it was and contained a lot of stuff that could have been edited out ie booting etc.
The simple resize it displayed I already knew how to do, as I resized the FAT partition earlier.

Thank you all the same though.

---

### Post by VH-BIL on 2010-07-27
I just had a look at your picture. The unallocated space is not next to the NTFS partition so you can not resize it. Maybe you can resize the FAT to take up the unallocated space then resize it to leave unallocated space in between the NTFS and FAT

---

### Post by SagnaB on 2010-07-27
Hmmm I think I know what you mean...

Do you think there is a higher chance for data loss this way? Reason I ask is the way gparted displays the partitions graphically, it would seem to me that reallocating the unused space to that part of the FAT partition might over write that part of the disk with "zeros", if you know what I mean.
Not that I really care if I loose the data, coz its all B/up, but save me having to copy over all the files agian.

Anyway, I will try that soon, and let ya'll know how I go.

---

### Post by VH-BIL on 2010-07-27
If it is all backed up then I would just delete the partition, resize the NTFS then recreate the FAT

---

### Post by SagnaB on 2010-07-27
Yeah I would do that except I really don't want to copy all those files back onto the USB HDD and restructure them to how they have to be (when I mentioned they were backed up I meant that they existed on another computer but in a completely different structure). Not only that, the computer they're on, for some reason has very slow USB speeds.

---

### Post by VH-BIL on 2010-07-27
You have 165.66 free on the NTFS drive, you can copy the structure there and then copy it back.

If not move the FAT partition in gparted then resize the NTFS.

I would go with the 1st option as you have a backup if anything went wrong. Moving a partition takes about the same time any way.

---

