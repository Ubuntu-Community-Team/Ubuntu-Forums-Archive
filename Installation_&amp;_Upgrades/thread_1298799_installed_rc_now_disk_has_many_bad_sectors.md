---
title: "installed rc now disk has many bad sectors"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by mnoyes on 2009-10-23
(Upgraded from 9.04, that is) Never got this message before. ATA Samsung HM160HI.:(

---

### Post by mikewhatever on 2009-10-23
Well, there is a first time for everything. In Karmic, there is a startup program that notifies about bad sectors. You should watch it, cause if the number of bad sectors is rising, you might have a disk failure soon.

---

### Post by frodon on 2009-10-23
Don't forget to run a disk test with another tool, it always helps to have different sources to avoid false positive which can always happen with any software.

If 2 different tools report bad sectors then this it is more likely to be real.

---

### Post by presence1960 on 2009-10-23
> **frodon said:**
> Don't forget to run a disk test with another tool, it always helps to have different sources to avoid false positive which can always happen with any software.

If 2 different tools report bad sectors then this it is more likely to be real.

+1

When I installed karmic it gave me warnings about my brand new Seagate SATA hard disk. I used a Seagate Seatools bootable CD to check the disk and it was fine. I even booted into windows and used software to check it and again everything passed.

---

### Post by CeeJayCee on 2009-10-23
I have the same issue: ATA Samsung HM320JI reporting that the "Disk has many bad sectors".

I googled the error a bit and it seems like this is a bug rather than an actual problem.

---

### Post by mnoyes on 2009-10-23
Thanks for the quick replies -- this is helpful, I suspected a bug, but I will do a scan with another utility -- by the way, what is a good tool for checking the hard disk (other than Palimpsest Disk Utility that is giving me the error message)?

---

### Post by jamsh on 2009-10-23
I'm getting the same message after updating earlier and intend to ignore it.  I have disabled the message in Disk Utility.

---

### Post by presence1960 on 2009-10-23
> **mnoyes said:**
> Thanks for the quick replies -- this is helpful, I suspected a bug, but I will do a scan with another utility -- by the way, what is a good tool for checking the hard disk (other than Palimpsest Disk Utility that is giving me the error message)?

Your hard disk manufacturer's web site should have the software to run to check your disk. I use Seagate exclusively and they have a bootable version of the software to run the utility, which is great because you don't need windows to run it.

---

### Post by mnoyes on 2009-10-24
Found the tool but...

"ES Tool can test a drive solely manufactured by Samsung. It is strongly recommended to back up the user's significant data in advance because ES Tool has a Write operation that can erase it. Samsung has no responsibility of lost data." ([http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html](http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html))

Not sure I want to go down this path! Seems better to ignore the warning -- I have no other reason to suspect hard disk trouble -- and hope that when I upgrade to the final version of 9.1 it will go away...

---

### Post by Dangger on 2009-10-24
I'm having the same issue. It suddenly started warning me as soon as I got Karmic's RC. Will try to run the SAMSUNG tool

---

### Post by howefield on 2009-10-24
Seldom seen so many posters complaining about bad sectors.

Try the vendors website to see if they have some diagnostic software you can try as well.

---

### Post by heldr on 2009-10-26
Got the same error installing Karmic on a brand new Toshiba.

---

### Post by ChuckMcB on 2009-10-26
Ditto. Reported bad sectors after fresh install on Dell D600.

---

### Post by linfidel on 2009-10-29
I just got the error booting from the Karmic CD on my Seagate ATA drive.  It's fairly old, but I doubt that it's bad.  However, I'll do some checking

I had a few programs on Windows that test SMART parameters, but none for linux.  There must be some, though.  Or maybe a bootable disk from Seagate will do it.  I'll check back.

---

### Post by oblador on 2009-10-29
I'm pretty sure palimpsest is giving false positive bad sectors warnings. I ran a handful other tools to examine my hd and everything went fine. The only program which appears to see the errors is palimpsest. I'm not going to trust this software.
I disabled it from begining with the session, is there another tool I can use in ubuntu 9.10?

---

### Post by small_potato on 2009-10-31
got the same message on ATA fujitsu mhv2060bhpl

---

### Post by DrIdiot on 2009-10-31
I got the same error.  My hard drive is an ATA ST3320620AS (Seagate Barracudy I think?).  I booted the liveCD and ran e2fsck and it came back all fine, so I think the application is just buggy.

Though, I recommend a fsck just to be sure.

---

### Post by ertw1 on 2009-11-03
> **Dangger said:**
> I'm having the same issue. It suddenly started warning me as soon as I got Karmic's RC. Will try to run the SAMSUNG tool

I have a samsung HM251Jl, and I tried using the estool but it did not work :(.  I burned the estool iso image ([http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html](http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html)) to a blank disc.  I restarted my computer and booted from the disc.  The estool.exe screen appears and asks to proceed with the test, when I hit 'y' the screen fills with red lines which say:

invalid opcode at 0017 0000 0003 50D2 016E FFFF 0046 0017 0000 0003 50Ed 016E FFFF

Finally it stops and says "Out of interrupt stacks!".

Please help me, my bad sector count is increasing :(

UPDATE: I found the compatibility list for samsung hutil diagnostic tool here: [http://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html](http://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html) .  Sadly my model isn't on the list, which could explain my problem...

---

### Post by expatCM on 2009-11-05
I have upgraded four machines to 9.10 from 9.04.  One is 64 bit and three 32 bit.

EVERY machine is reporting this message.  The drives all appear to be fine so I guess this is some sort of bug ......

---

### Post by linfidel on 2009-11-05
> **expatCM said:**
> I have upgraded four machines to 9.10 from 9.04.  One is 64 bit and three 32 bit.

EVERY machine is reporting this message.  The drives all appear to be fine so I guess this is some sort of bug ......Man, they just don't make hard drives like they used to!  ;)

---

### Post by expatCM on 2009-11-05
Yes, and that really is a blessing since we now enjoy very reliable drives :)

---

### Post by akaAndrew on 2009-11-07
My WD drive is only just a year old, a replacement for the original that died. 

It has 304 bad sectors, and increasing daily (297 yesterday). That figure reported by Palimpsest and confirmed by HardDiskSentinel. I'm downloading a WD tool to run another test and then I'll probably zero the disk and reload everything... and cross my fingers.

Disks die, I have no problem with that. What I'd like to know though is why these bad sectors are increasing at such a rate. Is there something about the environment (either hardware or software) that encourages it? My laptop runs hot for instance. Could that be a cause?

I don't want to go putting another HD in just to have it start failing again.

---

### Post by bendib on 2009-11-16
> **DrIdiot said:**
> I booted the liveCD and ran e2fsck and it came back all fine, so I think the application is just buggy.
 Ok, now run "smartctl -H /dev/sda" without the quotes where sda is the drive ID.

---

### Post by Devi 710 on 2009-11-18
Any other updates on this?

I first installed installed the RC for 9.10 on my new Dell Mini 10v. Then I formated everything and installed the final 9.10.

I partitioned and installed Ubuntu Moblin Remix, then Moblin v2.1 over of that (ext3). I then formated the whole HD and installed Ubuntu 9.10 final again. Now I am getting the bad sector error.

I installed 9.10 from a different image this time. Could that be it? When I boot from the USB and run "check disk for errors" it says it's fine.

The HD is 160GB ATA SANSUNG HM160HI

---

### Post by expatCM on 2009-11-18
This situation appears to have another perspective ....

If it is a bug then it should be quickly addressed since, based on the number of drives I have now seen reporting this error, if it is indeed an error with drives then the likes of Seagate and WD are going to be flooded with RMA requests.  

This would certainly focus their attention and if it was found to be without foundation (really a bug) then there would be some negative Ubuntu feeling from the storage sector....

---

### Post by Devi 710 on 2009-11-18
So is this a bug with Ubuntu or the Hardware??

If it is Ubuntu, has anyone reported the problem? I've never done something like that before.

---

### Post by linfidel on 2009-11-19
> **expatCM said:**
> This situation appears to have another perspective ....

If it is a bug then it should be quickly addressed since, based on the number of drives I have now seen reporting this error, if it is indeed an error with drives then the likes of Seagate and WD are going to be flooded with RMA requests.  

This would certainly focus their attention and if it was found to be without foundation (really a bug) then there would be some negative Ubuntu feeling from the storage sector....I don't think they will cover a drive that is reputedly failing - they cover drives that have failed already.  All drives are in the process of going bad, it's a matter of interpretation as to how bad they are.

I had installed another SMART utility (smartctl, I think), and it showed the exact same results, although it didn't tell me to worry about it. :)

FWIW, I have two identical Seagate drives, old 250 GB ata drives.  One shows warnings for a couple of parameters, the other checks fine.  The bad one has consistent results.  I'm using it as a backup for the good drive.

I suspect the software is reporting the information correctly; it may be misinterpreting the data, though, or being alarmist or premature about it's warnings of dire consequences.

---

### Post by suzieboy on 2009-11-28
hey all, iam experiencing the same problem with my new dell mini 10v..other than that it works fine when i disable the notification.
Any ideas or fixes?
Should i really be concerned?

---

### Post by akaAndrew on 2009-11-30
WD replaced my year old disk on RMA with no problems (304 reported bad sectors).

I'd say that's a 'thank you' to palimpsest! It did what it was mean to do and warned me of impending disk failure. Prior to the upgrade to 9.10, I was completely unaware of the problem. The new drive is, so far and touch wood, fine.

---

### Post by expatCM on 2009-11-30
Yes but I think that is the point.  The hdd manufacturers do not tend to challenge a request for an RMA, they tend to accept the customer concern.  They already know that a large percentage of hard drives are actually just fine but it is better to replace and keep a happy customer than explain that the problem may be elsewhere.

All hard drives have bad sectors.   100% all of them.  304 bad sectors are reported by akaAndrew.  I wonder, if that was say a 1TB drive, is 304 bad sectors a problem or not.  I know that Ubuntu identifies the sectors and flags a warning message but if the sensitivity level were lowered the warning would not appear and I suspect the drive would keep working.

This I think is a bit of a difficult situation since I have not yet seen any objective data as to what is and is not an acceptable number of bad sectors and on what drive size.

---

### Post by JiMMaR on 2009-12-02
ok , I'm having the same probelm here too
I'm using a dell inspiron 1520 , HD samsun HM320JI (320GB)
I did't have any problems with 9.04(32bit) , but when I installed 9.10(64bit) it keeps on saying my disk is failing (palimpsest).
was 5787 bad sectors about 3 days ago and it's 5878 now (someone got problems with 8's and 7's ? :P)

anyway , I tried using the win7 chekdsk thingie , and used 2 other windows programs (and one running on dos booting from flash memory) .. all negative , saying my disk is 100% fine.
if this was a bug , then why is the number of bad sectors increasing ? .. I just had a clean install for both my operating systems , don't wanna go back to that again T.T

so .. anything new about this ?

---

### Post by phillw on 2009-12-02
> **JiMMaR said:**
> ok , I'm having the same probelm here too
I'm using a dell inspiron 1520 , HD samsun HM320JI (320GB)
I did't have any problems with 9.04(32bit) , but when I installed 9.10(64bit) it keeps on saying my disk is failing (palimpsest).
was 5787 bad sectors about 3 days ago and it's 5878 now (someone got problems with 8's and 7's ? :P)

anyway , I tried using the win7 chekdsk thingie , and used 2 other windows programs (and one running on dos booting from flash memory) .. all negative , saying my disk is 100% fine.
if this was a bug , then why is the number of bad sectors increasing ? .. I just had a clean install for both my operating systems , don't wanna go back to that again T.T

so .. anything new about this ?

There is a bug report for palimpset -- it's over here. [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

If you get a launchpad account (free) you can tag the 'it affects me' and you will receive updates on the progress. It has been triaged, which means it is in the system being, looked at.

(Having more bad blocks reported than you physically have on your drive is real head-scratcher :-)  )

/edit - as noted below - And in the bug-report - It is recommended that you download the disk test utility from your hard-disk manufacturer and run it.

Regards,

Phill.

---

### Post by linfidel on 2009-12-02
> **JiMMaR said:**
> ok , I'm having the same probelm here too
I'm using a dell inspiron 1520 , HD samsun HM320JI (320GB)
I did't have any problems with 9.04(32bit) , but when I installed 9.10(64bit) it keeps on saying my disk is failing (palimpsest).
was 5787 bad sectors about 3 days ago and it's 5878 now (someone got problems with 8's and 7's ? :P)

anyway , I tried using the win7 chekdsk thingie , and used 2 other windows programs (and one running on dos booting from flash memory) .. all negative , saying my disk is 100% fine.
if this was a bug , then why is the number of bad sectors increasing ? .. I just had a clean install for both my operating systems , don't wanna go back to that again T.T

so .. anything new about this ?
I wouldn't be too quick to dismiss this as a bug.  And I especially wouldn't be thinking that "you had no problems with 9.04" or lower, unless you actually ran a utility that read the disk's SMART data.  Windows chkdsk doesn't, so it won't tell you anything about what the drive reports as potential problems, which is what SMART does.

SMART is a system the drive manufacturers use to report potential problems, but the interpretation of the data is not standardized.  Each drive handles bad sectors diferently, and Ubuntu is simply reporting the data that the drive is reporting.  If you were to run a different utility to read this, I'm pretty sure you would find the same numbers.

If there is a problem, it is that Ubuntu may be misinterpreting the numbers, and making it sound worse than it really is. 

FWIW, I have two identical drives, although one has been used more than the other.  Ubuntu reported problems with one, and none with the other, so it's hard to imagine that there might be a bug in reading the data.  I also used a different program, and got the same results.

In my case, the number is consistent, so it could be that the sectors got damaged previously, and the drive is OK now.  But if it was getting progressively worse, I would be concerned.

---

### Post by JiMMaR on 2009-12-03
> **linfidel said:**
> I wouldn't be too quick to dismiss this as a bug.  And I especially wouldn't be thinking that "you had no problems with 9.04" or lower, unless you actually ran a utility that read the disk's SMART data.  Windows chkdsk doesn't, so it won't tell you anything about what the drive reports as potential problems, which is what SMART does.

SMART is a system the drive manufacturers use to report potential problems, but the interpretation of the data is not standardized.  Each drive handles bad sectors diferently, and Ubuntu is simply reporting the data that the drive is reporting.  If you were to run a different utility to read this, I'm pretty sure you would find the same numbers.

If there is a problem, it is that Ubuntu may be misinterpreting the numbers, and making it sound worse than it really is. 

FWIW, I have two identical drives, although one has been used more than the other.  Ubuntu reported problems with one, and none with the other, so it's hard to imagine that there might be a bug in reading the data.  I also used a different program, and got the same results.

In my case, the number is consistent, so it could be that the sectors got damaged previously, and the drive is OK now.  But if it was getting progressively worse, I would be concerned.

thank you for your reply
in windows , I used HD tune ([http://www.hdtune.com/](http://www.hdtune.com/)) [the normal free release not the pro one] to check my disk.
and HDD Regenerator 1.71 ([http://www.dposoft.net/](http://www.dposoft.net/)) and used the boot feature .. after about 3 hours it gave me a negative (your disk is fine)

the bug reported is concerning the reallocated sector count
[http://launchpadlibrarian.net/32604239/palimpsest-screenshot.png](http://launchpadlibrarian.net/32604239/palimpsest-screenshot.png)

while what I have is current pending sector count
[http://img137.imageshack.us/img137/9719/screenshotsmartdata.png](http://img137.imageshack.us/img137/9719/screenshotsmartdata.png)
and
[http://img708.imageshack.us/img708/1665/screenshotsmartdata1.png](http://img708.imageshack.us/img708/1665/screenshotsmartdata1.png)

so .. am I at risk ?
I already backed up my data .. but should I just get another disk or keep with this till it fails ?

---

### Post by phillw on 2009-12-03
> **JiMMaR said:**
> thank you for your reply
in windows , I used HD tune ([http://www.hdtune.com/](http://www.hdtune.com/)) [the normal free release not the pro one] to check my disk.
and HDD Regenerator 1.71 ([http://www.dposoft.net/](http://www.dposoft.net/)) and used the boot feature .. after about 3 hours it gave me a negative (your disk is fine)

the bug reported is concerning the reallocated sector count
[http://launchpadlibrarian.net/32604239/palimpsest-screenshot.png](http://launchpadlibrarian.net/32604239/palimpsest-screenshot.png)

while what I have is current pending sector count
[http://img137.imageshack.us/img137/9719/screenshotsmartdata.png](http://img137.imageshack.us/img137/9719/screenshotsmartdata.png)
and
[http://img708.imageshack.us/img708/1665/screenshotsmartdata1.png](http://img708.imageshack.us/img708/1665/screenshotsmartdata1.png)

so .. am I at risk ?
I already backed up my data .. but should I just get another disk or keep with this till it fails ?

I've edited my thread, but as stated in the bug-report - get the hard disk utility from your hard-disk manufacturer - they're free. Run them on your disk(s) if you are in any doubt.

Phill.

---

### Post by expatCM on 2009-12-03
> get the hard disk utility from your hard-disk manufacturer - they're free. Run them on your disk(s) if you are in any doubt.

Ah ... that must be a comment directed at Windows users.  Seagate for example seems to have SeaTools for Windows and DOS.  There seems to be a command line utility but you have to register for this .....  and to register for a command line utility ....  no gui ...  but it does support Windows 3.0 ......

Western Digital seem to hide their tools rather well.  Not found them yet.

Are there any gui hdd testing tools for the Linux user?

Has anyone tried the SeaTools running under Wine?

---

### Post by JiMMaR on 2009-12-03
> **phillw said:**
>  get the hard disk utility from your hard-disk manufacturer 


the problem here is , the Samsung Disk Utility tool does not support my disk :(

I have an HM320JI
and it's not in here

[http://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html](http://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html)

some guy reported that it didn't work for him too .. guess I can only cross my fingers wait till it crashes XD

---

### Post by asdff on 2009-12-24
hi, when i trie to install ubuntu 9.10 or test it on my laptop (runs great on my desktop pc) it takes about 5 minutes and then there flashes a text on the screen about some bug, then it goes to desktop and it says that my ata fujitsu mht2060at 60gb disk is failing and contains many bad sectors. After that i tried to solve the problem with windows tools, didnt work and even ran a low level format with fujitsu tool ([fjerase]("http://www.fujitsu.com/us/services/computing/storage/hdd/support/utilities.html")) and it still says the same thing.
The cd check doesnt find any bugs so could there be some bug in 9.10 with my hd.
I would not want to buy new hd if possible because i bought the laptop with 50€. I will try to install ubuntu 8.04 today.
my fujitsu amilo laptop specs
1.4 ghz intel M
502 mb ram
60gb mht2060at
not sure about graphic things or sound things
I had windows xp but i would have formatted  it anyway.

---

### Post by linfidel on 2009-12-24
Don't know if you read any of the other posts, so I may be repeating myself.

If your only problem is the reporting of bad sectors, then installing an older version is not going to do any more than turning off the reporting tool.  If you were to run a similar program in an older version, it would tell you the same thing.  It is only reporting what the drive is telling it.  It may not be interpreting the data correctly, but nothing is forcing you to pay attention to it.

If your problem is that 9.10 doesn't run well, then you are posting in the wrong thread.

---

