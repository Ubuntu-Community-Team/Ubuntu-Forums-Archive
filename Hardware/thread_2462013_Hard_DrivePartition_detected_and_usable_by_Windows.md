---
title: "Hard Drive/Partition detected and usable by Windows, but not by Ubuntu"
date: 2021-05-11
forum: Hardware
---

### Post by abdullahtrees on 2021-05-11
Hello everyone!

The title pretty much describes the problem well enough already: For some reason a drive which is perfectly detectable and usable by Windows without any problems whatsoever, is not mountable and unusable on Ubuntu 20.04.

[COLOR=#ff0000][SIZE=4]WARNING: THIS DRIVE CONTAINS  CRITICAL DATA AND IS CURRENTLY USABLE BY WINDOWS. I CAN'T RUN COMMANDS  THAT MAY RISK LOSING DATA ON THE HDD.[/SIZE][/COLOR]

[IMG]https://i.imgur.com/Fgnfzjl.png[/IMG]
According to Windows, it is a single partition(Disk 1 in the image) of size 3.7TB and is perfectly fine. I ran SMART Tests and a disk surface test a few months ago and they confirm that the drive (although a bit old) is healthy and fine for now. 


I did some googling in order to figure out why this drive wasn't showing from Ubuntu's file manager and here are the preliminary results of some diagnostic checking.
```

abdullahtrees@PC-Abdullah-LINUX:~$ sudo fdisk -l

<6 redundant loop device information skipped>

Disk /dev/loop7: 38.9 MiB, 40771584 bytes, 79632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 698.65 GiB, 750156374016 bytes, 1465149168 sectors
Disk model: TOSHIBA MQ01ABD0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 3C5AF9D1-FCAB-4574-BD25-5357A6A6A9CC

Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624 1465147391 1464096768 698.1G Linux filesystem


Disk /dev/sdb: 2.75 TiB, 3000592982016 bytes, 5860533168 sectors
Disk model: TOSHIBA DT01ACA3
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: D6392940-B561-4318-B14A-855337883535

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048     923647     921600   450M Windows recovery environment
/dev/sdb2      923648    1126399     202752    99M EFI System
/dev/sdb3     1126400    1159167      32768    16M Microsoft reserved
/dev/sdb4     1159168 1610067495 1608908328 767.2G Microsoft basic data
/dev/sdb5  1610067968 1611769855    1701888   831M Windows recovery environment
/dev/sdb6  1611771904 3027349503 1415577600   675G Microsoft basic data
/dev/sdb7  3027349504 4442927103 1415577600   675G Microsoft basic data
/dev/sdb8  4442927104 5858504703 1415577600   675G Microsoft basic data


[COLOR=#ff0000]The primary GPT table is corrupt, but the backup appears OK, so that will be used.[/COLOR]
Disk /dev/sdc: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: TOSHIBA MD04ACA4
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B7E42D78-B176-432E-8A6B-15D91DCBFE73

Device      Start        End    Sectors  Size Type
/dev/sdc1      34     262177     262144  128M Microsoft reserved
/dev/sdc2  264192 7814035455 7813771264  3.7T Microsoft basic data

[COLOR=#ff0000]Partition 1 does not start on physical sector boundary.[/COLOR]

<6 redundant loop device information skipped>

```

My questions are: 
1) How can I repair the primary GPT table of this drive without reformatting the entire drive/losing the contents of the drive? I have no other drive to copy my data to. Any way to copy the current GPT Table and use software to make changes to the partition table only?
2) How come Windows can use this drive while Linux cannot?

This drive has most of my cartoons and games, so I'd really like to be able to use this drive between Windows and Linux so I don't have to restart my PC to watch some Avatar The Last Airbender, 
Thanks in advance!

---

### Post by ajgreeny on 2021-05-11
My guess is that you have not disabled fast-start in Windows which means that after using Windows and "shutting down" Windows all partition in use by that OS are in hibernation and not mountable in Linux.

Turn of fast-start in Windows (I've no idea how as I do not use Windows any more) and you may find the partition is now usable in Ubuntu, but be warned, Windows will often enable fast-start again in its upgrades so you may need to repeat the disabling again in future.

If fast start is not your problem I can not help you further but other forum users may be able to so keep looking back here for other answers.

---

### Post by tea for one on 2021-05-11
> **abdullahtrees said:**
> 
My questions are: 
1) How can I repair the primary GPT table of this drive without reformatting the entire drive/losing the contents of the drive? I have no other drive to copy my data to. Any way to copy the current GPT Table and use software to make changes to the partition table only?
2) How come Windows can use this drive while Linux cannot?

I certainly hope that [COLOR="#0000FF"]ajgreeny[/COLOR] has hit the nail on the head concerning Windows fast start-up.

Otherwise, you could consider [https://www.rodsbooks.com/gdisk/repairing.html](https://www.rodsbooks.com/gdisk/repairing.html)

Any process involving partitions and gpt tables can easily result in catastrophe i.e. loss of data.
My advice is:-
Do nothing at the moment until you have a back-up of your cartoons and games.
When you have a back-up, you will not have sleepless nights and **gdisk** will fix your drive.

---

### Post by abdullahtrees on 2021-05-11
At first when I read ajgreeny's answer, I was skeptical. If fast-start was enabled, then wouldn't that mean that C:/ drive (/dev/sdb4/) would be inaccessible? But I was able to mount and use all other drives except the 4TB one (/dev/sdc2/). But regardless, I booted up to Windows.
And well, well, well...  Turns out fast-start was enabled! So I laughed it out, disabled fast-started, and restarted into Ubuntu. 

But /dev/sdc2 is still inaccessible. I don't see it as an option from the file browser. So I think it's more of an issue with the fact that Linux gets really iffy with partitions that don't start on a physical sector boundary.

So about repairing the partition table, isn't there a way to backup the current version of the GPT on the disk "bit-for-bit" and save it into a file, to be restored later in case of a mistake? The GPT is the first and last bunch of sectors on every GPT-type disk, so why doesn't software like this exist? Then I'd imagine that repairing the partition table would be easier.

---------------------------------------------------------------

To be honest with you, I am a beginner to Linux. I actually prefer and love using Windows and am only forcing myself to learn and use Linux over concerns that Microsoft will continue to make the Windows lineup and it's future worse with time(Windows XP was the peak). But over the past year, my experience with Linux has been nothing but hours of googling, trying to understand complex console commands (can you believe that not a single distro of Linux is fully GUI/console-independent except Android???), trying to get around Linux limitations, and making many forum posts similar to this one. Now, I personally don't mind THAT much with fiddling around with these problems (it's like playing with an intricate digital puzzle)

But next time anyone in a YouTube comments section brags about how Linux is the best OS in the world, I'll take it with grains of salt.

---

### Post by tea for one on 2021-05-12
> **abdullahtrees said:**
> So about repairing the partition table, isn't there a way to backup the current version of the GPT on the disk "bit-for-bit" and save it into a file, to be restored later in case of a mistake? The GPT is the first and last bunch of sectors on every GPT-type disk, so why doesn't software like this exist? Then I'd imagine that repairing the partition table would be easier.

Your drive with the corrupt GPT is a Windows file system and the general advice is to use Windows tools to repair Windows file systems.
Which Windows tools did you consider?

Of course, your choice of file system is restricted because you need the data to be accessible in Windows.;)

Software does exist to repair corrupted GPT 
[https://www.rodsbooks.com/gdisk/walkthrough.html](https://www.rodsbooks.com/gdisk/walkthrough.html)
[https://www.rodsbooks.com/gdisk/repairing.html](https://www.rodsbooks.com/gdisk/repairing.html)

Please pay attention to the section [COLOR="#0000FF"]Things that Can Go Wrong[/COLOR]

If you decide to try and repair without a back-up, then that is your choice.

If your data is critical (as mentioned in post no. 1), then you would have a back-up anyway.

> **abdullahtrees said:**
> But next time anyone in a YouTube comments section brags about how Linux is the best OS in the world, I'll take it with grains of salt.

Yes, YouTube comments - the fountain of all knowledge.:rolleyes:

---

### Post by abdullahtrees on 2021-05-12
The data is critical, but I can't afford to buy another 4TB drive to back it up to, and my internet's too slow to upload 2.7TB of data in a reasonable amount of time :/

I wanted to inquire into whether changing the GPT was really risky or not, if you backed up the current GPT. But it looks like this might potentially cause me to lose my data. So I'll skip this for now. 

Since the problem was not solved(drive remains inaccessible from Linux) and I had to give up, I'll mark this thread as not solved. Thanks for all of your input, everyone.

---

### Post by tea for one on 2021-05-12
> **abdullahtrees said:**
>  But it looks like this might potentially cause me to lose my data. So I'll skip this for now. 

Very wise to skip the GPT repair at the moment.

I had another thought today. After you have used the problem drive in Windows, do you safely remove the device?

Sometimes when drives are not cleanly disconnected, there can be ensuing difficulties.

Finally, just to satisfy my curiosity, I understand that you did not consider the use of any Windows tool/utility to help you repair the ntfs file system?

---

### Post by abdullahtrees on 2021-05-13
> **tea for one said:**
> 
I had another thought today. After you have used the problem drive in Windows, do you safely remove the device?


It is an internal SATA drive, not a portable USB-driven drive, so the only way to safely remove the drive is to turn off the computer first.

> **tea for one said:**
> 
Finally, just to satisfy my curiosity, I understand that you did not consider the use of any Windows tool/utility to help you repair the ntfs file system? 

Technically nothing is wrong with the NTFS file system. It is the partition table which Windows considers fine, but Linux considers it corrupted. I haven't found Windows-based software that can repair the partition table of a currently working drive. 
(I know of [TestDisk]("https://www.cgsecurity.org/wiki/TestDisk"), but I only ever used that to successfully recover data from a dying external drive that had corrupted file system due to running it without its controller. I also ended up using TestDisk incorrectly and it ended up overwriting the drive information somehow (reported that it was 98127923434GB with 1289319237GB free, oops) which made the drive unrecoverable (but not before I lifted all my data off of it.)

---

