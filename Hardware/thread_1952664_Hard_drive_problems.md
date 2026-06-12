---
title: "Hard drive problems"
date: 2012-04-04
forum: Hardware
---

### Post by PashConscious on 2012-04-04
Right. 

I have an HP Pavilion Slimline S3531 that has a Radeon HD 4350 pci-e card, a Seagate Barracuda 750gb hard drive, 2gb Ram, a DVD drive and a Dual Core 2.7 ghz processor. 

I had Backtrack and Ubuntu 11.0 installed on it working fine then after about 2 weeks the hard drive started actng erratically. 
1) hard drive light stays on shortly after boot and crashes. 
2) system wouldnt boot up sometimes
3) same problem regardless of which OS I chose in grub

So I removed the partition with Backtrack on it and tried to reinstall from the CD. 
Then more problems:

1) GParted sometimes wouldn't detect any devices 
2) couldnt format partitions (read/write error)
3) install would fail when creating new partition ( when the device detected it)

This happened repeatedly last night. 
Tonight after fretting a lot I tried to reinstall Windows 7. Got the partitions sorted but froze on "Copying files" (0%)
Tried to reinstall Ubuntu again, same problem. I then tried swapping the SATA ports that the DVD and HDD were connected to. THIS time I actually managed to totally install Ubuntu on a brand new partition, taking up all allocated space. 
Restarted the machine and got to the desktop, happened again. System froze with LED constantly on, not making any noise. Restarted the machine and it now does that before even getting to the password screen. 

The guy I bought the machine from swears blind that there were never any problems with it when he sold it to me.

Am desperate for help, is really getting me down as I can afford to keep dropping money on this damn thing. 

Thanks in advance.

---

### Post by rmil on 2012-04-04
you have to know exact reason of such behaviour It can be disk but you should first try find right disk to be sure that it is what you suspect.

Firstly I would check memory with memtest or something similar for several hours if there is any error in memory slot it is rear but it can happen.

I would check if CD live works and try to check for bad blocks with command.
```
badblocks>bad-blocks-file
```wait for long time to finish and than check the file bad-blocks-file
```
cat bad-blocks-file
``` If this file is empty after finishing than disk's surface is ok.

Also commands like```
dmesg
``` or ```
cat /var/log/syslog
``` can help to determine what happened before/after the crash. Sometimes it can be Video Card bad drivers or something more stupid.

I would give money on memory slot:)

---

### Post by jmore9 on 2012-04-04
I nce tried to forve feed ubuntu 11.04 onto a machine which did not have the video hardware to run it , needless to say there were all sorts of non booting ,etc problems.  As was said in an earlier post maybe your video isn't ready for ubuntu 11.04/11.10 ?  Also you could try booting off an live gparted cd and it might be able to check your HD for you.  At least if will show you what partitions are on the drive.

---

### Post by ahallubuntu on 2012-04-04
Time to check the S.M.A.R.T. status of the hard drive.  That's ALWAYS the first thing I check if I even suspect a hard drive issue.  And I wouldn't buy any new computer without checking S.M.A.R.T. - good practice.  Not that S.M.A.R.T. tells you EVERYTHING that could be wrong but it can tell you a lot.

You can install GSmartControl on a live CD to check/test S.M.A.R.T., or you can use the awesome Parted Magic Linux distro, which has that plus many other utilities built in.

Anyway, check S.M.A.R.T. using SmartControl (or GSmartControl) and look for any Attributes listed in red - those are the ones you should be most worried about.  Pending sectors are bad.

---

### Post by PashConscious on 2012-04-05
I ran a SMART short test on it last night with no errors, just running an extended test now. The graphics card is the one that it came with out of the box and the LiveCD I used to install it sunning on another PC with a Zotac GTX 470 in it, an older hard drive and an even older MB/hard drive in it with no probs either. 

Is it likely to be a physical problem? That's what I need to rule out really as the seller has offered to replace the hard drive for me. When I swapped the SATA ports I noticed that the hard drive was very hot, though I can't tell if it was TOO hot if you know what I mean. 

Plus when I re-installed I did a FULL wipe and used all in allocated space so is it likely to have bad sectors if it completed the installation with no problems? The drive isn't noisy or anything :(

---

### Post by PashConscious on 2012-04-05
Also, would these problems then effect the drive permanently? I don't want to but I will bergrudgingly roll back to WinXP if I have to :'(

---

### Post by ahallubuntu on 2012-04-05
Are there any Attributes highlighted in Red in SmartControl?  Which ones? Those are what you should care about first.

Wiping a hard drive can fix some "soft" errors on a drive, but it cannot fix bad sectors on a hard drive.  XP won't work on a bad hard drive - nothing will.  Hard drives physically fall all the time.  You simply need to replace it if it is bad.

---

### Post by PashConscious on 2012-04-05
Thanks all replies :)

I haven't gt home tO check on the SMART test (I should note that I am running this from the BIOS and not from desktop. 

I'll post the results in the next few hours, I kinda hope it just is a bad HD because if it's not then I've NO idea!!

---

### Post by ahallubuntu on 2012-04-05
It could easily be some other hardware issue like Power Supply, RAM, or motherboard.  I have seen power supply issues that behave almost exactly like you describe - but I've also seen hard drive issues that have the same behavior.  You sort of have to test everything and rule it out.

I'd check the S.M.A.R.T. attributes (in addition to running the tests) first.  It's very easy to do just by booting a Parted Magic CD (google for it, download and burn, then boot).  If your hard drive has lots of reallocated sectors for example, it could still pass the extended S.M.A.R.T. test, but it might still be dying.  

Power supplies are easy to test if you have a power supply tester though the results can be misleading.  If that's not a standard power supply, it could be not cheap to replace.

RAM you can test with Memtest on any Ubuntu CD.  Let the test run for a while; if no failures, the RAM is probably OK.

If everything else is ruled out, it's probably the motherboard, which probably means the computer is junk.  Hope it's something else instead!

---

### Post by PashConscious on 2012-04-05
I sincerely doubt it's the motherboard or the PSU-mainy because it still has all standard parts and has had very little use according to seller. 

I'll see what SMART says and report back. Coincidentally, the sound card was erratic from the start as well. Wouldn't recognise speakers and kept flickering between detected and non-detected speakers. Perhaps this might be causing problems, or at least might indicate what the problem is?

---

### Post by ahallubuntu on 2012-04-05
It's not helpful to "sincerely doubt" anything when evaluating electronics.  Motherboards and power supplies can fail the first week you use a brand new computer, or they can last for years.  They often fail in unpredictable ways.  Just because the seller claims something doesn't mean it is true.  (A S.M.A.R.T. attribute will tell you how many hours the hard drive has been powered up, to give you an idea of how much use it has had.)

Instead, approach the problem objectively and methodically.  Rule out each component by testing it or swapping in another good part.  The fewer variables you change at one time, the better your chance of identifying the problem.  Try not to make assumptions you can't verify.

Ultimately, if you installed a replacement hard drive that is known good and you have the same problems, guess what?  Your hard drive is almost certainly not the problem.

Sound card issues indicate to me that it's more likely to be a motherboard or power supply problem than a hard drive problem.  But - you'll find out as you test things.

See if you can find someone with a power supply tester locally who can test it out.  Testers are cheap - I have one (about the size of a cell phone) I bought for about $13 new.  Most computer repair places would have one; it's something you can do yourself in about 5 minutes just by plugging the PSU cables into it.

---

### Post by PashConscious on 2012-04-05
Smart Test is fine, no errors.

Just reformatting with ext2 instead. Is a slimline PC so PSU and GFX card are odd-sized :(

DLing Parted Magic thingy, gonna try that too.

---

### Post by PashConscious on 2012-04-05
ok.

This is the error los from GParted:

GParted 0.12.0 --enable-libparted-dmraid

Libparted 2.3
Delete /dev/sda1 (unknown, 687.32 GiB) from /dev/sda  00:00:01    ( SUCCESS )
         
calibrate /dev/sda1  00:00:00    ( SUCCESS )
         
path: /dev/sda1
start: 2,048
end: 1,441,423,359
size: 1,441,421,312 (687.32 GiB)
delete partition  00:00:00    ( SUCCESS )

========================================
Delete Logical Partition (linux-swap, 11.31 GiB) from /dev/sda  00:00:00    ( SUCCESS )
         
calibrate /dev/sda5  00:00:00    ( SUCCESS )
         
path: /dev/sda5
start: 1,441,425,408
end: 1,465,147,391
size: 23,721,984 (11.31 GiB)
delete partition  00:00:00    ( SUCCESS )

========================================
Delete /dev/sda2 (extended, 11.31 GiB) from /dev/sda  00:00:00    ( SUCCESS )
         
calibrate /dev/sda2  00:00:00    ( SUCCESS )
         
path: /dev/sda2
start: 1,441,425,406
end: 1,465,147,391
size: 23,721,986 (11.31 GiB)
delete partition  00:00:00    ( SUCCESS )

========================================
Create Primary Partition #1 (ext2, 698.64 GiB) on /dev/sda  00:00:00    ( ERROR )
         
create empty partition  00:00:00    ( SUCCESS )
         
path: /dev/sda1
start: 2,048
end: 1,465,147,391
size: 1,465,145,344 (698.64 GiB)
set partition type on /dev/sda1  00:00:00    ( SUCCESS )
         
new partition type: ext2
create new ext2 file system  00:00:00    ( ERROR )
         
mkfs.ext2 -L "" /dev/sda1
         
mke2fs 1.42.1 (17-Feb-2012)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

========================================

attached is the Disk Health log, (the errors tab was highlighted in red)

An y thoughts?

---

### Post by PashConscious on 2012-04-05
and i'm sorry for "sincerely doubting" anything.

I havent installed anything in it either, all the hardware was provided to me and as its a slimline I dont have anything that will fit the case. 

Should I perhaps have posted this in the Absolute Beginner section so I could be replied to with less disdain?

---

### Post by PashConscious on 2012-04-05
After numerous misfires and near-misses, I have managed to fromeet the drive in NTFS and install Windows 7 Ultimate. Restarted ir repeatedly with no issues at all, though until its been working for at least a week I'm not resigning myself.

How strange is that? I suppose I could just swap my main PC for my alt, its only really used for movies and internet anway. Its just so odd that after ALL these test andworkarounds, the only way I could get it to work is with Windows 7!

Are there any hard drives that simply dont work with EXT4? I dunno. At least Idont have to f*ck around sending it back and all that.

---

### Post by recluce on 2012-04-05
According to the SMART status, everything is NOT in order. You have a high UDMA error count and ATA command errors, but the self tests complete just fine. This would point, most likely, towards cabling or controller (mainboard) issues. Other possibilities (flaky power supply, bad RAM) do exist, but are less likely. It would now be the appropriate time to start rotating components to isolate the problem. I would start with the cables.

That Windows installed fine may not have any meaning, since different OS put different loads on I/O and especially flaky cables are just pure chance. It may even work for a couple of days or weeks. 

No matter what OS you decide to use, unless you fix the underlying hardware problem, your data WILL come to grieve - sooner rather than later.

---

