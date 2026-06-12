---
title: "System Locks up when inserting CD's or DVD's"
date: 2009-05-08
forum: Hardware
---

### Post by Drikan on 2009-05-08
Hello all. Im rather new to linux so please bear with me.   

im running a duel boot system between windows vista and Ubuntu 9.04. Vista works great and so dose ubuntu. that is untill i insert any cd or dvd while booted in ubuntu then my system locks. in vista every thing works just fine. im not affraid to go diving in to my pc and chaning stuff around but ive read that users using my dvd ram are working fine so i need a little help diagnosing the issue 

hear is the info on my dvd ram drive please some one help thanks.
please let me know what other infomation you need to help me diagnose this issue

~$ sudo hdparm -I /dev/sr0

/dev/sr0:

ATAPI CD-ROM, with removable media
    Model Number:       HL-DT-ST DVDRAM GSA-H40N                
    Serial Number:      M0076J84117         
    Firmware Revision:  RG01    
Standards:
    Likely used CD-ROM ATAPI-1
Configuration:
    DRQ response: 50us.
    Packet size: 12 bytes
Capabilities:
    LBA, IORDY(can be disabled)
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
    CBLID- above Vih
    Device num = 0

sudo hdparm -i /dev/sr0

/dev/sr0:

 Model=HL-DT-ST DVDRAM GSA-H40N                , FwRev=RG01    , SerialNo=M0076J84117         
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

---

### Post by Gnea on 2009-05-09
If you can, you should paste the output of the dmesg command to see how the system is detecting the drive.  It may also be that your PCI bus isn't getting the signals correctly, so try the following boot option:  pci=routeirq

This can be specified by booting Ubuntu, and at the grub screen when it counts down before booting, press the ESC key to enter the grub menu.  Press 'e' on the first (Default) selection, then select the second line (it starts with *kernel*) and press 'e' again, then press the 'end' key to go to the far right of the line.  It will look something like this:

```
kernel          /boot/vmlinuz-2.6.28-12-generic root=UUID=e936952a-b147-4821-9f18-3fe429671db7 ro quiet splash
```

and you will want to add the *pci=routeirq* onto the end like this:

```
kernel          /boot/vmlinuz-2.6.28-12-generic root=UUID=e936952a-b147-4821-9f18-3fe429671db7 ro quiet splash pci=routeirq
```

Once you do, just press 'enter' to accept it, then ESC to back out to the menu, then 'enter' once more to boot the kernel with the new string attached.

This may or may not work, so if it doesn't, please say so and we can try something else. 
:popcorn:

---

### Post by Drikan on 2009-05-09
adding the pci=routeirq did not work. any other ideas?

---

### Post by Drikan on 2009-05-09
ok this is my dmesg 

[    4.203658] pata_it821x 0000:07:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.203661] pata_it821x: controller in pass through mode.
[    4.203680] pata_it821x 0000:07:02.0: setting latency timer to 64
[    4.203741] scsi6 : pata_it821x
[    4.203811] scsi7 : pata_it821x
[    4.203855] ata7: PATA max UDMA/133 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 18
[    4.203858] ata8: PATA max UDMA/133 cmd 0x1010 ctl 0x1020 bmdma 0x1008 irq 18
[    4.364423] ata7.00: ATAPI: HL-DT-ST DVDRAM GSA-H40N, RG01, max UDMA/66
[    4.380310] ata7.00: configured for UDMA/66
[    4.550869] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H40N  RG01 PQ: 0 ANSI: 5
[    4.562675] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.562679] Uniform CD-ROM driver Revision: 3.20
[    4.562779] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    4.562808] sr 6:0:0:0: Attached scsi generic sg2 type 5

---

