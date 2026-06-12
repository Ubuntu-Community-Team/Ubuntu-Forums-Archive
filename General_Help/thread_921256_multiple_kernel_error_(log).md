---
title: "multiple kernel error (log)"
date: 2008-09-16
forum: General Help
---

### Post by allorder on 2008-09-16
I just had a crash, dunno if its relied... then I checked my kernel log and a saw multiple errors:

Sep 16 02:34:27 ubuntu kernel: [   47.487692] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
Sep 16 02:34:27 ubuntu kernel: [   47.508216] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
Sep 16 02:34:27 ubuntu kernel: [   48.412432] ppdev: user-space parallel port driver
Sep 16 02:34:27 ubuntu kernel: [   48.576231] audit(1221546867.588:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4942 profile="/usr/sbin/cupsd" namespace="default"
Sep 16 02:34:27 ubuntu kernel: [   48.628414] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Sep 16 02:34:27 ubuntu kernel: [   48.628420] apm: overridden by ACPI.
Sep 16 02:34:29 ubuntu kernel: [   50.258349] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [   50.258357] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:29 ubuntu kernel: [   50.258361] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [   50.258366] end_request: I/O error, dev sr0, sector 64
Sep 16 02:34:29 ubuntu kernel: [   50.258369] Buffer I/O error on device sr0, logical block 8
Sep 16 02:34:29 ubuntu kernel: [   50.318678] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [   50.318681] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:29 ubuntu kernel: [   50.318683] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [   50.318687] end_request: I/O error, dev sr0, sector 64
Sep 16 02:34:29 ubuntu kernel: [   50.318689] Buffer I/O error on device sr0, logical block 8
Sep 16 02:34:29 ubuntu kernel: [   50.564553] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [   50.564559] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:29 ubuntu kernel: [   50.564562] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [   50.564566] end_request: I/O error, dev sr0, sector 72
Sep 16 02:34:29 ubuntu kernel: [   50.564568] Buffer I/O error on device sr0, logical block 9
Sep 16 02:34:29 ubuntu kernel: [   50.564571] Buffer I/O error on device sr0, logical block 10
Sep 16 02:34:29 ubuntu kernel: [   50.564574] Buffer I/O error on device sr0, logical block 11
Sep 16 02:34:29 ubuntu kernel: [   50.564576] Buffer I/O error on device sr0, logical block 12
Sep 16 02:34:29 ubuntu kernel: [   50.564578] Buffer I/O error on device sr0, logical block 13
Sep 16 02:34:29 ubuntu kernel: [   50.681389] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [   50.681392] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:29 ubuntu kernel: [   50.681394] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [   50.681398] end_request: I/O error, dev sr0, sector 112
Sep 16 02:34:29 ubuntu kernel: [   50.681400] Buffer I/O error on device sr0, logical block 14
Sep 16 02:34:29 ubuntu kernel: [   50.681402] Buffer I/O error on device sr0, logical block 15
Sep 16 02:34:29 ubuntu kernel: [   50.681405] Buffer I/O error on device sr0, logical block 16
Sep 16 02:34:29 ubuntu kernel: [   50.769478] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [   50.769481] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:29 ubuntu kernel: [   50.769484] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [   50.769487] end_request: I/O error, dev sr0, sector 64
Sep 16 02:34:29 ubuntu kernel: [   50.829744] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [   50.829748] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:29 ubuntu kernel: [   50.829751] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [   50.829755] end_request: I/O error, dev sr0, sector 64
Sep 16 02:34:29 ubuntu kernel: [   50.889797] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [   50.889800] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:29 ubuntu kernel: [   50.889802] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [   50.889806] end_request: I/O error, dev sr0, sector 64
Sep 16 02:34:29 ubuntu kernel: [   50.949786] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [   50.949789] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:29 ubuntu kernel: [   50.949792] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [   50.949795] end_request: I/O error, dev sr0, sector 64
Sep 16 02:34:30 ubuntu kernel: [   51.010011] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:30 ubuntu kernel: [   51.010014] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Sep 16 02:34:30 ubuntu kernel: [   51.010017] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:30 ubuntu kernel: [   51.010020] end_request: I/O error, dev sr0, sector 64

any ideas ? :confused:

---

### Post by Jonie on 2008-09-16
> I just had a crash, dunno if its relied... then I checked my kernel log and a saw multiple errors:

Sep 16 02:34:27 ubuntu kernel: [ 47.487692] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
Sep 16 02:34:27 ubuntu kernel: [ 47.508216] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]

This just suggests broken BIOS, no need to worry

> Sep 16 02:34:29 ubuntu kernel: [ 50.258349] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 16 02:34:29 ubuntu kernel: [ 50.258357] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current]
Sep 16 02:34:29 ubuntu kernel: [ 50.258361] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep 16 02:34:29 ubuntu kernel: [ 50.258366] end_request: I/O error, dev sr0, sector 64
Sep 16 02:34:29 ubuntu kernel: [ 50.258369] Buffer I/O error on device sr0, logical block 8

If the cause is not by chance a badly scratched CD, you may look at this post:

[http://ubuntuforums.org/showthread.php?t=726656]("http://ubuntuforums.org/showthread.php?t=726656")

I've also seen some similar issues on SIS chipset when using libata. Are you using SIS chipset?

---

### Post by allorder on 2008-09-17
> **Jonie said:**
> If the cause is not by chance a badly scratched CD, 
I've also seen some similar issues on SIS chipset when using libata. Are you using SIS chipset?

Thanks, it was the cd [-(

no its not a SIS :>

---

