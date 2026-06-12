---
title: "can't install vista, but I kinda &quot;need&quot; it."
date: 2008-09-04
forum: Hardware
---

### Post by aschulz90 on 2008-09-04
Hi all, brand spanking new to Ubuntu forums. So here's why Ubuntu has become my new O.S.: I tried using partition magic in Vista, these two things are to say the least not compatible. Partition magic corrupted the master boot record on my hard drive. Nothing worked from then on, so I wiped it clean and installed Ubuntu first. now I can't install vista because after formating the free space (10gbs goes to Ubuntu) it says my hard drive does not meet the necessary criteria. I tried using the highest rated partitioner to help but it didn't. Does this have to do with Ubuntu being mounted as "/" (vs "/home" etc.)? I am fairly certain that nothing that I did before is causing it not to work. Could it be that the disc for vista I have was a re-installation disc and it needs to see something dell provided before? idk why its not working but I would like to use my creative zen 8gb mp3 player without a butt-load of set up. Thanks for any help.

---

### Post by Namain on 2008-09-04
This is more of a question for a windows forum, but I can tell you that you need to set the partition that you wish to install vista on as the "Active" partition.

You can do that through GParted (Partition Editor in the Administration menu).

Start GParted, and select the drive that you intend to install Vista on, this is normally automatically selected if you only have one drive.  Next right click on the partition that you want to install vista on and click "Manage Flags".  Turn on the "Boot" flag and click "Close".  This will apply the flag and the vista installer should detect that the partition is eligible to install on.

---

