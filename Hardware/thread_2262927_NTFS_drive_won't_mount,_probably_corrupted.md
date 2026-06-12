---
title: "NTFS drive won't mount, probably corrupted"
date: 2015-01-28
forum: Hardware
---

### Post by n0c0d3 on 2015-01-28
Hi,

I was downloading some large files to an external USB-drive (NTFS). Then one download somehow failed, the other download continued and finished normally. After that I couldn't move anything on or to that drive anymore. I unmounted it and tried to mount it again, but besides the drive-icon on the desktop it won't mount. I rebooted, tried it on Windows as well, but nothing. Windows shows it as drive G, but I named it "T", but I can't access it. It won't show any properties or anything else about the drive.

Something must have gone awfully wrong with the download that failed. I think it's not a hardware problem because the other download seemed to have finished normally. I'm not really knowledgeable of file-systems, but I suspect something in the file-indexing table, or whatever it's called, must have become corrupted.

I tried gParted as well, but that doesn't see the drive, and it doesn't stop looking for devices when I plug in that drive and use the "Refresh devices" option.

I do have some NTFS recovering software (runs on windows only) I bought long time ago (I hope I can still find the reg-key). Some years ago it still worked on on another dive, but it creates lots of rubbish, didn't recover everything and on this 1 TB-drive (appr. 75% full) will very likely take days to run. In the mean time I wouldn't be able to use my Xubuntu of course, on which I do everything (the previous time I booted Windows was in March last year). My Windows is from another of my previous computers and it seems not to be allowed to use it on other computers that for the one it's originally installed. I only use it when there's no other option, and it just started nagging about it not being an official windows version or something like that and I can't update it, so prefer not to use it for lengths of times.

Does anyone know how to analyze the problem and hopefully recover this drive without losing any data, preferably from within (X)ubuntu?

---

### Post by weatherman2 on 2015-01-28
It could certainly be a hardware problem.  Check the drive's S.M.A.R.T. status and Attributes using GSmartControl to make sure it hasn't failed.  That won't help you recover anything, but if there is a hardware failure, you will have a more difficult problem in recovering data.

If the drive itself hasn't failed, then I would try file recovery tools next.  Try the free Recuva or testdisk if you don't want to mess with your old software.

---

### Post by n0c0d3 on 2015-01-28
In GSmartControl the basic health check shows "passed", but the short self-test says "completed with read failure". 
This is part of the log:
```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     32140         6271834
```

I've just started a deep search form the [analyze] menu in testdisk, which is going to take a while. I'll post a log of the results when it's finished.
Things can be written to disk with this program, so it might be dangerous to use. I hope you or someone else can advice me before I make changes.

Thanks so far.

---

### Post by weatherman2 on 2015-01-28
Look at the Attributes in GSmartControl too - look for any highlighted in red or pink, those are the most likely to be problems.  A read failure from a S.M.A.R.T. isn't good.  Then again, none of this helps you recover your data, only helps you understand what you are dealing with.  You can put a lot more stress on a healthy hard drive to try to recover files than one that is failing.

I've never even used testdisk, can't give you any pointers there.  Good luck with it!

---

### Post by n0c0d3 on 2015-01-28
GSmartControl shows one pink error in the attribute tab:

```
D# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
197 Current_Pending_Sector  0x0032   195   195   000    Old_age   Always       -       1465
```
 There's an entire essay in the tooltip of this entry, and I can't make much sense of it, but I think there may be a bad sector. Maybe if I run chkdsk in windows this can be repaired? Or maybe testdisk can repair this as well? But I couldn't enter the properties-menu of this disk in Windows earlier today, so this might be a problem.But I suppose I can do this form the dos-screen (or whatever it's called there), I don't know if I'd have to add any parameter to fix errors. Hopefully somebody can advice me on that.

The testdisk analysis is currently at 21%. Fortunately I can do this while I sleep. I've used testdisk before, but under strict guidance. It can change boot-records and such. It's not something to just fool around with when you don't want to loose stuff.

And btw, something I forgot to mention earlier: the drive has no boot-sectors. It's only in use for storage.

---

### Post by weatherman2 on 2015-01-28
You have 1465 bad sectors, so clearly the drive is failing or has failed. (A "pending" sector is one that could not be read.)  Once you had managed to recover whatever data you can with test disk, if you are able to recover anything, replace the drive.

---

### Post by n0c0d3 on 2015-01-28
Hmmm, that doesn't sound good. But it's not particularly the newest drive anyway, so it may not be too unexpected. 1465 sectors, that's about 12MB at a clustersize of 8kB. That's not really all that much, so I think not much will be lost. It depends a bit on how they're spread over various files of course.

I'll post this testdisk-log when it's finished. I hope someone can help me how to get as much as possible off it then, or how to repair these clusters, with testdisk or chkdsk, so I can mount it and copy the disk to somewhere else. Otherwise I'll have to see if GetDataBack or Recuva can help me out.

---

### Post by weatherman2 on 2015-01-28
If the disk surface is failing, and you do a full scan with testdisk, that number of pending sectors may go way up as testdisk attempts to read more sectors.

But if the number of pending sectors does not increase beyond 1465, you're right, you may have lost relatively few files (at worst 1465 files with one bad sector in each; in practice probably far few files).

If those failed sectors cannot be read, I don't think you will be able to recover the files that contained them.  Testdisk may have a mode where it will try repeatedly to re-access the same sector over several days and it may eventually succeed, but recovery could take a very long time.

Recuva isn't going to help recover bad sectors, only files that were deleted or corrupted but otherwise intact on a good disk.  chkdsk has an option to try to recover failed sectors but I'm not sure exactly what it does or how it works.  I am fairly sure it would take a very long time to run at all.

---

### Post by Reha_Andrew on 2015-01-29
Hey there are many bad sectors it is important now to recover files. You have already tried much i suppose.
I CAN HELP you suggesting one i have heard about them may be that could be helpful for you.[http://www.stellarinfo.co.in/services/hard-disk-recovery.php](http://www.stellarinfo.co.in/services/hard-disk-recovery.php)

---

### Post by Mark Phelps on 2015-01-29
BE advised that I have personally run into hard disk recovery options and contacted recovery services as a result.  In ALL cases, the recovery fees START at around $1000 USD!!  That's because, any hadware failure is going to require completely rebuilding the hard drive, and that must be done in a "clean room" environment.

Not saying StellarInfo will charge this much, but all the other services I've contacted do.

---

### Post by n0c0d3 on 2015-01-29
Thanks guys, for the professional recovery advice. But it's all not life-threatening or worth hundred of dollars ;-) I lost nothing really personal or irreplaceable.

This testdisk scan I started yesterday is still running. It's been at 76% all day, chewing over just a few cylinders, which I think contain the damaged clusters. Only since just about half an hour ago it&#8217;s been speeding up again. I'll post the logs of the scan to see if someone knows if it can be dealt with from within Ubuntu. If not then I'll probably be on Windows for the weekend, trying to recover what's left on the disk and I'll take this computer offline because Windows won't let me update as I explained earlier.

I've already ordered a new HDD which I hope I'll receive tomorrow, and I found my reg-code for GetDataBack again, which helped me out well recovering from damaged drives in the past, so at the moment my hopes are mainly directed on that.

---

### Post by weatherman2 on 2015-01-29
I'd be curious to know what the pending sector count is via GSmartControl after testdisk has completed, if you don't mind posting that as well.  I wonder if it went up significantly?

Good luck!

---

### Post by n0c0d3 on 2015-01-29
> **weatherman2 said:**
> I'd be curious to know what the pending sector count is via GSmartControl after testdisk has completed, if you don't mind posting that as well.  I wonder if it went up significantly?!

I hope not!
But I'll let you know.

---

### Post by n0c0d3 on 2015-01-30
Okay, the scan is finished. But I apparently pressed a wrong button and the entries that were found were gone from the list, except for the NTFS partition. All I can say there were 4 other small Linux partitions found.

But I don't think it matters all that much, as I've figured out how to copy the files from the NTFS partition with testdisk:
Analyze -> Quick Search ->  P (list files) -> : or a (to select directories/files) -> c or C (to copy single or multiple entries) -> [select destination] -> C (to start copying).

 When my new drive arrives I'm going to try that and I'll see where it all ends and hopefully there's not much lost.

After that I'm going to play around with testdisk to see if it can repair or restructure things. When I've copied everything nothing much can go wrong anymore after all. And I may reformat the old drive (in Widdows I still got the "format" option in the context-menu) and maybe I can still use it for temporary storage. Or maybe chkdsk can still do something useful.

And for weatherman2: there were no more pending sectors than were found earlier (1465). Fortunately!

Until further notice I consider this problem solved :-)

---

