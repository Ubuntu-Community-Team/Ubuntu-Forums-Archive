---
title: "GRUB problem (and the magical switching HD Partition numbers)"
date: 2008-09-02
forum: General Help
---

### Post by Derp on 2008-09-02
Okay okay. This is my first time with Linux, everything is NEW AND CONFUSING (this multi desktop is mighty handy though).

Installed Ubuntu (HARDY! HARDY! HARDY!) on a resized partition with Windows (PROBLEMS)

GRUB comes up with a Error 22 (you know, the one where it can't find the partition for some odd reason)
((as an addendum, when I select to boot from the drive I want, Grub has no problem loading up that very dull option screen, but still has trouble locating the partitions))

Looked on the documentation (thank god I had a 15 meter ethernet cable laying about, else I wouldn't be the happiest of chappys) and did the first few steps. (Silly Broadcom and its proprietary drivers >:V)

```
ubuntu@ubuntu:~$ Sudo Grub
Grub Find /boot/grub/stage1
(hd4,3)
Grub root (hd4,3)
Grub Setup (hd4)
```
GRUB GRAB. GRUB SMASH. GRUB MAD.

Okay, so I didn't read *too* far into the documentation, the part where I could do setup (hd4,3) instead of setup (hd4)
So anyway, I restarted, same problem.
Booted back into the UbubtuLiveCD and repeated the steps, this time doing it...
```
ubuntu@ubuntu:~$ Sudo Grub
Grub Find /boot/grub/stage1
(hd4,4)
Grub root (hd4,4)
Grub Setup (hd4,4)
```
wait, my hdpartition number changed. Oh well can't be too bad right?

just to make sure, I went into the boot/grub/main.lst

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd4,4)
```

Windows* was there too. Just under the AUTOMAGICAL KERNEL header. Moved it up above the AUTONOMOUSMAGIC KERNEL 

Rebooted, same problem. (booted from HD, Grub gave me a 22 on Ubuntu, and a NTLDR on Windows) Back to LinuxCD

```
ubuntu@ubuntu:~$ Sudo Grub
Grub Find /boot/grub/stage1
(hd3,4)

```

At this point, I like to think that I've either gone crazy, or Grub is just mucking about.

I didn't bother installing, instead, I randomly Grub rooted about on (hd4,x) to see which numbers have partitions on them. (((hd4,1) Windows?) and ((hd4,4) Ubuntu?) seem to be alive)

I tried changing the numbers around in main.lst, but now I get an Access Denied. (even when I'm installing through Terminal)

*Windows Root on main.lst shows;
```
title		Microsoft Windows XP Professional
root		(hd4,0)
```

And that is my problem so far. Magical changing HD/Partition numbers in Grub and access denied. Any help (besides using the computer to see how long a tower will remain airborne after being thrown out of a window) would be lovely (as I sip my tea and try not to slit my wrists with a butter knife).

Oh, Additional information too;
I've got 5 HDDs. Might be the reason why Grub keeps switching the numbers around.

Edit: It just occurred to me that I might have posted it in the wrong forum

---

### Post by Derp on 2008-09-02
Okay, I managed to fix it in the end (used the commandline grub to change the 4,4 to 0,4, then used the sudo gedit to change it into that).

Now, second problem. 

Whenever I try to boot into the Windows partition, I get "NTLDR is missing".
I looked up my disks using Fdisk -l, and my partition is Extended. Someone on here did say that XP doesn't boot from Extended partitions.

blahen.

additional information

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bb0cb46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1b8c1b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c428c42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4815    38676456    7  HPFS/NTFS
/dev/sdc2            4816        9729    39471705    5  Extended
/dev/sdc5            4816        9522    37808946   83  Linux
/dev/sdc6            9523        9729     1662696   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42379594

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38913   312568641   42  SFS

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfec4cf3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       24321   195358401    7  HPFS/NTFS

```

---

### Post by Derp on 2008-09-03
Just woke up, try some more things

That's strange, Windows (recovery console) reports that my windows is on E:\ rather than C:\
Probably the reason it can't find NTLDR?

Also, I installed some Nvidia drivers for my Nvid' 7800 and now all I get when I boot into Ubuntu is the command line. I've tried starting Gnome but that didn't do anything.

Blehaihaeihr.

Never mind about the NTLDR thing, I managed to fix it thanks to [Herman's guide]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI")
Now to do the Nvidia driver

---

