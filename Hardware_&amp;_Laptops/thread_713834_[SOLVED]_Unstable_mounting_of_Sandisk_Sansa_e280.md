---
title: "[SOLVED] Unstable mounting of Sandisk Sansa e280"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by chochem on 2008-03-03
I know there are a gazillian threads on sansa issues already so apologies in advance for burdening the world witth one more. The thing is, the others seem to fall into one of two categories a) switch to MSC already, or b) it doesn't get detected at all.

So here's my c) I plug it in (using MSC, needless to say), it gets detected and automounted (on the device itself, it will say at first 'Connected', then 'Disconnected' and then settle on 'Connected'). All is well. I can browse, I can play. Sometimes I'm even allowed to copy a file or two or create a directory, though it takes forever. Seriously, waiting half a minute for a directory to get created? (I should add that my normal user is listed as the owner of all files and dirs on the device and permissions are rwx for the owner and 0 for anybody else)  Inevitably however, the device will disconnect during an attempt at copying files to it. The device will switch to saying 'Disconnected' and operations will time out. It may get reconnected by itself oncve or twice but it ends up disconnected. If I try remounting it (while it's still plugged in) I get told that 'dev/sdb1 is not a valid block device'.

This here's dmesg from the initial plug in:

```
[10032.572000] usb-storage: device found at 5
[10032.572000] usb-storage: waiting for device to settle before scanning
[10037.584000] usb-storage: device scan complete
[10037.596000] scsi 3:0:0:0: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
[10037.612000] scsi 3:0:0:1: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
[10037.636000] sd 3:0:0:0: [sdb] 15708160 512-byte hardware sectors (8043 MB)
[10037.668000] sd 3:0:0:0: [sdb] Write Protect is off
[10037.668000] sd 3:0:0:0: [sdb] Mode Sense: 45 00 00 00
[10037.668000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[10037.720000] sd 3:0:0:0: [sdb] 15708160 512-byte hardware sectors (8043 MB)
[10037.740000] sd 3:0:0:0: [sdb] Write Protect is off
[10037.740000] sd 3:0:0:0: [sdb] Mode Sense: 45 00 00 00
[10037.740000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[10037.740000]  sdb: sdb1 sdb2
[10037.764000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[10037.764000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[10037.788000] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[10037.788000] sd 3:0:0:1: Attached scsi generic sg2 type 0

```

This I get when it first fails to copy something
```
[10552.956000] usb 3-1: reset high speed USB device using ehci_hcd and address 5 [reappears a couple of times]
```

and the it will deteriorate into:
```
[10590.312000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10590.312000] end_request: I/O error, dev sdb, sector 1849344
[10590.320000] sd 3:0:0:0: rejecting I/O to offline device
[10590.320000] Buffer I/O error on device sdb1, logical block 30600
[10590.320000] lost page write due to I/O error on sdb1
```
with the last few lines reappearing several times with varying addresses.

I have tried formatting the disk and using the firmware updater (Windows) to reestablish the file structure but it's still the same.

What I don't get (and what seems to me to be distinctive) is that it is the act of copying, that seems to trigger the disconnect. I can pretty quickly provoke it, but I can also use VLC to play  an entire album and still have it playing an hour later, so it doesn't seem to be a matter of time.  Also, it's not 100 % consistent: I have managed to copy a few files (though testing it now, it seems increasingly difficult to prove).

EDIT: Okay, I got as far as creating two directories and half a file (500 kb) then it fails. So it is possible, it's just slow and quickly fails.

---

### Post by chochem on 2008-03-03
Okay, I got some inital succes manually mounting the drive and using root to copy. However this did not seem like a viable option in the long run (it didn't seem to please the file manager - thunar - too much either) so I finally tried using [this recovery routine]("http://www.fixya.com/support/t295795-refreshing_database") and it seems to have changed things for the better. I can connect it, though without an fstab entry, it shifts wildly between saying connected and disconnected.

EDIT: I'm still not really sure what the issues are here but for anyone else with similar problems, that if you do use the recovery routine, be sure to give the drive a label afterwards  - something simple without spaces, like 'SANSA' (I did it in Windows - sure there's some way in linux too). In Windows the drive appeared as having no label and in linux it was given the name 'SD PLAYER'. With the label the 'mood swings' stopped without any fstab entry. Anyway, fstab is probably not the way to go for a plug and play device...

---

### Post by tytus on 2008-07-18
> **chochem said:**
> 
I'm still not really sure what the issues are here but for anyone else with similar problems, that if you do use the recovery routine, be sure to give the drive a label afterwards


Can you elaborate on how did give the drive a label? I am having a very similar problem. I went through the recovery routine and still having more or less the same problems (I am using MSC and running Ubuntu 8.04 on Dell Latitude D620). In my case the device initially connects and subsequently disconnects (for good). Here are my logs:

```
Jul 18 09:42:03 spinaker kernel: [ 1362.644588] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jul 18 09:42:08 spinaker kernel: [ 1367.273894] usb 1-4: new high speed USB device using ehci_hcd and address 9
Jul 18 09:42:16 spinaker kernel: [ 1375.138271] usb 1-4: new high speed USB device using ehci_hcd and address 10
Jul 18 09:42:17 spinaker kernel: [ 1373.443537] usb 1-4: configuration #128 chosen from 1 choice
Jul 18 09:42:17 spinaker kernel: [ 1376.034589] scsi3 : SCSI emulation for USB Mass Storage devices
Jul 18 09:42:22 spinaker kernel: [ 1381.035529] scsi 3:0:0:0: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Jul 18 09:42:22 spinaker kernel: [ 1381.036776] scsi 3:0:0:1: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Jul 18 09:42:22 spinaker kernel: [ 1378.474117] sd 3:0:0:0: [sdb] 15708160 512-byte hardware sectors (8043 MB)
Jul 18 09:42:22 spinaker kernel: [ 1378.475276] sd 3:0:0:0: [sdb] Write Protect is off
Jul 18 09:42:22 spinaker kernel: [ 1378.478018] sd 3:0:0:0: [sdb] 15708160 512-byte hardware sectors (8043 MB)
Jul 18 09:42:22 spinaker kernel: [ 1378.478894] sd 3:0:0:0: [sdb] Write Protect is off
Jul 18 09:42:22 spinaker kernel: [ 1378.478909]  sdb: sdb1 sdb2
Jul 18 09:42:22 spinaker kernel: [ 1378.482462] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Jul 18 09:42:22 spinaker kernel: [ 1378.482539] sd 3:0:0:0: Attached scsi generic sg2 type 0
Jul 18 09:42:22 spinaker kernel: [ 1378.483949] sd 3:0:0:1: [sdc] Attached SCSI removable disk
Jul 18 09:42:22 spinaker kernel: [ 1378.484007] sd 3:0:0:1: Attached scsi generic sg3 type 0
Jul 18 09:42:35 spinaker kernel: [ 1392.021017] lost page write due to I/O error on sdb1
Jul 18 09:42:45 spinaker kernel: [ 1402.147297] usb 1-4: reset high speed USB device using ehci_hcd and address 10


```Do you still have problems with connecting or your devices works correctly now?

---

### Post by tytus on 2008-07-18
Amazingly, I found a very simple answer to my problems. I disabled MTP plugin in Rythmbox and the drive mounts correctly now. I was able to copy music (a bit on the slow side) and play it using Rythmbox. 

Here is the post that helped me: [http://ubuntuforums.org/showthread.php?t=771952&highlight=E280](http://ubuntuforums.org/showthread.php?t=771952&highlight=E280)

I am still interested though in how did you set the label...

---

### Post by chochem on 2008-07-18
Oh good... then I won't post my speculations about the health of your drive :oops:

As far as labelling is concerned: In Windows, I believe I just right-clicked it in Explorer, chose properties and renamed it. As simple as. In linux, I think [this]("https://help.ubuntu.com/community/RenameUSBDrive#FAT16%20and%20FAT32") cover it (you'll need to sudo apt-get install mtools).

---

