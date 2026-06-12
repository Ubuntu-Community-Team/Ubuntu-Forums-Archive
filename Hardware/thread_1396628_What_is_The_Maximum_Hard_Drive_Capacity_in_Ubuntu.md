---
title: "What is The Maximum Hard Drive Capacity in Ubuntu?"
date: 2010-02-02
forum: Hardware
---

### Post by umechanism on 2010-02-02
I have a Dell Studio desktop that is only 1 year old and the 650 Gig drive is already full.  I have a second drive bay on this computer and wish to add a new SATA disc drive.  I want to get the biggest drive I can but wondered if there is a hardware/software limit in either my machine's Bios or within Ubuntu 9.10 that will limit my drive's maximum size.

So, here's the question...How much capacity can I add (starting with 650 Gigs).

Thanks!

---

### Post by Grenage on 2010-02-02
The limits will be down to BIOS and filesystem type; assuming both are modern, I doubt you could buy a drive that would touch their limits.

---

### Post by umechanism on 2010-02-02
Chatting with Dell...not sure of competency here...they said it was 1.2 TB max which means I can only add another 600 Gig or so.  That did not sound correct to me.  Anyway to verify limits (or lack of limits)before I purchase a new drive?

---

### Post by Rhubarb on 2010-02-02
The maximum volume size for ext4 (Ubuntu 9.10's default filesystem) is currently 1EiB.
1EiB = 1 Million TiB

The biggest single hard drives that I currently know of are just 2 Terabytes in size, so unless you stripe more than 500,000 2TB drives in RAID0, you won't ever come across this problem currently.

I've currently got a 1.5TB hard disk in my computer at the moment (running Ubuntu 9.10 64bit partitioned as one big ext4), everything is detected and works fine.

---

### Post by umechanism on 2010-02-02
So there's not a bios limit to be concerned with?  Is there a way to check what my bios limit is?   

What really concerns me is the fact that I have a Generation 1 version of [this Hp Media Vault]("http://k0lee.com/hpmediavault/mvgen2/")which runs on Linux.  The max capacity limit is 1.2TB or two 600 Gig drives per bay.  This is running on Linux so why is there a limit of only 1.2TB?  

Sorry for the questions but I just want to order the biggest drive I can afford AND be able to access all of it.

---

### Post by Thorongil on 2010-02-02
There are possibilities to create larger volumes.

e.g. LVM and also USB/e_SATA RAID devices which support two or more Hard Drives of sizes up to 2 TB.

I have a 3TB Volume as external USB-RAID device which will only be supported on Linux if the Kernel was compiled with "CONFIG_EFI_PARTITION", as "regular" Partitions (non-GPT) cannot be created larger than 2TB.

fdisk is limited to 2TB. gparted can handle GPT partitions.

I have heard that some Ubuntu versions did not support partitions larger than 2TB.

File system limits are not related to this.

---

### Post by Grenage on 2010-02-02
Find your board version, then check the BIOS revision at boot time.  Then check the Manufacturer's site.

Or look in the mainboard manual.

---

