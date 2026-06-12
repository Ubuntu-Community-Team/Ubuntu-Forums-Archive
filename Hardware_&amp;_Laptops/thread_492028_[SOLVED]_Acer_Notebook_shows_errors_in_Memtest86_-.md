---
title: "[SOLVED] Acer Notebook shows errors in Memtest86 - need advice today!"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by randytuggle on 2007-07-04
My ACER Aspire notebook has been giving me errors when booting cold or while running using Windows XP Media Center Edition. While using Windows, I got FIXED DISK FAILURE messages and the PXE-E61 error while booting or rebooting. Also, the system would crash while operating after a short time period.

I have used Ubuntu on this machine and always thought Ubuntu slowing down was a Linux issue - so I would go back to Windows and try a fresh reformat and reinstall of the standard OS for this computer.

I installed Ubuntu last night and ran Memtest86 and fsck on it a few times. I got errors on the automatic run of fsck during my initial startup - it's not given the errors since that time.... When I run Memtest86, I get errors starting at test 4, then test 6, and almost every test thereafter. The errors say FAILED ADDRESS 00000000000 and BAD 00000000 on slot 1 - I think slot 1...whatever the last column says.

Is this a hard drive issue (has Hitachi Travelstar 80GB drive), a motherboard problem, or just memory? I tried swapping the memory yesterday while testing under Windows XP.. removing one 512 (2 of these in it) didn't help - and I swapped the positions of the two memory chipsets also. I am about ready to buy a new hard drive but the test I ran on the drive (provided by Hitachi - called Drive Fitness Test) returned no errors. I am stuck for any ideas on what to do! PLEASE HELP!! If you know what the memtest86 error codes I got mean, please tell me. Thank you!

Randy

UPDATED NOTE: The memtest86 results show no address being bad OTHER THAN 00000000000 at 0.0MB. No memory chipsets installed show address errors with real addresses. FSCK runs alot at startup but no real errors are shown. Just 0.8% contiguous files is displayed at the end of the check.

---

### Post by az on 2007-07-04
> **randytuggle said:**
> My ACER Aspire notebook has been giving me errors when booting cold or while running using Windows XP Media Center Edition. While using Windows, I got FIXED DISK FAILURE messages and the PXE-E61 error while booting or rebooting. Also, the system would crash while operating after a short time period.

I have used Ubuntu on this machine and always thought Ubuntu slowing down was a Linux issue - so I would go back to Windows and try a fresh reformat and reinstall of the standard OS for this computer.

I installed Ubuntu last night and ran Memtest86 and fsck on it a few times. I got errors on the automatic run of fsck during my initial startup - it's not given the errors since that time.... When I run Memtest86, I get errors starting at test 4, then test 6, and almost every test thereafter. The errors say FAILED ADDRESS 00000000000 and BAD 00000000 on slot 1 - I think slot 1...whatever the last column says.

Is this a hard drive issue (has Hitachi Travelstar 80GB drive), a motherboard problem, or just memory? I tried swapping the memory yesterday while testing under Windows XP.. removing one 512 (2 of these in it) didn't help - and I swapped the positions of the two memory chipsets also. I am about ready to buy a new hard drive but the test I ran on the drive (provided by Hitachi - called Drive Fitness Test) returned no errors. I am stuck for any ideas on what to do! PLEASE HELP!! If you know what the memtest86 error codes I got mean, please tell me. Thank you!

Randy


When your ram fails, you can't trust any other diagnostic tool you use on that machine, since faulty ram will cause any application to throw random errors.

If you run with just one stick of ram, do you get the same errors?  Try running one stick in one slot and then in the other, to determine if one slot is bad rather than the individual stick.

If you get memory errors with both sticks individually, the problem may be your motherboard or perhaps a temperature problem.

---

### Post by randytuggle on 2007-07-04
I just did a google search on memtest86 failed 00000000000 and what I found out was that the motherboard may be the culprit. The FAILED 00000000000 message usually means dry contacts on the motherboard and not RAM failures. The site I found suggested replacing the motherboard. This kinda makes sense considering the hard drive not being detected at startup, the sudden Windows crashes, the random errors,etc. I guess the hard drive doesn't need replacement after all. I will never buy another ACER product. I just got this one in February - so it's just out of the 90 day warranty on a refurbished unit - provided by TigerDirect.com

I wish I had a workaround to fix this problem without buying a new board... thanks!

---

### Post by randytuggle on 2007-07-04
> **az said:**
> When your ram fails, you can't trust any other diagnostic tool you use on that machine, since faulty ram will cause any application to throw random errors.

If you run with just one stick of ram, do you get the same errors?  Try running one stick in one slot and then in the other, to determine if one slot is bad rather than the individual stick.

If you get memory errors with both sticks individually, the problem may be your motherboard or perhaps a temperature problem.

BTW, I did that yesterday and got the same problems...:(
However, since writing this post this morning I haven't had any really bad issues with the computer. Maybe fsck fixed my problems that were associated with the hard drive earlier?

---

### Post by az on 2007-07-04
> **randytuggle said:**
> Maybe fsck fixed my problems that were associated with the hard drive earlier?

Until you rule out the problem with ram or your motherboard, you will not know if your hard drive even had a problem.  Your drive problems are the symptom, not the cause.  A corrupt drive does not bork your ram - memtest runs without even looking at the disk.  But bad ram can make anyting show errors.

---

### Post by randytuggle on 2007-07-04
I'm still kicking on Ubuntu for today. No problems so far on Independence Day! I don't understand what the heck it is/was.  I did some more research on the memtest86 error codes and found that they are kind of a non-issue. It appears the program just does that on lots of hardware. I'm going back to believing the issue was/is hard drive related and will keep an eye on recurring issues. If the system takes a dump again (and it doesn't look as if it will), I will try a new hard drive and run it like crazy. Too many errors in windows pointed to the hard drive. I would take it out and reseat it and would usually get the same errors in time. Some issues I had such as slow,erratic mouse pointers, slow booting, slow running system after cold booting, etc. make me believe the drive was at fault all along. Thank you so much for your help on this concern. I appreciate your assistance and will do what you suggested step-by-step if the system fails again.

---

### Post by az on 2007-07-04
> **randytuggle said:**
> I ... will do what you suggested step-by-step if the system fails again.

Use badblocks to look for hard disk failures:


sudo badblocks -s /dev/sda1 

There is also a write test (-w) which would erase your whole disk in the process...

---

### Post by randytuggle on 2007-07-04
will do! thanks! I ran the test and it finished without showing any output of errors. I guess that means my drive has no bad blocks?

---

### Post by az on 2007-07-04
> **randytuggle said:**
> will do! thanks! I ran the test and it finished without showing any output of errors. I guess that means my drive has no bad blocks?

Correct.

---

### Post by randytuggle on 2007-07-04
Just installed new hard drive. Trying it out with Windows (since Windows memory functions will show wear on system much faster than Ubuntu). Will let you know if it was the hard drive or something happens. Thank you!

---

### Post by randytuggle on 2007-07-05
I installed new Western Digital drive and used Windows to test it. I had errors in the log file within one hour. I've decided to return the new drive and continue using the Hitachi Travelstar until I get a new notebook. Maybe I'll buy one within the year? Who knows. Thanks for your help!

---

### Post by l5110 on 2007-07-05
i think  you can use a new ram to replace the ram you using now , then you could know if it is you ram 's problem ,the same as your harddisk...

---

### Post by bobpur on 2007-07-05
I'm going out on a limb here, but how old are those two OS disks your installing from? How much use have they seen? 
I'm suggesting, maybe, that your disks are corrupted (scratched) causing the errors your getting. Burning a new disk, at least in linux, is cheaper than mobos and hard drives.
Just a thought.

---

### Post by tgalati4 on 2007-07-05
If I understand this post correctly, you bought a refurbished Acer notebook with a 90-day warranty.  Why was this notebook in the refurbish queue?

Could it be a manufacturing issue with the motherboard?  Perhaps it's a flaky solder job on the RAM slots.  Either way, the machine ended up in the refurb bin.  It was bench-checked and then resold.  Happens all the time.

There are known-knowns:  Known issues with known consequences.
There are known-unknowns:  Known issues with unknown consequenses.
Then there are unk-unks:  Unknown issues with unknown consequenses.

Your system exhibits a little of all three.  Plead your case with Tiger they may be sympathetic.

Good luck.

---

### Post by randytuggle on 2007-07-05
I'm going to try and address these past few posts. The OS disks I have been using are not old. They go back about 2-4 months. I've tried all kinds of OS installs and they all exhibit the same symptoms.

I could try new RAM. That may be an option I will look into - gotta buy some though...

I could plead the case with Tiger  but I doubt they'd help. I will try that option. I believe that the problem DOES come from the board. Poorly connected items or blown capacitors,etc. could be the culprit.

---

### Post by randytuggle on 2007-07-05
Well, it seems when I use the original hard drive, the system runs fsck at most startups. I get one simple message at completion stating 0.8% or 0.9% contiguous files. Nothing more. The system has started to reboot on it's own without warning at times,too.

How about a BIOS update? I'm using Phoenix Bios v.2 that came with the machine. It's very cheesy and not too changeable. Is there somewhere I can get a better BIOS to download and update this one? I'm going to go out on a limb with this question: Is it possible that I need to run a 64-bit OS on this computer? I've been running 32-bit versions of Windows and Ubuntu. I tried the 64-bit version of Ubuntu 6 and had a few display problems on startup - so I stuck with the 32-bit versions since then.

---

### Post by randytuggle on 2007-07-05
UPDATED: The original hard drive just hung up (hd light was illuminated) as computer was being used. I haven't had any luck with 7.04 using my ENE memory card reader - so what I'm going to do is to format and install Ubuntu 6.10 (edgy) and that will make my ENE card reader work again - and HOPEFULLY show no errors with my hard drive in the process. I'll update this with results. I'm really looking for an answer to this one! I've contacted TigerDirect by email and explained the situation to them about the possibilities of them sending a system with a bad board. I'll see if they are helpful...

---

### Post by randytuggle on 2007-07-05
ok. 6.10 is installed and currently updating 171 files. The ENE card reader doesn't work as I thought it once did...but oh well, that was my old HP desktop (duh!).

I noticed that the 7.04 system always posted a BIOS BUG 18 error - and 6.10 doesn't do that. That's good, I guess! I'll see if this works to alleviate the system problems.

---

### Post by randytuggle on 2007-07-08
:popcorn:

I think it's finally repaired as best as it can be under the circumstances. I did a dozen installs of Ubuntu 7 - 64-bit version -- and after assembling the thing from parts on the floor, it finally works without a hitch tonight!!!!!!

I upgraded the BIOS from a file newly-added to the ACER site, I used the Hitachi Drive Fitness Test tool (on their site) to fully erase the hard drive, then installed Ubuntu two or three times or more.

Finally, the hard drive stopped being a pain and the system is running great! One thing I did differently was to install bcm43xx_compwiz18.1 for the Broadcom 4318 wireless. I think the ndiswrapper was causing my soundcard to go back to flaky one-speaker-startup-mode.

The Ubuntu 7.10 64-bit version has allowed me to use alsamixer - whereas other versions did not from the start.... I will not run updates as they just mess this system up for me. They kill alsamixer and tend to mess up my install - the way it works great from the start.

I thank everyone for their help and I just want to say this: UBUNTU IS THE BEST!!!!! No Windows or Mac OSX for me! BTW, I love FSCK! It's too cool.

---

### Post by randytuggle on 2007-07-12
I don't believe this!!!!! The memtest errors were caused by the clock being wrong in the bios! GTFOH!!!!!! I have wasted WAY too much time on this due to my own ignorance of the system clock! Word to the wise: never overlook the clock when starting to tweak your bios settings.

Also, the Acer laptop will overheat quickly unless power management is set to run at a minimal CPU speed. I guess the components Acer supplied cannot be pushed to operate that much...

---

