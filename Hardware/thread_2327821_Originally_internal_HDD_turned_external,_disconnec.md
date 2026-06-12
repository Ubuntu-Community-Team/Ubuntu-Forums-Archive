---
title: "Originally internal HDD turned external, disconnects during operations"
date: 2016-06-14
forum: Hardware
---

### Post by 1geeky on 2016-06-14
After migrating from HDD to SSD, I've put my HDD inside an enclosure with USB 3 interface and SATA 3 adapter (Although my Laptop is both SATA 2 and USB 2 inside). The enclosure does not have a power adapter and get its power from the USB port.

I tried to keep my archive files on the HDD as described** [here]("http://askubuntu.com/q/784582/25831")** (with some doubts and issues mentioned there, of course); but in the daily use, I encountered fatal problems. Through data transportation from/to the HDD, it suddenly gets disappeared from the unity launcher and nautilus and even Gparted drives but the LED indicator of enclosure remains ON and the HDD keeps spinning (the vibration and noise).

I couldn't restore my backup of pre-migration data with *rsync* (aborted in the middle of the process) and access the drive for read and write.
I already created a whole image of the Linux partition of the disk with "*ddrescue** -n"* without any errors and have kept it somewhere safe. Has this problem anything to do with power shortage (Only USB) or is it bad sectors or filesystem?
Here is the S.M.A.R.T of the HDD : **[FUJITSU_MHZ2320BJ_G1_K84RT9525JE1]("https://paste.ubuntu.com/17344081/")**

Thanks

---

### Post by weatherman2 on 2016-06-14
The drive has clearly experienced some S.M.A.R.T. errors.

In the Attributes, you can also see that there were 69 offline uncorrectable sector errors and 105 reallocated sectors.  That means 105 sectors have failed but were successfully marked "do not used" and were replaced with spare sectors.  This is a big warning but not yet a catastrophe.  If that number keeps going up, the drive is surely about to fail.  (At some point, it will run out of spare sectors to remap from the bad ones.)

It's possible that one USB port isn't supplying enough peak power to keep the drive going.  There are Y adapters that let you tap power off of two USB ports to power the drive (typically not needed with modern motherboards that supply enough power off of one port, but I have found a couple of older boards that didn't supply enough power on one USB port and did use my Y adapter).

It's also possible that you're having USB 3 problems.  I have had occasional USB 3.0 issues even on Ubuntu 14.04; sometimes the USB 3 port simply stops working for no apparent reason and I have to reboot to use it again.  Not sure if that is an issue in your case or not.  (Not sure what version of Ubuntu you currently use - presumably not 10.04 any longer and your profile is out of date.)

Can you use a USB 2.0 port instead?  A USB 3.0 port would offer no benefit anyway in your case.

But given the errors on the drive and the number of reallocated sectors, I'd be wary about using this drive for anything important.

---

### Post by 1geeky on 2016-06-14
Thank you weatherman,


[LIST=1]
[*]What are those 69 offline uncorrectable sectors exactly?
[*]What is the number aside 105 reallocated sectors? *105 (1940 60)*
[*]My laptop' s motherboard was made at 2009. So maybe it's the kind which doesn't supply enough power on one USB port. How could I measure that? By the way, could be the power actually my issue? Or if there wasn't enough power, the HDD wouldn't start spinning and make click noise? (That's what happened when I attached enclosure to a USB hub which was connected to a single USB port)
[*]About USB 3 issue, My laptop's ports are all USB 2, Do you mean the USB 3 port of the enclosure and USB 3 cable? Currently, I use Ubuntu 16.04 (profile has been updated :D). After all, I think the port doesn't stop working since the LED of enclosure stays ON and HDD keeps making noise and vibration.
[*]a general question: Does SATA port provide more power than a USB port?
[/LIST]

**What's the workaround to access my data on HDD and ***rsync*[B] the data without getting disconnected in the middle of the procedure?
[/B]
Thanks

---

### Post by weatherman2 on 2016-06-14
My understanding is that "offline uncorrectable" are sectors that were corrupted but could not be fixed.  Do some googling to read more info.

I don't know what those other numbers are next to 105 - maybe the max number of spares and the threshold or something.  Most of my drives only show one RAW value there.

I'm guessing about how much power one USB port can supply.  I assume if I have issues with the drive - sometimes obvious, like I hear clicks but the drive won't start - that I need more power and try the Y adapter to use two ports.  If that works, then I know the power was probably the issue.

I may have misread: I thought you were trying to use a USB 3 port on your laptop.  If you are using a USB 2 port, then disregard all of that.

SATA ports don't provide any power - they are data only.  SATA devices must have a separate power connection directly to a power supply in addition to the SATA data connection or cable.

I don't know a "workaround" - a normally functioning drive won't get disconnected in the middle of an rsync.  I routinely connect portable drives that way.  I just rsynced 200GB of data from a portable drive in a USB enclosure yesterday.  The drive doesn't have any S.M.A.R.T. issues, though, like yours does.  Could well be your drive is dying.  Hard drives are getting cheap - even SSDs are getting cheap.   I wouldn't waste a lot of energy worrying about using an old laptop drive for backup.  If it is suspect at all, consider getting a replacement drive.

---

### Post by weatherman2 on 2016-06-14
I should also have suggested this earlier: run the Extended S.M.A.R.T. test on your suspect drive if you haven't already.  If it fails this test, then I would replace the drive or at least stop using it for anything important.  S.M.A.R.T. tests are run by the drive firmware so don't require much interaction with the host computer (so no real risk of another rsync-type failure) but the test may take an hour or two to complete.

---

### Post by 1geeky on 2016-06-14
Thank you, I've already performed an extended S.M.A.R.T and it ended successfully. the log in the first post was its output.

I thought both power and data ports make an SATA port (especially on laptop type):

[IMG]http://ww2.justanswer.com/uploads/drobertson1019/2011-09-17_180040_laptop-sata-hard-drive.jpg[/IMG]

But apparently only the data connector is actually the SATA.

---

### Post by xen3 on 2016-06-17
Just saying, an rsync transfer can be restarted, by e.g. using the -aPh parameters, the -P stands for "partial" (and I believe also progress) and it will just try to keep going where it left off.

It won't solve your problem, but at least it might make that little thing work ;-).

---

### Post by 1geeky on 2016-06-18
Thanks xen3,
I didn't use *-P* option. I'll consider use it in later cases

---

