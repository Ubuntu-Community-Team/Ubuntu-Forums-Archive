---
title: "What did Ubuntu do to my drives?"
date: 2012-02-14
forum: Hardware
---

### Post by Blasted Remnants on 2012-02-14
Hi guys, I'm new to Ubuntu but having fun with it so far. All the little hiccups along the way have been interesting enough, and I'm enjoying learning my new OS but I ran into something here that I cannot figure out. I've got two hard drives in my computer, with Ubuntu on one and (until yesterday) Windows 7 on the other. Lately though, my Windows installation had started puking out BSoDs like nobody's business, so I decided to wipe that drive and reinstall Windows. That's when I found out that Windows no longer "likes" my hard drives. I can start the install, choose a drive, format it, all of that stuff. But when setup gets to the point where it's done copying files and it begins to extract them, installation fails everytime. I tried it with both drives, and LOTS of different discs. I've got images of all the Windows I've ever owned (cyber-packrat) and I've tried XP, Vista and 7 so far with no success at all. I know that this isn't the place to ask for help with Windows issues, but I'm wondering if maybe Ubuntu somehow could've changed something about my drives. Does that sound like a possibility? I'm really stumped here, Ubuntu reads and writes to both the drives with no problem, and none of the diagnostics I've tried (Hiren's Boot CD) have indicated any problems.

---

### Post by gordintoronto on 2012-02-14
BSODs are often caused by hardware failure. If you run "disk utility" from Ubuntu, and click on a drive, it should display the "smart status" on the right side of the window. You might need to install Disk Utility.

Be cautious, though: Disk Utility is very powerful...

---

### Post by Blasted Remnants on 2012-02-14
> **gordintoronto said:**
> BSODs are often caused by hardware failure. If you run "disk utility" from Ubuntu, and click on a drive, it should display the "smart status" on the right side of the window. You might need to install Disk Utility.

Be cautious, though: Disk Utility is very powerful...

Thanks, I did try a bunch of different disk checking utilities already, but not anything from within Ubuntu. I'm too new to know where to find any of that stuff, lol. I'll check that out and see what comes of it though. Oh wait, do you mean smart as S.M.A.R.T., that hard drive info thing? I have had it disabled for a long time because it slowed my system considerably, or at least my system was faster after disabling it. Does this Disk Utility rely on S.M.A.R.T. info? I'll give it a shot, maybe even re-enable S.M.A.R.T. long enough to run a scan.

---

### Post by savanna on 2012-02-14
You could also try [Darik's Boot And Nuke]("http://www.dban.org/") on the problem hard drive, in case there's anything on the disk that Windows doesn't like. But, *be careful that you choose the correct drive* - once you wiped with DBAN **nothing** can recover the data :-)

---

### Post by haqking on 2012-02-14
if you get a BSOD, look it up to find out what caused it.

[http://technet.microsoft.com/en-us/library/cc750081.aspx](http://technet.microsoft.com/en-us/library/cc750081.aspx)

[http://pcsupport.about.com/od/findbyerrormessage/tp/stop_error_list.htm](http://pcsupport.about.com/od/findbyerrormessage/tp/stop_error_list.htm)

---

### Post by Blasted Remnants on 2012-02-14
> **savanna said:**
> You could also try [Darik's Boot And Nuke]("http://www.dban.org/") on the problem hard drive, in case there's anything on the disk that Windows doesn't like. But, *be careful that you choose the correct drive* - once you wiped with DBAN **nothing** can recover the data :-)

Hi, thanks for the tip. I had forgotten that I do have 6 bad sectors showing on the one drive, but Windows wouldn't install on either of them so I don't know if the bad sectors are the problem. I will try the DBAN next time I format it though, maybe it will make the difference.

---

### Post by Blasted Remnants on 2012-02-14
> **haqking said:**
> if you get a BSOD, look it up to find out what caused it.

[http://technet.microsoft.com/en-us/library/cc750081.aspx](http://technet.microsoft.com/en-us/library/cc750081.aspx)

[http://pcsupport.about.com/od/findbyerrormessage/tp/stop_error_list.htm](http://pcsupport.about.com/od/findbyerrormessage/tp/stop_error_list.htm)

The ones that I was getting were flashing by too quickly to read anything, just a quick flash and then straight into a reboot.

---

### Post by Blasted Remnants on 2012-02-14
> **gordintoronto said:**
> If you run "disk utility"...

Ok I did that and it's showing 6 bad sectors on the one drive, which doesn't seem too bad, does it? Is there any way to partition the drive so that the bad sectors are not being used?

---

### Post by ahallubuntu on 2012-02-14
You have six reallocated sectors - so far.  That means six sectors on your drive failed - so far - and were replaced by spare sectors automatically by the drive firmware.  If that number keeps going up, that drive is toast, because eventually you will run out of spare sectors.  I'm not sure how many that drive has - varies by the drive.  I'd guess 200 or so spares give or take...

Are you sure that's the ONLY S.M.A.R.T. error you have?  What about Pending Sectors?  Those are much worse than reallocated sectors; "pending" sectors are sectors on the disk that could not be read.  Those could definitely cause BSODs.  Seen that several times.  If you have a pending sector in just one Windows system file, it will be unable to use that file and maybe unable to boot.

I would DBAN the drive as suggested above.  That can clear pending sectors (if you have any).  However, I would assume this drive is failing and would not use it for important data.  If you use it, make frequent backups and assume it will fail sooner or later completely.

---

### Post by Blasted Remnants on 2012-02-14
> **ahallubuntu said:**
> You have six reallocated sectors - so far.  That means six sectors on your drive failed - so far - and were replaced by spare sectors automatically by the drive firmware.  If that number keeps going up, that drive is toast, because eventually you will run out of spare sectors.  I'm not sure how many that drive has - varies by the drive.  I'd guess 200 or so spares give or take...

Are you sure that's the ONLY S.M.A.R.T. error you have?  What about Pending Sectors?  Those are much worse than reallocated sectors; "pending" sectors are sectors on the disk that could not be read.  Those could definitely cause BSODs.  Seen that several times.  If you have a pending sector in just one Windows system file, it will be unable to use that file and maybe unable to boot.

I would DBAN the drive as suggested above.  That can clear pending sectors (if you have any).  However, I would assume this drive is failing and would not use it for important data.  If you use it, make frequent backups and assume it will fail sooner or later completely.

Thanks for reading, that's the only S.M.A.R.T. error being reported, nothing else shows up red in Disk Utility. I wasn't sure if 6 bad sectors was a big deal or not though, I figured there'd be millions of sectors available and I could just partition out 20 or 30 gigs around the bad sectors and not use that stuff. I'll do the Boot 'n' Nuke thing shortly and see if that makes any difference. Thanks again!

---

### Post by ahallubuntu on 2012-02-14
Six sectors is a big deal to me.  I would never use that drive for anything important myself, but I would use it for some things.  I have a similar drive (two reallocated sectors) in my home media center, but nothing important is on that drive, so if it fails tomorrow, I throw it away and put in another one.

You may have millions of sectors on a drive but you don't have millions of spares - maybe a few hundred spares.  As I said, keep watching that number; if it goes up over time you need to be very worried.  Spare sectors may also be in a different portion of the drive than the original so using spares can reduce performance, too.

I'd probably DBAN the drive myself (after getting all important data off of it first) then running an Extended S.M.A.R.T. test on it, then see how many reallocated sectors.  Then restore the data and try using it again, if you dare.

---

### Post by Blasted Remnants on 2012-02-14
> **ahallubuntu said:**
> Six sectors is a big deal to me.  I would never use that drive for anything important myself, but I would use it for some things.  I have a similar drive (two reallocated sectors) in my home media center, but nothing important is on that drive, so if it fails tomorrow, I throw it away and put in another one.

You may have millions of sectors on a drive but you don't have millions of spares - maybe a few hundred spares.  As I said, keep watching that number; if it goes up over time you need to be very worried.  Spare sectors may also be in a different portion of the drive than the original so using spares can reduce performance, too.

I'd probably DBAN the drive myself (after getting all important data off of it first) then running an Extended S.M.A.R.T. test on it, then see how many reallocated sectors.  Then restore the data and try using it again, if you dare.

Alright, I'll do exactly that. At least I don't have to go through a lengthy backup process first, as the drive has been recently formatted.  :p

---

### Post by gordintoronto on 2012-02-14
> **Blasted Remnants said:**
> ...Oh wait, do you mean smart as S.M.A.R.T., that hard drive info thing? I have had it disabled for a long time because it slowed my system considerably...

That is a really bad sign all by itself.

---

### Post by dFlyer on 2012-02-14
If you have bad sectors replace your hard drive so you don't loose any data. Your drive is starting to fail. It's not ubuntu fault, nor is it windows fault. It's just something that happens with time.

---

### Post by Blasted Remnants on 2012-02-14
> **dFlyer said:**
> If you have bad sectors replace your hard drive so you don't loose any data. Your drive is starting to fail. It's not ubuntu fault, nor is it windows fault. It's just something that happens with time.

There's nothing on it right now, so no worries that way. I'm mostly just stumped on why Windows will no longer install on EITHER of my drives, when only one of the drives has bad sectors. I just thought that maybe Ubuntu had changed some mysterious setting on the drives that had accidentally made them unusable to Windows.

[EDIT] I meant to add that up until a week or two ago, both of these drives were being used for Windows 7.

---

### Post by ahallubuntu on 2012-02-14
S.M.A.R.T. is reliable as a positive indicator - that means, if S.M.A.R.T. says there is a problem, there probably is.

But it's not reliable as a NEGATIVE indicator.  That is, just because no S.M.A.R.T. problem shows up doesn't mean there IS no problem.  Google for one has done studies showing that S.M.A.R.T. is not a reliable predictor of pending drive failure.

S.M.A.R.T. has indicated there has been SOME problem with your drive: six failed sectors that were re-allocated already.  So you know something bad has been happening to it.

Did you run a S.M.A.R.T. test?  Try running the extended test.  (I would personally DBAN it first.)  If it fails the extended test (which can take an hour or two to finish), then I'd dump the drive.

---

### Post by PeterMoss on 2012-03-15
For what it is worth, I as a complete newcomer to Ubuntu and Linux, have a very similar problem.  

A friend of mine, who was a Linux master, died recently and his wife asked me to rescue his PC data from a mix of computers, some Windows, some Linux ones.  Essentially I extracted the disks from them all and loaded them into a Windows machine.  Of course, some wouldn't read, so I took one of the PCs and with some guidance from a Linux-aware friend, converted a Dell PC to a Ubuntu machine.  Works beautifully.  I extracted the data from all the drives. along the way discovering the joys of EXT3, root privileges and lots of other things.  I backed up the data and thought that as I'd enjoyed playing with Ubuntu I'd convert the Dell PC (which is only a couple of years old) to a machine running both Windows and Ubuntu (my plan is to choose which to boot into on power-up rather than run Ubuntu through Windows).

So I re-formatted a couple of drives to NTFS format, removed the Ubuntu boot drive, replaced it with the reformatted ones, loaded in the Windows bootup disk (XP Pro) and after going through the loading of files, presented the BSOD together with news that my disk was corrupted, as the original poster found.  I've tried it with 3 hard drives in total; all give the same result.

I reloaded the Ubuntu boot hard drive and the PC boots up nicely; Running checks on the 3 suspect drives using disk utility declares them OK.  So I shall try the extended tests.  Any further advice gratefully received.

---

### Post by gordintoronto on 2012-03-15
PeterMoss: your problem isn't at all similar. You would have been better off to start a new message thread.

I can't figure out what you were trying to say with, "loaded in the Windows bootup disk (XP Pro) and after going through the loading of files, presented the BSOD together with news that my disk was corrupted..."

"I reloaded the Ubuntu boot hard drive and the PC boots up nicely; Running checks on the 3 suspect drives using disk utility declares them OK." I would like to help you, but it doesn't sound like you have a problem.

If, in Ubuntu, you install Gparted, then from Accessories/Terminal type in this command: sudo gparted, there is a drop-down list in the top-right of the screen to select a hard drive. It will display how the drive is formatted. If it's EXT2 (or 3 or 4) Windows XP can't deal with it without installing a special driver. But I have no idea if this is actually relevant to your situation.

---

### Post by PeterMoss on 2012-03-17
Thanks for the reply, GordinToronto.

My justification for posting in this topic is this from the OP:[INDENT][COLOR=Blue]"that's when I found out that Windows no longer "likes" my hard drives. I  can start the install, choose a drive, format it, all of that stuff. But  when setup gets to the point where it's done copying files and it  begins to extract them, installation fails everytime. I tried it with  both drives, and LOTS of different discs."
[/COLOR][/INDENT]That's what is happening to my PC.

To be fair, this might be a Windows problem, but seeing this topic on here prompted me to post.

Since my post I have tried various disks, first formatting them as NTFS format.  I have tried doing this from my Ubunto PC (using Gparted as you suggested)  and from my Windows PC; no luck in either case.

I have checked all disks using both Windowws chkdsk, the Windows XP disk checker, and Ubuntu's Disk Utility.  All three agree that I have no bad sectors.

So I'm puzzled.  Is there a problem formatting to NTFS before loading my WIndows boot-up disk?  

Suggestions gratefully received.

---

### Post by gordintoronto on 2012-03-17
> **PeterMoss said:**
> Since my post I have tried various disks, first formatting them as NTFS format.  I have tried doing this from my Ubunto PC (using Gparted as you suggested)  and from my Windows PC; no luck in either case.

Could you expand on "no luck," please? "I got the part where it said .... and such-and-such happened."

During the install, my preference is to blow away any partitions, and create three: a root partition (/) of perhaps 20 GB formatted as EXT3, a swap partition a bit larger than memory, and a Home partition (/home) also formatted as EXT3. The root partition doesn't really need to be that large, but if it gets full, it's quite traumatic.

Some people prefer EXT4.

---

### Post by BertN45 on 2012-03-18
> **ahallubuntu said:**
> S.M.A.R.T. is reliable as a positive indicator - that means, if S.M.A.R.T. says there is a problem, there probably is.

But it's not reliable as a NEGATIVE indicator.  That is, just because no S.M.A.R.T. problem shows up doesn't mean there IS no problem.  Google for one has done studies showing that S.M.A.R.T. is not a reliable predictor of pending drive failure.

S.M.A.R.T. has indicated there has been SOME problem with your drive: six failed sectors that were re-allocated already.  So you know something bad has been happening to it.

Did you run a S.M.A.R.T. test?  Try running the extended test.  (I would personally DBAN it first.)  If it fails the extended test (which can take an hour or two to finish), then I'd dump the drive.

Agree. In my laptop I have a disk with some bad sectors for years now and if it does not increase fast there is nothing to worry about. It can be a combination of many factors like an aging drive and some small glitches in the magnetic layer. If you disk is dying because of a head crash, the number a bad sectors should double each couple of days. Probably you have a mechanical problem, e.g. seek errors. 
Run the extended test and performance benchmarks using disk utility.
The performance benchmark takes a few minutes and maximizes the load on the drive.

---

### Post by PeterMoss on 2012-03-20
Thanks for the suggestions.  I have found the solution - or at least, I have worked around the problem - , which was that the Dell was setup for AHCI and was not recognising my drives.  When I selected (pre-bootup) ATA, it worked fine.  I've now reloaded Windows, and have re-installed Ubuntu so now have what I wanted, a dual boot machine.

Interesting that the Ubuntu setup had no problems with the hard drives, but Windows did.   Windows of course can't find any ethernet card, yet Ubuntu again has no problems.  And sound - Windows can't work out what on earth I'm trying to do, yet Ubuntu just gets on with it.  But none of this will be news to you long-term Linux fans, I'm sure.  Maybe I'll join you

---

