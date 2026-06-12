---
title: "kernel update 19 Aug: hd problems"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by taj on 2005-09-07
I am running Ubuntu Hoary HP laptop version on a HP nx6110.
After the kernel update to 2.6.10-34.4-386 (more accurately: after 19 Aug, so i suppose it was the kernel update) I got heaps of problems with the harddrive.
One out of 2 times at reboot I got messages that the filesystem was not clean.
I got the following messages:
hda: status error: status=0x58
an fsck at (re)bootup resulted in lots of messages:
deleted inode ....... has zero dtime. Fix
Entry ..... in ...... has deleted/unused inode .....
free blocks count wrong

After fixing the same thing happened again and again. So I thought: broken HD or broken Ubuntu.

I tried, all giving the same problems:
update to kernel 2.6.11 (Ubuntu stuck at startup...)
update to kernel 2.6.10-34.4-686

So after some real frustration I installed Suse 9.3: no hd problems
I got impatient with slow Suse and I reinstalled ubuntu, no hd problem, apt-get upgrade: same problems a as above.
Finally I reinstalled Ubuntu (again...) and did NOT update anything and no problem has arised since (1 week). So now I run a slightly unsecure kernel.

I have googled around and have not found any similar problem. Could there be anything wrong with the kernel or one of the other security updates that were issued on or just before 19 Aug?

---

### Post by taj on 2005-09-08
Forgot to mention: I tried to use ReiserFS instead of Ext3 without improvement, so that factor can be ruled out as well

---

### Post by phen on 2005-09-08
i am using an 60gb nc6120, and i had to replace my harddisk. my harddisk refused to work every now and then and i had to run fsck from knoppix or bootup, to fix hundreds of inodes (same errors like you!). That is why I replaced the harddisk, and now everything works (at least since the last 3 days). if the problems reappear, i try to reinstall ubuntu like you did...

i hope your problems are gone now!

cheers,
kai

---

### Post by taj on 2005-09-12
Hmm, that is peculiar, because I also have the 60 GB HD (see below for details).
So, the question still is: is the problem due to a faulty HD, or due to a bug in (I suppose) the kernel update?

I still haven't got any problems since I have installed ubuntu again from CD, This time with ReiserFS, but I do not think that the FS is the problem. Just do NOT update the kernel!

$ dmesg | grep hda
Kernel command line: root=/dev/hda7 ro reboot=b quiet splash
    ide0: BM-DMA at 0x2580-0x2587, BIOS settings: hda: DMA, hdb: DMA
hda: FUJITSU MHT2060AH PL, ATA DISK drive
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
(etc)

---

### Post by mlord on 2005-09-14
If you don't mind reinstalling the O/S again, then you could try blanking the drive first, to give the onboard firmware a chance to correct any media problems:

Boot from CD (eg. KNOPPIX) and do "cat /dev/zero >/dev/hda", and go away for an hour or so until it fails by attempting to run past the end of the drive.

Then reinstall your O/S of choice.

But first.. even before all of that, install "smartmontools" and do "smartctl -a /dev/hda" and perhaps post the output here.  It should tell what the low-level drive problem is.

Cheers

---

### Post by taj on 2005-09-17
I would like to post log outputs, but since I have reinstalled hoary without updating the kernel (although I noticed that there was another kernel update since 19 Aug), I have not got any problems at all.
I need linux for work in the first place, and I cannot afford the hassle to try everything out again. It is a dual boot machine, and the same is true for XP, so no total cleaning of the drive possible.
I mainly wonder if the problems were due to ubuntu or the HD. The first seems the most likely now. I'll keep an eye on it and as soon I run into the same trouble I'll post the output.

---

