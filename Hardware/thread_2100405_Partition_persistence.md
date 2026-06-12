---
title: "Partition persistence"
date: 2013-01-01
forum: Hardware
---

### Post by Faziri on 2013-01-01
Hiya

I've been reading some HowTos and other docs, but I just couldn't get a convincing answer to my problem.

I've currently got the following partitions on my HDD:
sda1: Windows RE
sda2: Win7
sda3-7: personal stuff
sda8-11: Ubuntu

The  Windows RE has become completely useless to me, so I'd like to delete  the RE partition (and perhaps move sda2 (Windows' C:) to the left and  then expand it).

What I'm wondering is: will this mess up the  numbering or not? I.e. will sda2 (and all the following partitions up to  11) keep its identity as sda2 or will it become sda1?
In other  words, are the numbers in "sd*x*" hard-coded into the partition  table or are they dynamically counted when the disk is connected?

I'm  just thinking that removing the first partition would cause a downwards  shift in all the following numbers, completely messing up all  sd*x* references.


Also: running update-grub is all  that's needed to keep everything working after (perhaps) altering sda2  (C:), right? Just need to remove the then invalid boot entry for WRE and  repair the relocated Win7 entry, Windows itself shouldn't care about  its physical location AFAIK. Or am I forgetting something there?

---

### Post by ahallubuntu on 2013-01-01
Here's another idea: instead of completely blowing away that first partition (is it really that large that you'll gain a lot of space?), try shrinking it to be as small as possible - a few MB, as small as is allowed.  Then the numbering won't change.  You may not even need to update Grub.

I'm always cautious about erasing stuff I might need later, just to make something work.  I'd probably make a copy of the Windows RE (recovery?) partition before erasing it completely, just in case I need it back.  Sometimes Windows 7 makes a separate small boot loader partition, too - make sure that isn't what you are deleting.  You could make a copy of the partition to another device with Clonezilla.  (dd would work too but is not very efficient unless the partition is almost full of data.)

---

### Post by Faziri on 2013-01-01
> **ahallubuntu said:**
> ~snip~

I need the space, it can't be shrunk, I won't be needing the Win Recovery Environment and I've already moved the Windows bootloader from its separate partition to C: itself.
I know what I'm doing, I'm just not sure about one or two little details like that partition numbering. It seems more logical to me that the numbers are hard-coded, but that's only a best estimate.

I also want to cut the RE out of my system because it's disfunctional: the full C: image is somehow not working anymore after having used it once and the partial repair options' files are so outdated that they only cause more problems than they fix. For some reason it's also configured to mess up the boot chain and wipe out GRUB the moment it's booted, another thing I'm getting a bit sick of.

Emptying it first and then just shrinking it would technically do the job, but I hate to leave a mess like that in my system if it's not necessary.

So my question still stands: does it affect the numbering (dynamically counted) or are the numbers hard-coded on them/on the partition table?

---

### Post by ahallubuntu on 2013-01-01
I wasn't really sure of the answer so while re-formatting a spare drive, I deleted the first partition /dev/sdc1 on it.  The other partition numbers did not change, even after unplugged the drive and plugged it back in (USB enclosured).  The old numbers remained.  When I created two new partition in the empty space left over from the old partition, the first one got sdc1, the second got sdc3 (previously unused) and the others (starting with sdc2) still had the same numbers as before.

---

### Post by Cheesehead on 2013-01-01
For several years now, the standard has been to use UUID instead of /dev/sdx or /dev/hdx assignments. The /dev/* assignments are still supported, and the /dev/* devices still exist. Problems crop up if /dev/xxx gets reassigned by the kernel, and partions can indeed be assigned different a/b/c values by the system at boot. Rare, but does happen.

Ubuntu and Debian use the /etc/fstab file to track those UUID assignments, so look in that file for any old /dev assignments, and feel free to update them if you need to. Best practice is to backup the old /etc/fstab to /etc/~fstab before editing.

See the UUIDs of partitions with the [FONT="Courier New"]sudo blkid[/FONT] command.

Some advanced users have custom mounting scripts for whatever reason, though most need for those has been replaced by /etc/fstab and gvfs. If you do happen to have one, be sure to update it to UUIDs.

If you move data between partitions, be sure to update the UUIDs in /etc/fstab.

---

### Post by Faziri on 2013-01-02
> **ahallubuntu said:**
> ~snip~
Great answer, thanks! :)
I didn't (don't) have any spare disks to test it on myself...

Cheesehead, I know sdx references are discouraged, but they are still useful from time to time... I think I use UUIDs in fstab and other critical places, but there's always the chance of something being an sdx reference so I'd rather not take my chances.

---

