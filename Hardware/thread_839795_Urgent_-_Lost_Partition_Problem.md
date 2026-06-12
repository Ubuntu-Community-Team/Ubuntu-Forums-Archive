---
title: "Urgent - Lost Partition Problem"
date: 2008-06-24
forum: Hardware
---

### Post by LMD1990 on 2008-06-24
Okay, so it goes like this:

On Sunday, my PC died, getting raped by a nasty virus and crashing my PC as a result of the "verifying DMI pool data" hang error. After trying to reinstall Windows XP but failing, I took it to a repair shop, where they completely wiped it all and returned my PC with an XP installation that took up all of my 230B hard disk.

Today, I reinstalled Ubuntu onto its own 80GB partition. I then tried to boot into Windows XP, and it couldn't. I used fixmbr in the recovery console, only to get the verifying DMI pool data error again. This annoyed me, so assuming that the partitions had become shredded and smashed together because of permanent damage to the physical hard drive, i decided for the time being to try and do a clean install myself.

I put in the XP disk, and i was shown only ONE partition. This happened last time, but assuming that it was just all of my hard drive, i thought nothing of it- I deleted it, and, formatted to NTFS, and then put Windows XP Pro back on. Then I checked my hard drive volume... and it should be 230, but is only 127GB. Therefore, I'm assuming that my Ubuntu partition has been buried.

I no longer want that particular partiton- I just wanted everything wiped so I could start off with a full-hard-drive-XP. However, I'm slightly worried that I cannot find that partition, and I just want it removed. What do I do?

---

### Post by logos34 on 2008-06-25
> **LMD1990 said:**
> I put in the XP disk, and i was shown only ONE partition. This happened last time, but assuming that it was just all of my hard drive, i thought nothing of it- I deleted it, and, formatted to NTFS, and then put Windows XP Pro back on. Then I checked my hard drive volume... and it should be 230, but is only 127GB. Therefore, I'm assuming that my Ubuntu partition has been buried.

Almost sounds like the old 28-bit LBA (128 GB) barrier...but SP1 took care of that.  Maybe check the hard disk detect settings in the Bios (and check with your mobo manufacturer that you have the latest Bios updates--although the repair shop would probably have done this already).

Boot from the ubuntu livecd and open Gparted. (system>admin>partition editor).  What does it show?

---

### Post by LMD1990 on 2008-06-25
I managed to fix it now- I used unetbootin partition-manager to find the rest of the space. What I found was just blank, unallocated space- it appears that my Linux partiton kinda blew up into nothingness O_o I think i have a defective hard drive, because this keeps happening.

I'm having to use Wubi Ubuntu for now :(

---

### Post by logos34 on 2008-06-25
> **LMD1990 said:**
> What I found was just blank, unallocated space-

hmm, it still should have showed up:

> I put in the XP disk, and i was shown only ONE partition. This happened last time, but assuming that it was just all of my hard drive, i thought nothing of it- I deleted it, and, formatted to NTFS, and then put Windows XP Pro back on. Then I checked my hard drive volume... and it should be 230, but is only 127GB. Therefore, I'm assuming that my Ubuntu partition has been buried.

even on the windows installation cd, it should list partitions AND show any remaining [unallocated] space.  And in xp disk storage/computer mgmt window, it should show any linux as type 'unknown' with the size

---

### Post by greco8523 on 2008-06-25
This is classic signs of bad sectors, backup your data and get a new drive. And count yourself lucky you haven't lost any important data.

---

