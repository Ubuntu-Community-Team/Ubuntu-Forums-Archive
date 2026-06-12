---
title: "HELP! Cannot access data on partitions"
date: 2009-03-24
forum: Hardware
---

### Post by joba1 on 2009-03-24
Hi,

I'm in desperate need for help! Ubuntu cannot access any of my files!


I think it might be useful to provide some background info first:

I have a Toshiba P300 16A which ships with Vista and a downgrade CD to XP Pro.
The laptop has 2 hard disks of 250 GB each.
When I got it I used the standard Vista utility to create 2 partitions, one 50 GB partition for the OS, and the rest for data. So Vista set up a RAID configuration and have partition D  on both HD1 and HD2.

I used the laptop for almost one year until I decided to reinstall XP from my original downgrade CD, just to kind of "lighten up" the system.
After reinstalling the OS I haven't been able to boot it because I get an error message saying "autochk program not found - skipping autocheck", then a blue screen and reboot...and it just kept doing this, even though I tried reinstalling 5 times.

Then a friend told I could run Ubuntu live from a CD, and access and backup my data. I tried, but unfortunately I still cannot access any data on my hard disks. When I try to open the D partition, which is where all my documents are, I get a message saying:
Cannot mount volume
and then something about the volume being "RAID/LDM but it wasn't set up yet"

Now I have installed Ubuntu 8.10 on partition C, so Windows is completely gone.

Partition editor does detect the presence of two distinct HDs, and it can see that there are now three partitions. It sees the Ubuntu partitions, but it is unable to identify partition D, it says "unknown file system".

What do I do?? 
I am terribly afraid of doing anything that might cause data loss on my D partition.

Any help on how to recover data or even solve the original XP problem will be hugely appreciated!!
THANX!

---

### Post by mal_conductor on 2009-03-29
Try testdisk and/or photorec.

These are my notes.

[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

