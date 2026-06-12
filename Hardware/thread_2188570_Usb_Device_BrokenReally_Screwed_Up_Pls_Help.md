---
title: "Usb Device Broken/Really Screwed Up Pls Help"
date: 2013-11-17
forum: Hardware
---

### Post by RedstonePoweredGam on 2013-11-17
Every Time I Plug My Usb Device In An error message appears
 ___________________________________________________________________________________________________________________________________________________________   
[B]Error mounting /dev/sdg1 at /media/redstone/efc6be7e-b062-4e93-aa06-7fd08eb30f68: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdg1" "/media/redstone/efc6be7e-b062-4e93-aa06-7fd08eb30f68"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdg1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
_____________________________________________________________________________________________________________________________________________________________


[/B]Every Time I Try to format/delete any partition I returns this
_______________________________________________________________________________________________________________________________________________________________
Input/output error during write on /dev/sdg
______________________________________________________________________________________________________________________________________________________________
I Hit Retry and it says Cannot Found Device /dev/sdg





I'd Would Appreciate any help I could get.

Thanks









EDIT:
Don't know if this helps but I'm on Linux Mint 15
Also Its a SD card but to read it i'm using a SD
to USB card reader



2nd EDIT:
I don't know if this is in the right category.

---

### Post by heir4c on 2013-11-18
Maybe you can open "Disk Utility" and do test on the drive with it.

---

### Post by RedstonePoweredGam on 2013-11-18
> **heir4c said:**
> Maybe you can open "Disk Utility" and do test on the drive with it.

Thanks for responding but it did not work:neutral:
It Returned the error message
```
Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)
```
But Thanks Any Way

---

### Post by heir4c on 2013-11-18
Can you give the output of:
```
sudo fsck /dev/sdg1
```

---

### Post by RedstonePoweredGam on 2013-11-19
Output
```
redstone@redstoned-Dell-DV051 ~ $ sudo fsck /dev/sdb1
[sudo] password for redstone: 
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sdb1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? yes

fsck.ext4: unable to set superblock flags on /dev/sdb1


/dev/sdb1: ********** WARNING: Filesystem still has errors **********

redstone@redstoned-Dell-DV051 ~ $ 
redstone@redstoned-Dell-DV051 ~ $ 






```
used sdb as that was the mount point when i rebooted

---

### Post by tgalati4 on 2013-11-19
Open a terminal, post the output of:

```
dmesg | tail -40
```

You might have a defective USB thumbdrive.

---

### Post by RedstonePoweredGam on 2013-11-20
Here it is
```
redstone@redstoned-Dell-DV051 ~ $ dmesg | tail -40
[   21.889337] vboxdrv: Successfully loaded version 4.3.2 (interface 0x001a0005).
[   22.116454] vboxpci: IOMMU not found (not registered)
[   22.862122] init: plymouth-stop pre-start process (1727) terminated with status 1
[   61.317197] sd 4:0:0:0: [sdb] Media Changed
[   61.317205] sd 4:0:0:0: [sdb]  
[   61.317209] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   61.317212] sd 4:0:0:0: [sdb]  
[   61.317214] Sense Key : Unit Attention [current] 
[   61.317219] sd 4:0:0:0: [sdb]  
[   61.317224] Add. Sense: Not ready to ready change, medium may have changed
[   61.317227] sd 4:0:0:0: [sdb] CDB: 
[   61.317229] Write(10): 2a 00 00 00 08 00 00 00 10 00
[   61.317239] end_request: I/O error, dev sdb, sector 2048
[   61.317246] Buffer I/O error on device sdb1, logical block 0
[   61.317249] lost page write due to I/O error on sdb1
[   61.317263] Buffer I/O error on device sdb1, logical block 1
[   61.317267] lost page write due to I/O error on sdb1
[   63.758690] sd 4:0:0:0: [sdb] Media Changed
[   63.758698] sd 4:0:0:0: [sdb]  
[   63.758701] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   63.758704] sd 4:0:0:0: [sdb]  
[   63.758707] Sense Key : Unit Attention [current] 
[   63.758712] sd 4:0:0:0: [sdb]  
[   63.758716] Add. Sense: Not ready to ready change, medium may have changed
[   63.758719] sd 4:0:0:0: [sdb] CDB: 
[   63.758721] Write(10): 2a 00 00 00 14 e0 00 00 18 00
[   63.758731] end_request: I/O error, dev sdb, sector 5344
[   63.758738] Buffer I/O error on device sdb1, logical block 412
[   63.758740] lost page write due to I/O error on sdb1
[   63.758754] Buffer I/O error on device sdb1, logical block 413
[   63.758756] lost page write due to I/O error on sdb1
[   63.758760] Buffer I/O error on device sdb1, logical block 414
[   63.758762] lost page write due to I/O error on sdb1
[   63.758794] JBD2: recovery failed
[   63.758799] EXT4-fs (sdb1): error loading journal
[   63.763568] sd 4:0:0:0: [sdb] No Caching mode page present
[   63.763576] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   63.788094] sd 4:0:0:0: [sdb] No Caching mode page present
[   63.788103] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   63.804631]  sdb: sdb1 sdb2 < sdb5 >
redstone@redstoned-Dell-DV051 ~ $ 

```

---

### Post by tgalati4 on 2013-11-21
I/O errors are bad.  It's possible that the flash drive has too many worn-out sectors such that the drive controller can't keep up with the I/O requests.  Try different ports on the same machine and also try some different linux machines and use the *dmesg* command to see if the bad blocks are the same.  

Running *badblocks* should provide a similar list as shown above.  Also run *fsck* without reloading the journal.  Since it appears that the journal was stored on sectors that are bad, thus fsck won't complete its repair and mark the filesystem clean.  You will lose some data, but at least the drive should mount then you can do a more thorough analysis.

---

