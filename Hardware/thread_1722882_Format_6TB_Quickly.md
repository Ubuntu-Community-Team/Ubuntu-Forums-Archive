---
title: "Format 6TB Quickly"
date: 2011-04-06
forum: Hardware
---

### Post by TheFuzz4 on 2011-04-06
Hey There fellow Ubuntuers,

So I now have a 6TB external drive.  The problem I have is that formating this sucker.  After spending the better part of the afternoon googling this I have yet to find an answer.  I want to create a partition table in EXT4.  Ok so I fire up my gparted and give it a go, several hours later it is still hard at work on this.  If I plug this thing into a windows box and do a quick format, the drive is up and running in under 2 mins but with gparted I let it run for over an hour.  Is there a way to get this thing to format quickly?  Or do I just start it before I head out for the day and come back next week and it might be done?

Thank you all in advance for your help with this.

---

### Post by Grenage on 2011-04-06
I'm assuming that at 6TB, it's not actually a single drive?  Have you tried fdisk from a command line?

---

### Post by TheFuzz4 on 2011-04-06
Yeah its 4 2TB drives in an enclosure.  No I haven't tried fdisk from the command line yet.  I'll give that a go.  I was just using gparted.  Thanks Grenage

---

### Post by TheFuzz4 on 2011-04-06
Ok not going to lie, I've never actually used the fdisk to partition a disk in Linux, back in the day of Windows 3.1 and 95 I used to use it all the time with a new HD but I know that the two versions are totally different.  So I've been reading through the man pages on this but if you could possibly provide me with a little sample of what a command to format the drive would look like that would be great.  I just want a EXT4 partition on it thats it :).  Thank you.

---

### Post by TheFuzz4 on 2011-04-06
Haha nevermind figured it out.  Thank you

---

### Post by Grenage on 2011-04-06
> **TheFuzz4 said:**
> Haha nevermind figured it out.  Thank you

Ok dokes. :)  Like most things, it's really simple *once* you know what you're doing!

---

### Post by TheFuzz4 on 2011-04-06
Thank you for your help with this it was greatly appreciated.

---

### Post by psusi on 2011-04-06
fdisk is for partitioning disks, and is limited to ones smaller than 2tb.  To format, you use mke2fs.  It has an option that will make the format much faster: -E lazy_itable_init, but it is not safe except on newer kernels ( like the one in Natty ) that know how to finish the format properly in the background, which is why the option is not enabled by default, except on Natty.

---

