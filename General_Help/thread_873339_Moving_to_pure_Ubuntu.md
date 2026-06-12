---
title: "Moving to pure Ubuntu"
date: 2008-07-28
forum: General Help
---

### Post by jamesdcarroll on 2008-07-28
I did a dual boot of Ubuntu onto my Windows machine just as a precaution against losing files. I have 2 physical hardrives, one was formatted ext3 from stem to stern during the Ubuntu install, while the other is two partitions of NTFS. I've now moved basically everything of value off the NTFS drives and with the joys of Virtual Box feel comfortable that anything that I could still need Windows for can be accounted for. I'd like to, therefore, claim that 2nd drive in the name (well, filesystem at least) of Ubuntu.

I installed GPartEd (I have a profound aversion to the command line) and looked around and found how to unmount and then reformat the drives.  The concern that I have is that one of the NTFS partitions has the 'boot' flag on it while the ext3 does not. 

How can I do this safely? 

Also, the devices are showing a fair bit smaller than they should. My 320 gig drive is being reported at 298 and the 250 at 232 gig. I know that there's a bit of 'rounding' that goes on in much the same way that a 2 by 4 isn't really, but this seems a bit more than I would expect; nearly 10%.

Thanks for you help!! I'm THIS close to being windows free. 

Except for that VBox one. Just in case. ;)

---

### Post by knightcoder on 2008-07-28
Yeah, the NTFS file system would store some data in the beginning of the space. Its for indexing for the file system and other stuff. I believe all file systems do that.

---

### Post by brokenLockpick on 2008-07-28
320GB is the same as 298GiB or very close
The problem is that often drives are advertised in GB while the system reads in GiB
GiB are TRUE gigabytes in the binary sense

Don't know about the boot flag though

Edit: An actual gigabyte is 2 to the 30th power bytes, which is 1073741824 bytes, they often for marketing purposes consider a gigabyte to be 1000000000 (one billion bytes)

---

### Post by knightcoder on 2008-07-28
But the difference in tens of gigs is not supposed to happen.

---

### Post by brokenLockpick on 2008-07-28
> **knightcoder said:**
> But the difference in tens of gigs is not supposed to happen.

see above

---

### Post by jamesdcarroll on 2008-07-29
Yea, I kinda figured the disk sizes were gonna be a little off, but I still need to know how to make that final move safely especially the whole 'boot' partition thing.

Any insight?

---

### Post by brokenLockpick on 2008-07-29
> **jamesdcarroll said:**
> Yea, I kinda figured the disk sizes were gonna be a little off, but I still need to know how to make that final move safely especially the whole 'boot' partition thing.

Any insight?

I have a similar setup but I have a 250GB disk that is all NTFS and one split into NTFS and ext3. it seems to me from looking at my filesystem that the flag has been moved to the ext3 part of the disk which appears to be where grub resides on my machine, or at least there is a /boot/grub directory that appears to be on my ext3 partition.

In your situation I would probably try simply disconnecting the NTFS drive and booting to see what happens. I highly doubt trying that will do anything catastrophic like erasing your ext3 drive, but I can't promise nothing bad will happen.

If you're feeling brave you could try disconnecting the NTFS drive and booting, or if you're feeling cautious you can wait for someone who knows exactly what to do, as I'm only 95ish percent confident in my take on the issue.

---

### Post by 3rods on 2008-07-29
If you're worried about the "boot" bit, you can turn that off in gparted. Right click on the drive, and it's something in there. 
I just saw it when I was using it last week, but I'm not in front of my Ubuntu box right now to check. :( 


You can always just leave it the 'boot' part and format it ext3 from gparted. It's not going to hurt anything. GRUB handles which drive to boot. It would be pretty hard to dual boot if that wasn't the case.

I'm not completely missing something here, am I? 

Does the NTFS drive have GRUB on it? Is it the first physical drive? (Channel 0)

---

