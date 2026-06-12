---
title: "ATA HDD is being recognized as SCSI HDD"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by LoyalTraitor on 2007-09-11
Well, I've tried multiple times to install Ubuntu from a LiveCD to no avail. Whenever I tried to boot without a the CD, I got the "BOOT DISK ERROR. PLEASE INSERT SYSTEM DISK AND PRESS ENTER" error. So maybe it has to do with the fact that the HDD I have installed is being recognized as SCSI, as the screenshot illustrates. 

Is this the cause of my problem? If so, how can I fix it?


On a side note: The only experience I've had on Linux is today, working from this LiveCD.

---

### Post by startlinuxtoday on 2007-09-11
same here. the cd came from a book and the install was not designed to go like the download iso. perhaps your install is incomplete. or try putting it in as entered and then from command line do an apt-get update. if all that fails, just burn the latest iso (recomended) and install - only takes a few minutes!

---

### Post by LoyalTraitor on 2007-09-11
> **startlinuxtoday said:**
> same here. the cd came from a book and the install was not designed to go like the download iso. perhaps your install is incomplete. or try putting it in as entered and then from command line do an apt-get update. if all that fails, just burn the latest iso (recomended) and install - only takes a few minutes!

Burning a new Disk would be kind of difficult, though. Considering that I only have 1 CD drive and it happens to be running the LiveCD. 
I was lucky enough that I had the thing, I burned it months ago, because I was going to install it then, but more pertinent tasks came up. Then my Windoze died. Actually, I think it was a HDD failure caused by heat, but the HDD is working fine, besides this whole getting recognized as an SCSI disk business.

---

### Post by ronWI on 2007-09-11
I'm not an expert, but I think it's pretty common to see your ATA disk show up as scsi. When you boot into the Live CD, open a terminal window and type 'dmesg'. (You may have to do a 'sudo -i' first to get root access.) Scroll back through and I think you'll see that your disk is detected as ATA first but then gets assigned a scsi 0.0.0.0 or some such thing.

Did you choose a boot loader when you installed?

Ron

---

### Post by dabl on 2007-09-11
> **LoyalTraitor said:**
> 

 but the HDD is working fine



Welllllll, maybe.

Since Feisty, in *buntu all hard drives are "sd_" as far as the OS is concerned (Grub is another story) -- don't worry about that.  The problem you are having is unrelated to the "s" designation.

But, I'm not so sure that it is unrelated to the late demise of Windows -- was it on that same 40GB drive?  Or did you get a new drive?  Because the installation of Grub on the Master Boot Record (MBR) doesn't seem to be taking.  And that's a bad thing.  :(

UNLESS, you happen to have a bad setting in your BIOS "boot sequence" settings, in which there is no hard drive listed.  You need one, right after the CD drive.  I'll cross my fingers ...

---

### Post by LoyalTraitor on 2007-09-11
> **dabl said:**
> Welllllll, maybe.

Since Feisty, in *buntu all hard drives are "sd_" as far as the OS is concerned (Grub is another story) -- don't worry about that.  The problem you are having is unrelated to the "s" designation. 
K. Done worryin' 'bout that. 

> **dabl said:**
> 
But, I'm not so sure that it is unrelated to the late demise of Windows -- was it on that same 40GB drive?  Or did you get a new drive?  Because the installation of Grub on the Master Boot Record (MBR) doesn't seem to be taking.  And that's a bad thing.  :(

Same drive. How do I go about fixing this problem?

> **dabl said:**
> 
UNLESS, you happen to have a bad setting in your BIOS "boot sequence" settings, in which there is no hard drive listed.  You need one, right after the CD drive.  I'll cross my fingers ...
Nope, My BIOS setting are pretty fine, I think. Removable, CDDrive, HDD, Disabled is the priority order, I believe.

---

### Post by ronWI on 2007-09-12
So, you didn't answer ...

Did you install the GRUB or LILO boot loader?

---

### Post by cimness on 2007-09-22
My computer (running Kubuntu Feisty from a 100gb hd that previously ran windows xp) is freezing on every shutdown and bootup now with a soft lockup which appears to be caused by this same problem, when I check the log. 

It is first trying it as an ATA and then, after a lot of errors, trying it as an SCSI instead. It goes through ata1: soft resetting port after an ATA bus error a bunch of times in a row during the same session, interspersed with SCSI bits in between.

I have grub installed, in answer to someone else's question. But I'm pretty new to Linux as well and mostly clueless.

---

