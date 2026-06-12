---
title: "Errr, Vista stuffed my filesystem"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by jimoz on 2008-03-23
Sorry, this isn't really a bug as such, just wanted some advice.

I run a dual boot system, Vista and Ubuntu Gutsy (I only use Vista because Photoshop CS3 and AnyDVD wont work on Linux... hint hint). I have an external USB 500GB hardrive (NTFS) with mpegs etc, and an internal 120GB, with three partitions (half Windows, half Ubuntu, and swap).

I started Ubuntu, and none of my hard drives were identified. The devices were listed under /dev, but nothing was listed under /mount, and only sda1 and sda2 were listed under /media... and both sda1 and 2 were empty. dmesg spit out several IO errors (sorry, didnt copy it down at the time). I then restarted Ubuntu to no effect.

I then restarted Vista. "Windows was not shut down properly... etc etc". Everything worked fine, and when I restarted Ubuntu afterwards everything was fine. I used to have a driver for Windows to access my ext3 partition which worked fine, but the first time I tried it Vista crashed a couple of hours later prompting Ubuntu to do the whole error check thing. I removed the driver straight after, so Windows shouldn't have any way to access the Ubuntu partition.

I'm relatively new to Ubuntu, but do know my way around a little.

What I'm asking is: How does a Vista crash somehow manage to stop Ubuntu from reading (or at least identifying) any hard drives at all?

---

### Post by schiznik on 2008-03-23
Its more likely to have been ntfs than vista. ntfs has a failed fsck flag of some sort that needed to be reset by booting into windows.

---

### Post by Sef on 2008-03-23
> (I only use Vista because Photoshop CS3 and AnyDVD wont work on Linux... hint hint).

Write to Adobe and Slyfox asking them to port their software to GNU/Linux, and specifically Ubuntu Linux.

---

### Post by dacorr on 2008-03-23
Windows also locks the NTFS file system when it boots it or you mount it as USB and if its not Safely Removed or shut down the lock is still in place preventing ubuntu to mount NTFS.

Dacorr

---

### Post by articpenguin on 2008-03-24
what windoze does with ntfs it sets a flag on it at boot saying needs recovery or sumthing. So if it was uncleanly unmount chkdsk would run the ntfs logfile or sumthing.

If you plug it in to linux after a unclean mount in windows ntfs will refuse to mount in linux because linux dosent know how to run the logfile.

---

### Post by prshah on 2008-03-24
> **jimoz said:**
> 
I then restarted Vista. "Windows was not shut down properly... etc etc". Everything worked fine, and when I restarted Ubuntu afterwards everything was fine. I used to have a driver for Windows to access my ext3 partition which worked fine, but the first time I tried it Vista crashed a couple of hours later prompting Ubuntu to do the whole error check thing. I removed the driver straight after, so Windows shouldn't have any way to access the Ubuntu partition.

You can setup the driver to give ro (read only) access to your ubuntu partitions. That way there is no chance of it damaging the filesystem, but you still have access to your linux data.

[/QUOTE]What I'm asking is: How does a Vista crash somehow manage to stop Ubuntu from reading (or at least identifying) any hard drives at all?[/QUOTE]

A "dirty" ntfs filesystem (not cleanly dismounted) will not be mounted in ubuntu. If you like, you can use the --force flag to mount the filesystem anyway, though it spits out dire warnings.

---

