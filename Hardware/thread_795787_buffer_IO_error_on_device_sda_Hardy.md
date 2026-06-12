---
title: "buffer I/O error on device sda Hardy"
date: 2008-05-15
forum: Hardware
---

### Post by 00arthuryu on 2008-05-15
Heya
I have had quite a bit of trouble from hardy so far. The computer randomly stops reading from the HDD and can only run the things that are already loaded onto ram.
If i go to ALT F1 then this kind of thing appears

```

ata validation failed
fat: fat read failed blocknr (many of these)
buffer I/O error on device sda11 logicalblock 0
buffer I/O error on device sda11 logicalblock 1 (and even more of these with random numbers)

buffer I/O error on device sda6 logicalblock 1 (and even more of these with random numbers)

EXT3-fs error (device sda11): ext3_find_entry: <6>sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK (at the end)

```
But these are really random and the amount varies ALOT

I don't want to believe my Hard disk is dying as I have never had this trouble before with Feisty and/or Gutsy and the HDD is only about 3 months old.
Its a Seagate 500GB SataII.
I've even done a clean/fresh install of Hardy :(

Any help or hints or any posts in general will be hugged by me :D
Thank you!

I haven't read this anywhere.. so is it just me? :(

---

### Post by hermes0710 on 2008-05-16
Check this thread:
   [http://ubuntuforums.org/showthread.php?t=551985]("http://ubuntuforums.org/showthread.php?t=551985")

---

### Post by 00arthuryu on 2008-05-16
Thanks for reply :D
I may be having a slight different problem as my sda is actually an internal SATAII drive, maybe ubuntu thinks its an external??
Its always mounted to /media/sda /media/sdb hmm..

I would like to point out that /dev/sda11 is my root partition

On a fresh install of hardy, none of my partition get mounted and I have to grab the old fstab from my previous install of ubuntu to tell it to mount my drives (I have a backup of my old drives)

I will experiment :D but thanks alot for information :D

---

### Post by hermes0710 on 2008-05-16
No problem, :) post the solution if you get it, seems very interesting

---

### Post by 00arthuryu on 2008-05-17
Okay this is really bugging me now as everything freezes and a hard reboot is necessary and has made my computer near unusable. This seems to happen more often when running virtualbox. bootup does not have any problems and everything seems to run fine but then out of the blue everything will freeze.

It is not in by dmesg as it cannot write to the HDD. Which is highly annoying.

and hint/pointers? but more importantly is anyone else getting this?

---

### Post by 00arthuryu on 2008-05-18
I've done the updates (kernel update included) and still no luck, I can't really live without me beloved ubuntu. Someone please help :(

After it can't read the Hard disk, It tries to remount the root partition as read only but still fails. I do not think any logs are taken as the HDD is completely unreadable/unwriteable

this happened twice just trying to post this :(

I believe this is the same problem as mine in another thread
[http://ubuntuforums.org/showthread.php?p=4986754#post4986754](http://ubuntuforums.org/showthread.php?p=4986754#post4986754)

---

### Post by jfdill_2 on 2008-05-23
I have a Dell GX260 with 3 PATA hard drives, 2 of the drives are fine, but the 3rd drive which is a 120 GB Maxtor 6Y120P0 gives me Buffer I/O errors.  At first, I thought the drive was just going bad, but have checked it with badblocks read / write mode and it didn't find any bad blocks (and no read / write errors during running badblocks) so now I'm not so sure.  smartctl selftest also passed with flying colors.

I'm wondering if somewhere it's trying to map to blocks outside the physical device or something crazy like that, but haven't bothered to do the math.  I did have a problem like that once with the Debian installer, I think it was Sarge, I think I just created a bogus empty partition at the end of the drive and didn't use it then fixed it after the install.  But I don't know if that has anything to do with this problem.

A couple other notes:  I got the same thing when that drive was /dev/sdb hooked to the other PATA interface.  It was fine with up to Ubuntu Gutsy, problem started on Hardy, but like always it's possible that is a coincidence.  The box has a relatively fresh power supply since the old one died and was replaced with a better unit and not just stock replacement.  I do think something could be wrong with the motherboard, so that is something else to rule out.  I think I'll give memtest86+ a whirl.

```
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST340016A        Rev: 3.75
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: WDC WD400BB-75DE Rev: 05.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: Maxtor 6Y120P0   Rev: YAR4
  Type:   Direct-Access                    ANSI  SCSI revision: 05

```

```
Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000335c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14946   120053713+  83  Linux
root@jester:~# cat bad.txt 
[   20.087741] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[   20.087757] sd 1:0:1:0: [sdc] Write Protect is off
[   20.087759] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   20.087781] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.087844] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[   20.087856] sd 1:0:1:0: [sdc] Write Protect is off
[   20.087859] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   20.087879] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.087883]  sdc: sdc1
[   20.105502] sd 1:0:1:0: [sdc] Attached SCSI disk
[ 1430.026035] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1430.026039] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1430.026059] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1430.026066] end_request: I/O error, dev sdc, sector 177471552
[ 1430.026070] Buffer I/O error on device sdc1, logical block 177471489
[ 1430.026076] Buffer I/O error on device sdc1, logical block 177471490
[ 1430.026079] Buffer I/O error on device sdc1, logical block 177471491
[ 1430.026082] Buffer I/O error on device sdc1, logical block 177471492
[ 1430.026085] Buffer I/O error on device sdc1, logical block 177471493
[ 1430.026088] Buffer I/O error on device sdc1, logical block 177471494
[ 1430.026091] Buffer I/O error on device sdc1, logical block 177471495
[ 1438.080851] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1438.080855] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1438.080875] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1438.080882] end_request: I/O error, dev sdc, sector 177471552
[ 1438.080887] Buffer I/O error on device sdc1, logical block 177471489
[ 1438.080891] Buffer I/O error on device sdc1, logical block 177471490
[ 1438.080894] Buffer I/O error on device sdc1, logical block 177471491
[ 1438.080897] Buffer I/O error on device sdc1, logical block 177471492
[ 1438.081165] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1438.092438] sd 1:0:1:0: [sdc] Write Protect is off
[ 1438.092446] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1438.092530] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1438.092560] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1438.092572] sd 1:0:1:0: [sdc] Write Protect is off
[ 1438.092575] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1438.092595] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1446.199630] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1446.199635] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1446.199655] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1446.199661] end_request: I/O error, dev sdc, sector 177733695
[ 1446.199669] Buffer I/O error on device sdc1, logical block 177733632
[ 1447.188074] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1455.209323] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1455.209327] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1455.209347] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1455.209353] end_request: I/O error, dev sdc, sector 177733695
[ 1455.209358] Buffer I/O error on device sdc1, logical block 177733632
[ 1455.209592] sd 1:0:1:0: [sdc] Write Protect is off
[ 1455.209595] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1456.000304] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1456.009559] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1456.009577] sd 1:0:1:0: [sdc] Write Protect is off
[ 1456.009580] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1456.009601] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1465.082066] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1465.082070] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1465.082090] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1465.082096] end_request: I/O error, dev sdc, sector 179306559
[ 1465.082101] Buffer I/O error on device sdc1, logical block 179306496
[ 1473.232770] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1473.232774] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1473.232794] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1473.232800] end_request: I/O error, dev sdc, sector 179306560
[ 1473.232805] Buffer I/O error on device sdc1, logical block 179306497
[ 1473.232810] Buffer I/O error on device sdc1, logical block 179306498
[ 1473.232813] Buffer I/O error on device sdc1, logical block 179306499
[ 1473.232816] Buffer I/O error on device sdc1, logical block 179306500
[ 1473.232987] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1481.255637] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1481.255642] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1481.255662] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1481.255668] end_request: I/O error, dev sdc, sector 179306559
[ 1481.255675] Buffer I/O error on device sdc1, logical block 179306496
[ 1481.255681] Buffer I/O error on device sdc1, logical block 179306497
[ 1481.256368] sd 1:0:1:0: [sdc] Write Protect is off
[ 1481.256372] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1481.256401] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1481.256428] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1481.256461] sd 1:0:1:0: [sdc] Write Protect is off
[ 1481.256464] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1481.256485] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

---

### Post by 00arthuryu on 2008-05-23
heya jfdill_2
Does the rest of your drives work? and does X crash with those errors?
I get a total freeze with only ctrl+alt+F1 to be able to see the error messages. In any case here is a link to the bug reports related to ubuntu.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229968](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229968)
I really do hope that these get fixed soon

Regards
Arthy

---

### Post by jfdill_2 on 2008-05-23
> **00arthuryu said:**
> heya jfdill_2
Does the rest of your drives work? and does X crash with those errors?
I get a total freeze with only ctrl+alt+F1 to be able to see the error messages. In any case here is a link to the bug reports related to ubuntu.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229968](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229968)
I really do hope that these get fixed soon

Regards
Arthy

X didn't crash, but the system froze for a few seconds, it wasn't the system disk, so maybe that helped.  With respect to my previous comment about partitioning, it just occurred to me that I didn't make any changes to that disk during the install.  The first problem I had was that I couldn't mount a filesystem that was on an LVM that was on that disk, but all of the other filesystems and LVMs were fine.  I tried reiserfsck and that bombed out right away and there were more I/O errors.

Doing some web searching with "Maxtor" and "Buffer I/O error" turned up a lot of results with other Linux flavors and similar kernel version, guess it could be related to firmware on the drive.

I wish I could get more detail on the mode that is being used to access the drive, DMA and all that.

memtest86+ checked out fine, no problems with the RAM.

---

