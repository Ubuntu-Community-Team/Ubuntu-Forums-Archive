---
title: "DMA timeout error durring install.."
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by Mr.C on 2007-07-24
I am trying to get 7.04 installed on a realy old laptop... but i am having issues with ide=nodma. 

I got Dapper running but i would like a newer kernel (for wifi stuff) but i carn't seam to get it to boot. so i dumped the boot out the serial port so i could copy it...

this is the last bit

hda: max request size: 128KiB
hda: 4221504 sectors (2161 MB) w/128KiB Cache, CHS=4188/16/63, DMA
hda:<5>pccard: CardBus card inserted into slot 1
cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x300-0x307 0x3
88-0x38f
cs: IO port probe 0x3e0-0x4ff: clean.
cs: IO port probe 0x820-0x8ff: clean.
cs: IO port probe 0xc00-0xcf7: clean.
cs: IO port probe 0xa00-0xaff: clean.
cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x300-0x307 0x3
88-0x38f
cs: IO port probe 0x3e0-0x4ff: clean.
cs: IO port probe 0x820-0x8ff: clean.
cs: IO port probe 0xc00-0xcf7: clean.
cs: IO port probe 0xa00-0xaff: clean.
floppy0: no floppy controllers found
hda: dma_timer_expiry: dma status == 0x22
hda: DMA timeout error
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown

and then its game over as the system locks up.:(

---

### Post by kvineeth on 2007-07-25
I am getting a similar kind of error...

this is with a single board computer having pentium m 1.1 GHz processor....

---

### Post by Mr.C on 2007-07-26
Ok....

This is a 166mmx (so 1.1GHz  is Luxury) but dapper (well linux) runs ok..

I managed to get around it by 
1. installing dapper alternative first
2. update (using apt-get dist-update)
3. then i changed the source.list to look ar fisty
4. and run the update again (using apt-get dist-update) a few times...

this got past the dma timeout issue... 

At a guess it was not the ide or hda error that stoped the machine but what ever would have come next..
I even looked at the kernel source code to see where the error was coming from (PIIX4 chipset...) this also controls the usb.. and i have seen usb errors on this machine before (it is old and has lots of stupid hardware eg a form of power managment, neomagic audio/video chip never beeped once and even a pain in windows...) more than likley it is the hardware detect in fisty installer that gets something wrong, where as the dapper one works....

But it now boots and i even got a desktop up on it.... next onto wifi and the dreaded bcm43xx

---

