---
title: "could hard drive corruption cause it to stop showing up in BIOS?"
date: 2010-03-12
forum: Hardware
---

### Post by stefansjs on 2010-03-12
The subject line kinda says it all.  A while ago (several months ago) I had a serious SATA hard drive failure that caused my mythbuntu system to stop booting.  I didn't have time for thorough troubleshooting at the time, so I simply discovered which HD was the problem and unplugged it.  I've recently had time to do some real troubleshooting to find out what the problem is.  The first thing I did was plug it into my windows computer (with a different SATA cable) windows would begin to load but just restart part-way through booting.  I loaded an Ubuntu Live CD (9.04) and it gave me an error along the lines of "SRST Failed (errno=-16)" (I think that's right) and the HD didn't show up in /dev.  I read around and found a bugreport that claimed that this error was fixed in a kernel update.  So, I decided to put it back into the mythbuntu computer, and it just doesn't show up in /dev.  I rooted around in the BIOS and found that the slot into which this HD was plugged was blank.  This is weird because the empty slots say "none" and the other filled slots list which HD it is (manufacturer and model number), but this one is just blank (this also happens for the BIOS on the windows computer).  All this was a very wordy workup to get to the question:
> Is it possible for there to be some sort of HD corruption that would cause it to confuse the BIOS and is there a way to fix this type of corruption?
If it helps, the HD was formatted ext3.  I'm especially confused since the Windows computer's BIOS won't see the HD, but it will still restart during boot anyways.

---

### Post by kidders on 2010-03-13
Hi there,

There's nothing you could put on a hard disk to prevent it being recognised by your BIOS. At that low a level, a computer simply doesn't care what's on the platters ... only that the drive's on-board controller responds properly to a series of basic commands.

Testing the disk with a different cable & motherboard pretty much rules out most possible problems. All that's left is a fault with the drive itself, imo. The boot problems you see when it's plugged in are probably being caused by the drive failing to respond properly to basic queries (eg what type of device it is, what it's controller bandwidth is, etc.)

I guess that isn't terribly helpful ... Sorry.

---

