---
title: "Hard Disk error before GRUB even loads!?"
date: 2009-01-12
forum: Hardware
---

### Post by kramer65 on 2009-01-12
Hello,


I've got a couple of partitions. I just erformated a partition which I just use for data. It is on the same physical drive as the ubuntu install, but it is as I said a totally different partition (it is also not the home partition).

After the reformat I rebooted and on startup, even before GRUB loads, I now get the following error:

```
Pri Master Hard Disk:S.M.A.R.T. Status BAD, Backup and Replace
Press F1 to Resume
```

After I press F1 ubuntu boots as normal. I deleted the partition in gparted but the error is still there. 
Does anybody know what the problem is here and what I should do?

---

### Post by damphoud on 2009-01-12
S.M.A.R.T is a utility that checks your HD for errors/problems, and tries to predict a possible drive failure. You might want to look into backing up your data/system, and giving the HD manufacture a call for a replacement. How old is your HD?

---

### Post by kramer65 on 2009-01-12
Actually, the HD is really new, only about half a year old. Is it for sure a hard ware failure or can it be a software one as well?

I backup up everything. Is there nothing else I can do?

---

### Post by damphoud on 2009-01-12
You can run the diagnostic utility from the manufacture. Usually you download an ISO from the companies website. Run a performance test, see how it comes out. If it comes out good, you can go into the BIOS and disable S.M.A.R.T. as it could be wrong.

If you don't know which utility to use, just let me know the manufactures name, and I can point you to it.

---

### Post by kramer65 on 2009-01-12
The hard drive says samsung..

---

### Post by damphoud on 2009-01-12
Link to download the utility ISO:
[http://www.samsung.com/global/business/hdd/support/downloads/Hutil210_iso_for_CDROM_drive.zip](http://www.samsung.com/global/business/hdd/support/downloads/Hutil210_iso_for_CDROM_drive.zip)

You need to burn the ISO inside this zip file to a CD. Boot off the cd to load the utility.
I think you have to extract the file and remove the "(For CD ROM Drive)" from its name for it to be recognized as an ISO.

Instructions on how to run the utility:
[http://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html](http://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html)

You need to do:
#5 Select submenu ( SELF DIAGNOSTIC)

---

### Post by kramer65 on 2009-01-12
Alright. I am going to do it a bit later today. Thanks for the info.

---

### Post by kramer65 on 2009-01-12
I just burned the cd and rebooted my pc. When it started to boot however I got an error saying something about the ram being wrong.

I attached a picture which I took of the screen. Does anybody know what's wrong here...?!?

---

### Post by damphoud on 2009-01-12
Hmmm well I'm not really sure what would cause that... we can try the floppy drive though, if you have one installed. 
[http://www.samsung.com/global/business/hdd/support/downloads/Hutil210_FDD.zip](http://www.samsung.com/global/business/hdd/support/downloads/Hutil210_FDD.zip)

You have to run the exe auto floppy write in Windows, or it might run in wine..

---

### Post by kramer65 on 2009-01-12
I unfortunately don't have a floppy drive installed and I don't have windows installed at my pc anymore either.

I am getting pretty sick of these errors. Is there no other way to solve this?

---

### Post by damphoud on 2009-01-14
Well an S.M.A.R.T. error isn't something you can just fix with a few commands.
Try a different CD/DVD-RAM/ROM... see if you can get it to boot into the util.
Try a different HD, one you know works, and see if you get the error. If you do, then you may have a problem with S.M.A.R.T., and disable it in your BIOS.
Otherwise, call Samsung, tell them S.M.A.R.T. is predicting a failure, and your system cannot boot their util because of "this" reason. They will probably send you a new HD.

/sorry about the delay

---

### Post by kramer65 on 2009-01-15
I tried to burn the cd again but the error remains. I can't really try a new HD since that would simply mean buying a new HD and reinstalling everything so then there would be no reason to check it anymore.

I will call Samsung today to ask them about it. Just one thing. Is S.M.A.R.T. a linux thing or is it something from the hard disk?

---

### Post by damphoud on 2009-01-17
[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).
I believe S.M.A.R.T. is built into your BIOS, rather you HD. Your error has little or nothing to do with Ubuntu.

My mistake... instead of burning a new cd, try the cd in a different dvd drive. If you don't have an extra HD laying around, you probably don't have another dvd drive...

Is the computer from a manufacture, or did you build the system yourself?

How was your call with Samsung?

---

### Post by kramer65 on 2009-01-20
Well, I just called samsung and asked them about the error. I have to send the hard drive to them. I just need to get it out, erase all my data, and live without an operating system for a week...

---

### Post by damphoud on 2009-01-21
Sorry to hear bud! Let us know how it makes out.

---

