---
title: "write image of bad hdd to new one with dd"
date: 2009-08-05
forum: Hardware
---

### Post by doas777 on 2009-08-05
howdy all,

one of my users turned up with a very dead ntfs partition on a failing drive. I need to try to recover some files off it, but the partition is in pretty bad shape.
I made an image of the affected drive with 
```

dd if=/dev/sdd1 of=/media/external_disk/backup.iso conv=noerrors

``` (I know, it's not actually an ISO but I hate not having extensions.)

so now that I have an image,** i want to write it out to another hdd, but that is where i'm getting stuck.**

I've tried using dd to write it to /dev/sdc (just another hdd) with: ```
sudo dd if=/media/external_disk/backup.iso of=/dev/sdc 
``` but after writing it failed to mount (mount said volume did not have partition table, after writing the image).

I created a partition table and a single partition (larger than the source one) as an unformatted type on sdc and , with ```
sudo dd if=/media/external_disk/backup.iso of=/dev/sdc1 
``` tried to write it off again, but I got a message that it does not recognize the partition on the drive as NTFS. fdisk says the type is "Linux"


so any idea what I'm doing wrong with dd? or should i assume the image is correctly written and concentrate on fixing the partition itself now that the media is mutable?

thanks folks!

---

### Post by doas777 on 2009-08-06
bump

---

### Post by PatrickVogeli on 2009-08-06
maybe the partition is so damaged it won't mount?

---

### Post by doas777 on 2009-08-06
> **PatrickVogeli said:**
> maybe the partition is so damaged it won't mount?
very possible, but there are intact files that photorec can see. unfortunately it (photorec) won't look for the filetypes I needs(.aspx, .cs, .vb, etc). I just rewrote it with ddrescue, so tomorrow I can see if there is anything to be done about recovering the partition table. 

Thanks

---

### Post by pp. on 2009-08-08
Have you defined the new partition on the target disk, e.g. using gparted?

---

### Post by doas777 on 2009-08-08
I did, on the second attempt. but alas, no luv. I did try working on the partition itself with some linux and windows tools (ntfsfix, dti-partition editor, and a couple file scourers),  but it looks like no tools I've found seem to be able to parse the begining and end of .net source files. needless to say, my first response to this issue was to train him on sourcesafe, but I digress.

I've had to give up on this sucker for now, but i'm keeping the image arround, just because it has presented me a challenge, so if anyone has any ideas on raw data recovery, please post.

thanks everyone,
franklin

---

