---
title: "all_generic_ide and Kernel 2.6.28"
date: 2009-05-02
forum: Hardware
---

### Post by j_a_n on 2009-05-02
Hello everybody,

i'm using Ubuntu for a short time for my server

[LIST]
[*]AMD Geode 800Mhz
[*]Mainboard Commell LV-651 ([http://www.commell.com.tw/Support/SBC/LV-651(S).htm]("http://www.commell.com.tw/Support/SBC/LV-651%28S%29.htm"))
[*]2,5" IDE HDD
[/LIST]
While booting the messages mentioned below are displayed. My interpretation is, that the HDD speed is reduced from UDMA/100 to UDMA/66. Extract from the mainboard's manual: "The board has one Ultra DMA33 IDE interface to support up to 2 ATAPI devices ...".

Before upgrading to Ubuntu 8.10er Version I used Kernel 2.6.27-11. I added the option "all_generic_ide" in the file /boot/grub/menu.lst and the messages have not been shown any longer (I read about this option in other contexts).

My questions are: 

[LIST]
[*]What is the impact of the option "all_generic_ide"?
[*]Why does this option no longer work with the Kernel 2.6.28?
[/LIST]
Here are the messages that are displayed while booting:

```

[    7.437463] pata_amd 0000:00:0f.2: version 0.3.10
[    7.438014] scsi0 : pata_amd
[    7.438479] scsi1 : pata_amd
[    7.439785] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    7.439807] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    7.969134] ata1.00: ATA-8: WDC WD3200BEVE-00A0HT0, 11.01A11, max UDMA/100
[    7.969156] ata1.00: 625142448 sectors, multi 16: LBA48
[    7.977085] ata1.00: configured for UDMA/100
[    7.977389] ata2: port disabled. ignoring.
[    7.977797] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVE-0 11.0 PQ: 0 ANSI: 5
[    7.978351] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    7.978438] sd 0:0:0:0: [sda] Write Protect is off
[    7.978457] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.978589] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.978906] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    7.978986] sd 0:0:0:0: [sda] Write Protect is off
[    7.979004] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.979133] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.979159]  sda:<3>ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    7.987512] ata1.00: BMDMA stat 0x24
[    7.987603] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[    7.987615]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[    7.987745] ata1.00: status: { DRDY ERR }
[    7.987806] ata1.00: error: { ICRC ABRT }
[    7.988190] ata1: soft resetting link
[    8.173494] ata1.00: configured for UDMA/100
[    8.173531] ata1: EH complete
[    8.176377] ata1.00: limiting speed to UDMA/66:PIO4
[    8.176398] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    8.176468] ata1.00: BMDMA stat 0x24
[    8.176547] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[    8.176560]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[    8.176689] ata1.00: status: { DRDY ERR }
[    8.176749] ata1.00: error: { ICRC ABRT }
[    8.177076] ata1: soft resetting link
[    8.352837] ata1.00: configured for UDMA/66
[    8.352868] ata1: EH complete
[    8.364908]  sda1 sda2 < sda5 >
[    8.393071] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.393323] sd 0:0:0:0: Attached scsi generic sg0 type 0
```

---

