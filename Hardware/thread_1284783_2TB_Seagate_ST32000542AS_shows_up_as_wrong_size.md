---
title: "2TB Seagate ST32000542AS shows up as wrong size"
date: 2009-10-07
forum: Hardware
---

### Post by fortytwo on 2009-10-07
Just bought a new 2TB Seagate ST32000542AS, and it's showing up as 931.53 GB (which I assume is the decimal form of 1TB).  I've searched and found a lot of complaints about >2TB partition sizes, but I can't even get the disk to be recognized as its full size.  I hop into gparted and try changing the disk label to gpt, but it doesn't seem to have made much difference.

Anything I can try to get this to show up as its correct size?  I've done it with 1.5TB drives before and had problems setting up the partitions (had to change the disk label) but never with the actual size being mis read.

Thanks.

---

### Post by QIII on 2009-10-07
Have you gotten the 1.5 TB drives to work on the machine you are installing this new disk on?

---

### Post by fortytwo on 2009-10-07
Yep 1.5TB drives weren't a problem getting recognized.  Like I said, had to get the disk label set correctly to get the partition right, but otherwise not an issue.  To double check I put one of the 1.5TB drives in and it came up fine.

EDIT: A little more background: I'm putting this into an unRAID box, and saw it come up as the wrong size when I added it.  Curious, I plugged it into my Ubuntu box with a USB adapter and saw the same result (931.53GB), so it doesn't appear to be an unRAID problem.  In the unRAID FAQ there's a link about drives showing up as the incorrect size ([http://blog.atola.com/restoring-factory-hard-drive-capacity/](http://blog.atola.com/restoring-factory-hard-drive-capacity/)) but it doesn't seem like any of the suggestions apply.  The unRAID box also handled the 1.5TB no problem.

---

### Post by fortytwo on 2009-10-07
Hmm, well, this is odd.  I was messing with the drive a bit...formatting it in Ubuntu to get a windows machine to recognize it so I could run a  'capacity restore tool' the unRAID forums had suggested when I read that it won't work when the drive is plugged into Windows as a mass storage device (which was my only option).  

I plugged it back into the unRAID box to run some hdparm commands from the unRAID FAQ...and it came up as the correct size!  Wish I knew a bit more conclusively what it was that did it.  But the last thing I did on the drive was format it as NTFS, so I'm not entirely sure exactly what solved it.  Even when I formatted it in Ubuntu, it was still coming up as only 1TB.

---

