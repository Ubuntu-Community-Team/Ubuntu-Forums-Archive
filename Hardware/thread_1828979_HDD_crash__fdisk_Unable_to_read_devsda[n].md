---
title: "HDD crash  fdisk: Unable to read /dev/sda[n]"
date: 2011-08-19
forum: Hardware
---

### Post by Jive Turkey on 2011-08-19
Today after booting my netbook I got an error just after the GRUB screen to the effect that my /boot partition was corrupted.  Booting then failed and restarting the computer now doesn't even get to the GRUB.  I attempted to boot ubuntu usb keys for 11.04(fail), 10.10(fail),10.04-3(fail), and ultimately got 9.04 to work. It takes about half an hour to boot with a steady stream of {ERR DRDY} messages (but not if I remove the HDD, its pretty quick then).  Once loaded I can access my old / /home /swap and /windows partitions just fine.  /boot appears to be gone.  Ive been googling around to find a fix but nothing seems to really touch the damaged partitions.  Also gparted on the bootable usb wont pick up the HDD at all.  fdisk and fsck also seem to hate me.

here's the output of "dmesg|grep sda":```

[ 5751.065626] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5751.065643] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 5751.065717] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 5751.065737] end_request: I/O error, dev sda, sector 63
[ 5751.065754] Buffer I/O error on device sda1, logical block 0
[ 5751.065783] Buffer I/O error on device sda1, logical block 1
[ 5751.065800] Buffer I/O error on device sda1, logical block 2
[ 5751.065816] Buffer I/O error on device sda1, logical block 3
[ 5751.066010] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5751.066652] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 5751.078746] sd 2:0:0:0: [sda] Write Protect is off
[ 5751.078765] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5751.101862] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5769.297196] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5769.297213] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 5769.297287] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 5769.297307] end_request: I/O error, dev sda, sector 63
[ 5769.297324] Buffer I/O error on device sda1, logical block 0
[ 5769.312755] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 5769.324632] sd 2:0:0:0: [sda] Write Protect is off
[ 5769.324648] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5769.346806] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5769.357912] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 5769.358043] sd 2:0:0:0: [sda] Write Protect is off
[ 5769.358059] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5769.370898] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5937.441070] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5937.441082] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 5937.441126] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 5937.441136] end_request: I/O error, dev sda, sector 63
[ 5937.441146] Buffer I/O error on device sda1, logical block 0
[ 5937.441163] Buffer I/O error on device sda1, logical block 1
[ 5937.441172] Buffer I/O error on device sda1, logical block 2
[ 5937.441180] Buffer I/O error on device sda1, logical block 3
[ 5956.056815] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5956.056827] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 5956.056883] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 5956.056898] end_request: I/O error, dev sda, sector 63
[ 5956.056911] Buffer I/O error on device sda1, logical block 0
[ 5956.057072] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 5974.753704] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5974.753720] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 5974.753795] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 5974.753815] end_request: I/O error, dev sda, sector 63
[ 5974.753832] Buffer I/O error on device sda1, logical block 0
[ 5974.755444] sd 2:0:0:0: [sda] Write Protect is off
[ 5974.755463] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5993.613119] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5993.613136] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 5993.613211] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 5993.613231] end_request: I/O error, dev sda, sector 63
[ 5993.613248] Buffer I/O error on device sda1, logical block 0
[ 5993.613476] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5993.615141] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6012.209716] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6012.209732] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6012.209807] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6012.209827] end_request: I/O error, dev sda, sector 63
[ 6012.209844] Buffer I/O error on device sda1, logical block 0
[ 6012.210153] sd 2:0:0:0: [sda] Write Protect is off
[ 6012.210165] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6012.210807] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6031.249622] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6031.249638] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6031.249713] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6031.249733] end_request: I/O error, dev sda, sector 63
[ 6031.249750] Buffer I/O error on device sda1, logical block 0
[ 6031.250046] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6031.253601] sd 2:0:0:0: [sda] Write Protect is off
[ 6031.253621] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6050.424883] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6050.424900] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6050.424975] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6050.424994] end_request: I/O error, dev sda, sector 63
[ 6050.425023] Buffer I/O error on device sda1, logical block 0
[ 6050.425396] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6068.741747] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6068.741763] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6068.741838] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6068.741858] end_request: I/O error, dev sda, sector 63
[ 6068.741875] Buffer I/O error on device sda1, logical block 0
[ 6068.743333] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6087.338349] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6087.338365] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6087.338440] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6087.338460] end_request: I/O error, dev sda, sector 63
[ 6087.338477] Buffer I/O error on device sda1, logical block 0
[ 6087.338798] sd 2:0:0:0: [sda] Write Protect is off
[ 6087.338810] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6106.193733] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6106.193749] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6106.193824] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6106.193844] end_request: I/O error, dev sda, sector 63
[ 6106.193861] Buffer I/O error on device sda1, logical block 0
[ 6106.215234] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6124.557723] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6124.557739] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6124.557814] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6124.557834] end_request: I/O error, dev sda, sector 63
[ 6124.557852] Buffer I/O error on device sda1, logical block 0
[ 6124.558215] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6124.558316] sd 2:0:0:0: [sda] Write Protect is off
[ 6124.558328] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6124.558477] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6124.558682] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6124.558772] sd 2:0:0:0: [sda] Write Protect is off
[ 6124.558784] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6124.558933] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6143.021036] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6143.021052] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6143.021127] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6143.021146] end_request: I/O error, dev sda, sector 63
[ 6143.021162] Buffer I/O error on device sda1, logical block 0
[ 6161.973637] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6161.973653] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6161.973728] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6161.973748] end_request: I/O error, dev sda, sector 71
[ 6161.973766] Buffer I/O error on device sda1, logical block 1
[ 6161.974111] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6161.999485] sd 2:0:0:0: [sda] Write Protect is off
[ 6161.999503] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6180.513111] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6180.513128] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6180.513202] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6180.513223] end_request: I/O error, dev sda, sector 71
[ 6180.513240] Buffer I/O error on device sda1, logical block 1
[ 6199.453667] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6199.453680] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6199.453739] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6199.453754] end_request: I/O error, dev sda, sector 71
[ 6199.453768] Buffer I/O error on device sda1, logical block 1
[ 6199.453908] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6217.973196] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6217.973212] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6217.973287] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6217.973307] end_request: I/O error, dev sda, sector 71
[ 6217.973324] Buffer I/O error on device sda1, logical block 1
[ 6217.973553] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6217.973869] sd 2:0:0:0: [sda] Write Protect is off
[ 6217.973880] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6217.990060] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6236.217828] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6236.217844] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6236.217919] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6236.217939] end_request: I/O error, dev sda, sector 71
[ 6236.217957] Buffer I/O error on device sda1, logical block 1
[ 6236.218683] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6254.588734] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6254.588746] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6254.588990] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6254.589005] end_request: I/O error, dev sda, sector 71
[ 6254.589019] Buffer I/O error on device sda1, logical block 1
[ 6254.589582] sd 2:0:0:0: [sda] Write Protect is off
[ 6254.589593] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6254.602829] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6273.672933] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6273.672949] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6273.673024] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6273.673044] end_request: I/O error, dev sda, sector 71
[ 6273.673062] Buffer I/O error on device sda1, logical block 1
[ 6273.673426] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6292.593384] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6292.593400] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6292.593475] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6292.593495] end_request: I/O error, dev sda, sector 71
[ 6292.593512] Buffer I/O error on device sda1, logical block 1
[ 6292.593712] sd 2:0:0:0: [sda] Write Protect is off
[ 6292.593727] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6310.913318] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6310.913334] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6310.913409] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6310.913429] end_request: I/O error, dev sda, sector 63
[ 6310.913446] Buffer I/O error on device sda1, logical block 0
[ 6310.914085] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6330.337223] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6330.337239] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6330.337314] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6330.337334] end_request: I/O error, dev sda, sector 63
[ 6330.337351] Buffer I/O error on device sda1, logical block 0
[ 6330.337723] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6349.345009] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6349.345025] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6349.345100] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6349.345120] end_request: I/O error, dev sda, sector 63
[ 6349.345137] Buffer I/O error on device sda1, logical block 0
[ 6349.345315] sd 2:0:0:0: [sda] Write Protect is off
[ 6349.345330] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6349.359812] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6367.945726] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6367.945742] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6367.945818] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6367.945838] end_request: I/O error, dev sda, sector 63
[ 6367.945855] Buffer I/O error on device sda1, logical block 0
[ 6386.121074] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6386.121086] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6386.121142] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6386.121157] end_request: I/O error, dev sda, sector 63
[ 6386.121170] Buffer I/O error on device sda1, logical block 0
[ 6386.121486] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6404.422012] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6404.422028] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6404.422102] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6404.422122] end_request: I/O error, dev sda, sector 63
[ 6404.422140] Buffer I/O error on device sda1, logical block 0
[ 6404.422518] sd 2:0:0:0: [sda] Write Protect is off
[ 6404.422530] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6422.449043] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6422.449059] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6422.449134] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6422.449154] end_request: I/O error, dev sda, sector 63
[ 6422.449171] Buffer I/O error on device sda1, logical block 0
[ 6441.033701] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6441.033717] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6441.033792] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6441.033812] end_request: I/O error, dev sda, sector 63
[ 6441.033828] Buffer I/O error on device sda1, logical block 0
[ 6441.038666] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6441.038939] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6441.039063] sd 2:0:0:0: [sda] Write Protect is off
[ 6441.039080] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6441.039279] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6459.382645] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6459.382661] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6459.382736] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6459.382756] end_request: I/O error, dev sda, sector 63
[ 6459.382773] Buffer I/O error on device sda1, logical block 0
[ 6459.382797] Buffer I/O error on device sda1, logical block 1
[ 6459.382810] Buffer I/O error on device sda1, logical block 2
[ 6459.382822] Buffer I/O error on device sda1, logical block 3
[ 6477.821838] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6477.821855] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6477.821930] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6477.821950] end_request: I/O error, dev sda, sector 63
[ 6477.821966] Buffer I/O error on device sda1, logical block 0
[ 6477.824763] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6477.824934] sd 2:0:0:0: [sda] Write Protect is off
[ 6477.824951] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6477.825166] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6477.825377] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6477.825493] sd 2:0:0:0: [sda] Write Protect is off
[ 6477.825508] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6477.825705] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6496.169804] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6496.169820] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6496.169895] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6496.169915] end_request: I/O error, dev sda, sector 63
[ 6496.169932] Buffer I/O error on device sda1, logical block 0
[ 6496.169957] Buffer I/O error on device sda1, logical block 1
[ 6496.169969] Buffer I/O error on device sda1, logical block 2
[ 6496.169981] Buffer I/O error on device sda1, logical block 3
[ 6514.781508] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6514.781525] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6514.781600] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6514.781620] end_request: I/O error, dev sda, sector 63
[ 6514.781636] Buffer I/O error on device sda1, logical block 0
[ 6514.782575] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6514.782725] sd 2:0:0:0: [sda] Write Protect is off
[ 6514.782740] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6514.782975] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6514.783186] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6514.783300] sd 2:0:0:0: [sda] Write Protect is off
[ 6514.783312] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6514.783455] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6690.941741] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6690.941757] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6690.941832] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6690.941852] end_request: I/O error, dev sda, sector 63
[ 6690.941869] Buffer I/O error on device sda1, logical block 0
[ 6690.941894] Buffer I/O error on device sda1, logical block 1
[ 6690.941906] Buffer I/O error on device sda1, logical block 2
[ 6690.941917] Buffer I/O error on device sda1, logical block 3
[ 6709.529408] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6709.529424] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6709.529499] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6709.529519] end_request: I/O error, dev sda, sector 63
[ 6709.529536] Buffer I/O error on device sda1, logical block 0
[ 6709.532878] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6709.533083] sd 2:0:0:0: [sda] Write Protect is off
[ 6709.533100] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6709.533305] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6709.533519] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 6709.533639] sd 2:0:0:0: [sda] Write Protect is off
[ 6709.533655] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6709.533855] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```
I've backed up the important stuff, and this is a pretty good excuse to finally get an SSD.  The only thing I can think of but haven't tried is to boot a windows usb install drive and run fixmbr.

Any suggestions to recover this drive would be greatly appreciated.

---

### Post by dandnsmith on 2011-08-20
With your comments, and a very quick scan of that log, I'd assume that there is a big problem at the start of the disk.
I see you've saved the important stuff, so would think about a new HDD (I'm not ready to accept SSD as a good long-term thing yet).
With the lack of enthusiam from gperted and fdisk, I'd remove the disk, and consider consider looking at it later via a USB converter interface to see if it can be got working - but don't waste time with fixmbr, as that would only ensure the loss of multiple booting (if it works at all).

Just my personal thoughts,

---

### Post by Jive Turkey on 2011-08-24
Using "bootrec /fixmbr" from the windows recovery command line got it to boot windows 7, and subsequent runs of chkdisk in windows revealed no errors (lol).  It's a Western Digital drive, so I got some of thier diagnostic utilities.  They were able to confirm a major problem with the disk and I was eventually able to image the partition with clonezilla (twice, once with partclone, and once with plain old dd).  My new SSD came today and I'm now trying to restore the windows partition (ubuntu is so easy to reinstall and restore I didn't image it, I only backed up some files).

While in windows I also used the "free" download of Acronis true image from western digital to make some backup images.  I attempted to reimage from those first, however acronis refuses to work without a western digital drive attached <gives finger in general direction of acronis and western digital corp HQ's with each hand>.  The bootable USB media created by acronis shows a dialog with a hyperlink to go buy the "full-version," but they didn't put a browser on the live distro to open it.  I guess if I really need to try using those acronis images I could use a usb dongle to attach the WD drive to the netbook but I don't have one yet.  There's no telling if it will refuse to write to the Intel brand ssd.

---

