---
title: "[SOLVED] Readahead actually slows my boot down"
date: 2008-11-13
forum: General Help
---

### Post by almahtar on 2008-11-13
I have a Gen 3 Macbook Pro, and my boot times are about 35 seconds.  I figured I could do better than that so I added "profile" to my boot options in grub, rebooted, removed it, and rebooted again.  My boot time has increased by about 30 seconds :\.  When I remove all the files in /etc/readahead my boot time goes back down to 35ish seconds.

This is with all bulky services like postgres, apache, and mysql turned off (I have to start them manually).  I've attached bootcharts of a clean boot and one with the readahead.  Notice that the readahead takes almost 50 seconds!

Anyone have any clue what could be causing this?  My suspicions are that perhaps the EFI isn't supporting my drive's capabilities correctly or that libata is trying to do some stuff that only worked correctly with BIOS instead of EFI.

hdparm reports dma is disabled and transfer mode is 16 bit, but I think it might not report correctly for SATA devices or the like... I have no idea really.

Thoughts? Suggestions?
*edit: I attached the output from hdparm -i *

---

### Post by grim4593 on 2008-11-13
Do you have a swapfile? Maybe its trying to read the whole thing or something. Might be a good idea to do a sanity check on the files listed. If they are too big, dump them.

---

### Post by almahtar on 2008-11-13
Good call - I wasn't able to make a swap partition because EFI freaks if I have too many partitions, so I have a swap file.  It was the 2nd item in /etc/readahead/boot.

I've removed it and I'm going to try rebooting.  I'll let you know how it works.

---

### Post by almahtar on 2008-11-13
You're the man.  That was the issue.  Took my boot time from 38 seconds (without readahead) to 29.

Thanks.

---

### Post by grim4593 on 2008-11-13
Sweet. I had the same problem a while back. Glad it worked for ya.

---

