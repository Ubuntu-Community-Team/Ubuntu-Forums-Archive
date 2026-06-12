---
title: "After GParted CD-DRIVE hates Windows CDs"
date: 2011-06-10
forum: Hardware
---

### Post by xtremesupremacy3 on 2011-06-10
Hey there,

For years I have not used anything except Linux.

But since Wine is starting to annoy me and I love gaming, I thought I'd make a Windows partition for gaming.

I loaded an Ubuntu Live-CD, used GParted to shrink my Linux partition and restarted.

Now here comes the weird bit.

I have 5 different Windows CD's, all in a range of versions.
And one single Ubuntu CD.

When I load Ubuntu Live, it loads no problem.
When I load any of the Windows CD's, it keeps spinning and spinning until it eventually loads my HDD.

EDIT: When I say spinning, I don't even get to load the CD, it's the blank screen and blinking white line until it times out and loads grub

Any idea what's going on and how to fix it?

---

### Post by papibe on 2011-06-10
Is it XP? In my experience, XP doesn't know about partitions, it always formats the whole drive.

If that's the case you should backup your linux partitions (clonezilla maybe), install XP, shrink NTFS, and then recover your partitions.

I hope Vista and 7 would do a better job.

Regards.

---

### Post by xtremesupremacy3 on 2011-06-10
Thanks for the uberquick reply!

I might not have made it too clear, but it doesn't even load the CD's...the only one it will load is Ubuntu, no Windows.

So I don't even get to the option of installing XP.

But I have XP, Vista and 7, all no luck

---

### Post by xtremesupremacy3 on 2011-06-10
I did some googling, and I didnt know (although i should have) that an OS checks the hard drive before it loads its program (?)

Now I am wondering, is there a possibility that after the change to partition, Ubuntu has kinda 'locked' the HDD so that I am unable to run Windows disks?

If that sounds plausible, how do I 'unlock' that?

---

### Post by smurphy_it on 2011-06-10
It's windows.  You are better off with linux ;-)

---

### Post by xtremesupremacy3 on 2011-06-10
As much as I agree.

For gaming Linux isn't the best...don't be offended, but having used Linux for years and years, I've watched it grow into an important OS, but gaming remains bad.

---

### Post by coffeecat on 2011-06-10
> **xtremesupremacy3 said:**
> I did some googling, and I didnt know (although i should have) that an OS checks the hard drive before it loads its program (?)

Now I am wondering, is there a possibility that after the change to partition, Ubuntu has kinda 'locked' the HDD so that I am unable to run Windows disks?

If that sounds plausible, how do I 'unlock' that?

No. I've done quite a bit of experimenting with the XP install CD with various partition layouts on the hard drive and the disc never fails to load. It will recognise Linux partitions as partitions, but does not recognise the filesystem and calls them "unknown partition" or words to that effect. 

If none of the XP discs will boot but the machine will boot from other CDs, then coincidence that it may be, but something must be wrong with those Windows CDs. But with one caveat. Are they Microsoft install CDs or OEM manufacturer's recovery discs? The latter are quite a different matter and some might be confused by an unusual (to them) partition layout.

By the way, if you do manage to get the Windows CD to boot and you have logical partitions on the drive formatted with a Linux filesystem, beware. In some circumstances, the XP disc will do the most extraordinary things to the partition table. I can give you more details if you manage to get one of those discs booting.

---

### Post by xtremesupremacy3 on 2011-06-10
Thanks for your reply there, really appreciate it.

I have 1 OEM but the others are just bog standard CD's.

It's odd though since they do run on my mothers system without problems.
Perhaps time to get a new drive I think.

I will try and somehow get them working, if only XP works, I will certainly let you know.

---

### Post by coffeecat on 2011-06-10
> **xtremesupremacy3 said:**
> Thanks for your reply there, really appreciate it.

I have 1 OEM but the others are just bog standard CD's.

It's odd though since they do run on my mothers system without problems.
Perhaps time to get a new drive I think.

I will try and somehow get them working, if only XP works, I will certainly let you know.

That is interesting that they run on your mother's system.

I was involved in a thread a few months ago with a similar issue. If I remember correctly, the OP could boot a Linux CD but not the XP CD, but the XP CD would boot on another system. I don't remember if we ever came to any satisfactory conclusion.

All very odd.

The important thing is that the XP CD will boot on a system with Linux partitions, all else being equal, but can do some very silly things.

Good luck!

---

### Post by xtremesupremacy3 on 2011-06-10
Yeah that sounds like the exact same problem I'm having now.

Well I'll let you know how I get on, thanks for that

---

### Post by xtremesupremacy3 on 2011-06-10
Okay, so it was the disks, odd.

Anyway, after the 6th disk of Windows 7, I get the 'press any key to boot...' blah blah.

Anyway, after pressing the key I get 
```
CDBOOT: can't find BOOTMGR
```
or something along those lines.

That's as far as it goes, what can I do now?

---

### Post by coffeecat on 2011-06-11
5 disks of XP and 6 of Win7, from the last of which something essential cannot be read? I wonder if there is something wrong with the optical drive, even though it's reading your Ubuntu live CD.

If that's a desktop machine, have you another optical drive you could test in it? Or do you have access to a USB optical drive to try?

---

### Post by dandnsmith on 2011-06-11
I'd go with a problem CD drive - makes much more sense than OS locking the HDD or CDs with problems. Booting from a CD is often much more demanding than just reading it as an ordinary data CD, and will show up developing problems.

Sometimes you can alleviate problems developing by using a lens-cleaner CD in the drive.

---

