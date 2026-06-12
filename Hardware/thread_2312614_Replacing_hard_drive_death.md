---
title: "Replacing hard drive death"
date: 2016-02-05
forum: Hardware
---

### Post by dan205 on 2016-02-05
I had Ubuntu 14 installed on my old laptop recently. But suddenly the hard drive died. It failed to boot. Message was that no operating system could be found. 
So I assume that the hard drive did die suddenly. This, by the way, was not a dual boot installation with another OS. This was a dedicated ubuntu OS machine. 

I bought a new(ish) hard drive to replace it, but I am curious, since this is totally clean drive it will have no drivers for any hardware on my laptop ( which is about 5 or 6 years old). 

That means that I have to try and find all the drivers online somewhere first before I can re-install ubuntu, right?

I do still have the the USB stick I used to run ubuntu  from which I also used, ultimately, to install ubuntu on my hard drive. Will that have the required drivers installed or not? Yeah, I'm a bit lost here :)

What can I do to get my laptop running again with the new hard drive and ubuntu installation?

---

### Post by Bashing-om on 2016-02-05
dan205; OuWeeel
That :
> 
Message was that no operating system could be found. 

Could have been a result of several reasons - maybe nothing more than a bit of corruption in the boot config files (???)....
A) run a file system check from the liveDVD
B) Run a SMART test on the health of the hard drive.

Now as to your concern:
> 
That means that I have to try and find all the drivers online somewhere first before I can re-install ubuntu, right?

nope. as before on your 1st install, the kernel has the majority of drivers OR our software repository also has a vast amount of proprietary drivers. I do not expect with the older hardware here to be any need for an outside source.

> 
What can I do to get my laptop running again with the new hard drive and ubuntu installation?
- bk -
I do still have the the USB stick I used to run ubuntu from which I also used, ultimately, to install ubuntu on my hard drive.

We are talking release 14.04 as this install medium, yes ? Then just as before .. boot the liveUSB to a terminal and check that the new hard drive is indeed seen by the system as 'sda' :
back on the desktop, choose "install ubuntu" IF you are content with a standard install that the wizard will set up for you; point the installer to the device fdisk indicated as the hard drive .. and have at it . All there is to it IF the wizard does it for you all you have to do is tell the system the personal info and  confirm the keyboard .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by weatherman2 on 2016-02-05
You may not recall, but when you originally installed Ubuntu, most if not all of the drivers were already included for you from the installation disk (the USB stick in your case).  It's unusual to need to download and install your own drivers afterward - and even then, Ubuntu has an "additional drivers" feature to search for proprietary (not open source) drivers for some hardware, so you don't have to search far for those drivers (typically for video cards and wireless cards). It's very rare that you'd need to install other drivers in a different way - maybe if you have very new hardware (not yet supported by Ubuntu) or some strange device that isn't well supported in Linux for some reason.

I've installed Ubuntu dozens of times, and most of the time, I didn't need to install any other drivers, not even "Additional drivers."  They were all included automatically.

Hard drives by the way fail routinely, sometimes when they aren't even very old.  Sometimes they last for years or decades.  You didn't complain about losing data, but it's still best to make regular backups of your data to avoid losing files after a hard drive crash.  I also monitor S.M.A.R.T. to check for potential problems - S.M.A.R.T. is kind of an early-warning system built into the hard drive itself, to monitor and test for certain problems.

---

### Post by dan205 on 2016-02-05
Thank you so much for the great advice! Sounds like there might be a chance to bring the old drive back to life, and if not, well I can at least get it all up and running again on the new drive without too much hassle. Will let you know the outcome.

---

### Post by weatherman2 on 2016-02-05
I would check the S.M.A.R.T. health of the old hard drive before attempting to use it again.  It could be there is nothing mechanically or electrically wrong with it, just a corruption - or it could be the drive's surface has started to fail and it already has hundreds or even more bad sectors, in which case it would be a waste of time to try to use it again.  (But if you had files on it that you needed, you might be able to get them off if you are lucky.)

I use GSmartControl to check hard drive S.M.A.R.T. health.  It gives you a list of Attributes (several including how many bad sectors if any) and lets you run short and long hard drive tests.  GSmartControl isn't installed in Ubuntu by default.  On a live USB boot, you can install GSmartControl by enabling the "universe" repository in Ubuntu Software center first.  There are online tutorials to help you understand how to use GSmartControl.  I consider it an essential tool after checking many hard drives with it and replacing a few after running it.

---

### Post by dan205 on 2016-02-05
Correction. I just restarted the laptop with the old hard drive still installed. The original error message was actually, "no hard drive detected". I'm running a check on it anyway. It's currently going through the Pre-Boot System Assessment ( I did request it to continue testing even though it detected no hard drive). 

I'll check out GSmartControl when ready.

---

### Post by dan205 on 2016-02-05
I ran the disk check through Ubuntu. It discovered an error in 1 file. It didn't tell me what file that was. I assume it's the hard drive. I'll try the new hard drive. 

Will report back result.

---

### Post by Bashing-om on 2016-02-05
dan205; Welp;

> 
I ran the disk check through Ubuntu. It discovered an error in 1 file. It didn't tell me what file that was.

Did you run the disk check such that the utility will fix the error ? Is further investigation warranted to effect a repair ?
IF you post the results we can give better advise .

What does the SMART reveal about the health of the hard drive ?

When you attempt to boot with the old hard drive what happens ? Maybe all we need to do is re-install the boot code ??

From the liveDVD(USB) can you mount the old drive's partitions and see the files ?

[INDENT][INDENT]haste makes waste
[/INDENT][/INDENT]

---

### Post by dan205 on 2016-02-05
I couldn't run checkdisk because there is no hard disk identifiable.  The same result when I install GSmartControl on my usb stick. It couldn't detect the hard disk. Dead as a rock hard desk, I can only conclude.  

I have since installed the new hard drive. The Ubuntu disk check at the boot up menu also detected an error in 1 file. ??? Anyway, I proceeded with GSmartControl. It did detect the new hard drive. I'm running ExtendedSelfTest on the hard drive with GSmartControl. Awaiting a good result. The Quick Test reported no errors.

---

### Post by dan205 on 2016-02-05
All good. New hard drive works. Ubuntu installed on hard drive. Problem solved. Thanks for your help!

---

### Post by Bashing-om on 2016-02-08
dan205; Goodeal !

> **dan205 said:**
> All good. New hard drive works. Ubuntu installed on hard drive. Problem solved. Thanks for your help!

We can conclude that the old hard drive had given up the ghost.

It is great you are up and running, IF this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT][INDENT]up up and away
[/INDENT][/INDENT][/INDENT]

---

