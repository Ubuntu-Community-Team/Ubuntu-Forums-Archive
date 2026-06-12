---
title: "sd card reader non-functional on Heron"
date: 2008-07-21
forum: Hardware
---

### Post by danzinho on 2008-07-21
Dear all

I have a new Dell Precision T5400 with card reader.  Hardy Heron installed wonderfully well in general, but I've just tried an SD card and it does not become visible on the system.  The light flashes after entry and then remains on, but nothing appears under /media.

I see some other people have had problems with card readers, but I haven;t found an authoritative position of whether this is a general or known unresolved problem.

Thanks

Daniel

---

### Post by coffeecat on 2008-07-21
I have no experience of that machine nor of Dells in general, but I would imagine that this is a specific problem with the card reader in your Dell. SD cards automount fine in the internal (USB) card reader I fitted to this desktop self-build, so this is not a general problem with SD cards and Ubuntu Hardy.

Have you tried one of those USB/SD-card adaptors? They don't cost much and I got one free with a 2GB SD card I bought. Ubuntu automounts an SD card in one of these fine for me also. That might be a way of seeing whether you're experiencing a problem with the Dell reader or whether there's a problem in the OS.

Another thought. You say 'an SD card' in the singular. Have you tried others? Could this be a faulty card? Have you looked at the output of dmesg when you plug the card in? If dmesg shows a response and the card is not automounted, perhaps it needs reformatting. You can do that with Gparted which you can install from Synaptic if you haven't already done so.

---

### Post by danzinho on 2008-07-21
Thanks very much, the adaptor idea is a good one.  This isn't too serious because I can connect the camera, where the SD card is from, directly to the USB.  It's just irritating when things don't work.  The card works fine in the camera - could it still be wrongly formatted?

The end of dmesg after inserting card goes like this.  I don't know if helps anyone...?

[12360.941685] sd 6:0:0:3: [sdf] 3868672 512-byte hardware sectors (1981 MB)
[12360.946044] sd 6:0:0:3: [sdf] Write Protect is off
[12360.946053] sd 6:0:0:3: [sdf] Mode Sense: 23 00 00 00
[12360.946054] sd 6:0:0:3: [sdf] Assuming drive cache: write through
[12360.950660] sd 6:0:0:3: [sdf] 3868672 512-byte hardware sectors (1981 MB)
[12360.955024] sd 6:0:0:3: [sdf] Write Protect is off
[12360.955027] sd 6:0:0:3: [sdf] Mode Sense: 23 00 00 00
[12360.955032] sd 6:0:0:3: [sdf] Assuming drive cache: write through
[12360.955036]  sdf: sdf1
[12362.518473] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12362.518482] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12362.518490] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12362.518494] end_request: I/O error, dev sdf, sector 605
[12362.518498] Buffer I/O error on device sdf1, logical block 472
[12364.052385] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12364.052393] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12364.052397] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12364.052400] end_request: I/O error, dev sdf, sector 0
[12364.052404] Buffer I/O error on device sdf, logical block 0
[12364.052411] Buffer I/O error on device sdf, logical block 1
[12364.052413] Buffer I/O error on device sdf, logical block 2
[12364.052415] Buffer I/O error on device sdf, logical block 3
[12365.566959] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12365.566973] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12365.566978] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12365.566984] end_request: I/O error, dev sdf, sector 0
[12365.566987] Buffer I/O error on device sdf, logical block 0
[12367.102871] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12367.102878] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12367.102881] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12367.102884] end_request: I/O error, dev sdf, sector 606
[12367.102888] Buffer I/O error on device sdf1, logical block 473
[12367.102892] Buffer I/O error on device sdf1, logical block 474
[12367.102894] Buffer I/O error on device sdf1, logical block 475
[12367.102895] Buffer I/O error on device sdf1, logical block 476
[12368.630030] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12368.630039] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12368.630043] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12368.630048] end_request: I/O error, dev sdf, sector 605
[12368.630051] printk: 35 messages suppressed.
[12368.630053] Buffer I/O error on device sdf1, logical block 472
[12370.165568] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12370.165583] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12370.165589] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12370.165593] end_request: I/O error, dev sdf, sector 606
[12371.692233] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12371.692247] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12371.692252] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12371.692256] end_request: I/O error, dev sdf, sector 0
[12373.225273] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12373.225284] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12373.225290] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12373.225294] end_request: I/O error, dev sdf, sector 133
[12373.225297] printk: 8 messages suppressed.
[12373.225300] Buffer I/O error on device sdf1, logical block 0
[12374.745467] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12374.745476] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12374.745480] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12374.745484] end_request: I/O error, dev sdf, sector 133
[12376.281233] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12376.281247] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12376.281253] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12376.281257] end_request: I/O error, dev sdf, sector 0
[12377.795937] sd 6:0:0:3: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12377.795945] sd 6:0:0:3: [sdf] Sense Key : Medium Error [current] 
[12377.795949] sd 6:0:0:3: [sdf] Add. Sense: Unrecovered read error
[12377.795953] end_request: I/O error, dev sdf, sector 0
[12377.795956] printk: 40 messages suppressed.
[12377.795958] Buffer I/O error on device sdf, logical block 0

---

### Post by coffeecat on 2008-07-21
If your card is coming up as sdf, then something's wrong - at least with the way it's being read by the Dell card reader. There's an awful lot of error messages there. If you can read the card by plugging the camera in, then I guess the problem probably lies with the Dell reader. Have you got Windows on there? Does the card reader work with Windows? If it does then perhaps it's not a standard USB device and Ubuntu hasn't got the driver for it.

> **danzinho said:**
> The card works fine in the camera - could it still be wrongly formatted?

I don't know. I'm mystified. And apologies for suggesting you format it in Gparted without mentioning a proviso. Some (all?) cameras format the card with folders that they use. If you format it in Gparted, the camera might not like it because the folders aren't there. And if the system is throwing up all those errors with the card in the reader, Gparted might not be able to see it anyway. But what you could do is to open up Gparted with the card in the reader (not in the camera) and see what is says about the card. Does it recognise a partition? What filesystem? It will probably be fat16 or fat32.

One last suggestion. Fat16/32 is a non-journalled filesystem. It's remotely possible that you've got a file corruption in there that's stopping it being mounted in the reader, but still enabling it to be used by the camera. I really don't know. But what you could do is to reformat the card in the camera - you should have a utility to do that in the camera menu - and then try it in the Dell card reader again.

---

### Post by rip_it on 2008-07-23
Im having the same issue with my sd card reader, except I have a toshiba Satelite laptop.  The sd card reader works with windows, I put ubuntu hardy over it, ubuntu does not recognize the card at all.  The sd card works when i put it in the digital camera I use.  Its a 2gb sd card, not sure what format it uses.  

rip_it

---

### Post by -M-ric on 2009-11-17
I got the exact same bug. I got a Sandisk SDHC 4GB category 6 extreme III. Some file copies wrapped up in a big filesystem error which corrupts the file system. I can still mount the card, sees its content. But I have a junk file of 1GB with a weird filename. I can't remove it. It always reappears after a umount/mount. But the main problem is that I struggle to reformat the card. Gparted sees the device, sees the partition. But when I tried to delete the partition, it hangs up in "error opening /dev/sde: no medium found".
When I plug the card reader into my linux PC, dmesg returns:

[107708.833932] scsi5 : SCSI emulation for USB Mass Storage devices
[107708.834529] usb-storage: device found at 33
[107708.834535] usb-storage: waiting for device to settle before scanning
[107713.825206] usb-storage: device scan complete
[107713.833186] scsi 5:0:0:0: Direct-Access     Datafab  MULTI READER     9727 PQ: 0 ANSI: 0
[107713.843042] scsi 5:0:0:1: Direct-Access     Datafab  MULTI READER     9727 PQ: 0 ANSI: 0 CCS
[107713.852775] scsi 5:0:0:2: Direct-Access     Datafab  MULTI READER     9727 PQ: 0 ANSI: 0
[107713.857460] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[107713.857533] sd 5:0:0:0: Attached scsi generic sg3 type 0
[107713.862094] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[107713.862171] sd 5:0:0:1: Attached scsi generic sg4 type 0
[107713.868807] sd 5:0:0:2: [sde] Attached SCSI removable disk
[107713.868874] sd 5:0:0:2: Attached scsi generic sg5 type 0
[107714.462104] sd 5:0:0:2: [sde] 7959552 512-byte hardware sectors (4075 MB)
[107714.464366] sd 5:0:0:2: [sde] Write Protect is off
[107714.464376] sd 5:0:0:2: [sde] Mode Sense: 03 00 00 00
[107714.464381] sd 5:0:0:2: [sde] Assuming drive cache: write through
[107714.469716] sd 5:0:0:2: [sde] 7959552 512-byte hardware sectors (4075 MB)
[107714.471464] sd 5:0:0:2: [sde] Write Protect is off
[107714.471473] sd 5:0:0:2: [sde] Mode Sense: 03 00 00 00
[107714.471477] sd 5:0:0:2: [sde] Assuming drive cache: write through
[107714.472374]  sde: sde1
[107721.423517] sd 5:0:0:2: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[107721.423530] sd 5:0:0:2: [sde] Sense Key : Hardware Error [current] 
[107721.423537] sd 5:0:0:2: [sde] Add. Sense: Data phase error
[107721.423545] end_request: I/O error, dev sde, sector 15554
[107721.423553] Buffer I/O error on device sde1, logical block 15548
[107721.423560] lost page write due to I/O error on sde1
[107721.423568] Buffer I/O error on device sde1, logical block 15549
[107721.423574] lost page write due to I/O error on sde1

I tried to reformat it on windows as well with 3 pieces of software. It failed the same way. I just don't know what to do except returning the card to the manufacturer... Any tip?

---

