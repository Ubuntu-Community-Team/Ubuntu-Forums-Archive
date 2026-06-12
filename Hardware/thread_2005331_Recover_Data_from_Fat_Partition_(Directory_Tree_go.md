---
title: "Recover Data from Fat Partition (Directory Tree gone)"
date: 2012-06-17
forum: Hardware
---

### Post by Germanunkol on 2012-06-17
Hello,

I just lost two thirds of my hard-drive's files, I have no idea where they went.
Testdisk didn't help (the partition table is all right) and PhotoRec only recovers tons of files (lots of which seem to be unusuable) but without any directory-tree.

Some of the files PhotoRec didn't find any more.

This is a Fat32 partition, so I tried dosfstools, but no luck so far.

What's interesting is that the Drive is still almost full (~150 gig) according to Nautilus, even though the data which is still on there (the data which I can see, that is) only takes up around 20 gigs... the rest is just not visible? (I also tried with ls -a ... it's not just invisible, it's gone.)

Any suggestions of how I could recover?

---

### Post by mbuell on 2012-06-17
Have you tried running a disk check on it? Use dosfsck or chkdsk. I'm not sure what dosfstools has to do that.

---

### Post by sudodus on 2012-06-17
I'd vote for ```
chkdsk /f
``` run from Windows if possible. It can repair 'almost everything' on FAT and NTFS file systems.

Maybe you can also try ***gpart*** (not gparted), which sometimes succeeds where testdisk fails (and vice versa).

Otherwise, you need patience and try once more to find the most important files with ***PhotoRec***.

---

### Post by Germanunkol on 2012-06-19
Hi, thanks for the replies!

I have tried chkdsk multiple times, and get tons and tons of .chk files (though it can't be everything, the size of the files is still much less than the size original files were). But there's nothing useful in there, even when I run various file-recognition programms on the .chk files. And chkdsk doesn't seem to repair anything at all, it just creates all those .chk files which I can't recover anything from...

Oh well. The new hard drive should arrive soon. I have a backup folder of the most important files, but there was quite a few other ones I would've liked to keep.

Thanks for your help.

---

### Post by mbuell on 2012-06-28
If you are getting .chk files - chkdsk is finding errors and correcting them. Or attempting to correct them. If you have run chkdsk in the fixing mode (I forget the switch, maybe /u?) and you still can not get to all the files that used to be there, I think you have severe hard drive problems. Likely either the physical surface is failing, or the drive brain is failing. In either case, you should immediately back up everything possible and  decommission the drive, unless you want to lose more stuff.  Sounds like you have already backed up what you could - good on ya.

If you have remaining data you want - there are companies that recover hdd data for a fee - they can even pull the actual disk out and mount it in another device to read it. But, their methods are not cheap!

---

### Post by Devillers on 2013-01-16
Hi Everyone,

If you are trying to recover data from your FAT partition, then I would suggest you to connect the affected drive to a healthy Windows system and try using a HDD partition recovery software to retrieve your data from it. This tool performs [fat partition recovery]("http://www.hddpartitionrecovery.com/reformatted-fat-partition-recovery-on-windows%207.html") in a very easy and efficient way. To download the software [click here]("http://www.hddpartitionrecovery.com/download/hddpartitionrecovery-windows.exe")

---

### Post by gary bridge on 2013-02-27
I was lost all my data from one of the FAT partition. But thank to god, one of my friend recommend me a software that really works, which help me to recover fat partition data back.

---

