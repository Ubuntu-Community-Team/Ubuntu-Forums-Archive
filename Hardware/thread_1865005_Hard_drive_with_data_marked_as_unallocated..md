---
title: "Hard drive with data marked as unallocated."
date: 2011-10-19
forum: Hardware
---

### Post by PorcupineTR33 on 2011-10-19
Hi everyone, not sure if this is the right place to post this thread. I'm still very new to Linux so I need some help. Ok here is whats going on.

I just recently migrated from Windows to Linux, currently using Ubuntu 11.10, now the issue is that in Windows I had 3 hard drives, 160GB (boot drive), 320GB (programs) and 500GB (data).

I did the same with Ubuntu, my 320GB is for Windows programs to work under WINE, and my 500GB is supposed to be my data.

It seems that my 500GB is using a GUID Partition Table while my other two drives are in Master Boot Record, now I am not sure why Ubuntu wont pick up my 500GB and show me all of my files stored in that drive like it did for my 320GB... What it does is, it does pick up the hard drive but it recognizes it as "unallocated" drive... basically empty drive with no partitions...

Is there a way I can get all of that data back?, I have all of my music and important school work in it and I'd like to get it all back and to work with Ubuntu... 

Thanks in advanced!

---

### Post by dabl on 2011-10-19
I haven't done it myself, but maybe this helps:  [http://ubuntuforums.org/archive/index.php/t-991328.html](http://ubuntuforums.org/archive/index.php/t-991328.html)

---

### Post by PorcupineTR33 on 2011-10-19
I actually, installed GParted and found out that the GPT Table is corrupted or damaged but that the disk itself is fine...

I also found this... [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) but I have no clue on how to use it or if its built in to Ubuntu? or if I have to get it somewhere.

---

### Post by oldfred on 2011-10-19
An older verison of gdisk is in the repository. Not sure what version you will get. You can download with synaptic. I do not think 11.10 even includes synaptic, it then may be in Ubuntu Software Center.

You can download it from links in the rodbooks site.
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

[http://www.rodsbooks.com/gdisk/download.html](http://www.rodsbooks.com/gdisk/download.html)

---

