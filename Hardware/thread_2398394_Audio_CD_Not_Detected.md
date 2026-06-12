---
title: "Audio CD Not Detected"
date: 2018-08-11
forum: Hardware
---

### Post by tom181 on 2018-08-11
I am running 18.04 with kernel 4.15.0-30-generic. I am unable to mount and use an audio CD. Any ideas how to debug this?

```

[ 1079.908120] sr 2:0:0:0: [sr0] tag#20 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1079.908123] sr 2:0:0:0: [sr0] tag#20 Sense Key : Illegal Request [current]
[ 1079.908126] sr 2:0:0:0: [sr0] tag#20 Add. Sense: Illegal mode for this track
[ 1079.908128] sr 2:0:0:0: [sr0] tag#20 CDB: Read(10) 28 00 00 02 9d 96 00 00 02 00
[ 1079.908129] print_req_error: I/O error, dev sr0, sector 685656
[ 1088.599902] sr 2:0:0:0: [sr0] tag#25 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1088.599905] sr 2:0:0:0: [sr0] tag#25 Sense Key : Illegal Request [current]
[ 1088.599907] sr 2:0:0:0: [sr0] tag#25 Add. Sense: Illegal mode for this track
[ 1088.599910] sr 2:0:0:0: [sr0] tag#25 CDB: Read(10) 28 00 00 02 9d 96 00 00 02 00
[ 1088.599911] print_req_error: I/O error, dev sr0, sector 685656
[ 1088.599915] Buffer I/O error on dev sr0, logical block 85707, async page read
[ 1097.191700] sr 2:0:0:0: [sr0] tag#30 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1097.191703] sr 2:0:0:0: [sr0] tag#30 Sense Key : Illegal Request [current]
[ 1097.191705] sr 2:0:0:0: [sr0] tag#30 Add. Sense: Illegal mode for this track
[ 1097.191707] sr 2:0:0:0: [sr0] tag#30 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1097.191709] print_req_error: I/O error, dev sr0, sector 0
[ 1097.939651] sr 2:0:0:0: [sr0] tag#4 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1097.939654] sr 2:0:0:0: [sr0] tag#4 Sense Key : Illegal Request [current]
[ 1097.939656] sr 2:0:0:0: [sr0] tag#4 Add. Sense: Illegal mode for this track
[ 1097.939659] sr 2:0:0:0: [sr0] tag#4 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1097.939660] print_req_error: I/O error, dev sr0, sector 0
[ 1097.939664] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1098.683628] sr 2:0:0:0: [sr0] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1098.683633] sr 2:0:0:0: [sr0] tag#7 Sense Key : Illegal Request [current]
[ 1098.683636] sr 2:0:0:0: [sr0] tag#7 Add. Sense: Illegal mode for this track
[ 1098.683639] sr 2:0:0:0: [sr0] tag#7 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1098.683642] print_req_error: I/O error, dev sr0, sector 0
[ 1098.683647] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1099.439637] sr 2:0:0:0: [sr0] tag#10 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1099.439640] sr 2:0:0:0: [sr0] tag#10 Sense Key : Illegal Request [current]
[ 1099.439642] sr 2:0:0:0: [sr0] tag#10 Add. Sense: Illegal mode for this track
[ 1099.439645] sr 2:0:0:0: [sr0] tag#10 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1099.439646] print_req_error: I/O error, dev sr0, sector 0
[ 1099.439650] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1119.283132] sr 2:0:0:0: [sr0] tag#16 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1119.283136] sr 2:0:0:0: [sr0] tag#16 Sense Key : Illegal Request [current]
[ 1119.283139] sr 2:0:0:0: [sr0] tag#16 Add. Sense: Illegal mode for this track
[ 1119.283143] sr 2:0:0:0: [sr0] tag#16 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1119.283145] print_req_error: I/O error, dev sr0, sector 0
[ 1119.283150] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1120.043144] sr 2:0:0:0: [sr0] tag#19 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1120.043147] sr 2:0:0:0: [sr0] tag#19 Sense Key : Illegal Request [current]
[ 1120.043149] sr 2:0:0:0: [sr0] tag#19 Add. Sense: Illegal mode for this track
[ 1120.043151] sr 2:0:0:0: [sr0] tag#19 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1120.043153] print_req_error: I/O error, dev sr0, sector 0
[ 1120.043156] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1120.771400] sr 2:0:0:0: [sr0] tag#22 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1120.771403] sr 2:0:0:0: [sr0] tag#22 Sense Key : Illegal Request [current]
[ 1120.771405] sr 2:0:0:0: [sr0] tag#22 Add. Sense: Illegal mode for this track
[ 1120.771408] sr 2:0:0:0: [sr0] tag#22 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1120.771409] print_req_error: I/O error, dev sr0, sector 0
[ 1120.771413] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1121.535087] sr 2:0:0:0: [sr0] tag#26 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1121.535091] sr 2:0:0:0: [sr0] tag#26 Sense Key : Illegal Request [current]
[ 1121.535094] sr 2:0:0:0: [sr0] tag#26 Add. Sense: Illegal mode for this track
[ 1121.535098] sr 2:0:0:0: [sr0] tag#26 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1121.535100] print_req_error: I/O error, dev sr0, sector 0
[ 1121.535104] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1122.275055] sr 2:0:0:0: [sr0] tag#29 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1122.275058] sr 2:0:0:0: [sr0] tag#29 Sense Key : Illegal Request [current]
[ 1122.275060] sr 2:0:0:0: [sr0] tag#29 Add. Sense: Illegal mode for this track
[ 1122.275063] sr 2:0:0:0: [sr0] tag#29 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1122.275064] print_req_error: I/O error, dev sr0, sector 0
[ 1122.275068] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1123.015048] sr 2:0:0:0: [sr0] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1123.015051] sr 2:0:0:0: [sr0] tag#1 Sense Key : Illegal Request [current]
[ 1123.015053] sr 2:0:0:0: [sr0] tag#1 Add. Sense: Illegal mode for this track
[ 1123.015055] sr 2:0:0:0: [sr0] tag#1 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1123.015057] print_req_error: I/O error, dev sr0, sector 0
[ 1123.015061] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1124.159034] sr 2:0:0:0: [sr0] tag#5 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1124.159037] sr 2:0:0:0: [sr0] tag#5 Sense Key : Illegal Request [current]
[ 1124.159039] sr 2:0:0:0: [sr0] tag#5 Add. Sense: Illegal mode for this track
[ 1124.159042] sr 2:0:0:0: [sr0] tag#5 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1124.159043] print_req_error: I/O error, dev sr0, sector 0
[ 1124.159047] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1124.914977] sr 2:0:0:0: [sr0] tag#8 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1124.914980] sr 2:0:0:0: [sr0] tag#8 Sense Key : Illegal Request [current]
[ 1124.914982] sr 2:0:0:0: [sr0] tag#8 Add. Sense: Illegal mode for this track
[ 1124.914984] sr 2:0:0:0: [sr0] tag#8 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1124.914986] print_req_error: I/O error, dev sr0, sector 0
[ 1124.914990] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1125.067032] sr 2:0:0:0: [sr0] tag#11 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1125.067035] sr 2:0:0:0: [sr0] tag#11 Sense Key : Illegal Request [current]
[ 1125.067037] sr 2:0:0:0: [sr0] tag#11 Add. Sense: Illegal mode for this track
[ 1125.067040] sr 2:0:0:0: [sr0] tag#11 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1125.067041] print_req_error: I/O error, dev sr0, sector 0
[ 1125.067045] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1125.798968] sr 2:0:0:0: [sr0] tag#15 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1125.798970] sr 2:0:0:0: [sr0] tag#15 Sense Key : Illegal Request [current]
[ 1125.798973] sr 2:0:0:0: [sr0] tag#15 Add. Sense: Illegal mode for this track
[ 1125.798975] sr 2:0:0:0: [sr0] tag#15 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1125.798977] print_req_error: I/O error, dev sr0, sector 0
[ 1125.798980] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1126.542978] sr 2:0:0:0: [sr0] tag#18 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1126.542981] sr 2:0:0:0: [sr0] tag#18 Sense Key : Illegal Request [current]
[ 1126.542983] sr 2:0:0:0: [sr0] tag#18 Add. Sense: Illegal mode for this track
[ 1126.542986] sr 2:0:0:0: [sr0] tag#18 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1126.542987] print_req_error: I/O error, dev sr0, sector 0
[ 1126.542990] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1127.294928] sr 2:0:0:0: [sr0] tag#21 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1127.294932] sr 2:0:0:0: [sr0] tag#21 Sense Key : Illegal Request [current]
[ 1127.294935] sr 2:0:0:0: [sr0] tag#21 Add. Sense: Illegal mode for this track
[ 1127.294938] sr 2:0:0:0: [sr0] tag#21 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1127.294940] print_req_error: I/O error, dev sr0, sector 0
[ 1127.294945] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1128.046925] sr 2:0:0:0: [sr0] tag#27 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1128.046929] sr 2:0:0:0: [sr0] tag#27 Sense Key : Illegal Request [current]
[ 1128.046931] sr 2:0:0:0: [sr0] tag#27 Add. Sense: Illegal mode for this track
[ 1128.046946] sr 2:0:0:0: [sr0] tag#27 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1128.046947] print_req_error: I/O error, dev sr0, sector 0
[ 1128.046951] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1128.782904] sr 2:0:0:0: [sr0] tag#30 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1128.782907] sr 2:0:0:0: [sr0] tag#30 Sense Key : Illegal Request [current]
[ 1128.782909] sr 2:0:0:0: [sr0] tag#30 Add. Sense: Illegal mode for this track
[ 1128.782912] sr 2:0:0:0: [sr0] tag#30 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1128.782913] print_req_error: I/O error, dev sr0, sector 0
[ 1128.782917] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1129.526874] sr 2:0:0:0: [sr0] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1129.526877] sr 2:0:0:0: [sr0] tag#2 Sense Key : Illegal Request [current]
[ 1129.526880] sr 2:0:0:0: [sr0] tag#2 Add. Sense: Illegal mode for this track
[ 1129.526883] sr 2:0:0:0: [sr0] tag#2 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1129.526885] print_req_error: I/O error, dev sr0, sector 0
[ 1129.526890] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1130.282882] sr 2:0:0:0: [sr0] tag#6 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1130.282886] sr 2:0:0:0: [sr0] tag#6 Sense Key : Illegal Request [current]
[ 1130.282889] sr 2:0:0:0: [sr0] tag#6 Add. Sense: Illegal mode for this track
[ 1130.282892] sr 2:0:0:0: [sr0] tag#6 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 1130.282894] print_req_error: I/O error, dev sr0, sector 0
[ 1130.282899] Buffer I/O error on dev sr0, logical block 0, async page read
[ 1131.022838] sr 2:0:0:0: [sr0] tag#9 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1131.022842] sr 2:0:0:0: [sr0] tag#9 Sense Key : Illegal Request [current]
[ 1131.022845] sr 2:0:0:0: [sr0] tag#9 Add. Sense: Illegal mode for this track
[ 1131.022848] sr 2:0:0:0: [sr0] tag#9 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 1131.022850] print_req_error: I/O error, dev sr0, sector 16
[ 1131.022854] Buffer I/O error on dev sr0, logical block 2, async page read
[ 1131.770846] sr 2:0:0:0: [sr0] tag#12 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1131.770849] sr 2:0:0:0: [sr0] tag#12 Sense Key : Illegal Request [current]
[ 1131.770851] sr 2:0:0:0: [sr0] tag#12 Add. Sense: Illegal mode for this track
[ 1131.770854] sr 2:0:0:0: [sr0] tag#12 CDB: Read(10) 28 00 00 00 00 20 00 00 02 00
[ 1131.770856] print_req_error: I/O error, dev sr0, sector 128
[ 1131.770859] Buffer I/O error on dev sr0, logical block 16, async page read
[ 1132.522829] sr 2:0:0:0: [sr0] tag#16 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1132.522833] sr 2:0:0:0: [sr0] tag#16 Sense Key : Illegal Request [current]
[ 1132.522835] sr 2:0:0:0: [sr0] tag#16 Add. Sense: Illegal mode for this track
[ 1132.522838] sr 2:0:0:0: [sr0] tag#16 CDB: Read(10) 28 00 00 00 00 20 00 00 02 00
[ 1132.522839] print_req_error: I/O error, dev sr0, sector 128
[ 1132.522842] Buffer I/O error on dev sr0, logical block 16, async page read
[ 1132.634860] sr 2:0:0:0: [sr0] tag#19 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1132.634863] sr 2:0:0:0: [sr0] tag#19 Sense Key : Illegal Request [current]
[ 1132.634865] sr 2:0:0:0: [sr0] tag#19 Add. Sense: Illegal mode for this track
[ 1132.634868] sr 2:0:0:0: [sr0] tag#19 CDB: Read(10) 28 00 00 00 00 20 00 00 02 00
[ 1132.634869] print_req_error: I/O error, dev sr0, sector 128
[ 1132.634873] Buffer I/O error on dev sr0, logical block 16, async page read
[ 1132.678828] sr 2:0:0:0: [sr0] tag#22 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1132.678831] sr 2:0:0:0: [sr0] tag#22 Sense Key : Illegal Request [current]
[ 1132.678833] sr 2:0:0:0: [sr0] tag#22 Add. Sense: Illegal mode for this track
[ 1132.678835] sr 2:0:0:0: [sr0] tag#22 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 1132.678836] print_req_error: I/O error, dev sr0, sector 16
[ 1132.678839] Buffer I/O error on dev sr0, logical block 2, async page read
[ 1132.830827] sr 2:0:0:0: [sr0] tag#25 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1132.830830] sr 2:0:0:0: [sr0] tag#25 Sense Key : Illegal Request [current]
[ 1132.830832] sr 2:0:0:0: [sr0] tag#25 Add. Sense: Illegal mode for this track
[ 1132.830835] sr 2:0:0:0: [sr0] tag#25 CDB: Read(10) 28 00 00 00 00 20 00 00 02 00
[ 1132.830836] print_req_error: I/O error, dev sr0, sector 128
[ 1132.830839] Buffer I/O error on dev sr0, logical block 16, async page read
[ 1133.586779] sr 2:0:0:0: [sr0] tag#28 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1133.586783] sr 2:0:0:0: [sr0] tag#28 Sense Key : Illegal Request [current]
[ 1133.586786] sr 2:0:0:0: [sr0] tag#28 Add. Sense: Illegal mode for this track
[ 1133.586789] sr 2:0:0:0: [sr0] tag#28 CDB: Read(10) 28 00 00 00 00 10 00 00 02 00
[ 1133.586791] print_req_error: I/O error, dev sr0, sector 64
[ 1133.586795] Buffer I/O error on dev sr0, logical block 8, async page read
[ 1146.530517] sr 2:0:0:0: [sr0] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1146.530519] sr 2:0:0:0: [sr0] tag#2 Sense Key : Illegal Request [current]
[ 1146.530522] sr 2:0:0:0: [sr0] tag#2 Add. Sense: Illegal mode for this track
[ 1146.530524] sr 2:0:0:0: [sr0] tag#2 CDB: Read(10) 28 00 00 00 00 10 00 00 02 00
[ 1146.530525] print_req_error: I/O error, dev sr0, sector 64
[ 1146.530529] Buffer I/O error on dev sr0, logical block 8, async page read
[ 1155.674291] sr 2:0:0:0: [sr0] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1155.674294] sr 2:0:0:0: [sr0] tag#7 Sense Key : Illegal Request [current]
[ 1155.674296] sr 2:0:0:0: [sr0] tag#7 Add. Sense: Illegal mode for this track
[ 1155.674299] sr 2:0:0:0: [sr0] tag#7 CDB: Read(10) 28 00 00 00 00 10 00 00 02 00
[ 1155.674300] print_req_error: I/O error, dev sr0, sector 64
[ 1155.674304] Buffer I/O error on dev sr0, logical block 8, async page read
tom@tom-Satellite-P855:~$ r]

```

---

### Post by tom181 on 2018-08-11
Here's my drive info

```

tom@tom-Satellite-P855:~$ sudo lshw -c storage -c disk
[sudo] password for tom: 
  *-usb                     
       description: Mass storage device
       product: AS2105
       vendor: ASMedia
       physical id: 1
       bus info: usb@4:1
       logical name: scsi6
       version: 0.01
       serial: 00000000000000000000
       capabilities: usb-3.00 scsi
       configuration: driver=uas maxpower=144mA speed=5000Mbit/s
     *-disk
          description: SCSI Disk
          product: 2105
          vendor: ASMT
          physical id: 0.0.0
          bus info: scsi@6:0.0.0
          logical name: /dev/sdb
          version: 0
          serial: 00000000000000000000
          size: 698GiB (750GB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=6 guid=22eeb4f8-1771-3a46-906a-749d4f5c79f8 logicalsectorsize=512 sectorsize=512
  *-storage
       description: SATA controller
       product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 04
       width: 32 bits
       clock: 66MHz
       capabilities: storage msi pm ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:25 ioport:40b0(size=8) ioport:40a0(size=4) ioport:4090(size=8) ioport:4080(size=4) ioport:4060(size=32) memory:c0c16000-c0c167ff
  *-scsi:0
       physical id: 1
       logical name: scsi0
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: Samsung SSD 840
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/sda
          version: BB6Q
          serial: S1DBNSAF870088D
          size: 232GiB (250GB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=b6823137-01f9-4663-bde5-23a7721f4714 logicalsectorsize=512 sectorsize=512
  *-scsi:1
       physical id: 2
       logical name: scsi2
       capabilities: emulated
     *-cdrom
          description: DVD-RAM writer
          product: CDDVDW SN-208AB
          vendor: TSSTcorp
          physical id: 0.0.0
          bus info: scsi@2:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/cdrw
          logical name: /dev/dvd
          logical name: /dev/dvdrw
          logical name: /dev/sr0
          version: TO03
          capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: ansiversion=5 status=nodisc

```

---

### Post by Autodave on 2018-08-11
Does the CD play in another machine and have you tried a different CD in this machine to see if it plays? Is this store bought or did you or someone else burn it?

---

### Post by tom181 on 2018-08-11
This does play in a Sony music player. It is store bought.

---

### Post by Yellow Pasque on 2018-08-12
> **tom181 said:**
> This does play in a Sony music player. It is store bought.

Please answer the second part of Autodave's question: Have you tried other audio CD's in this drive? When was the last time you cleaned the lens on this drive?

```
product: CDDVDW SN-208AB
vendor: TSSTcorp
version: TO03
```

Note that there is an updated firmware version for your drive (TO04), though it shouldn't make a difference reading commercial audio CD's.

---

### Post by tom181 on 2018-08-12
> **Autodave said:**
> Does the CD play in another machine and have you tried a different CD in this machine to see if it plays?

I have been able to read other commercially bought audio CDs, yes. I tried routing my optical drive to my Windows 10 image running in Virtualbox, but that failed to read the CD too. That leads me to believe that this is not an issue specific to 18.04 or even Ubuntu perhaps.

I am searching for vendor-provided download of firmware version TO04 for SN-208AB but have only found third party sources. Is there an Ubuntu utility for updating or a vendor website?

---

### Post by Autodave on 2018-08-12
Does the CD play in another PC?  If your first block is bad or has some new codec being used, it can still play in a CD player, but a PC will not know what to do with it.  Just like DVDs: they will put a bad block at the very beginning which causes a PC to stop right there while a DVD player just ignores it.

---

