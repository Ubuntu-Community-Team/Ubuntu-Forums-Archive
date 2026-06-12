---
title: "Problems burning DVDs"
date: 2008-10-18
forum: General Help
---

### Post by woodenbrick on 2008-10-18
I'm trying to backup some files to DVD and am getting errors everytime. 
Here's the tail end of the Brasero Log:
```

BraseroGrowisofs stderr:   0.54% done, estimate finish Sat Oct 18 20:35:03 2008
BraseroGrowisofs Called brasero_job_set_progress (0.005400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   0.81% done, estimate finish Sat Oct 18 20:34:01 2008
BraseroGrowisofs Called brasero_job_set_progress (0.008100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: /dev/scd0: reserving 1852048 blocks
BraseroGrowisofs stderr: :-[ RESERVE TRACK failed with SK=5h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 1.0x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=5h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
BraseroGrowisofs stderr: :-( media is not formatted or unsupported.
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: :-( write failed: Wrong medium type
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2524)

```
I tried burning using nautilus too, and it also failed.  As far as I know there is nothing wrong with my drive, and it can burn CD's just fine. It is a NEC ND-6500A Dual Layer DVD±RW Writer - 8x/4x/8x DVD+RW, 8x/4x/8x DVD-RW, 2.4 DVD+R DL, 24x/16x/24x CD-RW.

---

### Post by woodenbrick on 2008-10-20
bump, anyone?

---

### Post by TenPlus1 on 2008-10-20
k, try installing the latest version of Brasero from [www.getdeb.net](www.getdeb.net) and also check the dvd media you are using to burn, it may be the wrong type for your drive ..or.. a really crappy brand...

---

### Post by woodenbrick on 2008-10-20
I know it's not the DVD's since they burn fine on my other computer, 100% success rate there.  My burner is supposedly capable of burning and type of DVD + or -, so I don't quite understand the error message.  I'll give the new version of brasero a try though.

---

### Post by editrix on 2008-10-21
You may be a victim of the CD/DVD burning bug. See my post here
[http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700)

for more info.

---

### Post by localhorse on 2008-11-04
I had a similar problem, woodenbrick. I was receiving that error, but in my case the problem only occured with DVD-R discs, which I needed to use to burn Wii backups.

In the end I used cdrskin instead of wodim (which I believe Brasero uses) or cdrecord. If you don't want to use a command line program, K3B can be configured to use cdrskin. Possibly Brasero as well.

Had no problems when using cdrskin.

---

### Post by jonb on 2009-03-01
I had a similar problem after upgrading my OS.
I fixed it by reformatting the dvd from k3b (set the force option in the format dialogue).
My guess is either that previous k3b/driver versions set something in the format that triggered this, or that I had previously written the DVD on a different computer with a more modern dvd writer.

---

