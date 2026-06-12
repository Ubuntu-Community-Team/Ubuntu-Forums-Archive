---
title: "Wipe on my hard disk"
date: 2011-06-03
forum: Hardware
---

### Post by pardesi on 2011-06-03
I got a new hard disk from my laptop manufacturer and have to return him the old one. So i decided to run 4 passes of wipe on it(that is the old laptop). I was dual booting Ubuntu and Vista on it. Is it safe enough to be given out or is some more 'deletion' needed?

---

### Post by JohnBonne on 2011-06-03
> **pardesi said:**
> I got a new hard disk from my laptop manufacturer and have to return him the old one. So i decided to run 4 passes of wipe on it(that is the old laptop). I was dual booting Ubuntu and Vista on it. Is it safe enough to be given out or is some more 'deletion' needed?


What it is that you are trying?
n fact there is nothing you need more to do than format the hdd. You may find wiping it to have clean, unrecoverable information. I have a feeling if ahrd drive is wiped it would be more efficient, like washing a chalkboard wiping the dust off of it.
It that not what you are trying to do?

---

### Post by pardesi on 2011-06-03
I want to securely erase all the information in my hard disk before it goes to a third party to prevent all reasonable attempts at recovery of data. For that I would believe formatting alone would not suffice. Hence I used [wipe/]("http://wipe.sourceforge.net"). I was wondering if three passes of wipe would suffice given that I was dual booting Ubuntu and Vista.

---

### Post by yetiman64 on 2011-06-03
I am not familiar with the wipe utility you used, but if you have done 4 passes over the full drive it is very likely no data will be readable by file recovery utilities.

If you want to make completely sure you could run a zeroing pass with the shred command from a live cd. This will set every bit on the drive to a 0 (sometimes called a factory reset), and has the advantage of not showing what previous passes were done to the drive.

From a live cd terminal run,  **Note this command by itself will render all data unreadable on the drive you specify.**
```
sudo shred -f -n0 -v -z /dev/sdX 
``` where X is the drive letter for the drive you want to erase. After running this open gparted on the live cd and go to Devices menu > Create Partition Table > set an msdos partition table and apply the changes. The drive can then be formatted if you wish or left as unallocated space (but is still usable with the partition table restored).
Using ```
man shred
``` will explain what the switches above do or you can look [[COLOR=Blue]--here--[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10896044&postcount=3") (look about half way down the post)

I do think you are safe as you currently describe the situation, a zeroing pass is only an added precaution.

---

### Post by whatthefunk on 2011-06-03
> **pardesi said:**
> I want to securely erase all the information in my hard disk before it goes to a third party to prevent all reasonable attempts at recovery of data. For that I would believe formatting alone would not suffice. Hence I used [wipe/]("http://wipe.sourceforge.net"). I was wondering if three passes of wipe would suffice given that I was dual booting Ubuntu and Vista.

I dont really know how wipe works, but it probably does the same thing every time you run it so one pass would be the same as a thousand I would think.  Use wipe and then do a fresh install with one OS using the entire disk.

---

### Post by pardesi on 2011-06-03
Thank you Yettiman64.

---

