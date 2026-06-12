---
title: "Error: Can't have overlapping partitions."
date: 2009-05-08
forum: Hardware
---

### Post by Eosie on 2009-05-08
Hi.
I can't remove the second partition in my external harddrive, because gparted says it's unallocated, but both partitions can be mounted without a problem. I intentionally removed /dev/sda from the following logs.

sudo fdisk -lu
```
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   604237823   302118880+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *   604236780   625137344    10450282+  83  Linux

```

sudo sfdisk -d
```
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=604237761, Id= 7
/dev/sdb2 : start=604236780, size= 20900565, Id=83, bootable
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

```

sudo parted /dev/sdb print
```
Error: Can't have overlapping partitions.
```

I could remove sdb2 directly, but I am unsure about this solution and I don't want to screw things up. Having overlapping partitions is somewhat weird. So please, help me.

---

### Post by caljohnsmith on 2009-05-08
Since your two partitions overlap, we can't be sure if either of their start/stop sectors are correct at the point where they overlap. Therefore, I would suggest using "testdisk" to rebuild your correct partition table; to use testdisk, how about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions. We can work from there if you want.

John

---

### Post by Eosie on 2009-05-09
This has shown up:
```
Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63

The harddisk (320 GB / 298 GiB) seems too small! (< 320 GB / 298 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                37614   2  1 38915   1 58   20900560

[ Continue ]

```

Deep search results:
```
Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 37611 254 63  604236717 [My External Book]
D HPFS - NTFS              0   1  1 38912 254 63  625137282 [My External Book]
D Linux                37612   0  1 38912 254 63   20900565

Structure: Ok.
```

All partitions gave me a directory listing, though the first two are identical. All seem to be my partitions. It looks like something went terribly wrong when I was resizing the first partition a year ago, I guess.

---

### Post by caljohnsmith on 2009-05-09
> **Eosie said:**
> 
```
Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] HPFS - NTFS              0   1  1 37611 254 63  604236717 [My External Book]
[COLOR="Red"]D[/COLOR] HPFS - NTFS              0   1  1 38912 254 63  625137282 [My External Book]
[COLOR="Red"]D[/COLOR] Linux                37612   0  1 38912 254 63   20900565

Structure: Ok.
```

OK, so do you still want to delete your current sdb2 linux partition? If you do, how about using your up/down arrow keys to select each partition shown above, and then use your right/left arrow keys to mark them as I've shown highlighted in red. Once you are sure the partitions are marked exactly as shown above, press enter to get the next screen, and there you can write the new partition table. After that reboot, and you should be able to make any further partition changes you want after that. Let me know how it goes or if you run into problems. 

John

---

### Post by Eosie on 2009-05-09
Rebooting wasn't needed. I've just unplugged my harddrive from USB and plugged it in. sdb1 is mountable and contains all my data, sdb2 has been removed as expected. Everything is now ok.

Thank you so much.

---

### Post by caljohnsmith on 2009-05-09
Glad to hear testdisk fixed your overlapping partition problem. :) Hopefully whatever caused the problem in the first place won't happen to you again.

Cheers,
John

---

