---
title: "Hard drive file system issues"
date: 2010-01-17
forum: Hardware
---

### Post by buddist7 on 2010-01-17
I've been getting weird errors and missing text/images/etc that seemed like my hard drive was dying.  Ubuntu would stop functioning and I would reboot and have to run fsck on the partition.  It would clean up inode issues and illegal blocks and work for a while.

This became more and more frequent so I ran the hitachi hard drive test and it gave me a "disposition code 0X72" which indicates a drive is going to fail. 

I replaced the drive and not more than a week later I am getting the same errors and symptoms with the new drive.  Initially I copied the whole disk to the new disk with dd_rescue.  So I reinstalled ubuntu and I am still having this problem.  The errors are attached.

I can't decide if this is an ubuntu issue, another hard drive issue, or something wrong with my motherboard or power supply.  I am having no other issues, and I find it hard to believe the new drive is already dying unless ubuntu is killing it some how.

---

### Post by _Q_ on 2010-01-17
Here's another similar scenario:

Using Ubuntu Hardy 8.04.3 (with all latest updates)
on HP Compaq laptop
with dm-crypt (divided the HDD with LVM), ext3 partitions

It was all ok at first, but then errors began to increase..
Just today I couldn't logon to the GNOME session for some reason...
Than after checking the .xsession-errors, I found out I have to reinstall the libglib package (becasue it's probably corrupt), and it all works fine now, after the package reinstallation...

Another (frequent) unusual sceanrio...
If I calculate a md5 hash for three or four big files... and then re-calculate again after .. 15 minutes for an example, one file returns a different md5...

Also, every 10 days, if I do a fsck of the LVM partitions, they always return alot of invalid blocks reports or such...

Is this a HDD hardware problem?
I don't have any diagnostics for HDD, or I couldn't find any... (HP Compaq 6820s)..
Ideas? :)

---

### Post by buddist7 on 2010-01-17
Well given your use of disc encrpytion I would run a mem-test and check for bad blocks.  That might explain the 15 minute interval md5 differences.

---

### Post by _Q_ on 2010-01-17
Yes, good idea! :)
But I already tried that, and it seems memory is ok.. (I guess 30 minutes of mem-test is enough...?)

---

### Post by buddist7 on 2010-01-17
Yea all my bad memory incidents were apparent right away.  You could try running it overnight for lack of a better idea.  I'd download a disk fitness checker and do the more in-depth/advanced check.
[http://www.tacktech.com/display.cfm?ttid=287]("http://www.tacktech.com/display.cfm?ttid=287")

---

### Post by _Q_ on 2010-01-17
My disk is SATA... and it seems there are only ATA/IDE diagnostic tools for Fujitsu HDDs... :/

---

### Post by buddist7 on 2010-01-17
they should work

---

### Post by _Q_ on 2010-01-17
Also, they are all for Windows...
and no disks appear on the list when trying to run with WINE....

---

