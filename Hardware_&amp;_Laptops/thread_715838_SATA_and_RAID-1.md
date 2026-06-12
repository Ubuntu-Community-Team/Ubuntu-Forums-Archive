---
title: "SATA and RAID-1"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by tuxx on 2008-03-05
Hello

I don't seem to be able to find exactly what I'm looking for.

I'm building my new server around SATA and RAID-1 for maximum data-security.

However when I search google it seems this is not so straight forward on Linux, mainly due to FakeRaid (software raid controllers).

From what I can see it takes a lot of fuzz to get it to play.

Now I'm then looking for a hardware raid solution but this also seems to make problems with Linux.

Can I, and how?, run Ubuntu 7.1 (or later perhaps) on my server and get fully functional RAID-1 on my 2 SATA drives?

What does it take?

---

### Post by chrisdeckard on 2008-03-05
I use the on-board SATA controllers of my MSI motherboard.  I don't use "FakeRaid", but use Linux software RAID instead.  There will be an option to setup RAID with the Ubuntu server install.  My server at home uses two RAID 1 partitions.  One for swap, one for /.  If you are going to have a swap partition, it NEEDS to be mirrored as well because if the drive your swap partition is on dies, Linux will lock up or panic anyway.

During the install, create two partitions on each drive, and set the partition types to autoraid or raid, or whatever it is.  (I forget off the top of my head).  Then go in and setup RAID 1 devices for both partitions.  You can then set the partition types for the RAID containers to swap and ext3, and go on with your install from there.  It's pretty easy, though you may have to fiddle with it a bit to get it to your liking.

-Chris

---

### Post by tuxx on 2008-03-05
Thank you for your reply.

Does this mean it's working as real RAID? By real I mean hardware.

Is FakeRaid or Linux Software Raid as real as if I was running it eg. Windows XP?

Is there any downsides to software raid?

---

### Post by chrisdeckard on 2008-03-05
It's software raid, controlled by the kernel.  No hardware is involved except your CPU.  There is nothing wrong with software RAID, unless you are doing super high performance computing and you need the maximum I/O possible.  If you are running a CPU intensive program, and it's also I/O intensive, you will notice a slight decrease in performance.  For normal stuff (and I include basic video editing and transcoding, MythTV, etc. in that) software RAID is just fine.  The only real other benefit that you get from hardware RAID (and I'm talking expensive hardware RAID) is that the RAID controller has cache, and that cache can be battery backed up.  The RAID controller will make sure the integrity of your RAID container is in tact.

-Chris

---

### Post by tuxx on 2008-03-05
So software raid is as real as hardware raid?

I'm choosing -1 because I need to keep my data safe.

Can I risk loosing it all if my setup blows for some reason or will I always no matter what have my mirrors on each drive? (of cause not if I delete it.. hehe.) But does the existance of my data rely on my setup? If you catch my drift.. it's difficult for me to explain :-)

---

### Post by chrisdeckard on 2008-03-05
RAID is RAID.  Hardware RAID handles the computations in dedicated hardware, software RAID handles the exact same computations on your CPU.  It makes no difference where it's computed, all that matters is that your data is, in this case, mirrored.

All this protects you against is that your system will still run when one drive fails.  You should still have a reliable backup plan (external hard drive, tape drive, multiple copies off site, something in a fireproof safe, something in a safe deposit box) for your important data.  RAID is not a backup plan.  If a power surge fries every component in your computer, your data is still lost.

-Chris

---

### Post by tuxx on 2008-03-05
Thank you for your reply.

I believe I have what I need now.

My server will be acting as a central server in the house for backup, storage and mediaserver for the tv.

I'm aware that a fried computer will make me cry, however having RAID-1 I'm certain I'm so much more safe than with just one drive.

I have permament backup for the most critical files.

Thank you again :)

---

### Post by SighKick on 2008-03-06
I have much the same problem, ASUS P4C800 MB with Promise 20378 FastTrak SATA RAID.

Seems like a simple problem with the most difficult answers I have seen for someone trying to come to grips with Linux in general but also trying to make use of the available technology.

I have had RAID1 running just fine using Win2K3 and now wish to switch entirely to Linux, preferably Debian or Debian based such as Ubuntu. I will be starting from scratch with two SATA 120Gb drives and have been experimenting to no avail.

Can anyone help with basic step-by-step instructions please?  Is there a tutorial out there?  If I say please nicely :)

I am not very good with command line yet and have never compiled a kernel - some of the instructions I have found assume you are a Guru and the best one was in Japanese English. Trying to understand this broken English AND not being a Guru is just too much.

---

### Post by mspIggy on 2008-07-05
> **chrisdeckard said:**
> I use the on-board 
During the install, create two partitions on each drive....
-Chris

i am in a similar circumstance - setting up raid 1

how big are these drive partitions?

the first primary should be how big in size? the rest is swapable...?

i have no clue and an concerned - my install will sooner or later (like after a backup) crash as a result of no partition space left...

many thanks

---

