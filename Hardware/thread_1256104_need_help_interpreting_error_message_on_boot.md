---
title: "need help interpreting error message on boot"
date: 2009-09-02
forum: Hardware
---

### Post by Smiley Coyote on 2009-09-02
I am using an alternate computer to try and solve this problem.  Recently I switched out a DVD-RW for a new one, a dual layer burner, and now have problems getting Ubuntu to load.  I also recently moved and am hoping I did not simply jar something loose.  Also, I wonder if I may not have the settings re: master and slave set up properly or if this error has to do with my drives at all.

It goes fine and through the loading bar as if it is going to boot, takes an extraordinary amount of time to do so, then doesn't and reads the following:

Boot from (hd0,0) ext 3 bf54219e-7486

Okay, now I realize it is still scrolling a bit and I have lost the beginning of that error message.  I can't type that fast!

I am getting something referring to a missing modules 1s/ dev..

I know this is not a lot to go on but I have precious little to offer.  Is there something to look for regarding the drives?

I do believe everything is plugged in tightly.

Help!  I can't use my computer at all and have been without for two weeks now!

---

### Post by Smiley Coyote on 2009-09-02
Still lost here: my original post was an attempt to copy into it what was displayed on my screen but during that attempt I found that in waiting longer than I had in previous attempts to boot it started to scroll and I couldn't keep up. 

I should have added the following information:

I attempted to upgrade to Ubuntu Studio (not the new version) and did not have an internet connection when I did so so I did not get to download certain files it wanted to.  As well, I cannot boot from the original Ibex CD in order even to reformat.

Little help?

---

### Post by Smiley Coyote on 2009-09-02
Also shows this:

"Gave up waiting for root device"

then there is an error trying to read it at the normal screen resolution, then another error shows as it tries a lower resolution, then the overall failure. 

then the list of suggestions like "did it wait long enough" and missing modules

This also turns up:

alert /dev/disk/by-uuid/bf642119e-7486-a7ce-4b21b65c7bea does not exist

dropping to a shell

This motherboard has way above average built in graphics. Everything seemed fine until I tried to install Ubuntu Studio AND the move to my new home. I hope something did not jar loose.

I wonder if there is some problem now with the monitor. Could that feed back into the boot as an error?

---

### Post by misterfixit on 2009-09-03
It appears that your boot loader is not locating the boot part of Linux.  However, if you believe that this may be due to your recent move (and I've knocked things loose a couple of times like that too) open your case and make sure all connectors are seated, this includes the power connector from the power supply to the MoBo; if you have one of the segmented power connectors it is pssible for the smaller side to come loose slightly.  After jiggling everything, go back and start the machine again; open yur BiOS (delete or F10 or something like that) and look at the boot sequence and look at what comes up listed as devices.  If you don't see the drive that is supposed to be there you could have one or more of several problems -- the worst of which could be a failed HD.

Reboot the machine again if you see the HD's and when the messages start to scroll upward, hit "Control S" to stop the scroll and "Control Q" to restart the scroll.  I am hoping that your system will recognize those olden days DOS commands.

Get back to us here with information and we can try to continue to sort out your issues.

HTH, YMMV, LSMFT

Dave

---

### Post by earthpigg on 2009-09-03
have you consulted your new optical drive's documentation to see if any jumpers need to be set?

or resetting your system BIOS, so it doesn't go crazy trying to find an optical drive that is no longer there?

have you tried booting from a LiveCD and/or LiveUSB (just to see if it works, including the new optical drive) to either rule out or verify hardware failure?

have you considered super grub disk to restore your bootloader? [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Smiley Coyote on 2009-09-04
> **misterfixit said:**
> It appears that your boot loader is not locating the boot part of Linux.  However, if you believe that this may be due to your recent move (and I've knocked things loose a couple of times like that too) open your case and make sure all connectors are seated, this includes the power connector from the power supply to the MoBo; if you have one of the segmented power connectors it is pssible for the smaller side to come loose slightly.  After jiggling everything, go back and start the machine again; open yur BiOS (delete or F10 or something like that) and look at the boot sequence and look at what comes up listed as devices.  If you don't see the drive that is supposed to be there you could have one or more of several problems -- the worst of which could be a failed HD.

Reboot the machine again if you see the HD's and when the messages start to scroll upward, hit "Control S" to stop the scroll and "Control Q" to restart the scroll.  I am hoping that your system will recognize those olden days DOS commands.

Get back to us here with information and we can try to continue to sort out your issues.

HTH, YMMV, LSMFT

Dave

Okay, viewing the boot sequence gives me the following:

First Boot Device: Hard Disk
Second Boot Device: CDROM
Third Boot Device: CDROM
Boot Other Device: Enabled

Swap Floppy Drive: Disabled
Boot Up Floppy Seek: Disabled

This seems strange as the newly inserted drive is a dual layer DVD-RW.

Stopping the scroll has not worked but I recently heard a story from someone else, who uses Windows, that they had a similar problem when putting in a new DVD-RW.  The lost the boot sector and he says he removed the new one and booted it without the device plugged in and it found it again and then he put it back in and everything was okay.

I have no idea if he is worth his wait in salt or not.  I believe I have posted everything that comes up but if you need an exact copy of everything displayed, in the order it comes up, let me know and I will post it.  After it resorts to (Intramfs) where it seems to be awaiting commands, though none are entered, it continues to scroll giving me long series of numbers that I cannot decipher.

---

### Post by Smiley Coyote on 2009-09-04
> **earthpigg said:**
> have you consulted your new optical drive's documentation to see if any jumpers need to be set?

or resetting your system BIOS, so it doesn't go crazy trying to find an optical drive that is no longer there?

have you tried booting from a LiveCD and/or LiveUSB (just to see if it works, including the new optical drive) to either rule out or verify hardware failure?

have you considered super grub disk to restore your bootloader? [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

The DVD-RW is not from a retailer but looks brand new and I was assured it was fine.  It was still in its packing but no paperwork.  I could look it up online.  I DID have misgivings about using a Memorex product.

I HAVE tried booting from a disk that has worked fine in the past and get a similar error anyway, even when not trying to install but just run from the disk.  I used ANOTHER one, Ubuntu Studio, and had the same problem.

I will try booting from the new drive to possibly eliminate one potential issue and I will check out the website you provided.  Unfortunately, I am barely wrapping my brain around most this being a relative noob.

---

### Post by Yellow Pasque on 2009-09-04
> This seems strange as the newly inserted drive is a dual layer DVD-RW.
This is normal. The BIOS will just see it as a standard CD-ROM, because that's all the BIOS needs to know.

Is the new drive a PATA or SATA device? If you have PATA devices, how are they connected/configured?

---

### Post by misterfixit on 2009-09-04
> **Smiley Coyote said:**
> The DVD-RW is not from a retailer but looks brand new and I was assured it was fine.  It was still in its packing but no paperwork.  I could look it up online.  I DID have misgivings about using a Memorex product.

I HAVE tried booting from a disk that has worked fine in the past and get a similar error anyway, even when not trying to install but just run from the disk.  I used ANOTHER one, Ubuntu Studio, and had the same problem.

I will try booting from the new drive to possibly eliminate one potential issue and I will check out the website you provided.  Unfortunately, I am barely wrapping my brain around most this being a relative noob.



OK, I understand.  Careful about wrapping your brain around anything .. you end up with a migraine :-)

I really think this is an issue which involves both BiOS and your boot loader.  I'm sorry I can't be more specific, but if your BIOS is properly configured to have the HD with your boot section as the first device it looks for and boots from, then the rest of the system will follow when the HD boots and GRUB or LILO begins the process of bringing  up Ubuntu.  Your "error message" stating that the system is looking for something other than the boot HD means that your boot loader is not set up properly -- assuming that the BiOS is telling the system that your HD is the first drive present and the one from which to boot.

Really, it doesn't matter if the CDROM is a Memorex or some Brand-X they all have hard coding which talks to the BIOS and then the BIOS tells the system what's there and what it is supposed to be doing.

I would begin again by eliminating potential problems.

With the case open, dis connect all drives except for the HD which has your Ubuntu install on it.  Go through a complete boot cycle and see if that is OK.  That will eliminate any possible glitches with the Ubuntu install.  Again, go through the entire boot process up to when Ubuntu come up alive.

Then shut down the system and plug each device in one at a time, going through the identical process over again.

I would leave the problematic CDROM until last.  Start with the punched paper tape drive, cassette tape drive, the 8" Floppy, then the 5.25" floppy, then the 3.5" floppy,  .. oh sorry .. Old School ... never mind that humor.

Sounds like you have a relatively simple system with an HD and a CDROM (your DVD hootchie).  If when you get to the CDROM and there is a fault in booting -- i.e. the system doesn't find your boot sector on the HD, then you have isolated the problem.  We can go on from there.

HTH, YMMV, LSMFT

Dave

---

### Post by Smiley Coyote on 2009-09-05
> **Temüjin said:**
> Is the new drive a PATA or SATA device? If you have PATA devices, how are they connected/configured?

I have no idea.  I do not know how to configure a device.

---

### Post by Smiley Coyote on 2009-09-05
Okay, let me know if skipping a step or two could pose potential problems but all I did to start eliminating was remove the new drive and attempt to boot and there was no problem.  It booted up very nicely.  Now, there are settings on the back of the drive that need to be dealt with, correct?  Like setting them to master and slave respectively?

I don't know if the CD-R is set as master or not as I was not the one that put it together initially.  Should I take all that out and take a look?

I am getting ahead of myself, I have the feeling I am going to hear.  Anything you have on this would be much appreciated.  I would dearly love to have the ability to burn DVDs again.

Thanx!!!

---

### Post by misterfixit on 2009-09-06
> **Smiley Coyote said:**
> Okay, let me know if skipping a step or two could pose potential problems but all I did to start eliminating was remove the new drive and attempt to boot and there was no problem.  It booted up very nicely.  Now, there are settings on the back of the drive that need to be dealt with, correct?  Like setting them to master and slave respectively?

I don't know if the CD-R is set as master or not as I was not the one that put it together initially.  Should I take all that out and take a look?

I am getting ahead of myself, I have the feeling I am going to hear.  Anything you have on this would be much appreciated.  I would dearly love to have the ability to burn DVDs again.

Thanx!!!


OK, you have solved most of the problem.  Everything else is working, it is now known that the CDROM is the problem.

Examine the rear of the CDROM where there is a set of jumpers (tiny rectangular plastic plugs which are placed upon tiny metal prongs).  There should be a diagram next to the "jumpers" which indicate master, slave or cable select.

If the CDROM is connected to the Mother Board (MoBo) by a flat ribbon cable, determine which jack the ribbon cable is plugged into on the MoBo.

If the ribbon cable is the same cable which connects the HD, set the jumper to "slave".

If the ribbon cable is a separate cable connecting the CDROM, make sure that it is plugged into the IDE2 jack.  Make sure that the CDROM Jumpers are set to "Master".

Try re-booting and see what happens.

HOWEVER:  If the HD and the CDROM are connected to the SATA port -- and you will know this is the cable is a thin single cable with a small plastic connector on each end, all you have to do is make sure the CDROM jumper is set to "cable select".

Verify that the jumper on the CDROM is set properly and reboot.

Come back here and let us know what is what.

HTH, YMMV.

Dave

---

### Post by Smiley Coyote on 2009-09-06
Okay, now I have another problem: I expected to find a switch I could move back and forth between master and slave and instead I find the three sets of prongs, as you said, and ONE green piece that is sitting fixed to the two prongs that say master.  Am I supposed to remove this and place it over the appropriate pair?

---

### Post by misterfixit on 2009-09-06
> **Smiley Coyote said:**
> Okay, now I have another problem: I expected to find a switch I could move back and forth between master and slave and instead I find the three sets of prongs, as you said, and ONE green piece that is sitting fixed to the two prongs that say master.  Am I supposed to remove this and place it over the appropriate pair?

Prongs and green plastic piece was what I was describing.  The setting appears to be "master" for your CDROM drive.  This is OK if you are using the flat ribbon cables to connect your HD and CDROM and the flat ribbon cable for the CDROM is plugged into the second IDE socket on the MoBo.  

However, if the HD and the CDROM are using one ribbon cable then the CDROM green plastic piece should be moved to the slave position.  It is best practice to use a strong tweezer or a hemostat/roach holder to grasp and move the green piece.   They are difficult to remove.  If you have long and stong fingernails, that would work too IMHO.

HTH, YMMV, GL, LSMFT

Dave

---

### Post by Smiley Coyote on 2009-09-06
Then it is as I feared.  The HD is on a separate ribbon connector and they plug into two side by side spots.  Neither of these is labeled but the HD goes into a blue one and the other into a yellow one.

If that is correct, and this is the one it has always been plugged into with the CD-RW that I have and the DVD-RW that WAS in there, then knowing it has been on master the whole time is discouraging.  It means everything was set up properly to begin with.

To be clear, is there supposed to be a connector where the master/slave/cable prongs are?

---

### Post by Smiley Coyote on 2009-09-06
Now, if the CD-RW was not properly set (and I have not removed that to check) then I would not be able to use it properly, correct?

---

### Post by misterfixit on 2009-09-06
> **Smiley Coyote said:**
> Then it is as I feared.  The HD is on a separate ribbon connector and they plug into two side by side spots.  Neither of these is labeled but the HD goes into a blue one and the other into a yellow one.

If that is correct, and this is the one it has always been plugged into with the CD-RW that I have and the DVD-RW that WAS in there, then knowing it has been on master the whole time is discouraging.  It means everything was set up properly to begin with.

To be clear, is there supposed to be a connector where the master/slave/cable prongs are?

It appears to me that you have eliminated a lot of questions and have ascertained that all the cables and the master/slave plugs are correct.  The CDROM/DVD device appears to be the problem.  Believe me when I tell you that having that information is important to your quest for Perfect harmony.  It is all about detective work and eliminating the suspects and finding the guilty party.

Can you remove the CDROM and try it out in another machine?  That would verify that the CDROM device is either working properly or not.  If not, then it must be exchanged for one which does work.  If it works, then the issue is specific to your existing system and the way it is "seeing" the DVD device.

Resolve the issue of whether the CDROM/DVD device is working properly and then we can proceed from that point.

YMMV, HTH, LSMFT, ETC

Dave

---

### Post by Smiley Coyote on 2009-09-06
I want to be clear first on something: must both drives be set to slave?

---

### Post by misterfixit on 2009-09-06
> **Smiley Coyote said:**
> I want to be clear first on something: must both drives be set to slave?

No .. set your BOTH Hard Drive to Master and your DVD-CDROM to Master

 .. the reason you are doing this like that is because they are using different IDE ribbon cables.  If they were using the same cable the HD would be Master and the DVD would be slave.

I'll be off the net for the next few hours .. 0944 local time here .... we are on the way to church and will return about 1pm local

---

### Post by Smiley Coyote on 2009-09-06
> **misterfixit said:**
> No .. set your BOTH Hard Drive to Master and your DVD-CDROM to Master

What I am trying to find out here is if the DVD-RW and the CD-RW should both be set to master.  As of now there are two rewritables on the same ribbon that are set to master.

---

### Post by Yellow Pasque on 2009-09-06
[http://en.wikipedia.org/wiki/Parallel_ATA#Multiple_devices_on_a_cable](http://en.wikipedia.org/wiki/Parallel_ATA#Multiple_devices_on_a_cable)

The device on the end of the cable should be 'master' and the device in the middle should be 'slave'

---

### Post by Smiley Coyote on 2009-09-06
Okay...apparently I did not make my situation clear enough from the onset.  I have set the CD-RW to slave and all is now well.  Should I have any more problems with the same type of error or with this particular drive that I feel could be related to what we have gone through then I will post it here.

Thank you for all of your time.  It has been a learning experience and I am certainly better equipped to deal with some of these issues now!

---

### Post by Smiley Coyote on 2009-09-06
> **Temüjin said:**
> [http://en.wikipedia.org/wiki/Parallel_ATA#Multiple_devices_on_a_cable](http://en.wikipedia.org/wiki/Parallel_ATA#Multiple_devices_on_a_cable)

The device on the end of the cable should be 'master' and the device in the middle should be 'slave'

Thank you.

---

### Post by misterfixit on 2009-09-06
> **Smiley Coyote said:**
> What I am trying to find out here is if the DVD-RW and the CD-RW should both be set to master.  As of now there are two rewritables on the same ribbon that are set to master.

OK, I am officially confused.  Do you have one or two optical disk drives????  I say "optical disk drive" since you might have a CDROM AND a DVD .. as in TWO drives . is that correct -- you have TWO optical drives???

If you have TWO optical drives, put one on the cable with the Hard Drive and set the plug for "slave"; put the other on the second ribbon cable and place the plug in the "master" position.

Your settings will look like this IF you have two optical drives:

Hard Drive set to Master and on the first IDE cable

CDROM drive set to Slave and on the first IDE cable

DVD  on set to Master and on the second IDE cable.

---

