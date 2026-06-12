---
title: "Error 16"
date: 2008-10-05
forum: General Help
---

### Post by mylifedrive on 2008-10-05
I have a Toshiba satellite laptop without a hard drive, and without windows. I run kubuntu linux of a 4GB thumb drive. Today I started up and it Says Grub loading, then error 16. I don't hae any windows disks or anything, but I do have the kubuntu and ubuntu live CD's and they both work. When I try to reinstall it doesn't recognize my flash drive. I would hate to lose all my settings. what should I do? :confused:

---

### Post by Atsuko on 2008-10-05
Read here see if any help?
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64928](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64928)

---

### Post by mylifedrive on 2008-10-05
Hmm, no I need a direct response to my own problem. That person could use windows to fix the problem- I can't.

---

### Post by caljohnsmith on 2008-10-05
From the Grub manual:
> **Error 16** : Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.
So could be a hardware problem with your USB drive. How about posting:
```
sudo fdisk -lu
```
while you have the USB drive plugged in, and we can work from there.

---

### Post by mylifedrive on 2008-10-05
I get this:

```
Disk /dev/sda: 504 MB, 504365056 bytes
16 heads, 32 sectors/track, 1924 cylinders, total 985088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32      985087      492528    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$

```

---

### Post by caljohnsmith on 2008-10-05
> **mylifedrive said:**
> I get this:

```
Disk /dev/sda: 504 MB, 504365056 bytes
16 heads, 32 sectors/track, 1924 cylinders, total 985088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32      985087      492528    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$

```
So what is drive sda? sda is only 500 MB, while you said your Kubuntu drive is 4 GB. If fdisk doesn't see your Kubuntu thumb drive at all, unfortunately it might be dead. I would try plugging your Kubuntu thumb drive into another computer and see if the computer will recognize it.

---

### Post by mylifedrive on 2008-10-05
oops. Wrong flash drive :oops:

```
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xffff890e of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7373834     3686886   83  Linux
/dev/sda2         7373835     7823654      224910    5  Extended
/dev/sda5         7670159   282236046   137282944   e4  SpeedStor
ubuntu@ubuntu:~$
```

---

### Post by caljohnsmith on 2008-10-05
> **mylifedrive said:**
> oops. Wrong flash drive :oops:

```
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xffff890e of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7373834     3686886   83  Linux
/dev/sda2         7373835     [COLOR="Red"]7823654[/COLOR]      224910    5  Extended
/dev/sda5         [COLOR="Red"]7670159[/COLOR]   282236046   137282944   e4  SpeedStor
ubuntu@ubuntu:~$
```
Which drive gave you all those warnings above? Also, what is sda5? It looks like your thumb drive's partition table is really messed up, because sda5 starts within the sda2 extended partition, but sda5 ends clearly outside of the sda2 partition; also, sda5's end point is at a cylinder that is beyond the drive's total cylinders. I'm guessing sda5 was your swap partition, is that true?

Your best bet at this point I think is to try and recover your partition table using testdisk. While you are in the Ubuntu Live CD, first enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. 

Then do "proceed", "N" to search for Vista partitions, and then post the output of the screen showing all the listed partitions.

---

### Post by mylifedrive on 2008-10-05
I will try this out. I simply installed Kubuntu once, using just the normal install on the Live cd- chose an option for my flash drive, I believe it was something like "Guided- use entire disk". I'm just a GUI user, so I don't know much about code or that stuff, I will just follow what you say.

I don't know what "Vista partitions" is- I don't think you are referring to an os, because I phisically have No hard drive- there is just an empty hole there.

---

### Post by mylifedrive on 2008-10-06
I get this when I plug in my flash drive using a Ubuntu live CD

[[IMG]http://img293.imageshack.us/img293/1710/screenshotgnomemounthz8.th.png[/IMG]](http://img293.imageshack.us/my.php?image=screenshotgnomemounthz8.png)[[IMG]http://img293.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by caljohnsmith on 2008-10-06
That's OK, just don't let Ubuntu mount the flash drive when you plug it in, if it gives you that option. How did you previously get that "fdisk" output showing your flash drive? If fdisk shows your flash drive, you can use testdisk to try and repair its partition table.

---

### Post by mylifedrive on 2008-10-06
Following the first part of your instructions I get this:

```
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found
ubuntu@ubuntu:~$ 


```

---

### Post by mylifedrive on 2008-10-06
before I was using Kubuntu. Kubuntu recognizes the lash drive, ubuntu doesn't.

---

### Post by caljohnsmith on 2008-10-06
You have to have an internet connection from your Live CD in order to download testdisk from the repositories. If you can't get an internet connection while using your Live CD, if you can use another computer you could download the [SystemRescueCD]("http://www.sysresccd.org/") and run testdisk from that CD, since it comes with testdisk.

---

### Post by mylifedrive on 2008-10-06
I've actually been posting all this using the live CD. I tried it again, as you can see, I am connected to the net, but I still got the same results.

---

### Post by caljohnsmith on 2008-10-06
Did you make sure you have all your repositories enabled? You could just download the testdisk package from packages.ubuntu.com, save it to your desktop, and then do:
```
sudo dpkg -i ~/Desktop/test*.deb
```
That will install it, and then run it with:
```
sudo testdisk
```

---

### Post by mylifedrive on 2008-10-09
Testdisk gave me this:

```

Disk /dev/sda - 4005 MB / 3820 MiB - CHS 487 255 63 (RO)
     Partition               Start        End    Size in sectors
* Linux                    0   1  1   458 254 63    7373772
```

---

### Post by Gannon8 on 2008-10-09
There should be an option that restores the partition. Tab to it and hit enter, then reboot.

---

### Post by mylifedrive on 2008-10-09
If I don't do that last proceed, I get this:

```
Disk /dev/sda - 4005 MB / 3820 MiB - CHS 487 255 63 (RO)
Current partition structure:
     Partition                  Start        End    Size in sectors
 1 * Linux                    0   1  1   458 254 63    7373772
 2 E extended               459   0  1   486 254 63     449820

test_logical:
Partition sector doesn't have the endmark 0xAA55


```

---

### Post by mylifedrive on 2008-10-09
> **Gannon8 said:**
> There should be an option that restores the partition. Tab to it and hit enter, then reboot.

Thanks, but I don't see it.

---

### Post by caljohnsmith on 2008-10-09
Mylifedrive, it looks like you will need to use testdisk's "deeper search" feature to help sort out your partitions, so run testdisk again:
```
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "proceed", "N" to search for Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Please post the output of that screen.

Also, to make it easy to compare fdisk with testdisk's results, please post:
```
sudo fdisk -l
```

---

### Post by mylifedrive on 2008-10-10
after
choosing "no log", selecting HDD and "proceed", "Intel", "Analyze",
I get this:

```
TestDisk 6.5, Data Recovery Utility, October 2006
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 4005 MB / 3820 MiB - CHS 487 255 63 (RO)
Current partition structure:
     Partition                  Start        End    Size in sectors
 1 * Linux                    0   1  1   458 254 63    7373772
 2 E extended               459   0  1   486 254 63     449820

test_logical:
Partition sector doesn't have the endmark 0xAA55









*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

[Proceed ]  [ Backup ]
                            Try to locate partition








```
Proceed again would be selecting the Linux partition. Should I do that?

---

### Post by caljohnsmith on 2008-10-10
Yes, go ahead and "proceed", the linux partition is not actually going to be selected.

---

### Post by mylifedrive on 2008-10-10
It sure seems lke it will. using the up and down keys, I can move the selection between

```
 1 * Linux                    0   1  1   458 254 63    7373772
```
and
```
 2 E extended               459   0  1   486 254 63     449820
```

---

### Post by mylifedrive on 2008-10-31
I want to thank you all for your help, I recenty reformatted the flash drive in Windows on another computer, and reinstalled linux. Thanks!

---

