---
title: "[SOLVED] Can someone suggest an External HD to me?"
date: 2008-11-11
forum: General Help
---

### Post by dfgilbert on 2008-11-11
Could someone please suggest a quality hard drive/brand that has full support under Linux?  

Only requirement:
USB only, two of the laptops in the house don't have firewire.

Preferably one that you use right now under Ubuntu.

---

### Post by cariboo on 2008-11-11
I havn't see any external drives that won't work  under linux. Buy an external drive, with a good warranty (3-5 years) and you should be ok.

Jim

---

### Post by CLomax on 2008-11-11
I have a Western Digital External HD which works perfectly.

---

### Post by dfgilbert on 2008-11-11
> **cariboo907 said:**
> I havn't see any external drives that won't work  under linux. Buy an external drive, with a good warranty (3-5 years) and you should be ok.

Jim

Well, I have a Seagate FreeAgent that I used to backup my audio work in OS X.  

Under Linux it does this:
- Read only
- When it's idle for a bit, it goes to sleep and never wakes up without me unplugging and replugging it in.  

I read that a lot of people had the same issue and Seagate has no plans to help Linux users out.  So I'd steer clear of them in the future.

---

### Post by dfgilbert on 2008-11-11
> **CLomax said:**
> I have a Western Digital External HD which works perfectly.

Awesome, I'm gonna look into those.

Thanks to both of you for your responses!

---

### Post by CLomax on 2008-11-12
> **dfgilbert said:**
> Awesome, I'm gonna look into those.

Thanks to both of you for your responses!

Glad to be of service.

Btw, here's an Amazon page of my external...

[http://www.amazon.co.uk/Western-Digital-320GB-Essential-External/dp/B000EXZB02](http://www.amazon.co.uk/Western-Digital-320GB-Essential-External/dp/B000EXZB02)

---

### Post by kaptengu on 2008-11-12
Or this one:
[http://www.amazon.com/LaCie-301304U-External-Design-Poulton/dp/B0010YWPZ8](http://www.amazon.com/LaCie-301304U-External-Design-Poulton/dp/B0010YWPZ8)

---

### Post by CLomax on 2008-11-12
> **kaptengu said:**
> Or this one:
[http://www.amazon.com/LaCie-301304U-External-Design-Poulton/dp/B0010YWPZ8](http://www.amazon.com/LaCie-301304U-External-Design-Poulton/dp/B0010YWPZ8)

:shock:

---

### Post by Doug77 on 2008-11-14
Does anyone have any experience with Buffalo external hard drives?  I liked Seagate, but I'll avoid them if they don't appear very accommodating for Linux, and I've had bad customer service experiences with Western Digital.  I'm leaning towards a Buffalo 2.5" HD-PF series.  Their website says that they just support Windows XP, Vista, 2000, or Mac - but I assume it's pretty normal for companies not to explicitly say they support Linux.  Is this safe to assume?

---

### Post by The Cog on 2008-11-14
I think anything that also says Mac is likely to work. Mine is a Freecom "Hard Drive Classic 500G" and works like a dream. Again, the box says Windows and Mac, no mention of Linux. 

It also says you need a CD-ROM drive, which my netbook doesn't have, presumably to load their software whatever that does. It certainly isn't needed on Linux.

---

### Post by Riverside on 2008-12-12
> **dfgilbert said:**
> Well, I have a Seagate FreeAgent that I used to backup my audio work in OS X.  

Under Linux it does this:
- Read only
- When it's idle for a bit, it goes to sleep and never wakes up without me unplugging and replugging it in.  

I read that a lot of people had the same issue and Seagate has no plans to help Linux users out.  So I'd steer clear of them in the future.I installed a new Seagate FreeAgent Xtreme 1TB external hard drive this week and am not experiencing the sleep issue.  The drive spins down when not in use and spins back up again when needed.

However, it is connected using eSATA (the drive supports eSATA, Firewire and USB 2.0), I wonder if that makes a difference?

In respect of the drive being read only, as standard it is formatted with the NTFS file system and I could write to it immediately.  Since it is in use with Linux only I reformatted it using gparted as ext3 after which I was unable to write to it, as it is owned by root and has permissions:

anthony@riverside:/media$ ls -l
total 6
lrwxrwxrwx 1 root       root          6 2008-11-12 00:30 cdrom -> cdrom0
dr-xr-xr-x 4 4294967295 4294967295  136 2036-02-07 01:58 cdrom0
drwxr-xr-x 4 root       root       4096 2008-12-12 12:40 FreeAgent

The solution is straightforward though, either change ownership and group of the entire drive:

sudo chown anthony:anthony FreeAgent

Or, more correctly since Linux is a multi-user operating system, create a directory for myself as a user on the drive:

anthony@riverside:/media/FreeAgent$ sudo mkdir anthony
anthony@riverside:/media/FreeAgent$ sudo chown anthony:anthony anthony

I now have a directory that I can read and write to as ordinary user anthony.  If I wish at a later stage to allow other users on the system to write to it, I can create similar writeable directories on the drive for those users also.

---

### Post by scouser73 on 2008-12-12
I am using four 500GB Maxtor Basics HDDs, and one LaCie 250GB HD, all working perfectly under Ubuntu/Linux. So I would suggest any of those makes.

---

