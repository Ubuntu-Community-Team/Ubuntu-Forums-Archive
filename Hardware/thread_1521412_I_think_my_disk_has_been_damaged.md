---
title: "I think my disk has been damaged?"
date: 2010-06-30
forum: Hardware
---

### Post by Nesaskewatch on 2010-06-30
Hi there!  I have a toshiba L500-00U laptop with windows 7 and 10.04 64 bit installed.  10.04 has separate /, /home and swap partitions.  

Earlier, I was waiting for the disk to spin up after opening the lid (It was in standby) when a large cast iron pan fell from the shelf above me!  It hit right on the mousepad.  The system froze, and I was only able to shut it down by holding the power button down for 5 secs.  It will not boot now.  It doesn't even get to grub.  The laptop *appears* fine...  Not even a scratch.  I removed and looked at the pins on the HDD and they look fine.  The ram tests out good from the live dvd.  The drive light flicks on and off and it doesn't make any unusual noises.  I can boot up with the live dvd and mount the linux volumes.  Some of the files have an X over them now.  I haven't tried to open those.

I am thinking the disk has been damaged somehow by the impact...  (duh)  I was wondering if there is a way of getting it to boot again?  I tried the "recover broken system" but ended up in a shell in my root partition with no idea what to do next!  Is there some way of repairing the broken files?  Or move them to an undamaged area on the disk?

Thanks for any help you can give me.  I wish the darned pan had hit my head!  I can afford to do without *that*...

---

### Post by Nesaskewatch on 2010-06-30
It's funny, but it seems to be slowly recovering some functions.  Kinda like a concussion.  I am running disk utility, and it is showing a bunch of bad sectors, but also seems to be moving things to good sectors!  I haven't done much of anything!  Like I said, just like after a bad knock to the head.  It's regaining consciousness!

Too cool.

---

### Post by Nesaskewatch on 2010-06-30
Well, it seems to be stuck.  On boot, it only gets to a point where it says; PXE-E61  Media test failure.  Check cable.  It also listed another but I missed it.  Next is init: Failed to spawn hostname process.  Input/output error.  Now it's just stuck there.  The drive seems to be busy doing something though...  Still no sign of grub.

Is there some way of running something from the live dvd that can repair/rewrite/relocate files in damaged areas?  How can I determine if the disk is hooped?  

Disk utility said "Re-allocated sector count"  

Normalized  100
Worst       100
Threshold   24

655376 bad sectors

There is another section lower down called "Current pending sector count" that was also in red font that I forgot to get the numbers from, but it seems to be trying to do something while it sits there...
I am on my other laptop right now, and can make changes should anyone care to dive in with some suggestions?

I am at your service.

Cheers!

---

### Post by Nesaskewatch on 2010-07-01
Just a little update on my blind progress.  I entered this into terminal;
```
sudo fsck -t ext4 -y dev/sda5
```

fsck would not work yesterday, no matter what I did.  Today things seem to be a bit better?  I discovered the code above for automating what is proving to be an hours long process.  fsck returned "Error reading block xxxxxxx (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.    Ignore error? <y>"  When y selected; "Force rewrite? <y>"  Again when y selected it runs until hitting the next error.  That code automated the process.

My questions now are: Am I doing the right thing?  It has been working through a huge amount of errors and is still going after 6 hours!  Am I correct in assuming that with that command, fsck will fix the damaged blocks, ultimately leading to a functioning filesystem?  If I am left with continuing errors, does that mean I have a physically damaged disk that should be replaced?  Am I talking to myself again, or is someone going to have sympathy for a fellow weary traveler and offer some hints?  ;)

Cheers!

---

### Post by paulisdead on 2010-07-01
If you've got that many bad sectors, the drive's definitely not worth keeping.  In fact some of the other temporary problems you've run into are consistent with a bad drive.  Use a live cd or something to copy what you can off of it, and get the drive replaced.  You need to get whatever data you can off of there.  Stop doing file system checks, since the more you use the drive, the worse it's going to make it.  If you don't say anything about the frying pan, and only tell them "hey it just started doing this." you should be able to get an RMA if it's in warranty.  If it's the one that came with the laptop, check the laptop manufacturer, if it's one you bought and installed yourself, check the drive manufacturer's website for an rma.

If you're unable to copy what you want off with normal means, you can attempt to image the entire drive or partition with dd_rescue, and then work on the image by mounting it.  Try to minimize any utilization of the drive, since it can make things worse.

---

### Post by Nesaskewatch on 2010-07-02
Thanks for the reply.  I shut it down yesterday after reading your post.  I will be picking up a new one later today.  They're fairly cheap, and I need one fast, so I'll just buy one.  I won't be using the laptop for recipes again while cooking, that's for sure.  At least, not as long as the wife keeps the pans hanging above my head!  I'll use this old laptop as a transfer box for the files on the injured drive, then totally smash the wounded beast into tiny pieces.  

Any suggestions for a replacement?  I guess WD ain't what it used to be, and Seagate looks simply too cheap.  I'm going 7200 rpm with the new one, and I might as well go with a decent drive.  I guess where it is made makes a diff as well?  Who gives honest reviews of this stuff these days?

Cheers, and thanks again.

---

### Post by paulisdead on 2010-07-02
The reviews of that seagate hybrid hdd/ssd have been really positive, and showing it can keep up with a 10k RPM raptor drive in most benchmarks, plus it's 2.5" form factor, so it can go into a laptop.  The other seagate momentus drives will probably be the next best choice for performance, since they're still 7200RPM drives.  I don't know if it's just that tons of Toshiba drives are used by OEMs, but it seems like out of all notebook drives, I see far more of theirs dead than any other 2.5" drives.

I've been kind of disappointed with the failure rates from all the drive manufacturers lately, but I've stuck with seagate and western digital, since they've never given me trouble with RMAs before.  Then again, I have a business account with seagate, and they don't any ask questions when you rma something through a business account with them.  I think for normal users you just need a seatools or wd diagnostics error code to get an RAM from either of them, so long as it's in warranty.

I've always trusted anandtech's reviews, if you want a good review site.  Phoronix does some great Linux specific reviews as well, but they don't get as much hardware to review.

---

### Post by Nesaskewatch on 2010-07-10
> **paulisdead said:**
> I see far more of theirs dead than any other 2.5" drives.

Ain't that the truth!  The old drive (Fujitsu.  You know, they make steak knives too ;)) didn't die from any sort of inherent defect; rather, it was put to death by a frying pan!  It was rather noisy though, and I am told that usually is an indication of things to come?  I purchased a 500 gig Hitachi from a local discounter here in .ca.  Price was great ($70) and it spins nice and quiet.  8 meg cache @5400 rpm though...  I might have preferred a 7200 rpm with a bigger cache, but this laptop probably wouldn't be much faster with a better drive anyway.  It's a *decent* low cost system.  I plan to shop for a speed monkey fairly soon, and Anandtech, along with DSLReports will be my go to guys for reviews.  I'll poke around Phoronix as well being as you mention it.  I don't really have a preference, but proprietary has always been good to me.  My budget will be around 2-3 grand, so I will shop around a fair bit.

Thanks again for the help!

---

### Post by rogerdg on 2010-07-10
I agree that the drive is dying.  As for the rest of the computer the frying pan may have damaged some internals especially where the pan hit (mouse pad, buttons.)  Continuing to use the laptop may present more problems in the future.  It's fairly easy to replace all the components as they fail, but would probably be better to replace the machine before it starts showing other problems.

In addition to not dropping cast iron pans on computers I would also suggest that you avoid giving them anything to drink.  If you do give your system a drink remove all power (including the battery) and wait for the entire machine to dry out (may take 2-3 weeks) before attempting to use it!

I lost a nice Gateway when it was connected to a wall outlet and someone tripped on the wire.  The wire fit very snugly into the case, and pulling the wire pulled the laptop onto the floor while the drive was in use.  The drive never ran again, just made a few clicking noises as it attempted to spin up.  Best recommendation is backup all important (can't live without it) information before you damage your computer.

---

