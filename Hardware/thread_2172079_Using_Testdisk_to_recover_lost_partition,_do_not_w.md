---
title: "Using Testdisk to recover lost partition, do not want to lose previously saved data"
date: 2013-09-03
forum: Hardware
---

### Post by JWilliams8200 on 2013-09-03
Hello Ubuntu world, switched from XP to Ubuntu about 6 months ago and so far so good!

I have a problem with a hard drive, i have been reading up on Testdisk, but i am lost and need some help. 

So i took my 3tb hard drive used for data storage only, out of my xp computer and put it in my Ubuntu box, but when i mounted the drive only 1 parttition shows up. For anyone that knows, windows xp is limited on hard drive size so when i formated the 3tb originally i had to make a 2.2tb and a 750gb, i used the 2.2 for pictures, video, and music, and i used the 750 for all my important documents. When i mount the drive in Ubuntu the 2.2tb drive is showing up with the correct label and i have had no problem accessing that date, but the other 750gb partition is not showing up. 

First i would like to say i know my terminology is probably a little off. I do realize there is in fact only one partition dividing the drive into 2 parts, but for lack of a better term i call each side a partition. The 2.2tb partition shows up and i can access the data. The 750gb partition does not show up.

So i installed testdisk, ran the quick search and it found my 1st partition (2.2tb) but nothing else, after running deeper search it appears that it is finding 2 partitions, equating to 3 drives. 1st is my 2.2 partition, then something in the middle then apparantly my 2nd partition the 750gb, but when all is said and done this is adding up to 5tb of data, which i assume is not possible. So please help! What steps do i follow to recover my data? 

Also i tried putting the drive back into my xp computer. The drive did not show up in My Computer. I went to disk management and it shows up there, with a 2.2 parition that it cannot assign a drive letter to and asks me to format it, and 750gb in RAW format, which again it asks me to partition. 

This is my first time reaching out on a forum like this for help so im really hoping for a response!

EDIT: Here is the final outcome of the deeper scan.

The harddisk (3000 GB / 2794 GiB) seems too small! (< 5823 GB / 542
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start   End  Size in sectors

>  FAT16 <32M           226270  204  45    490641  34 24 4247109385
    FAT12                    249549  205 53     507436 219 35 4142955520
    HPFS - NTFS          353553    27  5      597165  96 22 3913631145
    FAT12                    579211  203  9     708012 119 31 2069182796

---

