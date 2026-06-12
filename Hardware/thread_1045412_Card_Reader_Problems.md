---
title: "Card Reader Problems"
date: 2009-01-20
forum: Hardware
---

### Post by valuntahr on 2009-01-20
I'm currently trying to get the card working on my Asus M6Ne Laptop, I followed the instructions found in some other threads and I have made some progress, however I have run into a snag that I can't seem to find a solution for. When I run dmesg the output returns this,

```
[ 9586.472844] sdricoh_cs 0.0: Searching MMC controller for pcmcia device RICOH Bay1Controller ...
[ 9586.473598] sdricoh_cs 0.0: MMC controller found
[ 9586.999446] sdricoh_cs 0.0: query_status: timeout waiting for 1000000
[ 9586.999458] sdricoh_cs 0.0: sdricoh_request: cmd 6 block transfer failed
[ 9587.204948] sdricoh_cs 0.0: query_status: timeout waiting for 4
[ 9587.204952] sdricoh_cs 0.0: sdricoh_request: transfer end error
[ 9587.232728] mmc0: problem reading switch capabilities, performance might suffer.
[ 9587.234870] mmc0: new SD card at address 0002
[ 9587.279910] mmcblk0: mmc0:0002 00000 994816KiB 
[ 9587.280339]  mmcblk0:<3>sdricoh_cs 0.0: query_status: timeout waiting for 1000000
[ 9587.487041] sdricoh_cs 0.0: sdricoh_request: cmd 18 block transfer failed
[ 9587.692311] sdricoh_cs 0.0: query_status: timeout waiting for 4
[ 9587.692315] sdricoh_cs 0.0: sdricoh_request: transfer end error
[ 9587.902641] mmcblk0: error -22 sending read/write command
[ 9587.902654] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.902660] __ratelimit: 15 callbacks suppressed
[ 9587.902664] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.902776] mmcblk0: error -110 sending read/write command
[ 9587.902780] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.902784] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.902870] mmcblk0: error -110 sending read/write command
[ 9587.902874] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.902877] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.902955] mmcblk0: error -110 sending read/write command
[ 9587.902959] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.902962] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.903039] mmcblk0: error -110 sending read/write command
[ 9587.903043] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903046] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.903059] ldm_validate_partition_table(): Disk read failed.
[ 9587.903128] mmcblk0: error -110 sending read/write command
[ 9587.903132] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903135] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.903212] mmcblk0: error -110 sending read/write command
[ 9587.903215] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903218] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.903295] mmcblk0: error -110 sending read/write command
[ 9587.903298] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903302] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.903379] mmcblk0: error -110 sending read/write command
[ 9587.903382] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903386] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.903398] Dev mmcblk0: unable to read RDB block 0
[ 9587.903466] mmcblk0: error -110 sending read/write command
[ 9587.903469] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903473] Buffer I/O error on device mmcblk0, logical block 0
[ 9587.903550] mmcblk0: error -110 sending read/write command
[ 9587.903553] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903652] mmcblk0: error -110 sending read/write command
[ 9587.903656] end_request: I/O error, dev mmcblk0, sector 24
[ 9587.903731] mmcblk0: error -110 sending read/write command
[ 9587.903734] end_request: I/O error, dev mmcblk0, sector 24
[ 9587.903811] mmcblk0: error -110 sending read/write command
[ 9587.903814] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903891] mmcblk0: error -110 sending read/write command
[ 9587.903894] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.903907]  unable to read partition table
[ 9587.929424] mmcblk0: error -110 sending read/write command
[ 9587.929433] end_request: I/O error, dev mmcblk0, sector 8
[ 9587.929500] mmcblk0: error -110 sending read/write command
[ 9587.929503] end_request: I/O error, dev mmcblk0, sector 16
[ 9587.929561] mmcblk0: error -110 sending read/write command
[ 9587.929564] end_request: I/O error, dev mmcblk0, sector 24
[ 9587.929622] mmcblk0: error -110 sending read/write command
[ 9587.929626] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.929704] mmcblk0: error -110 sending read/write command
[ 9587.929707] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.942066] mmcblk0: error -110 sending read/write command
[ 9587.942074] end_request: I/O error, dev mmcblk0, sector 8
[ 9587.942141] mmcblk0: error -110 sending read/write command
[ 9587.942144] end_request: I/O error, dev mmcblk0, sector 16
[ 9587.942202] mmcblk0: error -110 sending read/write command
[ 9587.942205] end_request: I/O error, dev mmcblk0, sector 24
[ 9587.942263] mmcblk0: error -110 sending read/write command
[ 9587.942267] end_request: I/O error, dev mmcblk0, sector 0
[ 9587.942345] mmcblk0: error -110 sending read/write command
[ 9587.942349] end_request: I/O error, dev mmcblk0, sector 0
```

Any help in fixing this problem would be much appreciated.

---

