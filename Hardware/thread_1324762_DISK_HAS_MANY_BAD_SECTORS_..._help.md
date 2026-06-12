---
title: "DISK HAS MANY BAD SECTORS ... help?"
date: 2009-11-12
forum: Hardware
---

### Post by spatialwarp on 2009-11-12
So after upgrading to Karmic, I have this handy little drive assessment tool telling me in large red letters that my laptop (IBM Thinkpad T43p, 3.4 years old) has a hard disk with crutches and a terrible limp. My friend who is more experienced in such matters than I has advised me to ask here if anyone knows of a program that can help me further diagnose the extent of the problem and possibly fix it - in case it is merely the result of corrupted data. Otherwise, I am prepared to replace the disk, and I would appreciate any suggestions on buying a new HD for a T43p thinkpad.

---

### Post by Lanser on 2009-11-12
Easy to replace the hard drive in a T43. Remove, Open the case ( 4 screws ) replace with any 2.5 inch IDE drive.  I suggest seagate or fujitsu less than 320Gb.  I have replaced T42's and 43's with seagate 160's with no issues. Just remember to boot into the bios after the install and make sure the drive is recognised.  regards

---

### Post by spatialwarp on 2009-11-12
Thank you, Lanser. That will come in handy if I do indeed have to replace the drive. However, I am looking to see if anyone knows of a software program that could tell me for sure if the problem is fixable without replacing the drive. Anyone? Anyone? Beuller? Beuller?

---

### Post by Flightmare on 2009-11-13
What's the Device manufacturer/model, it's listed in your Disk Utility aswell. Most manufacturers provide tools/bootcds to check and fix your HDD health.

---

### Post by spatialwarp on 2009-11-13
The model is FUJITSU MT2080AH. After some digging, which eventually led me to Toshiba's website, the only tools they have available for diagnosing Fujitsu's HDs are for Windows only. Do you know of one that would work in ubuntu?

---

### Post by KaYnemO on 2009-11-29
The same thing happened with me and my relatively old Seagate Barracuda HDD. Downloaded bootable SeaTools for Dos, ran all possible checks and they all came back negative (meaning no errors were found). FSCK doesn't seem to find anything wrong with the disk. Just going to ignore the Palimsest Disk Utility for now.

---

### Post by buyit1986 on 2009-11-29
I am having the same problem aftrer upgrading, the smart program is telling me i have many bad sectors and my hard drive is failing. my computer is about 3 months old and i am very surprised that the hard disk is going out. are there and linux apps that will diagnose the problem/fix . also i dual boot windos and the windows drive checking utility hasnt found any errors. any help would be appreciated.

---

### Post by zanknits on 2009-12-18
I have the same problem with my 1-year old HP Pavillion dv4. On one hand, I wouldn't be surprised at all since this computer is such a piece of crap, but on the other since everyone else seems to be getting the same error message, it might be a bug...

I didn't get the error until I upgraded to koala.

---

### Post by didi2005 on 2009-12-19
I'm having same issue also after upgraded to 9.10...When checked under window using various kind tools, no error is found.
Perhaps is a bug?

---

### Post by dc2quick on 2009-12-20
I'm having this same problem on an alienware m5750. At first I thought it was my hard drive, so I swapped it out with the 2nd hard drive installed in the laptop (/dev/sdb). And it tells me the same exact thing, that  /dev/sda has many bad sectors. (note that the  I'm using a sata Fujitsu. However I can configure these Hd's in a raid 0 or raid 1. I notice when i try to configure in raid 0 that I have extreme difficulties, and can't get ubuntu 9.10 installed. Installing it out of raid works fine but regardless of what hard drive I install onto /dev/sda. Might this have something to do with my software raid controller? I'm lost, and don't know where to go from here

---

### Post by Krovas on 2009-12-20
I may or may not be having the same problem. Brand new install of 9.10(my first time); Palimpsest is reporting a relocated sector count of 196614 on my 1.5 year old Hitachi. Everything else specs out as normal. If it matters, the install is fully encrypted and x64. Please assist.

---

### Post by Geffers on 2009-12-20
> **buyit1986 said:**
> I am having the same problem aftrer upgrading, the smart program is telling me i have many bad sectors and my hard drive is failing. my computer is about 3 months old and i am very surprised that the hard disk is going out. are there and linux apps that will diagnose the problem/fix . also i dual boot windos and the windows drive checking utility hasnt found any errors. any help would be appreciated.

I know of a friend getting similar alerts after upgrading to Karmic but no other utility or Windows is giving similar warnings.

My netbook is fine but I have a solid state drive, it seems these alerts are occurring on conventional drives.

Geffers

---

### Post by kiridude on 2009-12-23
Doesn't anyone know what's up with this "bad sectors" thing?

Is it a bug or do we all need to go buy a new hard drive?

---

### Post by dc2quick on 2009-12-23
yeah what gives!?

---

### Post by kiridude on 2009-12-24
So it seems that "bad sectors" are physical faults and the drive should be replaced asap.

The issue here is the accuracy of the report claiming "bad sectors."

First, try to find a drive report tool from the manufacturer of your disk. If this tool also reports bad sectors, toss the drive. If you cannot find a tool for linux, continue below.

Second, try re-running the palimpsest disk utility again, System->Administration->Disk Utility and select the Hard Disk and click on the More Information link and re-run a self test.

Third, boot into recovery mode and run fsck.

If none of the above work, get a new disk. Luckily, they're pretty cheap.

---

### Post by Strongmind on 2010-01-14
> **kiridude said:**
> 
First, try to find a drive report tool from the manufacturer of your disk. If this tool also reports bad sectors, toss the drive. If you cannot find a tool for linux, continue below.


SeaGate has a great tool called SeaTools for DOS. It comes as a bootable iso image. It works on every hard drive. It's easier than buying a new hard drive. For me, this error was a bug in Karmic.

---

### Post by recluce on 2010-01-14
There is a known problem in Karmic with Samsung HDs. 

So if you are running Karmic and your harddrive is made by Samsung, **disregard the message and turn off monitoring of the drive in the Palimpset utility**.

To the best of my knowledge, palimpset or one of the libraries involved is unaware of the fact that Samsung drives report the raw SMART values in a reversed byte order, thus causing the report of a ridiculous number of bad sectors. 

If your drive is made by any other manufacturer, please take the warning seriously.

---

### Post by emarkay on 2010-01-24
It's a bug!  
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all)

Same issue posted here:
[http://georgia.ubuntuforums.org/showthread.php?t=1336267&page=2](http://georgia.ubuntuforums.org/showthread.php?t=1336267&page=2)

Affects Fujitsu 160 gig notebook drives, too.

---

### Post by kiridude on 2010-01-25
I'm using a dell xps and changed my hard drive. With the new drive, all error messages ceased.

---

### Post by vfigueiro on 2010-02-01
I'm definitely not an expert in this area and would appreciate any input on this. I upgraded to Koala long ago. Yesterday I opened my box to upgrade the RAM. Afterwards (not sure it's related) I got error messages about ATA BUS. I re-opened the box and made sure the SATA cables were well connected. The error messages are gone, but now Palimpsest warns me about having many bad sectors whenever I reboot, even after running its test again. All my RAID 1 arrays show up as clean, though. Both disks just passed both tests of SeaTools for DOS without errors.

Should I replace the drive, run fsck (in single user, but how, exactly?), or just ignore Palimpsest?

Palimpsest window: [ATTACH]145635[/ATTACH]
'smartctl -a' output: [ATTACH]145636[/ATTACH]

---

### Post by admiralspark on 2010-02-01
Please do a search of the forum before posting, because this topic has been covered in-depth many times. There is a KNOWN PROBLEM with Karmic giving it's users "bad data sectors", see [here]("http://ubuntuforums.org/showthread.php?t=1300590&highlight=bad+disks+karmic") and [here]("http://ubuntuforums.org/showthread.php?t=1336267&highlight=bad+disks+karmic")

---

### Post by RJARRRPCGP on 2010-02-01
Folks, please check the HDD with MHDD, scan by pressing the F4 key, after selecting your HDD on the first menu.

MHDD is good at finding even somewhat slow sectors.

Get MHDD here:

[http://hddguru.com/content/en/software/2005.10.02-MHDD/](http://hddguru.com/content/en/software/2005.10.02-MHDD/)

---

### Post by Admiral_Payne on 2010-02-02
I registered at these forums just to say thank you for looking in to this, I wouldn't have found the bug report on my own :)

Glad to see that it's not my drive failing. Any idea on how long it'll take for a bugfix?

---

### Post by Admiral_Payne on 2010-02-03
Lol.. Merely a few hours after that post it appears my HD crashed :oops:
Perhaps it's not just a bug ;) I got it back up with fsck, but who knows how long it'll take.

I guess this Samsung Spinpoint HD753LJ has had its best days. I'm going to upgrade system to x64 with new HD, anyone knows if it's possible to import (all) data from firefox/thunderbird by copying some folder(s)?

---

### Post by chrisjenkins on 2010-02-04
Hi,

I have the same problem i.e. a Seagate ATA ST340015a disk that is reporting many bad disk sectors, however I have two PC's, bought at the same time from the same shop and the same, as far as I can tell setup, but only one is reporting a problem.

I bought another disk from eBay and I'm getting the same issues, so now I'm thinking connectors, leads and the bios settings ...

I would rather diagnose the problem than pull my working machine apart to swap things over. So far I have used the SeaTools and MHDD Scans to try and detect any issues but they are both +ve.

This is certainly not my area of expertise, but hopefully somebody can guide me?

Cheers

Chris

---

### Post by Admiral_Payne on 2010-02-04
Chris, if I were you I'd check the Seagate website for a disk tool. I'm pretty sure they will have one, Seagate usually has good support.

I actually managed to get my Samsung disk working for the time being with some bogus Samsung disk repair tool from their website.
Try searching on the product name in the Seagate website and see if you can find a software or tools section.

Also, if you open the Palimpsest Disk Utility, you can pick "More Information" on the disk in question. In the "Attributes" pane you can see most of the SMART data from your HDD, scroll through it to find the items that are marked red.
You'll see "Value" and "Threshold" values; basically, if (value > threshold) broken else ignore.

What the different attributes mean, I've no idea.. I'm also clueless on how it calculates whether or not something is bad, I've got lots of stuff that's way over threshold but still in the green... Just go for the red things ;)
If you see a lot of red things where value is over threshold, you should definitely get yourself a new disk.

Hope this is an answer to your question,

---

### Post by mdrake36 on 2010-02-09
> **admiralspark said:**
> Please do a search of the forum before posting, because this topic has been covered in-depth many times. There is a KNOWN PROBLEM with Karmic giving it's users "bad data sectors", see [here]("http://ubuntuforums.org/showthread.php?t=1300590&highlight=bad+disks+karmic") and [here]("http://ubuntuforums.org/showthread.php?t=1336267&highlight=bad+disks+karmic")
This is an obnoxious answer to a legitimate thread. why would you care how many threads cover similiar issues. Thanks to this bug my computer completely crashed an I was enjoying this dialog until you got snotty. 
I got a big X in middle of my screen. So just help out, with out, the tude....:popcorn: Here and Here cuz I am typing this message from a damn xp system

---

### Post by tgalati4 on 2010-02-09
I'm not sure which is worse:

1.  A crashed disk taking your favorite linux distro with it.
2.  Having to use Windows XP to fix it.

---

### Post by mdrake36 on 2010-02-09
Luckly I have no important stuff on my HDD. Hopefully I can just wipe it and start over. I wonder what caused my hard drive to dump like this?
I have been messing wiht the Priorities alot on my Ubuntu Studio way too much.
 
Using XP is the worst.
 
I don't mind starting over. I backed up my stuff pretty good.
What is the best way to re-image?
 
FIX A BROKEN SYSTEM
 
or 
 
INSTALL NEW SYSTEM

---

### Post by mdrake36 on 2010-02-09
> **RJARRRPCGP said:**
> Folks, please check the HDD with MHDD, scan by pressing the F4 key, after selecting your HDD on the first menu.
 
MHDD is good at finding even somewhat slow sectors.
 
Get MHDD here:
 
[http://hddguru.com/content/en/software/2005.10.02-MHDD/](http://hddguru.com/content/en/software/2005.10.02-MHDD/)
 
Used your tool and its doing its thing and my drive is a mess.
 
Now what?

---

### Post by mdrake36 on 2010-02-09
> **tgalati4 said:**
> I'm not sure which is worse:
 
1. A crashed disk taking your favorite linux distro with it.
2. Having to use Windows XP to fix it.
 
I might try Juanty Studio RT kernel
I have had some scary things happen in Karmen Koala
Jaunty even booted my Broadcomm WiFi which Karmin has yet to figure out.
Now this and not to mention the whole Pulse Audio thing.
I just figured out the Pulse problems when my HDD crashed.
what do you think?

---

### Post by 23dornot23d on 2010-02-09
I am still using Karmic Koala .... but it worries me ......

I now see on this thread that certain drives do not work properly at boot ...

Do we need to add the Iomega Terra USB drives to the list .... 

They mount ok in all my other systems .....

Ubuntu 8.10 and Mandriva and Vista on this quad boot system .....

Yet Karmic 9.10 does not mount or dismount them which I have yet to find out why ......

I had to use Thunar and after 20 seconds or so all partitions in the USB drive mount ... but this is the error I see
before this happens ...........

[IMG]http://i50.tinypic.com/2mmyat5.jpg[/IMG]

and why after leaving Karmic and going into 
Mandriva 2010 it checks the disk and finds problems on the drive 
(but never the other way around) ...... causing it to do a re-boot each time .....
as well as worrying what is being altered to cause this to happen .....

But hopefully that will come to light soon ..... some reports say that its because it was not properly dismounted from Vista .... 
but that does not seem to be the case here ....... as it works perfectly in the other systems .....

I do not know if this is related to the same bug ..... does anybody know of any issues with USB drives not working as they should in Karmic 
and is there a known problem / solution ? ( any help on this matter would be appreciated )

---

### Post by Nick_Jinn on 2010-02-10
For those of you who dont know this, the new Ubuntu is RESPONSIBLE for your HD failing, indirectly in conjunction with default factory settings of the hardware.

I would have thought that everyone would have been aware of this by now and it would be fixed.

I have lost 3 hard drives in 3 months...Not a coincidence and not acceptable.

When is this really going to get fixed?

---

### Post by Admiral_Payne on 2010-02-10
> **Nick_Jinn said:**
> For those of you who dont know this, the new Ubuntu is RESPONSIBLE for your HD failing, indirectly in conjunction with default factory settings of the hardware.
Ouch.. Do you have an idea which settings it'd be?

---

### Post by mdrake36 on 2010-02-11
My Distro was fine for like three weeks strong and I was tweeking it abusively.
My HDD crashed immediately after Logging on to the repository two days ago I was able to repair the hard drive with the sticky sector cleaner. 
> **RJARRRPCGP said:**
> Folks, please check the HDD with MHDD, scan by pressing the F4 key, after selecting your HDD on the first menu.
 
MHDD is good at finding even somewhat slow sectors.
 
Get MHDD here:
 
[http://hddguru.com/content/en/software/2005.10.02-MHDD/](http://hddguru.com/content/en/software/2005.10.02-MHDD/)
I am Prepping to regress to Juanty Studio or Studio 64 (ouch) please help me understand why. I want to stick with Ubuntu cuz everybody is so awesome here.
 
 
HDD finally quieted down turned off failing notification crossed my fingers.
Should I go back to Juanty?

---

### Post by recluce on 2010-02-13
> **Nick_Jinn said:**
> For those of you who dont know this, the new Ubuntu is RESPONSIBLE for your HD failing, indirectly in conjunction with default factory settings of the hardware.


Any hard facts to substantiate the above claim?

This sounds very much like an urban legend.

---

### Post by waynefoutz on 2010-02-13
Installing Karmic was how I found out my hard drive was failing. I came here and was told no, it's a known bug. I went and got a diagnoses app for windows that reads the SMART data, and yes, the drive was failing. I borrowed a copy of Spinrite, and indeed, the drive was NOT in good shape. 

I don't think the Palimsest Disk Utility is buggy. And I don't think Ubuntu is destroying hard drives. I think what's happening is a lot of people who have never had access to the SMART data on their drives are finding problems they didn't know they have. I took my drive out, replaced it, and now Karmic says it's healthy. I made the old drive into an external with an enclosure kit, I figure it has some life in it if it's used that way.

---

### Post by recluce on 2010-02-13
> **waynefoutz said:**
> Installing Karmic was how I found out my hard drive was failing. I came here and was told no, it's a known bug. I went and got a diagnoses app for windows that reads the SMART data, and yes, the drive was failing. I borrowed a copy of Spinrite, and indeed, the drive was NOT in good shape. 

I don't think the Palimsest Disk Utility is buggy. And I don't think Ubuntu is destroying hard drives. I think what's happening is a lot of people who have never had access to the SMART data on their drives are finding problems they didn't know they have. I took my drive out, replaced it, and now Karmic says it's healthy. I made the old drive into an external with an enclosure kit, I figure it has some life in it if it's used that way.

Palimpset is buggy under very special circumstances, see below.

[SIZE="6"]Please, people, note the following:[/SIZE]

**_Samsung HDs_**
Palimpset (or one of the libraries used by it) is broken for SMART attribute 197 "Current Sectors Pending". If you have a Samsung HD and **only** attribute 197 shows a raw error rate in the millions - with the normalized value being 100 or close to it: disregard, it is not a hard drive issue. If you get errors for any other attribute, it is likely to be a harddrive problem and needs further investigation.

**_Fujitsu HDs_**
I have read some reports about false positives for some Fujitsu drives. I cannot test or confirm this here, so additional input would be welcome.

**_Seagate HDs_**
I have only seen anecdotal evidence of a malfunction of palimpset with Seagate HDs and my tests indicate that there is no problem.

[SIZE="4"]Conclusion: disregard SMART attribute 197 errors on Samsung drives under Karmic. Any other error, any other drive: use one of the many SMART test suites that are around, many do not require Windows. Smartmon Tools under Jaunty, for example, work very well. If possible, use your drive manufacturer's tool suite.[/SIZE]

---

### Post by Admiral_Payne on 2010-02-14
> **waynefoutz said:**
> Installing Karmic was how I found out my hard drive was failing. I came here and was told no, it's a known bug. I went and got a diagnoses app for windows that reads the SMART data, and yes, the drive was failing. I borrowed a copy of Spinrite, and indeed, the drive was NOT in good shape. 

I don't think the Palimsest Disk Utility is buggy. And I don't think Ubuntu is destroying hard drives. I think what's happening is a lot of people who have never had access to the SMART data on their drives are finding problems they didn't know they have. I took my drive out, replaced it, and now Karmic says it's healthy. I made the old drive into an external with an enclosure kit, I figure it has some life in it if it's used that way.
Same here. I disregarded it and lost my data.. ouch!
New disks are working fine and the disk utility is reporting everything in the green.
From now on I'm running RAID5 and closely watching the Palimpset ;)

---

### Post by tstrike on 2010-02-27
> **recluce said:**
> Palimpset is buggy under very special circumstances, see below.

[SIZE=6]Please, people, note the following:[/SIZE]

**_Samsung HDs_**
Palimpset (or one of the libraries used by it) is broken for SMART attribute 197 &quot;Current Sectors Pending&quot;. If you have a Samsung HD and **only** attribute 197 shows a raw error rate in the millions - with the normalized value being 100 or close to it: disregard, it is not a hard drive issue. If you get errors for any other attribute, it is likely to be a harddrive problem and needs further investigation.

**_Fujitsu HDs_**
I have read some reports about false positives for some Fujitsu drives. I cannot test or confirm this here, so additional input would be welcome.

**_Seagate HDs_**
I have only seen anecdotal evidence of a malfunction of palimpset with Seagate HDs and my tests indicate that there is no problem.

[SIZE=4]Conclusion: disregard SMART attribute 197 errors on Samsung drives under Karmic. Any other error, any other drive: use one of the many SMART test suites that are around, many do not require Windows. Smartmon Tools under Jaunty, for example, work very well. If possible, use your drive manufacturer's tool suite.[/SIZE]

 Karmic has a bunch of problems running on my Alienware M15X.. After I performed a hardware swap with Dell Alienware (that was a journey that requires 5 cigarettes and a six pack of beer JUST to calm down from their support folks).. Karmic was still showing red on a brand new hard drive.   I have since switched to Hardy Heron and this problem disappeared... I mean I did everything from badblocks to you name it.  Is Karmic Ubuntu's version of Vista?

---

### Post by RJARRRPCGP on 2010-03-04
> **mdrake36 said:**
> 

I am Prepping to regress to Juanty Studio or Studio 64 (ouch) please help me understand why. I want to stick with Ubuntu cuz everybody is so awesome here.

Should I go back to Juanty?

At this time, I think Karmic Koala is unacceptable. 

I recommend going back to Jaunty Jackalope or to Lucid Lynx alpha 3, if you want to test drive. ;)

---

### Post by tstrike on 2010-03-04
> **RJARRRPCGP said:**
> At this time, I think Karmic Koala is unacceptable. 

I recommend going back to Jaunty Jackalope or to Lucid Lynx alpha 3, if you want to test drive. ;)

 I went back to Jaunty .... Life is good again!  Karmic Koala is not ready for primetime.

---

### Post by psusi on 2010-03-04
Even if a drive reports the pending sector count in the wrong byte order, it is still a bad sign.  It just means instead of 1 you see millions, but even 1 bad sector is not good.

---

### Post by filtermeout on 2010-03-05
I recently upgraded to 9.10 as well (from 9.04).  Disk has many bad sectors were reported...  I quickly shut the laptop down, spent a couple of hours backing up critical files (needed to do that anyway) and replaced with another hd.  Installed 9.10, same issue.. Two in one day?? - So I installed a third (new in box)...  Same...   I run dual boot and WinXP / Win7 do not see any issues.   Thoughts?

---

### Post by psusi on 2010-03-05
I'm not familiar with this program you're using.  If you install the smartmontools package then run sudo smartctl -A /dev/sda, it will print out all kinds of information on the drive.

---

### Post by monkeyface766 on 2010-04-17
I got this error upon installation of 9.10. Performing a system update solved the issue immediately.

-Austin

---

### Post by solutionorppt on 2010-04-17
Had the same problem, updates will take care of the issue... take a deep breath... all will be well.

I had installed Karmic Koala in a dual boot on my HP, and I freaked out a little bit when I got the 'HD failure imminent' message... it will vanish when you install all of the recent updates.

---

