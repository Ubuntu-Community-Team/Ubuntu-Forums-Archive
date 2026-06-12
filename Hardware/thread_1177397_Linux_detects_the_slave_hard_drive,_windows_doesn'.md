---
title: "Linux detects the slave hard drive, windows doesn't"
date: 2009-06-03
forum: Hardware
---

### Post by hypernova on 2009-06-03
Hello everyone

I have just installed ubuntu linux 9.04 today, and am still in the beginning of the beginning phase in linux (...also a novice in computers...)...so some things I say may not make any sense, so please correct me wherever possible

I was gifted a 200Gb hard drive from someone, which I didnt know how to install /attach. So I asked someone else to do it, and that person said that this particular hard drive is not compatible with the computer. He gave the reason because of some "red tape" thing....
But he attached the hard drive anyway, and windows never recognized it (as expected)...and everything ran as usual.

Today when I ran the live CD of linux, after entering the partitioner, it was showing me 200049 Mb of free space, and showing two devices - dev/sda and dev/sdb. The "dev/sda" had the familiar partitions C,D and E. But dev/sdb only had "free space" in it. So I tried using the free space and created 3 partitions out of it (boot, swap, root) and it worked !!:o....I am using the hard drive which was lying dormant inside the computer for such a long time.....!!

Now, the problem is that the hard drive on which Windows is installed is very small (40Gb)...and I have severe space crunch in it. So i somehow want to repartition the root partition (about 185Gb) of dev/sdb (for linux)...and give around 100Gb to windows to resolve space issues in windows, leaving around 85Gb for root of linux. Is that possible ? Please tell me how I can do it.

please forgive me if this is not the right place to post this question, i thought it may be some hardware problem....but I dont know....

---

### Post by adalal on 2009-06-03
From what I understand, one method is try creating a blank partition on that hard drive and then rerun windows and format it for NTFS using Windows utilities. Or, you could just try and formatting it to a FAT32, and use it in Windows.

As far as adding space to your Windows, I highly doubt you can just transfer over the entire OS over given the restrictions Microsoft puts in place. What you may be able to do, is reinstall a fresh copy of Windows on the new partition (NTFS would probably be the best bet), and then copy all the files over and delete the other partition. However, I think you would need to set this hard drive as primary and the other as slave, again, because of Microsoft restrictions.


------------
Oh, you could just keep the Windows partition you have now, and install and save all new data on the new hard drive instead...

---

### Post by Teutorix on 2009-06-03
I am not an expert but I always use fat32 over NTFS. NTFS is "supposedly" more stable but i have always found fat32 to be much easier to deal with.

---

### Post by dandnsmith on 2009-06-03
hypernova: I think the first issue to address is why the PC is said not to be compatible with that HDD - to this end, are you prepared to start again, delete all the partitions and create new, with one for Windows to use?

If so, then create your 100G partition first, as some type which Windows can recognise (FAT32 or NTFS), and then try to see if Windows can see it (which flavour of Windows is it?).

If it doesn't, then you're back to square one
if it does, then you can go ahead and decide whether to try to transfer the whole OS across by imaging the partition and putting the content on the second HDD, or just to use it for data.

---

### Post by hypernova on 2009-06-04
thank u everyone for the quick replies, but I feel I havent made my problems very clear. I will try to do so now -

Some more info- (if it helps)
I have windows XP SP2 on old hard drive (40Gb) (ntfs file system)
Linux on new hard drive(200Gb) (ext4 for root, ext2 for boot partition)
256 Mb Ram
ASUS P4G8X Deluxe motherboard
NVIDIA RIVA TNT2 
Pentium 4


The problems I have noticed yet -

1. I have installed windows Xp quite a few times now, but the winxp installer was never able to detect the 200Gb hard drive, and thus there is no question of partitioning it through the winxp installer.

2. My computer's BIOS detects only one hard drive, and when the computer is just starting (I see some things written on black screen with white)....I see somethings like this-
Primary - Samsung SV040....(something something...)
secondary slave - none - - (computer doesnt detect the new drive):(

3. How do I create a partition ? The windows is not able to detect the new drive (so I cant partition through windows). And I dont know how to partition through linux. Could you tell me how to do it ? I dont know how to open gparted, when I entered the command "sudo gparted" in terminal, it said "command not found".



 [B]@dandnsmith
[/B]Yes, I am prepared to create a new partition and uninstall and reinstall windows or linux if required. I have some serious space crunch in windows, i have no choice.;)

[B]@adalal
[/B]Even though I dont know how to create a blanck partition through linux right now, even if I do and somehow format it to ntfs, will the windows XP installer detect it, when the BIOS is not able to detect it ?
I have no problems in uninstalling the existing XP, and installing it on the new drive. In fact I would have done it a long time ago myself, if xp installer could just detect the hard drive somehow !! And, how do I convert new hard drive to primary and old to slave ?? (Could this simply be the solution ?)

Thanks again for all your help:), I hope I have made made the problems clear this time, I will be awaiting your replies......

---

### Post by dandnsmith on 2009-06-04
Your re-statement confirms what I initially read, but adds that the BIOS doesn't show that drive. This is worrying, because the XP installer tends to believe the BIOS in this matter - but there is an interesting point to notice in that you could install linux on that HDD, something which I thought wasn't possible.

Within the linux installation you should have been able to use gparted in the manner you showed, unless it isn't part of the distro which was loaded (unlikely, as the installer, I think, uses it). However you could download and burn the [usrl=http://gparted.sourceforge.net/livecd.php]gparted CD[/url], and try that instead.

I did have a home-built system which wouldn't accept HDDs above a certain size, but was capable of using them (I seem to recall) once I'd managed to partition and format them (size again a criterion) - so it's worth a try.

---

