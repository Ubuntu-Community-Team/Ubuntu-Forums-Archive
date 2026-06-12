---
title: "Hard drive wiped?"
date: 2011-01-14
forum: Hardware
---

### Post by Alex_GT on 2011-01-14
I've been trying the last few days to upgrade to 10.10 from 9.10, there's been a few issues. 

The structure of my hard drive before the attempt of this was:

160 GB drive containing 

10gb partition of windows recovery
D volume 75gb
C volume 67GB or so (with a 8.4gb hidden 9.10 installation basically I took some free space off volume C when I installed)

This has been working fine for I guess the better part of the past year of dual booting 9.10 and windows vista.

So I put 10.10 on USB with the intention of installing. Why couldn't I just upgrade within 9.10? Well for some reason it kept running out of space when attempting this so I would try to reformat the 9.10 partition and install it on that which didn't really work so I took a further 12GB free space from C drive which 10.10 could use. This worked fine and 10.10 seemed to be installed alongside 9.10 and vista.

After this, I wanted to remove 9.10 and try to merge that partition with the new 10.10 so it would have enough space. So I reformatted the 9.10. This didn't really work as intended and I was left with a 8.4gb blank partition that now appeared in windows as well as 10.10. While all this was happening I kept having issues grub menu so I had to keep booting the live disk and repairing/installing grub again also windows kept running chkdisk every now and again (on both volumes C and D).

Then I thought it had resolved itself finally except some weird stuff happened when I booted up 10.10 this one time ie it looked a bit glitchy. But it loaded fine and seemed ok when I shut down. I then booted up vista which went OK IE nothing unusual. I then left my laptop over night turned on (closed) and woke up to find it unplugged (basically it was left to run on battery till it went dead) which I thought nothing of at the time.

So later today I booted up my laptop to find the message "No Operating system found", I've received that message before (and it wasn't a very good omen then either!)

So I put my flash drive in containing ubuntu 10.10, load it up and try to locate what exactly has happened.

I go to "Computer" and the first thing I noticed was there was neither the normal C partition (containing windows) or D (other data). This was extremely odd. Having had all sorts of issues with Ubuntu/windows over the years on this machine I've never had this before.

There is only the CD drive and "File System" (which is I don't know what, it says it has 1gb free space which is odd because the flash drive I boot up is 1gb itself and has very little space).

When I load up disk utility, there is the 160gb there. However it doesn't appear to have any partitions or known anything about it. It just has "Unknown 160Gb" and smart status says its "healthy"

Gparted comes up with something slightly different, it says the HD is 149GB with partition table "unrecognised".

Even the recovery partition of windows has disappeared :(

I've started up the ubuntu 10.10 installation to see if that offered any information but again, no offering of anything about the HD beyond that it needs reformating to make its own partition.

I've put in the windows recovery disks, but the option to recover isn't available and it seems only a fresh install will work.

This is about my limit of what I know to do with this matter now. I'm afraid anything further will wipe the data off my hard drive in a highly unusual situation I've never encountered before. I've had problematic ubuntu upgrades/installations, bugged vista, but there's always been the option to recover my data before I need to do a fresh windows installation to fix these issues.

Well, that's it, if you could please help me in this matter hopefully I could resolve this problem :-?

---

### Post by ajgreeny on 2011-01-14
Using your live USB can you please run ```
sudo fdisk -l
sudo parted -l
``` in terminal and show the output of those two commands here.

Also run System ->Administration ->Gparted and post a screenshot back here as an attachment, not in-line, of what it shows, as it can make the layout and size of partitions easier to see than the text of the first two commands.

We will then have a good idea of what is actually left on the computer, and hopefully be able to tell you where to go from here.

---

### Post by Alex_GT on 2011-01-14
[[IMG]http://img839.imageshack.us/img839/9936/screenshotlk.png[/IMG]](http://img839.imageshack.us/i/screenshotlk.png/)

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1039 MB, 1039663104 bytes
32 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1023     1014785    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 31, 62) logical=(1022, 31, 62)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table



ubuntu@ubuntu:~$ sudo parted -l
Model: BUFFALO USB Flash Disk (scsi)
Disk /dev/sda: 1040MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  1039MB  1039MB  primary  fat16        boot


Error: /dev/sdb: unrecognised disk label

---

### Post by Alex_GT on 2011-01-14
.

---

### Post by ajgreeny on 2011-01-14
As you have probably gathered from all those things, you appear to have wiped out any OS you did have on the disk, and now have just empty space.

It is possible that testdisk may be able to help you restore what was on there before by restoring the old partition table, but I have never used it so I am unable to help with any more info on how to use it.

---

### Post by Alex_GT on 2011-01-16
Bump

---

### Post by Alex_GT on 2011-01-17
Bump

---

### Post by VanillaMozilla on 2011-01-17
> **Alex_GT said:**
> Well for some reason it kept running out of space when attempting this
This doesn't solve your current problem, but unless they have fixed a bug very recently, Nautilus does a poor job of presenting disk space.  Disk Usage Analyzer works correctly.  Ubuntu has perversely put this under Applications > Accessories.  In my case, the cause of huge missing disk space was the Trash can, which is not self-emptying.  Too late, alas.

---

### Post by VanillaMozilla on 2011-01-17
> **Alex_GT said:**
> I then booted up vista which went OK IE nothing unusual. I then left my laptop over night turned on (closed) and woke up to find it unplugged (basically it was left to run on battery till it went dead) which I thought nothing of at the time.

So later today I booted up my laptop to find the message "No Operating system found", I've received that message before (and it wasn't a very good omen then either!)
Clearly, you did NOT wipe the Windows partition.  You do appear to have a hardware failure, however.  Perhaps it couldn't read the boot sector, or perhaps worse.

So you're in need of heavy-duty data recovery.  That's way beyond me, but I can make one small suggestion.  A friend's computer became nonbootable, although the drive passed hardware tests.  I used SpinRite on it and got it working.  Over the next few months I had to repeat this twice before my friend finally replaced the computer, but it worked each time.  It was extremely slow -- up to 20 hours or so -- but it did work.  Reportedly, it does often solve disk failure problems long enough to recover data.  The program has been around for many years, and if you don't like it, they refund the price--no questions asked.  That doesn't solve your unformatting problem, but it might solve your Windows partition recovery.  As far as I know, there's no harm in trying it.  It won't alter any data on the disk, and shouldn't exacerbate your formatting problems.

---

### Post by psusi on 2011-01-17
> **VanillaMozilla said:**
> Clearly, you did NOT wipe the Windows partition.  You do appear to have a hardware failure, however.  Perhaps it couldn't read the boot sector, or perhaps worse.

Ummm, no.  Clearly he DID wipe the windows partition since there are NO partitions on the disk.  Nothing he has said gives any indication of hardware failure either.

> **ajgreeny said:**
> As you have probably gathered from all those things, you appear to have wiped out any OS you did have on the disk, and now have just empty space.

It is possible that testdisk may be able to help you restore what was on there before by restoring the old partition table, but I have never used it so I am unable to help with any more info on how to use it.

+1

---

### Post by VanillaMozilla on 2011-01-17
[quote="psusi"]Ummm, no.  Clearly he DID wipe the windows partition since there are NO partitions on the disk.  Nothing he has said gives any indication of hardware failure either.[/quote]
[QUOTE="Alex_GT"]I booted up 10.10 this one time ie it looked a bit glitchy. But it loaded fine and seemed ok when I shut down. I then booted up vista which went OK....[/quote]
If the disk was wiped, then he didn't boot it, did he?  Clearly he had NOT wiped out either the Linux OR Windows partitions at that point.  The only thing he did after that was to let the battery run down, which should not wipe a partition.  Windows and Linux are still on that disk.

Software tests can easily fail to detect a partition in case of a hardware failure, e.g., if the disk fails to read certain formatting information.  Whatever mistakes may or may not have been made in setting up that disk, it still sounds like there has likely been a hardware failure.

---

### Post by Alex_GT on 2011-01-17
Thankyou VanillaMozilla, as I tried to get across in my first post the issue (as I see it) seems to be some type of hardware malfunction. I would like to state this again *The laptop/HD was working fine*.

I wouldn't call it a freak occurance, but my HD has been very stable since I bought the laptop itself 2 years ago.

I'm running out of options now, I tried a Gparted bootdisk but that just seemed very much the same as the gparted that comes with ubuntu livedisk and didn't offer anything new. (I was actually looking for the testdisk booter which lead me to gparted bootdisk).

This really wouldn't be a problem for me (I do have the windows recovery disks) but without knowing what has happened to the partitions I find it rather frustrating.

(I see someone still thinks I somehow reformated the drive - If that was true then going through the steps of ubuntu install surely wouldn't require ANOTHER reformat...a partition maybe)

---

### Post by psusi on 2011-01-17
> **VanillaMozilla said:**
> If the disk was wiped, then he didn't boot it, did he?

Of course he didn't boot it, he said so; he got an OPERATING SYSTEM NOT FOUND error.

> **VanillaMozilla said:**
> Software tests can easily fail to detect a partition in case of a hardware failure, e.g., if the disk fails to read certain formatting information.  Whatever mistakes may or may not have been made in setting up that disk, it still sounds like there has likely been a hardware failure.

It didn't say it could not read it, it said the drive is blank.  That means it read it just fine but it contains no data.

> **Alex_GT said:**
> Thankyou VanillaMozilla, as I tried to get across in my first post the issue (as I see it) seems to be some type of hardware malfunction. I would like to state this again *The laptop/HD was working fine*.

Take a look at the SMART values and run the self test with the disk utility to see if there is a hardware problem.  At this point you don't appear to have a valid partition table.  It may be that is the only part of the disk that got overwritten, so you can run testdisk to scan the rest and see if it can recognize any partitions and rebuild the partition table.

---

### Post by mr clark25 on 2011-01-17
I'm surprised nobody has said this yet...


it sounds like the partition table got corrupted (somehow). all of your data is still there, its just that your computer doesnt know where it is on the disk.


i would try testdisk from the Ubuntu live CD/USB. just install it, and look at the man pages. 

someone here should be able to help you use testdisk if you have trouble.

---

### Post by VanillaMozilla on 2011-01-17
Alex_GT, you wrote, "I booted up 10.10 this one time ie it looked a bit glitchy. But it loaded fine and seemed ok when I shut down. I then booted up vista which went OK...."  You said "OK" twice.  Did Vista and Linux start or did they not?

If they did, then Vista were intact, or at least at that time.  If they were intact, then you didn't wipe it out.  The partition table or whatever could have been corrupted LATER by hardware failure, but I'm not at all sure any part of your installation was responsible.

I suppose Mr. Clark is correct, you might be able to fix the partition table even if it was corrupted by hardware failure.  But just because it can't read it now, doesn't mean it will always be unable to read it.  Many times I've seen disks temporarily fail to boot, and then work perfectly the next time.  If it were my disk, I would try the conservative, hardware solution FIRST, before making any desperate changes on the disk.  But you're hanging by your fingernails, and it's your choice, not ours.

---

### Post by Alex_GT on 2011-01-18
[[IMG]http://img140.imageshack.us/img140/1140/screenshotal.png[/IMG]](http://img140.imageshack.us/i/screenshotal.png/)

[[IMG]http://img146.imageshack.us/img146/6808/screenshot1ykb.png[/IMG]](http://img146.imageshack.us/i/screenshot1ykb.png/)

Any advice ?

---

### Post by Alex_GT on 2011-01-20
Bump if anyone could please help with above (using testdisk), thanks!

---

### Post by VanillaMozilla on 2011-01-20
Alex, you know, no one has yet explained how you could have booted both Linux and Windows if the partition table was messed up.

You thought the computer was working all right, but you certainly could have had a hardware failure that you didn't know about, which only became apparent after all the parted and installation activity.  And a hardware failure can affect the partition table.

---

### Post by psusi on 2011-01-20
> **VanillaMozilla said:**
> Alex, you know, no one has yet explained how you could have booted both Linux and Windows if the partition table was messed up.

He didn't boot after the partition table was messed up.  Follow the description:

1)  Computer boots, acts weird
2)  Computer no longer boots, gets OPERATING SYSTEM NOT FOUND error
3)  Inspecting the disk shows no partition table.

---

### Post by VanillaMozilla on 2011-01-20
> **psusi said:**
> He didn't boot after the partition table was messed up.  Follow the description:

1)  Computer boots, acts weird
2)  Computer no longer boots, gets OPERATING SYSTEM NOT FOUND error
3)  Inspecting the disk shows no partition table.
Psusi, Alex can answer for himself.  You have left out several crucial steps.  In Alex's words:

-4) try to reformat the 9.10 partition and install it on that

-3) took a further 12GB free space from C drive which 10.10 could use. This worked fine and 10.10 seemed to be installed

-2) reformatted the 9.10. This didn't really work as intended and I was left with a 8.4gb blank partition that now appeared in windows as well as 10.10.

-1) keep booting the live disk and repairing/installing grub again

0) windows kept running chkdisk every now and again (on both volumes C and D

Now come the steps that you described:
1)  Computer boots [both 10.10 and Windows], acts weird
2)  Computer no longer boots, gets OPERATING SYSTEM NOT FOUND error
3)  Inspecting the disk shows no partition table.

Alex, when someone spends time trying to solve your problem, it's customary to answer questions, or at least acknowledge that you have read and understood what was written.

---

### Post by psusi on 2011-01-21
The 3 that I listed are the only relevant ones.  No successful boot since OPERATING SYSTEM NOT FOUND, which indicates a corrupt partition table.  This was then confirmed by fdisk.

---

### Post by VanillaMozilla on 2011-01-21
The unreadable or corrupt partition table was probably caused by a hardware failure, which, believe it or not, can sometimes be fixed by software.

The partition table was intact at last boot.  If it had been corrupt, he would not have been able to boot at all.  And he did nothing that would affect the partition table after the last boot.  Partition tables don't corrupt themselves, but hardware failure certainly can.

Everything that happened before the last boot is also consistent with hardware failure.  The multiple chkdisks, the repeated repairs of grub, and the general flakiness before the last boot, suggest that new disk errors were appearing even then.

---

### Post by VanillaMozilla on 2011-01-21
As I wrote before, a lot of people have had good luck with SpinRite for disk recovery.  There's an article about it in Linux Journal:  [http://www.linuxjournal.com/article/7684](http://www.linuxjournal.com/article/7684) .  I think the GNU program ddrescue operates in a somewhat similar way, but it probably requires a separate disk to copy to, and I don't have any experience with it.

Either way, let us know how it turns out, Alex.

---

