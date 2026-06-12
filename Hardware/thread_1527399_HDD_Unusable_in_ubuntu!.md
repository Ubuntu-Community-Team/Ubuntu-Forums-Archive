---
title: "HDD Unusable in ubuntu!"
date: 2010-07-09
forum: Hardware
---

### Post by revered on 2010-07-09
I have ubuntu in a sata hdd and a secondary pata hdd with ntfs partition.
This second disk cannot be used in ubuntu, it almost always fails at startup, heres the syslog part that "talks" about that hdd:

```
Jul  9 09:12:13 desktop kernel: [  225.804527] ata3: lost interrupt (Status 0x51)
Jul  9 09:12:18 desktop kernel: [  230.808030] ata3.01: qc timeout (cmd 0xa0)
Jul  9 09:12:18 desktop kernel: [  230.808042] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul  9 09:12:18 desktop kernel: [  230.808047] sr 7:0:1:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Jul  9 09:12:18 desktop kernel: [  230.808059] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jul  9 09:12:18 desktop kernel: [  230.808060]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Jul  9 09:12:18 desktop kernel: [  230.808063] ata3.01: status: { DRDY ERR }
Jul  9 09:12:18 desktop kernel: [  230.808096] ata3: soft resetting link
Jul  9 09:12:24 desktop kernel: [  236.160048] ata3.00: qc timeout (cmd 0xf8)
Jul  9 09:12:24 desktop kernel: [  236.160057] ata3.00: failed to read native max address (err_mask=0x4)
Jul  9 09:12:24 desktop kernel: [  236.160060] ata3.00: revalidation failed (errno=-5)
Jul  9 09:12:24 desktop kernel: [  236.160097] ata3: soft resetting link
Jul  9 09:12:34 desktop kernel: [  246.516044] ata3.00: qc timeout (cmd 0xf8)
Jul  9 09:12:34 desktop kernel: [  246.516055] ata3.00: failed to read native max address (err_mask=0x4)
Jul  9 09:12:34 desktop kernel: [  246.516061] ata3.00: revalidation failed (errno=-5)
Jul  9 09:12:34 desktop kernel: [  246.516101] ata3: soft resetting link
Jul  9 09:12:44 desktop kernel: [  256.872049] ata3.00: qc timeout (cmd 0xf8)
Jul  9 09:12:44 desktop kernel: [  256.872060] ata3.00: failed to read native max address (err_mask=0x4)
Jul  9 09:12:44 desktop kernel: [  256.872066] ata3.00: revalidation failed (errno=-5)
Jul  9 09:12:44 desktop kernel: [  256.872071] ata3.00: disabled
Jul  9 09:12:44 desktop kernel: [  256.872085] ata3: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jul  9 09:12:44 desktop kernel: [  256.872090] ata3.01: limited to UDMA/33 due to 40-wire cable
Jul  9 09:12:44 desktop kernel: [  256.872117] ata3.01: failed to set xfermode (err_mask=0x40)
Jul  9 09:12:44 desktop kernel: [  256.872150] ata3: soft resetting link
Jul  9 09:12:45 desktop kernel: [  257.220532] ata3: nv_mode_filter: 0x739f&0x1f39f->0x739f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jul  9 09:12:45 desktop kernel: [  257.252459] ata3.01: configured for UDMA/33
Jul  9 09:12:50 desktop kernel: [  262.252044] ata3.01: qc timeout (cmd 0xa0)
Jul  9 09:12:50 desktop kernel: [  262.252055] ata3.01: TEST_UNIT_READY failed (err_mask=0x5)
Jul  9 09:12:50 desktop kernel: [  262.252061] ata3.01: limiting speed to UDMA/33:PIO3
Jul  9 09:12:50 desktop kernel: [  262.252099] ata3: soft resetting link
Jul  9 09:12:50 desktop kernel: [  262.600518] ata3: nv_mode_filter: 0x738f&0x1f39f->0x738f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jul  9 09:12:50 desktop kernel: [  262.632445] ata3.01: configured for UDMA/33
Jul  9 09:12:55 desktop kernel: [  267.632046] ata3.01: qc timeout (cmd 0xa0)
Jul  9 09:12:55 desktop kernel: [  267.632056] ata3.01: TEST_UNIT_READY failed (err_mask=0x5)
Jul  9 09:12:55 desktop kernel: [  267.632060] ata3.01: disabled
Jul  9 09:12:55 desktop kernel: [  267.632113] ata3: soft resetting link
Jul  9 09:12:55 desktop kernel: [  267.956122] ata3: EH complete
Jul  9 09:12:55 desktop kernel: [  267.956263] sd 7:0:0:0: [sdb] READ CAPACITY(16) failed
Jul  9 09:12:55 desktop kernel: [  267.956268] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul  9 09:12:55 desktop kernel: [  267.956275] sd 7:0:0:0: [sdb] Sense not available.
Jul  9 09:12:55 desktop kernel: [  267.956348] sd 7:0:0:0: [sdb] READ CAPACITY failed
Jul  9 09:12:55 desktop kernel: [  267.956352] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul  9 09:12:55 desktop kernel: [  267.956358] sd 7:0:0:0: [sdb] Sense not available.
Jul  9 09:12:55 desktop kernel: [  267.956479] sd 7:0:0:0: [sdb] Asking for cache data failed
Jul  9 09:12:55 desktop kernel: [  267.956484] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Jul  9 09:12:55 desktop kernel: [  267.956492] sdb: detected capacity change from 40020664320 to 0
```As you can see in the last line of the syslog, the hdd changes capacity from 40gb to 0, and I cant use it then. I still can see the disk in "disk utility" but it shows like if it has no partitions.

What could be causing this? the disk is a [Seagate ATA ST340810A]("http://www.seagate.com/ww/v/index.jsp?vgnextoid=fffb5a802efbd010VgnVCM100000dd04090aRCRD&locale=en-US&reqPage=Legacy")
Is there something I could try to fix it? Or if I reformat this disk to ext4, would it stop this error? (I dont want to delete everything if it will still have the same error)

---

