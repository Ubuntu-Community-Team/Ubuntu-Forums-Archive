---
title: "Question about fdisk"
date: 2012-06-24
forum: Hardware
---

### Post by cyberswordman on 2012-06-24
Since I'm new here, I want to start greeting everyone):P.
Now, back to topic.. fdisk
I'm trying to handle the partitioning of an SD card for an embedded system (Beagleboard in this case).
I've already done that once on a ubuntu 11.04 and everything was fine
(this is the guide i'm following: [http://code.google.com/p/beagleboard/wiki/LinuxBootDiskFormat](http://code.google.com/p/beagleboard/wiki/LinuxBootDiskFormat) , so you can get an idea of the procedure I'm following).
I've upgraded to ubuntu 12.04, and still using fdisk, but with a new SD.
now, the current geometry of the SD is 61 heads, 62 sectors, 1021 cylinders.
I start changing these values with expert mode, then, whne I try to create the first partition, I'm forced to make it start at sector 2048 (63 if toggling the DOC compatibility)... I really don't remember to have had any problem last time I doing this... I've read quite some links about this, but really can't figure out a solution... 
Second quick question, when I quit fdisk, and re enter, I notice that the new set geometry is not save, I always have the 61/62/1021 values...
does anyone have any idea about this?
Thanks for your help! :p

---

