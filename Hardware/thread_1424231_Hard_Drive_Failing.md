---
title: "Hard Drive Failing?"
date: 2010-03-07
forum: Hardware
---

### Post by lextori on 2010-03-07
So, Ubuntu pops up an error message every time I boot into it since in installed it on my new laptop saying that I have a large number of bad sectors and my harddrive may be failing. When I boot into windows the utilities there seem to think that it is just fine.

I'm more inclined to trust ubuntu's error message but I'm not sure how to tell if the disk is actually failing or just possibly failing.

What steps can I take to see some more details and determine if I need to be calling tech support to get them to replace the HDD.

---

### Post by viper250 on 2010-03-07
In windows run scandisk/f if there are errors it should show them.
scandisk/f will locate and mark all bad sectors and configure the os to ignore and not use them.
a disk test utility will locate bad sectors! also formatting the drive can also show bad sectors during format and will display the message  trying to recover sector #####.
 
linux install programs are more critical of hard drive errors.
 
if you are unsure how to proceed run d-ban on it It will clean the drive and run a brute force drive test on it.
if d-ban finishes early and displays errors the drive wil fail soon.
but keep in mind that some sata drives may not be detected.
 
also if this is a new system you may need to enter bios and change the drive mode to ide (if it is a sata drive)
check to see if your system is still under warranty, If the drive is failing and your system is still covered they should repair it.

---

