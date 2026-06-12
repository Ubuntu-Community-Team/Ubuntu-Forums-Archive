---
title: "USB WD Elements drive will not stay mounted"
date: 2010-05-24
forum: Hardware
---

### Post by Zaphod69 on 2010-05-24
Hi,

I've just purchased a Western Digital Elements 1tb USB drive. My problem is that when I first plug it into my Toshiba Satellite laptop it mounts then shortly after (usually within 5 min) it's no longer mounted.

Works fine with Windows XP on same laptop.

Did some reading and managed to get a "dmesg" log file but I don't understand what it's saying (complete noob I'm afraid).

Log output (I'm only pasting what seems to be related to the drive);

[29214.345296] usbcore: registered new interface driver usb-storage
[29214.345300] USB Mass Storage support registered.
[29214.346331] usb-storage: device found at 2
[29214.346335] usb-storage: waiting for device to settle before scanning
[29219.344280] usb-storage: device scan complete
[29219.345268] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[29219.345817] sd 2:0:0:0: Attached scsi generic sg2 type 0
[29219.371085] sd 2:0:0:0: [sdb] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[29219.378970] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[29219.378978] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[29219.383529] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[29219.383535] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[29219.383542]  sdb: sdb1
[29219.405817] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[29219.405823] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[29219.405830] sd 2:0:0:0: [sdb] Attached SCSI disk
[29429.124080] usb 1-5: reset high speed USB device using ehci_hcd and address 2
[29444.680048] usb 1-5: device not accepting address 2, error -110
[29444.792082] usb 1-5: reset high speed USB device using ehci_hcd and address 2
[29460.348210] usb 1-5: device not accepting address 2, error -110
[29460.460063] usb 1-5: reset high speed USB device using ehci_hcd and address 2
[29470.892042] usb 1-5: device not accepting address 2, error -110
[29471.004063] usb 1-5: reset high speed USB device using ehci_hcd and address 2
[29481.436060] usb 1-5: device not accepting address 2, error -110
[29481.436130] sd 2:0:0:0: Device offlined - not ready after error recovery
[29481.436151] sd 2:0:0:0: [sdb] Unhandled error code
[29481.436154] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[29481.436160] end_request: I/O error, dev sdb, sector 283617720
[29481.436167] Buffer I/O error on device sdb1, logical block 35451959
[29481.436170] lost page write due to I/O error on sdb1
[29481.436180] Buffer I/O error on device sdb1, logical block 35451960
[29481.436183] lost page write due to I/O error on sdb1
[29481.436187] Buffer I/O error on device sdb1, logical block 35451961
[29481.436190] lost page write due to I/O error on sdb1
[29481.436194] Buffer I/O error on device sdb1, logical block 35451962
[29481.436197] lost page write due to I/O error on sdb1
[29481.436201] Buffer I/O error on device sdb1, logical block 35451963
[29481.436204] lost page write due to I/O error on sdb1
[29481.436208] Buffer I/O error on device sdb1, logical block 35451964
[29481.436210] lost page write due to I/O error on sdb1
[29481.436214] Buffer I/O error on device sdb1, logical block 35451965
[29481.436217] lost page write due to I/O error on sdb1
[29481.436221] Buffer I/O error on device sdb1, logical block 35451966
[29481.436224] lost page write due to I/O error on sdb1
[29481.436228] Buffer I/O error on device sdb1, logical block 35451967
[29481.436230] lost page write due to I/O error on sdb1
[29481.436235] Buffer I/O error on device sdb1, logical block 35451968
[29481.436238] lost page write due to I/O error on sdb1
[29481.436279] sd 2:0:0:0: rejecting I/O to offline device
[29481.436293] sd 2:0:0:0: rejecting I/O to offline device
[29481.436333] sd 2:0:0:0: rejecting I/O to offline device
[29481.436371] sd 2:0:0:0: rejecting I/O to offline device
[29481.436407] sd 2:0:0:0: rejecting I/O to offline device
[29481.436441] sd 2:0:0:0: rejecting I/O to offline device
[29481.436491] sd 2:0:0:0: rejecting I/O to offline device
[29481.436528] sd 2:0:0:0: rejecting I/O to offline device
[29481.436561] sd 2:0:0:0: rejecting I/O to offline device
[29481.436594] sd 2:0:0:0: rejecting I/O to offline device
[29481.436632] sd 2:0:0:0: rejecting I/O to offline device
[29481.436664] sd 2:0:0:0: rejecting I/O to offline device
[29481.436701] sd 2:0:0:0: rejecting I/O to offline device
[29481.436735] sd 2:0:0:0: rejecting I/O to offline device
[29481.436770] sd 2:0:0:0: rejecting I/O to offline device
[29481.436804] sd 2:0:0:0: rejecting I/O to offline device
[29481.436836] sd 2:0:0:0: rejecting I/O to offline device
[29481.436865] sd 2:0:0:0: rejecting I/O to offline device
[29481.436897] sd 2:0:0:0: rejecting I/O to offline device
[29481.436933] sd 2:0:0:0: rejecting I/O to offline device
[29481.436969] sd 2:0:0:0: rejecting I/O to offline device
[29481.437003] sd 2:0:0:0: rejecting I/O to offline device
[29481.437037] sd 2:0:0:0: rejecting I/O to offline device
[29481.437071] sd 2:0:0:0: rejecting I/O to offline device
[29481.437103] sd 2:0:0:0: rejecting I/O to offline device
[29481.437136] sd 2:0:0:0: rejecting I/O to offline device
[29481.437171] sd 2:0:0:0: rejecting I/O to offline device
[29481.437205] sd 2:0:0:0: rejecting I/O to offline device
[29481.437235] sd 2:0:0:0: rejecting I/O to offline device
[29481.437270] sd 2:0:0:0: rejecting I/O to offline device
[29481.437303] sd 2:0:0:0: rejecting I/O to offline device
[29481.437338] sd 2:0:0:0: rejecting I/O to offline device
[29481.437371] sd 2:0:0:0: rejecting I/O to offline device
[29481.437401] sd 2:0:0:0: rejecting I/O to offline device
[29481.437432] sd 2:0:0:0: rejecting I/O to offline device
[29481.437465] sd 2:0:0:0: rejecting I/O to offline device
[29481.437498] sd 2:0:0:0: rejecting I/O to offline device
[29481.437531] sd 2:0:0:0: rejecting I/O to offline device
[29481.437564] sd 2:0:0:0: rejecting I/O to offline device
[29481.437600] sd 2:0:0:0: rejecting I/O to offline device
[29481.437631] sd 2:0:0:0: rejecting I/O to offline device
[29481.437665] sd 2:0:0:0: rejecting I/O to offline device
[29481.437694] sd 2:0:0:0: rejecting I/O to offline device
[29481.437719] sd 2:0:0:0: rejecting I/O to offline device
[29481.437748] sd 2:0:0:0: rejecting I/O to offline device
[29481.437783] sd 2:0:0:0: rejecting I/O to offline device
[29481.437811] sd 2:0:0:0: rejecting I/O to offline device
[29481.437842] sd 2:0:0:0: rejecting I/O to offline device
[29481.437874] sd 2:0:0:0: rejecting I/O to offline device
[29481.437906] sd 2:0:0:0: rejecting I/O to offline device
[29481.437938] sd 2:0:0:0: rejecting I/O to offline device
[29481.437972] sd 2:0:0:0: rejecting I/O to offline device
[29481.438004] sd 2:0:0:0: rejecting I/O to offline device
[29481.438034] sd 2:0:0:0: rejecting I/O to offline device
[29481.438064] sd 2:0:0:0: rejecting I/O to offline device
[29481.438093] sd 2:0:0:0: rejecting I/O to offline device
[29481.438125] sd 2:0:0:0: rejecting I/O to offline device
[29481.438157] sd 2:0:0:0: rejecting I/O to offline device
[29481.438192] sd 2:0:0:0: rejecting I/O to offline device
[29481.438223] sd 2:0:0:0: rejecting I/O to offline device
[29481.438258] sd 2:0:0:0: rejecting I/O to offline device
[29481.438290] sd 2:0:0:0: rejecting I/O to offline device
[29481.438317] sd 2:0:0:0: rejecting I/O to offline device
[29481.438346] sd 2:0:0:0: rejecting I/O to offline device
[29481.438379] sd 2:0:0:0: rejecting I/O to offline device
[29481.438410] sd 2:0:0:0: rejecting I/O to offline device
[29481.438441] sd 2:0:0:0: rejecting I/O to offline device
[29481.438472] sd 2:0:0:0: rejecting I/O to offline device
[29481.438505] sd 2:0:0:0: rejecting I/O to offline device
[29481.438531] sd 2:0:0:0: rejecting I/O to offline device
[29481.438563] sd 2:0:0:0: rejecting I/O to offline device
[29481.438597] sd 2:0:0:0: rejecting I/O to offline device
[29481.438622] sd 2:0:0:0: rejecting I/O to offline device
[29481.438648] sd 2:0:0:0: rejecting I/O to offline device
[29481.438680] sd 2:0:0:0: rejecting I/O to offline device
[29481.438714] sd 2:0:0:0: rejecting I/O to offline device
[29481.438746] sd 2:0:0:0: rejecting I/O to offline device
[29481.438780] sd 2:0:0:0: rejecting I/O to offline device
[29481.438813] sd 2:0:0:0: rejecting I/O to offline device
[29481.438842] sd 2:0:0:0: rejecting I/O to offline device
[29481.438873] sd 2:0:0:0: rejecting I/O to offline device
[29481.438906] sd 2:0:0:0: rejecting I/O to offline device
[29481.438938] sd 2:0:0:0: rejecting I/O to offline device
[29481.438969] sd 2:0:0:0: rejecting I/O to offline device
[29481.438997] sd 2:0:0:0: rejecting I/O to offline device
[29481.439028] sd 2:0:0:0: rejecting I/O to offline device
[29481.439058] sd 2:0:0:0: rejecting I/O to offline device
[29481.439090] sd 2:0:0:0: rejecting I/O to offline device
[29481.439120] sd 2:0:0:0: rejecting I/O to offline device
[29481.439150] sd 2:0:0:0: rejecting I/O to offline device
[29481.439182] sd 2:0:0:0: rejecting I/O to offline device
[29481.439212] sd 2:0:0:0: rejecting I/O to offline device
[29481.439241] sd 2:0:0:0: rejecting I/O to offline device
[29481.439273] sd 2:0:0:0: rejecting I/O to offline device
[29481.439306] sd 2:0:0:0: rejecting I/O to offline device
[29481.439339] sd 2:0:0:0: rejecting I/O to offline device
[29481.439371] sd 2:0:0:0: rejecting I/O to offline device
[29481.439403] sd 2:0:0:0: rejecting I/O to offline device
[29481.439432] sd 2:0:0:0: rejecting I/O to offline device
[29481.439464] sd 2:0:0:0: rejecting I/O to offline device
[29481.439497] sd 2:0:0:0: rejecting I/O to offline device
[29481.439525] sd 2:0:0:0: rejecting I/O to offline device
[29481.439560] sd 2:0:0:0: rejecting I/O to offline device
[29481.439592] sd 2:0:0:0: rejecting I/O to offline device
[29481.439624] sd 2:0:0:0: rejecting I/O to offline device
[29481.439654] sd 2:0:0:0: rejecting I/O to offline device
[29481.439695] sd 2:0:0:0: rejecting I/O to offline device
[29481.439871] sd 2:0:0:0: [sdb] Unhandled error code

Any geniuses out there know what this problem is?

Actually the same thing happens with my iPod Classic - it mounts then a few minutes later is unmounted / disconnected.

Any help would be appreciated :)

Thanks,
Wayne

---

### Post by dino99 on 2010-05-24
install mountmanager and set your prefs about devices and partitions as you need (system admin mountmanager)

of course each device need to be formated (partedmagic)

---

### Post by Zaphod69 on 2010-05-24
Ok - I've installed mountmanager and plugged the usb drive in. mountmanager doesn't see it and neither does the system.

This is the problem - once it's unmounted it will not be recognised by the system until I reboot - then it's there for 5min or so and then gone.

Why would I need to reformat it? It's working great under Windows XP on the same laptop (the drive is NTFS formatted). During the 5mins or so when it works under Ubuntu 9.10 it's readable and writable.

---

### Post by dino99 on 2010-05-24
you can check it with [http://partedmagic.com/](http://partedmagic.com/) (boot with partedmagic)

but you might have errors logged into .xsession-errors (unhide it into /home with menu), and into: system admin log viewer

maybe you can google around with the exact WD model + ubuntu or lucid
[COLOR="Blue"]could it be a power problem: hdd dont receive enough power ? check its specs[/COLOR]

---

### Post by Zaphod69 on 2010-05-24
Hi,

I've been through the log file viewer and found this in the kernal log :

May 25 01:56:06 wayne-laptop kernel: [  148.980102] usb 1-5: new high speed USB device using ehci_hcd and address 2
May 25 01:56:06 wayne-laptop kernel: [  149.113619] usb 1-5: configuration #1 chosen from 1 choice
May 25 01:56:06 wayne-laptop kernel: [  149.190593] Initializing USB Mass Storage driver...
May 25 01:56:06 wayne-laptop kernel: [  149.190745] scsi2 : SCSI emulation for USB Mass Storage devices
May 25 01:56:06 wayne-laptop kernel: [  149.190951] usbcore: registered new interface driver usb-storage
May 25 01:56:06 wayne-laptop kernel: [  149.190954] USB Mass Storage support registered.
May 25 01:56:06 wayne-laptop kernel: [  149.191718] usb-storage: device found at 2
May 25 01:56:06 wayne-laptop kernel: [  149.191721] usb-storage: waiting for device to settle before scanning
May 25 01:56:11 wayne-laptop kernel: [  154.188268] usb-storage: device scan complete
May 25 01:56:11 wayne-laptop kernel: [  154.189123] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
May 25 01:56:11 wayne-laptop kernel: [  154.189669] sd 2:0:0:0: Attached scsi generic sg2 type 0
May 25 01:56:11 wayne-laptop kernel: [  154.206721] sd 2:0:0:0: [sdb] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
May 25 01:56:11 wayne-laptop kernel: [  154.207698] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 25 01:56:11 wayne-laptop kernel: [  154.207702] sd 2:0:0:0: [sdb] Assuming drive cache: write through
May 25 01:56:11 wayne-laptop kernel: [  154.209949] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 25 01:56:11 wayne-laptop kernel: [  154.209952] sd 2:0:0:0: [sdb] Assuming drive cache: write through
May 25 01:56:11 wayne-laptop kernel: [  154.209957]  sdb: sdb1
May 25 01:56:11 wayne-laptop kernel: [  154.232462] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 25 01:56:11 wayne-laptop kernel: [  154.232468] sd 2:0:0:0: [sdb] Assuming drive cache: write through
May 25 01:56:11 wayne-laptop kernel: [  154.232475] sd 2:0:0:0: [sdb] Attached SCSI disk
May 25 02:12:06 wayne-laptop kernel: [ 1109.163583] usb 1-5: reset high speed USB device using ehci_hcd and address 2
May 25 02:12:22 wayne-laptop kernel: [ 1124.716050] usb 1-5: device not accepting address 2, error -110
May 25 02:12:22 wayne-laptop kernel: [ 1124.828166] usb 1-5: reset high speed USB device using ehci_hcd and address 2
May 25 02:12:38 wayne-laptop kernel: [ 1140.392396] usb 1-5: device not accepting address 2, error -110
May 25 02:12:38 wayne-laptop kernel: [ 1140.504152] usb 1-5: reset high speed USB device using ehci_hcd and address 2
May 25 02:12:48 wayne-laptop kernel: [ 1150.936093] usb 1-5: device not accepting address 2, error -110
May 25 02:12:48 wayne-laptop kernel: [ 1151.048061] usb 1-5: reset high speed USB device using ehci_hcd and address 2
May 25 02:12:59 wayne-laptop kernel: [ 1161.488082] usb 1-5: device not accepting address 2, error -110
May 25 02:12:59 wayne-laptop kernel: [ 1161.488221] sd 2:0:0:0: Device offlined - not ready after error recovery
May 25 02:12:59 wayne-laptop kernel: [ 1161.488235] sd 2:0:0:0: [sdb] Unhandled error code
May 25 02:12:59 wayne-laptop kernel: [ 1161.488238] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
May 25 02:12:59 wayne-laptop kernel: [ 1161.488243] end_request: I/O error, dev sdb, sector 267956392
May 25 02:12:59 wayne-laptop kernel: [ 1161.488248] __ratelimit: 3 callbacks suppressed
May 25 02:12:59 wayne-laptop kernel: [ 1161.488252] Buffer I/O error on device sdb1, logical block 33494293
May 25 02:12:59 wayne-laptop kernel: [ 1161.488255] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488262] Buffer I/O error on device sdb1, logical block 33494294
May 25 02:12:59 wayne-laptop kernel: [ 1161.488265] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488269] Buffer I/O error on device sdb1, logical block 33494295
May 25 02:12:59 wayne-laptop kernel: [ 1161.488272] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488275] Buffer I/O error on device sdb1, logical block 33494296
May 25 02:12:59 wayne-laptop kernel: [ 1161.488278] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488282] Buffer I/O error on device sdb1, logical block 33494297
May 25 02:12:59 wayne-laptop kernel: [ 1161.488285] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488288] Buffer I/O error on device sdb1, logical block 33494298
May 25 02:12:59 wayne-laptop kernel: [ 1161.488291] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488295] Buffer I/O error on device sdb1, logical block 33494299
May 25 02:12:59 wayne-laptop kernel: [ 1161.488297] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488301] Buffer I/O error on device sdb1, logical block 33494300
May 25 02:12:59 wayne-laptop kernel: [ 1161.488304] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488307] Buffer I/O error on device sdb1, logical block 33494301
May 25 02:12:59 wayne-laptop kernel: [ 1161.488310] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488314] Buffer I/O error on device sdb1, logical block 33494302
May 25 02:12:59 wayne-laptop kernel: [ 1161.488316] lost page write due to I/O error on sdb1
May 25 02:12:59 wayne-laptop kernel: [ 1161.488344] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488355] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488379] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488403] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488423] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488446] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488471] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488491] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488523] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488550] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488575] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488600] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488621] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488648] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488674] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488700] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488727] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488754] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488781] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488807] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488827] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488847] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488869] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488889] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488909] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488929] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488949] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488970] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.488990] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489010] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489030] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489050] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489071] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489091] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489111] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489131] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489151] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489171] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489191] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489212] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489232] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489252] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489272] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489292] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489313] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489333] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489353] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489374] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489394] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489414] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489434] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489454] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489474] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489493] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489513] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489533] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489554] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489573] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489593] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489613] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489634] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489653] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489674] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489694] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489720] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489741] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489760] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489780] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489800] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489820] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489840] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489861] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489882] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489903] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489922] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489942] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489962] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.489983] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490003] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490024] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490044] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490063] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490084] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490103] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490124] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490143] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490163] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490182] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490202] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490222] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490242] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490262] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490281] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490301] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490321] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490341] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490363] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490383] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490403] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490423] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490443] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490462] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490481] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490500] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490504] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490510] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490515] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490525] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490530] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490537] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490541] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490547] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.490597] sd 2:0:0:0: [sdb] Unhandled error code
May 25 02:12:59 wayne-laptop kernel: [ 1161.490601] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
May 25 02:12:59 wayne-laptop kernel: [ 1161.490606] end_request: I/O error, dev sdb, sector 267956632
May 25 02:12:59 wayne-laptop kernel: [ 1161.491301] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.491344] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.491363] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.491383] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.491802] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.491824] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.491842] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.491861] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.491987] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.492008] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.492019] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.492019] sd 2:0:0:0: rejecting I/O to offline device
May 25 02:12:59 wayne-laptop kernel: [ 1161.496762] usb 1-5: USB disconnect, address 2
May 25 02:12:59 wayne-laptop kernel: [ 1161.835355] usb 1-5: new high speed USB device using ehci_hcd and address 3
May 25 02:13:15 wayne-laptop kernel: [ 1177.392900] usb 1-5: device not accepting address 3, error -110
May 25 02:13:15 wayne-laptop kernel: [ 1177.504717] usb 1-5: new high speed USB device using ehci_hcd and address 4
May 25 02:13:30 wayne-laptop kernel: [ 1193.064140] usb 1-5: device not accepting address 4, error -110
May 25 02:13:30 wayne-laptop kernel: [ 1193.176057] usb 1-5: new high speed USB device using ehci_hcd and address 5
May 25 02:13:41 wayne-laptop kernel: [ 1203.608142] usb 1-5: device not accepting address 5, error -110
May 25 02:13:41 wayne-laptop kernel: [ 1203.720054] usb 1-5: new high speed USB device using ehci_hcd and address 6
May 25 02:13:51 wayne-laptop kernel: [ 1214.152034] usb 1-5: device not accepting address 6, error -110
May 25 02:13:51 wayne-laptop kernel: [ 1214.152068] hub 1-0:1.0: unable to enumerate USB device on port 5

partedmagic doesn't report any errors - just a large NTFS partition.

Power for the drive is via a power pack. However the drive does have power saving - it spins down and goes to sleep. Could that be what causes it to unmount? Trouble is it wont mount again until I reboot.

I just don't get why Ubuntu 9.10 (Karmic Koala) has so many problems with it when Window XP just works. I don't want Windows tho - thats why I run Karmic the majority of the time (unless I need to access my ipod or new usb drive).

TIA,
Wayne

---

