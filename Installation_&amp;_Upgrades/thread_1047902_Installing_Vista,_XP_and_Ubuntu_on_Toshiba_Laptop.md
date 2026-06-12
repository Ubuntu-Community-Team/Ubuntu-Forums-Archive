---
title: "Installing Vista, XP and Ubuntu on Toshiba Laptop"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by petersfreeman on 2009-01-22
**BACKGROUND**

I purchased a Toshiba Satellite A300-02W with Windows Vista Home Premium (64 bit) pre-installed.  What I want to do is install three operating systems, Vista, XP and Ubuntu.  

My reason is that I use Ubuntu as my main operating system, however there are some Windows XP applications that I need to use and there is one application that I use that only runs on Vista.

Initially I hoped to be able to shrink the partition upon which Vista runs and then create two new partitions, one for XP and the other for Ubuntu.  I recognize that the Ubuntu install would also need to create a swap partition.  While I can shrink the partition using The Computer Management tool in Vista, the resultant gained space is marked as "Unallocated" and is not recognized by the Ubuntu install. I cannot create any new partitions from this "Unallocated" space using the Computer Management tool in Vista Home Premium.  I would need a more advanced version of Vista. 

In the past, I have successfully install Ubuntu and XP on a number of machines.  This is the first time I am going to attempt this with Vista.

I have created the Recovery Disks for Vista.

**PLAN**

[LIST]
[*]I will use the Ubuntu install to completely delete all existing partition to the point where I have just one huge 250GB drive.
[*]Next, Using the Ubuntu install, I will partition the drive into four partitions, one for each operating system with the last one for the Ubuntu Swap.
[*]Then I will install XP in the middle partition.
[*]After that, I will install Vista in the first partition.  I will not need to create the partition that holds the Recovery System.  Neither will I need to create the other two partitions.  I believe one is for the "Media Centre", I don't know for what the other partition is used.
[*]Finally, I will install Ubuntu in the last two partitions.
[/LIST]

**QUESTIONS**

[LIST]
[*]Can I install Vista in the first partition using the Recovery Disk or will it blindly re-structure my 250 GB disk and return it to just the way it was as I purchased it?
[*]Assuming that the Vista Recovery Disk will allow me to install Vista into the partition I choose, will Vista see the existing XP installation and create a dual boot for XP and Vista?
[*]When I install Ubuntu, will Ubuntu GRUB create an operating system menu which includes Ubuntu, Vista and XP, or will it just show Ubuntu and Vista relying on the Vista choice to provide a second boot menu to choose between Vista and XP?
[/LIST]

Thank you,

Peter

---

### Post by Mark Phelps on 2009-01-22
If the "recovery disks" work like others, they will completely reformat and reinstall your entire drive, effectively wiping out anything you do to it -- including the XP installation.  Your disks may be different, of course, but the ones I've used give you no choices at all, they simply restore the machine to its original state.

Also, not having the disks, it's also my guess that if you do have a recovery partition, all the disks will do is boot into that partition to start the actual restore; meaning, that if you wipe the recovery partition, you will NOT be able to get Vista back, period.  So, I would advise against reformatting your entire drive unless you can confirm that the recovery disks contain a complete Vista image, not just a WinPE recovery boot program.

The different Vista versions use the same Disk Management console, so a "higher" version is not going to make a difference

You could try downloading and burning either a SystemRescueCd or a Gparted disk. Gparted just came out with a new version the end of December, so I would use it instead of the older versions.  The link to GParted is below:

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")  Burn the CD and boot from it.  You should then be able to format the unallocated space.

Also, formatting an NTFS partition for Vista with anything other than Vista may not work.  I tried this some time back from XP, and although the format appeared to work, once Vista was installed, it forced CHKDSKs on every boot.  I had to wipe the partition and reformat within the Vista install to get it to work.

---

### Post by petersfreeman on 2009-01-23
Thanks Mark, I'll try Gparted.

Peter

---

### Post by petersfreeman on 2009-01-23
**PROGRESS**

I tried GParted and it appears to work well.  The problem that I am encountering is the four Primary partition limit.  The pre-installed installation of Vista came with the following four partitions:

[FONT="Courier New"]
  1.46 GB 100% Free    EISA Config 
216.29 GB  50% Free C: System, Boot, Page File, Active, Crash Dump, Primary Partition
  7.63 GB  99% Free D: Primary Partition
  7.51 GB 100% Free    Primary Partition
[/FONT]
It appears that D: contains the recycle bin.  After shrinking C:, I freed up the following unallocated space and reduced C: to 174.58 GB
[FONT="Courier New"]
 41.71 GB              Unallocated
[/FONT]
**QUESTIONS**

[LIST]
[*]Where are the Recovery files kept since D: and the other two partitions without drive letters are essentially empty?
[*]What is the purpose of the 1.46 GB EISA partition ?
[*]What is the purpose of the 7.51 GB partition?
[*]If I delete the 7.63 and 7.51 GB partitions, will Vista load, operate normally?
[*]If I also delete D:, will I screw up Vista because it won't be able to find the recycle bin?
[*]Can I migrate the Recycle Bin to C:?
[/LIST]

Thanks,

Peter

---

### Post by petersfreeman on 2009-01-26
I managed to get most of my goals achieved.  I used the old 7.63 GB D: for Ubuntu ext3 partition and the old 7.51 GB fourth partition for Ubuntu swap.  I was not able to install XP, but I have decided to not install it now and just have dual boot Ubuntu and Vista.

I would still like to change the partition sizes so that the ext3 partition is more than 7.63 GB and the swap partition is less than 7.51 GB.  I'm not sure if I can do it with GParted now that I have installed Ubuntu, but if I cannot, I can re-install Ubuntu if required.  Comments?

---

### Post by David2009 on 2009-02-15
I am really interested in your multiple OS installation.  I have been running another version of linux, but I cannot get the wireless to work.  So, I have put in the Ubuntu Live CD, and it works out of the box.  I have a Toshiba A300 64-bit, too.

Good luck with the the triple installation!

---

### Post by petersfreeman on 2009-02-19
Hi David,

I am really happy with the Toshiba Laptops.  The install works right out of the box.

I also had a HP laptop and could never get the wireless to work.  My wife has a Compaq Presario and I needed to do a special install to get the wireless to work.  All this with the latest Ubuntu 8.10

I have yet to put WinXP on my Toshiba.  I need to do a bit more research first.

Cheers,

Peter

---

### Post by David2009 on 2009-04-07
Hello Peter.  I am unable to get the webcam (Chicony 2.0) to work.  Any suggestions?  I read that a Ubuntu version 9 is coming out soon.  Should I reinstall, or will updates come automatically?  

Thank you.

David

---

### Post by petersfreeman on 2010-03-11
Hi David, 

Sorry about the very delayed response.  I had not been monitoring the thread.  I have yet to get my web cam working, but have not looked at it yet as I don't really use it.  Have you had any luck?

Peter

---

