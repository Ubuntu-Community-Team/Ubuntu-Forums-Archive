---
title: "Defragmenting your hard drive."
date: 2008-10-19
forum: General Help
---

### Post by Randomness6454564 on 2008-10-19
What if I ran the Ubuntu live cd, took all, and I mean all, of the files on my C: and copied them to an external hard drive then erased the C: and copied the files back. This would certainly defragment my hard drive but would there be any negative consequences? Would Windows (xp) still load? thanks!!!

---

### Post by p_quarles on 2008-10-19
No. That would not work. You will have a corrupted filesystem, missing symlinks, no master boot record, and quite possibly more filesystem fragmentation than before.

---

### Post by gnudoc on 2008-10-19
are you thinking of using the ubuntu live cd to defragment your windows installation?

as you probably know, the received wisdom is that typical linux filesystems like ext3 (the default on ubuntu) are much more sane than fat32 etc and don't really need defragmenting. So if that's what you mean, then there's probably no need.

i did once try something similar to what i think you are proposing, except that i used knoppix and i didn't do it for defragmenting but just to see what would happen. the result was a system that didn't boot up! :)

---

### Post by az on 2008-10-19
> **Randomness6454564 said:**
> What if I ran the Ubuntu live cd, took all, and I mean all, of the files on my C: and copied them to an external hard drive then erased the C: and copied the files back. This would certainly defragment my hard drive but would there be any negative consequences? Would Windows (xp) still load? thanks!!!

No, it wouldn't.   But you can use the partition editor to shrink your windows partition to as small as it will let you, and then grow the partition back up.  That should accomplish some defragmenting.  It probably wouldn't be very efficient.

---

### Post by 3rdalbum on 2008-10-19
> **az said:**
> No, it wouldn't.   But you can use the partition editor to shrink your windows partition to as small as it will let you, and then grow the partition back up.  That should accomplish some defragmenting.

That will fragment the system further, as contiguous files that are stored near the end of the partition will be moved into little spaces near the front of the partition. Either that, or it won't move any files at all, accomplishing nothing.

---

### Post by BDNiner on 2008-10-19
You could just use the default defrag tool in windows. That would be the best way to defrag your drive. Is there something wrong with you windows installation that is preventing you from booting to it?

---

### Post by Randomness6454564 on 2008-10-19
> **BDNiner said:**
> You could just use the default defrag tool in windows. That would be the best way to defrag your drive. Is there something wrong with you windows installation that is preventing you from booting to it?

No, It boots just fine. I have been running windows for over four years now without a reinstalling it once (or a backup for that matter (which I have done now)). And now the hard drive is pretty fragmented. The idea is similar to this: if you had usb drive and the files were very fragmented for some reason, One method would be to defragment it like normal. The other way is to copy all of the files off of it then delete the stick, and copy the files back. Since each file would be copied back one at a time the data for all the files would be contiguous. So I figured why wouldn't that work for my hard drive?

The reason I am using Ubuntu Live CD is so that I have access to the C: so I would be able to copy the files then move them back. You can't do that while running windows for obvious reasons.

I'm aware of defrag programs but I can be kind of a perfectionist. I figured this would be very thorough.

---

### Post by MaxIBoy on 2008-10-19
If you're a perfectionist, jkdefrag not only defrags your hard drive better than the default Windows program, it actually organizes the sectors of your hard drive! (See, the "beginning" of your hard drive can be read and written faster, so commonly used data should be moved to the first few sectors for a nice performance boost.)

Not only that, as long as you're not actually saving new files, you can continue to use your computer normally while it runs. It's a very well-made program.


You should always defragment *before* you do any messing around with the partitions. ANY partition activity carries risk of data loss, which can be almost eliminated by defragmenting.

---

### Post by jerome1232 on 2008-10-19
If you want to avoid fragmentation in the first place, put your page file on it's own separate partition (similar to how Linux uses a swap partition) and don't let the disk fill up. Files shouldn't really be getting fragmented this way.

---

### Post by MaxIBoy on 2008-10-19
I don't know-- NTFS never ceases to astound me.

---

### Post by BDNiner on 2008-10-21
> **Randomness6454564 said:**
> No, It boots just fine. I have been running windows for over four years now without a reinstalling it once (or a backup for that matter (which I have done now)). And now the hard drive is pretty fragmented. The idea is similar to this: if you had usb drive and the files were very fragmented for some reason, One method would be to defragment it like normal. The other way is to copy all of the files off of it then delete the stick, and copy the files back. Since each file would be copied back one at a time the data for all the files would be contiguous. So I figured why wouldn't that work for my hard drive?

The reason I am using Ubuntu Live CD is so that I have access to the C: so I would be able to copy the files then move them back. You can't do that while running windows for obvious reasons.

I'm aware of defrag programs but I can be kind of a perfectionist. I figured this would be very thorough.

Ok i get it now. if it is the partition that you boot from then you cannot copy the files off, format the drive and then copy them back. you will not copy important files from the hidden boot partitions and the computer won't boot until you recreate the boot partitions (which is not fun and can be time consuming if you don't know what you are doing). but if it is a secondary drive then that could work. i can't say yes or no until i try it myself.

---

### Post by Randomness6454564 on 2008-10-23
Ok then. I'll put off trying this when I don't have anything to lose. Thanks guys!

---

### Post by psusi on 2008-11-07
> **jerome1232 said:**
> If you want to avoid fragmentation in the first place, put your page file on it's own separate partition (similar to how Linux uses a swap partition) and don't let the disk fill up. Files shouldn't really be getting fragmented this way.

This really won't do a thing.  Once the swap file is created, it doesn't go anywhere, so it isn't going to do anything to the fragmentation level of the disk.  As long as you create it when the disk is relatively not fragmented/full ( like when you first install windows ) then it should be contiguous or have very few fragments.  There is no reason to have a separate partition for the swap file.

---

### Post by jimv on 2008-11-07
You can always run a defrag from the Ultimate Boot CD!

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

