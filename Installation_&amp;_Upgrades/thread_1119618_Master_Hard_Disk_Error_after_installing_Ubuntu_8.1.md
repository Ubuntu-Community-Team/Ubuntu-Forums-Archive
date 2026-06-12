---
title: "Master Hard Disk Error after installing Ubuntu 8.10 - hard disk died"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by kojakojakoja on 2009-04-08
Hi people.

I'm a newbe to Linux and I need help.
Here is my problem...


In short: **after installing Ubuntu on one WD 500 GB hard disk and after making mistake and pasting wrong code into Terminal:**

> 
$ sudo su

$grub
$find /boot/grub/stage1

the command shows where grub is installed, e.g. (hd1,1) 

$root (hd1,1)
$setup (hd1)
$quit


...**my OTHER WD 500 GB hard disk that was also in the system (I guess it was "hd1") - died.**

(The problem must be, I guess, I typed wrong code: "hd_1,1_" instead of "hd_0,0_".)


500 GB (NTFS) of data was on that *other* _(non-Ubuntu)_ hard disk, and now I can not access it anymore. **While booting, system gives "Hard Disk Error" warning and stops.**


One again: I installed Ubuntu od one hard disk and at the end of instalation I pasted wrong code for GRUB, giving address of another hard disk. Now that other hard disk has error and will not work.


Can anybody help, please? I'd appreciate it very much!
Thanks.


Detailed explanation follows...

---

### Post by kojakojakoja on 2009-04-08
[COLOR="Red"]**_DETAILED EXPLANATION:_**[/COLOR]





1. Had Ubuntu Live (8.10) running and was so excited that I decided to install it to hard disk (at midnight).


2. Read 2 tutorials, followed them, and everything went fine.

On one 500 GB drive (Western Digital, WDC WD5000AAKS) I deleted the first (and smaller) partition (32 GB) and made 3 new partitions: "/" (25 GB, ext3), "swap" (3 GB), "home" (4 GB, ext3). The rest (about 450 GB) was NTFS, filled with data.


3. Tutorial (language is not English, but pictures are important) is here: [Tutorial with pictures]("http://www.ubuntu-rs.org/wiki/Instalacija_Ubuntu-a_8.10").


4. My problems started with or after last 2 steps of instalation:

a) I clicked ADVANCED button shown [here]("http://www.ubuntu-rs.org/wiki/Slika:Instubu022.jpg") or [here]("http://www.ubuntu-rs.org/w/images/0/0c/Instubu022.jpg"), and...

b) ...before I would click RESTART NOW (shown [here]("http://www.ubuntu-rs.org/w/images/thumb/c/c6/Instubu024.jpg/180px-Instubu024.jpg") and [here]("http://www.ubuntu-rs.org/w/images/c/c6/Instubu024.jpg") ...

...I decided NOT TO WAIT any longer - since it was already late night and I wanted to "do it right" the first time and not to reboot several times (like with Windows) - so instead of only restarting PC (as offered at the end of instalation), I did the following:

I copied the code from here: [putting GRUB in place where it belongs]("http://www.ubuntu-rs.org/wiki/Vracanje_grub-a").


Why did I do it? It's not that much important, but - for the curious - I thought I would prevent rebooting or something, I thought I was very smart, and it was late and I was not thinking rationaly.

> 
$ sudo su

$grub
$find /boot/grub/stage1

the command shows where grub is installed, e.g. (hd1,1) 

$root (hd1,1)
$setup (hd1)
$quit


The problem is I typed wrong code: "hd1,1" instead of "hd0,0".
(I simply copied the "hd1,1" code from tutorial, even thought the answer I received from Terminal was "hd0,0".)


After that I restarted PC.


To my surprize WINDOWS booted - not Ubuntu as I expected, and I saw ONE HARD DISK LESS in my list of hard drives (actually two partitions less, both on the same hard disk).

Started Partition Magic and receiven info that one hard drive has "bad partiton" (I'm almost sure that's what I read).

At that time I thought the problem was with the hard drive where I installed Ubuntu (500 GB hard drive that had 3 new Linux partitons and one 450 GB NTFS partiton.

I rebooted ... and rebooted ... and rebooted ... and started receiving "Third Masted Hard Disk Error".

After disconnecting one by one disks, I realized the problem is not with the hard drive I installed Ubuntu on, but with _other_ WD 500 GB hard drive (I have 2 same disks in PC).

It seems it is the one where wrong code pointed to (hd1,1).
(Not sure, but there is simply no other explanation.)

So now my PC refuses to boot if this hard is connected to system; it stops at the beginning of boot process and gives information that there is a "Hard Disk Error", or says

Ultra DMA Mode-5, S.M.A.R.T. Capable but Disabled

or, sometimes, it boots Hiren Boot.

Hiren Boot, or [these WD tools]("http://support.wdc.com/product/download.asp?groupid=606&sid=3&lang=en"), gave me info that disc is disconnected (the best), or there is no disc at all (worst scenario).


I can not access my WD 500 GB hard drive that has 2 or 3 NTFS partitions that are filled with data. No WIndows was installed on that disc, only data.

---

