---
title: "RTS5229 on Toshiba Satellite L50-C-29V"
date: 2016-06-14
forum: Hardware
---

### Post by karhulitos on 2016-06-14
Hi,

other than the card reader Ubuntu 16.04 is running fine on this lappy. Card reader occasionally mounts SD card but when anything is read the operation stalls to an IO error.

[COLOR="#FF0000"]dmesg
[ 3257.290228] mmcblk0: unknown error -22 sending read/write command, card status 0x900
[ 3257.489891] mmc0: cannot verify signal voltage switch
[ 3257.604886] mmc0: tried to reset card
[ 3257.608735] mmcblk0: unknown error -22 sending read/write command, card status 0x900
[ 3257.805782] mmc0: cannot verify signal voltage switch
[ 3257.920808] mmc0: tried to reset card
[ 3257.921786] mmcblk0: unknown error -22 sending read/write command, card status 0x900
[ 3257.921803] blk_update_request: I/O error, dev mmcblk0, sector 60751136
[ 3257.923947] mmcblk0: unknown error -22 sending read/write command, card status 0x900
[ 3258.121764] mmc0: cannot verify signal voltage switch[/COLOR]

[COLOR="#FF0000"]lspci
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)[/COLOR]

[COLOR="#FF0000"]lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial
4.4.0-25-generic[/COLOR]

Copying with Nautilus from SD card (SanDisk Ultra 32G) to HDD throws: Error in splice operation: I/O error.

[COLOR="#FF0000"]Also compiling the Linux driver from 2012 end with many errors but I am not sure if I should be compiling anything as the kernel should have the module. Very confusing.
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/nalle/System/drivers/RTS5229/rts5229/rtsx_chip.o' failed
make[2]: *** [/home/nalle/System/drivers/RTS5229/rts5229/rtsx_chip.o] Error 1
Makefile:1403: recipe for target '_module_/home/nalle/System/drivers/RTS5229/rts5229' failed
make[1]: *** [_module_/home/nalle/System/drivers/RTS5229/rts5229] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-25-generic'
Makefile:35: recipe for target 'default' failed
make: *** [default] Error 2[/COLOR]

Google gives many hits for RTS5229 related problems but not so many from recent times. Could my hardware be faulty? After all this is very new lappy, a week old only.

---

### Post by karhulitos on 2016-06-15
> **karhulitos said:**
> 
Google gives many hits for RTS5229 related problems but not so many from recent times. Could my hardware be faulty? After all this is very new lappy, a week old only.
Well, what's the next probable cause if kernel has the driver and no one else whines about RTS5229 not working? Went to the store and tried same model lappy on shop display and RTS5229 worked flawlessly. Hardware failure.
Not a plus for Toshiba qualitywise but got to say Ubuntu 16.04 appears to work rather perfectly with this model, if anyone happens to search for such info and stumbles across this post. Very good deal spec/pricewise.

[edit] not so fast, I can't figure out what's going on.
- Similar L50-C-29V in the shop, booted with 16.04 Live USB, same SDHC card, result: 250MB file read is successful and all actions are fast. Retried 3 times, no hickups.
- My L50-C-29V at home, booted with 16.04 Live USB, same SDHC card, result: 250MB read I/O error, mounting requires multiple card inserts before success.
- My L50-C-29V at home, installed Win 10 with Toshiba drivers, same SDHC card, result:  250MB file read is successful and all actions are fast. Retried 3 times, no hickups.
Back to square one :confused:

---

### Post by karhulitos on 2016-06-16
Thinking very carefully what could be the differences, I can only think of one: I updated uEFI Firmware of my laptop to version 1.50 while it was 1.20 when unboxed. Now need to figure out how to downgrade.

---

