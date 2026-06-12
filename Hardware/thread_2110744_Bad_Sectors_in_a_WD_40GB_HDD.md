---
title: "Bad Sectors in a WD 40GB HDD?"
date: 2013-01-31
forum: Hardware
---

### Post by cybrsaylr on 2013-01-31
Have this WD 40GB drive that was starting to act 'funny'.
It's a dual booted setup with XP and Natty 11.04.

Ran Disk Utility that reports about 450 bad sectors in two places. Both XP and Natty still run OK but not really at 100%. 

How long should one go before replacing this drive that appears to be failing? Do it now or wait till Disk Utility red flags it? Disk utility just rates it 'unknown' right now and I have no idea what that means. 

I have another 120GB Seagate HDD in that PC for storage and Disk Utility reports it healthy and it has all green dots. Both are IDE drives.

---

### Post by mörgæs on 2013-01-31
While partitioning the half-dead drive you could create partitions which span the defective areas. Then, when installing you just use other partitions for the system.

On the other hand, 40 GB is not much. As an installation takes only about 5 GB you don't really need this drive.

You might be interested in
[http://static.googleusercontent.com/external_content/untrusted_dlcp/research.google.com/da//archive/disk_failures.pdf](http://static.googleusercontent.com/external_content/untrusted_dlcp/research.google.com/da//archive/disk_failures.pdf)

---

### Post by Mark Phelps on 2013-01-31
> **cybrsaylr said:**
> ... How long should one go before replacing this drive that appears to be failing? 

Really no way of knowing.  I had several WD drives fail me last year.  In one case, I suddenly encountered very slow booting -- bad sign.

I ran a check on the drive and it found bad blocks.

Within a few days, the drive became useless.  I tried to run the WD tools against it, but the utility shut down claiming there were too many errors.

So, you may have weeks to go, or only days.  No real way to know.

---

### Post by Bucky Ball on 2013-01-31
*Thread moved to** Hardware***

---

### Post by tgalati4 on 2013-01-31
How many poweron hours?

```
sudo smartctl -a /dev/sda
```

I have an old Maxtor 20GB drive that has been running for 118,529 hours.  It's been running Dapper Drake continuously since June 2006, and it was old then!

So as others have said, it may run for another 10 years or it may die tomorrow.  Back up your data regardless.

---

### Post by cybrsaylr on 2013-01-31
Thanks for the suggestions.

Decided to replace the WD drive with the 120GB Seagate drive used for storage. The 120GB drive already had 3, 40GB partitions. Used Seagate Disc Wizard to clone over XP from the WD drive. Took about 30 minutes to put XP on the first partition and it worked great. Did this because this was a spare PC and had no XP install discs. Then swapped the drives pulling out the failing WD drive. XP runs just like before on the WD drive only better since this Seagate drive is completely healthy with no bad sectors......so far. 

Too bad I couldn't do the same cloning, with 11.04. 
Am still undecided on what Ubuntu version to install as dual boot. 11.04 ran great but this 2.8 GHZ P4 PC only has 1 Gig of RAM, so I'm not sure how well 12.04 with run on it. Oh and this P4 can only run 32 bit Linux. Any suggestions?

---

### Post by ahallubuntu on 2013-01-31
FYI, you can copy partitions with Gparted very easily, even Windows partitions.  Works great.  The only issue is perhaps the boot sector, but assuming you are using Grub you can easily update it.  This assumes you are using a live CD/live USB boot.  You can't/don't want to copy a live partition.  You may also need to update the /etc/fstab file of the copied partition (in case UUIDs of / and swap partitions changed, find them with 'sudo blkid') but once you know what to do, takes maybe five minutes tops to do all of this after copying partitions.

Ubuntu 11.04 was great, but it's no longer supported.  I've been using 12.04 LTS for a couple of weeks with Gnome Shell and it's been working quite well - looks almost exactly like 11.04 (if you want EXACTLY like 11.04, try Mate, but Gnome 3 / Gnome Shell is probably going to be more standard with Ubuntu going forward than Mate, where I'd expect some things to break).

1GB should be plenty for 12.04 - I don't see why the RAM constraints would be much different than 11.04.

---

### Post by mörgæs on 2013-01-31
Xubuntu (or even better Lubuntu) will be a good choice.

---

### Post by cybrsaylr on 2013-01-31
> **ahallubuntu said:**
> FYI, you can copy partitions with Gparted very easily, even Windows partitions.  Works great. 
I did not know that thanks. 
> **ahallubuntu said:**
> The only issue is perhaps the boot sector, but assuming you are using Grub you can easily update it.  This assumes you are using a live CD/live USB boot.  You can't/don't want to copy a live partition.  You may also need to update the /etc/fstab file of the copied partition (in case UUIDs of / and swap partitions changed, find them with 'sudo blkid') but once you know what to do, takes maybe five minutes tops to do all of this after copying partitions.
I'll share something very interesting that just happened to me recently on the Dell i7 in my signature below. I installed a 128GB SSD as a boot drive with only 12.04 on it. Thus had 2 drives, SSD with 12.04 LTS and a 2TB drive with Windows 7. Didn't install ANY GRUB bootloader since W7 was seldom used and preferred going right into Ubuntu. Thus 12.04 started in ~20 seconds with no GRUB delay. If I wanted to boot into W7 it was very easy to do with SATA. You just hit F12 upon booting and select the HDD for boot. This worked great for almost a week. Then after some 12.04 updates Ubuntu auto-installed  GRUB and the traditional bootloader was installed tailored to my 2 drive configuration without me doing a thing! I was impressed! This applied with SATA drives, not sure if it will work with an IDE drive.


> **ahallubuntu said:**
> Ubuntu 11.04 was great, but it's no longer supported.  I've been using 12.04 LTS for a couple of weeks with Gnome Shell and it's been working quite well - looks almost exactly like 11.04 (if you want EXACTLY like 11.04, try Mate, but Gnome 3 / Gnome Shell is probably going to be more standard with Ubuntu going forward than Mate, where I'd expect some things to break).

1GB should be plenty for 12.04 - I don't see why the RAM constraints would be much different than 11.04.
Just yesterday something unusual happened with that PC with 11.04. Haven't used that PC in over a month or so and I know 11.04 is no longer supported....Update Manager did a popup stating this. However after a few seconds Update Manager showed there were 108 updates updates available totaling 251 MEGS! I clicked on update and Ubuntu updated those 108 updates to 11.04, which really surprised me, then said to restart since there were kernel upgrades! Didn't expect this at all and wonder how this even came about?

---

### Post by Bucky Ball on 2013-01-31
> **cybrsaylr said:**
> 

Just yesterday something unusual happened with that PC with 11.04. Haven't used that PC in over a month or so and I know 11.04 is no longer supported....Update Manager did a popup stating this. However after a few seconds Update Manager showed there were 108 updates updates available totaling 251 MEGS! I clicked on update and Ubuntu updated those 108 updates to 11.04, which really surprised me, then said to restart since there were kernel upgrades! Didn't expect this at all and wonder how this even came about?

Doubt they'll be another one. Probably just the dregs of what was left from the final update which was probably around October 2012. Also, if you had third-party PPAs (manually added repositories) they'll keep updating until the dev stops maintaining them and updating the PPA.

---

### Post by cybrsaylr on 2013-01-31
> **Bucky Ball said:**
> Doubt they'll be another one. Probably just the dregs of what was left from the final update which was probably around October 2012. Also, if you had third-party PPAs (manually added repositories) they'll keep updating until the dev stops maintaining them and updating the PPA.

Bucky Ball, thanks for the clarification on those updates.....never expected them.

---

### Post by Bucky Ball on 2013-01-31
All good, my theory. If you really wanted to check you could 'uname -r' and compare the kernel you get with the final kernel update for 11.04. ;)

---

### Post by ahallubuntu on 2013-01-31
> **cybrsaylr said:**
> I installed a 128GB SSD as a boot drive with only 12.04 on it. Thus had 2 drives, SSD with 12.04 LTS and a 2TB drive with Windows 7. Didn't install ANY GRUB bootloader since W7 was seldom used and preferred going right into Ubuntu. Thus 12.04 started in ~20 seconds with no GRUB delay. If I wanted to boot into W7 it was very easy to do with SATA. You just hit F12 upon booting and select the HDD for boot. This worked great for almost a week. Then after some 12.04 updates Ubuntu auto-installed  GRUB and the traditional bootloader was installed tailored to my 2 drive configuration without me doing a thing!

FYI, Grub was always installed.  But, when Grub detects only one OS, it doesn't show you a boot menu.  (Unless you hold down the "Shift" key I believe - think that still works.)  But if a 2nd OS like Windows is detected, then it shows you a menu.

What probably happened is that originally, Grub didn't detect Windows.  Hard drive not connected? Or something like that.  But an update ran the "update-grub" command that detected Windows 7, so it added it to the boot menu and started showing the menu upon startup.

> **cybrsaylr said:**
> Just yesterday something unusual happened with that PC with 11.04. Haven't used that PC in over a month or so and I know 11.04 is no longer supported....Update Manager did a popup stating this. However after a few seconds Update Manager showed there were 108 updates updates available totaling 251 MEGS! I clicked on update and Ubuntu updated those 108 updates to 11.04, which really surprised me, then said to restart since there were kernel upgrades! Didn't expect this at all and wonder how this even came about?

Those were the last updates for 11.04 that you never installed before.  For the moment, the repository servers are still active, but at some point they will be shut off.  I found this out with an old 10.10 installation I don't use for much.  I tried to install something and found that all of the source links in my repository were now broken.  The same will surely happen soon enough with 11.04.

---

### Post by varunendra on 2013-02-01
Nice explanation *ahallubuntu*, I just want to add a comment.

> **cybrsaylr said:**
> Thus had 2 drives, SSD with 12.04 LTS and a 2TB drive with Windows 7*...<snip>...*If I wanted to boot into W7 it was very easy to do with SATA. You just hit F12 upon booting and select the HDD for boot.
@cybrsaylr
You happened to actually have the kind of setup I 'Recommend' for people having more than one drive and multiple OS. That is - each hard disk having its own OS and bootloader. Then it is usually just a matter of hitting a key (like F12 in your case) during boot-up to choose between desired drives to boot their own OS.

This ensures that the system remains bootable if any of the drives or the OS on them fails.

However, a grub update in ubuntu has the tendency to install grub boot-loader on the drive which it 'sees' as the 'first' drive. So I recommend to set the Ubuntu drive as the 'first' one in BIOS so the windows boot loader doesn't get accidently overwritten during a grub update. To be extra sure, I even advise to 'remove' the other drive(s) while installing OS on one drive.

In this case, a grub update detects the other OS on the other drive > includes it in its menu to be presented on the next boot, but doesn't touch the boot loader on the other drive. So even if you remove the Ubuntu drive later, the system is able to boot from the other drive using its own boot loader and pertaining OS.

Hope I didn't confuse you. :)

Cheers!:popcorn:

---

### Post by cybrsaylr on 2013-02-01
Not confusing at all varunendra.
In fact we discussed this in this tread, along with a way to keep GRUB from updating if you prefer using F12 or whatever for selecting which OS to boot.
In post #7 darkod explains how to do this:
[http://ubuntuforums.org/showthread.php?t=2097492](http://ubuntuforums.org/showthread.php?t=2097492)

---

