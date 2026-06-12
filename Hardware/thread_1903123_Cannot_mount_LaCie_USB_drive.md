---
title: "Cannot mount LaCie USB drive"
date: 2012-01-01
forum: Hardware
---

### Post by perevera on 2012-01-01
I have this USB drive which is not working anymore, maybe after being disconnected without unmounting.

I copy hereafter the messages that syslog shows when I connect the drive:

[I]Jan  1 23:26:54 perevera-laptop kernel: [ 6879.248058] usb 2-1: new high speed USB device number 9 using ehci_hcd
Jan  1 23:26:54 perevera-laptop kernel: [ 6879.383495] scsi12 : usb-storage 2-1:1.0
Jan  1 23:26:54 perevera-laptop mtp-probe: checking bus 2, device 9: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1"
Jan  1 23:26:54 perevera-laptop mtp-probe: bus: 2, device: 9 was not an MTP device
Jan  1 23:26:55 perevera-laptop kernel: [ 6880.385534] scsi 12:0:0:0: Direct-Access     SAMSUNG  HM120JC          0000 PQ: 0 ANSI: 0
Jan  1 23:26:55 perevera-laptop kernel: [ 6880.385572] scsi: killing requests for dead queue
Jan  1 23:26:55 perevera-laptop kernel: [ 6880.404121] scsi: killing requests for dead queue
Jan  1 23:26:55 perevera-laptop kernel: [ 6880.420138] scsi: killing requests for dead queue
Jan  1 23:26:55 perevera-laptop kernel: [ 6880.440117] scsi: killing requests for dead queue
Jan  1 23:26:55 perevera-laptop kernel: [ 6880.456113] scsi: killing requests for dead queue
Jan  1 23:26:55 perevera-laptop kernel: [ 6880.468099] scsi: killing requests for dead queue
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.480114] scsi: killing requests for dead queue
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.492091] scsi: killing requests for dead queue
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.504241] sd 12:0:0:0: Attached scsi generic sg2 type 0
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.507017] sd 12:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.507888] sd 12:0:0:0: [sdb] Write Protect is off
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.507892] sd 12:0:0:0: [sdb] Mode Sense: 27 00 00 00
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.512911] sd 12:0:0:0: [sdb] No Caching mode page present
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.512915] sd 12:0:0:0: [sdb] Assuming drive cache: write through
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.515644] sd 12:0:0:0: [sdb] No Caching mode page present
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.515648] sd 12:0:0:0: [sdb] Assuming drive cache: write through
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.623276]  sdb: sdb1 sdb2 < sdb5 >
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.637392] sd 12:0:0:0: [sdb] No Caching mode page present
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.637397] sd 12:0:0:0: [sdb] Assuming drive cache: write through
Jan  1 23:26:56 perevera-laptop kernel: [ 6880.637400] sd 12:0:0:0: [sdb] Attached SCSI disk
Jan  1 23:27:27 perevera-laptop kernel: [ 6911.952058] usb 2-1: reset high speed USB device number 9 using ehci_hcd
(...)
[ 7072.907644] sd 12:0:0:0: [sdb] Unhandled error code
[ 7072.907648] sd 12:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 7072.907652] sd 12:0:0:0: [sdb] CDB: Read(10): 28 00 0a 24 1b 56 00 00 08 00
[ 7072.907659] end_request: I/O error, dev sdb, sector 170138454
[ 7072.907664] Buffer I/O error on device sdb5, logical block 6291456
[ 7072.907669] Buffer I/O error on device sdb5, logical block 6291457
[ 7072.907671] Buffer I/O error on device sdb5, logical block 6291458
[ 7072.907673] Buffer I/O error on device sdb5, logical block 6291459
[ 7072.907675] Buffer I/O error on device sdb5, logical block 6291460
[ 7072.907677] Buffer I/O error on device sdb5, logical block 6291461
[ 7072.907680] Buffer I/O error on device sdb5, logical block 6291462
[ 7072.907682] Buffer I/O error on device sdb5, logical block 6291463
[ 7080.944062] usb 2-1: reset high speed USB device number 9 using ehci_hcd
[ 7091.188030] usb 2-1: reset high speed USB device number 9 using ehci_hcd
[ 7107.432056] usb 2-1: reset high speed USB device number 9 using ehci_hcd
[ 7107.680033] usb 2-1: reset high speed USB device number 9 using ehci_hcd
[ 7117.924056] usb 2-1: reset high speed USB device number 9 using ehci_hcd
[ 7118.057291] sd 12:0:0:0: Device offlined - not ready after error recovery[/I]

The disk is not seen with *fdisk*, so there is no action I could do on it by using *fsck* or any other command.

I am afraid I am facing a serious hardware problem, if anybody could give me some possible solution...

Thanks in advance.

---

### Post by perevera on 2012-01-02
I tried to boot on al older Ubuntu release, 9.10 instead of my current 11.10, but the exact same problem appears:

[I]Jan  2 07:16:59 ubuntu kernel: [  450.609471] usb 2-3: USB disconnect, address 3
Jan  2 07:17:01 ubuntu CRON[3829]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  2 07:17:09 ubuntu kernel: [  460.660103] usb 2-2: new high speed USB device using ehci_hcd and address 4
Jan  2 07:17:09 ubuntu kernel: [  460.813449] usb 2-2: configuration #1 chosen from 1 choice
Jan  2 07:17:09 ubuntu kernel: [  460.818925] scsi8 : SCSI emulation for USB Mass Storage devices
Jan  2 07:17:09 ubuntu kernel: [  460.824946] usb-storage: device found at 4
Jan  2 07:17:09 ubuntu kernel: [  460.824952] usb-storage: waiting for device to settle before scanning
Jan  2 07:17:14 ubuntu kernel: [  465.820344] usb-storage: device scan complete
Jan  2 07:17:14 ubuntu kernel: [  465.833277] scsi 8:0:0:0: Direct-Access     SAMSUNG  HM120JC          0000 PQ: 0 ANSI: 0
Jan  2 07:17:14 ubuntu kernel: [  465.834168] sd 8:0:0:0: Attached scsi generic sg2 type 0
Jan  2 07:17:14 ubuntu kernel: [  465.835005] sd 8:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Jan  2 07:17:14 ubuntu kernel: [  465.836975] sd 8:0:0:0: [sdb] Write Protect is off
Jan  2 07:17:14 ubuntu kernel: [  465.836975] sd 8:0:0:0: [sdb] Mode Sense: 27 00 00 00
Jan  2 07:17:14 ubuntu kernel: [  465.836975] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jan  2 07:17:14 ubuntu kernel: [  465.839512] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jan  2 07:17:15 ubuntu kernel: [  465.839521]  sdb: sdb1 sdb2 < sdb5 >
Jan  2 07:17:15 ubuntu kernel: [  466.343939] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jan  2 07:17:15 ubuntu kernel: [  466.343949] sd 8:0:0:0: [sdb] Attached SCSI disk
Jan  2 07:17:15 ubuntu kernel: [  466.511238] sd 8:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Jan  2 07:17:15 ubuntu kernel: [  466.511250] Descriptor sense data with sense descriptors (in hex):
Jan  2 07:17:15 ubuntu kernel: [  466.511254]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
Jan  2 07:17:15 ubuntu kernel: [  466.511270]         00 00 00 00 e0 50 
Jan  2 07:17:15 ubuntu kernel: [  466.511279] sd 8:0:0:0: [sdb] Add. Sense: ATA pass through information available
Jan  2 07:17:15 ubuntu kernel: [  466.519615] sd 8:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Jan  2 07:17:15 ubuntu kernel: [  466.519626] Descriptor sense data with sense descriptors (in hex):
Jan  2 07:17:15 ubuntu kernel: [  466.519630]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
Jan  2 07:17:15 ubuntu kernel: [  466.519644]         00 4f 00 c2 e0 50 
Jan  2 07:17:15 ubuntu kernel: [  466.519652] sd 8:0:0:0: [sdb] Add. Sense: ATA pass through information available
Jan  2 07:17:15 ubuntu kernel: [  466.567387] sd 8:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Jan  2 07:17:15 ubuntu kernel: [  466.567399] Descriptor sense data with sense descriptors (in hex):
Jan  2 07:17:15 ubuntu kernel: [  466.567404]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
Jan  2 07:17:15 ubuntu kernel: [  466.567420]         00 00 00 00 e0 50 
Jan  2 07:17:15 ubuntu kernel: [  466.567428] sd 8:0:0:0: [sdb] Add. Sense: ATA pass through information available
Jan  2 07:17:15 ubuntu kernel: [  466.652919] sd 8:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Jan  2 07:17:15 ubuntu kernel: [  466.652930] Descriptor sense data with sense descriptors (in hex):
Jan  2 07:17:15 ubuntu kernel: [  466.652934]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
Jan  2 07:17:15 ubuntu kernel: [  466.652948]         00 4f 00 c2 e0 50 
Jan  2 07:17:15 ubuntu kernel: [  466.652956] sd 8:0:0:0: [sdb] Add. Sense: ATA pass through information available
Jan  2 07:17:15 ubuntu kernel: [  466.719317] sd 8:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Jan  2 07:17:15 ubuntu kernel: [  466.719328] Descriptor sense data with sense descriptors (in hex):
Jan  2 07:17:15 ubuntu kernel: [  466.719333]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 ff 00 00 
Jan  2 07:17:15 ubuntu kernel: [  466.719348]         00 00 00 00 e0 50 
Jan  2 07:17:15 ubuntu kernel: [  466.719356] sd 8:0:0:0: [sdb] Add. Sense: ATA pass through information available
Jan  2 07:17:23 ubuntu kernel: [  474.014269] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Jan  2 07:17:33 ubuntu kernel: [  484.280132] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Jan  2 07:17:49 ubuntu kernel: [  500.550103] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Jan  2 07:17:49 ubuntu kernel: [  500.834264] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Jan  2 07:18:00 ubuntu kernel: [  511.104270] usb 2-2: reset high speed USB device using ehci_hcd and address 4
Jan  2 07:18:00 ubuntu kernel: [  511.256081] sd 8:0:0:0: Device offlined - not ready after error recovery
Jan  2 07:18:00 ubuntu kernel: [  511.256108] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256124] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256168] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256191] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256246] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256276] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256291] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256307] sd 8:0:0:0: [sdb] Unhandled error code
Jan  2 07:18:00 ubuntu kernel: [  511.256311] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jan  2 07:18:00 ubuntu kernel: [  511.256318] end_request: I/O error, dev sdb, sector 234436286
Jan  2 07:18:00 ubuntu kernel: [  511.256326] Buffer I/O error on device sdb5, logical block 70589288
Jan  2 07:18:00 ubuntu kernel: [  511.256332] Buffer I/O error on device sdb5, logical block 70589289
Jan  2 07:18:00 ubuntu kernel: [  511.256338] Buffer I/O error on device sdb5, logical block 70589290
Jan  2 07:18:00 ubuntu kernel: [  511.256343] Buffer I/O error on device sdb5, logical block 70589291
Jan  2 07:18:00 ubuntu kernel: [  511.256348] Buffer I/O error on device sdb5, logical block 70589292
Jan  2 07:18:00 ubuntu kernel: [  511.256352] Buffer I/O error on device sdb5, logical block 70589293
Jan  2 07:18:00 ubuntu kernel: [  511.256357] Buffer I/O error on device sdb5, logical block 70589294
Jan  2 07:18:00 ubuntu kernel: [  511.256362] Buffer I/O error on device sdb5, logical block 70589295
Jan  2 07:18:00 ubuntu kernel: [  511.256430] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256450] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256465] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256531] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256518] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256611] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256640] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256669] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256685] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256695] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256703] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256712] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256720] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256729] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256738] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256748] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256757] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256766] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256774] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256785] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256794] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256802] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256811] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256852] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256859] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256882] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256984] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.257011] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.257026] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.256984] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.257060] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.257029] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.257045] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.257089] sd 8:0:0:0: rejecting I/O to offline device
Jan  2 07:18:00 ubuntu kernel: [  511.266475] sd 8:0:0:0: rejecting I/O to offline device[/I]

I need some good advice...

---

