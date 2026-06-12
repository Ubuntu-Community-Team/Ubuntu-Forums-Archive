---
title: "Unable to install on Inspiron 9300"
date: 2009-03-29
forum: Hardware
---

### Post by Tweak1029 on 2009-03-29
Not sure what the deal is.  I have two hard drives, a 160GB and an 80GB and it will not install on either no matter what I do.

So far all I've tried to install on it has been 8.10, the normal version and the version for Dell laptops.

Does anybody know how to get it on here without using Wubi / through Windows?

---

### Post by s.dalas on 2009-03-29
can you give more info?
i mean you download the .iso file of Ubuntu burning on a cd and try to install it? what exactly have you tried? did you check the cd for defects?
also in which step of installation do you get the error or something that stops the process?

---

### Post by Tweak1029 on 2009-03-29
I have a Ubuntu disc from canonical and the Ubuntu for dell laptops iso that I downloaded at school.  Neither disc has any errors, and I used each to successfully install Ubuntu to another computer (I cleared 5 GB out and installed to make sure that it would work).

It won't get past the formatting part.  I've tried booting to gparted live and formatting the HD using that before the installation, and that seemed to work, but then it just froze on the next step (I forgot what step that is).

---

### Post by s.dalas on 2009-03-29
in which drive you try to install Ubuntu? this drive you want to install has any unallocated space on it? is the same drive that you have windows?

---

### Post by Tweak1029 on 2009-03-29
I've tried just about everything there.  At first, I had Windows, then I formatted Windows and tried to use just free space, then I pre-formatted it using gparted live cd, then I just said screw it and installed Windows again.  Back to square one.

Brand new 160GB drive is the one I want it on.

---

### Post by s.dalas on 2009-03-29
try this out:

1.Install Windows (during installation make a partition for Win and the other leave it unallocated)
2.restart and Login in Windows and make a user (eg.ME )
3.restart and put in Ubuntu installation cd
4.make a new installation
5.at partition manager go to manual - and make an ext3 partition for Ubuntu with mountpoint "/"
6.at ntfs partition (windows) put mountpoint "/windows" DONT format the partition
7.make a swap partition (about the size of your ram)
8.make any other partition you want (free space etc) but if you want to be accessed by windows make them fat32 format.

At least these steps working fine for me.

Good luck and post back for any trouble

---

### Post by Tweak1029 on 2009-03-29
I'm pretty sure I've tried that but I'll give it a shot.  I'll let you know how it goes.

---

### Post by s.dalas on 2009-03-29
hope that helps. post back to find a solution if not.

---

### Post by Tweak1029 on 2009-03-29
Nothing.  I couldn't get far enough to do the partitioning.  Most of the time the partitioner would "load" but never come up.  Once it hung at 50% and another time it loaded, but after I selected manual and tried to proceed it hung there.

---

### Post by s.dalas on 2009-03-30
> **Tweak1029 said:**
> Nothing.  I couldn't get far enough to do the partitioning.  Most of the time the partitioner would "load" but never come up.  Once it hung at 50% and another time it loaded, but after I selected manual and tried to proceed it hung there.

yes sometimes the partition manager hungs. i checked arround the internet and the only thing that i found was that inspiron9300 has almost great compatibility with Ubuntu. 

Some people say that the hardest part is to make Ubuntu work. After this everything else is easy. 

Try to burn the .iso file at lower speed (X4) and give it a try again.

---

### Post by Tweak1029 on 2009-03-30
Different DVD, same problem.

As for the hardest part being to make Ubuntu work, I disagree.  That's usually the easiest part.  The hardest part is getting it configured to be perfect.

I can boot to the live version and it works okay.  There are the typical sound issues and stuff crashes a lot, though.

---

### Post by Tweak1029 on 2009-03-31
Bump

---

### Post by Tweak1029 on 2009-04-02
Another bump.  I'd love to get this thing working.  If anybody has any ideas, please let me know.

I may try Hardy today if I can dig up a disc.

---

### Post by Tweak1029 on 2009-04-12
Bump again.  I couldn't find a Hardy disc.  Right now I'm installing Ubuntu using wubi, but I'd still love to install it properly.
EDIT: "Installing inside Windows" option from Ubuntu 8.10 Desktop Edition disc

For the record, Debian Lenny segfaults... a lot...  I learned something else, too.  I have a mismatched pair of 512 MB RAM sticks, but even one at a time, it does the same thing.

I'm not sure, but I think it might be DMA.  Would that make sense?  If so, how can I turn DMA off/on?

---

### Post by Tweak1029 on 2009-04-12
Wubi seems to be having issues, too.  It tried making an ext3 partition, failed, told me to come back to Windows and do chkdsk /r and then reboot and try again.  After I clicked "Okay" on that box, it popped up a black screen with this on it:

[b]
[107.145530] SQUASHFS error: sb_bread failed reading block 0x5add3
[107.145586] SQUASHFS error: Unable to read page, block 16b73c55, size 119e
[107.146051] SQUASHFS error: sb_bread failed reading block 0x5add3
[107.146104] SQUASHFS error: Unable to read page, block 16b73c55, size 119e
[107.146493] SQUASHFS error: sb_bread failed reading block 0x5add3
[107.146546] SQUASHFS error: Unable to read page, block 16b73c55, size 119e
[107.146686] SQUASHFS error: sb_bread failed reading block 0x5add3
[107.146739] SQUASHFS error: Unable to read page, block 16b73c55, size 119e
[107.147007] SQUASHFS error: sb_bread failed reading block 0x5add3
[107.147059] SQUASHFS error: Unable to read page, block 16b73c55, size 119e
[/b]

Had a BSOD on first boot to windows.  It went away too quickly so I couldn't write what it said.  Boot to Windows after BSOD gave me a box that says, "The system has recovered from a serious error." with a log.  Here's what the log contains:

Error Signature:
[b]BCCode : 10000050     BCP1 : EBC8003F     BCP2 : 00000008     BCP3 : EBC8003F
BCP4 : 00000000     OSVer : 5_1_2600     SP : 2_0     Product : 256_1[/b]

"Technical information about the error report" or "The following files will be included in this error report:"
[b]C:\DOCUME~1\User\LOCALS~1\Temp\WERce49.dir00\Mini041209-01.dmp
C:\DOCUME~1\User\LOCALS~1\Temp\WERce49.dir00\sysdata.xml[/b]

Off to run chkdsk and see if it will work.

EDIT: Ran chkdsk /r and then tried booting to Ubuntu from the menu.  Every option on the menu takes me to BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash).

---

### Post by Tweak1029 on 2009-04-13
I ran memtest86+ v2.01

I have 1 GB of total RAM.

It passes all of the default tests.
If I go to (c)onfigure -> 3 (memory sizing) -> BIOS-all it fails.
Error message:> 
Tst Pass "Failing address" Good Bad Err-Bits "Count Chan (sp?)"
0 0 000e0000000-3584.0MB ffffffff 25908086 10000000 5714


The Err-bits thing seems like a pattern.  It looks like it goes 00000001 to 00000002 to 00000003 to 00000004 etc. then moves left a place and repeats.  The "Count Chan" thing is just a counter, which goes up to 5714, apparently.

If I go to (c)onfigure -> 3 (memory sizing) -> Probe it seems to fail.  It freezes at 50% on the first test and then becomes unresponsive.  If I press c and tell it to skip the first test before it gets to 50%, it stops at 48% on the next test and becomes unresponsive.

It passes the dell diagnostic thing, but I'm not sure if I'm doing that right because I don't have a utility partition and don't have the drivers disc when it asks for it.  What ran, exactly, is "Pre-boot System Assessment Build 3018", I think.

---

### Post by Tweak1029 on 2009-04-14
Gonna go ahead and bump this...

---

