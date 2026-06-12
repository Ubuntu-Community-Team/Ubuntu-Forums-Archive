---
title: "Burning DVDs..."
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by matrisking on 2006-08-04
Hi,

I'm trying to burn data DVDs via an external USB burner.  When I insert a blank DVD, CD/DVD creator automatically opens in Ubuntu.  Great.  However, after I move all of the files to be burned into the creator window and click "Write to Disc".  I get the following error:

FILE IMAGE CREATION FAILED
The selected location does not have enough space to store the disc image (185 MiB needed).

Even though I'm only trying to burn 4.2 gigs of data.  Anyways, just in case, I removed a file that was around 185 MB.  Tried again, said "4 MiB" needed.  Removed one more 185 MB file, said "3900 MiB needed" (approximately)! 

Any idea what I'm doing wrong?  I've been reading about console-based dvd-r tools.  Should I look into using one of those?  Or am I handling this improperly?  Is there something I should be doing to mount the drive, etc?

Thanks!

---

### Post by DerHesse on 2006-08-04
FILE IMAGE CREATION FAILED
The selected location does not have enough space to store the disc image (185 MiB needed).

...your partition is full!

Whatever "3900 **MiB** needed" means, probably --> 4GigaBytes

Execute
$ df -h
..and see what is left.

---

### Post by matrisking on 2006-08-04
Awesome, that fixed it.

Thanks!

---

### Post by marcusg on 2006-08-12
Does the free space have to be on a particular partion? I'm trying to burn about 3gb of data from hda6. I ran $ df -h and that says that hda6 has 4.9gb free.
Thanks!

---

