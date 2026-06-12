---
title: "How to mount HDD?"
date: 2015-06-18
forum: Hardware
---

### Post by Ali_Ashal on 2015-06-18
I installed Xubuntu 12 on my old laptop and everything was running perfectly until I thought to access my HDD. After searching everywhere all I could see is my 'Home' folder which was 13.5 GB. Where is the rest of my space on my 20GB HDD? There was no important data though, still, where is my rest of HDD gone, and secondly, can I repartition it?

---

### Post by Ali_Ashal on 2015-06-18
Here is my fdisk -l
> Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00049f9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    34910207    17454080   83  Linux
/dev/sda2        34912254    39069695     2078721    5  Extended
/dev/sda5        34912256    39069695     2078720   82  Linux swap / Solaris



---

### Post by ajgreeny on 2015-06-18
I don't understand exactly what you mean.

When you open the file manager it opens by default in your home but you should be able to move up in the file system by using Alt+Up two times to get you to the main filesystem.

To see more detail of your partitions and some of the virtual filesystems in your OS run terminal command ```
df -hT
``` which will give an output similar to ```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda2      ext4       20G  8.7G  9.5G  48% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  3.8G  4.0K  3.8G   1% /dev
tmpfs          tmpfs     769M  1.3M  767M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.8G  276K  3.8G   1% /run/shm
none           tmpfs     100M   32K  100M   1% /run/user
/dev/sda1      vfat      197M  3.4M  194M   2% /boot/efi
/dev/sda4      ext4      890G  340G  505G  41% /home
```
To answer your final query, yes, you can repartition it but only using a live OS, but at this stage it is not something I would recommend, nor would it help you, I suspect, with only 20GB available in total.

By the way, is that 20GB disk the only HDD in the machine?

---

### Post by Ali_Ashal on 2015-06-19
This is the result of df -hT:
> 
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       17G  2.2G   14G    14%  /
udev           devtmpfs  992M  4.0K  992M  1%   /dev
tmpfs          tmpfs     400M  732K  399M   1%   /run
none           tmpfs     5.0M     0     5.0M     0%  /run/lock
none           tmpfs     999M   84K  999M    1%  /run/shm
/dev/sda1      ext4       17G  2.2G   14G  14% /media/part1


and yes, the only HDD in this laptop is 20GB
Secondly, when I see the properties of home folder, it says 13.4 GB available, and the /dev/sda1 partition is the same (imo) which I managed to mount in Media in a folder I made named 'Part1'.
I did not made any partitions myself, I had let the installer replace windows with xubuntu, so that means I have no partitions now, just a single '/' partition which will be erased when I will update/reinstall OS. Should I reinstall Xubuntu with manual partitioning because I haven't installed/downloaded anything uptill now?
Thanks for the help.

---

### Post by Bucky Ball on 2015-06-19
Install Gparted, launch it and have a look at how your hard drive is partitioned. If there's free space, you can create partitions using it.

I'd give 18Gb to the install and 2Gb for /swap and keep the personal data (/home) on an external drive, but depends what you're intending to do with it ...

---

### Post by Dennis N on 2015-06-19
You let Ubuntu use the entire 20gB. After erasing your disk, the installer created primary partition #1, an extended partition #2 entirely filled with logical partition #5 which is used for swap. All disk space is used by these.

After the installation and whatever you have subsequently added, 13.4 gB remains available for use by you and the OS out of the 20 you started with. All of it is in partition 1 (sda1). Nothing unusual, and you can't add any more partitions without resizing sda1. 

What you are mounting are filesystems on the HDD, and in this case your only usable filesystem /dev/sda1 is mounted at startup. So you need do nothing more. I hope that clears up some of the issues.

Post #4:
The two mounts of filesystem /dev/sda1 at different mount points should not be done unless you have some special reason.

---

### Post by ajgreeny on 2015-06-19
I think you will find that you have only one main partition in which your home folder is loc
fated.

Many users create a separate /home or /data partition but with only 20GB HDD this would be a bit pointless.

I think you are seeing exactly what I expect to see, but it would be interesting to see how large your swap partition is from command **sudo parted -l**

---

### Post by Dennis N on 2015-06-19
> it would be interesting to see how large your swap partition is
A back-of-the-envelope calculation with rounded numbers tells us Ubuntu installer has set swap size at 1 gB (to nearest gB).

---

### Post by Ali_Ashal on 2015-06-19
I will be installing Lubuntu 14 tomorrow, can anyone guide me how to avoid the mistake I made this time, I mean that can anyone guide me how to use manual partitioning this time without messing things up? And the suitable size of partitions?

---

### Post by Bashing-om on 2015-06-19
Ali_Ashal; Hello;

Pardon me, but are you not making a mountain out of a mole hill ?
With such a small hard drive, The default standard install I expect will serve your purpose just fine - "erase disk and install ubuntu".
> 
can anyone guide me how to avoid the mistake I made this time

What is the mistake you think you have made ?
Else if there is some other object in mind than that of the standard install, please specify . There are many paths to an end .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Ali_Ashal on 2015-06-19
I want to partition disk like it was on windows. A partition with ubuntu on it, a /home partition, and a partition for saving important files (Word Docs etc.)
I don't use this laptop for any major purposes, but I only save my school work there. Will /home partition get erased after upgrade?

---

### Post by Bucky Ball on 2015-06-19
I'd let Ubuntu install automatically, as suggested by Bashing-om, install Gparted, and have a look at how your disk has been set up.

If you want to change it, boot from the Lubuntu install media> Try Lubuntu> launch Gparted> resize partitions. 

It's fairly self-evident once you get that far. Right click the partition> choose resize> move the resize bar. When you're finished hit 'Apply'. Reboot from the hard drive.

* Just read your last post. Install Lubuntu> Hit 'Something Else' when you get to that part (see [here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352"))> make / 8Gb, 10Gb for /home and /swap 2Gb at the end. With a disk that size that is the best you are going to get with a Ubuntu flavour ...

Once installed and setup, you could have a look in Gparted and see how full the 8Gb / partition is. If it is using 5Gb of the 8Gb, guess you could boot from the install media, shrink it and expand /home ...

---

### Post by Dennis N on 2015-06-19
> **Ali_Ashal said:**
> I want to partition disk like it was on windows. A partition with ubuntu on it, a /home partition, and a partition for saving important files (Word Docs etc.)
You are talking about three partitions - root, home, data. That's not efficient for such a small disk.The problem is getting the sizes of the root, home, and data partitions optimal. Sooner or later, you will find one of them is running out of space, and another has too much space, and you can't adjust them. Better to have everything in one partition and have space dynamically allocated as needed. And separating content is what folders are for.

---

### Post by Bucky Ball on 2015-06-19
> **Dennis N said:**
> You are talking about three partitions - root, home, data. That's not efficient for such a small disk.The problem is getting the sizes of the root, home, and data partitions optimal. Sooner or later, you will find one of them is running out of space, and another has too much space, and you can't adjust them. Better to have everything in one partition and have space dynamically allocated as needed. And separating content is what folders are for.

Don't forget a 2Gb /swap. You can make a /swap directory, but beyond the scope of this thread.

There are some good reasons for having a separate /home, even on a small disk like this (I'm guessing it is a 20Gb eMMC card or something). I have a couple of Xubuntu installs using under 8Gb with a medium amount of stuff installed. A mini install and adding what you want would be a better option. A vanilla mini install with very little added is 3 - 5Gb. A vanilla Lubuntu would probably swing in around 5Gb, 6Gb with 1Gb headroom ... don't quote me. :)

---

### Post by Dennis N on 2015-06-19
> Don't forget a 2Gb /swap.
Of course he needs a swap too. My comment was about having the three partitions Ali_Ashai mentioned he wanted, and why this arrangement will be an inefficient use of disk space.

---

### Post by Bashing-om on 2015-06-19
Ali_Ashal; Further more;


In addition to what Bucky Ball and Dennis advise; this :
An example of a "minimal install"
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  3.0G  1.5G  68% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  744K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   25M  2.0G   2% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2       9.5G  2.5G  6.6G  28% /home
/dev/sda8       4.7G  981M  3.5G  22% /var
sysop@1404mini:~$

```
The partition space is very tight, and one has to stay on top of things. I do keep an eye on things, and this partitioning set up works well - for my use case ! - .
Caveat: I do have some little knowledge; and I do exercise some small amount of ability in system administration. In the event of running out of disk space one will be in deep trouble real quick .
If you do partition manually and set up something like the above, The learning curve in system administration is going to get real steep real quick. If you are in for this learning experience; well, Go for it ! We are all here to help you along on this curve of learning. On this curve, you must expect breakage, and learn what it takes to "fix" .

[INDENT][INDENT]that is but only my opinion
[/INDENT][/INDENT]

---

### Post by Ali_Ashal on 2015-06-20
Ok thanks guys, and secondly, will my /home partition get erased when I'll upgrade?

---

### Post by Bucky Ball on 2015-06-20
No. Not with a net upgrade. If you do a clean install, then you can keep it or wipe it. Up to you. There is LOTS of info available online about upgrading both ways.

---

### Post by Dennis N on 2015-06-20
> will my /home partition get erased when I'll upgrade? 

If you upgrade in the future to a newer version (using the software updater), as opposed to doing a fresh install, your personal files are supposed to be left intact - they should not be deleted in either case: (1) normal home folder in your root partition, or (2) home folder on a separate partition. But I would back them up before any upgrading to be safe. 

Good luck with your new installation.

---

