---
title: "NTFS Partitions -- Worked Fine, Now Broken"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by caesar424 on 2007-05-29
I have verified that all my NTFS partitions by booting into XP and using all my partitions there.

I used the Automatix script about 4 weeks ago to install support for NTFS read/write. I then edited fstab for some better mountpoints (ones of my own choosing). These all worked great, so I created soft symlinks in my Home Directory to access these partitions and subfolders faster.

The whole setup worked fine until 2 weeks ago. I would reckon I had a full week of perfect access after creating the symlinks. I'm supposing an update of some kind knocked the partitions out, but I can't find any info in Google or these forums already (maybe my search terms are poor).

Booted up one day and noticed that the NTFS partition failed to mount (this was after the POST, before X windows started). Installed ntfsprogs (or something similar) using apt. Ran a fix on each partition. Rebooted, still won't mount correctly.

[LIST=1]
[*]Can anyone direct me to the error log something like this would be located in?
[*]Does anyone have any information regarding this issue?
[*]Should I post a bug? If so, where to?[/LIST]Thanks in advance for all your help!

---

### Post by kornhead127 on 2007-05-29
Linux will not mount an NTFS partition if it is marked for a check-up. Boot into windows and if it doesn't automatically run CHKDSK then go to start | run | and type cmd and press enter. From the prompt type chkdsk /F. It will let you know that the partition must be unmounted to check it, and will tell you to restart. When it starts up again it will automatically run chkdsk. Once it is finished you may boot back into Linux and the partition should mount cleanly.

-=]Rob Swift[=-

---

### Post by caesar424 on 2007-05-29
Will try this method before the day is out.

Is there a way to run checkdisk inside linux for NTFS partitions so I can do this pre-emptively in the future?

Thanks!

---

### Post by caesar424 on 2007-05-30
> **kornhead127 said:**
> Linux will not mount an NTFS partition if it is marked for a check-up. Boot into windows and if it doesn't automatically run CHKDSK then go to start | run | and type cmd and press enter. From the prompt type chkdsk /F. It will let you know that the partition must be unmounted to check it, and will tell you to restart. When it starts up again it will automatically run chkdsk. Once it is finished you may boot back into Linux and the partition should mount cleanly.

-=]Rob Swift[=-

Just booting up and letting checkdisk run didn't do the trick for some reason.

But chkdsk /F worked just fine. Thanks for the suggestion! :D

---

