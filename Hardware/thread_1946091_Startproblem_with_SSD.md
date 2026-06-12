---
title: "Startproblem with SSD"
date: 2012-03-24
forum: Hardware
---

### Post by gnuser12 on 2012-03-24
Hello Users,
I've been using a SSD device since nearly one year. 
It is a G.SKILL Model=FM-25S2S-115GBPE, FwRev=4.2
I've installed U10.04 on it because the long term support.
In the beginning all things seems to be good.
Fast boot, fast programs ... 
But since ca. 3 months I have the issue with starting U10.04.
I fact sometimes I have to press up to 20 times on the Powerbutton to start U10.04.
Mostly if I start the system in the beginning of the day. 
The good thing is U10.04 starts always but the many tries are annoying 
But I have to say that I'm not been using trim since yesterday ;-) 
Furthermore important to say ist that if I reboot between short time for example in 2 minutes the system starts immediately.
Free drive space is ca. 16 percent.

What can I do?

Thanks

---

### Post by recluce on 2012-03-24
You may have more than one problem.

1.) Ubuntu 10.04 with the "stock" kernel does not support TRIM, even if you have it enabled in fstab. So your drive (at only 16% free space) will be out of empty cells - so every write is a sloooow overwrite operation. Let me know if you have a newer kernel installed and TRIM enabled if FSTAB. If not I will be happy to give you some pointers.

2.) The start-up failures: when EXACTLY does the system hang? During BIOS post, when trying to load GRUB or at some other point?

---

### Post by gnuser12 on 2012-03-26
Thanks for reply 
> **recluce said:**
> You may have more than one problem.

1.) Ubuntu 10.04 with the "stock" kernel does not support TRIM, even if you have it enabled in fstab. So your drive (at only 16% free space) will be out of empty cells - so every write is a sloooow overwrite operation. Let me know if you have a newer kernel installed and TRIM enabled if FSTAB. If not I will be happy to give you some pointers.[INDENT]I have used wiper.sh for trim 3 times
> wiper.sh --verbose --commit /dev/sda1
output 
fsmode2: fsmode=read-write
/: fstype=ext4
freesize = 16319604 KB, reserved = 163196 KB
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (16156408 KB).. 
Syncing disks.. 
Beginning TRIM operations..
get_trimlist=/sbin/hdparm --fibmap WIPER_TMPFILE.9359

/dev/sda:
trimming 3407872 sectors from 64 ranges
succeeded
trimming 3817469 sectors from 64 ranges
succeeded
trimming 3817473 sectors from 64 ranges
succeeded
trimming 3899394 sectors from 64 ranges
succeeded
trimming 3915776 sectors from 64 ranges
succeeded
trimming 3899392 sectors from 64 ranges
succeeded
trimming 3866624 sectors from 64 ranges
succeeded
trimming 3801085 sectors from 64 ranges
succeeded
trimming 1887731 sectors from 33 ranges
succeeded
Removing temporary file..
Syncing disks.. 
done
[/INDENT]2.) The start-up failures: when EXACTLY does the system hang? During BIOS post, when trying to load GRUB or at some other point?[INDENT]Start: I press the Power Button .. then the Notebook shows the Bios Logo
and at this point nothing is going on .. (The Harddrive LED shines steady)
so I hold the Power Button for several seconds and the Notebook goes off
then I go to Start ;-) 
and this repeats on and on until (The Harddrive LED blinks) and Ubuntu boots ...
[/INDENT]

---

### Post by recluce on 2012-03-27
> **gnuser12 said:**
> Thanks for reply 
[INDENT]Start: I press the Power Button .. then the Notebook shows the Bios Logo
and at this point nothing is going on .. (The Harddrive LED shines steady)
so I hold the Power Button for several seconds and the Notebook goes off
then I go to Start ;-) 
and this repeats on and on until (The Harddrive LED blinks) and Ubuntu boots ...
[/INDENT]

As to wiper.sh: sure, that works. But with a newer kernel, you can just add "DISCARD" to your fstab mount entries for ext3 or ext4 and file deletes release the disk space immediately and without the need for a wiper.

What you describe sounds like a hardware issue to me, since no OS or boot loader is active at this point. I would verify the issue by trying to boot this SSD in a different notebook, but if in doubt, I would return the drive as long as you still have a warranty on it!

---

### Post by Mark Phelps on 2012-03-29
Crucial recently admitted they had a problem with their M4 SSDs that only appeared after a certain number of hours of use.  Thus, new users did not see any problem.  They fixed it with a firmware upgrade.

Sounds like you might have a similar problem.

You should check the SDD manufacturer to see if they have any firmware upgrades -- or, at least, a forum where you can voice your concerns.

---

