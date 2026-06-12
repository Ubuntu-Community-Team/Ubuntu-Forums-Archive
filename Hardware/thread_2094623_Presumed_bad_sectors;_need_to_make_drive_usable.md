---
title: "Presumed bad sectors; need to make drive usable"
date: 2012-12-14
forum: Hardware
---

### Post by Paddy Landau on 2012-12-14
I have an external USB Seagate 1Tb hard drive with five partitions. One of the partitions holds Ubuntu.

Recently, I had a problem with the Ubuntu partition, so I deleted the partition, recreated it, reformatted it and reinstalled Ubuntu. But today, I cannot mount that partition, and even [FONT=Lucida Console]fsck[/FONT] on that partition hangs; I had to kill [FONT=Lucida Console]fsck[/FONT].

I suspect that the partition has bad sectors that the SMART utility is not picking up.

How can I check the partition for bad sectors in such a way that they are marked unusable (so that the rest of the partition can be used)? Or, have I misdiagnosed and should I do something else?

There is **no important data** on that partition that I need, so I am happy to delete the partition if required. I also have a **full backup of data** on the rest of the drive, so if I have to reformat the entire drive, that too is OK.

TIA

---

### Post by Grenage on 2012-12-14
To be honest I thought that all modern drives automatically locked out bad sectors, and continued to do so once their backup supply was exhausted.  The only time I've had ongoing issues, are when new bad sectors are created (bad sectors are rarely a one-off, and just get worse) - in such cases I've always ditched the drive.

---

### Post by Paddy Landau on 2012-12-14
> **Grenage said:**
> … I thought that all modern drives automatically locked out bad sectors…
Yes, I though so too. However, I am no expert when it comes to hardware, so I was hoping that there was something to fix this.

---

### Post by Grenage on 2012-12-14
I believe that a full format would flag and block bad sectors, but it obviously wont be able to tell you about any that occur after the fact.  fsck should be able to, with regular scans.

---

### Post by Paddy Landau on 2012-12-14
> **Grenage said:**
> I believe that a full format would flag and block bad sectors, but it obviously wont be able to tell you about any that occur after the fact.  fsck should be able to, with regular scans.
I have just deleted and recreated the partition, and formatted. The format takes mere seconds, so it cannot be scanning the disk.

Likewise, [FONT=Lucida Console]fsck[/FONT] seems to check only the allocation of files rather than the files themselves. It took mere seconds on the reformatted (empty) partition.

You mention a "full format". Is that something that writes to every sector on the partition? If so, how do I do it?

Alternatively, perhaps I need to use some program that just writes a random string to every sector. That may alert SMART to some problem and prompt it to fix it.

I have seen the following warnings on the SMART report:

[LIST]
[*]8,160 reallocated sectors
[*]197 current pending sectors
[/LIST]

---

### Post by Grenage on 2012-12-14
That's right; most formats done are usually 'quick' formats.  You know them when you do them - because they take bloody ages.

mkfs.ext4 has a flag for checking bad blocks during the format:

> -c     Check the device for bad blocks before creating the file system.  If this option is specified twice, then a slower read-write test is used instead  of a fast read-only test.

So, *-c* is what you want!

---

### Post by Paddy Landau on 2012-12-14
I think that I have discovered what to do.

[FONT=Lucida Console]fsck.ext4[/FONT] has two options: [FONT=Lucida Console]-c[/FONT], which if doubled performs a non-destructive read-write test, and [FONT=Lucida Console]-k[/FONT], which does not destroy old information about bad sectors. (It uses the [FONT=Lucida Console]badblocks[/FONT] application.)

I have been running the following command for 35 minutes (it is only 35% complete), but it has found four bad sectors.

```
sudo fsck -CMfcck /dev/sdb8
```Well, I presume it is four bad sectors, because the display shows "[FONT=Lucida Console](4/0/0 errors)[/FONT]". I do not know quite what  that means, but the scan did at one stage appear to hang before it  showed the first error.

(Do you know where to find a description of the output? It's not in the [FONT=Lucida Console]badblocks[/FONT] manual.)

I think that I can mark this as solved, now.

EDIT: Sorry, I missed your last post!

---

### Post by Grenage on 2012-12-14
Alas, I do not, but I'm willing to bet that the verbose (-v) flag will give you what you want.

---

### Post by dannyboy79 on 2012-12-14
i'd just get rid of the drive, playing with fire trying to use a dieing drive

---

### Post by Paddy Landau on 2012-12-14
> **dannyboy79 said:**
> i'd just get rid of the drive, playing with fire trying to use a dieing drive
Well, it seems to be with isolated areas, and fortunately it is only a backup drive. I take your point, but if it does fail, I can order a new one quickly. As I don't have plenty of money, I'd like to wait until it actually does die!

The scan is still running (it's slow, which I expected). I'll let you know the results once it has finished.

Thank you Grenage and dannyboy79 for your help.

---

### Post by Grenage on 2012-12-14
Anytime, and on a final note, don't forget to check the warranty of the drive.  Might still be valid, and this could all be a moot point. ^^

---

### Post by Paddy Landau on 2012-12-14
> **Grenage said:**
> Anytime, and on a final note, don't forget to check the warranty of the drive.  Might still be valid, and this could all be a moot point. ^^
LOL, unfortunately the drive's warranty expired last year; but thanks for the reminder!

---

