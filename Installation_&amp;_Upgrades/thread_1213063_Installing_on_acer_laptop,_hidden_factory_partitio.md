---
title: "Installing on acer laptop, hidden factory partitions"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by bmuto on 2009-07-14
Hi, I am new to ubuntu and I want to install it to dual boot on my laptop.

The laptop is Acer aspire 6930, with factory installed vista. There are 4 partitions on it currently (factory setup):
1 hidden partition (i'm guessing for booting and/or restoring system)
1 partition for C: with windows and program files etc
1 empty partition for user data
and 1 smaller hidden partition

I was thinking of using this empty data partition to install ubuntu, reserve about 4 gb of it for swap and the rest for /

What I'm worried is that the first partition on the disk is one a hidden partition named "PQSERVICE".

So if I install ubuntu, will it write on this partition to allow dual boot menu?

In this case, will I still be able to use "restore factory default" for vista? (since part of that will be overwritten by ubuntu)

Or in worst case, will I even be able to boot vista? Since this is some non-standard partition I think.

Anyone had similar experience, or can help with some guide link or soemthing? I tried searching forums but couldnt find exactly what I am asking for.

Thank you, and sorry my english is not very good.

---

### Post by Mark Phelps on 2009-07-14
Everyone's probably going to provide different advice, so I can only provide what I've found works well.

If you need more space, you should defrag the Vista OS partition and shrink it using the Vista Disk Management utility.  Don't resort to using the Ubuntu installer or a GParted Live CD. If you do, you run the risk of corrupting the Vista OS partition and rendering it unbootable.

Don't touch the hidden partitions if you ever want to recover your machine's Vista install.

I found that the Ubuntu Desktop LiveCD had problems recognizing an existing Vista install, so I used the Alternate CD (which DID see the partitions), created the partitions needed for Ubuntu, and installed using that.  You could also create the partitions by downloading and burning a GParted LiveCD from Distrowatch.com, and then use "manual" mode during the partitioning part of the install to reuse what you've already done.  That way, you'll reduce the risk of overwriting one of the other partitions.

Ubuntu will recognize the existence of Vista and add an entry to its boot menu, but it will also overwrite the disk MBR. This will allow you to boot either Vista or Ubuntu. If you later do a repair of Vista, that will wipe out what Ubuntu did to the MBR.

That being said, I STRONGLY suggest that you boot with a desktop LiveCD and try it out before you do the install.  Laptops are infamous for customized hardware requiring drivers that Linux does not supply.  You won't be able to use your MS Windows drivers in Ubuntu, so anything that doesn't work in LiveCD mode is likely to be considerable work to fix later -- if it's even fixable.

---

### Post by az on 2009-07-14
Do you have the Acer backup utility which allows you to reinstall Vista?  Did your laptop ship with Vista Installation disks?

---

### Post by bmuto on 2009-07-14
Thanks for the detailed advice Mark. I did try the livecd 9.04 for half an hour, and everything seemed to work fine, but it was a little slow. I liked the OS so I wanted to install it, dual with vista.

But as az asked, the laptop didnt come with any vista cds.. =( Ther is a preloaded utility which presumably backups your system and restore it, or restore factory setup. What Iam not sure (and afraid) is when I install Ubuntu, it might overwrite this restore option data, which I think is probably on the hidden partitions.

I'll try to find if there are any "tricks" that I should do to prevent anything like this happening.

---

### Post by az on 2009-07-15
> **bmuto said:**
> Thanks for the detailed advice Mark. I did try the livecd 9.04 for half an hour, and everything seemed to work fine, but it was a little slow. I liked the OS so I wanted to install it, dual with vista.

But as az asked, the laptop didnt come with any vista cds.. =( Ther is a preloaded utility which presumably backups your system and restore it, or restore factory setup. What Iam not sure (and afraid) is when I install Ubuntu, it might overwrite this restore option data, which I think is probably on the hidden partitions.

I'll try to find if there are any "tricks" that I should do to prevent anything like this happening.

I backed up The default Vista that came with my Acer and wiped the drive of everything on it.  Then I deleted everything.  

I installed Ubuntu onto a pristine partition table.  The laptop works fine and I can restore the Vista default install onto the drive if I want to.  I can restore it to a partition or erase the drive and restore it to a single partition if I want to.  I believe the underlying backup software is Norton Ghost (?) (Not sure, but it's not some obscure backup format).

I don't know about running Vista and making incremental backups without a separate partition for that because I don't run Windows.  Ever.

---

### Post by Mark Phelps on 2009-07-15
> **az said:**
> ... and I can restore the Vista default install onto the drive if I want to.  I can restore it to a partition or erase the drive and restore it to a single partition if I want to.  I believe the underlying backup software is Norton Ghost (?) (Not sure, but it's not some obscure backup format).

You sure that you can restore?  The "obscure format" is likely to be a MS-format "image" file that the vendor used to install Vista on your machine.  If you removed that, unless you have a set of recovery CDs that include that image, you're NOT going to be able to restore Vista.

---

### Post by az on 2009-07-16
> **Mark Phelps said:**
> You sure that you can restore?  The "obscure format" is likely to be a MS-format "image" file that the vendor used to install Vista on your machine.  If you removed that, unless you have a set of recovery CDs that include that image, you're NOT going to be able to restore Vista.

I did not have an image on the partition.  The Acer Recovery utility created two DVD'S which are bootable and will write the OS back to a blank drive.

Obviously, if you don't have that, then you should not delete your only way to reinstall The OS.

---

