---
title: "Just installed but can't Update"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by backfour94 on 2009-07-14
Hi I've just installed jaunty using all the defaults in terms of partition size.

But when I try to run the first Update manager I get told that there isn't enough space.

I've read some other posts and the result of the df -h is:

steve@connor-tosh:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.1G   87M  97% /
tmpfs                 468M     0  468M   0% /lib/init/rw
varrun                468M  112K  468M   1% /var/run
varlock               468M     0  468M   0% /var/lock
udev                  468M  152K  468M   1% /dev
tmpfs                 468M  524K  468M   1% /dev/shm
lrm                   468M  2.4M  466M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda3              69G  4.7G   65G   7% /media/Data

so I'm not sure what I'm supposed to do now.  I've had a play with increasing the partition size but just got myself confused.  As I'm new to this I have no idea what can and can't be removed.  

Also, why didn't the installation set the root large enough?

Thanks for any help.

---

### Post by ptn107 on 2009-07-14
> **backfour94 said:**
> 
/dev/sda5             2.3G  2.1G   87M  97% /


Your Ubuntu OS partition is 97% full.  Ubuntu does not have enough room.

---

### Post by ajgreeny on 2009-07-14
You may need to start again, but before that, tell us what you actually did to install with "all the defaults".

Is this a completely empty disk or do you already have windows on it and you are double booting?  I suspect you have windows and therefore need to know how your disk partitioning is arranged.   I think you may not have understood the partitioning part of the installation, and certainly 2.3GB root is nowhere near enough for a running ubuntu system.  However it may be easy to reduce the size of your data partition and add that space to your root partition.

Boot to ubuntu and run ```
sudo fdisk -l
``` in terminal and copy the output back here.  This will list all your partitions with their sizes and the file system type on them so will give us a better idea of what you have now.

Don't despair, even if you do need to reinstall, it is only a half hour job, and once we know what happened first time, we can put you right next time.

---

### Post by backfour94 on 2009-07-16
Thanks.

When I insalled I'm pretty certain that I just said OK to all the prompts.  Of course I may have pressed something I shouldn't have done but I don't think so.

Yes it's set up as a dual boot with Vista.


Here's the output.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef3fe0d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9900    77981696    7  HPFS/NTFS
/dev/sda3            9901       18876    72099720    7  HPFS/NTFS
/dev/sda4           19133       19457     2610562+   5  Extended
/dev/sda5           19133       19435     2433816   83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris

---

### Post by backfour94 on 2009-07-18
Got around this by re-installing., reducing the Vista Data partition and letting Ubuntu take the rest.

---

