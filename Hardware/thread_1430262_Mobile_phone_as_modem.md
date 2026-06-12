---
title: "Mobile phone as modem"
date: 2010-03-15
forum: Hardware
---

### Post by FabioBraso on 2010-03-15
Hello all,

I connected my new "Vodafome 840"  mobile phone in Ubuntu 9.10. But Ubuntu recognize it as a external flash  memory. I would use my 
"vodafone 840" mobile phone as a modem. 
Does I  need special package? How can i configure network manager?
How can i tell to Ubuntu to use my phone as a Modem?

thank  you

Best regards

Fabio

---

### Post by Fafler on 2010-03-15
The NetworkManager Applet should take care of it if the phone is recognized as a modem. I haven't used any Huawei phones, so i don't know how the software in your's is working, but try opening a console and type dmesg after connecting the phone. The last few lines should tell something about the phone. With my Nokia N79 i get
```
[251723.444091] usb 1-3: new high speed USB device using ehci_hcd and address 49
[251723.577521] usb 1-3: configuration #1 chosen from 1 choice
[251723.582749] cdc_acm 1-3:1.1: ttyACM1: USB ACM device
[251723.586286] usb 1-3: bad CDC descriptors
[251723.586412] usb 1-3: bad CDC descriptors

```

ttyACM1 being the device name. Maybe you can define the USB connection mode somewhere on the phone? Change it from mass storage to modem or data connection or PC suite or whatever they have chosen to call it.

---

### Post by FabioBraso on 2010-03-30
Hello, this is the lsusb output,

```

fabio@fabio-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 12d1:101f Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
fabio@fabio-desktop:~$ 

```and this is the result of dmesg. 

```

  156.124223] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.124236] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.124246] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.124259] Info fld=0x0
[  156.124264] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.124277] end_request: I/O error, dev sr1, sector 36544
[  156.124292] Buffer I/O error on device sr1, logical block 4568
[  156.172217] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.172231] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.172241] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.172253] Info fld=0x0
[  156.172259] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.172272] end_request: I/O error, dev sr1, sector 36552
[  156.172287] Buffer I/O error on device sr1, logical block 4569
[  156.236223] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.236237] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.236247] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.236260] Info fld=0x0
[  156.236265] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.236278] end_request: I/O error, dev sr1, sector 36552
[  156.236292] Buffer I/O error on device sr1, logical block 4569
[  156.288238] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.288252] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.288262] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.288274] Info fld=0x0
[  156.288279] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.288294] end_request: I/O error, dev sr1, sector 36552
[  156.288310] Buffer I/O error on device sr1, logical block 4569
[  156.328380] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.328399] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.328409] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.328423] Info fld=0x0
[  156.328428] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.328443] end_request: I/O error, dev sr1, sector 36552
[  156.328461] Buffer I/O error on device sr1, logical block 4569
[  156.400251] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.400267] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.400277] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.400289] Info fld=0x0
[  156.400294] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.400308] end_request: I/O error, dev sr1, sector 36552
[  156.400324] Buffer I/O error on device sr1, logical block 4569
[  156.504218] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.504232] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.504242] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.504255] Info fld=0x0
[  156.504260] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.504274] end_request: I/O error, dev sr1, sector 36552
[  156.504290] Buffer I/O error on device sr1, logical block 4569
[  156.540202] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.540216] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.540226] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.540238] Info fld=0x0
[  156.540243] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.540257] end_request: I/O error, dev sr1, sector 36552
[  156.540272] Buffer I/O error on device sr1, logical block 4569
[  156.604202] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.604215] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.604225] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.604238] Info fld=0x0
[  156.604243] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.604256] end_request: I/O error, dev sr1, sector 36496
[  156.604270] Buffer I/O error on device sr1, logical block 4562
[  156.660233] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.660247] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.660257] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.660270] Info fld=0x0
[  156.660275] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.660288] end_request: I/O error, dev sr1, sector 36544
[  156.720227] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.720241] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.720252] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.720264] Info fld=0x0
[  156.720269] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.720283] end_request: I/O error, dev sr1, sector 36552
[  156.768240] sr 3:0:0:0: [sr1] Unhandled sense code
[  156.768254] sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  156.768264] sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  156.768276] Info fld=0x0
[  156.768281] sr 3:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  156.768295] end_request: I/O error, dev sr1, sector 36552
[  527.883407] usb 1-4: USB disconnect, address 4
[  530.812079] usb 1-4: new high speed USB device using ehci_hcd and address 5
[  531.000432] usb 1-4: configuration #1 chosen from 1 choice
[  531.018210] scsi4 : SCSI emulation for USB Mass Storage devices
[  531.018783] usb-storage: device found at 5
[  531.018790] usb-storage: waiting for device to settle before scanning
[  534.028132] usb 1-4: USB disconnect, address 5
[  534.364080] usb 1-4: new high speed USB device using ehci_hcd and address 6
[  534.608383] usb 1-4: configuration #1 chosen from 1 choice
[  534.619854] scsi5 : SCSI emulation for USB Mass Storage devices
[  534.643322] usb-storage: device found at 6
[  534.643330] usb-storage: waiting for device to settle before scanning
[  539.644312] usb-storage: device scan complete
[  539.656504] scsi 5:0:0:0: CD-ROM            Vodafone Mass Storage     2.31 PQ: 0 ANSI: 2
[  539.920122] sr1: scsi-1 drive
[  539.920484] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  539.920703] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  553.515135] sr 5:0:0:0: [sr1] Unhandled sense code
[  553.515149] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  553.515159] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  553.515172] Info fld=0x0
[  553.515177] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  553.515190] end_request: I/O error, dev sr1, sector 36544
[  553.515203] __ratelimit: 3 callbacks suppressed
[  553.515211] Buffer I/O error on device sr1, logical block 4568
[  553.568249] sr 5:0:0:0: [sr1] Unhandled sense code
[  553.568263] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  553.568274] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  553.568287] Info fld=0x0
[  553.568292] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  553.568306] end_request: I/O error, dev sr1, sector 36544
[  553.568320] Buffer I/O error on device sr1, logical block 4568
[  553.625515] sr 5:0:0:0: [sr1] Unhandled sense code
[  553.625529] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  553.625539] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  553.625552] Info fld=0x0
[  553.625557] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  553.625571] end_request: I/O error, dev sr1, sector 36552
[  553.625585] Buffer I/O error on device sr1, logical block 4569
[  553.684244] sr 5:0:0:0: [sr1] Unhandled sense code
[  553.684258] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  553.684268] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  553.684281] Info fld=0x0
[  553.684286] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  553.684300] end_request: I/O error, dev sr1, sector 36552
[  553.684316] Buffer I/O error on device sr1, logical block 4569
[  553.798593] sr 5:0:0:0: [sr1] Unhandled sense code
[  553.798607] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  553.798617] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  553.798630] Info fld=0x0
[  553.798635] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  553.798648] end_request: I/O error, dev sr1, sector 36552
[  553.798663] Buffer I/O error on device sr1, logical block 4569
[  553.864241] sr 5:0:0:0: [sr1] Unhandled sense code
[  553.864256] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  553.864266] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  553.864278] Info fld=0x0
[  553.864283] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  553.864297] end_request: I/O error, dev sr1, sector 36552
[  553.864311] Buffer I/O error on device sr1, logical block 4569
[  553.924995] sr 5:0:0:0: [sr1] Unhandled sense code
[  553.925009] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  553.925020] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  553.925032] Info fld=0x0
[  553.925037] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  553.925051] end_request: I/O error, dev sr1, sector 36552
[  553.925065] Buffer I/O error on device sr1, logical block 4569
[  554.002458] sr 5:0:0:0: [sr1] Unhandled sense code
[  554.002472] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  554.002482] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  554.002494] Info fld=0x0
[  554.002499] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  554.002512] end_request: I/O error, dev sr1, sector 36552
[  554.002526] Buffer I/O error on device sr1, logical block 4569
[  554.120218] sr 5:0:0:0: [sr1] Unhandled sense code
[  554.120232] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  554.120242] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  554.120255] Info fld=0x0
[  554.120260] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  554.120274] end_request: I/O error, dev sr1, sector 36552
[  554.120290] Buffer I/O error on device sr1, logical block 4569
[  554.208155] sr 5:0:0:0: [sr1] Unhandled sense code
[  554.208169] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  554.208178] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  554.208191] Info fld=0x0
[  554.208196] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  554.208209] end_request: I/O error, dev sr1, sector 36496
[  554.208223] Buffer I/O error on device sr1, logical block 4562
[  554.324124] sr 5:0:0:0: [sr1] Unhandled sense code
[  554.324138] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  554.324148] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  554.324160] Info fld=0x0
[  554.324165] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  554.324178] end_request: I/O error, dev sr1, sector 36544
[  554.420130] sr 5:0:0:0: [sr1] Unhandled sense code
[  554.420145] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  554.420155] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  554.420168] Info fld=0x0
[  554.420173] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  554.420187] end_request: I/O error, dev sr1, sector 36552
[  554.516237] sr 5:0:0:0: [sr1] Unhandled sense code
[  554.516251] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  554.516261] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  554.516275] Info fld=0x0
[  554.516280] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  554.516293] end_request: I/O error, dev sr1, sector 36552
[  631.328454] usb 1-4: USB disconnect, address 6
[  631.379003] scsi 5:0:0:0: rejecting I/O to dead device
[  686.456085] usb 1-4: new high speed USB device using ehci_hcd and address 7
[  686.696384] usb 1-4: configuration #1 chosen from 1 choice
[  686.707736] scsi6 : SCSI emulation for USB Mass Storage devices
[  686.719471] usb-storage: device found at 7
[  686.719481] usb-storage: waiting for device to settle before scanning
[  689.718587] usb 1-4: USB disconnect, address 7
[  690.052081] usb 1-4: new high speed USB device using ehci_hcd and address 8
[  690.296384] usb 1-4: configuration #1 chosen from 1 choice
[  690.307808] scsi7 : SCSI emulation for USB Mass Storage devices
[  690.334752] usb-storage: device found at 8
[  690.334762] usb-storage: waiting for device to settle before scanning
[  695.359757] usb-storage: device scan complete
[  695.368211] scsi 7:0:0:0: CD-ROM            Vodafone Mass Storage     2.31 PQ: 0 ANSI: 2
[  695.573625] sr1: scsi-1 drive
[  695.573968] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  695.574193] sr 7:0:0:0: Attached scsi generic sg2 type 5
[  708.812217] sr 7:0:0:0: [sr1] Unhandled sense code
[  708.812230] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  708.812240] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  708.812253] Info fld=0x0
[  708.812258] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  708.812271] end_request: I/O error, dev sr1, sector 36544
[  708.812283] __ratelimit: 3 callbacks suppressed
[  708.812291] Buffer I/O error on device sr1, logical block 4568
[  708.870649] sr 7:0:0:0: [sr1] Unhandled sense code
[  708.870663] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  708.870673] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  708.870685] Info fld=0x0
[  708.870690] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  708.870704] end_request: I/O error, dev sr1, sector 36544
[  708.870718] Buffer I/O error on device sr1, logical block 4568
[  708.916216] sr 7:0:0:0: [sr1] Unhandled sense code
[  708.916230] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  708.916240] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  708.916252] Info fld=0x0
[  708.916257] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  708.916270] end_request: I/O error, dev sr1, sector 36552
[  708.916285] Buffer I/O error on device sr1, logical block 4569
[  708.952273] sr 7:0:0:0: [sr1] Unhandled sense code
[  708.952288] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  708.952297] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  708.952310] Info fld=0x0
[  708.952315] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  708.952329] end_request: I/O error, dev sr1, sector 36552
[  708.952345] Buffer I/O error on device sr1, logical block 4569
[  709.024200] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.024214] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.024224] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.024237] Info fld=0x0
[  709.024242] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.024256] end_request: I/O error, dev sr1, sector 36552
[  709.024272] Buffer I/O error on device sr1, logical block 4569
[  709.078666] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.078679] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.078689] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.078701] Info fld=0x0
[  709.078707] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.078720] end_request: I/O error, dev sr1, sector 36552
[  709.078735] Buffer I/O error on device sr1, logical block 4569
[  709.147527] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.147541] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.147551] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.147564] Info fld=0x0
[  709.147569] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.147582] end_request: I/O error, dev sr1, sector 36552
[  709.147597] Buffer I/O error on device sr1, logical block 4569
[  709.200218] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.200232] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.200242] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.200255] Info fld=0x0
[  709.200260] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.200273] end_request: I/O error, dev sr1, sector 36552
[  709.200287] Buffer I/O error on device sr1, logical block 4569
[  709.288123] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.288138] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.288148] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.288161] Info fld=0x0
[  709.288166] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.288180] end_request: I/O error, dev sr1, sector 36552
[  709.288194] Buffer I/O error on device sr1, logical block 4569
[  709.432479] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.432494] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.432504] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.432517] Info fld=0x0
[  709.432522] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.432535] end_request: I/O error, dev sr1, sector 36496
[  709.432550] Buffer I/O error on device sr1, logical block 4562
[  709.532183] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.532197] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.532207] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.532220] Info fld=0x0
[  709.532225] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.532238] end_request: I/O error, dev sr1, sector 36544
[  709.624197] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.624210] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.624221] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.624233] Info fld=0x0
[  709.624238] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.624251] end_request: I/O error, dev sr1, sector 36552
[  709.696125] sr 7:0:0:0: [sr1] Unhandled sense code
[  709.696139] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  709.696149] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current] 
[  709.696161] Info fld=0x0
[  709.696166] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  709.696179] end_request: I/O error, dev sr1, sector 36552
[ 1209.088244] usb 1-4: USB disconnect, address 8
[ 1209.598244] scsi 7:0:0:0: rejecting I/O to dead device
[ 1212.904199] usb 1-4: new high speed USB device using ehci_hcd and address 9
[ 1213.072536] usb 1-4: configuration #1 chosen from 1 choice
[ 1213.084732] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1213.085046] usb-storage: device found at 9
[ 1213.085052] usb-storage: waiting for device to settle before scanning
[ 1216.080211] usb 1-4: USB disconnect, address 9
[ 1216.452203] usb 1-4: new high speed USB device using ehci_hcd and address 10
[ 1216.660527] usb 1-4: configuration #1 chosen from 1 choice
[ 1216.670701] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1216.671022] usb-storage: device found at 10
[ 1216.671028] usb-storage: waiting for device to settle before scanning
[ 1221.680388] usb-storage: device scan complete
[ 1221.700377] scsi 9:0:0:0: CD-ROM            Vodafone Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1221.869779] sr1: scsi-1 drive
[ 1221.870134] sr 9:0:0:0: Attached scsi CD-ROM sr1
[ 1221.870347] sr 9:0:0:0: Attached scsi generic sg2 type 5
[ 1234.991672] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1234.991688] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1234.991698] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1234.991712] Info fld=0x0
[ 1234.991717] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1234.991731] end_request: I/O error, dev sr1, sector 36544
[ 1234.991744] __ratelimit: 3 callbacks suppressed
[ 1234.991753] Buffer I/O error on device sr1, logical block 4568
[ 1235.016279] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.016294] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.016304] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.016318] Info fld=0x0
[ 1235.016323] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.016337] end_request: I/O error, dev sr1, sector 36544
[ 1235.016352] Buffer I/O error on device sr1, logical block 4568
[ 1235.091478] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.091493] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.091503] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.091516] Info fld=0x0
[ 1235.091521] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.091535] end_request: I/O error, dev sr1, sector 36552
[ 1235.091550] Buffer I/O error on device sr1, logical block 4569
[ 1235.124280] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.124297] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.124308] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.124321] Info fld=0x0
[ 1235.124326] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.124341] end_request: I/O error, dev sr1, sector 36552
[ 1235.124356] Buffer I/O error on device sr1, logical block 4569
[ 1235.176575] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.176591] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.176601] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.176614] Info fld=0x0
[ 1235.176620] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.176634] end_request: I/O error, dev sr1, sector 36552
[ 1235.176651] Buffer I/O error on device sr1, logical block 4569
[ 1235.252245] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.252261] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.252271] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.252284] Info fld=0x0
[ 1235.252289] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.252303] end_request: I/O error, dev sr1, sector 36552
[ 1235.252319] Buffer I/O error on device sr1, logical block 4569
[ 1235.332255] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.332271] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.332281] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.332295] Info fld=0x0
[ 1235.332300] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.332313] end_request: I/O error, dev sr1, sector 36552
[ 1235.332329] Buffer I/O error on device sr1, logical block 4569
[ 1235.404240] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.404255] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.404265] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.404279] Info fld=0x0
[ 1235.404284] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.404297] end_request: I/O error, dev sr1, sector 36552
[ 1235.404313] Buffer I/O error on device sr1, logical block 4569
[ 1235.480254] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.480271] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.480280] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.480294] Info fld=0x0
[ 1235.480299] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.480312] end_request: I/O error, dev sr1, sector 36552
[ 1235.480328] Buffer I/O error on device sr1, logical block 4569
[ 1235.532221] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.532235] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.532245] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.532258] Info fld=0x0
[ 1235.532263] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.532277] end_request: I/O error, dev sr1, sector 36496
[ 1235.532292] Buffer I/O error on device sr1, logical block 4562
[ 1235.600199] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.600213] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.600222] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.600235] Info fld=0x0
[ 1235.600240] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.600254] end_request: I/O error, dev sr1, sector 36544
[ 1235.656222] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.656235] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.656246] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.656258] Info fld=0x0
[ 1235.656263] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.656277] end_request: I/O error, dev sr1, sector 36552
[ 1235.723336] sr 9:0:0:0: [sr1] Unhandled sense code
[ 1235.723350] sr 9:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1235.723360] sr 9:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1235.723373] Info fld=0x0
[ 1235.723379] sr 9:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1235.723392] end_request: I/O error, dev sr1, sector 36552
[ 1407.746042] usb 1-4: USB disconnect, address 10
[ 1407.785584] scsi 9:0:0:0: rejecting I/O to dead device
[ 1411.105466] usb 2-3: USB disconnect, address 2
[ 1411.105616] usb 2-3: Disconnecting SN9C1xx PC Camera...
[ 1411.105625] usb 2-3: V4L2 device /dev/video0 deregistered
[ 1429.984078] usb 1-4: new high speed USB device using ehci_hcd and address 11
[ 1430.228382] usb 1-4: configuration #1 chosen from 1 choice
[ 1430.239741] scsi10 : SCSI emulation for USB Mass Storage devices
[ 1430.251517] usb-storage: device found at 11
[ 1430.251527] usb-storage: waiting for device to settle before scanning
[ 1433.246047] usb 1-4: USB disconnect, address 11
[ 1433.580081] usb 1-4: new high speed USB device using ehci_hcd and address 12
[ 1433.824376] usb 1-4: configuration #1 chosen from 1 choice
[ 1433.835822] scsi11 : SCSI emulation for USB Mass Storage devices
[ 1433.862424] usb-storage: device found at 12
[ 1433.862434] usb-storage: waiting for device to settle before scanning
[ 1438.865724] usb-storage: device scan complete
[ 1438.876600] scsi 11:0:0:0: CD-ROM            Vodafone Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1439.036130] sr1: scsi-1 drive
[ 1439.036478] sr 11:0:0:0: Attached scsi CD-ROM sr1
[ 1439.036689] sr 11:0:0:0: Attached scsi generic sg2 type 5
[ 1452.608233] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1452.608246] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1452.608256] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1452.608269] Info fld=0x0
[ 1452.608274] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1452.608287] end_request: I/O error, dev sr1, sector 36544
[ 1452.608300] __ratelimit: 3 callbacks suppressed
[ 1452.608308] Buffer I/O error on device sr1, logical block 4568
[ 1452.652186] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1452.652200] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1452.652210] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1452.652261] Info fld=0x0
[ 1452.652266] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1452.652280] end_request: I/O error, dev sr1, sector 36544
[ 1452.652295] Buffer I/O error on device sr1, logical block 4568
[ 1452.716255] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1452.716269] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1452.716279] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1452.716292] Info fld=0x0
[ 1452.716297] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1452.716311] end_request: I/O error, dev sr1, sector 36552
[ 1452.716326] Buffer I/O error on device sr1, logical block 4569
[ 1452.764949] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1452.764963] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1452.764973] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1452.764985] Info fld=0x0
[ 1452.764990] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1452.765003] end_request: I/O error, dev sr1, sector 36552
[ 1452.765019] Buffer I/O error on device sr1, logical block 4569
[ 1452.852232] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1452.852246] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1452.852256] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1452.852270] Info fld=0x0
[ 1452.852275] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1452.852288] end_request: I/O error, dev sr1, sector 36552
[ 1452.852303] Buffer I/O error on device sr1, logical block 4569
[ 1452.903268] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1452.903284] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1452.903294] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1452.903306] Info fld=0x0
[ 1452.903312] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1452.903325] end_request: I/O error, dev sr1, sector 36552
[ 1452.903355] Buffer I/O error on device sr1, logical block 4569
[ 1452.960294] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1452.960310] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1452.960321] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1452.960334] Info fld=0x0
[ 1452.960339] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1452.960353] end_request: I/O error, dev sr1, sector 36552
[ 1452.960369] Buffer I/O error on device sr1, logical block 4569
[ 1453.016221] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1453.016234] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1453.016244] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1453.016256] Info fld=0x0
[ 1453.016261] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1453.016274] end_request: I/O error, dev sr1, sector 36552
[ 1453.016289] Buffer I/O error on device sr1, logical block 4569
[ 1453.076249] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1453.076262] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1453.076272] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1453.076285] Info fld=0x0
[ 1453.076290] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1453.076304] end_request: I/O error, dev sr1, sector 36552
[ 1453.076318] Buffer I/O error on device sr1, logical block 4569
[ 1453.148193] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1453.148206] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1453.148216] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1453.148230] Info fld=0x0
[ 1453.148235] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1453.148248] end_request: I/O error, dev sr1, sector 36496
[ 1453.148262] Buffer I/O error on device sr1, logical block 4562
[ 1453.228636] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1453.228651] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1453.228661] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1453.228674] Info fld=0x0
[ 1453.228679] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1453.228693] end_request: I/O error, dev sr1, sector 36544
[ 1453.324144] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1453.324158] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1453.324168] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1453.324180] Info fld=0x0
[ 1453.324185] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1453.324199] end_request: I/O error, dev sr1, sector 36552
[ 1453.432129] sr 11:0:0:0: [sr1] Unhandled sense code
[ 1453.432144] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1453.432154] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current] 
[ 1453.432167] Info fld=0x0
[ 1453.432172] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 1453.432186] end_request: I/O error, dev sr1, sector 36552
fabio@fabio-desktop:~$ 

```   Into the phone there is not a setup option that allow it to be recognized as modem instead of mass storage.
   
  If I connect the phone under a PC with WinXP, an automatic setup program will start.
   
  Please can someone help me? How can tell to Network Manager that the phone is a modem and not a mass storage?
   
  Thank you
   
  Best regards
   
  Fabio

---

### Post by Fafler on 2010-03-30
There's a small tool for that called usb_modeswitch, but i don't know how it works. It should tell the phone to change from virtual CD to modem.

---

### Post by FabioBraso on 2010-03-30
I'll get and try it.

Thank you

---

### Post by dineshs on 2010-03-30
[http://packages.ubuntu.com/karmic/usb-modeswitch](http://packages.ubuntu.com/karmic/usb-modeswitch)

---

### Post by FabioBraso on 2010-04-20
Hello all, 
  
 I had solved my problem with usb-modemswitck package.
  But to allow it work with my mobile phone (HUAWEI U7510S/VODAFONE-840) I must modify some setting for usb-modemswitch utility.
  Her the steps:
  1)      from Synaptic install usb-modemswitch
  2)      create a new file named “12d1:101f”  in folder “/etc/usb_modeswitch.d” with the following content:
   
```
########################################################
  # Vodafone 840
   
  DefaultVendor= 0x12d1
  DefaultProduct=0x101f
   
  TargetClass=0xff
   
  CheckSuccess=20
   
  MessageContent="55534243123456780600000080000601000000000000000000000000000000"
   

```3)      Modify the file “/lib/udev/rules.d/40-usb_modeswitch.rules” and add the  following line:
```
# Vodafone 840
  ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="101f", RUN+="usb_modeswitch '%b/%k'"

```  Between the # Huawei U7510 / U7517 and # Huawei E180 entries.
   
      After these simple step , Network Manager recognize it as a modem an I can use it.
  
  Thank you all 
   
  Best regards
   
  Fabio

:guitar:

---

### Post by ibod on 2010-09-07
Hi 

I also have a Huawei U7510 mobile phone, but mine is on the "3" network, not Vodafone.
The above looks to me to be specific for Vodafone.
Can you help me with what is needed to use the U7510 on my network "3"  as a modem 

Also does the modeswitch program stop the phone from being recognised as a external flash  memory permanently or can it be switched back ?

---

### Post by Hughchadders on 2010-09-07
Hi Folks.

Going along with this particular subject area, I was just wondering if anyone knows of a Ubuntu 10.04/Linux compatible device such as this, (this device is designed for windows sadly I'd imagine): [http://inventive-ideas.auctivacommerce.com/EDGE-Quad-Band-Wireless-Modem-SIM-Card-Internet-Modem-P147276.aspx](http://inventive-ideas.auctivacommerce.com/EDGE-Quad-Band-Wireless-Modem-SIM-Card-Internet-Modem-P147276.aspx)

It would be interesting to know, as many people would not have such a great deal of phone compatibility issues as they usually would because of such a device like this that can utilise your phone's SIM card for, internet, emails, etc.

Thank you for your time.

Cheers, Hugh. :D

---

