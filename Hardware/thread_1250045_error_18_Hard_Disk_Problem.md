---
title: "error 18 :Hard Disk Problem"
date: 2009-08-26
forum: Hardware
---

### Post by pranjalsaxena on 2009-08-26
Hi All,

I have ubuntu 9.04
(It was working fine the last night but today morning strange things happened)

When I boot my system it shows

Grub stage 1.5
Loading Grub 
Error 18

And then nothing happens.

I tried reinstalling the grub using live CD.
But it cannot find /boot/grub/stage1

I tried fdisk -l but it says 
unable to read /dev/sda

I tried installing ubuntu just to view the partitions 
But its partition manager is not showing any partitions

I also tried Gparted .it is also no showing any partitions its just saying that there is 74.5GB unallocated space 

I have 80GB hardisk with 3 partitions one for windows(16GB),one 40GB partition (ntfs) for data and rest for ubuntu
Live CD is showing that I have a 16GB partition but is not showing the 40GB one.

And when I try to open 16 GB disk it says:

ntfs_attr_pread_i:ntfs_pread failed:input/output error
Failed to read $MFTMirr:Input/output error failed to mount /dev/sda1.....

(there is more in the details if it is needed please tell  will post the complete error)

I also tried to fix the MBR using windows CD (FIXMBR) but to no effect
when I typed FIXBOOT it gave some error which I don't remember exactly but it said something like unable to access disk

And one more thing I checked /etc/fstab it is empty

Here is the output of dmesg

```

66] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  241.514081] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  241.514084] ata1.00: BMDMA stat 0x25
[  241.514090] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  241.514092]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  241.514096] ata1.00: status: { DRDY ERR }
[  241.514098] ata1.00: error: { IDNF }
[  241.536537] ata1.00: configured for UDMA/100
[  241.536543] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  241.536547] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  241.536553] Descriptor sense data with sense descriptors (in hex):
[  241.536556]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  241.536568]         09 50 f8 a8 
[  241.536574] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  241.536579] end_request: I/O error, dev sda, sector 156301480
[  241.536583] Buffer I/O error on device sda, logical block 19537685
[  241.536593] ata1: EH complete
[  241.536687] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  242.963220] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  242.963223] ata1.00: BMDMA stat 0x25
[  242.963229] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  242.963230]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  242.963234] ata1.00: status: { DRDY ERR }
[  242.963237] ata1.00: error: { IDNF }
[  242.984517] ata1.00: configured for UDMA/100
[  242.984523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  242.984527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  242.984533] Descriptor sense data with sense descriptors (in hex):
[  242.984535]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  242.984548]         09 50 f8 a8 
[  242.984553] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  242.984559] end_request: I/O error, dev sda, sector 156301480
[  242.984562] Buffer I/O error on device sda, logical block 19537685
[  242.984572] ata1: EH complete
[  242.984589] sd 0:0:0:0: [sda] Write Protect is off
[  242.984592] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  244.423421] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  244.423424] ata1.00: BMDMA stat 0x25
[  244.423430] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  244.423432]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  244.423436] ata1.00: status: { DRDY ERR }
[  244.423438] ata1.00: error: { IDNF }
[  244.444504] ata1.00: configured for UDMA/100
[  244.444510] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  244.444514] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  244.444520] Descriptor sense data with sense descriptors (in hex):
[  244.444523]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  244.444535]         09 50 f8 a8 
[  244.444540] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  244.444546] end_request: I/O error, dev sda, sector 156301480
[  244.444549] Buffer I/O error on device sda, logical block 19537685
[  244.444559] ata1: EH complete
[  244.444651] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  245.905747] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  245.905750] ata1.00: BMDMA stat 0x25
[  245.905756] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  245.905757]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  245.905761] ata1.00: status: { DRDY ERR }
[  245.905764] ata1.00: error: { IDNF }
[  245.928503] ata1.00: configured for UDMA/100
[  245.928508] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  245.928513] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  245.928518] Descriptor sense data with sense descriptors (in hex):
[  245.928521]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  245.928534]         09 50 f8 a8 
[  245.928539] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  245.928544] end_request: I/O error, dev sda, sector 156301480
[  245.928548] Buffer I/O error on device sda, logical block 19537685
[  245.928558] ata1: EH complete
[  245.928596] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  247.365947] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  247.365950] ata1.00: BMDMA stat 0x25
[  247.365956] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  247.365958]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  247.365962] ata1.00: status: { DRDY ERR }
[  247.365964] ata1.00: error: { IDNF }
[  247.388534] ata1.00: configured for UDMA/100
[  247.388539] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  247.388544] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  247.388549] Descriptor sense data with sense descriptors (in hex):
[  247.388552]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  247.388565]         09 50 f8 a8 
[  247.388570] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  247.388575] end_request: I/O error, dev sda, sector 156301480
[  247.388579] Buffer I/O error on device sda, logical block 19537685
[  247.388589] ata1: EH complete
[  247.388606] sd 0:0:0:0: [sda] Write Protect is off
[  247.388609] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  248.770838] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  248.770841] ata1.00: BMDMA stat 0x25
[  248.770847] ata1.00: cmd c8/00:08:70:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  248.770849]          res 51/10:08:70:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  248.770852] ata1.00: status: { DRDY ERR }
[  248.770855] ata1.00: error: { IDNF }
[  248.792462] ata1.00: configured for UDMA/100
[  248.792467] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  248.792472] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  248.792477] Descriptor sense data with sense descriptors (in hex):
[  248.792480]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  248.792493]         09 50 f8 70 
[  248.792498] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  248.792503] end_request: I/O error, dev sda, sector 156301424
[  248.792507] Buffer I/O error on device sda, logical block 19537678
[  248.792517] ata1: EH complete
[  248.792533] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  250.242101] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  250.242104] ata1.00: BMDMA stat 0x25
[  250.242110] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  250.242112]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  250.242115] ata1.00: status: { DRDY ERR }
[  250.242118] ata1.00: error: { IDNF }
[  250.264471] ata1.00: configured for UDMA/100
[  250.264476] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  250.264480] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  250.264486] Descriptor sense data with sense descriptors (in hex):
[  250.264489]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  250.264502]         09 50 f8 a0 
[  250.264507] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  250.264512] end_request: I/O error, dev sda, sector 156301472
[  250.264516] Buffer I/O error on device sda, logical block 19537684
[  250.264526] ata1: EH complete
[  250.264544] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  251.746551] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  251.746554] ata1.00: BMDMA stat 0x25
[  251.746560] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  251.746561]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  251.746565] ata1.00: status: { DRDY ERR }
[  251.746568] ata1.00: error: { IDNF }
[  251.768515] ata1.00: configured for UDMA/100
[  251.768521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  251.768525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  251.768531] Descriptor sense data with sense descriptors (in hex):
[  251.768534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  251.768546]         09 50 f8 a8 
[  251.768551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  251.768557] end_request: I/O error, dev sda, sector 156301480
[  251.768560] Buffer I/O error on device sda, logical block 19537685
[  251.768570] ata1: EH complete
[  251.768587] sd 0:0:0:0: [sda] Write Protect is off
[  251.768590] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  253.251000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  253.251003] ata1.00: BMDMA stat 0x25
[  253.251009] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  253.251010]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  253.251014] ata1.00: status: { DRDY ERR }
[  253.251017] ata1.00: error: { IDNF }
[  253.272518] ata1.00: configured for UDMA/100
[  253.272524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  253.272528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  253.272534] Descriptor sense data with sense descriptors (in hex):
[  253.272536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  253.272549]         09 50 f8 a8 
[  253.272554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  253.272560] end_request: I/O error, dev sda, sector 156301480
[  253.272563] Buffer I/O error on device sda, logical block 19537685
[  253.272573] ata1: EH complete
[  253.272605] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  253.272641] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  253.303221] sd 0:0:0:0: [sda] Write Protect is off
[  253.303225] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  253.303974] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  254.711214] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  254.711220] ata1.00: BMDMA stat 0x25
[  254.711228] ata1.00: cmd c8/00:01:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  254.711229]          res 51/10:01:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  254.711234] ata1.00: status: { DRDY ERR }
[  254.711236] ata1.00: error: { IDNF }
[  254.732516] ata1.00: configured for UDMA/100
[  254.732526] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  254.732531] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  254.732538] Descriptor sense data with sense descriptors (in hex):
[  254.732541]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  254.732554]         01 e4 60 bf 
[  254.732559] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  254.732566] end_request: I/O error, dev sda, sector 31744191
[  254.732571] Buffer I/O error on device sda1, logical block 31744128
[  254.732582] ata1: EH complete
[  257.576297] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  257.576300] ata1.00: BMDMA stat 0x25
[  257.576306] ata1.00: cmd c8/00:07:c0:60:e4/00:00:00:00:00/e1 tag 0 dma 3584 in
[  257.576308]          res 51/10:07:c0:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  257.576312] ata1.00: status: { DRDY ERR }
[  257.576314] ata1.00: error: { IDNF }
[  257.600516] ata1.00: configured for UDMA/100
[  257.600523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  257.600527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  257.600533] Descriptor sense data with sense descriptors (in hex):
[  257.600536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  257.600549]         01 e4 60 c0 
[  257.600554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  257.600559] end_request: I/O error, dev sda, sector 31744192
[  257.600563] Buffer I/O error on device sda1, logical block 31744129
[  257.600567] Buffer I/O error on device sda1, logical block 31744130
[  257.600571] Buffer I/O error on device sda1, logical block 31744131
[  257.600575] Buffer I/O error on device sda1, logical block 31744132
[  257.600578] Buffer I/O error on device sda1, logical block 31744133
[  257.600582] Buffer I/O error on device sda1, logical block 31744134
[  257.600586] Buffer I/O error on device sda1, logical block 31744135
[  257.600596] ata1: EH complete
[  257.600680] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  259.047560] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  259.047563] ata1.00: BMDMA stat 0x25
[  259.047569] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  259.047571]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  259.047574] ata1.00: status: { DRDY ERR }
[  259.047577] ata1.00: error: { IDNF }
[  259.068537] ata1.00: configured for UDMA/100
[  259.068543] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  259.068547] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  259.068553] Descriptor sense data with sense descriptors (in hex):
[  259.068556]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  259.068568]         01 e4 61 b8 
[  259.068573] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  259.068579] end_request: I/O error, dev sda, sector 31744440
[  259.068583] Buffer I/O error on device sda2, logical block 0
[  259.068592] ata1: EH complete
[  259.068665] sd 0:0:0:0: [sda] Write Protect is off
[  259.068669] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  260.540946] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  260.540949] ata1.00: BMDMA stat 0x25
[  260.540955] ata1.00: cmd c8/00:08:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  260.540956]          res 51/10:08:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  260.540960] ata1.00: status: { DRDY ERR }
[  260.540963] ata1.00: error: { IDNF }
[  260.564515] ata1.00: configured for UDMA/100
[  260.564521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  260.564525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  260.564531] Descriptor sense data with sense descriptors (in hex):
[  260.564534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  260.564546]         01 e4 60 bf 
[  260.564551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  260.564557] end_request: I/O error, dev sda, sector 31744191
[  260.564561] Buffer I/O error on device sda1, logical block 31744128
[  260.564565] Buffer I/O error on device sda1, logical block 31744129
[  260.564569] Buffer I/O error on device sda1, logical block 31744130
[  260.564572] Buffer I/O error on device sda1, logical block 31744131
[  260.564576] Buffer I/O error on device sda1, logical block 31744132
[  260.564580] Buffer I/O error on device sda1, logical block 31744133
[  260.564583] Buffer I/O error on device sda1, logical block 31744134
[  260.564587] Buffer I/O error on device sda1, logical block 31744135
[  260.564600] ata1: EH complete
[  262.034333] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  262.034336] ata1.00: BMDMA stat 0x25
[  262.034342] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  262.034344]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  262.034347] ata1.00: status: { DRDY ERR }
[  262.034350] ata1.00: error: { IDNF }
[  262.056518] ata1.00: configured for UDMA/100
[  262.056524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  262.056528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  262.056533] Descriptor sense data with sense descriptors (in hex):
[  262.056536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  262.056549]         01 e4 61 b8 
[  262.056554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  262.056560] end_request: I/O error, dev sda, sector 31744440
[  262.056563] Buffer I/O error on device sda2, logical block 0
[  262.056572] ata1: EH complete
[  262.056644] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  263.538788] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  263.538791] ata1.00: BMDMA stat 0x25
[  263.538798] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  263.538800]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  263.538803] ata1.00: status: { DRDY ERR }
[  263.538806] ata1.00: error: { IDNF }
[  263.560516] ata1.00: configured for UDMA/100
[  263.560525] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  263.560530] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  263.560535] Descriptor sense data with sense descriptors (in hex):
[  263.560538]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  263.560551]         01 e4 61 a7 
[  263.560556] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  263.560562] end_request: I/O error, dev sda, sector 31744423
[  263.560566] Buffer I/O error on device sda1, logical block 31744360
[  263.560585] ata1: EH complete
[  263.560693] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  264.987921] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  264.987924] ata1.00: BMDMA stat 0x25
[  264.987930] ata1.00: cmd c8/00:05:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 2560 in
[  264.987931]          res 51/10:05:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  264.987935] ata1.00: status: { DRDY ERR }
[  264.987938] ata1.00: error: { IDNF }
[  265.012515] ata1.00: configured for UDMA/100
[  265.012521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  265.012525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  265.012531] Descriptor sense data with sense descriptors (in hex):
[  265.012534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  265.012546]         01 e4 61 a7 
[  265.012551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  265.012557] end_request: I/O error, dev sda, sector 31744423
[  265.012568] ata1: EH complete
[  265.012640] sd 0:0:0:0: [sda] Write Protect is off
[  265.012643] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  266.602991] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  266.602994] ata1.00: BMDMA stat 0x25
[  266.603000] ata1.00: cmd c8/00:03:ac:61:e4/00:00:00:00:00/e1 tag 0 dma 1536 in
[  266.603002]          res 51/10:03:ac:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  266.603006] ata1.00: status: { DRDY ERR }
[  266.603008] ata1.00: error: { IDNF }
[  266.624517] ata1.00: configured for UDMA/100
[  266.624523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  266.624527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  266.624533] Descriptor sense data with sense descriptors (in hex):
[  266.624535]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  266.624548]         01 e4 61 ac 
[  266.624553] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  266.624559] end_request: I/O error, dev sda, sector 31744428
[  266.624562] __ratelimit: 12 callbacks suppressed
[  266.624565] Buffer I/O error on device sda1, logical block 31744365
[  266.624570] Buffer I/O error on device sda1, logical block 31744366
[  266.624573] Buffer I/O error on device sda1, logical block 31744367
[  266.624583] ata1: EH complete
[  266.624617] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  266.655647] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  266.655996] sd 0:0:0:0: [sda] Write Protect is off
[  266.656000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  268.085318] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  268.085321] ata1.00: BMDMA stat 0x25
[  268.085327] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  268.085328]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  268.085332] ata1.00: status: { DRDY ERR }
[  268.085335] ata1.00: error: { IDNF }
[  268.108540] ata1.00: configured for UDMA/100
[  268.108546] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  268.108550] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  268.108556] Descriptor sense data with sense descriptors (in hex):
[  268.108559]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  268.108571]         01 e4 61 b7 
[  268.108576] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  268.108582] end_request: I/O error, dev sda, sector 31744439
[  268.108586] Buffer I/O error on device sda1, logical block 31744376
[  268.108596] ata1: EH complete
[  269.600829] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  269.600832] ata1.00: BMDMA stat 0x25
[  269.600838] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  269.600840]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  269.600843] ata1.00: status: { DRDY ERR }
[  269.600846] ata1.00: error: { IDNF }
[  269.624514] ata1.00: configured for UDMA/100
[  269.624519] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  269.624524] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  269.624529] Descriptor sense data with sense descriptors (in hex):
[  269.624532]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  269.624545]         01 e4 61 b7 
[  269.624550] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  269.624555] end_request: I/O error, dev sda, sector 31744439
[  269.624559] Buffer I/O error on device sda1, logical block 31744376
[  269.624569] ata1: EH complete
[  269.624586] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  269.624685] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  271.049968] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  271.049971] ata1.00: BMDMA stat 0x25
[  271.049977] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  271.049979]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  271.049982] ata1.00: status: { DRDY ERR }
[  271.049985] ata1.00: error: { IDNF }
[  271.072517] ata1.00: configured for UDMA/100
[  271.072523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  271.072527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  271.072533] Descriptor sense data with sense descriptors (in hex):
[  271.072536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  271.072549]         01 e4 61 af 
[  271.072554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  271.072559] end_request: I/O error, dev sda, sector 31744431
[  271.072563] Buffer I/O error on device sda1, logical block 31744368
[  271.072567] Buffer I/O error on device sda1, logical block 31744369
[  271.072570] Buffer I/O error on device sda1, logical block 31744370
[  271.072574] Buffer I/O error on device sda1, logical block 31744371
[  271.072578] Buffer I/O error on device sda1, logical block 31744372
[  271.072589] ata1: EH complete
[  271.072606] sd 0:0:0:0: [sda] Write Protect is off
[  271.072609] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  272.510167] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  272.510170] ata1.00: BMDMA stat 0x25
[  272.510176] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  272.510178]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  272.510182] ata1.00: status: { DRDY ERR }
[  272.510184] ata1.00: error: { IDNF }
[  272.532516] ata1.00: configured for UDMA/100
[  272.532522] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  272.532526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  272.532532] Descriptor sense data with sense descriptors (in hex):
[  272.532535]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  272.532547]         01 e4 61 b7 
[  272.532552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  272.532558] end_request: I/O error, dev sda, sector 31744439
[  272.532561] __ratelimit: 3 callbacks suppressed
[  272.532564] Buffer I/O error on device sda1, logical block 31744376
[  272.532574] ata1: EH complete
[  272.532591] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  273.970371] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  273.970374] ata1.00: BMDMA stat 0x25
[  273.970379] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  273.970381]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  273.970385] ata1.00: status: { DRDY ERR }
[  273.970387] ata1.00: error: { IDNF }
[  273.992516] ata1.00: configured for UDMA/100
[  273.992522] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  273.992526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  273.992531] Descriptor sense data with sense descriptors (in hex):
[  273.992534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  273.992547]         01 e4 61 b7 
[  273.992552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  273.992557] end_request: I/O error, dev sda, sector 31744439
[  273.992561] Buffer I/O error on device sda1, logical block 31744376
[  273.992571] ata1: EH complete
[  273.992589] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  273.992670] sd 0:0:0:0: [sda] Write Protect is off
[  273.992673] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  275.441635] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  275.441638] ata1.00: BMDMA stat 0x25
[  275.441644] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  275.441646]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  275.441650] ata1.00: status: { DRDY ERR }
[  275.441652] ata1.00: error: { IDNF }
[  275.464503] ata1.00: configured for UDMA/100
[  275.464509] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  275.464513] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  275.464518] Descriptor sense data with sense descriptors (in hex):
[  275.464521]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  275.464534]         01 e4 61 b7 
[  275.464539] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  275.464544] end_request: I/O error, dev sda, sector 31744439
[  275.464548] Buffer I/O error on device sda1, logical block 31744376
[  275.464558] ata1: EH complete
[  275.464654] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  276.879711] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  276.879714] ata1.00: BMDMA stat 0x25
[  276.879720] ata1.00: cmd c8/00:06:af:61:e4/00:00:00:00:00/e1 tag 0 dma 3072 in
[  276.879722]          res 51/10:06:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  276.879726] ata1.00: status: { DRDY ERR }
[  276.879728] ata1.00: error: { IDNF }
[  276.900504] ata1.00: configured for UDMA/100
[  276.900510] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  276.900514] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  276.900519] Descriptor sense data with sense descriptors (in hex):
[  276.900522]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  276.900535]         01 e4 61 af 
[  276.900540] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  276.900545] end_request: I/O error, dev sda, sector 31744431
[  276.900549] Buffer I/O error on device sda1, logical block 31744368
[  276.900553] Buffer I/O error on device sda1, logical block 31744369
[  276.900557] Buffer I/O error on device sda1, logical block 31744370
[  276.900561] Buffer I/O error on device sda1, logical block 31744371
[  276.900564] Buffer I/O error on device sda1, logical block 31744372
[  276.900568] Buffer I/O error on device sda1, logical block 31744373
[  276.900576] ata1: EH complete
[  278.339912] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  278.339916] ata1.00: BMDMA stat 0x25
[  278.339921] ata1.00: cmd c8/00:02:b5:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  278.339923]          res 51/10:02:b5:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  278.339927] ata1.00: status: { DRDY ERR }
[  278.339929] ata1.00: error: { IDNF }
[  278.364502] ata1.00: configured for UDMA/100
[  278.364508] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  278.364512] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  278.364518] Descriptor sense data with sense descriptors (in hex):
[  278.364521]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  278.364534]         01 e4 61 b5 
[  278.364539] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  278.364544] end_request: I/O error, dev sda, sector 31744437
[  278.364548] Buffer I/O error on device sda1, logical block 31744374
[  278.364559] ata1: EH complete
[  278.364577] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  278.364661] sd 0:0:0:0: [sda] Write Protect is off
[  278.364665] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  279.766927] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  279.766930] ata1.00: BMDMA stat 0x25
[  279.766936] ata1.00: cmd c8/00:06:77:61:e4/00:00:00:00:00/e1 tag 0 dma 3072 in
[  279.766938]          res 51/10:06:77:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  279.766942] ata1.00: status: { DRDY ERR }
[  279.766944] ata1.00: error: { IDNF }
[  279.788486] ata1.00: configured for UDMA/100
[  279.788491] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  279.788496] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  279.788501] Descriptor sense data with sense descriptors (in hex):
[  279.788504]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  279.788517]         01 e4 61 77 
[  279.788522] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  279.788527] end_request: I/O error, dev sda, sector 31744375
[  279.788531] __ratelimit: 1 callbacks suppressed
[  279.788534] Buffer I/O error on device sda1, logical block 31744312
[  279.788538] Buffer I/O error on device sda1, logical block 31744313
[  279.788541] Buffer I/O error on device sda1, logical block 31744314
[  279.788545] Buffer I/O error on device sda1, logical block 31744315
[  279.788549] Buffer I/O error on device sda1, logical block 31744316
[  279.788552] Buffer I/O error on device sda1, logical block 31744317
[  279.788560] ata1: EH complete
[  281.393060] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  281.393063] ata1.00: BMDMA stat 0x25
[  281.393069] ata1.00: cmd c8/00:02:7d:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  281.393071]          res 51/10:02:7d:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  281.393075] ata1.00: status: { DRDY ERR }
[  281.393077] ata1.00: error: { IDNF }
[  281.416479] ata1.00: configured for UDMA/100
[  281.416485] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  281.416489] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  281.416495] Descriptor sense data with sense descriptors (in hex):
[  281.416498]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  281.416510]         01 e4 61 7d 
[  281.416515] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  281.416521] end_request: I/O error, dev sda, sector 31744381
[  281.416525] Buffer I/O error on device sda1, logical block 31744318
[  281.416529] Buffer I/O error on device sda1, logical block 31744319
[  281.416539] ata1: EH complete
[  281.416555] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  282.864325] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  282.864328] ata1.00: BMDMA stat 0x25
[  282.864334] ata1.00: cmd c8/00:04:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 2048 in
[  282.864336]          res 51/10:04:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  282.864339] ata1.00: status: { DRDY ERR }
[  282.864342] ata1.00: error: { IDNF }
[  282.888517] ata1.00: configured for UDMA/100
[  282.888523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  282.888527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  282.888532] Descriptor sense data with sense descriptors (in hex):
[  282.888535]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  282.888548]         01 e4 61 a7 
[  282.888553] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  282.888558] end_request: I/O error, dev sda, sector 31744423
[  282.888562] Buffer I/O error on device sda1, logical block 31744360
[  282.888566] Buffer I/O error on device sda1, logical block 31744361
[  282.888575] ata1: EH complete
[  282.888648] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  284.501519] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  284.501522] ata1.00: BMDMA stat 0x25
[  284.501527] ata1.00: cmd c8/00:04:ab:61:e4/00:00:00:00:00/e1 tag 0 dma 2048 in
[  284.501529]          res 51/10:04:ab:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  284.501533] ata1.00: status: { DRDY ERR }
[  284.501535] ata1.00: error: { IDNF }
[  284.524514] ata1.00: configured for UDMA/100
[  284.524520] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  284.524524] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  284.524530] Descriptor sense data with sense descriptors (in hex):
[  284.524533]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  284.524546]         01 e4 61 ab 
[  284.524551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  284.524556] end_request: I/O error, dev sda, sector 31744427
[  284.524569] ata1: EH complete
[  284.524585] sd 0:0:0:0: [sda] Write Protect is off
[  284.524588] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  285.939599] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  285.939602] ata1.00: BMDMA stat 0x25
[  285.939608] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  285.939609]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  285.939613] ata1.00: status: { DRDY ERR }
[  285.939615] ata1.00: error: { IDNF }
[  285.960515] ata1.00: configured for UDMA/100
[  285.960521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  285.960525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  285.960530] Descriptor sense data with sense descriptors (in hex):
[  285.960533]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  285.960546]         01 e4 61 b7 
[  285.960551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  285.960556] end_request: I/O error, dev sda, sector 31744439
[  285.960560] __ratelimit: 6 callbacks suppressed
[  285.960563] Buffer I/O error on device sda1, logical block 31744376
[  285.960573] ata1: EH complete
[  285.960665] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  287.377676] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  287.377679] ata1.00: BMDMA stat 0x25
[  287.377685] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  287.377686]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  287.377690] ata1.00: status: { DRDY ERR }
[  287.377693] ata1.00: error: { IDNF }
[  287.400517] ata1.00: configured for UDMA/100
[  287.400523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  287.400527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  287.400533] Descriptor sense data with sense descriptors (in hex):
[  287.400536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  287.400548]         01 e4 61 b7 
[  287.400554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  287.400559] end_request: I/O error, dev sda, sector 31744439
[  287.400563] Buffer I/O error on device sda1, logical block 31744376
[  287.400573] ata1: EH complete
[  287.400605] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  287.400626] sd 0:0:0:0: [sda] Write Protect is off
[  287.400629] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  287.430563] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  287.431323] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  287.431708] sd 0:0:0:0: [sda] Write Protect is off
[  287.431711] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  287.432388] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  292.500137] Clocksource tsc unstable (delta = -164184383 ns)
[  302.223083] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  302.223089] ata1.00: BMDMA stat 0x25
[  302.223097] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  302.223098]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  302.223103] ata1.00: status: { DRDY ERR }
[  302.223105] ata1.00: error: { IDNF }
[  302.244518] ata1.00: configured for UDMA/100
[  302.244532] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  302.244538] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  302.244544] Descriptor sense data with sense descriptors (in hex):
[  302.244547]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  302.244560]         01 e4 61 b8 
[  302.244565] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  302.244572] end_request: I/O error, dev sda, sector 31744440
[  302.244578] Buffer I/O error on device sda, logical block 3968055
[  302.244596] ata1: EH complete
[  303.672201] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  303.672204] ata1.00: BMDMA stat 0x25
[  303.672211] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  303.672212]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  303.672216] ata1.00: status: { DRDY ERR }
[  303.672219] ata1.00: error: { IDNF }
[  303.696518] ata1.00: configured for UDMA/100
[  303.696525] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  303.696529] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  303.696535] Descriptor sense data with sense descriptors (in hex):
[  303.696538]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  303.696551]         01 e4 61 b8 
[  303.696556] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  303.696562] end_request: I/O error, dev sda, sector 31744440
[  303.696565] Buffer I/O error on device sda, logical block 3968055
[  303.696577] ata1: EH complete
[  303.696600] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  303.696626] sd 0:0:0:0: [sda] Write Protect is off
[  303.696629] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  303.696664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  303.696701] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  303.696720] sd 0:0:0:0: [sda] Write Protect is off
[  303.696723] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  303.696872] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  305.143474] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  305.143480] ata1.00: BMDMA stat 0x25
[  305.143487] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  305.143489]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  305.143493] ata1.00: status: { DRDY ERR }
[  305.143496] ata1.00: error: { IDNF }
[  305.164516] ata1.00: configured for UDMA/100
[  305.164530] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  305.164535] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  305.164542] Descriptor sense data with sense descriptors (in hex):
[  305.164545]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  305.164558]         01 e4 61 b8 
[  305.164563] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  305.164569] end_request: I/O error, dev sda, sector 31744440
[  305.164575] Buffer I/O error on device sda2, logical block 0
[  305.164592] ata1: EH complete
[  306.636849] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  306.636852] ata1.00: BMDMA stat 0x25
[  306.636858] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  306.636860]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  306.636864] ata1.00: status: { DRDY ERR }
[  306.636866] ata1.00: error: { IDNF }
[  306.660506] ata1.00: configured for UDMA/100
[  306.660513] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  306.660517] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  306.660523] Descriptor sense data with sense descriptors (in hex):
[  306.660526]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  306.660539]         01 e4 61 b8 
[  306.660544] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  306.660549] end_request: I/O error, dev sda, sector 31744440
[  306.660553] Buffer I/O error on device sda2, logical block 0
[  306.660564] ata1: EH complete
[  306.660587] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  306.660612] sd 0:0:0:0: [sda] Write Protect is off
[  306.660615] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  306.660716] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  306.688928] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  308.108112] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  308.108116] ata1.00: BMDMA stat 0x25
[  308.108122] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  308.108123]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  308.108127] ata1.00: status: { DRDY ERR }
[  308.108130] ata1.00: error: { IDNF }
[  308.132505] ata1.00: configured for UDMA/100
[  308.132512] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  308.132517] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  308.132523] Descriptor sense data with sense descriptors (in hex):
[  308.132525]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  308.132538]         01 e4 61 b8 
[  308.132543] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  308.132549] end_request: I/O error, dev sda, sector 31744440
[  308.132553] Buffer I/O error on device sda, logical block 3968055
[  308.132564] ata1: EH complete
[  308.132582] sd 0:0:0:0: [sda] Write Protect is off
[  308.132586] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  309.535126] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  309.535130] ata1.00: BMDMA stat 0x25
[  309.535136] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  309.535137]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  309.535141] ata1.00: status: { DRDY ERR }
[  309.535144] ata1.00: error: { IDNF }
[  309.556503] ata1.00: configured for UDMA/100
[  309.556510] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  309.556514] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  309.556520] Descriptor sense data with sense descriptors (in hex):
[  309.556523]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  309.556535]         01 e4 61 b8 
[  309.556540] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  309.556546] end_request: I/O error, dev sda, sector 31744440
[  309.556550] Buffer I/O error on device sda, logical block 3968055
[  309.556561] ata1: EH complete
[  309.556595] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  309.556632] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  309.556651] sd 0:0:0:0: [sda] Write Protect is off
[  309.556655] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  309.556687] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  310.368520] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  310.368524] Bluetooth: BNEP filters: protocol multicast
[  310.412527] Bridge firewalling registered
[  317.346748] lp: driver loaded but no devices found
[  317.421050] ppdev: user-space parallel port driver
[  319.149291] [drm] Initialized drm 1.1.0 20060810
[  319.203057] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  319.203064] pci 0000:00:02.0: setting latency timer to 64
[  319.203267] [drm] Initialized i915 1.6.0 20080730 on minor 0
[  319.206410] [drm:i915_setparam] *ERROR* unknown parameter 4
[  319.206438] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  319.350971] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  319.352113] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-1.ucode
[  319.936062] Registered led device: iwl-phy0:radio
[  319.936087] Registered led device: iwl-phy0:assoc
[  319.936145] Registered led device: iwl-phy0:RX
[  319.936165] Registered led device: iwl-phy0:TX
[  319.945490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  320.786632] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  324.734494] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  324.734500] ata1.00: BMDMA stat 0x25
[  324.734508] ata1.00: cmd c8/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  324.734509]          res 51/10:08:00:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  324.734514] ata1.00: status: { DRDY ERR }
[  324.734516] ata1.00: error: { IDNF }
[  324.764400] ata1.00: configured for UDMA/100
[  324.764421] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  324.764426] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  324.764433] Descriptor sense data with sense descriptors (in hex):
[  324.764436]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  324.764449]         09 50 f8 00 
[  324.764454] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  324.764461] end_request: I/O error, dev sda, sector 156301312
[  324.764468] Buffer I/O error on device sda, logical block 19537664
[  324.764490] ata1: EH complete
[  326.194718] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  326.194724] ata1.00: BMDMA stat 0x25
[  326.194732] ata1.00: cmd c8/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  326.194734]          res 51/10:08:00:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  326.194738] ata1.00: status: { DRDY ERR }
[  326.194741] ata1.00: error: { IDNF }
[  326.216415] ata1.00: configured for UDMA/100
[  326.216429] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  326.216435] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  326.216441] Descriptor sense data with sense descriptors (in hex):
[  326.216445]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  326.216457]         09 50 f8 00 
[  326.216463] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  326.216469] end_request: I/O error, dev sda, sector 156301312
[  326.216475] Buffer I/O error on device sda, logical block 19537664
[  326.216490] ata1: EH complete
[  326.216627] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  327.621728] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  327.621734] ata1.00: BMDMA stat 0x25
[  327.621742] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  327.621744]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  327.621748] ata1.00: status: { DRDY ERR }
[  327.621750] ata1.00: error: { IDNF }
[  327.644398] ata1.00: configured for UDMA/100
[  327.644411] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  327.644416] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  327.644422] Descriptor sense data with sense descriptors (in hex):
[  327.644426]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  327.644438]         09 50 f8 a0 
[  327.644444] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  327.644450] end_request: I/O error, dev sda, sector 156301472
[  327.644456] Buffer I/O error on device sda, logical block 19537684
[  327.644468] ata1: EH complete
[  327.644568] sd 0:0:0:0: [sda] Write Protect is off
[  327.644571] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  329.081928] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  329.081934] ata1.00: BMDMA stat 0x25
[  329.081941] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  329.081943]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  329.081947] ata1.00: status: { DRDY ERR }
[  329.081950] ata1.00: error: { IDNF }
[  329.104441] ata1.00: configured for UDMA/100
[  329.104455] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  329.104460] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  329.104466] Descriptor sense data with sense descriptors (in hex):
[  329.104470]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  329.104482]         09 50 f8 a0 
[  329.104488] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  329.104494] end_request: I/O error, dev sda, sector 156301472
[  329.104499] Buffer I/O error on device sda, logical block 19537684
[  329.104512] ata1: EH complete
[  329.134002] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  330.564251] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  330.564256] ata1.00: BMDMA stat 0x25
[  330.564264] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  330.564266]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  330.564270] ata1.00: status: { DRDY ERR }
[  330.564273] ata1.00: error: { IDNF }
[  330.588447] ata1.00: configured for UDMA/100
[  330.588460] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  330.588465] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  330.588472] Descriptor sense data with sense descriptors (in hex):
[  330.588475]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  330.588488]         09 50 f8 a8 
[  330.588493] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  330.588499] end_request: I/O error, dev sda, sector 156301480
[  330.588504] Buffer I/O error on device sda, logical block 19537685
[  330.588518] ata1: EH complete
[  332.013391] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  332.013397] ata1.00: BMDMA stat 0x25
[  332.013405] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  332.013407]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  332.013411] ata1.00: status: { DRDY ERR }
[  332.013414] ata1.00: error: { IDNF }
[  332.036424] ata1.00: configured for UDMA/100
[  332.036437] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  332.036442] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  332.036448] Descriptor sense data with sense descriptors (in hex):
[  332.036452]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  332.036464]         09 50 f8 a8 
[  332.036470] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  332.036476] end_request: I/O error, dev sda, sector 156301480
[  332.036481] Buffer I/O error on device sda, logical block 19537685
[  332.036495] ata1: EH complete
[  332.036614] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  333.462525] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  333.462530] ata1.00: BMDMA stat 0x25
[  333.462537] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  333.462539]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  333.462543] ata1.00: status: { DRDY ERR }
[  333.462545] ata1.00: error: { IDNF }
[  333.484482] ata1.00: configured for UDMA/100
[  333.484501] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  333.484510] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  333.484522] Descriptor sense data with sense descriptors (in hex):
[  333.484528]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  333.484554]         09 50 f8 a8 
[  333.484564] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  333.484576] end_request: I/O error, dev sda, sector 156301480
[  333.484586] Buffer I/O error on device sda, logical block 19537685
[  333.484612] ata1: EH complete
[  333.484765] sd 0:0:0:0: [sda] Write Protect is off
[  333.484782] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  334.955915] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  334.955921] ata1.00: BMDMA stat 0x25
[  334.955929] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  334.955931]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  334.955935] ata1.00: status: { DRDY ERR }
[  334.955938] ata1.00: error: { IDNF }
[  334.980430] ata1.00: configured for UDMA/100
[  334.980445] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  334.980450] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  334.980457] Descriptor sense data with sense descriptors (in hex):
[  334.980460]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  334.980473]         09 50 f8 a8 
[  334.980478] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  334.980484] end_request: I/O error, dev sda, sector 156301480
[  334.980490] Buffer I/O error on device sda, logical block 19537685
[  334.980507] ata1: EH complete
[  336.405063] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  336.405068] ata1.00: BMDMA stat 0x25
[  336.405076] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  336.405078]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  336.405082] ata1.00: status: { DRDY ERR }
[  336.405084] ata1.00: error: { IDNF }
[  336.428535] ata1.00: configured for UDMA/100
[  336.428547] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  336.428552] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  336.428559] Descriptor sense data with sense descriptors (in hex):
[  336.428562]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  336.428575]         09 50 f8 a8 
[  336.428580] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  336.428587] end_request: I/O error, dev sda, sector 156301480
[  336.428592] Buffer I/O error on device sda, logical block 19537685
[  336.428604] ata1: EH complete
[  336.428719] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  337.887381] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  337.887387] ata1.00: BMDMA stat 0x25
[  337.887395] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  337.887397]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  337.887401] ata1.00: status: { DRDY ERR }
[  337.887404] ata1.00: error: { IDNF }
[  337.908415] ata1.00: configured for UDMA/100
[  337.908427] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  337.908433] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  337.908439] Descriptor sense data with sense descriptors (in hex):
[  337.908442]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  337.908455]         09 50 f8 a8 
[  337.908460] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  337.908467] end_request: I/O error, dev sda, sector 156301480
[  337.908472] Buffer I/O error on device sda, logical block 19537685
[  337.908486] ata1: EH complete
[  339.347557] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  339.347564] ata1.00: BMDMA stat 0x25
[  339.347571] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  339.347573]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  339.347577] ata1.00: status: { DRDY ERR }
[  339.347580] ata1.00: error: { IDNF }
[  339.368414] ata1.00: configured for UDMA/100
[  339.368428] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  339.368433] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  339.368440] Descriptor sense data with sense descriptors (in hex):
[  339.368443]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  339.368456]         09 50 f8 a8 
[  339.368461] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  339.368467] end_request: I/O error, dev sda, sector 156301480
[  339.368472] Buffer I/O error on device sda, logical block 19537685
[  339.368488] ata1: EH complete
[  339.368611] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  340.818851] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  340.818857] ata1.00: BMDMA stat 0x25
[  340.818865] ata1.00: cmd c8/00:08:70:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  340.818867]          res 51/10:08:70:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  340.818871] ata1.00: status: { DRDY ERR }
[  340.818874] ata1.00: error: { IDNF }
[  340.840413] ata1.00: configured for UDMA/100
[  340.840430] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  340.840435] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  340.840442] Descriptor sense data with sense descriptors (in hex):
[  340.840445]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  340.840458]         09 50 f8 70 
[  340.840463] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  340.840469] end_request: I/O error, dev sda, sector 156301424
[  340.840475] Buffer I/O error on device sda, logical block 19537678
[  340.840495] ata1: EH complete
[  340.840627] sd 0:0:0:0: [sda] Write Protect is off
[  340.840631] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  342.301173] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  342.301178] ata1.00: BMDMA stat 0x25
[  342.301186] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  342.301188]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  342.301192] ata1.00: status: { DRDY ERR }
[  342.301195] ata1.00: error: { IDNF }
[  342.324414] ata1.00: configured for UDMA/100
[  342.324427] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  342.324432] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  342.324438] Descriptor sense data with sense descriptors (in hex):
[  342.324441]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  342.324454]         09 50 f8 a0 
[  342.324459] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  342.324466] end_request: I/O error, dev sda, sector 156301472
[  342.324471] Buffer I/O error on device sda, logical block 19537684
[  342.324484] ata1: EH complete
[  343.717128] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  343.717133] ata1.00: BMDMA stat 0x25
[  343.717141] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  343.717143]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  343.717147] ata1.00: status: { DRDY ERR }
[  343.717150] ata1.00: error: { IDNF }
[  343.740415] ata1.00: configured for UDMA/100
[  343.740428] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  343.740434] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  343.740440] Descriptor sense data with sense descriptors (in hex):
[  343.740443]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  343.740456]         09 50 f8 a8 
[  343.740461] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  343.740468] end_request: I/O error, dev sda, sector 156301480
[  343.740473] Buffer I/O error on device sda, logical block 19537685
[  343.740487] ata1: EH complete
[  343.740602] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  345.177322] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  345.177328] ata1.00: BMDMA stat 0x25
[  345.177335] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  345.177337]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  345.177341] ata1.00: status: { DRDY ERR }
[  345.177344] ata1.00: error: { IDNF }
[  345.200414] ata1.00: configured for UDMA/100
[  345.200427] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  345.200433] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  345.200439] Descriptor sense data with sense descriptors (in hex):
[  345.200442]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  345.200455]         09 50 f8 a8 
[  345.200460] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  345.200467] end_request: I/O error, dev sda, sector 156301480
[  345.200472] Buffer I/O error on device sda, logical block 19537685
[  345.200486] ata1: EH complete
[  345.229467] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  345.229764] sd 0:0:0:0: [sda] Write Protect is off
[  345.229768] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  345.230382] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  345.230920] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  345.231235] sd 0:0:0:0: [sda] Write Protect is off
[  345.231238] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  345.231805] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  348.153983] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  392.490031] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  392.490037] ata1.00: BMDMA stat 0x25
[  392.490045] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  392.490047]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  392.490051] ata1.00: status: { DRDY ERR }
[  392.490054] ata1.00: error: { IDNF }
[  392.516536] ata1.00: configured for UDMA/100
[  392.516551] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  392.516557] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  392.516563] Descriptor sense data with sense descriptors (in hex):
[  392.516567]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  392.516580]         09 50 f8 a8 
[  392.516585] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  392.516591] end_request: I/O error, dev sda, sector 156301480
[  392.516598] Buffer I/O error on device sda, logical block 19537685
[  392.516615] ata1: EH complete
[  393.972443] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  393.972453] ata1.00: BMDMA stat 0x25
[  393.972467] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  393.972470]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  393.972479] ata1.00: status: { DRDY ERR }
[  393.972484] ata1.00: error: { IDNF }
[  393.996549] ata1.00: configured for UDMA/100
[  393.996582] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  393.996591] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  393.996604] Descriptor sense data with sense descriptors (in hex):
[  393.996610]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  393.996635]         09 50 f8 a8 
[  393.996646] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  393.996658] end_request: I/O error, dev sda, sector 156301480
[  393.996670] Buffer I/O error on device sda, logical block 19537685
[  393.996711] ata1: EH complete
[  393.996776] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  393.996844] sd 0:0:0:0: [sda] Write Protect is off
[  393.996851] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  393.997016] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  394.024474] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  394.025054] sd 0:0:0:0: [sda] Write Protect is off
[  394.025061] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  395.532203] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  395.532213] ata1.00: BMDMA stat 0x25
[  395.532227] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  395.532230]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  395.532238] ata1.00: status: { DRDY ERR }
[  395.532243] ata1.00: error: { IDNF }
[  395.556510] ata1.00: configured for UDMA/100
[  395.556539] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  395.556549] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  395.556561] Descriptor sense data with sense descriptors (in hex):
[  395.556567]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  395.556593]         01 e4 61 b8 
[  395.556603] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  395.556615] end_request: I/O error, dev sda, sector 31744440
[  395.556626] Buffer I/O error on device sda, logical block 3968055
[  395.556664] ata1: EH complete
[  396.981342] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  396.981351] ata1.00: BMDMA stat 0x25
[  396.981365] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  396.981369]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  396.981377] ata1.00: status: { DRDY ERR }
[  396.981382] ata1.00: error: { IDNF }
[  397.004543] ata1.00: configured for UDMA/100
[  397.004574] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  397.004583] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  397.004596] Descriptor sense data with sense descriptors (in hex):
[  397.004602]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  397.004628]         01 e4 61 b8 
[  397.004638] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  397.004650] end_request: I/O error, dev sda, sector 31744440
[  397.004662] Buffer I/O error on device sda, logical block 3968055
[  397.004703] ata1: EH complete
[  397.004762] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  397.004858] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  397.004898] sd 0:0:0:0: [sda] Write Protect is off
[  397.004904] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  397.004969] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  423.000107] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  423.000131] ata2.00: cmd a0/01:00:00:00:fc/00:00:00:00:00/a0 tag 0 dma 98304 in
[  423.000135]          cdb 28 00 00 00 06 c7 00 00  30 00 00 00 00 00 00 00
[  423.000138]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  423.000146] ata2.00: status: { DRDY }
[  423.000196] ata2: soft resetting link
[  423.180595] ata2.00: configured for MWDMA2
[  423.189919] ata2: EH complete
[  487.613349] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  487.613359] ata1.00: BMDMA stat 0x25
[  487.613373] ata1.00: cmd c8/00:08:f7:30:f2/00:00:00:00:00/e0 tag 0 dma 4096 in
[  487.613377]          res 51/10:08:f7:30:f2/00:00:00:00:00/e0 Emask 0x81 (invalid argument)
[  487.613385] ata1.00: status: { DRDY ERR }
[  487.613390] ata1.00: error: { IDNF }
[  487.636608] ata1.00: configured for UDMA/100
[  487.636640] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  487.636650] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  487.636662] Descriptor sense data with sense descriptors (in hex):
[  487.636668]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  487.636694]         00 f2 30 f7 
[  487.636704] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  487.636716] end_request: I/O error, dev sda, sector 15872247
[  487.636729] Buffer I/O error on device sda1, logical block 15872184
[  487.636739] Buffer I/O error on device sda1, logical block 15872185
[  487.636747] Buffer I/O error on device sda1, logical block 15872186
[  487.636754] Buffer I/O error on device sda1, logical block 15872187
[  487.636762] Buffer I/O error on device sda1, logical block 15872188
[  487.636769] Buffer I/O error on device sda1, logical block 15872189
[  487.636777] Buffer I/O error on device sda1, logical block 15872190
[  487.636784] Buffer I/O error on device sda1, logical block 15872191
[  487.636820] ata1: EH complete
[  489.062487] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  489.062496] ata1.00: BMDMA stat 0x25
[  489.062511] ata1.00: cmd c8/00:08:f7:30:f2/00:00:00:00:00/e0 tag 0 dma 4096 in
[  489.062514]          res 51/10:08:f7:30:f2/00:00:00:00:00/e0 Emask 0x81 (invalid argument)
[  489.062522] ata1.00: status: { DRDY ERR }
[  489.062527] ata1.00: error: { IDNF }
[  489.084623] ata1.00: configured for UDMA/100
[  489.084656] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  489.084666] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  489.084678] Descriptor sense data with sense descriptors (in hex):
[  489.084684]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  489.084710]         00 f2 30 f7 
[  489.084720] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  489.084732] end_request: I/O error, dev sda, sector 15872247
[  489.084744] Buffer I/O error on device sda1, logical block 15872184
[  489.084754] Buffer I/O error on device sda1, logical block 15872185
[  489.084798] ata1: EH complete
[  489.094995] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  489.095103] sd 0:0:0:0: [sda] Write Protect is off
[  489.095110] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  489.095178] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  489.095252] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  489.095292] sd 0:0:0:0: [sda] Write Protect is off
[  489.095298] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  489.095362] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  490.633326] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  490.633336] ata1.00: BMDMA stat 0x25
[  490.633350] ata1.00: cmd c8/00:01:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  490.633354]          res 51/10:01:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  490.633362] ata1.00: status: { DRDY ERR }
[  490.633367] ata1.00: error: { IDNF }
[  490.656618] ata1.00: configured for UDMA/100
[  490.656650] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  490.656660] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  490.656672] Descriptor sense data with sense descriptors (in hex):
[  490.656678]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  490.656704]         01 e4 60 bf 
[  490.656714] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  490.656726] end_request: I/O error, dev sda, sector 31744191
[  490.656764] ata1: EH complete
[  492.093487] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  492.093497] ata1.00: BMDMA stat 0x25
[  492.093511] ata1.00: cmd c8/00:07:c0:60:e4/00:00:00:00:00/e1 tag 0 dma 3584 in
[  492.093515]          res 51/10:07:c0:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  492.093523] ata1.00: status: { DRDY ERR }
[  492.093528] ata1.00: error: { IDNF }
[  492.116574] ata1.00: configured for UDMA/100
[  492.116606] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  492.116615] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  492.116628] Descriptor sense data with sense descriptors (in hex):
[  492.116634]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  492.116659]         01 e4 60 c0 
[  492.116670] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  492.116682] end_request: I/O error, dev sda, sector 31744192
[  492.116730] ata1: EH complete
[  492.116902] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  494.980742] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  494.980752] ata1.00: BMDMA stat 0x25
[  494.980766] ata1.00: cmd c8/00:08:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  494.980770]          res 51/10:08:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  494.980778] ata1.00: status: { DRDY ERR }
[  494.980783] ata1.00: error: { IDNF }
[  495.004544] ata1.00: configured for UDMA/100
[  495.004577] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  495.004587] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  495.004599] Descriptor sense data with sense descriptors (in hex):
[  495.004605]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  495.004631]         01 e4 60 bf 
[  495.004641] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  495.004653] end_request: I/O error, dev sda, sector 31744191
[  495.004664] __ratelimit: 14 callbacks suppressed
[  495.004671] Buffer I/O error on device sda1, logical block 31744128
[  495.004681] Buffer I/O error on device sda1, logical block 31744129
[  495.004689] Buffer I/O error on device sda1, logical block 31744130
[  495.004696] Buffer I/O error on device sda1, logical block 31744131
[  495.004703] Buffer I/O error on device sda1, logical block 31744132
[  495.004711] Buffer I/O error on device sda1, logical block 31744133
[  495.004718] Buffer I/O error on device sda1, logical block 31744134
[  495.004725] Buffer I/O error on device sda1, logical block 31744135
[  495.004761] ata1: EH complete
[  495.005015] sd 0:0:0:0: [sda] Write Protect is off
[  495.005022] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  496.407748] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  496.407757] ata1.00: BMDMA stat 0x25
[  496.407772] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  496.407775]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  496.407793] ata1.00: status: { DRDY ERR }
[  496.407798] ata1.00: error: { IDNF }
[  496.428562] ata1.00: configured for UDMA/100
[  496.428595] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  496.428605] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  496.428617] Descriptor sense data with sense descriptors (in hex):
[  496.428623]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  496.428660]         01 e4 61 a7 
[  496.428670] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  496.428682] end_request: I/O error, dev sda, sector 31744423
[  496.428695] Buffer I/O error on device sda1, logical block 31744360
[  496.428705] Buffer I/O error on device sda1, logical block 31744361
[  496.428748] ata1: EH complete
[  497.856890] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  497.856900] ata1.00: BMDMA stat 0x25
[  497.856915] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  497.856918]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  497.856926] ata1.00: status: { DRDY ERR }
[  497.856931] ata1.00: error: { IDNF }
[  497.880597] ata1.00: configured for UDMA/100
[  497.880630] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  497.880640] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  497.880652] Descriptor sense data with sense descriptors (in hex):
[  497.880658]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  497.880684]         01 e4 61 a7 
[  497.880694] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  497.880706] end_request: I/O error, dev sda, sector 31744423
[  497.880757] ata1: EH complete
[  497.881064] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  499.372397] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  499.372407] ata1.00: BMDMA stat 0x25
[  499.372421] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  499.372424]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  499.372432] ata1.00: status: { DRDY ERR }
[  499.372438] ata1.00: error: { IDNF }
[  499.396598] ata1.00: configured for UDMA/100
[  499.396630] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  499.396639] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  499.396652] Descriptor sense data with sense descriptors (in hex):
[  499.396658]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  499.396684]         01 e4 61 b7 
[  499.396694] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  499.396706] end_request: I/O error, dev sda, sector 31744439
[  499.396748] ata1: EH complete
[  499.396913] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  500.810470] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  500.810480] ata1.00: BMDMA stat 0x25
[  500.810494] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  500.810498]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  500.810506] ata1.00: status: { DRDY ERR }
[  500.810511] ata1.00: error: { IDNF }
[  500.832606] ata1.00: configured for UDMA/100
[  500.832637] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  500.832647] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  500.832659] Descriptor sense data with sense descriptors (in hex):
[  500.832665]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  500.832691]         01 e4 61 b7 
[  500.832701] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  500.832713] end_request: I/O error, dev sda, sector 31744439
[  500.832723] __ratelimit: 15 callbacks suppressed
[  500.832731] Buffer I/O error on device sda1, logical block 31744376
[  500.832768] ata1: EH complete
[  500.832992] sd 0:0:0:0: [sda] Write Protect is off
[  500.832999] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  502.248548] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  502.248557] ata1.00: BMDMA stat 0x25
[  502.248572] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  502.248575]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  502.248583] ata1.00: status: { DRDY ERR }
[  502.248588] ata1.00: error: { IDNF }
[  502.272561] ata1.00: configured for UDMA/100
[  502.272592] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  502.272602] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  502.272614] Descriptor sense data with sense descriptors (in hex):
[  502.272620]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  502.272646]         01 e4 61 af 
[  502.272656] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  502.272668] end_request: I/O error, dev sda, sector 31744431
[  502.272680] Buffer I/O error on device sda1, logical block 31744368
[  502.272689] Buffer I/O error on device sda1, logical block 31744369
[  502.272697] Buffer I/O error on device sda1, logical block 31744370
[  502.272705] Buffer I/O error on device sda1, logical block 31744371
[  502.272712] Buffer I/O error on device sda1, logical block 31744372
[  502.272720] Buffer I/O error on device sda1, logical block 31744373
[  502.272727] Buffer I/O error on device sda1, logical block 31744374
[  502.272734] Buffer I/O error on device sda1, logical block 31744375
[  502.272767] ata1: EH complete
[  503.719823] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  503.719833] ata1.00: BMDMA stat 0x25
[  503.719847] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  503.719850]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  503.719858] ata1.00: status: { DRDY ERR }
[  503.719863] ata1.00: error: { IDNF }
[  503.744614] ata1.00: configured for UDMA/100
[  503.744646] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  503.744656] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  503.744668] Descriptor sense data with sense descriptors (in hex):
[  503.744674]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  503.744700]         01 e4 61 b7 
[  503.744710] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  503.744722] end_request: I/O error, dev sda, sector 31744439
[  503.744735] Buffer I/O error on device sda1, logical block 31744376
[  503.744773] ata1: EH complete
[  503.744965] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  505.169548] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  505.169558] ata1.00: BMDMA stat 0x25
[  505.169572] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  505.169575]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  505.169583] ata1.00: status: { DRDY ERR }
[  505.169589] ata1.00: error: { IDNF }
[  505.192611] ata1.00: configured for UDMA/100
[  505.192641] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  505.192651] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  505.192664] Descriptor sense data with sense descriptors (in hex):
[  505.192670]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  505.192695]         01 e4 61 b7 
[  505.192706] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  505.192718] end_request: I/O error, dev sda, sector 31744439
[  505.192762] ata1: EH complete
[  506.640220] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  506.640230] ata1.00: BMDMA stat 0x25
[  506.640244] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  506.640248]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  506.640256] ata1.00: status: { DRDY ERR }
[  506.640261] ata1.00: error: { IDNF }
[  506.664612] ata1.00: configured for UDMA/100
[  506.664644] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  506.664653] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  506.664666] Descriptor sense data with sense descriptors (in hex):
[  506.664672]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  506.664698]         01 e4 61 b7 
[  506.664708] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  506.664720] end_request: I/O error, dev sda, sector 31744439
[  506.664763] ata1: EH complete
[  506.664974] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  508.111486] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  508.111495] ata1.00: BMDMA stat 0x25
[  508.111510] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  508.111513]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  508.111521] ata1.00: status: { DRDY ERR }
[  508.111527] ata1.00: error: { IDNF }
[  508.132611] ata1.00: configured for UDMA/100
[  508.132643] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  508.132652] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  508.132665] Descriptor sense data with sense descriptors (in hex):
[  508.132671]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  508.132697]         01 e4 61 af 
[  508.132707] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  508.132719] end_request: I/O error, dev sda, sector 31744431
[  508.132729] __ratelimit: 2 callbacks suppressed
[  508.132736] Buffer I/O error on device sda1, logical block 31744368
[  508.132747] Buffer I/O error on device sda1, logical block 31744369
[  508.132754] Buffer I/O error on device sda1, logical block 31744370
[  508.132761] Buffer I/O error on device sda1, logical block 31744371
[  508.132769] Buffer I/O error on device sda1, logical block 31744372
[  508.132776] Buffer I/O error on device sda1, logical block 31744373
[  508.132783] Buffer I/O error on device sda1, logical block 31744374
[  508.132791] Buffer I/O error on device sda1, logical block 31744375
[  508.132826] ata1: EH complete
[  508.133082] sd 0:0:0:0: [sda] Write Protect is off
[  508.133089] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  509.615927] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  509.615937] ata1.00: BMDMA stat 0x25
[  509.615951] ata1.00: cmd c8/00:08:77:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  509.615954]          res 51/10:08:77:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  509.615962] ata1.00: status: { DRDY ERR }
[  509.615977] ata1.00: error: { IDNF }
[  509.632546] ata1.00: configured for UDMA/100
[  509.632583] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  509.632594] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  509.632606] Descriptor sense data with sense descriptors (in hex):
[  509.632613]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  509.632638]         01 e4 61 77 
[  509.632649] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  509.632661] end_request: I/O error, dev sda, sector 31744375
[  509.632675] Buffer I/O error on device sda1, logical block 31744312
[  509.632685] Buffer I/O error on device sda1, logical block 31744313
[  509.632734] ata1: EH complete
[  511.087201] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  511.087211] ata1.00: BMDMA stat 0x25
[  511.087225] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  511.087229]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  511.087237] ata1.00: status: { DRDY ERR }
[  511.087242] ata1.00: error: { IDNF }
[  511.108511] ata1.00: configured for UDMA/100
[  511.108541] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  511.108551] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  511.108563] Descriptor sense data with sense descriptors (in hex):
[  511.108569]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  511.108595]         01 e4 61 a7 
[  511.108605] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  511.108617] end_request: I/O error, dev sda, sector 31744423
[  511.108666] ata1: EH complete
[  511.108846] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  512.514212] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  512.514222] ata1.00: BMDMA stat 0x25
[  512.514236] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  512.514239]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  512.514247] ata1.00: status: { DRDY ERR }
[  512.514253] ata1.00: error: { IDNF }
[  512.536656] ata1.00: configured for UDMA/100
[  512.536685] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  512.536695] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  512.536708] Descriptor sense data with sense descriptors (in hex):
[  512.536714]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  512.536740]         01 e4 61 b7 
[  512.536750] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  512.536762] end_request: I/O error, dev sda, sector 31744439
[  512.536802] ata1: EH complete
[  514.073936] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  514.073945] ata1.00: BMDMA stat 0x25
[  514.073960] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  514.073963]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  514.073971] ata1.00: status: { DRDY ERR }
[  514.073976] ata1.00: error: { IDNF }
[  514.096513] ata1.00: configured for UDMA/100
[  514.096538] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  514.096547] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  514.096560] Descriptor sense data with sense descriptors (in hex):
[  514.096566]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  514.096591]         01 e4 61 b7 
[  514.096602] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  514.096614] end_request: I/O error, dev sda, sector 31744439
[  514.096623] __ratelimit: 15 callbacks suppressed
[  514.096631] Buffer I/O error on device sda1, logical block 31744376
[  514.096659] ata1: EH complete
[  514.096951] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  514.126945] sd 0:0:0:0: [sda] Write Protect is off
[  514.126955] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  514.127639] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  514.129788] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  514.130130] sd 0:0:0:0: [sda] Write Protect is off
[  514.130137] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  514.130806] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1056.679945] VFS: busy inodes on changed media or resized disk sr0
[ 1057.009922] VFS: busy inodes on changed media or resized disk sr0
[ 1088.000242] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1088.000264] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1088.000267]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1088.000270]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1088.000278] ata2.00: status: { DRDY }
[ 1088.000328] ata2: soft resetting link
[ 1088.180682] ata2.00: configured for MWDMA2
[ 1088.190082] ata2: EH complete
[ 1088.207180] VFS: busy inodes on changed media or resized disk sr0
[ 1110.948181] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 1111.082240] usb 1-2: configuration #1 chosen from 1 choice
[ 1112.795613] Initializing USB Mass Storage driver...
[ 1112.795891] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1112.796120] usbcore: registered new interface driver usb-storage
[ 1112.796132] USB Mass Storage support registered.
[ 1112.796366] usb-storage: device found at 3
[ 1112.796374] usb-storage: waiting for device to settle before scanning
[ 1117.796558] usb-storage: device scan complete
[ 1117.797187] scsi 2:0:0:0: Direct-Access     WD       2500BEV External 1.05 PQ: 0 ANSI: 4
[ 1117.812311] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[ 1117.814010] sd 2:0:0:0: [sdb] Write Protect is off
[ 1117.814017] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 1117.814023] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1117.814743] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[ 1117.818511] sd 2:0:0:0: [sdb] Write Protect is off
[ 1117.818519] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 1117.818525] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1117.818535]  sdb: sdb1
[ 1117.859346] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 1117.859501] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1178.360605] usb 1-2: USB disconnect, address 3
[ 1777.835156] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 2156.082042] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2156.082051] ata1.00: BMDMA stat 0x25
[ 2156.082065] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[ 2156.082069]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[ 2156.082077] ata1.00: status: { DRDY ERR }
[ 2156.082082] ata1.00: error: { IDNF }
[ 2156.104607] ata1.00: configured for UDMA/100
[ 2156.104636] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2156.104646] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2156.104658] Descriptor sense data with sense descriptors (in hex):
[ 2156.104664]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2156.104690]         09 50 f8 a8 
[ 2156.104700] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2156.104712] end_request: I/O error, dev sda, sector 156301480
[ 2156.104725] Buffer I/O error on device sda, logical block 19537685
[ 2156.104762] ata1: EH complete
[ 2157.509092] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2157.509102] ata1.00: BMDMA stat 0x25
[ 2157.509116] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[ 2157.509119]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[ 2157.509127] ata1.00: status: { DRDY ERR }
[ 2157.509132] ata1.00: error: { IDNF }
[ 2157.532610] ata1.00: configured for UDMA/100
[ 2157.532641] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2157.532651] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2157.532663] Descriptor sense data with sense descriptors (in hex):
[ 2157.532669]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2157.532695]         09 50 f8 a8 
[ 2157.532705] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2157.532717] end_request: I/O error, dev sda, sector 156301480
[ 2157.532729] Buffer I/O error on device sda, logical block 19537685
[ 2157.532767] ata1: EH complete
[ 2157.533135] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2157.561160] sd 0:0:0:0: [sda] Write Protect is off
[ 2157.561167] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2159.024576] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2159.024585] ata1.00: BMDMA stat 0x25
[ 2159.024600] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[ 2159.024603]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2159.024611] ata1.00: status: { DRDY ERR }
[ 2159.024616] ata1.00: error: { IDNF }
[ 2159.048568] ata1.00: configured for UDMA/100
[ 2159.048597] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2159.048606] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2159.048619] Descriptor sense data with sense descriptors (in hex):
[ 2159.048625]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2159.048650]         01 e4 61 b8 
[ 2159.048661] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2159.048673] end_request: I/O error, dev sda, sector 31744440
[ 2159.048684] Buffer I/O error on device sda, logical block 3968055
[ 2159.048720] ata1: EH complete
[ 2159.048873] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2160.506927] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2160.506937] ata1.00: BMDMA stat 0x25
[ 2160.506951] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[ 2160.506954]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2160.506962] ata1.00: status: { DRDY ERR }
[ 2160.506968] ata1.00: error: { IDNF }
[ 2160.528530] ata1.00: configured for UDMA/100
[ 2160.528558] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2160.528568] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2160.528580] Descriptor sense data with sense descriptors (in hex):
[ 2160.528586]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2160.528612]         01 e4 61 b8 
[ 2160.528622] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2160.528634] end_request: I/O error, dev sda, sector 31744440
[ 2160.528646] Buffer I/O error on device sda, logical block 3968055
[ 2160.528682] ata1: EH complete
[ 2160.529806] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2160.529851] sd 0:0:0:0: [sda] Write Protect is off
[ 2160.529858] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2160.529924] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2160.529996] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2160.530035] sd 0:0:0:0: [sda] Write Protect is off
[ 2160.530041] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2160.530105] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2326.483296] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2326.483306] ata1.00: BMDMA stat 0x25
[ 2326.483320] ata1.00: cmd c8/00:08:f7:30:f2/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2326.483323]          res 51/10:08:f7:30:f2/00:00:00:00:00/e0 Emask 0x81 (invalid argument)
[ 2326.483331] ata1.00: status: { DRDY ERR }
[ 2326.483336] ata1.00: error: { IDNF }
[ 2326.504613] ata1.00: configured for UDMA/100
[ 2326.504647] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2326.504657] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2326.504669] Descriptor sense data with sense descriptors (in hex):
[ 2326.504675]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2326.504701]         00 f2 30 f7 
[ 2326.504711] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2326.504723] end_request: I/O error, dev sda, sector 15872247
[ 2326.504736] Buffer I/O error on device sda1, logical block 15872184
[ 2326.504746] Buffer I/O error on device sda1, logical block 15872185
[ 2326.504753] Buffer I/O error on device sda1, logical block 15872186
[ 2326.504761] Buffer I/O error on device sda1, logical block 15872187
[ 2326.504769] Buffer I/O error on device sda1, logical block 15872188
[ 2326.504776] Buffer I/O error on device sda1, logical block 15872189
[ 2326.504784] Buffer I/O error on device sda1, logical block 15872190
[ 2326.504791] Buffer I/O error on device sda1, logical block 15872191
[ 2326.504827] ata1: EH complete
[ 2327.998778] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2327.998787] ata1.00: BMDMA stat 0x25
[ 2327.998801] ata1.00: cmd c8/00:08:f7:30:f2/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2327.998804]          res 51/10:08:f7:30:f2/00:00:00:00:00/e0 Emask 0x81 (invalid argument)
[ 2327.998812] ata1.00: status: { DRDY ERR }
[ 2327.998818] ata1.00: error: { IDNF }
[ 2328.020561] ata1.00: configured for UDMA/100
[ 2328.020590] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2328.020599] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2328.020612] Descriptor sense data with sense descriptors (in hex):
[ 2328.020618]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2328.020643]         00 f2 30 f7 
[ 2328.020654] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2328.020666] end_request: I/O error, dev sda, sector 15872247
[ 2328.020677] Buffer I/O error on device sda1, logical block 15872184
[ 2328.020687] Buffer I/O error on device sda1, logical block 15872185
[ 2328.020728] ata1: EH complete
[ 2328.022753] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2328.022816] sd 0:0:0:0: [sda] Write Protect is off
[ 2328.022823] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2328.022892] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2328.022966] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2328.023006] sd 0:0:0:0: [sda] Write Protect is off
[ 2328.023012] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2328.023077] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2329.525390] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2329.525399] ata1.00: BMDMA stat 0x25
[ 2329.525413] ata1.00: cmd c8/00:01:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2329.525417]          res 51/10:01:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2329.525425] ata1.00: status: { DRDY ERR }
[ 2329.525430] ata1.00: error: { IDNF }
[ 2329.548607] ata1.00: configured for UDMA/100
[ 2329.548638] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2329.548647] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2329.548660] Descriptor sense data with sense descriptors (in hex):
[ 2329.548666]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2329.548691]         01 e4 60 bf 
[ 2329.548702] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2329.548714] end_request: I/O error, dev sda, sector 31744191
[ 2329.548752] ata1: EH complete
[ 2330.985529] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2330.985539] ata1.00: BMDMA stat 0x25
[ 2330.985553] ata1.00: cmd c8/00:07:c0:60:e4/00:00:00:00:00/e1 tag 0 dma 3584 in
[ 2330.985557]          res 51/10:07:c0:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2330.985564] ata1.00: status: { DRDY ERR }
[ 2330.985570] ata1.00: error: { IDNF }
[ 2331.008622] ata1.00: configured for UDMA/100
[ 2331.008655] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2331.008664] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2331.008677] Descriptor sense data with sense descriptors (in hex):
[ 2331.008683]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2331.008709]         01 e4 60 c0 
[ 2331.008719] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2331.008731] end_request: I/O error, dev sda, sector 31744192
[ 2331.008785] ata1: EH complete
[ 2331.008934] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2332.489985] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2332.489995] ata1.00: BMDMA stat 0x25
[ 2332.490009] ata1.00: cmd c8/00:03:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 1536 in
[ 2332.490013]          res 51/10:03:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2332.490021] ata1.00: status: { DRDY ERR }
[ 2332.490026] ata1.00: error: { IDNF }
[ 2332.512605] ata1.00: configured for UDMA/100
[ 2332.512638] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2332.512647] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2332.512659] Descriptor sense data with sense descriptors (in hex):
[ 2332.512665]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2332.512691]         01 e4 60 bf 
[ 2332.512701] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2332.512713] end_request: I/O error, dev sda, sector 31744191
[ 2332.512724] __ratelimit: 14 callbacks suppressed
[ 2332.512732] Buffer I/O error on device sda1, logical block 31744128
[ 2332.512742] Buffer I/O error on device sda1, logical block 31744129
[ 2332.512750] Buffer I/O error on device sda1, logical block 31744130
[ 2332.512779] ata1: EH complete
[ 2332.512946] sd 0:0:0:0: [sda] Write Protect is off
[ 2332.512952] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2334.149359] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2334.149368] ata1.00: BMDMA stat 0x25
[ 2334.149383] ata1.00: cmd c8/00:05:c2:60:e4/00:00:00:00:00/e1 tag 0 dma 2560 in
[ 2334.149386]          res 51/10:05:c2:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2334.149394] ata1.00: status: { DRDY ERR }
[ 2334.149400] ata1.00: error: { IDNF }
[ 2334.172608] ata1.00: configured for UDMA/100
[ 2334.172643] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2334.172652] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2334.172665] Descriptor sense data with sense descriptors (in hex):
[ 2334.172671]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2334.172696]         01 e4 60 c2 
[ 2334.172707] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2334.172719] end_request: I/O error, dev sda, sector 31744194
[ 2334.172731] Buffer I/O error on device sda1, logical block 31744131
[ 2334.172742] Buffer I/O error on device sda1, logical block 31744132
[ 2334.172750] Buffer I/O error on device sda1, logical block 31744133
[ 2334.172757] Buffer I/O error on device sda1, logical block 31744134
[ 2334.172765] Buffer I/O error on device sda1, logical block 31744135
[ 2334.172818] ata1: EH complete
[ 2334.172930] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2335.598503] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2335.598513] ata1.00: BMDMA stat 0x25
[ 2335.598527] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[ 2335.598531]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2335.598539] ata1.00: status: { DRDY ERR }
[ 2335.598544] ata1.00: error: { IDNF }
[ 2335.620564] ata1.00: configured for UDMA/100
[ 2335.620596] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2335.620606] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2335.620618] Descriptor sense data with sense descriptors (in hex):
[ 2335.620624]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2335.620650]         01 e4 61 a7 
[ 2335.620660] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2335.620672] end_request: I/O error, dev sda, sector 31744423
[ 2335.620684] Buffer I/O error on device sda1, logical block 31744360
[ 2335.620693] Buffer I/O error on device sda1, logical block 31744361
[ 2335.620737] ata1: EH complete
[ 2337.102956] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2337.102966] ata1.00: BMDMA stat 0x25
[ 2337.102980] ata1.00: cmd c8/00:01:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2337.102983]          res 51/10:01:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2337.102991] ata1.00: status: { DRDY ERR }
[ 2337.102997] ata1.00: error: { IDNF }
[ 2337.124586] ata1.00: configured for UDMA/100
[ 2337.124615] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2337.124625] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2337.124637] Descriptor sense data with sense descriptors (in hex):
[ 2337.124643]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2337.124669]         01 e4 61 a7 
[ 2337.124679] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2337.124691] end_request: I/O error, dev sda, sector 31744423
[ 2337.124726] ata1: EH complete
[ 2337.124847] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2338.762277] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2338.762287] ata1.00: BMDMA stat 0x25
[ 2338.762300] ata1.00: cmd c8/00:07:a8:61:e4/00:00:00:00:00/e1 tag 0 dma 3584 in
[ 2338.762304]          res 51/10:07:a8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2338.762312] ata1.00: status: { DRDY ERR }
[ 2338.762317] ata1.00: error: { IDNF }
[ 2338.784568] ata1.00: configured for UDMA/100
[ 2338.784599] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2338.784608] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2338.784621] Descriptor sense data with sense descriptors (in hex):
[ 2338.784627]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2338.784652]         01 e4 61 a8 
[ 2338.784663] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2338.784675] end_request: I/O error, dev sda, sector 31744424
[ 2338.784684] __ratelimit: 7 callbacks suppressed
[ 2338.784691] Buffer I/O error on device sda1, logical block 31744361
[ 2338.784701] Buffer I/O error on device sda1, logical block 31744362
[ 2338.784709] Buffer I/O error on device sda1, logical block 31744363
[ 2338.784716] Buffer I/O error on device sda1, logical block 31744364
[ 2338.784724] Buffer I/O error on device sda1, logical block 31744365
[ 2338.784731] Buffer I/O error on device sda1, logical block 31744366
[ 2338.784739] Buffer I/O error on device sda1, logical block 31744367
[ 2338.784776] ata1: EH complete
[ 2338.784833] sd 0:0:0:0: [sda] Write Protect is off
[ 2338.784839] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2338.814984] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2340.266728] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2340.266738] ata1.00: BMDMA stat 0x25
[ 2340.266752] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2340.266755]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2340.266763] ata1.00: status: { DRDY ERR }
[ 2340.266769] ata1.00: error: { IDNF }
[ 2340.288608] ata1.00: configured for UDMA/100
[ 2340.288640] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2340.288650] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2340.288663] Descriptor sense data with sense descriptors (in hex):
[ 2340.288669]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2340.288694]         01 e4 61 b7 
[ 2340.288705] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2340.288717] end_request: I/O error, dev sda, sector 31744439
[ 2340.288730] Buffer I/O error on device sda1, logical block 31744376
[ 2340.288772] ata1: EH complete
[ 2340.288911] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2341.715870] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2341.715880] ata1.00: BMDMA stat 0x25
[ 2341.715894] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2341.715897]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2341.715905] ata1.00: status: { DRDY ERR }
[ 2341.715910] ata1.00: error: { IDNF }
[ 2341.740552] ata1.00: configured for UDMA/100
[ 2341.740579] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2341.740589] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2341.740602] Descriptor sense data with sense descriptors (in hex):
[ 2341.740608]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2341.740633]         01 e4 61 b7 
[ 2341.740643] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2341.740656] end_request: I/O error, dev sda, sector 31744439
[ 2341.740667] Buffer I/O error on device sda1, logical block 31744376
[ 2341.740704] ata1: EH complete
[ 2341.740759] sd 0:0:0:0: [sda] Write Protect is off
[ 2341.740766] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2343.165010] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2343.165020] ata1.00: BMDMA stat 0x25
[ 2343.165034] ata1.00: cmd c8/00:04:af:61:e4/00:00:00:00:00/e1 tag 0 dma 2048 in
[ 2343.165037]          res 51/10:04:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2343.165045] ata1.00: status: { DRDY ERR }
[ 2343.165050] ata1.00: error: { IDNF }
[ 2343.188611] ata1.00: configured for UDMA/100
[ 2343.188643] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2343.188653] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2343.188665] Descriptor sense data with sense descriptors (in hex):
[ 2343.188671]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2343.188697]         01 e4 61 af 
[ 2343.188707] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2343.188719] end_request: I/O error, dev sda, sector 31744431
[ 2343.188731] Buffer I/O error on device sda1, logical block 31744368
[ 2343.188766] ata1: EH complete
[ 2343.188887] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2344.680521] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2344.680530] ata1.00: BMDMA stat 0x25
[ 2344.680544] ata1.00: cmd c8/00:04:b3:61:e4/00:00:00:00:00/e1 tag 0 dma 2048 in
[ 2344.680548]          res 51/10:04:b3:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2344.680556] ata1.00: status: { DRDY ERR }
[ 2344.680561] ata1.00: error: { IDNF }
[ 2344.704611] ata1.00: configured for UDMA/100
[ 2344.704645] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2344.704654] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2344.704667] Descriptor sense data with sense descriptors (in hex):
[ 2344.704673]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2344.704698]         01 e4 61 b3 
[ 2344.704709] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2344.704721] end_request: I/O error, dev sda, sector 31744435
[ 2344.704730] __ratelimit: 3 callbacks suppressed
[ 2344.704738] Buffer I/O error on device sda1, logical block 31744372
[ 2344.704749] Buffer I/O error on device sda1, logical block 31744373
[ 2344.704756] Buffer I/O error on device sda1, logical block 31744374
[ 2344.704764] Buffer I/O error on device sda1, logical block 31744375
[ 2344.704803] ata1: EH complete
[ 2344.704983] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2346.151758] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2346.151767] ata1.00: BMDMA stat 0x25
[ 2346.151781] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2346.151784]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2346.151792] ata1.00: status: { DRDY ERR }
[ 2346.151797] ata1.00: error: { IDNF }
[ 2346.172557] ata1.00: configured for UDMA/100
[ 2346.172588] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2346.172597] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2346.172610] Descriptor sense data with sense descriptors (in hex):
[ 2346.172616]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2346.172642]         01 e4 61 b7 
[ 2346.172652] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2346.172664] end_request: I/O error, dev sda, sector 31744439
[ 2346.172676] Buffer I/O error on device sda1, logical block 31744376
[ 2346.172718] ata1: EH complete
[ 2346.172782] sd 0:0:0:0: [sda] Write Protect is off
[ 2346.172788] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2347.623054] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2347.623063] ata1.00: BMDMA stat 0x25
[ 2347.623078] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2347.623081]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2347.623089] ata1.00: status: { DRDY ERR }
[ 2347.623094] ata1.00: error: { IDNF }
[ 2347.644554] ata1.00: configured for UDMA/100
[ 2347.644587] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2347.644596] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2347.644609] Descriptor sense data with sense descriptors (in hex):
[ 2347.644615]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2347.644641]         01 e4 61 b7 
[ 2347.644651] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2347.644663] end_request: I/O error, dev sda, sector 31744439
[ 2347.644675] Buffer I/O error on device sda1, logical block 31744376
[ 2347.644716] ata1: EH complete
[ 2349.094318] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2349.094328] ata1.00: BMDMA stat 0x25
[ 2349.094342] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2349.094345]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2349.094353] ata1.00: status: { DRDY ERR }
[ 2349.094358] ata1.00: error: { IDNF }
[ 2349.116585] ata1.00: configured for UDMA/100
[ 2349.116617] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2349.116627] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2349.116639] Descriptor sense data with sense descriptors (in hex):
[ 2349.116645]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2349.116671]         01 e4 61 b7 
[ 2349.116681] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2349.116693] end_request: I/O error, dev sda, sector 31744439
[ 2349.116705] Buffer I/O error on device sda1, logical block 31744376
[ 2349.116746] ata1: EH complete
[ 2349.116806] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2350.576648] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2350.576658] ata1.00: BMDMA stat 0x25
[ 2350.576672] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[ 2350.576675]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2350.576683] ata1.00: status: { DRDY ERR }
[ 2350.576688] ata1.00: error: { IDNF }
[ 2350.600611] ata1.00: configured for UDMA/100
[ 2350.600645] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2350.600655] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2350.600667] Descriptor sense data with sense descriptors (in hex):
[ 2350.600673]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2350.600699]         01 e4 61 af 
[ 2350.600709] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2350.600721] end_request: I/O error, dev sda, sector 31744431
[ 2350.600734] Buffer I/O error on device sda1, logical block 31744368
[ 2350.600744] Buffer I/O error on device sda1, logical block 31744369
[ 2350.600752] Buffer I/O error on device sda1, logical block 31744370
[ 2350.600760] Buffer I/O error on device sda1, logical block 31744371
[ 2350.600767] Buffer I/O error on device sda1, logical block 31744372
[ 2350.600775] Buffer I/O error on device sda1, logical block 31744373
[ 2350.600782] Buffer I/O error on device sda1, logical block 31744374
[ 2350.600790] Buffer I/O error on device sda1, logical block 31744375
[ 2350.600828] ata1: EH complete
[ 2350.600890] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2350.601034] sd 0:0:0:0: [sda] Write Protect is off
[ 2350.601041] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2352.058941] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2352.058950] ata1.00: BMDMA stat 0x25
[ 2352.058964] ata1.00: cmd c8/00:08:77:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[ 2352.058967]          res 51/10:08:77:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2352.058975] ata1.00: status: { DRDY ERR }
[ 2352.058980] ata1.00: error: { IDNF }
[ 2352.080632] ata1.00: configured for UDMA/100
[ 2352.080665] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2352.080675] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2352.080687] Descriptor sense data with sense descriptors (in hex):
[ 2352.080693]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2352.080719]         01 e4 61 77 
[ 2352.080729] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2352.080741] end_request: I/O error, dev sda, sector 31744375
[ 2352.080753] Buffer I/O error on device sda1, logical block 31744312
[ 2352.080764] Buffer I/O error on device sda1, logical block 31744313
[ 2352.080808] ata1: EH complete
[ 2352.081001] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2353.574492] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2353.574501] ata1.00: BMDMA stat 0x25
[ 2353.574515] ata1.00: cmd c8/00:04:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 2048 in
[ 2353.574519]          res 51/10:04:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2353.574527] ata1.00: status: { DRDY ERR }
[ 2353.574532] ata1.00: error: { IDNF }
[ 2353.596611] ata1.00: configured for UDMA/100
[ 2353.596643] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2353.596653] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2353.596665] Descriptor sense data with sense descriptors (in hex):
[ 2353.596671]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2353.596697]         01 e4 61 a7 
[ 2353.596707] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2353.596719] end_request: I/O error, dev sda, sector 31744423
[ 2353.596760] ata1: EH complete
[ 2355.056818] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2355.056827] ata1.00: BMDMA stat 0x25
[ 2355.056841] ata1.00: cmd c8/00:04:ab:61:e4/00:00:00:00:00/e1 tag 0 dma 2048 in
[ 2355.056845]          res 51/10:04:ab:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2355.056852] ata1.00: status: { DRDY ERR }
[ 2355.056858] ata1.00: error: { IDNF }
[ 2355.080605] ata1.00: configured for UDMA/100
[ 2355.080638] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2355.080648] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2355.080660] Descriptor sense data with sense descriptors (in hex):
[ 2355.080666]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2355.080692]         01 e4 61 ab 
[ 2355.080702] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2355.080715] end_request: I/O error, dev sda, sector 31744427
[ 2355.080764] ata1: EH complete
[ 2355.080826] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2356.494894] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2356.494904] ata1.00: BMDMA stat 0x25
[ 2356.494918] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2356.494922]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2356.494930] ata1.00: status: { DRDY ERR }
[ 2356.494935] ata1.00: error: { IDNF }
[ 2356.516608] ata1.00: configured for UDMA/100
[ 2356.516638] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2356.516648] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2356.516661] Descriptor sense data with sense descriptors (in hex):
[ 2356.516667]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2356.516692]         01 e4 61 b7 
[ 2356.516703] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2356.516715] end_request: I/O error, dev sda, sector 31744439
[ 2356.516725] __ratelimit: 14 callbacks suppressed
[ 2356.516732] Buffer I/O error on device sda1, logical block 31744376
[ 2356.516775] ata1: EH complete
[ 2356.516838] sd 0:0:0:0: [sda] Write Protect is off
[ 2356.516844] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2357.932974] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2357.932983] ata1.00: BMDMA stat 0x25
[ 2357.932997] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[ 2357.933001]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[ 2357.933008] ata1.00: status: { DRDY ERR }
[ 2357.933014] ata1.00: error: { IDNF }
[ 2357.956611] ata1.00: configured for UDMA/100
[ 2357.956643] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2357.956652] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2357.956665] Descriptor sense data with sense descriptors (in hex):
[ 2357.956671]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2357.956696]         01 e4 61 b7 
[ 2357.956706] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[ 2357.956718] end_request: I/O error, dev sda, sector 31744439
[ 2357.956731] Buffer I/O error on device sda1, logical block 31744376
[ 2357.956773] ata1: EH complete
[ 2357.956881] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2357.957055] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2357.985829] sd 0:0:0:0: [sda] Write Protect is off
[ 2357.985836] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2357.986191] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA

```

PLease Help me out I have data on the hard disk and I don't have its backup


Thanks in advance

---

### Post by pranjalsaxena on 2009-08-26
don't know how I got two different outputs posting both of them as I have no idea what it is..
the one I posted earlier is the one that I am getting consistently

```

0: [sda] Add. Sense: Recorded entity not found
[  183.648556] end_request: I/O error, dev sda, sector 31744440
[  183.648561] Buffer I/O error on device sda2, logical block 0
[  183.648576] ata1: EH complete
[  183.678648] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  183.678672] sd 0:0:0:0: [sda] Write Protect is off
[  183.678675] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  183.678709] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  185.108286] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  185.108289] ata1.00: BMDMA stat 0x25
[  185.108295] ata1.00: cmd c8/00:01:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  185.108296]          res 51/10:01:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  185.108300] ata1.00: status: { DRDY ERR }
[  185.108303] ata1.00: error: { IDNF }
[  185.132507] ata1.00: configured for UDMA/100
[  185.132513] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  185.132517] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  185.132523] Descriptor sense data with sense descriptors (in hex):
[  185.132526]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  185.132539]         01 e4 60 bf 
[  185.132544] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  185.132549] end_request: I/O error, dev sda, sector 31744191
[  185.132553] Buffer I/O error on device sda1, logical block 31744128
[  185.132562] ata1: EH complete
[  186.579554] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  186.579557] ata1.00: BMDMA stat 0x25
[  186.579563] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  186.579565]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  186.579569] ata1.00: status: { DRDY ERR }
[  186.579572] ata1.00: error: { IDNF }
[  186.600477] ata1.00: configured for UDMA/100
[  186.600483] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  186.600487] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  186.600492] Descriptor sense data with sense descriptors (in hex):
[  186.600495]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  186.600508]         01 e4 61 b8 
[  186.600513] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  186.600519] end_request: I/O error, dev sda, sector 31744440
[  186.600522] Buffer I/O error on device sda2, logical block 0
[  186.600533] ata1: EH complete
[  186.600608] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  188.050816] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  188.050819] ata1.00: BMDMA stat 0x25
[  188.050826] ata1.00: cmd c8/00:07:c0:60:e4/00:00:00:00:00/e1 tag 0 dma 3584 in
[  188.050827]          res 51/10:07:c0:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  188.050831] ata1.00: status: { DRDY ERR }
[  188.050834] ata1.00: error: { IDNF }
[  188.072463] ata1.00: configured for UDMA/100
[  188.072470] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  188.072474] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  188.072480] Descriptor sense data with sense descriptors (in hex):
[  188.072483]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  188.072495]         01 e4 60 c0 
[  188.072500] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  188.072506] end_request: I/O error, dev sda, sector 31744192
[  188.072510] Buffer I/O error on device sda1, logical block 31744129
[  188.072514] Buffer I/O error on device sda1, logical block 31744130
[  188.072518] Buffer I/O error on device sda1, logical block 31744131
[  188.072521] Buffer I/O error on device sda1, logical block 31744132
[  188.072525] Buffer I/O error on device sda1, logical block 31744133
[  188.072528] Buffer I/O error on device sda1, logical block 31744134
[  188.072539] ata1: EH complete
[  188.072558] sd 0:0:0:0: [sda] Write Protect is off
[  188.072561] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  188.072594] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  188.072629] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  188.072648] sd 0:0:0:0: [sda] Write Protect is off
[  188.072651] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  188.072683] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  190.119441] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  190.119444] ata1.00: BMDMA stat 0x25
[  190.119450] ata1.00: cmd c8/00:08:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  190.119452]          res 51/10:08:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  190.119455] ata1.00: status: { DRDY ERR }
[  190.119458] ata1.00: error: { IDNF }
[  190.140517] ata1.00: configured for UDMA/100
[  190.140524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  190.140528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  190.140534] Descriptor sense data with sense descriptors (in hex):
[  190.140536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  190.140549]         01 e4 60 bf 
[  190.140554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  190.140560] end_request: I/O error, dev sda, sector 31744191
[  190.140563] __ratelimit: 1 callbacks suppressed
[  190.140566] Buffer I/O error on device sda1, logical block 31744128
[  190.140570] Buffer I/O error on device sda1, logical block 31744129
[  190.140574] Buffer I/O error on device sda1, logical block 31744130
[  190.140577] Buffer I/O error on device sda1, logical block 31744131
[  190.140581] Buffer I/O error on device sda1, logical block 31744132
[  190.140584] Buffer I/O error on device sda1, logical block 31744133
[  190.140588] Buffer I/O error on device sda1, logical block 31744134
[  190.140592] Buffer I/O error on device sda1, logical block 31744135
[  190.140601] ata1: EH complete
[  190.140634] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  190.140654] sd 0:0:0:0: [sda] Write Protect is off
[  190.140657] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  190.140689] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  191.535390] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  191.535393] ata1.00: BMDMA stat 0x25
[  191.535399] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  191.535401]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  191.535405] ata1.00: status: { DRDY ERR }
[  191.535407] ata1.00: error: { IDNF }
[  191.556513] ata1.00: configured for UDMA/100
[  191.556519] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  191.556524] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  191.556529] Descriptor sense data with sense descriptors (in hex):
[  191.556532]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  191.556545]         01 e4 61 a7 
[  191.556550] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  191.556555] end_request: I/O error, dev sda, sector 31744423
[  191.556559] Buffer I/O error on device sda1, logical block 31744360
[  191.556563] Buffer I/O error on device sda1, logical block 31744361
[  191.556576] ata1: EH complete
[  191.556609] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  191.556629] sd 0:0:0:0: [sda] Write Protect is off
[  191.556632] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  191.556664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  192.984528] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  192.984531] ata1.00: BMDMA stat 0x25
[  192.984537] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  192.984539]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  192.984543] ata1.00: status: { DRDY ERR }
[  192.984545] ata1.00: error: { IDNF }
[  193.008514] ata1.00: configured for UDMA/100
[  193.008521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  193.008525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  193.008530] Descriptor sense data with sense descriptors (in hex):
[  193.008533]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  193.008546]         01 e4 61 a7 
[  193.008551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  193.008557] end_request: I/O error, dev sda, sector 31744423
[  193.008571] ata1: EH complete
[  193.008603] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  193.008623] sd 0:0:0:0: [sda] Write Protect is off
[  193.008626] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  193.008658] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  194.466851] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  194.466854] ata1.00: BMDMA stat 0x25
[  194.466860] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  194.466862]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  194.466866] ata1.00: status: { DRDY ERR }
[  194.466868] ata1.00: error: { IDNF }
[  194.488515] ata1.00: configured for UDMA/100
[  194.488521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  194.488526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  194.488531] Descriptor sense data with sense descriptors (in hex):
[  194.488534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  194.488547]         01 e4 61 b7 
[  194.488552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  194.488557] end_request: I/O error, dev sda, sector 31744439
[  194.488568] ata1: EH complete
[  194.488600] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  194.488621] sd 0:0:0:0: [sda] Write Protect is off
[  194.488624] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  194.488656] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  195.960239] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  195.960242] ata1.00: BMDMA stat 0x25
[  195.960248] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  195.960250]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  195.960253] ata1.00: status: { DRDY ERR }
[  195.960256] ata1.00: error: { IDNF }
[  195.984517] ata1.00: configured for UDMA/100
[  195.984523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  195.984528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  195.984533] Descriptor sense data with sense descriptors (in hex):
[  195.984536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  195.984549]         01 e4 61 b7 
[  195.984554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  195.984559] end_request: I/O error, dev sda, sector 31744439
[  195.984563] __ratelimit: 15 callbacks suppressed
[  195.984566] Buffer I/O error on device sda1, logical block 31744376
[  195.984576] ata1: EH complete
[  195.984608] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  195.984628] sd 0:0:0:0: [sda] Write Protect is off
[  195.984631] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  195.984664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  197.442565] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  197.442568] ata1.00: BMDMA stat 0x25
[  197.442574] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  197.442575]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  197.442579] ata1.00: status: { DRDY ERR }
[  197.442582] ata1.00: error: { IDNF }
[  197.464517] ata1.00: configured for UDMA/100
[  197.464523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  197.464527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  197.464533] Descriptor sense data with sense descriptors (in hex):
[  197.464536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  197.464549]         01 e4 61 af 
[  197.464554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  197.464559] end_request: I/O error, dev sda, sector 31744431
[  197.464563] Buffer I/O error on device sda1, logical block 31744368
[  197.464567] Buffer I/O error on device sda1, logical block 31744369
[  197.464571] Buffer I/O error on device sda1, logical block 31744370
[  197.464574] Buffer I/O error on device sda1, logical block 31744371
[  197.464578] Buffer I/O error on device sda1, logical block 31744372
[  197.464582] Buffer I/O error on device sda1, logical block 31744373
[  197.464585] Buffer I/O error on device sda1, logical block 31744374
[  197.464589] Buffer I/O error on device sda1, logical block 31744375
[  197.464598] ata1: EH complete
[  197.464631] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  197.464651] sd 0:0:0:0: [sda] Write Protect is off
[  197.464654] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  197.464686] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  198.913828] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  198.913831] ata1.00: BMDMA stat 0x25
[  198.913837] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  198.913839]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  198.913842] ata1.00: status: { DRDY ERR }
[  198.913845] ata1.00: error: { IDNF }
[  198.936516] ata1.00: configured for UDMA/100
[  198.936522] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  198.936526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  198.936532] Descriptor sense data with sense descriptors (in hex):
[  198.936534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  198.936547]         01 e4 61 b7 
[  198.936552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  198.936558] end_request: I/O error, dev sda, sector 31744439
[  198.936562] Buffer I/O error on device sda1, logical block 31744376
[  198.936571] ata1: EH complete
[  198.936604] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  198.936624] sd 0:0:0:0: [sda] Write Protect is off
[  198.936627] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  198.936660] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  200.385091] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  200.385095] ata1.00: BMDMA stat 0x25
[  200.385101] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  200.385102]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  200.385106] ata1.00: status: { DRDY ERR }
[  200.385109] ata1.00: error: { IDNF }
[  200.408518] ata1.00: configured for UDMA/100
[  200.408524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  200.408529] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  200.408534] Descriptor sense data with sense descriptors (in hex):
[  200.408537]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  200.408550]         01 e4 61 b7 
[  200.408555] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  200.408560] end_request: I/O error, dev sda, sector 31744439
[  200.408571] ata1: EH complete
[  200.408603] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  200.408623] sd 0:0:0:0: [sda] Write Protect is off
[  200.408626] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  200.408658] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  201.867417] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  201.867420] ata1.00: BMDMA stat 0x25
[  201.867426] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  201.867427]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  201.867431] ata1.00: status: { DRDY ERR }
[  201.867434] ata1.00: error: { IDNF }
[  201.888519] ata1.00: configured for UDMA/100
[  201.888525] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  201.888529] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  201.888534] Descriptor sense data with sense descriptors (in hex):
[  201.888537]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  201.888550]         01 e4 61 b7 
[  201.888555] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  201.888561] end_request: I/O error, dev sda, sector 31744439
[  201.888571] ata1: EH complete
[  201.888604] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  201.888624] sd 0:0:0:0: [sda] Write Protect is off
[  201.888627] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  201.888659] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  203.327617] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  203.327620] ata1.00: BMDMA stat 0x25
[  203.327626] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  203.327628]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  203.327632] ata1.00: status: { DRDY ERR }
[  203.327634] ata1.00: error: { IDNF }
[  203.348542] ata1.00: configured for UDMA/100
[  203.348548] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  203.348553] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  203.348558] Descriptor sense data with sense descriptors (in hex):
[  203.348561]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  203.348574]         01 e4 61 af 
[  203.348579] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  203.348584] end_request: I/O error, dev sda, sector 31744431
[  203.348588] __ratelimit: 2 callbacks suppressed
[  203.348591] Buffer I/O error on device sda1, logical block 31744368
[  203.348595] Buffer I/O error on device sda1, logical block 31744369
[  203.348598] Buffer I/O error on device sda1, logical block 31744370
[  203.348602] Buffer I/O error on device sda1, logical block 31744371
[  203.348606] Buffer I/O error on device sda1, logical block 31744372
[  203.348609] Buffer I/O error on device sda1, logical block 31744373
[  203.348613] Buffer I/O error on device sda1, logical block 31744374
[  203.348616] Buffer I/O error on device sda1, logical block 31744375
[  203.348626] ata1: EH complete
[  203.348659] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  203.348678] sd 0:0:0:0: [sda] Write Protect is off
[  203.348682] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  203.348714] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  204.765694] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  204.765697] ata1.00: BMDMA stat 0x25
[  204.765703] ata1.00: cmd c8/00:08:77:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  204.765705]          res 51/10:08:77:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  204.765709] ata1.00: status: { DRDY ERR }
[  204.765711] ata1.00: error: { IDNF }
[  204.788540] ata1.00: configured for UDMA/100
[  204.788546] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  204.788551] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  204.788556] Descriptor sense data with sense descriptors (in hex):
[  204.788559]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  204.788572]         01 e4 61 77 
[  204.788577] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  204.788582] end_request: I/O error, dev sda, sector 31744375
[  204.788586] Buffer I/O error on device sda1, logical block 31744312
[  204.788590] Buffer I/O error on device sda1, logical block 31744313
[  204.788603] ata1: EH complete
[  204.788636] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  204.788655] sd 0:0:0:0: [sda] Write Protect is off
[  204.788659] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  204.788691] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  206.236956] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  206.236959] ata1.00: BMDMA stat 0x25
[  206.236965] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  206.236966]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  206.236970] ata1.00: status: { DRDY ERR }
[  206.236973] ata1.00: error: { IDNF }
[  206.260515] ata1.00: configured for UDMA/100
[  206.260522] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  206.260526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  206.260532] Descriptor sense data with sense descriptors (in hex):
[  206.260534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  206.260547]         01 e4 61 a7 
[  206.260552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  206.260558] end_request: I/O error, dev sda, sector 31744423
[  206.260572] ata1: EH complete
[  206.260604] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  206.260625] sd 0:0:0:0: [sda] Write Protect is off
[  206.260628] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  206.260660] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  207.697159] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  207.697162] ata1.00: BMDMA stat 0x25
[  207.697168] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  207.697170]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  207.697174] ata1.00: status: { DRDY ERR }
[  207.697176] ata1.00: error: { IDNF }
[  207.720519] ata1.00: configured for UDMA/100
[  207.720525] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  207.720529] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  207.720535] Descriptor sense data with sense descriptors (in hex):
[  207.720537]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  207.720550]         01 e4 61 b7 
[  207.720555] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  207.720561] end_request: I/O error, dev sda, sector 31744439
[  207.720571] ata1: EH complete
[  207.720603] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  207.720623] sd 0:0:0:0: [sda] Write Protect is off
[  207.720627] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  207.720659] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  209.190544] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  209.190547] ata1.00: BMDMA stat 0x25
[  209.190553] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  209.190555]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  209.190559] ata1.00: status: { DRDY ERR }
[  209.190561] ata1.00: error: { IDNF }
[  209.212518] ata1.00: configured for UDMA/100
[  209.212524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  209.212528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  209.212534] Descriptor sense data with sense descriptors (in hex):
[  209.212536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  209.212549]         01 e4 61 b7 
[  209.212554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  209.212560] end_request: I/O error, dev sda, sector 31744439
[  209.212563] __ratelimit: 15 callbacks suppressed
[  209.212566] Buffer I/O error on device sda1, logical block 31744376
[  209.212576] ata1: EH complete
[  209.212609] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  209.212629] sd 0:0:0:0: [sda] Write Protect is off
[  209.212632] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  209.212664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  230.475736] udev: starting version 141
[  231.322185] Bluetooth: Generic Bluetooth USB driver ver 0.3
[  231.322333] usbcore: registered new interface driver btusb
[  232.675465] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  232.675471] ata1.00: BMDMA stat 0x25
[  232.675479] ata1.00: cmd c8/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  232.675481]          res 51/10:08:00:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  232.675485] ata1.00: status: { DRDY ERR }
[  232.675487] ata1.00: error: { IDNF }
[  232.688106] cfg80211: Calling CRDA to update world regulatory domain
[  232.700413] ata1.00: configured for UDMA/100
[  232.700430] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  232.700436] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  232.700442] Descriptor sense data with sense descriptors (in hex):
[  232.700445]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  232.700458]         09 50 f8 00 
[  232.700463] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  232.700470] end_request: I/O error, dev sda, sector 156301312
[  232.700476] Buffer I/O error on device sda, logical block 19537664
[  232.700494] ata1: EH complete
[  232.825931] input: PC Speaker as /devices/platform/pcspkr/input/input6
[  232.888626] ricoh-mmc: Ricoh MMC Controller disabling driver
[  232.888631] ricoh-mmc: Copyright(c) Philip Langdale
[  232.888675] ricoh-mmc: Ricoh MMC controller found at 0000:05:05.2 [1180:0843] (rev 1)
[  232.888696] ricoh-mmc: Controller is now disabled.
[  233.154110] Linux agpgart interface v0.103
[  233.215767] intel_rng: FWH not detected
[  233.284219] sdhci: Secure Digital Host Controller Interface driver
[  233.284223] sdhci: Copyright(c) Pierre Ossman
[  233.634090] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input7
[  233.641145] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  233.893785] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[  233.894555] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[  233.898617] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[  233.907665] sdhci-pci 0000:05:05.1: SDHCI controller found [1180:0822] (rev 19)
[  233.907681] sdhci-pci 0000:05:05.1: enabling device (0000 -> 0002)
[  233.907690] sdhci-pci 0000:05:05.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  233.911460] mmc0: SDHCI controller on PCI [0000:05:05.1] using PIO
[  233.978764] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[  234.146723] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  234.146729] ata1.00: BMDMA stat 0x25
[  234.146737] ata1.00: cmd c8/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  234.146738]          res 51/10:08:00:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  234.146743] ata1.00: status: { DRDY ERR }
[  234.146745] ata1.00: error: { IDNF }
[  234.155755] cfg80211: World regulatory domain updated:
[  234.155759] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  234.155763] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  234.155766] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  234.155770] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  234.155773] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  234.155776] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  234.168580] ata1.00: configured for UDMA/100
[  234.168596] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  234.168601] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  234.168607] Descriptor sense data with sense descriptors (in hex):
[  234.168610]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  234.168623]         09 50 f8 00 
[  234.168628] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  234.168635] end_request: I/O error, dev sda, sector 156301312
[  234.168640] Buffer I/O error on device sda, logical block 19537664
[  234.168654] ata1: EH complete
[  234.168686] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  234.168726] sd 0:0:0:0: [sda] Write Protect is off
[  234.168729] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  234.299475] iTCO_vendor_support: vendor-support=0
[  234.301400] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[  234.301593] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
[  234.301692] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  234.375364] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[  234.375369] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[  234.375505] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  234.375521] iwl3945 0000:02:00.0: setting latency timer to 64
[  234.375569] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[  234.377266] iwl3945 0000:02:00.0: irq 2301 for MSI/MSI-X
[  234.418796] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[  234.419767] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  234.635761] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  234.635849] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  234.955649] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[  235.017451] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[  235.595861] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  235.595866] ata1.00: BMDMA stat 0x25
[  235.595874] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  235.595876]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  235.595880] ata1.00: status: { DRDY ERR }
[  235.595883] ata1.00: error: { IDNF }
[  235.620412] ata1.00: configured for UDMA/100
[  235.620424] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  235.620429] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  235.620436] Descriptor sense data with sense descriptors (in hex):
[  235.620439]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  235.620452]         09 50 f8 a0 
[  235.620457] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  235.620463] end_request: I/O error, dev sda, sector 156301472
[  235.620468] Buffer I/O error on device sda, logical block 19537684
[  235.620481] ata1: EH complete
[  237.100312] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  237.100318] ata1.00: BMDMA stat 0x25
[  237.100326] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  237.100328]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  237.100332] ata1.00: status: { DRDY ERR }
[  237.100335] ata1.00: error: { IDNF }
[  237.124516] ata1.00: configured for UDMA/100
[  237.124532] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  237.124537] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  237.124543] Descriptor sense data with sense descriptors (in hex):
[  237.124547]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  237.124559]         09 50 f8 a0 
[  237.124565] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  237.124571] end_request: I/O error, dev sda, sector 156301472
[  237.124577] Buffer I/O error on device sda, logical block 19537684
[  237.124599] ata1: EH complete
[  237.124635] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  237.152431] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  238.571556] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  238.571559] ata1.00: BMDMA stat 0x25
[  238.571565] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  238.571567]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  238.571571] ata1.00: status: { DRDY ERR }
[  238.571573] ata1.00: error: { IDNF }
[  238.592515] ata1.00: configured for UDMA/100
[  238.592521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  238.592526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  238.592531] Descriptor sense data with sense descriptors (in hex):
[  238.592534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  238.592547]         09 50 f8 a8 
[  238.592552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  238.592558] end_request: I/O error, dev sda, sector 156301480
[  238.592561] Buffer I/O error on device sda, logical block 19537685
[  238.592572] ata1: EH complete
[  238.592589] sd 0:0:0:0: [sda] Write Protect is off
[  238.592592] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  240.064943] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  240.064946] ata1.00: BMDMA stat 0x25
[  240.064952] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  240.064954]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  240.064958] ata1.00: status: { DRDY ERR }
[  240.064960] ata1.00: error: { IDNF }
[  240.088517] ata1.00: configured for UDMA/100
[  240.088523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  240.088527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  240.088533] Descriptor sense data with sense descriptors (in hex):
[  240.088536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  240.088548]         09 50 f8 a8 
[  240.088553] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  240.088559] end_request: I/O error, dev sda, sector 156301480
[  240.088563] Buffer I/O error on device sda, logical block 19537685
[  240.088573] ata1: EH complete
[  240.088666] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  241.514081] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  241.514084] ata1.00: BMDMA stat 0x25
[  241.514090] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  241.514092]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  241.514096] ata1.00: status: { DRDY ERR }
[  241.514098] ata1.00: error: { IDNF }
[  241.536537] ata1.00: configured for UDMA/100
[  241.536543] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  241.536547] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  241.536553] Descriptor sense data with sense descriptors (in hex):
[  241.536556]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  241.536568]         09 50 f8 a8 
[  241.536574] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  241.536579] end_request: I/O error, dev sda, sector 156301480
[  241.536583] Buffer I/O error on device sda, logical block 19537685
[  241.536593] ata1: EH complete
[  241.536687] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  242.963220] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  242.963223] ata1.00: BMDMA stat 0x25
[  242.963229] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  242.963230]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  242.963234] ata1.00: status: { DRDY ERR }
[  242.963237] ata1.00: error: { IDNF }
[  242.984517] ata1.00: configured for UDMA/100
[  242.984523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  242.984527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  242.984533] Descriptor sense data with sense descriptors (in hex):
[  242.984535]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  242.984548]         09 50 f8 a8 
[  242.984553] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  242.984559] end_request: I/O error, dev sda, sector 156301480
[  242.984562] Buffer I/O error on device sda, logical block 19537685
[  242.984572] ata1: EH complete
[  242.984589] sd 0:0:0:0: [sda] Write Protect is off
[  242.984592] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  244.423421] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  244.423424] ata1.00: BMDMA stat 0x25
[  244.423430] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  244.423432]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  244.423436] ata1.00: status: { DRDY ERR }
[  244.423438] ata1.00: error: { IDNF }
[  244.444504] ata1.00: configured for UDMA/100
[  244.444510] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  244.444514] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  244.444520] Descriptor sense data with sense descriptors (in hex):
[  244.444523]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  244.444535]         09 50 f8 a8 
[  244.444540] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  244.444546] end_request: I/O error, dev sda, sector 156301480
[  244.444549] Buffer I/O error on device sda, logical block 19537685
[  244.444559] ata1: EH complete
[  244.444651] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  245.905747] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  245.905750] ata1.00: BMDMA stat 0x25
[  245.905756] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  245.905757]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  245.905761] ata1.00: status: { DRDY ERR }
[  245.905764] ata1.00: error: { IDNF }
[  245.928503] ata1.00: configured for UDMA/100
[  245.928508] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  245.928513] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  245.928518] Descriptor sense data with sense descriptors (in hex):
[  245.928521]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  245.928534]         09 50 f8 a8 
[  245.928539] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  245.928544] end_request: I/O error, dev sda, sector 156301480
[  245.928548] Buffer I/O error on device sda, logical block 19537685
[  245.928558] ata1: EH complete
[  245.928596] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  247.365947] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  247.365950] ata1.00: BMDMA stat 0x25
[  247.365956] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  247.365958]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  247.365962] ata1.00: status: { DRDY ERR }
[  247.365964] ata1.00: error: { IDNF }
[  247.388534] ata1.00: configured for UDMA/100
[  247.388539] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  247.388544] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  247.388549] Descriptor sense data with sense descriptors (in hex):
[  247.388552]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  247.388565]         09 50 f8 a8 
[  247.388570] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  247.388575] end_request: I/O error, dev sda, sector 156301480
[  247.388579] Buffer I/O error on device sda, logical block 19537685
[  247.388589] ata1: EH complete
[  247.388606] sd 0:0:0:0: [sda] Write Protect is off
[  247.388609] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  248.770838] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  248.770841] ata1.00: BMDMA stat 0x25
[  248.770847] ata1.00: cmd c8/00:08:70:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  248.770849]          res 51/10:08:70:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  248.770852] ata1.00: status: { DRDY ERR }
[  248.770855] ata1.00: error: { IDNF }
[  248.792462] ata1.00: configured for UDMA/100
[  248.792467] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  248.792472] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  248.792477] Descriptor sense data with sense descriptors (in hex):
[  248.792480]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  248.792493]         09 50 f8 70 
[  248.792498] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  248.792503] end_request: I/O error, dev sda, sector 156301424
[  248.792507] Buffer I/O error on device sda, logical block 19537678
[  248.792517] ata1: EH complete
[  248.792533] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  250.242101] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  250.242104] ata1.00: BMDMA stat 0x25
[  250.242110] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  250.242112]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  250.242115] ata1.00: status: { DRDY ERR }
[  250.242118] ata1.00: error: { IDNF }
[  250.264471] ata1.00: configured for UDMA/100
[  250.264476] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  250.264480] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  250.264486] Descriptor sense data with sense descriptors (in hex):
[  250.264489]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  250.264502]         09 50 f8 a0 
[  250.264507] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  250.264512] end_request: I/O error, dev sda, sector 156301472
[  250.264516] Buffer I/O error on device sda, logical block 19537684
[  250.264526] ata1: EH complete
[  250.264544] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  251.746551] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  251.746554] ata1.00: BMDMA stat 0x25
[  251.746560] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  251.746561]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  251.746565] ata1.00: status: { DRDY ERR }
[  251.746568] ata1.00: error: { IDNF }
[  251.768515] ata1.00: configured for UDMA/100
[  251.768521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  251.768525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  251.768531] Descriptor sense data with sense descriptors (in hex):
[  251.768534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  251.768546]         09 50 f8 a8 
[  251.768551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  251.768557] end_request: I/O error, dev sda, sector 156301480
[  251.768560] Buffer I/O error on device sda, logical block 19537685
[  251.768570] ata1: EH complete
[  251.768587] sd 0:0:0:0: [sda] Write Protect is off
[  251.768590] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  253.251000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  253.251003] ata1.00: BMDMA stat 0x25
[  253.251009] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  253.251010]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  253.251014] ata1.00: status: { DRDY ERR }
[  253.251017] ata1.00: error: { IDNF }
[  253.272518] ata1.00: configured for UDMA/100
[  253.272524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  253.272528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  253.272534] Descriptor sense data with sense descriptors (in hex):
[  253.272536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  253.272549]         09 50 f8 a8 
[  253.272554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  253.272560] end_request: I/O error, dev sda, sector 156301480
[  253.272563] Buffer I/O error on device sda, logical block 19537685
[  253.272573] ata1: EH complete
[  253.272605] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  253.272641] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  253.303221] sd 0:0:0:0: [sda] Write Protect is off
[  253.303225] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  253.303974] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  254.711214] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  254.711220] ata1.00: BMDMA stat 0x25
[  254.711228] ata1.00: cmd c8/00:01:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  254.711229]          res 51/10:01:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  254.711234] ata1.00: status: { DRDY ERR }
[  254.711236] ata1.00: error: { IDNF }
[  254.732516] ata1.00: configured for UDMA/100
[  254.732526] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  254.732531] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  254.732538] Descriptor sense data with sense descriptors (in hex):
[  254.732541]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  254.732554]         01 e4 60 bf 
[  254.732559] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  254.732566] end_request: I/O error, dev sda, sector 31744191
[  254.732571] Buffer I/O error on device sda1, logical block 31744128
[  254.732582] ata1: EH complete
[  257.576297] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  257.576300] ata1.00: BMDMA stat 0x25
[  257.576306] ata1.00: cmd c8/00:07:c0:60:e4/00:00:00:00:00/e1 tag 0 dma 3584 in
[  257.576308]          res 51/10:07:c0:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  257.576312] ata1.00: status: { DRDY ERR }
[  257.576314] ata1.00: error: { IDNF }
[  257.600516] ata1.00: configured for UDMA/100
[  257.600523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  257.600527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  257.600533] Descriptor sense data with sense descriptors (in hex):
[  257.600536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  257.600549]         01 e4 60 c0 
[  257.600554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  257.600559] end_request: I/O error, dev sda, sector 31744192
[  257.600563] Buffer I/O error on device sda1, logical block 31744129
[  257.600567] Buffer I/O error on device sda1, logical block 31744130
[  257.600571] Buffer I/O error on device sda1, logical block 31744131
[  257.600575] Buffer I/O error on device sda1, logical block 31744132
[  257.600578] Buffer I/O error on device sda1, logical block 31744133
[  257.600582] Buffer I/O error on device sda1, logical block 31744134
[  257.600586] Buffer I/O error on device sda1, logical block 31744135
[  257.600596] ata1: EH complete
[  257.600680] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  259.047560] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  259.047563] ata1.00: BMDMA stat 0x25
[  259.047569] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  259.047571]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  259.047574] ata1.00: status: { DRDY ERR }
[  259.047577] ata1.00: error: { IDNF }
[  259.068537] ata1.00: configured for UDMA/100
[  259.068543] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  259.068547] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  259.068553] Descriptor sense data with sense descriptors (in hex):
[  259.068556]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  259.068568]         01 e4 61 b8 
[  259.068573] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  259.068579] end_request: I/O error, dev sda, sector 31744440
[  259.068583] Buffer I/O error on device sda2, logical block 0
[  259.068592] ata1: EH complete
[  259.068665] sd 0:0:0:0: [sda] Write Protect is off
[  259.068669] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  260.540946] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  260.540949] ata1.00: BMDMA stat 0x25
[  260.540955] ata1.00: cmd c8/00:08:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  260.540956]          res 51/10:08:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  260.540960] ata1.00: status: { DRDY ERR }
[  260.540963] ata1.00: error: { IDNF }
[  260.564515] ata1.00: configured for UDMA/100
[  260.564521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  260.564525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  260.564531] Descriptor sense data with sense descriptors (in hex):
[  260.564534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  260.564546]         01 e4 60 bf 
[  260.564551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  260.564557] end_request: I/O error, dev sda, sector 31744191
[  260.564561] Buffer I/O error on device sda1, logical block 31744128
[  260.564565] Buffer I/O error on device sda1, logical block 31744129
[  260.564569] Buffer I/O error on device sda1, logical block 31744130
[  260.564572] Buffer I/O error on device sda1, logical block 31744131
[  260.564576] Buffer I/O error on device sda1, logical block 31744132
[  260.564580] Buffer I/O error on device sda1, logical block 31744133
[  260.564583] Buffer I/O error on device sda1, logical block 31744134
[  260.564587] Buffer I/O error on device sda1, logical block 31744135
[  260.564600] ata1: EH complete
[  262.034333] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  262.034336] ata1.00: BMDMA stat 0x25
[  262.034342] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  262.034344]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  262.034347] ata1.00: status: { DRDY ERR }
[  262.034350] ata1.00: error: { IDNF }
[  262.056518] ata1.00: configured for UDMA/100
[  262.056524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  262.056528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  262.056533] Descriptor sense data with sense descriptors (in hex):
[  262.056536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  262.056549]         01 e4 61 b8 
[  262.056554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  262.056560] end_request: I/O error, dev sda, sector 31744440
[  262.056563] Buffer I/O error on device sda2, logical block 0
[  262.056572] ata1: EH complete
[  262.056644] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  263.538788] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  263.538791] ata1.00: BMDMA stat 0x25
[  263.538798] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  263.538800]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  263.538803] ata1.00: status: { DRDY ERR }
[  263.538806] ata1.00: error: { IDNF }
[  263.560516] ata1.00: configured for UDMA/100
[  263.560525] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  263.560530] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  263.560535] Descriptor sense data with sense descriptors (in hex):
[  263.560538]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  263.560551]         01 e4 61 a7 
[  263.560556] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  263.560562] end_request: I/O error, dev sda, sector 31744423
[  263.560566] Buffer I/O error on device sda1, logical block 31744360
[  263.560585] ata1: EH complete
[  263.560693] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  264.987921] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  264.987924] ata1.00: BMDMA stat 0x25
[  264.987930] ata1.00: cmd c8/00:05:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 2560 in
[  264.987931]          res 51/10:05:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  264.987935] ata1.00: status: { DRDY ERR }
[  264.987938] ata1.00: error: { IDNF }
[  265.012515] ata1.00: configured for UDMA/100
[  265.012521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  265.012525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  265.012531] Descriptor sense data with sense descriptors (in hex):
[  265.012534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  265.012546]         01 e4 61 a7 
[  265.012551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  265.012557] end_request: I/O error, dev sda, sector 31744423
[  265.012568] ata1: EH complete
[  265.012640] sd 0:0:0:0: [sda] Write Protect is off
[  265.012643] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  266.602991] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  266.602994] ata1.00: BMDMA stat 0x25
[  266.603000] ata1.00: cmd c8/00:03:ac:61:e4/00:00:00:00:00/e1 tag 0 dma 1536 in
[  266.603002]          res 51/10:03:ac:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  266.603006] ata1.00: status: { DRDY ERR }
[  266.603008] ata1.00: error: { IDNF }
[  266.624517] ata1.00: configured for UDMA/100
[  266.624523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  266.624527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  266.624533] Descriptor sense data with sense descriptors (in hex):
[  266.624535]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  266.624548]         01 e4 61 ac 
[  266.624553] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  266.624559] end_request: I/O error, dev sda, sector 31744428
[  266.624562] __ratelimit: 12 callbacks suppressed
[  266.624565] Buffer I/O error on device sda1, logical block 31744365
[  266.624570] Buffer I/O error on device sda1, logical block 31744366
[  266.624573] Buffer I/O error on device sda1, logical block 31744367
[  266.624583] ata1: EH complete
[  266.624617] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  266.655647] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  266.655996] sd 0:0:0:0: [sda] Write Protect is off
[  266.656000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  268.085318] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  268.085321] ata1.00: BMDMA stat 0x25
[  268.085327] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  268.085328]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  268.085332] ata1.00: status: { DRDY ERR }
[  268.085335] ata1.00: error: { IDNF }
[  268.108540] ata1.00: configured for UDMA/100
[  268.108546] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  268.108550] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  268.108556] Descriptor sense data with sense descriptors (in hex):
[  268.108559]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  268.108571]         01 e4 61 b7 
[  268.108576] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  268.108582] end_request: I/O error, dev sda, sector 31744439
[  268.108586] Buffer I/O error on device sda1, logical block 31744376
[  268.108596] ata1: EH complete
[  269.600829] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  269.600832] ata1.00: BMDMA stat 0x25
[  269.600838] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  269.600840]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  269.600843] ata1.00: status: { DRDY ERR }
[  269.600846] ata1.00: error: { IDNF }
[  269.624514] ata1.00: configured for UDMA/100
[  269.624519] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  269.624524] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  269.624529] Descriptor sense data with sense descriptors (in hex):
[  269.624532]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  269.624545]         01 e4 61 b7 
[  269.624550] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  269.624555] end_request: I/O error, dev sda, sector 31744439
[  269.624559] Buffer I/O error on device sda1, logical block 31744376
[  269.624569] ata1: EH complete
[  269.624586] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  269.624685] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  271.049968] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  271.049971] ata1.00: BMDMA stat 0x25
[  271.049977] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  271.049979]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  271.049982] ata1.00: status: { DRDY ERR }
[  271.049985] ata1.00: error: { IDNF }
[  271.072517] ata1.00: configured for UDMA/100
[  271.072523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  271.072527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  271.072533] Descriptor sense data with sense descriptors (in hex):
[  271.072536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  271.072549]         01 e4 61 af 
[  271.072554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  271.072559] end_request: I/O error, dev sda, sector 31744431
[  271.072563] Buffer I/O error on device sda1, logical block 31744368
[  271.072567] Buffer I/O error on device sda1, logical block 31744369
[  271.072570] Buffer I/O error on device sda1, logical block 31744370
[  271.072574] Buffer I/O error on device sda1, logical block 31744371
[  271.072578] Buffer I/O error on device sda1, logical block 31744372
[  271.072589] ata1: EH complete
[  271.072606] sd 0:0:0:0: [sda] Write Protect is off
[  271.072609] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  272.510167] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  272.510170] ata1.00: BMDMA stat 0x25
[  272.510176] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  272.510178]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  272.510182] ata1.00: status: { DRDY ERR }
[  272.510184] ata1.00: error: { IDNF }
[  272.532516] ata1.00: configured for UDMA/100
[  272.532522] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  272.532526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  272.532532] Descriptor sense data with sense descriptors (in hex):
[  272.532535]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  272.532547]         01 e4 61 b7 
[  272.532552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  272.532558] end_request: I/O error, dev sda, sector 31744439
[  272.532561] __ratelimit: 3 callbacks suppressed
[  272.532564] Buffer I/O error on device sda1, logical block 31744376
[  272.532574] ata1: EH complete
[  272.532591] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  273.970371] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  273.970374] ata1.00: BMDMA stat 0x25
[  273.970379] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  273.970381]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  273.970385] ata1.00: status: { DRDY ERR }
[  273.970387] ata1.00: error: { IDNF }
[  273.992516] ata1.00: configured for UDMA/100
[  273.992522] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  273.992526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  273.992531] Descriptor sense data with sense descriptors (in hex):
[  273.992534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  273.992547]         01 e4 61 b7 
[  273.992552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  273.992557] end_request: I/O error, dev sda, sector 31744439
[  273.992561] Buffer I/O error on device sda1, logical block 31744376
[  273.992571] ata1: EH complete
[  273.992589] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  273.992670] sd 0:0:0:0: [sda] Write Protect is off
[  273.992673] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  275.441635] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  275.441638] ata1.00: BMDMA stat 0x25
[  275.441644] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  275.441646]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  275.441650] ata1.00: status: { DRDY ERR }
[  275.441652] ata1.00: error: { IDNF }
[  275.464503] ata1.00: configured for UDMA/100
[  275.464509] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  275.464513] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  275.464518] Descriptor sense data with sense descriptors (in hex):
[  275.464521]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  275.464534]         01 e4 61 b7 
[  275.464539] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  275.464544] end_request: I/O error, dev sda, sector 31744439
[  275.464548] Buffer I/O error on device sda1, logical block 31744376
[  275.464558] ata1: EH complete
[  275.464654] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  276.879711] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  276.879714] ata1.00: BMDMA stat 0x25
[  276.879720] ata1.00: cmd c8/00:06:af:61:e4/00:00:00:00:00/e1 tag 0 dma 3072 in
[  276.879722]          res 51/10:06:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  276.879726] ata1.00: status: { DRDY ERR }
[  276.879728] ata1.00: error: { IDNF }
[  276.900504] ata1.00: configured for UDMA/100
[  276.900510] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  276.900514] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  276.900519] Descriptor sense data with sense descriptors (in hex):
[  276.900522]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  276.900535]         01 e4 61 af 
[  276.900540] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  276.900545] end_request: I/O error, dev sda, sector 31744431
[  276.900549] Buffer I/O error on device sda1, logical block 31744368
[  276.900553] Buffer I/O error on device sda1, logical block 31744369
[  276.900557] Buffer I/O error on device sda1, logical block 31744370
[  276.900561] Buffer I/O error on device sda1, logical block 31744371
[  276.900564] Buffer I/O error on device sda1, logical block 31744372
[  276.900568] Buffer I/O error on device sda1, logical block 31744373
[  276.900576] ata1: EH complete
[  278.339912] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  278.339916] ata1.00: BMDMA stat 0x25
[  278.339921] ata1.00: cmd c8/00:02:b5:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  278.339923]          res 51/10:02:b5:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  278.339927] ata1.00: status: { DRDY ERR }
[  278.339929] ata1.00: error: { IDNF }
[  278.364502] ata1.00: configured for UDMA/100
[  278.364508] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  278.364512] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  278.364518] Descriptor sense data with sense descriptors (in hex):
[  278.364521]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  278.364534]         01 e4 61 b5 
[  278.364539] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  278.364544] end_request: I/O error, dev sda, sector 31744437
[  278.364548] Buffer I/O error on device sda1, logical block 31744374
[  278.364559] ata1: EH complete
[  278.364577] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  278.364661] sd 0:0:0:0: [sda] Write Protect is off
[  278.364665] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  279.766927] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  279.766930] ata1.00: BMDMA stat 0x25
[  279.766936] ata1.00: cmd c8/00:06:77:61:e4/00:00:00:00:00/e1 tag 0 dma 3072 in
[  279.766938]          res 51/10:06:77:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  279.766942] ata1.00: status: { DRDY ERR }
[  279.766944] ata1.00: error: { IDNF }
[  279.788486] ata1.00: configured for UDMA/100
[  279.788491] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  279.788496] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  279.788501] Descriptor sense data with sense descriptors (in hex):
[  279.788504]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  279.788517]         01 e4 61 77 
[  279.788522] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  279.788527] end_request: I/O error, dev sda, sector 31744375
[  279.788531] __ratelimit: 1 callbacks suppressed
[  279.788534] Buffer I/O error on device sda1, logical block 31744312
[  279.788538] Buffer I/O error on device sda1, logical block 31744313
[  279.788541] Buffer I/O error on device sda1, logical block 31744314
[  279.788545] Buffer I/O error on device sda1, logical block 31744315
[  279.788549] Buffer I/O error on device sda1, logical block 31744316
[  279.788552] Buffer I/O error on device sda1, logical block 31744317
[  279.788560] ata1: EH complete
[  281.393060] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  281.393063] ata1.00: BMDMA stat 0x25
[  281.393069] ata1.00: cmd c8/00:02:7d:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  281.393071]          res 51/10:02:7d:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  281.393075] ata1.00: status: { DRDY ERR }
[  281.393077] ata1.00: error: { IDNF }
[  281.416479] ata1.00: configured for UDMA/100
[  281.416485] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  281.416489] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  281.416495] Descriptor sense data with sense descriptors (in hex):
[  281.416498]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  281.416510]         01 e4 61 7d 
[  281.416515] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  281.416521] end_request: I/O error, dev sda, sector 31744381
[  281.416525] Buffer I/O error on device sda1, logical block 31744318
[  281.416529] Buffer I/O error on device sda1, logical block 31744319
[  281.416539] ata1: EH complete
[  281.416555] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  282.864325] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  282.864328] ata1.00: BMDMA stat 0x25
[  282.864334] ata1.00: cmd c8/00:04:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 2048 in
[  282.864336]          res 51/10:04:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  282.864339] ata1.00: status: { DRDY ERR }
[  282.864342] ata1.00: error: { IDNF }
[  282.888517] ata1.00: configured for UDMA/100
[  282.888523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  282.888527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  282.888532] Descriptor sense data with sense descriptors (in hex):
[  282.888535]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  282.888548]         01 e4 61 a7 
[  282.888553] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  282.888558] end_request: I/O error, dev sda, sector 31744423
[  282.888562] Buffer I/O error on device sda1, logical block 31744360
[  282.888566] Buffer I/O error on device sda1, logical block 31744361
[  282.888575] ata1: EH complete
[  282.888648] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  284.501519] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  284.501522] ata1.00: BMDMA stat 0x25
[  284.501527] ata1.00: cmd c8/00:04:ab:61:e4/00:00:00:00:00/e1 tag 0 dma 2048 in
[  284.501529]          res 51/10:04:ab:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  284.501533] ata1.00: status: { DRDY ERR }
[  284.501535] ata1.00: error: { IDNF }
[  284.524514] ata1.00: configured for UDMA/100
[  284.524520] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  284.524524] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  284.524530] Descriptor sense data with sense descriptors (in hex):
[  284.524533]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  284.524546]         01 e4 61 ab 
[  284.524551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  284.524556] end_request: I/O error, dev sda, sector 31744427
[  284.524569] ata1: EH complete
[  284.524585] sd 0:0:0:0: [sda] Write Protect is off
[  284.524588] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  285.939599] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  285.939602] ata1.00: BMDMA stat 0x25
[  285.939608] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  285.939609]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  285.939613] ata1.00: status: { DRDY ERR }
[  285.939615] ata1.00: error: { IDNF }
[  285.960515] ata1.00: configured for UDMA/100
[  285.960521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  285.960525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  285.960530] Descriptor sense data with sense descriptors (in hex):
[  285.960533]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  285.960546]         01 e4 61 b7 
[  285.960551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  285.960556] end_request: I/O error, dev sda, sector 31744439
[  285.960560] __ratelimit: 6 callbacks suppressed
[  285.960563] Buffer I/O error on device sda1, logical block 31744376
[  285.960573] ata1: EH complete
[  285.960665] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  287.377676] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  287.377679] ata1.00: BMDMA stat 0x25
[  287.377685] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  287.377686]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  287.377690] ata1.00: status: { DRDY ERR }
[  287.377693] ata1.00: error: { IDNF }
[  287.400517] ata1.00: configured for UDMA/100
[  287.400523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  287.400527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  287.400533] Descriptor sense data with sense descriptors (in hex):
[  287.400536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  287.400548]         01 e4 61 b7 
[  287.400554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  287.400559] end_request: I/O error, dev sda, sector 31744439
[  287.400563] Buffer I/O error on device sda1, logical block 31744376
[  287.400573] ata1: EH complete
[  287.400605] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  287.400626] sd 0:0:0:0: [sda] Write Protect is off
[  287.400629] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  287.430563] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  287.431323] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  287.431708] sd 0:0:0:0: [sda] Write Protect is off
[  287.431711] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  287.432388] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  292.500137] Clocksource tsc unstable (delta = -164184383 ns)
[  302.223083] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  302.223089] ata1.00: BMDMA stat 0x25
[  302.223097] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  302.223098]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  302.223103] ata1.00: status: { DRDY ERR }
[  302.223105] ata1.00: error: { IDNF }
[  302.244518] ata1.00: configured for UDMA/100
[  302.244532] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  302.244538] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  302.244544] Descriptor sense data with sense descriptors (in hex):
[  302.244547]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  302.244560]         01 e4 61 b8 
[  302.244565] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  302.244572] end_request: I/O error, dev sda, sector 31744440
[  302.244578] Buffer I/O error on device sda, logical block 3968055
[  302.244596] ata1: EH complete
[  303.672201] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  303.672204] ata1.00: BMDMA stat 0x25
[  303.672211] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  303.672212]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  303.672216] ata1.00: status: { DRDY ERR }
[  303.672219] ata1.00: error: { IDNF }
[  303.696518] ata1.00: configured for UDMA/100
[  303.696525] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  303.696529] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  303.696535] Descriptor sense data with sense descriptors (in hex):
[  303.696538]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  303.696551]         01 e4 61 b8 
[  303.696556] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  303.696562] end_request: I/O error, dev sda, sector 31744440
[  303.696565] Buffer I/O error on device sda, logical block 3968055
[  303.696577] ata1: EH complete
[  303.696600] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  303.696626] sd 0:0:0:0: [sda] Write Protect is off
[  303.696629] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  303.696664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  303.696701] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  303.696720] sd 0:0:0:0: [sda] Write Protect is off
[  303.696723] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  303.696872] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  305.143474] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  305.143480] ata1.00: BMDMA stat 0x25
[  305.143487] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  305.143489]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  305.143493] ata1.00: status: { DRDY ERR }
[  305.143496] ata1.00: error: { IDNF }
[  305.164516] ata1.00: configured for UDMA/100
[  305.164530] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  305.164535] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  305.164542] Descriptor sense data with sense descriptors (in hex):
[  305.164545]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  305.164558]         01 e4 61 b8 
[  305.164563] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  305.164569] end_request: I/O error, dev sda, sector 31744440
[  305.164575] Buffer I/O error on device sda2, logical block 0
[  305.164592] ata1: EH complete
[  306.636849] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  306.636852] ata1.00: BMDMA stat 0x25
[  306.636858] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
[  306.636860]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  306.636864] ata1.00: status: { DRDY ERR }
[  306.636866] ata1.00: error: { IDNF }
[  306.660506] ata1.00: configured for UDMA/100
[  306.660513] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  306.660517] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  306.660523] Descriptor sense data with sense descriptors (in hex):
[  306.660526]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  306.660539]         01 e4 61 b8 
[  306.660544] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  306.660549] end_request: I/O error, dev sda, sector 31744440
[  306.660553] Buffer I/O error on device sda2, logical block 0
[  306.660564] ata1: EH complete
[  306.660587] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  306.660612] sd 0:0:0:0: [sda] Write Protect is off
[  306.660615] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  306.660716] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  306.688928] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  308.108112] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  308.108116] ata1.00: BMDMA stat 0x25
[  308.108122] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  308.108123]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  308.108127] ata1.00: status: { DRDY ERR }
[  308.108130] ata1.00: error: { IDNF }
[  308.132505] ata1.00: configured for UDMA/100
[  308.132512] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  308.132517] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  308.132523] Descriptor sense data with sense descriptors (in hex):
[  308.132525]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  308.132538]         01 e4 61 b8 
[  308.132543] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  308.132549] end_request: I/O error, dev sda, sector 31744440
[  308.132553] Buffer I/O error on device sda, logical block 3968055
[  308.132564] ata1: EH complete
[  308.132582] sd 0:0:0:0: [sda] Write Protect is off
[  308.132586] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  309.535126] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  309.535130] ata1.00: BMDMA stat 0x25
[  309.535136] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  309.535137]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  309.535141] ata1.00: status: { DRDY ERR }
[  309.535144] ata1.00: error: { IDNF }
[  309.556503] ata1.00: configured for UDMA/100
[  309.556510] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  309.556514] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  309.556520] Descriptor sense data with sense descriptors (in hex):
[  309.556523]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  309.556535]         01 e4 61 b8 
[  309.556540] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  309.556546] end_request: I/O error, dev sda, sector 31744440
[  309.556550] Buffer I/O error on device sda, logical block 3968055
[  309.556561] ata1: EH complete
[  309.556595] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  309.556632] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  309.556651] sd 0:0:0:0: [sda] Write Protect is off
[  309.556655] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  309.556687] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  310.368520] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  310.368524] Bluetooth: BNEP filters: protocol multicast
[  310.412527] Bridge firewalling registered
[  317.346748] lp: driver loaded but no devices found
[  317.421050] ppdev: user-space parallel port driver
[  319.149291] [drm] Initialized drm 1.1.0 20060810
[  319.203057] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  319.203064] pci 0000:00:02.0: setting latency timer to 64
[  319.203267] [drm] Initialized i915 1.6.0 20080730 on minor 0
[  319.206410] [drm:i915_setparam] *ERROR* unknown parameter 4
[  319.206438] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  319.350971] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  319.352113] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-1.ucode
[  319.936062] Registered led device: iwl-phy0:radio
[  319.936087] Registered led device: iwl-phy0:assoc
[  319.936145] Registered led device: iwl-phy0:RX
[  319.936165] Registered led device: iwl-phy0:TX
[  319.945490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  320.786632] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  324.734494] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  324.734500] ata1.00: BMDMA stat 0x25
[  324.734508] ata1.00: cmd c8/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  324.734509]          res 51/10:08:00:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  324.734514] ata1.00: status: { DRDY ERR }
[  324.734516] ata1.00: error: { IDNF }
[  324.764400] ata1.00: configured for UDMA/100
[  324.764421] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  324.764426] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  324.764433] Descriptor sense data with sense descriptors (in hex):
[  324.764436]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  324.764449]         09 50 f8 00 
[  324.764454] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  324.764461] end_request: I/O error, dev sda, sector 156301312
[  324.764468] Buffer I/O error on device sda, logical block 19537664
[  324.764490] ata1: EH complete
[  326.194718] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  326.194724] ata1.00: BMDMA stat 0x25
[  326.194732] ata1.00: cmd c8/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  326.194734]          res 51/10:08:00:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  326.194738] ata1.00: status: { DRDY ERR }
[  326.194741] ata1.00: error: { IDNF }
[  326.216415] ata1.00: configured for UDMA/100
[  326.216429] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  326.216435] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  326.216441] Descriptor sense data with sense descriptors (in hex):
[  326.216445]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  326.216457]         09 50 f8 00 
[  326.216463] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  326.216469] end_request: I/O error, dev sda, sector 156301312
[  326.216475] Buffer I/O error on device sda, logical block 19537664
[  326.216490] ata1: EH complete
[  326.216627] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  327.621728] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  327.621734] ata1.00: BMDMA stat 0x25
[  327.621742] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  327.621744]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  327.621748] ata1.00: status: { DRDY ERR }
[  327.621750] ata1.00: error: { IDNF }
[  327.644398] ata1.00: configured for UDMA/100
[  327.644411] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  327.644416] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  327.644422] Descriptor sense data with sense descriptors (in hex):
[  327.644426]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  327.644438]         09 50 f8 a0 
[  327.644444] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  327.644450] end_request: I/O error, dev sda, sector 156301472
[  327.644456] Buffer I/O error on device sda, logical block 19537684
[  327.644468] ata1: EH complete
[  327.644568] sd 0:0:0:0: [sda] Write Protect is off
[  327.644571] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  329.081928] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  329.081934] ata1.00: BMDMA stat 0x25
[  329.081941] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  329.081943]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  329.081947] ata1.00: status: { DRDY ERR }
[  329.081950] ata1.00: error: { IDNF }
[  329.104441] ata1.00: configured for UDMA/100
[  329.104455] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  329.104460] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  329.104466] Descriptor sense data with sense descriptors (in hex):
[  329.104470]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  329.104482]         09 50 f8 a0 
[  329.104488] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  329.104494] end_request: I/O error, dev sda, sector 156301472
[  329.104499] Buffer I/O error on device sda, logical block 19537684
[  329.104512] ata1: EH complete
[  329.134002] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  330.564251] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  330.564256] ata1.00: BMDMA stat 0x25
[  330.564264] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  330.564266]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  330.564270] ata1.00: status: { DRDY ERR }
[  330.564273] ata1.00: error: { IDNF }
[  330.588447] ata1.00: configured for UDMA/100
[  330.588460] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  330.588465] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  330.588472] Descriptor sense data with sense descriptors (in hex):
[  330.588475]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  330.588488]         09 50 f8 a8 
[  330.588493] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  330.588499] end_request: I/O error, dev sda, sector 156301480
[  330.588504] Buffer I/O error on device sda, logical block 19537685
[  330.588518] ata1: EH complete
[  332.013391] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  332.013397] ata1.00: BMDMA stat 0x25
[  332.013405] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  332.013407]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  332.013411] ata1.00: status: { DRDY ERR }
[  332.013414] ata1.00: error: { IDNF }
[  332.036424] ata1.00: configured for UDMA/100
[  332.036437] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  332.036442] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  332.036448] Descriptor sense data with sense descriptors (in hex):
[  332.036452]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  332.036464]         09 50 f8 a8 
[  332.036470] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  332.036476] end_request: I/O error, dev sda, sector 156301480
[  332.036481] Buffer I/O error on device sda, logical block 19537685
[  332.036495] ata1: EH complete
[  332.036614] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  333.462525] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  333.462530] ata1.00: BMDMA stat 0x25
[  333.462537] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  333.462539]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  333.462543] ata1.00: status: { DRDY ERR }
[  333.462545] ata1.00: error: { IDNF }
[  333.484482] ata1.00: configured for UDMA/100
[  333.484501] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  333.484510] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  333.484522] Descriptor sense data with sense descriptors (in hex):
[  333.484528]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  333.484554]         09 50 f8 a8 
[  333.484564] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  333.484576] end_request: I/O error, dev sda, sector 156301480
[  333.484586] Buffer I/O error on device sda, logical block 19537685
[  333.484612] ata1: EH complete
[  333.484765] sd 0:0:0:0: [sda] Write Protect is off
[  333.484782] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  334.955915] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  334.955921] ata1.00: BMDMA stat 0x25
[  334.955929] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  334.955931]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  334.955935] ata1.00: status: { DRDY ERR }
[  334.955938] ata1.00: error: { IDNF }
[  334.980430] ata1.00: configured for UDMA/100
[  334.980445] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  334.980450] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  334.980457] Descriptor sense data with sense descriptors (in hex):
[  334.980460]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  334.980473]         09 50 f8 a8 
[  334.980478] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  334.980484] end_request: I/O error, dev sda, sector 156301480
[  334.980490] Buffer I/O error on device sda, logical block 19537685
[  334.980507] ata1: EH complete
[  336.405063] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  336.405068] ata1.00: BMDMA stat 0x25
[  336.405076] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  336.405078]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  336.405082] ata1.00: status: { DRDY ERR }
[  336.405084] ata1.00: error: { IDNF }
[  336.428535] ata1.00: configured for UDMA/100
[  336.428547] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  336.428552] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  336.428559] Descriptor sense data with sense descriptors (in hex):
[  336.428562]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  336.428575]         09 50 f8 a8 
[  336.428580] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  336.428587] end_request: I/O error, dev sda, sector 156301480
[  336.428592] Buffer I/O error on device sda, logical block 19537685
[  336.428604] ata1: EH complete
[  336.428719] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  337.887381] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  337.887387] ata1.00: BMDMA stat 0x25
[  337.887395] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  337.887397]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  337.887401] ata1.00: status: { DRDY ERR }
[  337.887404] ata1.00: error: { IDNF }
[  337.908415] ata1.00: configured for UDMA/100
[  337.908427] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  337.908433] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  337.908439] Descriptor sense data with sense descriptors (in hex):
[  337.908442]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  337.908455]         09 50 f8 a8 
[  337.908460] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  337.908467] end_request: I/O error, dev sda, sector 156301480
[  337.908472] Buffer I/O error on device sda, logical block 19537685
[  337.908486] ata1: EH complete
[  339.347557] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  339.347564] ata1.00: BMDMA stat 0x25
[  339.347571] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  339.347573]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  339.347577] ata1.00: status: { DRDY ERR }
[  339.347580] ata1.00: error: { IDNF }
[  339.368414] ata1.00: configured for UDMA/100
[  339.368428] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  339.368433] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  339.368440] Descriptor sense data with sense descriptors (in hex):
[  339.368443]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  339.368456]         09 50 f8 a8 
[  339.368461] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  339.368467] end_request: I/O error, dev sda, sector 156301480
[  339.368472] Buffer I/O error on device sda, logical block 19537685
[  339.368488] ata1: EH complete
[  339.368611] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  340.818851] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  340.818857] ata1.00: BMDMA stat 0x25
[  340.818865] ata1.00: cmd c8/00:08:70:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  340.818867]          res 51/10:08:70:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  340.818871] ata1.00: status: { DRDY ERR }
[  340.818874] ata1.00: error: { IDNF }
[  340.840413] ata1.00: configured for UDMA/100
[  340.840430] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  340.840435] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  340.840442] Descriptor sense data with sense descriptors (in hex):
[  340.840445]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  340.840458]         09 50 f8 70 
[  340.840463] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  340.840469] end_request: I/O error, dev sda, sector 156301424
[  340.840475] Buffer I/O error on device sda, logical block 19537678
[  340.840495] ata1: EH complete
[  340.840627] sd 0:0:0:0: [sda] Write Protect is off
[  340.840631] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  342.301173] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  342.301178] ata1.00: BMDMA stat 0x25
[  342.301186] ata1.00: cmd c8/00:08:a0:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  342.301188]          res 51/10:08:a0:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  342.301192] ata1.00: status: { DRDY ERR }
[  342.301195] ata1.00: error: { IDNF }
[  342.324414] ata1.00: configured for UDMA/100
[  342.324427] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  342.324432] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  342.324438] Descriptor sense data with sense descriptors (in hex):
[  342.324441]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  342.324454]         09 50 f8 a0 
[  342.324459] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  342.324466] end_request: I/O error, dev sda, sector 156301472
[  342.324471] Buffer I/O error on device sda, logical block 19537684
[  342.324484] ata1: EH complete
[  343.717128] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  343.717133] ata1.00: BMDMA stat 0x25
[  343.717141] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  343.717143]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  343.717147] ata1.00: status: { DRDY ERR }
[  343.717150] ata1.00: error: { IDNF }
[  343.740415] ata1.00: configured for UDMA/100
[  343.740428] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  343.740434] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  343.740440] Descriptor sense data with sense descriptors (in hex):
[  343.740443]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  343.740456]         09 50 f8 a8 
[  343.740461] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  343.740468] end_request: I/O error, dev sda, sector 156301480
[  343.740473] Buffer I/O error on device sda, logical block 19537685
[  343.740487] ata1: EH complete
[  343.740602] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  345.177322] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  345.177328] ata1.00: BMDMA stat 0x25
[  345.177335] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  345.177337]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  345.177341] ata1.00: status: { DRDY ERR }
[  345.177344] ata1.00: error: { IDNF }
[  345.200414] ata1.00: configured for UDMA/100
[  345.200427] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  345.200433] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  345.200439] Descriptor sense data with sense descriptors (in hex):
[  345.200442]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  345.200455]         09 50 f8 a8 
[  345.200460] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  345.200467] end_request: I/O error, dev sda, sector 156301480
[  345.200472] Buffer I/O error on device sda, logical block 19537685
[  345.200486] ata1: EH complete
[  345.229467] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  345.229764] sd 0:0:0:0: [sda] Write Protect is off
[  345.229768] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  345.230382] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  345.230920] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  345.231235] sd 0:0:0:0: [sda] Write Protect is off
[  345.231238] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  345.231805] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  348.153983] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  392.490031] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  392.490037] ata1.00: BMDMA stat 0x25
[  392.490045] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  392.490047]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  392.490051] ata1.00: status: { DRDY ERR }
[  392.490054] ata1.00: error: { IDNF }
[  392.516536] ata1.00: configured for UDMA/100
[  392.516551] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  392.516557] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  392.516563] Descriptor sense data with sense descriptors (in hex):
[  392.516567]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  392.516580]         09 50 f8 a8 
[  392.516585] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  392.516591] end_request: I/O error, dev sda, sector 156301480
[  392.516598] Buffer I/O error on device sda, logical block 19537685
[  392.516615] ata1: EH complete
[  393.972443] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  393.972453] ata1.00: BMDMA stat 0x25
[  393.972467] ata1.00: cmd c8/00:08:a8:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
[  393.972470]          res 51/10:08:a8:f8:50/00:00:00:00:00/e9 Emask 0x81 (invalid argument)
[  393.972479] ata1.00: status: { DRDY ERR }
[  393.972484] ata1.00: error: { IDNF }
[  393.996549] ata1.00: configured for UDMA/100
[  393.996582] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  393.996591] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  393.996604] Descriptor sense data with sense descriptors (in hex):
[  393.996610]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  393.996635]         09 50 f8 a8 
[  393.996646] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  393.996658] end_request: I/O error, dev sda, sector 156301480
[  393.996670] Buffer I/O error on device sda, logical block 19537685
[  393.996711] ata1: EH complete
[  393.996776] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  393.996844] sd 0:0:0:0: [sda] Write Protect is off
[  393.996851] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  393.997016] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  394.024474] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  394.025054] sd 0:0:0:0: [sda] Write Protect is off
[  394.025061] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  395.532203] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  395.532213] ata1.00: BMDMA stat 0x25
[  395.532227] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  395.532230]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  395.532238] ata1.00: status: { DRDY ERR }
[  395.532243] ata1.00: error: { IDNF }
[  395.556510] ata1.00: configured for UDMA/100
[  395.556539] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  395.556549] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  395.556561] Descriptor sense data with sense descriptors (in hex):
[  395.556567]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  395.556593]         01 e4 61 b8 
[  395.556603] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  395.556615] end_request: I/O error, dev sda, sector 31744440
[  395.556626] Buffer I/O error on device sda, logical block 3968055
[  395.556664] ata1: EH complete
[  396.981342] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  396.981351] ata1.00: BMDMA stat 0x25
[  396.981365] ata1.00: cmd c8/00:08:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  396.981369]          res 51/10:08:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  396.981377] ata1.00: status: { DRDY ERR }
[  396.981382] ata1.00: error: { IDNF }
[  397.004543] ata1.00: configured for UDMA/100
[  397.004574] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  397.004583] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  397.004596] Descriptor sense data with sense descriptors (in hex):
[  397.004602]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  397.004628]         01 e4 61 b8 
[  397.004638] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  397.004650] end_request: I/O error, dev sda, sector 31744440
[  397.004662] Buffer I/O error on device sda, logical block 3968055
[  397.004703] ata1: EH complete
[  397.004762] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  397.004858] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  397.004898] sd 0:0:0:0: [sda] Write Protect is off
[  397.004904] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  397.004969] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  423.000107] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  423.000131] ata2.00: cmd a0/01:00:00:00:fc/00:00:00:00:00/a0 tag 0 dma 98304 in
[  423.000135]          cdb 28 00 00 00 06 c7 00 00  30 00 00 00 00 00 00 00
[  423.000138]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  423.000146] ata2.00: status: { DRDY }
[  423.000196] ata2: soft resetting link
[  423.180595] ata2.00: configured for MWDMA2
[  423.189919] ata2: EH complete
[  487.613349] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  487.613359] ata1.00: BMDMA stat 0x25
[  487.613373] ata1.00: cmd c8/00:08:f7:30:f2/00:00:00:00:00/e0 tag 0 dma 4096 in
[  487.613377]          res 51/10:08:f7:30:f2/00:00:00:00:00/e0 Emask 0x81 (invalid argument)
[  487.613385] ata1.00: status: { DRDY ERR }
[  487.613390] ata1.00: error: { IDNF }
[  487.636608] ata1.00: configured for UDMA/100
[  487.636640] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  487.636650] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  487.636662] Descriptor sense data with sense descriptors (in hex):
[  487.636668]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  487.636694]         00 f2 30 f7 
[  487.636704] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  487.636716] end_request: I/O error, dev sda, sector 15872247
[  487.636729] Buffer I/O error on device sda1, logical block 15872184
[  487.636739] Buffer I/O error on device sda1, logical block 15872185
[  487.636747] Buffer I/O error on device sda1, logical block 15872186
[  487.636754] Buffer I/O error on device sda1, logical block 15872187
[  487.636762] Buffer I/O error on device sda1, logical block 15872188
[  487.636769] Buffer I/O error on device sda1, logical block 15872189
[  487.636777] Buffer I/O error on device sda1, logical block 15872190
[  487.636784] Buffer I/O error on device sda1, logical block 15872191
[  487.636820] ata1: EH complete
[  489.062487] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  489.062496] ata1.00: BMDMA stat 0x25
[  489.062511] ata1.00: cmd c8/00:08:f7:30:f2/00:00:00:00:00/e0 tag 0 dma 4096 in
[  489.062514]          res 51/10:08:f7:30:f2/00:00:00:00:00/e0 Emask 0x81 (invalid argument)
[  489.062522] ata1.00: status: { DRDY ERR }
[  489.062527] ata1.00: error: { IDNF }
[  489.084623] ata1.00: configured for UDMA/100
[  489.084656] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  489.084666] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  489.084678] Descriptor sense data with sense descriptors (in hex):
[  489.084684]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  489.084710]         00 f2 30 f7 
[  489.084720] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  489.084732] end_request: I/O error, dev sda, sector 15872247
[  489.084744] Buffer I/O error on device sda1, logical block 15872184
[  489.084754] Buffer I/O error on device sda1, logical block 15872185
[  489.084798] ata1: EH complete
[  489.094995] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  489.095103] sd 0:0:0:0: [sda] Write Protect is off
[  489.095110] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  489.095178] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  489.095252] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  489.095292] sd 0:0:0:0: [sda] Write Protect is off
[  489.095298] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  489.095362] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  490.633326] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  490.633336] ata1.00: BMDMA stat 0x25
[  490.633350] ata1.00: cmd c8/00:01:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  490.633354]          res 51/10:01:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  490.633362] ata1.00: status: { DRDY ERR }
[  490.633367] ata1.00: error: { IDNF }
[  490.656618] ata1.00: configured for UDMA/100
[  490.656650] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  490.656660] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  490.656672] Descriptor sense data with sense descriptors (in hex):
[  490.656678]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  490.656704]         01 e4 60 bf 
[  490.656714] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  490.656726] end_request: I/O error, dev sda, sector 31744191
[  490.656764] ata1: EH complete
[  492.093487] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  492.093497] ata1.00: BMDMA stat 0x25
[  492.093511] ata1.00: cmd c8/00:07:c0:60:e4/00:00:00:00:00/e1 tag 0 dma 3584 in
[  492.093515]          res 51/10:07:c0:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  492.093523] ata1.00: status: { DRDY ERR }
[  492.093528] ata1.00: error: { IDNF }
[  492.116574] ata1.00: configured for UDMA/100
[  492.116606] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  492.116615] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  492.116628] Descriptor sense data with sense descriptors (in hex):
[  492.116634]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  492.116659]         01 e4 60 c0 
[  492.116670] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  492.116682] end_request: I/O error, dev sda, sector 31744192
[  492.116730] ata1: EH complete
[  492.116902] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  494.980742] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  494.980752] ata1.00: BMDMA stat 0x25
[  494.980766] ata1.00: cmd c8/00:08:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  494.980770]          res 51/10:08:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  494.980778] ata1.00: status: { DRDY ERR }
[  494.980783] ata1.00: error: { IDNF }
[  495.004544] ata1.00: configured for UDMA/100
[  495.004577] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  495.004587] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  495.004599] Descriptor sense data with sense descriptors (in hex):
[  495.004605]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  495.004631]         01 e4 60 bf 
[  495.004641] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  495.004653] end_request: I/O error, dev sda, sector 31744191
[  495.004664] __ratelimit: 14 callbacks suppressed
[  495.004671] Buffer I/O error on device sda1, logical block 31744128
[  495.004681] Buffer I/O error on device sda1, logical block 31744129
[  495.004689] Buffer I/O error on device sda1, logical block 31744130
[  495.004696] Buffer I/O error on device sda1, logical block 31744131
[  495.004703] Buffer I/O error on device sda1, logical block 31744132
[  495.004711] Buffer I/O error on device sda1, logical block 31744133
[  495.004718] Buffer I/O error on device sda1, logical block 31744134
[  495.004725] Buffer I/O error on device sda1, logical block 31744135
[  495.004761] ata1: EH complete
[  495.005015] sd 0:0:0:0: [sda] Write Protect is off
[  495.005022] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  496.407748] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  496.407757] ata1.00: BMDMA stat 0x25
[  496.407772] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  496.407775]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  496.407793] ata1.00: status: { DRDY ERR }
[  496.407798] ata1.00: error: { IDNF }
[  496.428562] ata1.00: configured for UDMA/100
[  496.428595] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  496.428605] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  496.428617] Descriptor sense data with sense descriptors (in hex):
[  496.428623]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  496.428660]         01 e4 61 a7 
[  496.428670] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  496.428682] end_request: I/O error, dev sda, sector 31744423
[  496.428695] Buffer I/O error on device sda1, logical block 31744360
[  496.428705] Buffer I/O error on device sda1, logical block 31744361
[  496.428748] ata1: EH complete
[  497.856890] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  497.856900] ata1.00: BMDMA stat 0x25
[  497.856915] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  497.856918]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  497.856926] ata1.00: status: { DRDY ERR }
[  497.856931] ata1.00: error: { IDNF }
[  497.880597] ata1.00: configured for UDMA/100
[  497.880630] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  497.880640] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  497.880652] Descriptor sense data with sense descriptors (in hex):
[  497.880658]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  497.880684]         01 e4 61 a7 
[  497.880694] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  497.880706] end_request: I/O error, dev sda, sector 31744423
[  497.880757] ata1: EH complete
[  497.881064] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  499.372397] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  499.372407] ata1.00: BMDMA stat 0x25
[  499.372421] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  499.372424]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  499.372432] ata1.00: status: { DRDY ERR }
[  499.372438] ata1.00: error: { IDNF }
[  499.396598] ata1.00: configured for UDMA/100
[  499.396630] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  499.396639] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  499.396652] Descriptor sense data with sense descriptors (in hex):
[  499.396658]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  499.396684]         01 e4 61 b7 
[  499.396694] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  499.396706] end_request: I/O error, dev sda, sector 31744439
[  499.396748] ata1: EH complete
[  499.396913] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  500.810470] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  500.810480] ata1.00: BMDMA stat 0x25
[  500.810494] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  500.810498]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  500.810506] ata1.00: status: { DRDY ERR }
[  500.810511] ata1.00: error: { IDNF }
[  500.832606] ata1.00: configured for UDMA/100
[  500.832637] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  500.832647] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  500.832659] Descriptor sense data with sense descriptors (in hex):
[  500.832665]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  500.832691]         01 e4 61 b7 
[  500.832701] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  500.832713] end_request: I/O error, dev sda, sector 31744439
[  500.832723] __ratelimit: 15 callbacks suppressed
[  500.832731] Buffer I/O error on device sda1, logical block 31744376
[  500.832768] ata1: EH complete
[  500.832992] sd 0:0:0:0: [sda] Write Protect is off
[  500.832999] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  502.248548] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  502.248557] ata1.00: BMDMA stat 0x25
[  502.248572] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  502.248575]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  502.248583] ata1.00: status: { DRDY ERR }
[  502.248588] ata1.00: error: { IDNF }
[  502.272561] ata1.00: configured for UDMA/100
[  502.272592] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  502.272602] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  502.272614] Descriptor sense data with sense descriptors (in hex):
[  502.272620]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  502.272646]         01 e4 61 af 
[  502.272656] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  502.272668] end_request: I/O error, dev sda, sector 31744431
[  502.272680] Buffer I/O error on device sda1, logical block 31744368
[  502.272689] Buffer I/O error on device sda1, logical block 31744369
[  502.272697] Buffer I/O error on device sda1, logical block 31744370
[  502.272705] Buffer I/O error on device sda1, logical block 31744371
[  502.272712] Buffer I/O error on device sda1, logical block 31744372
[  502.272720] Buffer I/O error on device sda1, logical block 31744373
[  502.272727] Buffer I/O error on device sda1, logical block 31744374
[  502.272734] Buffer I/O error on device sda1, logical block 31744375
[  502.272767] ata1: EH complete
[  503.719823] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  503.719833] ata1.00: BMDMA stat 0x25
[  503.719847] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  503.719850]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  503.719858] ata1.00: status: { DRDY ERR }
[  503.719863] ata1.00: error: { IDNF }
[  503.744614] ata1.00: configured for UDMA/100
[  503.744646] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  503.744656] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  503.744668] Descriptor sense data with sense descriptors (in hex):
[  503.744674]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  503.744700]         01 e4 61 b7 
[  503.744710] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  503.744722] end_request: I/O error, dev sda, sector 31744439
[  503.744735] Buffer I/O error on device sda1, logical block 31744376
[  503.744773] ata1: EH complete
[  503.744965] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  505.169548] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  505.169558] ata1.00: BMDMA stat 0x25
[  505.169572] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  505.169575]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  505.169583] ata1.00: status: { DRDY ERR }
[  505.169589] ata1.00: error: { IDNF }
[  505.192611] ata1.00: configured for UDMA/100
[  505.192641] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  505.192651] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  505.192664] Descriptor sense data with sense descriptors (in hex):
[  505.192670]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  505.192695]         01 e4 61 b7 
[  505.192706] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  505.192718] end_request: I/O error, dev sda, sector 31744439
[  505.192762] ata1: EH complete
[  506.640220] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  506.640230] ata1.00: BMDMA stat 0x25
[  506.640244] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  506.640248]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  506.640256] ata1.00: status: { DRDY ERR }
[  506.640261] ata1.00: error: { IDNF }
[  506.664612] ata1.00: configured for UDMA/100
[  506.664644] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  506.664653] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  506.664666] Descriptor sense data with sense descriptors (in hex):
[  506.664672]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  506.664698]         01 e4 61 b7 
[  506.664708] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  506.664720] end_request: I/O error, dev sda, sector 31744439
[  506.664763] ata1: EH complete
[  506.664974] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  508.111486] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  508.111495] ata1.00: BMDMA stat 0x25
[  508.111510] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  508.111513]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  508.111521] ata1.00: status: { DRDY ERR }
[  508.111527] ata1.00: error: { IDNF }
[  508.132611] ata1.00: configured for UDMA/100
[  508.132643] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  508.132652] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  508.132665] Descriptor sense data with sense descriptors (in hex):
[  508.132671]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  508.132697]         01 e4 61 af 
[  508.132707] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  508.132719] end_request: I/O error, dev sda, sector 31744431
[  508.132729] __ratelimit: 2 callbacks suppressed
[  508.132736] Buffer I/O error on device sda1, logical block 31744368
[  508.132747] Buffer I/O error on device sda1, logical block 31744369
[  508.132754] Buffer I/O error on device sda1, logical block 31744370
[  508.132761] Buffer I/O error on device sda1, logical block 31744371
[  508.132769] Buffer I/O error on device sda1, logical block 31744372
[  508.132776] Buffer I/O error on device sda1, logical block 31744373
[  508.132783] Buffer I/O error on device sda1, logical block 31744374
[  508.132791] Buffer I/O error on device sda1, logical block 31744375
[  508.132826] ata1: EH complete
[  508.133082] sd 0:0:0:0: [sda] Write Protect is off
[  508.133089] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  509.615927] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  509.615937] ata1.00: BMDMA stat 0x25
[  509.615951] ata1.00: cmd c8/00:08:77:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  509.615954]          res 51/10:08:77:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  509.615962] ata1.00: status: { DRDY ERR }
[  509.615977] ata1.00: error: { IDNF }
[  509.632546] ata1.00: configured for UDMA/100
[  509.632583] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  509.632594] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  509.632606] Descriptor sense data with sense descriptors (in hex):
[  509.632613]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  509.632638]         01 e4 61 77 
[  509.632649] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  509.632661] end_request: I/O error, dev sda, sector 31744375
[  509.632675] Buffer I/O error on device sda1, logical block 31744312
[  509.632685] Buffer I/O error on device sda1, logical block 31744313
[  509.632734] ata1: EH complete
[  511.087201] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  511.087211] ata1.00: BMDMA stat 0x25
[  511.087225] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  511.087229]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  511.087237] ata1.00: status: { DRDY ERR }
[  511.087242] ata1.00: error: { IDNF }
[  511.108511] ata1.00: configured for UDMA/100
[  511.108541] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  511.108551] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  511.108563] Descriptor sense data with sense descriptors (in hex):
[  511.108569]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  511.108595]         01 e4 61 a7 
[  511.108605] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  511.108617] end_request: I/O error, dev sda, sector 31744423
[  511.108666] ata1: EH complete
[  511.108846] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  512.514212] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  512.514222] ata1.00: BMDMA stat 0x25
[  512.514236] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  512.514239]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  512.514247] ata1.00: status: { DRDY ERR }
[  512.514253] ata1.00: error: { IDNF }
[  512.536656] ata1.00: configured for UDMA/100
[  512.536685] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  512.536695] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  512.536708] Descriptor sense data with sense descriptors (in hex):
[  512.536714]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  512.536740]         01 e4 61 b7 
[  512.536750] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  512.536762] end_request: I/O error, dev sda, sector 31744439
[  512.536802] ata1: EH complete
[  514.073936] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  514.073945] ata1.00: BMDMA stat 0x25
[  514.073960] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
[  514.073963]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  514.073971] ata1.00: status: { DRDY ERR }
[  514.073976] ata1.00: error: { IDNF }
[  514.096513] ata1.00: configured for UDMA/100
[  514.096538] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  514.096547] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  514.096560] Descriptor sense data with sense descriptors (in hex):
[  514.096566]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  514.096591]         01 e4 61 b7 
[  514.096602] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  514.096614] end_request: I/O error, dev sda, sector 31744439
[  514.096623] __ratelimit: 15 callbacks suppressed
[  514.096631] Buffer I/O error on device sda1, logical block 31744376
[  514.096659] ata1: EH complete
[  514.096951] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  514.126945] sd 0:0:0:0: [sda] Write Protect is off
[  514.126955] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  514.127639] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  514.129788] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  514.130130] sd 0:0:0:0: [sda] Write Protect is off
[  514.130137] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  514.130806] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
ubuntu@ubuntu:~$ sudo gedit /etc/fstab 0: [sda] Add. Sense: Recorded entity not found


** (gedit:5205): CRITICAL **: gedit_utils_str_middle_truncate: assertion `string != NULL' failed
ubuntu@ubuntu:~$ [  183.648556] end_request: I/O error, dev sda, sector 31744440
[  188.072629] sd 0:0:0:0: [sda] 156301488 512-byte hardware se
bash: [: missing `]'
ubuntu@ubuntu:~$ [  183.648561] Buffer I/O error on device sda2, logical block 0
bash: [: missing `]'
[  188.072648] sd 0:0:0:0: [sda] Write Protect is off
[  188.07ubuntu@ubuntu:~$ [  183.648576] ata1: EH complete
bash: [: missing `]'
2651] sd 0:0:0:0: [sda] Mode Sens
ubuntu@ubuntu:~$ [  183.678648] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
bash: syntax error near unexpected token `('
[  188.072683] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't sup
ubuntu@ubuntu:~$ [  183.678672] sd 0:0:0:0: [sda] Write Protect is off
bash: [: missing `]'
[  190.119441] ata1.00: exception Emask 0x0 SAct 0x0 
ubuntu@ubuntu:~$ [  183.678675] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  190.119444] ata1.00: BMDMA stat 0x25
[  190.119450] abash: [: missing `]'
ubuntu@ubuntu:~$ [  183.678709] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
> [  185.108286] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
> [  185.108289] ata1.00: BMDMA stat 0x25
> [  185.108295] ata1.00: cmd c8/00:01:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 512 in
> [  185.108296]          res 51/10:01:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
> [  185.108300] ata1.00: status: { DRDY ERR }
> [  185.108303] ata1.00: error: { IDNF }
> [  185.132507] ata1.00: configured for UDMA/100
> [  185.132513] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
> [  185.132517] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
> [  185.132523] Descriptor sense data with sense descriptors (in hex):
> [  185.132526]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
> [  185.132539]         01 e4 60 bf 
> [  185.132544] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
> [  185.132549] end_request: I/O error, dev sda, sector 31744191
> [  185.132553] Buffer I/O error on device sda1, logical block 31744128
> [  185.132562] ata1: EH complete
> [  186.579554] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
> [  186.579557] ata1.00: BMDMA stat 0x25
ta1.00: cmd c8/00:08:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  190.119452]          res 51/10:08:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  190.119455] ata1.00: status: { DRDY ERR }
[  190.119458] ata1.00: error: { IDNF }
[  190.140517] ata1.00: configured for UDMA/100
[  190.140524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  190.140528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  190.140534] Descriptor sense data with sense descriptors (in hex):
[  190.140536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  190.140549]         01 e4 60 bf 
[  190.140554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  190.140560] end_request: I/O error, dev sda, sector 31744191
[  190.140563] __ratelimit: 1 callbacks suppressed
[  190.140566] Buffer I/O error on device sda1, logical block 31744128
[  190.140570] Buffer I/O error on device sda1, logical block 31744129
[  190.140574] Buffer I/O error on device sda1, logical block 31744130
[  190.140577] Buffer I/O error on device sda1, logical block 31744131
[  190.140581] Buffer I/O error on device sda1, logical block 31744132
[  190.140584] Buffer I/O error on device s> [  186.579563] ata1.00: cmd c8/00:02:b8:61:e4/00:00:00:00:00/e1 tag 0 dma 1024 in
> [  186.579565]          res 51/10:02:b8:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
> [  186.579569] ata1.00: status: { DRDY ERR }
> [  186.579572] ata1.00: error: { IDNF }
> [  186.600477] ata1.00: configured for UDMA/100
> [  186.600483] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
> [  186.600487] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
> [  186.600492] Descriptor sense data with sense descriptors (in hex):
> [  186.600495]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
da1, logical block 31744133
[  190.140588] Buffer I/O error on device sda1, logical block 31744134
[  190.140592] Buffer I/O error on device sda1, logical block 31744135
[  190.140601] ata1: EH complete
[  190.140634] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  190.140654] sd 0:0:0:0: [sda] Write Protect is off
[  190.140657] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  190.140689] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  191.535390] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  191.535393] ata1.00: BMDMA stat 0x25
[  191.> [  186.600508]         01 e4 61 b8 
> [  186.600513] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
> [  186.600519] end_request: I/O error, dev sda, sector 31744440
> [  186.600522] Buffer I/O error on device sda2, logical block 0
> [  186.600533] ata1: EH complete
535399] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  191.535401]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  191.535405] ata1.00: status: { DRDY ERR }
[  191.535407] ata1.00: error: { IDNF }
[  191.556513]> [  186.600608] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
> [  188.050816] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
> [  188.050819] ata1.00: BMDMA stat 0x25
 ata1.00: configured for UDMA/100
[  191.556519] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  191.556524] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [desc> [  188.050826] ata1.00: cmd c8/00:07:c0:60:e4/00:00:00:00:00/e1 tag 0 dma 3584 in
> [  188.050827]          res 51/10:07:c0:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
> [  188.050831] ata1.00: status: { DRDY ERR }
> [  188.050834] ata1.00: error: { IDNF }
riptor]
[  191.556529] Descriptor sense data with sense descriptors (in hex):
[  191.556532]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  191.556545]         01 e4 61 a7 
[  191.556550] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  1> [  188.072463] ata1.00: configured for UDMA/100
91.556555] end_request: I/O error, dev sda, sect
> [  188.072470] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
> [  188.072474] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
> [  188.072480] Descriptor sense data with sense descriptors (in hex):
[  191.556559] Buffer I/O error on device sda1, logical block 31744360
[  191.556563] Buffer I/O error on device sda1, logical block 31744361
[  191.556576] ata1: EH complete
[  191.556609] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: > [  188.072483]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
> [  188.072495]         01 e4 60 c0 
(80.0 GB/74.5 GiB)
[  191.556629] sd 0:0:0:0: [sda] Write Protect is off
[  191.556632] sd 0:0:0:0: [sda] Mo> [  188.072500] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
> [  188.072506] end_request: I/O error, dev sda, sector 31744192
> [  188.072510] Buffer I/O error on device sda1, logical block 31744129
> [  188.072514] Buffer I/O error on device sda1, logical block 31744130
> [  188.072518] Buffer I/O error on device sda1, logical block 31744131
> [  188.072521] Buffer I/O error on device sda1, logical block 31744132
> [  188.072525] Buffer I/O error on device sda1, logical block 31744133
> [  188.072528] Buffer I/O error on device sda1, logical block 31744134
> [  188.072539] ata1: EH complete
de Sense: 00 3a 00 00
[  191.556664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  192.984528] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  192.984531] ata1.00: BMDMA stat 0x25
[  192.984537] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  192.984539]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  192.984543] ata1.00: status: { DRDY ERR }
[  192.984545] ata1.00: error: { IDNF }
[  193.008514] ata1.00: configured for UDMA/100
[  193.008521] sd 0:0:0:0: [sda] Result: hostb> [  188.072558] sd 0:0:0:0: [sda] Write Protect is off
> [  188.072561] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
> [  188.072594] sd 0:0:0:0: [sda] Write
> [  188.072629] sd 0:0:0:0: [sda] 156301488 512-byte hardware se
> [  188.072648] sd 0:0:0:0: [sda] Write Protect is off
yte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  193.008525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  193.008530] Descriptor sense data with sense descriptors (in hex):
[  193.008533]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 > [  188.072651] sd 0:0:0:0: [sda] Mode Sens
00 
[  193.008546]         01 e4 61 a7 
[  > [  188.072683] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't sup
bash: [: missing `]'
193.008551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
[  193.008557] end_reubuntu@ubuntu:~$ [  190.119441] ata1.00: exception Emask 0x0 SAct 0x0 
quest: I/O error, dev sda, sector 31744423
[  193.0085bash: [: missing `]'
ubuntu@ubuntu:~$ [  190.119444] ata1.00: BMDMA stat 0x25
bash: [: missing `]'
71] ata1: EH complete
[  193.008603] sd ubuntu@ubuntu:~$ [  190.119450] ata1.00: cmd c8/00:08:bf:60:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
bash: [: missing `]'
0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  193.0086ubuntu@ubuntu:~$ [  190.119452]          res 51/10:08:bf:60:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
bash: syntax error near unexpected token `('
23] sd 0:0:0:0: [sda] Write Protect is off
[  193.008626] sd 0:0:0:0: [sda] Mode Sense: 00 3a ubuntu@ubuntu:~$ [  190.119455] ata1.00: status: { DRDY ERR }
bash: [: missing `]'
00 00
[  193.008658] sd 0:0:0:0: [sda] Write ubuntu@ubuntu:~$ [  190.119458] ata1.00: error: { IDNF }
bash: [: missing `]'
cache: disabled, read cache: enabled, do
ubuntu@ubuntu:~$ [  190.140517] ata1.00: configured for UDMA/100
bash: [: missing `]'
[  194.466851] ata1.00: exception Emask 0x0 SAc
ubuntu@ubuntu:~$ [  190.140524] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
bash: [: missing `]'
[  194.466854] ata1.00: BMDMA stat 0x25
[  194.466860] ata1.00: cmd c8/00:01:b7:61:e4/00:00ubuntu@ubuntu:~$ [  190.140528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
bash: [: missing `]'
:00:00:00/e1 tag 0 dma 512 in
[  194.466862]          res 51/10:01:b7:61:e4/00:00:00ubuntu@ubuntu:~$ [  190.140534] Descriptor sense data with sense descriptors (in hex):
:00:00/e1 Emask 0x81 (invalid argument)
[  194.466866] ata1.00: statusbash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ [  190.140536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
bash: [: missing `]'
: { DRDY ERR }
[  194.466868] ata1.00: error: { IDNF }
[  194.488515] atubuntu@ubuntu:~$ [  190.140549]         01 e4 60 bf 
bash: [: missing `]'
a1.00: configured for UDMA/100
[  19ubuntu@ubuntu:~$ [  190.140554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
4.488521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_S
bash: [: missing `]'
ubuntu@ubuntu:~$ [  190.140560] end_request: I/O error, dev sda, sector 31744191
bash: [: missing `]'
[  194.488526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [c
ubuntu@ubuntu:~$ [  190.140563] __ratelimit: 1 callbacks suppressed
bash: [: missing `]'
[  194.488531] Descriptor sense data with sense de
ubuntu@ubuntu:~$ [  190.140566] Buffer I/O error on device sda1, logical block 31744128
bash: [: missing `]'
[  194.488534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00
ubuntu@ubuntu:~$ [  190.140570] Buffer I/O error on device sda1, logical block 31744129
bash: [: missing `]'
[  194.488547]         01 e4 61 b7 
[  194.488552] sd 0:0:0:0: [sda] Aubuntu@ubuntu:~$ [  190.140574] Buffer I/O error on device sda1, logical block 31744130
bash: [: missing `]'
dd. Sense: Recorded entity not found
[  194.488557] end_request: I/O erubuntu@ubuntu:~$ [  190.140577] Buffer I/O error on device sda1, logical block 31744131
bash: [: missing `]'
ror, dev sda, sector 31744439
[  194.488568] ata1: EH complete
[  194.4ubuntu@ubuntu:~$ [  190.140581] Buffer I/O error on device sda1, logical block 31744132
bash: [: missing `]'
88600] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/
ubuntu@ubuntu:~$ [  190.140584] Buffer I/O error on device sda1, logical block 31744133
bash: [: missing `]'
[  194.488621] sd 0:0:0:0: [sda] Write Protect is off
[  194.488624] subuntu@ubuntu:~$ [  190.140588] Buffer I/O error on device sda1, logical block 31744134
bash: [: missing `]'
d 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  194.488656] sd 0:0:0:0: [sdubuntu@ubuntu:~$ [  190.140592] Buffer I/O error on device sda1, logical block 31744135
bash: [: missing `]'
a] Write cache: disabled, read cache: enabled, doesn't support DPO or F
ubuntu@ubuntu:~$ [  190.140601] ata1: EH complete
bash: [: missing `]'
[  195.960239] ata1.00: exceptio
ubuntu@ubuntu:~$ [  190.140634] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
bash: syntax error near unexpected token `('
[  195.960242] ata1.00: BMDMA stat 0x25
[  195.960248] ata1.00: cmd c8/00:01:b7:61:e4/00ubuntu@ubuntu:~$ [  190.140654] sd 0:0:0:0: [sda] Write Protect is off
bash: [: missing `]'
:00:00:00:00/e1 tag 0 dma 512 in
[  195.960250]       ubuntu@ubuntu:~$ [  190.140657] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
   res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (in
bash: [: missing `]'
ubuntu@ubuntu:~$ [  190.140689] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
> [  191.535390] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
> [  191.535393] ata1.00: BMDMA stat 0x25
[  195.960253] ata1.00: status: { DRDY ERR }
[  195.960256] ata1.00: error: { IDNF }
[  195.984517] ata1.00: configured for UDMA/100
[  195.984523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SU> [  191.535399] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
> [  191.535401]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
> [  191.535405] ata1.00: status: { DRDY ERR }
GGEST_OK
[  195.984528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  195.984533] Descriptor sense data with sense descriptors (in hex):
[  195.984536]         72 0b 14 00 00 00 00 0c 00 0a 80 00> [  191.535407] ata1.00: error: { IDNF }
 00 00 00 00 
[  195.984549]         01 > [  191.556513] ata1.00: configured for UDMA/100
e4 61 b7 
[  195.984554] sd 0:0:0:0: [sda] Add. > [  191.556519] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
> [  191.556524] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
563] __ratelimit: 15 callbacks suppressed
[  195.984566] Buffer I/O e> [  191.556529] Descriptor sense data with sense descriptors (in hex):
> [  191.556532]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
> [  191.556545]         01 e4 61 a7 
> [  191.556550] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
> [  191.556555] end_request: I/O error, dev sda, sect
> [  191.556559] Buffer I/O error on device sda1, logical block 31744360
> [  191.556563] Buffer I/O error on device sda1, logical block 31744361
rror on device sda1, logical block 31744376
[  195.984576] ata1: EH complete
[  195.984608] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  195.984628] sd 0:0:0:0: [sda] Write Protect is off
[  195.984631] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  195.984664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  197.442565] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 a> [  191.556576] ata1: EH complete
> [  191.556609] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
> [  191.556629] sd 0:0:0:0: [sda] Write Protect is off
> [  191.556632] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
ction 0x0
[  197.442568] ata1.00: BMDMA stat 0x25
[  197.442574] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
[  197.442575]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
[  197.> [  191.556664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
442579] ata1.00: status: { DRDY ERR }
[  197.442582] ata1.00: error: { IDNF }
[  197.464517] ata1.00: cobash: [: missing `]'
ubuntu@ubuntu:~$ [  192.984528] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
nfigured for UDMA/100
[  197.464523] sd 0:0:0:0: [sda] Result: hostbyte=Dbash: [: missing `]'
ubuntu@ubuntu:~$ [  192.984531] ata1.00: BMDMA stat 0x25
ID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
bash: [: missing `]'
ubuntu@ubuntu:~$ [  192.984537] ata1.00: cmd c8/00:08:a7:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
bash: [: missing `]'
[  197.464527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descripto
ubuntu@ubuntu:~$ [  192.984539]          res 51/10:08:a7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
bash: syntax error near unexpected token `('
[  197.464533] Descriptor sense data with sense descriptors (in hex):
[  197.464536]         ubuntu@ubuntu:~$ [  192.984543] ata1.00: status: { DRDY ERR }
bash: [: missing `]'
72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 
ubuntu@ubuntu:~$ [  192.984545] ata1.00: error: { IDNF }
bash: [: missing `]'
[  197.464549]         01 e4 61 af 
[  ubuntu@ubuntu:~$ [  193.008514] ata1.00: configured for UDMA/100
bash: [: missing `]'
197.464554] sd 0:0:0:0: [sda] Add. Sense: Record
ubuntu@ubuntu:~$ [  193.008521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
bash: [: missing `]'
[  197.464559] end_request: I/O error, dev sda, sector 31744431
[  197.464563] Buffer I/O eubuntu@ubuntu:~$ [  193.008525] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
bash: [: missing `]'
rror on device sda1, logical block 31744368
[  197.464567] Buffer I/O error on devicubuntu@ubuntu:~$ [  193.008530] Descriptor sense data with sense descriptors (in hex):
e sda1, logical block 31744369
[  197.464571] Buffer I/O error onbash: syntax error near unexpected token `(' 
deviubuntu@ubuntu:~$ [  193.008533]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
bash: [: missing `]'
ce sda1, logical block 31744370
[  197.464574] Buffer I/O error on devicubuntu@ubuntu:~$ [  193.008546]         01 e4 61 a7 
bash: [: missing `]'
e sda1, logical block 31744371
[  19ubuntu@ubuntu:~$ [  193.008551] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
7.464578] Buffer I/O error on device sda1, logical block 31744372
[  19bash: [: missing `]'
ubuntu@ubuntu:~$ [  193.008557] end_request: I/O error, dev sda, sector 31744423
7.464582] Buffer I/O error on device sda1, logical block 3174437
bash: [: missing `]'
ubuntu@ubuntu:~$ [  193.008571] ata1: EH complete
bash: [: missing `]'
[  197.464585] Buffer I/O error 
ubuntu@ubuntu:~$ [  193.008603] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  197.464589] Buffer I/O error on device sda1, logical block 31744375
[  197.464598] atbash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ [  193.008623] sd 0:0:0:0: [sda] Write Protect is off
bash: [: missing `]'
a1: EH complete
[  197.464631] sd 0:0:0:0: [sda] 15630ubuntu@ubuntu:~$ [  193.008626] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
bash: [: missing `]'
1488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  197ubuntu@ubuntu:~$ [  193.008658] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, do
.464651] sd 0:0:0:0: [sda] Write Protect is off
[  197.464654] sd 0:0:0:0: [sda]bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.466851] ata1.00: exception Emask 0x0 SAc
 Mode Sense: 00 3a 00 00
[  197.464686] sd 0:0:0bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.466854] ata1.00: BMDMA stat 0x25
bash: [: missing `]'
:0: [sda] Write cache: disabled, read ca
ubuntu@ubuntu:~$ [  194.466860] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
bash: [: missing `]'
[  198.913828] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  198.ubuntu@ubuntu:~$ [  194.466862]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
bash: syntax error near unexpected token `('
913831] ata1.00: BMDMA stat 0x25
ubuntu@ubuntu:~$ [  194.466866] ata1.00: status: { DRDY ERR }
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.466868] ata1.00: error: { IDNF }
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488515] ata1.00: configured for UDMA/100
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488521] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_S
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488526] sd 0:0:0:0: [sda] Sense Key : Aborted Command [c
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488531] Descriptor sense data with sense de
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488534]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488547]         01 e4 61 b7 
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488552] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488557] end_request: I/O error, dev sda, sector 31744439
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488568] ata1: EH complete
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488600] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ [  194.488621] sd 0:0:0:0: [sda] Write Protect is off
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488624] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
bash: [: missing `]'
ubuntu@ubuntu:~$ [  194.488656] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or F
> [  195.960239] ata1.00: exceptio
> [  195.960242] ata1.00: BMDMA stat 0x25
> [  195.960248] ata1.00: cmd c8/00:01:b7:61:e4/00:00:00:00:00/e1 tag 0 dma 512 in
> [  195.960250]          res 51/10:01:b7:61:e4/00:00:00:00:00/e1 Emask 0x81 (in
> [  195.960253] ata1.00: status: { DRDY ERR }
> [  195.960256] ata1.00: error: { IDNF }
> [  195.984517] ata1.00: configured for UDMA/100
> [  195.984523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
> [  195.984528] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
> [  195.984533] Descriptor sense data with sense descriptors (in hex):
> [  195.984536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
> [  195.984549]         01 e4 61 b7 
> [  195.984554] sd 0:0:0:0: [sda] Add. Sense: Recorded entity not found
> [  195.984559] end_request: I/O error, dev sda, sector 31744439
> [  195.984563] __ratelimit: 15 callbacks suppressed
> [  195.984566] Buffer I/O error on device sda1, logical block 31744376
> [  195.984576] ata1: EH complete
> [  195.984608] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
> [  195.984628] sd 0:0:0:0: [sda] Write Protect is off
> [  195.984631] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
> [  195.984664] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.442565] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.442568] ata1.00: BMDMA stat 0x25
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.442574] ata1.00: cmd c8/00:08:af:61:e4/00:00:00:00:00/e1 tag 0 dma 4096 in
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.442575]          res 51/10:08:af:61:e4/00:00:00:00:00/e1 Emask 0x81 (invalid argument)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ [  197.442579] ata1.00: status: { DRDY ERR }
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.442582] ata1.00: error: { IDNF }
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464517] ata1.00: configured for UDMA/100
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464523] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464527] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descripto
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464533] Descriptor sense data with sense descriptors (in hex):
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ [  197.464536]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464549]         01 e4 61 af 
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464554] sd 0:0:0:0: [sda] Add. Sense: Record
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464559] end_request: I/O error, dev sda, sector 31744431
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464563] Buffer I/O error on device sda1, logical block 31744368
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464567] Buffer I/O error on device sda1, logical block 31744369
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464571] Buffer I/O error on device sda1, logical block 31744370
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464574] Buffer I/O error on device sda1, logical block 31744371
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464578] Buffer I/O error on device sda1, logical block 31744372
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464582] Buffer I/O error on device sda1, logical block 3174437
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464585] Buffer I/O error 
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464589] Buffer I/O error on device sda1, logical block 31744375
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464598] ata1: EH complete
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464631] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ [  197.464651] sd 0:0:0:0: [sda] Write Protect is off
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464654] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
bash: [: missing `]'
ubuntu@ubuntu:~$ [  197.464686] sd 0:0:0:0: [sda] Write cache: disabled, read ca
bash: [: missing `]'
ubuntu@ubuntu:~$ [  198.913828] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
bash: [: missing `]'
ubuntu@ubuntu:~$ [  198.913831] ata1.00: BMDMA stat 0x25
bash: [: missing `]'
ubuntu@ubuntu:~$ 

```

---

