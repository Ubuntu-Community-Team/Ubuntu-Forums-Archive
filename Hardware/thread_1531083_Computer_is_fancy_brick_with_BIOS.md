---
title: "Computer is fancy brick with BIOS"
date: 2010-07-14
forum: Hardware
---

### Post by Turmacar on 2010-07-14
Am extremely frustrated/confused at this point and this seemed like the right forum to come to for help..
So.

Until yesterday my desktop had been running fine for a year, was dual-booting win7 and lucid. Adobe needed to restart the windows side to update and I had just installed some scanner drivers so I restarted. Everything posts and then just hangs where normally it would go into grub. I rebooted a few times and nothing changed so got out UBCD and the 10.04 liveCD.

Then it got weird. The LiveCD will get to the point where it is loading into RAM and then just freeze, it will sometimes get get farther, or at least run longer, and sometimes restart the computer but it has not completed booting into live or just a straight install in the 20+ times I've tried.

UBCD is similarly weird. Tried using its grub2 to boot into either OS but no luck, they load part way and freeze. Checked the hdds and they are apparently fine. As is the cpu. It does however freeze on any memtest I try. The NSSI tool also said it thought there was a virus in memory but a)the AVIRA tool on the disk freezes and b) I left the power supply off all night so I don't see how there could still be anything in memory.

The only other thing I can think of that I did out of the ordinary was to plug in a external hdd he was having problems with. It won't show up sometimes and when it does not all the data will be there. Not sure how that could be 'infectious' though and UBCD as far as I can tell has given my hdds a clean bill of health.

So yea. I have no idea what the hell is going on. My linux and windows partitions are on different drives and I would like to save the windows side, I've pretty much given up hope that I can save both.

tldr: Yesterday something happened and computer's so frelled liveCD won't boot....

System
Intel E8400 3.00GHz dual-core
BFG Nvidea 8800GT 512MB
OCZ Reaper 2x2GB DDR2 1066
Gigabyte GA-EP45-UD3P LGA 775
Samsung cd/dvd burner SH-S223C
Western Digital 250GB
Western Digital 500GB x2
Windows 7 32bit
Ubuntu 10.04LTS 64bit

Help? What other info should I post.

---

### Post by IcarusR on 2010-07-14
> loading into RAM and then just freeze
> It does however freeze on any memtest I try

Sounds like it could be a ram related problem.

Do you have any different ram sticks you can try ?
Try removing then replacing ram sticks, then try booting.
Try removing 1 ram stick & ty booting. Then change ram & try again.

---

### Post by Turmacar on 2010-07-14
Don't have any other sticks. Moved the 2 around though, took one out, took the other out, put them in all the different slots. Nada.

---

### Post by Turmacar on 2010-07-14
Was the ram, borrowed a 1gig stick off a friend and am able to boot into ubuntu using UBCD. However it still does not go into grub automatically, I have to use the grub on the UBCD. From my ubuntu install it also cannot see my windows partition, but it can see the disk. 

Searching around forum/weberverse but help would be appreciated.

fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40f54cf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2be4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29165   234259456   83  Linux
/dev/sdb2           29165       30402     9936897    5  Extended
/dev/sdb5           29165       30402     9936896   82  Linux swap / Solaris

```

---

