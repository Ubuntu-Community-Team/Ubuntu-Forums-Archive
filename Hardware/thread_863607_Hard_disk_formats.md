---
title: "Hard disk formats"
date: 2008-07-18
forum: Hardware
---

### Post by trevorsowers on 2008-07-18
I am using Hardy Heron to run Azureus.  I am going to use an external USB hard drive to store the files on.  I tried using FAT32 but got write errors from Azureus (I think because of the files over 4GB).  So I am wondering what you would suggest as the best format for the disk to simplify permissions etc.  Also I have two Macs in the house so a format that they could read would be useful but not necessary.  I formated the disk to ext3 but that created write permission problems.  I also tried HFS+ which Ubuntu read but I could not write to.  

Please suggest what my best format would be.

Thanks.

---

### Post by SunnyRabbiera on 2008-07-18
Well worse comes to worst you can try to format it to ntfs, it should be possible to do that.

---

### Post by coffeecat on 2008-07-18
> **SunnyRabbiera said:**
> Well worse comes to worst you can try to format it to ntfs, it should be possible to do that.

+1

That's what I used to transfer some large files from Ubuntu to my Mac. NTFS read-write works a treat out of the box in Hardy Heron, and Mac OS will read from (but not write to) NTFS.

In fact, I'm slowly coming round to using NTFS more widely for external drives and shared partitions simply because it avoids permission issues.

---

### Post by trevorsowers on 2008-07-31
Thanks for the advice.  I have been using NTFS for a week now with great success.  I also found a way to make my Mac read and write to NTFS.  Check out [http://applicationtidbits.com/ntfs.html]("http://applicationtidbits.com/ntfs.html") for the instructions.

---

