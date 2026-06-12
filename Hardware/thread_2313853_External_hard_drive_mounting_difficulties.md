---
title: "External hard drive mounting difficulties"
date: 2016-02-16
forum: Hardware
---

### Post by Dan_Bowser on 2016-02-16
I am getting a bunch of strange behaviour when I plug in my external hard drive.

Sometimes it will mount, and I have a fully functioning drive, with a full file tree and accessible files.

Sometimes it will mount and I do not have access to the file tree. Additionally the OS may or may not crash; this seems to depend on whether or not I try and remount the drive before restarting.

Sometimes it wont mount at all.

I've checked the drive on a windows system. The hard drive managing GUI there reports it to be healthy, but since the drive is ext2 I can't access the files without some software.

Since the first-ish thing that pops up with a google search on this is "check dmesg" here is that output.

```
[  139.067983] usb 2-1.2: new high-speed USB device number 4 using ehci_hcd
[  139.273813] usb 2-1.2: New USB device found, idVendor=174c, idProduct=5106
[  139.273818] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[  139.273822] usb 2-1.2: Product: AS2105
[  139.273825] usb 2-1.2: Manufacturer: ASMedia
[  139.273828] usb 2-1.2: SerialNumber: 00000000000000000000
[  139.290545] scsi4 : uas
[  139.290670] usbcore: registered new interface driver uas
[  139.291489] scsi 4:0:0:0: Direct-Access     ASMT     2105             0    PQ: 0 ANSI: 6
[  139.292123] sd 4:0:0:0: Attached scsi generic sg4 type 0
[  139.310777] Initializing USB Mass Storage driver...
[  139.310839] usbcore: registered new interface driver usb-storage
[  139.310841] USB Mass Storage support registered.
[  142.560939] sd 4:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[  142.560946] sd 4:0:0:0: [sdd] 4096-byte physical blocks
[  142.562304] sd 4:0:0:0: [sdd] Write Protect is off
[  142.562311] sd 4:0:0:0: [sdd] Mode Sense: 43 00 00 00
[  142.562869] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  142.583231]  sdd: sdd1
[  142.585953] sd 4:0:0:0: uas_sense_old: urb length 30 disagrees with IU sense data length 510, using 22 bytes of sense data
[  142.664863] sd 4:0:0:0: [sdd] Attached SCSI disk
[  142.835008] sd 4:0:0:0: uas_sense_old: urb length 30 disagrees with IU sense data length 510, using 22 bytes of sense data
[  143.028524] EXT2-fs (sdd1): warning: mounting unchecked fs, running e2fsck is recommended
[  180.492179] sd 4:0:0:0: uas_eh_abort_handler tag 0
[  180.492188] sd 4:0:0:0: uas_eh_abort_handler tag 1
[  180.492199] sd 4:0:0:0: uas_eh_device_reset_handler tag 0
[  180.492204] sd 4:0:0:0: uas_eh_target_reset_handler tag 0
[  180.492208] sd 4:0:0:0: uas_eh_bus_reset_handler tag 1
[  180.496510] usb 2-1.2: URB BAD STATUS -71
[  180.564024] usb 2-1.2: reset high-speed USB device number 4 using ehci_hcd
[  180.769140] sd 4:0:0:0: Device offlined - not ready after error recovery
[  180.769147] sd 4:0:0:0: Device offlined - not ready after error recovery
[  180.769173] sd 4:0:0:0: [sdd] Unhandled error code
[  180.769177] sd 4:0:0:0: [sdd]  
[  180.769180] Result: hostbyte=DID_TIME_OUT driverbyte=DRIVER_OK
[  180.769184] sd 4:0:0:0: [sdd] CDB: 
[  180.769186] Write(10): 2a 00 00 00 08 00 00 00 08 00
[  180.769200] end_request: I/O error, dev sdd, sector 2048
[  180.769204] quiet_error: 48 callbacks suppressed
[  180.769208] Buffer I/O error on device sdd1, logical block 0
[  180.769210] lost page write due to I/O error on sdd1
[  180.770289] sd 4:0:0:0: rejecting I/O to offline device
[  180.770299] sd 4:0:0:0: rejecting I/O to offline device
[  180.770341] sd 4:0:0:0: rejecting I/O to offline device
[  180.770944] sd 4:0:0:0: rejecting I/O to offline device
[  180.771104] sd 4:0:0:0: rejecting I/O to offline device
[  180.788427] sd 4:0:0:0: rejecting I/O to offline device
[  180.788436] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.788436] 
[  180.788531] sd 4:0:0:0: rejecting I/O to offline device
[  180.788534] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.788576] sd 4:0:0:0: rejecting I/O to offline device
[  180.788579] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.788579] 
[  180.788657] sd 4:0:0:0: rejecting I/O to offline device
[  180.788660] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.788698] sd 4:0:0:0: rejecting I/O to offline device
[  180.788701] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.788701] 
[  180.788779] sd 4:0:0:0: rejecting I/O to offline device
[  180.788781] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.788814] sd 4:0:0:0: rejecting I/O to offline device
[  180.788818] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.788818] 
[  180.788895] sd 4:0:0:0: rejecting I/O to offline device
[  180.788898] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.788934] sd 4:0:0:0: rejecting I/O to offline device
[  180.788937] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.788937] 
[  180.789015] sd 4:0:0:0: rejecting I/O to offline device
[  180.789017] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.789052] sd 4:0:0:0: rejecting I/O to offline device
[  180.789055] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.789055] 
[  180.789133] sd 4:0:0:0: rejecting I/O to offline device
[  180.789135] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.789169] sd 4:0:0:0: rejecting I/O to offline device
[  180.789172] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.789172] 
[  180.789249] sd 4:0:0:0: rejecting I/O to offline device
[  180.789252] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.789285] sd 4:0:0:0: rejecting I/O to offline device
[  180.789288] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.789288] 
[  180.789366] sd 4:0:0:0: rejecting I/O to offline device
[  180.789368] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.789403] sd 4:0:0:0: rejecting I/O to offline device
[  180.789406] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.789406] 
[  180.789484] sd 4:0:0:0: rejecting I/O to offline device
[  180.789486] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.789517] sd 4:0:0:0: rejecting I/O to offline device
[  180.789521] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.789521] 
[  180.789634] sd 4:0:0:0: rejecting I/O to offline device
[  180.789637] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.789673] sd 4:0:0:0: rejecting I/O to offline device
[  180.789676] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.789676] 
[  180.789754] sd 4:0:0:0: rejecting I/O to offline device
[  180.789756] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.789786] sd 4:0:0:0: rejecting I/O to offline device
[  180.789789] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.789789] 
[  180.789867] sd 4:0:0:0: rejecting I/O to offline device
[  180.789869] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.789899] sd 4:0:0:0: rejecting I/O to offline device
[  180.789902] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.789902] 
[  180.789980] sd 4:0:0:0: rejecting I/O to offline device
[  180.789982] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.790010] sd 4:0:0:0: rejecting I/O to offline device
[  180.790013] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.790013] 
[  180.790090] sd 4:0:0:0: rejecting I/O to offline device
[  180.790092] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.790119] sd 4:0:0:0: rejecting I/O to offline device
[  180.790122] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.790122] 
[  180.790200] sd 4:0:0:0: rejecting I/O to offline device
[  180.790202] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.790229] sd 4:0:0:0: rejecting I/O to offline device
[  180.790232] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.790232] 
[  180.790309] sd 4:0:0:0: rejecting I/O to offline device
[  180.790312] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.790338] sd 4:0:0:0: rejecting I/O to offline device
[  180.790341] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.790341] 
[  180.790419] sd 4:0:0:0: rejecting I/O to offline device
[  180.790421] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.790450] sd 4:0:0:0: rejecting I/O to offline device
[  180.790453] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.790453] 
[  180.790531] sd 4:0:0:0: rejecting I/O to offline device
[  180.790533] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.790568] sd 4:0:0:0: rejecting I/O to offline device
[  180.790571] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.790571] 
[  180.790648] sd 4:0:0:0: rejecting I/O to offline device
[  180.790651] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.790685] sd 4:0:0:0: rejecting I/O to offline device
[  180.790688] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.790688] 
[  180.790766] sd 4:0:0:0: rejecting I/O to offline device
[  180.790768] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  180.797390] sd 4:0:0:0: rejecting I/O to offline device
[  180.797403] EXT2-fs (sdd1): previous I/O error to superblock detected
[  180.797403] 
[  180.797550] sd 4:0:0:0: rejecting I/O to offline device
[  180.797555] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  181.584995] sd 4:0:0:0: rejecting I/O to offline device
[  181.633173] sd 4:0:0:0: rejecting I/O to offline device
[  181.633183] EXT2-fs (sdd1): previous I/O error to superblock detected
[  181.633183] 
[  181.633331] sd 4:0:0:0: rejecting I/O to offline device
[  181.633336] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[  182.826491] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=94.210.80.251 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=64440 DF PROTO=TCP SPT=34514 DPT=53282 WINDOW=5840 RES=0x00 SYN URGP=0 
[  185.817069] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=94.210.80.251 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=64441 DF PROTO=TCP SPT=34514 DPT=53282 WINDOW=5840 RES=0x00 SYN URGP=0 
[  191.804877] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=94.210.80.251 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=64442 DF PROTO=TCP SPT=34514 DPT=53282 WINDOW=5840 RES=0x00 SYN URGP=0 
[  242.869938] sd 4:0:0:0: rejecting I/O to offline device
[  253.927317] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=69.172.153.159 DST=192.168.0.135 LEN=58 TOS=0x00 PREC=0x00 TTL=45 ID=16711 DF PROTO=UDP SPT=49152 DPT=53282 LEN=38 
[  257.008443] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=69.172.153.159 DST=192.168.0.135 LEN=58 TOS=0x00 PREC=0x00 TTL=45 ID=17387 DF PROTO=UDP SPT=49152 DPT=53282 LEN=38 
[  257.827755] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:19:5b:d5:47:f9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  335.768619] type=1400 audit(1455642525.509:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1233 comm="cupsd" pid=1233 comm="cupsd" capability=36  capname="block_suspend"
[  382.586750] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:19:5b:d5:47:f9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  389.946048] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=172.98.67.32 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=56698 DF PROTO=TCP SPT=51124 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  390.933813] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=172.98.67.32 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=56699 DF PROTO=TCP SPT=51124 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  392.928653] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=172.98.67.32 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=56700 DF PROTO=TCP SPT=51124 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  396.958474] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=172.98.67.32 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=56701 DF PROTO=TCP SPT=51124 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  397.227681] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=192.95.27.197 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=52 ID=20502 DF PROTO=TCP SPT=60969 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  398.222783] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=192.95.27.197 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=52 ID=20503 DF PROTO=TCP SPT=60969 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  412.220712] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=192.95.27.197 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=52 ID=20506 DF PROTO=TCP SPT=60969 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  456.264405] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=192.131.44.89 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=30916 DF PROTO=TCP SPT=49953 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  457.264641] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=192.131.44.89 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=30917 DF PROTO=TCP SPT=49953 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  471.262150] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=192.131.44.89 DST=192.168.0.135 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=30920 DF PROTO=TCP SPT=49953 DPT=53282 WINDOW=7300 RES=0x00 SYN URGP=0 
[  486.418777] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=108.243.241.125 DST=192.168.0.135 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=19610 PROTO=UDP SPT=50857 DPT=53282 LEN=28 
[  507.345719] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:19:5b:d5:47:f9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  611.539103] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=108.243.241.125 DST=192.168.0.135 LEN=52 TOS=0x00 PREC=0x00 TTL=117 ID=7778 DF PROTO=TCP SPT=41930 DPT=53282 WINDOW=8192 RES=0x00 SYN URGP=0 
[  632.104698] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:19:5b:d5:47:f9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  657.926751] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=80.223.247.239 DST=192.168.0.135 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=532 PROTO=UDP SPT=32748 DPT=53282 LEN=28 
[  658.693836] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=80.223.247.239 DST=192.168.0.135 LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=533 DF PROTO=TCP SPT=54110 DPT=53282 WINDOW=8192 RES=0x00 SYN URGP=0 
[  660.994628] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=80.223.247.239 DST=192.168.0.135 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=534 PROTO=UDP SPT=32748 DPT=53282 LEN=28 
[  667.435396] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=80.223.247.239 DST=192.168.0.135 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=535 PROTO=UDP SPT=32748 DPT=53282 LEN=28 
[  677.140781] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=71.19.248.67 DST=192.168.0.135 LEN=64 TOS=0x00 PREC=0x00 TTL=48 ID=51506 DF PROTO=TCP SPT=51120 DPT=53282 WINDOW=8192 RES=0x00 SYN URGP=0 
```

Thanks for any help in advance.

---

### Post by Dan_Bowser on 2016-02-17
This morning I turn the drive on and it functions perfectly. This is the dmesg output:

```
[ 9353.155242] usb 2-1.2: new high-speed USB device number 4 using ehci_hcd
[ 9353.361197] usb 2-1.2: New USB device found, idVendor=174c, idProduct=5106
[ 9353.361202] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 9353.361206] usb 2-1.2: Product: AS2105
[ 9353.361209] usb 2-1.2: Manufacturer: ASMedia
[ 9353.361212] usb 2-1.2: SerialNumber: 00000000000000000000
[ 9353.692692] Initializing USB Mass Storage driver...
[ 9353.692917] scsi4 : usb-storage 2-1.2:1.0
[ 9353.693047] usbcore: registered new interface driver usb-storage
[ 9353.693050] USB Mass Storage support registered.
[ 9353.725659] usbcore: registered new interface driver uas
[ 9354.689311] scsi 4:0:0:0: Direct-Access     ASMT     2105             0    PQ: 0 ANSI: 6
[ 9354.691085] sd 4:0:0:0: Attached scsi generic sg4 type 0
[ 9356.545698] sd 4:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 9356.546659] sd 4:0:0:0: [sdd] Write Protect is off
[ 9356.546666] sd 4:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 9356.547658] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9356.567668]  sdd: sdd1
[ 9356.570712] sd 4:0:0:0: [sdd] Attached SCSI disk
[ 9357.141061] EXT2-fs (sdd1): warning: mounting unchecked fs, running e2fsck is recommended

```

I looked up the e2fsck command and I think using it might be problematic for me.

Also, I'm not sure this sub forum is the right one for this thread anymore.

---

### Post by SeijiSensei on 2016-02-17
As a guess, the drive is developing hardware problems.  Try installing the [smartmontools]("https://help.ubuntu.com/community/Smartmontools") package and running some tests with that.

---

### Post by Dan_Bowser on 2016-02-17
OK I installed GSmartControl opened the GUI as superuser and ran both the short and extended tests and got this output:

```
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-18-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EZEX-00M2NA0
Serial Number:    WD-WCC3FRUZKYPP
LU WWN Device Id: 5 0014ee 2b5433491
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Not recognized. Minor revision code: 0x001f
Local Time is:    Wed Feb 17 18:18:05 2016 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (11880) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 123) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   175   174   021    Pre-fail  Always       -       2208
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       151
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       350
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       57
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       33
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       118
194 Temperature_Celsius     0x0022   101   098   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       350         -
# 2  Short offline       Completed without error       00%       345         -
# 3  Extended offline    Aborted by host               50%       345         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

So the drive passed both tests fine.

---

### Post by Dan_Bowser on 2016-02-17
I was going to just format it with a new file table, ext3 or 4 but that seems like it would be an irrelevant change.

---

### Post by oldos2er on 2016-02-17
Moving from a non-journaling files system (ext2) to a journaling one (ext3 or 4) means your data will have an extra layer of protection. Up to you whether it's worthwhile or not.

---

### Post by Dan_Bowser on 2016-02-21
> **oldos2er said:**
> Moving from a non-journaling files system (ext2) to a journaling one (ext3 or 4) means your data will have an extra layer of protection. Up to you whether it's worthwhile or not.

I can do this yes.

Will it have any effect on my problems mounting my hard drive though?

---

### Post by Dan_Bowser on 2016-02-21
Here's another dmesg output if that's helpful.
```
[33186.620036] usb 2-1.2: new high-speed USB device number 5 using ehci_hcd
[33186.826000] usb 2-1.2: New USB device found, idVendor=174c, idProduct=5106
[33186.826005] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[33186.826009] usb 2-1.2: Product: AS2105
[33186.826012] usb 2-1.2: Manufacturer: ASMedia
[33186.826015] usb 2-1.2: SerialNumber: 00000000000000000000
[33187.255187] scsi4 : uas
[33187.255351] usbcore: registered new interface driver uas
[33187.256276] scsi 4:0:0:0: Direct-Access     ASMT     2105             0    PQ: 0 ANSI: 6
[33187.256925] sd 4:0:0:0: Attached scsi generic sg4 type 0
[33187.263723] Initializing USB Mass Storage driver...
[33187.263763] usbcore: registered new interface driver usb-storage
[33187.263764] USB Mass Storage support registered.
[33190.263338] sd 4:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[33190.263345] sd 4:0:0:0: [sdd] 4096-byte physical blocks
[33190.264705] sd 4:0:0:0: [sdd] Write Protect is off
[33190.264712] sd 4:0:0:0: [sdd] Mode Sense: 43 00 00 00
[33190.265409] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[33190.285152]  sdd: sdd1
[33190.287984] sd 4:0:0:0: [sdd] Attached SCSI disk
[33190.298334] sd 4:0:0:0: uas_sense_old: urb length 30 disagrees with IU sense data length 510, using 22 bytes of sense data
[33190.553224] sd 4:0:0:0: uas_sense_old: urb length 30 disagrees with IU sense data length 510, using 22 bytes of sense data
[33191.271526] EXT2-fs (sdd1): warning: mounting unchecked fs, running e2fsck is recommended
[33202.214007] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:19:5b:d5:47:f9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[33229.042952] sd 4:0:0:0: uas_eh_abort_handler tag 0
[33229.042958] sd 4:0:0:0: uas_eh_abort_handler tag 1
[33229.042966] sd 4:0:0:0: uas_eh_device_reset_handler tag 0
[33229.042971] sd 4:0:0:0: uas_eh_target_reset_handler tag 0
[33229.042975] sd 4:0:0:0: uas_eh_bus_reset_handler tag 1
[33229.046992] usb 2-1.2: URB BAD STATUS -71
[33229.114948] usb 2-1.2: reset high-speed USB device number 5 using ehci_hcd
[33229.320218] sd 4:0:0:0: Device offlined - not ready after error recovery
[33229.320222] sd 4:0:0:0: Device offlined - not ready after error recovery
[33229.320246] sd 4:0:0:0: [sdd] Unhandled error code
[33229.320250] sd 4:0:0:0: [sdd]  
[33229.320253] Result: hostbyte=DID_TIME_OUT driverbyte=DRIVER_OK
[33229.320257] sd 4:0:0:0: [sdd] CDB: 
[33229.320259] Write(10): 2a 00 00 00 08 00 00 00 08 00
[33229.320273] end_request: I/O error, dev sdd, sector 2048
[33229.320277] quiet_error: 182 callbacks suppressed
[33229.320281] Buffer I/O error on device sdd1, logical block 0
[33229.320284] lost page write due to I/O error on sdd1
[33229.320865] sd 4:0:0:0: rejecting I/O to offline device
[33229.320873] sd 4:0:0:0: rejecting I/O to offline device
[33229.320911] sd 4:0:0:0: rejecting I/O to offline device
[33229.321545] sd 4:0:0:0: rejecting I/O to offline device
[33229.321598] sd 4:0:0:0: rejecting I/O to offline device
[33229.321611] sd 4:0:0:0: rejecting I/O to offline device
[33229.321617] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.321617] 
[33229.321752] sd 4:0:0:0: rejecting I/O to offline device
[33229.321756] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.321804] sd 4:0:0:0: rejecting I/O to offline device
[33229.321808] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.321808] 
[33229.321928] sd 4:0:0:0: rejecting I/O to offline device
[33229.321932] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.321984] sd 4:0:0:0: rejecting I/O to offline device
[33229.321988] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.321988] 
[33229.322113] sd 4:0:0:0: rejecting I/O to offline device
[33229.322117] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.322164] sd 4:0:0:0: rejecting I/O to offline device
[33229.322168] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.322168] 
[33229.322292] sd 4:0:0:0: rejecting I/O to offline device
[33229.322296] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.322345] sd 4:0:0:0: rejecting I/O to offline device
[33229.322349] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.322349] 
[33229.322475] sd 4:0:0:0: rejecting I/O to offline device
[33229.322480] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.322530] sd 4:0:0:0: rejecting I/O to offline device
[33229.322533] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.322533] 
[33229.322663] sd 4:0:0:0: rejecting I/O to offline device
[33229.322666] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.322714] sd 4:0:0:0: rejecting I/O to offline device
[33229.322718] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.322718] 
[33229.322847] sd 4:0:0:0: rejecting I/O to offline device
[33229.322850] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.322895] sd 4:0:0:0: rejecting I/O to offline device
[33229.322899] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.322899] 
[33229.323021] sd 4:0:0:0: rejecting I/O to offline device
[33229.323025] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.323073] sd 4:0:0:0: rejecting I/O to offline device
[33229.323077] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.323077] 
[33229.323201] sd 4:0:0:0: rejecting I/O to offline device
[33229.323205] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.323247] sd 4:0:0:0: rejecting I/O to offline device
[33229.323250] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.323250] 
[33229.323377] sd 4:0:0:0: rejecting I/O to offline device
[33229.323380] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.323423] sd 4:0:0:0: rejecting I/O to offline device
[33229.323426] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.323426] 
[33229.323559] sd 4:0:0:0: rejecting I/O to offline device
[33229.323563] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.323604] sd 4:0:0:0: rejecting I/O to offline device
[33229.323608] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.323608] 
[33229.323741] sd 4:0:0:0: rejecting I/O to offline device
[33229.323745] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.323785] sd 4:0:0:0: rejecting I/O to offline device
[33229.323789] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.323789] 
[33229.323911] sd 4:0:0:0: rejecting I/O to offline device
[33229.323915] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.323952] sd 4:0:0:0: rejecting I/O to offline device
[33229.323955] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.323955] 
[33229.324085] sd 4:0:0:0: rejecting I/O to offline device
[33229.324089] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.324125] sd 4:0:0:0: rejecting I/O to offline device
[33229.324129] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.324129] 
[33229.324257] sd 4:0:0:0: rejecting I/O to offline device
[33229.324261] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.324299] sd 4:0:0:0: rejecting I/O to offline device
[33229.324303] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.324303] 
[33229.324448] sd 4:0:0:0: rejecting I/O to offline device
[33229.324452] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.324488] sd 4:0:0:0: rejecting I/O to offline device
[33229.324492] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.324492] 
[33229.324630] sd 4:0:0:0: rejecting I/O to offline device
[33229.324634] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.324678] sd 4:0:0:0: rejecting I/O to offline device
[33229.324682] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.324682] 
[33229.324820] sd 4:0:0:0: rejecting I/O to offline device
[33229.324824] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.324872] sd 4:0:0:0: rejecting I/O to offline device
[33229.324876] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.324876] 
[33229.325010] sd 4:0:0:0: rejecting I/O to offline device
[33229.325014] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.325065] sd 4:0:0:0: rejecting I/O to offline device
[33229.325069] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.325069] 
[33229.325201] sd 4:0:0:0: rejecting I/O to offline device
[33229.325205] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33229.326161] sd 4:0:0:0: rejecting I/O to offline device
[33229.326168] EXT2-fs (sdd1): previous I/O error to superblock detected
[33229.326168] 
[33229.326303] sd 4:0:0:0: rejecting I/O to offline device
[33229.326307] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33230.785998] sd 4:0:0:0: rejecting I/O to offline device
[33230.858562] sd 4:0:0:0: rejecting I/O to offline device
[33230.858572] EXT2-fs (sdd1): previous I/O error to superblock detected
[33230.858572] 
[33230.858679] sd 4:0:0:0: rejecting I/O to offline device
[33230.858683] EXT2-fs (sdd1): error: ext2_readdir: bad page in #2
[33231.066550] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=216.69.253.35 DST=192.168.0.135 LEN=58 TOS=0x00 PREC=0x00 TTL=56 ID=3060 DF PROTO=UDP SPT=51413 DPT=53282 LEN=38 
[33234.080217] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:bc:08:d2:9c:00:19:5b:d5:47:f9:08:00 SRC=216.69.253.35 DST=192.168.0.135 LEN=58 TOS=0x00 PREC=0x00 TTL=56 ID=3061 DF PROTO=UDP SPT=51413 DPT=53282 LEN=38
```

---

### Post by Dan_Bowser on 2016-02-22
> **oldos2er said:**
> Moving from a non-journaling files system (ext2) to a journaling one (ext3 or 4) means your data will have an extra layer of protection. Up to you whether it's worthwhile or not.

That did actually seem to help a bit. At least now when I turn the drive on it seems to always connect and mount properly instead of hanging.

---

