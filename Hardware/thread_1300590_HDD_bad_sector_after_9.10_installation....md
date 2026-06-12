---
title: "HDD bad sector after 9.10 installation..."
date: 2009-10-25
forum: Hardware
---

### Post by samuraitor on 2009-10-25
Hey ,

I just installed ubuntu 9.10. After installation I got a message saying that there are bad sectors on One or Many harddrives.

The Palimpset Disk Utility app, gives me a warning with ID '197' and attribute Current Pending Sector Count.

I never had any issues with my harddrive when using 9.04. Could this be a bug or something?

PS: Have installed 9.10 twice!

---

### Post by arnab_das on 2009-10-25
same problem here! :( installed RC ubuntu 9.10 and got a bad sector message, something which i never got with 9.04

---

### Post by makan on 2009-10-28
same problem here.... palimsest said my disk has many bad sectors

ATA Hitachi HTS542512K9SA00

---

### Post by leandromartinez98 on 2009-10-28
You all be careful. 9.04 didn't have the same disk utility, 9.10 has it exactly to warn you about a possible disk failure. Probably you should consider backing up your data an running disk checks.

---

### Post by quimkaos on 2009-10-28
Just try and do a disk check with another tool, preferably outside of any OS. I just installed Ubuntu in another PC and I'm getting those errors too, and tho they are probably true, I've read in this forums that the disk tool is giving some false information. So in my personal opinion it's better to sun an OS independent tool to look for error and try to fix it. Tho if they are hardware bad blocks you'll better star backing up your data. Last time i chose to ignore the warning i lost 120GB of work!

---

### Post by millermccullum on 2009-10-28
Hey Samuraitor.
  	 	 	 	 	 	  Myself Millermccullum and I read your entire posting. Welcome to the forum Samuraitor. First you should have to take advise from the hard drive repairing expert. If it is ok then you may consider this problem as bug. But you should have to pay attension to this problem.  Anyways Thanks. Stay Connected.

---

### Post by Noble Hacker on 2009-10-29
I too was informed by Disk Utility that "Disk has many bad sectors", right after upgrading to Ubuntu 9.10 (final). With 9.04 it was ok... 
Hope these are false alarms ))

---

### Post by SoundGuy.Jon on 2009-10-30
Same thing is happening with me. I really don't want to have to replace the hard drive on my laptop. I don't have the money to do it right now, and not having a laptop would be really crippling :/

---

### Post by rmayer32 on 2009-10-30
Booted the LiveCD of 9.10 final and got this as well. I don't get it with the 9.04 install though, and have Win7 on another partition. I have tried getting sector errors on that partition but haven't found anything. Could be false reporting, at least I hope. :)

---

### Post by Peedjay on 2009-10-31
Hey everyone 
I'm having a similar problem here. Right after my upgrade to 9.10 Ubuntu gives a warning (ID 197) for bad sectors on my HDD (ST9160821AS). But...
- checking trough my windows partition (chkdsk) results in no problems found.
- the value for "current sector pending count" is -1. I would understand anything above zero but a negative value???? 

Help from anyone?

---

### Post by zaferaktan on 2009-10-31
Same thing happened to me as well :(
I had no issues with 9.04 but all of a sudden I had this issue reported.  I backed the critical information to my usb external disk just in case.  But I don't believe the disk is corrupted.  I believe this is a bug.
Zafer

Dell XPS 1330 - ubuntu 9.10 (32bit) - 320gb ATA Samsung HM320JI

---

### Post by jonathanysp on 2009-10-31
i have this message as well. its not 9.10's fault, its just that 9.10 now includes this program which can tell you if your disks are failing. If it is failing now, it was probably not that good when you had 9.04. The best thing to do is to double check with another program (e.g. badblocks) just to make sure before you go about backing up everything and getting a new hdd. Anyways i just bought a 1TB hdd which was on sale!

---

### Post by cariboo on 2009-10-31
Have a look at the screenshot, make sure **Don't warn me if the disk is failing** is checked, and you shouldn't see the warning any more.

I would suggest you look at the more details window, as you can see in the screenshot that the drive I selected has 12 bad sectors, the threshold in the case of this drive is 36, so I have a ways to go before having to replace the drive.

---

### Post by cKGunslinger on 2009-11-01
I got the same error right after my 9.10 upgrade.  

Sure, it's *possible* that we all managed to have our disks start to fail right about the time we upgraded, but that seems a bit suspicious.  Perhaps the tool is a bit too aggressive?

Also:  [Bug 438136]("https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136")

---

### Post by astembridge on 2009-11-02
Same here -- just upgraded and Palimpset is reporting 675 bad sectors (threshold 50)

---

### Post by mokrayz on 2009-11-03
[LEFT]Apparently this is a bug in karmic. so we must just wait for a fix. running a disk utility wont help.

             **Bug Description**

   
   Binary package hint: yelp
 Palimpsest Disk Utility 2.28.0 reports "disk has many bad sectors".
 ProblemType: Bug
Architecture: i386
Date: Fri Oct 30 15:30:41 2009
DistroRelease: Ubuntu 9.10
ExecutablePath: /usr/bin/yelp
NonfreeKernelModules: nvidia
Package: yelp 2.28.0-0ubuntu2
ProcEnviron:
 LANG=en_US.UTF-8
 SHELL=/bin/bash
ProcVersionSignature: Ubuntu 2.6.31-14.48-generic
SourcePackage: yelp
Uname: Linux 2.6.31-14-generic i686

 
  

[/LEFT]

---

### Post by Slatts on 2009-11-07
Same problem here...
I just updated a HP laptop to Ubuntu 9.10 and at the first boot I got the following message from the Palimpsest 'SMART Data' window:
"Disk Has Many Bad Sectors" - "Back up all data and replace disk".
The warning relates to "Reallocated sector count" and says I have 327712 bad sectors. All other checked parameters were OK.

So I ran 'Spinrite' and it says there are no bad sectors. So I did a deep scan with the same result – no bad sectors.

I guess these are all false positives --- But why?

---

### Post by kkady32 on 2009-11-07
i have the same issue :bad sector
i download Hiren's Boot CD v.10.0 and run HDDRegenerator and this repair problem.
now,message from palimpsest is :'disk is healthy'

---

### Post by mdshann on 2009-11-07
All of you should run a hard drive test from your hard drive manufacturers. Seagate Seatools works well for most though. For example with Seatools you download the iso from their web site and burn it to a CD. Boot your computer from the CD and run a full diagnostics on you hard drive. This will tell you if your drive has any bad sectors on it. Even one bad sector can cause problems and if you have more than a few chances are the drive is failing and will get worse quickly. I do not trust drives which show any bad sectors as if the bad sector is in the right place it can cause files not to open or even the OS not to boot. It is possible to reallocate bad sectors and I have seen drives last a while after developing a few but like I said I do not trust drives with bad sectors. I work in a repair shop so believe me when I say that once you start seeing bad sectors replace the drive! Especially if you reallocate them and then more show up!!

---

### Post by kkady32 on 2009-11-08
I run Estool from Samsung(my HDD is Samsung) and this tool reported LBA error.reinstall before 3 time fresh Ubuntu 9.10 ,try with fsck and testdisk ant this error was still in the same places.Then test with HDDRegenerator and the error was same,and after i decided to use scan and repair and after this error is no more reported.

---

### Post by willemferguson on 2009-11-11
Be VERY careful before assuming your hard disk is faulty. The bad sectors reported is almost certainly a nondestructive Ubuntu bug. Let us hope Canonical does something to this soon. I get the same 9.10  error message with a recommendation 'Replace the disk'. Below is the output of a systematic disk check (after booting from CD), indicating the hard disk on my machine is NOT faulty.

root@ubuntu:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

root@ubuntu:~# badblocks -v -p 3 -n -s -o badblocklist /dev/sda1
Checking for bad blocks in non-destructive read-write mode
From block 0 to 149902482
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
Pass completed, 0 bad blocks found.
Checking for bad blocks in non-destructive read-write mode
From block 0 to 149902482
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
Pass completed, 0 bad blocks found.
Checking for bad blocks in non-destructive read-write mode
From block 0 to 149902482
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
Pass completed, 0 bad blocks found.
root@ubuntu:~#

---

### Post by mdshann on 2009-11-11
Exactly what I was trying to say just didn't know about the badblocks command! :)

---

### Post by avangerx on 2009-11-13
I have the same problem here. Ubuntu says my external hard drive has bad sectors and it needs to be replaced. After reading all these I started to assume that it is a bug especially previous version did not warn me neither Windows XP/Vista.

---

### Post by ensign.dan on 2009-11-13
First of all you haven't got warnings in 9.04 because there wasn't Palimpsest included. The same history was when Fedora Leonidas had Palimpsest installed. Forums where flooded with scared voices. If you have bad sectors but remapped and below the threshold (50 or something like that) it is not that bad (for now;)).

---

### Post by scundo on 2009-11-14
Same error here.  Glad I joined this forum.  I'm new to Ubuntu and I've been playing with different versions (9.04 32 and 64 bit, 9.10 32 bit) and this error didn't surface until I wiped my XP partition and went all Linux.  When I ran this release (32 bit 9.10) on a 100gb partition the error never surfaced.  Only when I made the entire 250gb available to the OS and did a clean install did this error surface.  Odd.

---

### Post by marcdutonkin on 2009-11-15
I have installed Karmic on 3 USB hard disks connected on differents platforms. With two of these disks, i have EXT4_FS errors at boot. The first one has been used previously with jaunty without any problem. I bought the second one two weeks ago. And the badblocks command tells me there are no bad blocks on this USB hard disk. For me, it is clear that something is wrong in Karmic.

---

### Post by Usabent on 2009-11-21
It migth be just a false error becuase nothing bads happening to xp or ubuntu im able to boot in fine. So its a false error;)

---

### Post by Devi 710 on 2009-11-21
What is a good utilitiy in linux to use to make sure I don't have any real bad sectors? 

I can't use the Samsung DOS one because it only works from a live CD (can't boot from a USB) and I'm using a netbook.

Can I just boot a live Karmic session from a USB and run the ```
fdisk -l
``` command mentioned before?

Is there a live distro like Partition Magic for this? I can't find the tool/program I would use on Partition Magic's website. 

And I'm not interested in your ads for hddregenerator.

---

### Post by Devi 710 on 2009-11-21
OK, so I installed and ran GSmartControl and it said my "overall health self-assessment test" PASSED.

Though it does show the same errors as Palimpsest, which is:

ID # 197: Current Pending Sector Count=
Normalized:100
Worst: 100
Threshold: 0
Value: 61 sectors

GSmartControl also highlights:

ID # 196: Reallocation Event Count=
Normalized:100
Worst: 100
Threshold: 0
Value: 2438

and

ID # 198: Offline Uncorrectable=
Normalized:100
Worst: 100
Threshold: 0
Value: 395

So is my HD screwed up? Or does that mean Palimpsest is just quicker to say that the disk has bad sectors?

My HD is only about 3 weeks old. I partitioned a 30GB section to try some OSes, then reformatted the whole thing for Karmic. Now I have this issue. 

Should be worried? Does this need to be repaired, or can it be repaired?

Devi

---

### Post by Devi 710 on 2009-11-21
Now I am really worried.

I've booted up a live session with Parted Magic and Smart Control shows that the Raw Values have now gone up:

ID # 196: Reallocation Event Count: 2632 (up from 2438)
ID # 197: Current Pending Sector Count: 145 (up from 61)
ID # 198: Offline Uncorrectable: 517 (up from 395)

Is there anything I can do about this? Should I be doing something?

I feel like the numbers only go up when I boot from a live USB session...

---

### Post by AVH on 2009-11-24
> Is there anything I can do about this? Should I be doing something?Go to your HD manufacturer's website, download their disk utility program and run it. If your disk passes, then don't worry. If it fails return it while it is still under warranty.

There is a know bug in Palimpsest that reports bad sectors on good disks.  
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

---

### Post by Devi 710 on 2009-11-25
That is what I am trying to do. 
I downloaded the disk utility program from Seagate's website, but it won't boot from a USB and I have a netbook with no optical drive. I am just going to have to check when I have access to an external CD drive.

---

### Post by patg7590 on 2009-12-18
I am having the same/ a similar problem,

The machine is a brand new (refurbished) Dell Mini 10v

Dualbooting 9.10 NBR with xp sp3 (came on it) 

Ran a couple chkdsk /f's in xp and it fixed some stuff, the disk passed Spinrite at level 2 and now Im running it at level 4, close to an hour left. 

So what is the result of this issue? I looked through the bugtracker... Is a fix imminent? I will post my results but are people just disabling the warning? Ignoring it? Is this affecting only certain hardware or is it pretty much standard on most people's 9.10 installs? 

Thanks all. :)

---

### Post by patg7590 on 2009-12-18
> **patg7590 said:**
> I am having the same/ a similar problem,

The machine is a brand new (refurbished) Dell Mini 10v

Dualbooting 9.10 NBR with xp sp3 (came on it) 

Ran a couple chkdsk /f's in xp and it fixed some stuff, the disk passed Spinrite at level 2 and now Im running it at level 4, close to an hour left. 

So what is the result of this issue? I looked through the bugtracker... Is a fix imminent? I will post my results but are people just disabling the warning? Ignoring it? Is this affecting only certain hardware or is it pretty much standard on most people's 9.10 installs? 

Thanks all. :)

Passes SR level 4!

 I'm doing and extended self test atm, the disk is ext4, and a samsung. 

The only red/warning assessment I have is 336 Current Pending Sectors...can I safely ignore this?

---

### Post by emarkay on 2010-01-24
Looks like this bug: 
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all)

---

### Post by NeoSilverDagger on 2010-03-21
There is definitely some kind of bug, I have both Windows 7 and Ubuntu 9.10 running perfectly on my hard disk, yet palimpsest claims I have 5882 bad sectors... Somehow I don't think that is correct

---

### Post by prodigy_ on 2010-03-22
> **NeoSilverDagger said:**
> There is definitely some kind of bug, I have both Windows 7 and Ubuntu 9.10 running perfectly on my hard disk, yet palimpsest claims I have 5882 bad sectors... Somehow I don't think that is correct
Disk Utility simply reads SMART data from your HDD, so that's how HDD evaluates its own condition. Keep in mind that modern HDDs don't have "bad" sectors, they have "reallocated" ones. In terms of possible data loss it's the same thing but software that doesn't read SMART data won't alert you at all.

Buggy SMART readings are possible but having a backup never hurts.

---

