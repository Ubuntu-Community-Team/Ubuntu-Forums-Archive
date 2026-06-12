---
title: "Mount Partition Problems"
date: 2008-10-17
forum: Hardware
---

### Post by Ango on 2008-10-17
Hi,

I just did a fresh Ubuntu install on my good old Acer TravelMate and had some issues with auto-mounting one partition - unfortunately it is the one where I keep all my data... It was mounting fine manually, until I tried to solve the issue using a few ideas listed here. I must have made a mistake as I can't even mount it manually any more.

A few more info to enlighten the specialists...

> jacques@Jacques-pc:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f038f03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1148     9221278+   7  HPFS/NTFS
/dev/sda2            1149        1219      570307+  82  Linux swap / Solaris
/dev/sda3            1220        2374     9277537+  83  Linux
/dev/sda4            2375        3648    10233405    f  W95 Ext'd (LBA)
/dev/sda5            2375        3648    10233373+   b  W95 FAT32

> jacques@Jacques-pc:~$ sudo mount -a
jacques@Jacques-pc:~$ 

> jacques@Jacques-pc:~$ sudo blkid
/dev/sda1: UUID="D22800C92800AE93" LABEL="WinXPp" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="1dda05f6-43c8-4013-87e7-5e3bce4f6b8e" 
/dev/sda3: UUID="59b3fd7e-befb-40e5-9639-3fe526408939" TYPE="ext3" 
/dev/sda5: LABEL="DATA" UUID="48F7-B447" TYPE="vfat" 

Thanks for any lead on how to solve my problems !

---

### Post by Ango on 2008-10-17
Nobody? Really?
Am really at a lost here :-s

---

### Post by nickcboi on 2008-10-17
I just posted something probably about the exact same problem. I hope somebody responds.

---

### Post by tomhat on 2008-10-17
[B][COLOR="Navy"]I have a similar problem.
I recently reinstalled my Windows XP. All went fine & I managed to boot Ubuntu except that all partitions load automatically apart from the partition which carries the newly installed WinXP.
The partition appears when I view the "Computer" in Places, but I have to open it from there to mount.
I have to do this every time I login.
That makes 3 of us with the same problem.[/COLOR][/B]

---

### Post by tomhat on 2008-10-17
[b][color=darkblue]I found a thread related to this problem & it helped me solve my problem.

[http://ubuntuforums.org/showthread.php?t=390312](http://ubuntuforums.org/showthread.php?t=390312)

See if it can help you solve your problem too.[/color][/b]

---

### Post by Ango on 2008-10-18
Thanks for the tip - just bookmarked it.
I will revert to it when I do a fesh install of Ubuntu.
My laptop decided to surprise me this morning... Grub did not launch. Hence I had to revert to my XP partition. I don't know how I did but I ended up with a blank partition where Ubuntu was supposed to be. 

As for now, XP will be good enough for the next few days and  I'll wait for 8.10 - hoping it will solve all my problems - fingers crossed !!

---

### Post by tomhat on 2008-10-18
[COLOR=darkblue][B]I think it's normal that the partition with Ubuntu can't be read from WinXp.
Did you reinstall your windows or something. My Grub messed up when I reinstalled mine.
I'm a Ubuntu newbie, but I managed to solve the Grub problem using this page.[/B][/COLOR]

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

