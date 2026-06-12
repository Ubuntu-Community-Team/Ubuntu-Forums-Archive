---
title: "RAID0 and LVM guidance"
date: 2008-11-19
forum: Hardware
---

### Post by kcallis on 2008-11-19
While I was cannibalizing an old machine I came across a 250G SATA drive, a 200G SATA drive and a couple of low capacity IDE drives (40G and 60G) drives. I figured that I would load Ubuntu 8.10 Server and call it a day.

So I decided the use the 60G drive as the / filesystem and use 400G of the SATA drives as /data and the spare 50G from the 250GB drive for /home. The first question is can I do a layout like the above or does the drive have to match in size?

Is there any particular type of fs that I should format the drive for... For instance, considering that I will be serving up primarily video, so I look at xfs or some other filesystem type?

I was also wondering if maybe I should do an additional RAID1 between the 60G IDE drive and the 50G spare space on the 250G hard drive and create a RAID0 between the two SATA drives.

Any pointers would be greatly appreciated... I was also thinking about maybe adding in LVM into the mix...

---

