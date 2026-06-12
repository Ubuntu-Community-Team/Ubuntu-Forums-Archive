---
title: "Troubles with external drive, dmesg Logs included"
date: 2020-03-16
forum: Hardware
---

### Post by askar-andersson on 2020-03-16
Hello there!

I am having some problems with my external drive connected to Ubuntu Server. After a while this shows up in dmesg. Not sure what is going on? Somehow it seems to switch from sdb to sbc?

```
[  813.851995] perf: interrupt took too long (2507 > 2500), lowering kernel.perf_event_max_sample_rate to 79750

[  818.269073] usb 2-3: USB disconnect, device number 2

[  818.270573] blk_update_request: I/O error, dev sdb, sector 0 op 0x1:(WRITE) flags 0x800 phys_seg 0 prio class 0

[  818.278549] sd 0:0:0:0: [sdb] Synchronizing SCSI cache

[  818.279284] sd 0:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK

[  818.577101] usb 2-3: new SuperSpeed Gen 1 USB device number 3 using xhci_hcd

[  818.597910] usb 2-3: New USB device found, idVendor=0bc2, idProduct=231a, bcdDevice= 7.10

[  818.597912] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3

[  818.597913] usb 2-3: Product: Expansion

[  818.597914] usb 2-3: Manufacturer: Seagate

[  818.597915] usb 2-3: SerialNumber: NAAECZTW

[  818.599025] usb 2-3: UAS is blacklisted for this device, using usb-storage instead

[  818.599027] usb-storage 2-3:1.0: USB Mass Storage device detected

[  818.600130] usb-storage 2-3:1.0: Quirks match for vid 0bc2 pid 231a: 800000

[  818.600187] scsi host4: usb-storage 2-3:1.0

[  819.629353] scsi 4:0:0:0: Direct-Access     Seagate  Expansion        0710 PQ: 0 ANSI: 6

[  819.634647] sd 4:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).

[  819.634739] sd 4:0:0:0: Attached scsi generic sg1 type 0

[  819.634765] sd 4:0:0:0: [sdc] 7814037167 512-byte logical blocks: (4.00 TB/3.64 TiB)

[  819.634767] sd 4:0:0:0: [sdc] 4096-byte physical blocks

[  819.634979] sd 4:0:0:0: [sdc] Write Protect is off

[  819.634980] sd 4:0:0:0: [sdc] Mode Sense: 47 00 00 08

[  819.635918] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[  819.929055]  sdc: sdc1

[  819.932660] udevd[383]: inotify_add_watch(6, /dev/sdc, 10) failed: No such file or directory

[  819.933078] udevd[426]: inotify_add_watch(6, /dev/sdc, 10) failed: No such file or directory

[  819.933478] udevd[325]: inotify_add_watch(6, /dev/sdc, 10) failed: No such file or directory

[  819.933586] udevd[426]: inotify_add_watch(6, /dev/sdc1, 10) failed: No such file or directory

[  819.934081] udevd[383]: inotify_add_watch(6, /dev/sdc1, 10) failed: No such file or directory

[  819.934686] sd 4:0:0:0: [sdc] Attached SCSI disk

[  819.934744] udevd[325]: inotify_add_watch(6, /dev/sdc1, 10) failed: No such file or directory
```

---

### Post by ajgreeny on 2020-03-16
Has the disk worked properly in the past or is it either new or the first time attached to your ubuntu system?

I assume it is a 4TB disk from what the dmesg says; to what filesystem is it formatted, and is it a single partition?
It is better to create more than one partition on a large disk of that size.

---

### Post by askar-andersson on 2020-03-18
> **ajgreeny said:**
> Has the disk worked properly in the past or is it either new or the first time attached to your ubuntu system?

I assume it is a 4TB disk from what the dmesg says; to what filesystem is it formatted, and is it a single partition?
It is better to create more than one partition on a large disk of that size.

It is ext4 and 4 tb yes and one partition. It used to work 

It looks to me like it disconnects? This is the latest from dmesg:

```
[34132.756059] usb 2-3: USB disconnect, device number 2[34132.757549] blk_update_request: I/O error, dev sdb, sector 0 op 0x1:(WRITE) flags 0x800 phys_seg 0 prio class 0
[34132.879695] sd 0:0:0:0: [sdb] Synchronizing SCSI cache
[34132.879723] sd 0:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[34133.168339] usb 2-3: new SuperSpeed Gen 1 USB device number 3 using xhci_hcd
[34133.189379] usb 2-3: New USB device found, idVendor=0bc2, idProduct=231a, bcdDevice= 7.10
[34133.189383] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[34133.189386] usb 2-3: Product: Expansion
[34133.189389] usb 2-3: Manufacturer: Seagate
[34133.189391] usb 2-3: SerialNumber: NAAECZTW
[34133.191499] usb 2-3: UAS is blacklisted for this device, using usb-storage instead
[34133.191505] usb-storage 2-3:1.0: USB Mass Storage device detected
[34133.191938] usb-storage 2-3:1.0: Quirks match for vid 0bc2 pid 231a: 800000
[34133.192343] scsi host4: usb-storage 2-3:1.0
[34134.224947] scsi 4:0:0:0: Direct-Access     Seagate  Expansion        0710 PQ: 0 ANSI: 6
[34134.227675] sd 4:0:0:0: Attached scsi generic sg1 type 0
[34134.231191] sd 4:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[34134.231308] sd 4:0:0:0: [sdc] 7814037167 512-byte logical blocks: (4.00 TB/3.64 TiB)
[34134.231309] sd 4:0:0:0: [sdc] 4096-byte physical blocks
[34134.231573] sd 4:0:0:0: [sdc] Write Protect is off
[34134.231575] sd 4:0:0:0: [sdc] Mode Sense: 47 00 00 08
[34134.231795] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[34134.313477]  sdc: sdc1
[34134.315042] sd 4:0:0:0: [sdc] Attached SCSI disk
[34134.319141] udevd[811]: inotify_add_watch(6, /dev/sdc, 10) failed: No such file or directory
[34134.320288] udevd[5939]: inotify_add_watch(6, /dev/sdc, 10) failed: No such file or directory
[34134.321111] udevd[811]: inotify_add_watch(6, /dev/sdc1, 10) failed: No such file or directory
[34134.321906] udevd[1002]: inotify_add_watch(6, /dev/sdc, 10) failed: No such file or directory
[34134.323708] udevd[5939]: inotify_add_watch(6, /dev/sdc1, 10) failed: No such file or directory
[34134.324694] udevd[1002]: inotify_add_watch(6, /dev/sdc1, 10) failed: No such file or directory
[36883.585028] EXT4-fs warning (device sdb1): htree_dirblock_to_tree:997: inode #8388609: lblock 0: comm Thread Pool Wor: error -5 reading directory block
[36896.435628] EXT4-fs warning (device sdb1): htree_dirblock_to_tree:997: inode #8388609: lblock 0: comm mono: error -5 reading directory block
[36897.192539] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm Thread Pool Wor: reading directory lblock 0
[36950.800738] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36950.800750] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36950.800760] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36950.800764] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36950.800811] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36950.800815] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36950.800821] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36950.800825] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36950.800831] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36950.800835] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36967.312135] EXT4-fs error: 78 callbacks suppressed
[36967.312140] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36967.312168] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36967.312200] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36967.312217] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36968.157497] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36968.157542] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36968.157579] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[36968.157597] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36969.404673] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[36969.404726] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37108.805278] EXT4-fs error: 46 callbacks suppressed
[37108.805284] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[37108.805314] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37108.805343] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37108.805359] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[37108.805397] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37108.805414] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37468.799422] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[37468.799453] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37468.799483] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37468.799499] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[37468.799539] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37468.799555] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37501.538629] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37539.163238] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37539.163260] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37539.166224] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37539.167377] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37738.867553] EXT4-fs warning (device sdb1): htree_dirblock_to_tree:997: inode #8388609: lblock 0: comm jellyfin: error -5 reading directory block
[37738.867555] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37802.117508] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37802.117519] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37802.119793] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37802.120233] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37819.535159] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.535174] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.535232] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.535468] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.740419] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.740445] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.740511] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.740766] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.756837] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37819.756868] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37824.227923] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37824.227949] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37824.228282] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37824.229317] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37828.790931] EXT4-fs error: 66 callbacks suppressed
[37828.790936] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[37828.790968] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37828.790998] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37828.791015] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360962: comm transmission-da: reading directory lblock 0
[37828.791053] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37828.791070] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #56360961: comm transmission-da: reading directory lblock 0
[37832.168645] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37832.168671] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37832.168737] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37832.169050] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37832.890620] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.890647] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.895150] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.896013] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.905157] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.905182] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.905644] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.908138] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.915583] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37832.915637] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37838.693219] EXT4-fs warning: 38 callbacks suppressed
[37838.693222] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37838.693233] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37838.693297] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37838.693604] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37839.627501] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37839.627520] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37839.627605] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37839.628059] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37839.629047] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37839.629056] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37842.346184] EXT4-fs error: 24 callbacks suppressed
[37842.346187] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37842.346200] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37842.346229] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37842.346332] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37842.347016] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37842.347046] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37842.347075] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37842.347164] EXT4-fs error (device sdb1): __ext4_find_entry:1530: inode #8388609: comm jellyfin: reading directory lblock 0
[37843.696467] EXT4-fs warning: 342 callbacks suppressed
[37843.696471] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.696486] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.696523] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.696710] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.697134] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.697146] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.697179] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.697314] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.698212] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block
[37843.698226] EXT4-fs warning (device sdb1): dx_probe:761: inode #52428801: lblock 0: comm jellyfin: error -5 reading directory block



```

---

