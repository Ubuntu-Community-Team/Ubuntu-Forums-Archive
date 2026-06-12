---
title: "Moving from HD to SSD"
date: 2014-01-05
forum: Hardware
---

### Post by makitso on 2014-01-05
I have a dual boot system, win7 and ubuntu, installed on a 500GB disk.  I am planning on moving to a 128GB SSD device.  In preparation, I have reduced the size of the WIN7 partition and also the ubuntu / and /home partitions to a size that would fit on the SSD.  

My thoughts are that I would use the dd command to copy the new 500GB disk partitions to a backup device, install the SSD and create the new partitions, and then using the dd command copy the backed up partitions to the new SSD.   

Does this sound reasonable?
Would there be a problem with the boot partition on the SSD in finding the grub since its has changed its position from what it was on the larger disk?

---

### Post by oldfred on 2014-01-05
You cannot dd the drive as that is size for size and also copies empty space.
For image backup I would suggest clonezilla or for Windows these.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
Do not know what kind of issues Windows may have, but are you planning on keeping rotating drive plugged in? If so with dd you have duplicate UUIDs and system will not work without changing UUIDs, updating fstab with new UUIDs and reinstalling grub to update its use of UUIDs. Often with Ubuntu reinstalling is easier.

Similar thread:
[http://ubuntuforums.org/showthread.php?t=2195575&highlight=ssd](http://ubuntuforums.org/showthread.php?t=2195575&highlight=ssd)
[http://ubuntuforums.org/showthread.php?t=2194916&highlight=ssd](http://ubuntuforums.org/showthread.php?t=2194916&highlight=ssd)

---

### Post by Bucky Ball on 2014-01-05
Quite apart from oldfred's excellent tips, rule of thumb appears to be to run the OSs on the SSD and keep your data on the HDD. Therefore, might consider keeping /home on the 500Gb drive as you may run out of room on the SSD and, from what I've read so far (am about to invest in one myself) for pure data grunt (dealing with large amounts of data rather than OS work) there is not a lot of diff between the two.

---

### Post by oldfred on 2014-01-05
Two years ago I added SSD. I thought I might get new system, but tried SSD first. Since then I have had trouble convincing myself I need new system. My 6 year old (parts 4 years old) has worked so well that new system was not required. 
But I keep all data on rotating drives and only have SSD configured with / (root) partitions. With my 64GB drive I have 2 28GB partitions.

---

