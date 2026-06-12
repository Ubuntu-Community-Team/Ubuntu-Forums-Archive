---
title: "NTFS removed, how to recover?"
date: 2016-10-04
forum: Hardware
---

### Post by ktatar156 on 2016-10-04
My Friend deleted NTFS partition - 900 GB and created two: 100 GB for  Ubuntu and 800 GB for NTFS. The problem is that she doesn't shrink  partition, but deleted it :/ I want to try to recover it. State for now  is: 100 GB ext4 and 800 GB free space. Is there any way to deal with that?
I've used testdisk 'quick search' which was really slow from 10%. After finish it found only that 100 GB with ext4. Any other solution? Maybe creating in that 800 GB free space some NTFS patrition and using some software to recover files?

---

### Post by Bucky Ball on 2016-10-04
_DO NOT_ create anything on that disk. In fact, don't even use that disk. Boot from a Ubuntu install disk or repair disk and NOT the disk you are trying to retrieve data from. 

If you want to retrieve data from it the worst and most disasterous thing you can do is use it for anything other than recovering files from. It's like this. When something is deleted, the data remains and the area it 'lives' in is marked as 'writable'. Until something is written on it, the data will remain.

If you then start fiddling around with the partition and disk you will succeed in writing data over the data which is on the blocks marked 'writable' but which in fact still contains your data. 

'Delete' is a misnomer. Nothing is deleted. The blocks where the data lives are simply marked as 'writable'.

Can't help other than to advise testdisk, which you've already tried, and possibly photorec, which it doesn't sound like you have. My advice would be to download the [SystemRescueCD ISO]("http://www.system-rescue-cd.org/SystemRescueCd_Homepage"), create bootable media from that and use that. It contains testdisk, photorec and a bunch of other handy fixing tools.

---

### Post by ktatar156 on 2016-10-04
Hi,
thanks for fast replay!

But how to use photorec or other software with that 800GB 'free space' (I know that there is still that data in NTFS, but how to use that on that 'blank' space?) And is it possible to recover data from first 100GB that is already formated to EXT4 (before there was one 900 GB NTFS)?
Delete these two partition and create again one 900 GB NTFS?

---

### Post by Bucky Ball on 2016-10-04
> **ktatar156 said:**
> Delete these two partition and create again one 900 GB NTFS?

No. Re-read my last post carefully as you appear to have missed some very important points. ;) If you want any chance of getting the data back you shouldn't use the drive at all unless you are trying to retrieve data with a suitable data retrieval tool running from USB or CD.

If it was one 900Gb partition then try a deeper search with testdisk if that's possible and see if it finds it. See [this page for some tips with testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") and download SystemRescueCD from the link in my last post. If you're trying to retrieve a partition while you are running testdisk on the drive you are trying to retrieve the partition from that ain't gonna work.

---

### Post by Mark Phelps on 2016-10-04
I've generally found that Windows data recovery apps do the better job of recovering Windows filesystems, Linux data recovery apps, Linux filesystems.

Your best bet for recovering data now is to do the following:
1) Remove the hard drive from the PC
2) Purchase a USB-to-Hard Driver adapter kit
3) Download and install this utility on a working WINDOWS PC: [http://www.majorgeeks.com/news/story/recover_data_in_3_steps_with_minitool_power_data_recovery_free_edition.html](http://www.majorgeeks.com/news/story/recover_data_in_3_steps_with_minitool_power_data_recovery_free_edition.html)
4) Connect the old drive to the working PC
5) Run the data recovery utility to see what can be retrieved from the old drive.
 
If that tools does not find what you need, an alternative is Recuva:  [http://www.piriform.com/recuva](http://www.piriform.com/recuva)
 
And, if that does not work well, the best tool out there is this one, but only the trial version is free:  [http://www.file-recovery.com/](http://www.file-recovery.com/)

Good Luck

---

### Post by mastablasta on 2016-10-06
marked #5 post for possible future use.

i am curious though why would the OP need to do use USB enclosure case or similar? why not just connect the drive  to SATA port on another PC?

---

### Post by ktatar156 on 2016-10-10
> **Bucky Ball said:**
> No. Re-read my last post carefully as you appear to have missed some very important points. ;) If you want any chance of getting the data back you shouldn't use the drive at all unless you are trying to retrieve data with a suitable data retrieval tool running from USB or CD.

If it was one 900Gb partition then try a deeper search with testdisk if that's possible and see if it finds it. See [this page for some tips with testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") and download SystemRescueCD from the link in my last post. If you're trying to retrieve a partition while you are running testdisk on the drive you are trying to retrieve the partition from that ain't gonna work.

Thanks! I've used photorec to scan whole disk (because I haven't got option to use only in 'unallocated space'), set filters to important files (autocad, jpg, png, etc.) and it works! Thank you very much :)

---

### Post by Bucky Ball on 2016-10-11
Excellent. If you're happy, please see the last, blue link in my signature at the bottom of this post and mark the thread as 'solved' to help others. Good luck.

---

