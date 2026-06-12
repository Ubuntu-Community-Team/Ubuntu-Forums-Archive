---
title: "Can not install ubuntu 9.04 seagate sata Hard disk (sata_sil module not found)"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by rofoeagle on 2009-05-12
Hi
I am trying to install ubuntu 9.04 on a Laptop Toshiba Model M100-SP with HDD Seagate  100 GB SATA...

The problem is that the installer could  not detect the sata hard disk... I think the problem is because the kernel 2.26.28-11-generic (ubuntu 9.04) doesn't have the sata_sil module.

I have tried to load it manually with modprobe -i sata_sil   and  modprobe -i libata  but the modules were not found!!!


Please any advice? I need your help ...  What can I do?


this is the information:


**LSHW**
*-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: ATA Disk
                product: ST9100821AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5NJ0FB9G
                size: 93GiB (100GB)
                configuration: ansiversion=5



**HDPARM**
 /dev/sda:

 Model=ST9100821AS                             , FwRev=3.AAB   , SerialNo=            5NJ0FB9G
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=195371568
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode



[B]
LSPCI[/B]
00:00.0 Host bridge [0600]: ATI Technologies Inc Device [1002:5a31] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
09:04.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
09:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)



[B]
DMESG[/B]
a 4096 in
[   12.103851]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   12.103962] ata1.00: status: { DRDY ERR }
[   12.104014] ata1.00: error: { ABRT }
[   12.128659] ata1.00: configured for UDMA/100
[   12.128668] ata1: EH complete
[   12.275590] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   12.275641] ata1.00: BMDMA2 stat 0x82d0009
[   12.275692] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   12.275693]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   12.275804] ata1.00: status: { DRDY ERR }
[   12.275851] ata1.00: error: { ABRT }
[   12.300648] ata1.00: configured for UDMA/100
[   12.300657] ata1: EH complete
[   12.447641] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   12.447692] ata1.00: BMDMA2 stat 0x82d0009
[   12.447744] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   12.447745]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   12.447855] ata1.00: status: { DRDY ERR }
[   12.447903] ata1.00: error: { ABRT }
[   12.472647] ata1.00: configured for UDMA/100
[   12.472656] ata1: EH complete
[   12.619591] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   12.619642] ata1.00: BMDMA2 stat 0x82d0009
[   12.619694] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   12.619695]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   12.619806] ata1.00: status: { DRDY ERR }
[   12.619854] ata1.00: error: { ABRT }
[   12.644648] ata1.00: configured for UDMA/100
[   12.644658] ata1: EH complete
[   12.791640] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   12.791691] ata1.00: BMDMA2 stat 0x82d0009
[   12.791742] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   12.791744]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   12.791854] ata1.00: status: { DRDY ERR }
[   12.791902] ata1.00: error: { ABRT }
[   12.816649] ata1.00: configured for UDMA/100
[   12.816658] ata1: EH complete
[   12.963588] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   12.963639] ata1.00: BMDMA2 stat 0x82d0009
[   12.963690] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   12.963692]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   12.963802] ata1.00: status: { DRDY ERR }
[   12.963849] ata1.00: error: { ABRT }
[   12.988647] ata1.00: configured for UDMA/100
[   12.988656] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   12.988660] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   12.988665] Descriptor sense data with sense descriptors (in hex):
[   12.988667]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   12.988677]         00 00 00 00 
[   12.988681] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   12.988686] end_request: I/O error, dev sda, sector 0
[   12.988736] Buffer I/O error on device sda, logical block 0
[   12.988791] ata1: EH complete
[   13.135745] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   13.135795] ata1.00: BMDMA2 stat 0x82d0009
[   13.135847] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   13.135848]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   13.135959] ata1.00: status: { DRDY ERR }
[   13.136012] ata1.00: error: { ABRT }
[   13.160648] ata1.00: configured for UDMA/100
[   13.160657] ata1: EH complete
[   13.307587] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   13.307638] ata1.00: BMDMA2 stat 0x82d0009
[   13.307689] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   13.307691]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   13.307801] ata1.00: status: { DRDY ERR }
[   13.307849] ata1.00: error: { ABRT }
[   13.332648] ata1.00: configured for UDMA/100
[   13.332657] ata1: EH complete
[   13.479638] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   13.479689] ata1.00: BMDMA2 stat 0x82d0009
[   13.479740] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   13.479742]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   13.479852] ata1.00: status: { DRDY ERR }
[   13.479900] ata1.00: error: { ABRT }
[   13.504648] ata1.00: configured for UDMA/100
[   13.504657] ata1: EH complete
[   13.651585] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   13.651636] ata1.00: BMDMA2 stat 0x82d0009
[   13.651688] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   13.651689]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   13.651799] ata1.00: status: { DRDY ERR }
[   13.651847] ata1.00: error: { ABRT }
[   13.676645] ata1.00: configured for UDMA/100
[   13.676654] ata1: EH complete
[   13.823636] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   13.823687] ata1.00: BMDMA2 stat 0x82d0009
[   13.823738] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   13.823740]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   13.823850] ata1.00: status: { DRDY ERR }
[   13.823898] ata1.00: error: { ABRT }
[   13.848645] ata1.00: configured for UDMA/100
[   13.848654] ata1: EH complete
[   13.995592] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   13.995643] ata1.00: BMDMA2 stat 0x82d0009
[   13.995695] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   13.995696]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   13.995806] ata1.00: status: { DRDY ERR }
[   13.995854] ata1.00: error: { ABRT }
[   14.020648] ata1.00: configured for UDMA/100
[   14.020656] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   14.020660] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   14.020665] Descriptor sense data with sense descriptors (in hex):
[   14.020667]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   14.020677]         00 00 00 00 
[   14.020681] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   14.020686] end_request: I/O error, dev sda, sector 0
[   14.020736] Buffer I/O error on device sda, logical block 0
[   14.020790] ata1: EH complete
[   14.167741] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   14.167792] ata1.00: BMDMA2 stat 0x82d0009
[   14.167844] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   14.167845]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   14.167955] ata1.00: status: { DRDY ERR }
[   14.168008] ata1.00: error: { ABRT }
[   14.192648] ata1.00: configured for UDMA/100
[   14.192657] ata1: EH complete
[   14.339583] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   14.339634] ata1.00: BMDMA2 stat 0x82d0009
[   14.339685] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   14.339686]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   14.340324] ata1.00: status: { DRDY ERR }
[   14.340373] ata1.00: error: { ABRT }
[   14.364648] ata1.00: configured for UDMA/100
[   14.364657] ata1: EH complete
[   14.511634] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   14.511685] ata1.00: BMDMA2 stat 0x82d0009
[   14.511736] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   14.511738]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   14.511848] ata1.00: status: { DRDY ERR }
[   14.511896] ata1.00: error: { ABRT }
[   14.536648] ata1.00: configured for UDMA/100
[   14.536657] ata1: EH complete
[   14.683585] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   14.683636] ata1.00: BMDMA2 stat 0x82d0009
[   14.683687] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   14.683689]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   14.683799] ata1.00: status: { DRDY ERR }
[   14.683847] ata1.00: error: { ABRT }
[   14.708648] ata1.00: configured for UDMA/100
[   14.708657] ata1: EH complete
[   14.855634] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   14.855685] ata1.00: BMDMA2 stat 0x82d0009
[   14.855736] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   14.855738]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   14.855848] ata1.00: status: { DRDY ERR }
[   14.855896] ata1.00: error: { ABRT }
[   14.880648] ata1.00: configured for UDMA/100
[   14.880657] ata1: EH complete
[   15.027581] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   15.027632] ata1.00: BMDMA2 stat 0x82d0009
[   15.027683] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   15.027685]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   15.027795] ata1.00: status: { DRDY ERR }
[   15.027843] ata1.00: error: { ABRT }
[   15.052647] ata1.00: configured for UDMA/100
[   15.052656] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   15.052660] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   15.052665] Descriptor sense data with sense descriptors (in hex):
[   15.052668]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   15.052677]         00 00 00 18 
[   15.052682] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   15.052687] end_request: I/O error, dev sda, sector 24
[   15.052737] Buffer I/O error on device sda, logical block 3
[   15.052791] ata1: EH complete
[   15.199738] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   15.199788] ata1.00: BMDMA2 stat 0x82d0009
[   15.199840] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   15.199841]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   15.199951] ata1.00: status: { DRDY ERR }
[   15.199999] ata1.00: error: { ABRT }
[   15.224647] ata1.00: configured for UDMA/100
[   15.224656] ata1: EH complete
[   15.371580] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   15.371631] ata1.00: BMDMA2 stat 0x82d0009
[   15.371682] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   15.371684]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   15.371794] ata1.00: status: { DRDY ERR }
[   15.371842] ata1.00: error: { ABRT }
[   15.396645] ata1.00: configured for UDMA/100
[   15.396654] ata1: EH complete
[   15.543632] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   15.543682] ata1.00: BMDMA2 stat 0x82d0009
[   15.543734] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   15.543735]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   15.543845] ata1.00: status: { DRDY ERR }
[   15.543893] ata1.00: error: { ABRT }
[   15.568645] ata1.00: configured for UDMA/100
[   15.568654] ata1: EH complete
[   15.715579] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   15.715629] ata1.00: BMDMA2 stat 0x82d0009
[   15.715681] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   15.715682]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   15.715793] ata1.00: status: { DRDY ERR }
[   15.715840] ata1.00: error: { ABRT }
[   15.740648] ata1.00: configured for UDMA/100
[   15.740657] ata1: EH complete
[   15.887631] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   15.887681] ata1.00: BMDMA2 stat 0x82d0009
[   15.887732] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   15.887734]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   15.887844] ata1.00: status: { DRDY ERR }
[   15.887892] ata1.00: error: { ABRT }
[   15.912650] ata1.00: configured for UDMA/100
[   15.912659] ata1: EH complete
[   16.059578] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   16.059629] ata1.00: BMDMA2 stat 0x82d0009
[   16.059680] ata1.00: cmd c8/00:08:18:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   16.059681]          res 51/04:08:18:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   16.059791] ata1.00: status: { DRDY ERR }
[   16.059839] ata1.00: error: { ABRT }
[   16.084648] ata1.00: configured for UDMA/100
[   16.084656] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   16.084660] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   16.084665] Descriptor sense data with sense descriptors (in hex):
[   16.084667]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   16.084677]         00 00 00 18 
[   16.084681] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   16.084686] end_request: I/O error, dev sda, sector 24
[   16.084736] Buffer I/O error on device sda, logical block 3
[   16.084790] ata1: EH complete
[   16.231731] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   16.231781] ata1.00: BMDMA2 stat 0x82d0009
[   16.231832] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   16.231834]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   16.231944] ata1.00: status: { DRDY ERR }
[   16.231992] ata1.00: error: { ABRT }
[   16.256648] ata1.00: configured for UDMA/100
[   16.256657] ata1: EH complete
[   16.403576] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   16.403627] ata1.00: BMDMA2 stat 0x82d0009
[   16.403678] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   16.403680]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   16.403790] ata1.00: status: { DRDY ERR }
[   16.403838] ata1.00: error: { ABRT }
[   16.428647] ata1.00: configured for UDMA/100
[   16.428656] ata1: EH complete
[   16.575628] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   16.575679] ata1.00: BMDMA2 stat 0x82d0009
[   16.575730] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   16.575732]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   16.575842] ata1.00: status: { DRDY ERR }
[   16.575890] ata1.00: error: { ABRT }
[   16.600647] ata1.00: configured for UDMA/100
[   16.600656] ata1: EH complete
[   16.747575] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   16.747626] ata1.00: BMDMA2 stat 0x82d0009
[   16.747677] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   16.747679]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   16.747789] ata1.00: status: { DRDY ERR }
[   16.747837] ata1.00: error: { ABRT }
[   16.772651] ata1.00: configured for UDMA/100
[   16.772661] ata1: EH complete
[   16.919628] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   16.919679] ata1.00: BMDMA2 stat 0x82d0009
[   16.919730] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   16.919732]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   16.919842] ata1.00: status: { DRDY ERR }
[   16.919890] ata1.00: error: { ABRT }
[   16.944647] ata1.00: configured for UDMA/100
[   16.944656] ata1: EH complete
[   17.091575] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   17.091626] ata1.00: BMDMA2 stat 0x82d0009
[   17.091677] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   17.091678]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   17.091788] ata1.00: status: { DRDY ERR }
[   17.091836] ata1.00: error: { ABRT }
[   17.116648] ata1.00: configured for UDMA/100
[   17.116656] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   17.116660] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   17.116665] Descriptor sense data with sense descriptors (in hex):
[   17.116668]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   17.116678]         00 00 00 00 
[   17.116682] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   17.116687] end_request: I/O error, dev sda, sector 0
[   17.116737] Buffer I/O error on device sda, logical block 0
[   17.116791] ata1: EH complete
[   17.263730] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   17.263781] ata1.00: BMDMA2 stat 0x82d0009
[   17.263832] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   17.263834]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   17.263944] ata1.00: status: { DRDY ERR }
[   17.263992] ata1.00: error: { ABRT }
[   17.288648] ata1.00: configured for UDMA/100
[   17.288657] ata1: EH complete
[   17.435571] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   17.435622] ata1.00: BMDMA2 stat 0x82d0009
[   17.435673] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   17.435674]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   17.435784] ata1.00: status: { DRDY ERR }
[   17.435832] ata1.00: error: { ABRT }
[   17.456647] ata1.00: configured for UDMA/100
[   17.456656] ata1: EH complete
[   17.603560] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   17.603611] ata1.00: BMDMA2 stat 0x82d0009
[   17.603662] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   17.603664]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   17.603774] ata1.00: status: { DRDY ERR }
[   17.603822] ata1.00: error: { ABRT }
[   17.624648] ata1.00: configured for UDMA/100
[   17.624657] ata1: EH complete
[   17.771550] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   17.771600] ata1.00: BMDMA2 stat 0x82d0009
[   17.771651] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   17.771653]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   17.771763] ata1.00: status: { DRDY ERR }
[   17.771811] ata1.00: error: { ABRT }
[   17.792648] ata1.00: configured for UDMA/100
[   17.792657] ata1: EH complete
[   17.939647] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   17.939698] ata1.00: BMDMA2 stat 0x82d0009
[   17.939749] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   17.939751]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   17.939861] ata1.00: status: { DRDY ERR }
[   17.939908] ata1.00: error: { ABRT }
[   17.964647] ata1.00: configured for UDMA/100
[   17.964656] ata1: EH complete
[   18.111594] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   18.111645] ata1.00: BMDMA2 stat 0x82d0009
[   18.111696] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   18.111698]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   18.112338] ata1.00: status: { DRDY ERR }
[   18.112386] ata1.00: error: { ABRT }
[   18.136647] ata1.00: configured for UDMA/100
[   18.136656] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   18.136660] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   18.136664] Descriptor sense data with sense descriptors (in hex):
[   18.136667]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   18.136677]         00 00 00 00 
[   18.136681] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   18.136686] end_request: I/O error, dev sda, sector 0
[   18.136736] Buffer I/O error on device sda, logical block 0
[   18.136790] ata1: EH complete
[   18.136795]  unable to read partition table
[   18.136884] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.136944] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.137144] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.137204] pata_atiixp 0000:00:14.1: setting latency timer to 64
[   18.137304] scsi2 : pata_atiixp
[   18.137370] scsi3 : pata_atiixp
[   18.138733] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8460 irq 14
[   18.138737] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8468 irq 15
[   18.138782] ata3: port disabled. ignoring.
[   18.316573] ata4.00: ATAPI: TSSTcorpCDW/DVD TS-L462C, TO11, max UDMA/33
[   18.348566] ata4.00: configured for UDMA/33
[   18.349493] scsi 3:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C TO11 PQ: 0 ANSI: 5
[   18.350478] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   18.350482] Uniform CD-ROM driver Revision: 3.20
[   18.350597] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   18.350650] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   18.351122] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   18.351152] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.351179] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   18.351255] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[   18.351330] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0506000
[   18.360018] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[   18.360127] usb usb1: configuration #1 chosen from 1 choice
[   18.360160] hub 1-0:1.0: USB hub found
[   18.360171] hub 1-0:1.0: 8 ports detected
[   18.360322] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.360342] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.360357] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   18.360406] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[   18.360425] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0504000
[   18.416098] usb usb2: configuration #1 chosen from 1 choice
[   18.416127] hub 2-0:1.0: USB hub found
[   18.416143] hub 2-0:1.0: 4 ports detected
[   18.416244] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.416258] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   18.416305] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   18.416327] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0505000
[   18.472098] usb usb3: configuration #1 chosen from 1 choice
[   18.472125] hub 3-0:1.0: USB hub found
[   18.472141] hub 3-0:1.0: 4 ports detected
[   18.472248] uhci_hcd: USB Universal Host Controller Interface driver
[   18.472316] usbcore: registered new interface driver libusual
[   18.472353] usbcore: registered new interface driver usbserial
[   18.472366] USB Serial support registered for generic
[   18.472380] usbcore: registered new interface driver usbserial_generic
[   18.472383] usbserial: USB Serial Driver core
[   18.472435] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   18.472769] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.472857] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.472863] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.472866] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.472869] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.472871] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.473058] mice: PS/2 mouse device common for all mice
[   18.473242] rtc_cmos 00:04: RTC can wake from S4
[   18.473284] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[   18.473318] rtc0: alarms up to one month, 114 bytes nvram
[   18.473396] device-mapper: uevent: version 1.0.3
[   18.473534] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[   18.473592] device-mapper: multipath: version 1.0.5 loaded
[   18.473596] device-mapper: multipath round-robin: version 1.0.0 loaded
[   18.473688] EISA: Probing bus 0 at eisa.0
[   18.473701] Cannot allocate resource for EISA slot 1
[   18.473734] Cannot allocate resource for EISA slot 8
[   18.473736] EISA: Detected 0 cards.
[   18.473825] cpuidle: using governor ladder
[   18.473894] cpuidle: using governor menu
[   18.474471] TCP cubic registered
[   18.474595] NET: Registered protocol family 10
[   18.475049] lo: Disabled Privacy Extensions
[   18.475389] NET: Registered protocol family 17
[   18.475410] Bluetooth: L2CAP ver 2.11
[   18.475412] Bluetooth: L2CAP socket layer initialized
[   18.475415] Bluetooth: SCO (Voice Link) ver 0.6
[   18.475417] Bluetooth: SCO socket layer initialized
[   18.475461] Bluetooth: RFCOMM socket layer initialized
[   18.475470] Bluetooth: RFCOMM TTY layer initialized
[   18.475472] Bluetooth: RFCOMM ver 1.10
[   18.475523] Using IPI No-Shortcut mode
[   18.475628] registered taskstats version 1
[   18.475746]   Magic number: 9:299:683
[   18.475860] rtc_cmos 00:04: setting system clock to 2009-05-12 12:40:40 UTC (1242132040)
[   18.475863] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.475866] EDD information not available.
[   18.476404] Freeing unused kernel memory: 532k freed
[   18.476534] Write protecting the kernel text: 4128k
[   18.476578] Write protecting the kernel read-only data: 1532k
[   18.479849] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[   19.027470] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   19.027516] 8139cp 0000:09:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[   19.032025] 8139too Fast Ethernet driver 0.9.28
[   19.032094] 8139too 0000:09:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.033943] eth0: RealTek RTL8139 at 0xa000, 00:16:d4:1f:87:02, IRQ 22
[   19.033946] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   19.139875] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   19.139883] ata1.00: BMDMA2 stat 0x82d0009
[   19.139891] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   19.139893]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   19.139896] ata1.00: status: { DRDY ERR }
[   19.139899] ata1.00: error: { ABRT }
[   19.164712] ata1.00: configured for UDMA/100
[   19.164750] ata1: EH complete
[   19.281632] Marking TSC unstable due to TSC halts in idle
[   19.311730] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   19.311736] ata1.00: BMDMA2 stat 0x82d0009
[   19.311744] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   19.311746]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   19.311750] ata1.00: status: { DRDY ERR }
[   19.311752] ata1.00: error: { ABRT }
[   19.332707] ata1.00: configured for UDMA/100
[   19.332728] ata1: EH complete
[   19.479711] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   19.479714] ata1.00: BMDMA2 stat 0x82d0009
[   19.479720] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   19.479722]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   19.479725] ata1.00: status: { DRDY ERR }
[   19.479728] ata1.00: error: { ABRT }
[   19.500694] ata1.00: configured for UDMA/100
[   19.500704] ata1: EH complete
[   19.647723] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   19.647726] ata1.00: BMDMA2 stat 0x82d0009
[   19.647732] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   19.647733]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   19.647737] ata1.00: status: { DRDY ERR }
[   19.647739] ata1.00: error: { ABRT }
[   19.668700] ata1.00: configured for UDMA/100
[   19.668710] ata1: EH complete
[   19.815738] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   19.815741] ata1.00: BMDMA2 stat 0x82d0009
[   19.815747] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   19.815749]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   19.815752] ata1.00: status: { DRDY ERR }
[   19.815754] ata1.00: error: { ABRT }
[   19.836702] ata1.00: configured for UDMA/100
[   19.836711] ata1: EH complete
[   19.983668] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   19.983674] ata1.00: BMDMA2 stat 0x82d0009
[   19.983682] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   19.983684]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   19.983687] ata1.00: status: { DRDY ERR }
[   19.983690] ata1.00: error: { ABRT }
[   20.004748] ata1.00: configured for UDMA/100
[   20.004766] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.004771] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   20.004777] Descriptor sense data with sense descriptors (in hex):
[   20.004780]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   20.004790]         00 00 00 00 
[   20.004794] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   20.004800] end_request: I/O error, dev sda, sector 0
[   20.004805] Buffer I/O error on device sda, logical block 0
[   20.004821] ata1: EH complete
[   20.151870] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   20.151873] ata1.00: BMDMA2 stat 0x82d0009
[   20.151879] ata1.00: cmd c8/00:18:08:00:00/00:00:00:00:00/e0 tag 0 dma 12288 in
[   20.151881]          res 51/04:18:08:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   20.151884] ata1.00: status: { DRDY ERR }
[   20.151887] ata1.00: error: { ABRT }
[   20.176704] ata1.00: configured for UDMA/100
[   20.176714] ata1: EH complete
[   20.323732] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   20.323735] ata1.00: BMDMA2 stat 0x82d0009
[   20.323741] ata1.00: cmd c8/00:18:08:00:00/00:00:00:00:00/e0 tag 0 dma 12288 in
[   20.323742]          res 51/04:18:08:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   20.323746] ata1.00: status: { DRDY ERR }
[   20.323748] ata1.00: error: { ABRT }
[   20.344702] ata1.00: configured for UDMA/100
[   20.344712] ata1: EH complete
[   20.491752] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   20.491757] ata1.00: BMDMA2 stat 0x82d0009
[   20.491764] ata1.00: cmd c8/00:18:08:00:00/00:00:00:00:00/e0 tag 0 dma 12288 in
[   20.491766]          res 51/04:18:08:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   20.491769] ata1.00: status: { DRDY ERR }
[   20.491772] ata1.00: error: { ABRT }
[   20.512738] ata1.00: configured for UDMA/100
[   20.512751] ata1: EH complete
[   20.659766] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   20.659770] ata1.00: BMDMA2 stat 0x82d0009
[   20.659776] ata1.00: cmd c8/00:18:08:00:00/00:00:00:00:00/e0 tag 0 dma 12288 in
[   20.659778]          res 51/04:18:08:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   20.659781] ata1.00: status: { DRDY ERR }
[   20.659784] ata1.00: error: { ABRT }
[   20.680702] ata1.00: configured for UDMA/100
[   20.680715] ata1: EH complete
[   20.827685] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   20.827691] ata1.00: BMDMA2 stat 0x82d0009
[   20.827699] ata1.00: cmd c8/00:18:08:00:00/00:00:00:00:00/e0 tag 0 dma 12288 in
[   20.827700]          res 51/04:18:08:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   20.827704] ata1.00: status: { DRDY ERR }
[   20.827706] ata1.00: error: { ABRT }
[   20.848699] ata1.00: configured for UDMA/100
[   20.848715] ata1: EH complete
[   20.995674] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   20.995677] ata1.00: BMDMA2 stat 0x82d0009
[   20.995683] ata1.00: cmd c8/00:18:08:00:00/00:00:00:00:00/e0 tag 0 dma 12288 in
[   20.995685]          res 51/04:18:08:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   20.995689] ata1.00: status: { DRDY ERR }
[   20.995691] ata1.00: error: { ABRT }
[   21.020704] ata1.00: configured for UDMA/100
[   21.020720] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.020725] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   21.020731] Descriptor sense data with sense descriptors (in hex):
[   21.020734]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   21.020744]         00 00 00 08 
[   21.020748] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   21.020753] end_request: I/O error, dev sda, sector 8
[   21.020758] Buffer I/O error on device sda, logical block 1
[   21.020763] Buffer I/O error on device sda, logical block 2
[   21.020766] Buffer I/O error on device sda, logical block 3
[   21.020776] ata1: EH complete
[   21.020867] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[   21.167751] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   21.167754] ata1.00: BMDMA2 stat 0x82d0009
[   21.167761] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   21.167762]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   21.167766] ata1.00: status: { DRDY ERR }
[   21.167768] ata1.00: error: { ABRT }
[   21.188703] ata1.00: configured for UDMA/100
[   21.188713] ata1: EH complete
[   21.335658] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   21.335662] ata1.00: BMDMA2 stat 0x82d0009
[   21.335667] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   21.335669]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   21.335672] ata1.00: status: { DRDY ERR }
[   21.335675] ata1.00: error: { ABRT }
[   21.356700] ata1.00: configured for UDMA/100
[   21.356710] ata1: EH complete
[   21.503672] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   21.503675] ata1.00: BMDMA2 stat 0x82d0009
[   21.503681] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   21.503683]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   21.503686] ata1.00: status: { DRDY ERR }
[   21.503688] ata1.00: error: { ABRT }
[   21.524691] ata1.00: configured for UDMA/100
[   21.524701] ata1: EH complete
[   21.671682] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   21.671685] ata1.00: BMDMA2 stat 0x82d0009
[   21.671691] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   21.671692]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   21.671696] ata1.00: status: { DRDY ERR }
[   21.671698] ata1.00: error: { ABRT }
[   21.692706] ata1.00: configured for UDMA/100
[   21.692716] ata1: EH complete
[   21.839694] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   21.839697] ata1.00: BMDMA2 stat 0x82d0009
[   21.839702] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   21.839704]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   21.839707] ata1.00: status: { DRDY ERR }
[   21.839710] ata1.00: error: { ABRT }
[   21.860702] ata1.00: configured for UDMA/100
[   21.860712] ata1: EH complete
[   22.007703] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   22.007706] ata1.00: BMDMA2 stat 0x82d0009
[   22.007712] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   22.007713]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   22.007717] ata1.00: status: { DRDY ERR }
[   22.007719] ata1.00: error: { ABRT }
[   22.028701] ata1.00: configured for UDMA/100
[   22.028711] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   22.028714] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   22.028719] Descriptor sense data with sense descriptors (in hex):
[   22.028722]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   22.028732]         00 00 00 00 
[   22.028736] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   22.028741] end_request: I/O error, dev sda, sector 0
[   22.028744] Buffer I/O error on device sda, logical block 0
[   22.028755] ata1: EH complete
[   22.029887] sd 0:0:0:0: [sda] Write Protect is off
[   22.029891] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.029939] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.029978] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[   22.029995] sd 0:0:0:0: [sda] Write Protect is off
[   22.029998] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.030026] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.132067] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   22.569560] ISO 9660 Extensions: Microsoft Joliet Level 3
[   22.644419] ISO 9660 Extensions: RRIP_1991A
[   23.028612] aufs 20080922
[   23.336428] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   25.420071] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   28.708047] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   31.996062] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   31.996076] hub 2-0:1.0: unable to enumerate USB device on port 1
[   32.300072] usb 2-3: new low speed USB device using ohci_hcd and address 6
[   32.502954] usb 2-3: configuration #1 chosen from 1 choice
[   32.511229] usbcore: registered new interface driver hiddev
[   32.515364] input: HID 04b3:310b as /devices/pci0000:00/0000:00:13.0/usb2/2-3/2-3:1.0/input/input5
[   32.515679] generic-usb 0003:04B3:310B.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:13.0-3/input0
[   32.515702] usbcore: registered new interface driver usbhid
[   32.515706] usbhid: v2.6:USB HID core driver
[   77.174831] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   77.174838] ata1.00: BMDMA2 stat 0x82d0009
[   77.174847] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   77.174849]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   77.174852] ata1.00: status: { DRDY ERR }
[   77.174855] ata1.00: error: { ABRT }
[   77.196758] ata1.00: configured for UDMA/100
[   77.196795] ata1: EH complete
[   77.343780] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   77.343787] ata1.00: BMDMA2 stat 0x82d0009
[   77.343795] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   77.343797]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   77.343801] ata1.00: status: { DRDY ERR }
[   77.343803] ata1.00: error: { ABRT }
[   77.364692] ata1.00: configured for UDMA/100
[   77.364709] ata1: EH complete
[   77.511664] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   77.511667] ata1.00: BMDMA2 stat 0x82d0009
[   77.511673] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   77.511675]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   77.511678] ata1.00: status: { DRDY ERR }
[   77.511681] ata1.00: error: { ABRT }
[   77.532705] ata1.00: configured for UDMA/100
[   77.532715] ata1: EH complete
[   77.679692] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   77.679697] ata1.00: BMDMA2 stat 0x82d0009
[   77.679703] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   77.679705]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   77.679709] ata1.00: status: { DRDY ERR }
[   77.679711] ata1.00: error: { ABRT }
[   77.700697] ata1.00: configured for UDMA/100
[   77.700711] ata1: EH complete
[   77.847693] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   77.847696] ata1.00: BMDMA2 stat 0x82d0009
[   77.847702] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   77.847704]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   77.847708] ata1.00: status: { DRDY ERR }
[   77.847710] ata1.00: error: { ABRT }
[   77.868707] ata1.00: configured for UDMA/100
[   77.868719] ata1: EH complete
[   78.015709] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.015713] ata1.00: BMDMA2 stat 0x82d0009
[   78.015721] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   78.015723]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   78.015726] ata1.00: status: { DRDY ERR }
[   78.015729] ata1.00: error: { ABRT }
[   78.036702] ata1.00: configured for UDMA/100
[   78.036718] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   78.036723] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   78.036729] Descriptor sense data with sense descriptors (in hex):
[   78.036731]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   78.036741]         00 00 00 00 
[   78.036746] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   78.036751] end_request: I/O error, dev sda, sector 0
[   78.036756] Buffer I/O error on device sda, logical block 0
[   78.036762] Buffer I/O error on device sda, logical block 1
[   78.036765] Buffer I/O error on device sda, logical block 2
[   78.036768] Buffer I/O error on device sda, logical block 3
[   78.036777] ata1: EH complete
[   78.183821] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.183824] ata1.00: BMDMA2 stat 0x82d0009
[   78.183830] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   78.183832]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   78.183835] ata1.00: status: { DRDY ERR }
[   78.183838] ata1.00: error: { ABRT }
[   78.204708] ata1.00: configured for UDMA/100
[   78.204720] ata1: EH complete
[   78.351726] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.351729] ata1.00: BMDMA2 stat 0x82d0009
[   78.351735] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   78.351737]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   78.351741] ata1.00: status: { DRDY ERR }
[   78.351743] ata1.00: error: { ABRT }
[   78.372705] ata1.00: configured for UDMA/100
[   78.372716] ata1: EH complete
[   78.519737] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.519740] ata1.00: BMDMA2 stat 0x82d0009
[   78.519746] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   78.519748]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   78.519751] ata1.00: status: { DRDY ERR }
[   78.519753] ata1.00: error: { ABRT }
[   78.540702] ata1.00: configured for UDMA/100
[   78.540712] ata1: EH complete
[   78.687645] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.687648] ata1.00: BMDMA2 stat 0x82d0009
[   78.687654] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   78.687656]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   78.687659] ata1.00: status: { DRDY ERR }
[   78.687661] ata1.00: error: { ABRT }
[   78.708692] ata1.00: configured for UDMA/100
[   78.708702] ata1: EH complete
[   78.855658] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.855661] ata1.00: BMDMA2 stat 0x82d0009
[   78.855666] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   78.855668]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   78.855671] ata1.00: status: { DRDY ERR }
[   78.855674] ata1.00: error: { ABRT }
[   78.876700] ata1.00: configured for UDMA/100
[   78.876710] ata1: EH complete
[   79.023670] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   79.023673] ata1.00: BMDMA2 stat 0x82d0009
[   79.023678] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   79.023680]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   79.023683] ata1.00: status: { DRDY ERR }
[   79.023686] ata1.00: error: { ABRT }
[   79.044696] ata1.00: configured for UDMA/100
[   79.044705] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   79.044709] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   79.044714] Descriptor sense data with sense descriptors (in hex):
[   79.044717]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   79.044727]         00 00 00 00 
[   79.044731] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   79.044736] end_request: I/O error, dev sda, sector 0
[   79.044740] Buffer I/O error on device sda, logical block 0
[   79.044752] ata1: EH complete
[   79.045906] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[   79.045948] sd 0:0:0:0: [sda] Write Protect is off
[   79.045951] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   79.045983] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.046019] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[   79.046036] sd 0:0:0:0: [sda] Write Protect is off
[   79.046039] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   79.046067] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   97.792566] udev: starting version 141
[   98.552655] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   98.552662] ata1.00: BMDMA2 stat 0x82d0009
[   98.552670] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   98.552672]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   98.552676] ata1.00: status: { DRDY ERR }
[   98.552678] ata1.00: error: { ABRT }
[   98.576705] ata1.00: configured for UDMA/100
[   98.576728] ata1: EH complete
[   98.723683] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   98.723689] ata1.00: BMDMA2 stat 0x82d0009
[   98.723696] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   98.723698]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   98.723702] ata1.00: status: { DRDY ERR }
[   98.723704] ata1.00: error: { ABRT }
[   98.744695] ata1.00: configured for UDMA/100
[   98.744706] ata1: EH complete
[   98.891691] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   98.891695] ata1.00: BMDMA2 stat 0x82d0009
[   98.891701] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   98.891703]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   98.891707] ata1.00: status: { DRDY ERR }
[   98.891709] ata1.00: error: { ABRT }
[   98.912702] ata1.00: configured for UDMA/100
[   98.912714] ata1: EH complete
[   99.059701] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.059704] ata1.00: BMDMA2 stat 0x82d0009
[   99.059710] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   99.059712]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   99.059715] ata1.00: status: { DRDY ERR }
[   99.059718] ata1.00: error: { ABRT }
[   99.080700] ata1.00: configured for UDMA/100
[   99.080710] ata1: EH complete
[   99.180048] cfg80211: Calling CRDA to update world regulatory domain
[   99.227735] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.227741] ata1.00: BMDMA2 stat 0x82d0009
[   99.227749] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   99.227751]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   99.227755] ata1.00: status: { DRDY ERR }
[   99.227757] ata1.00: error: { ABRT }
[   99.248761] ata1.00: configured for UDMA/100
[   99.248777] ata1: EH complete
[   99.395744] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.395751] ata1.00: BMDMA2 stat 0x82d0009
[   99.395759] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   99.395761]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   99.395765] ata1.00: status: { DRDY ERR }
[   99.395767] ata1.00: error: { ABRT }
[   99.416703] ata1.00: configured for UDMA/100
[   99.416724] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   99.416730] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   99.416736] Descriptor sense data with sense descriptors (in hex):
[   99.416738]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   99.416749]         00 00 00 00 
[   99.416753] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[   99.416758] end_request: I/O error, dev sda, sector 0
[   99.416764] Buffer I/O error on device sda, logical block 0
[   99.416770] Buffer I/O error on device sda, logical block 1
[   99.416774] Buffer I/O error on device sda, logical block 2
[   99.416777] Buffer I/O error on device sda, logical block 3
[   99.416795] ata1: EH complete
[   99.563850] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.563856] ata1.00: BMDMA2 stat 0x82d0009
[   99.563862] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   99.563864]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   99.563868] ata1.00: status: { DRDY ERR }
[   99.563870] ata1.00: error: { ABRT }
[   99.584701] ata1.00: configured for UDMA/100
[   99.584715] ata1: EH complete
[   99.690383] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   99.731770] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.731777] ata1.00: BMDMA2 stat 0x82d0009
[   99.731785] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   99.731787]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   99.731791] ata1.00: status: { DRDY ERR }
[   99.731793] ata1.00: error: { ABRT }
[   99.746773] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8450, revision 0
[   99.757044] ata1.00: configured for UDMA/100
[   99.757075] ata1: EH complete
[   99.904053] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.904059] ata1.00: BMDMA2 stat 0x82d0009
[   99.904067] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   99.904069]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[   99.904073] ata1.00: status: { DRDY ERR }
[   99.904075] ata1.00: error: { ABRT }
[   99.928779] ata1.00: configured for UDMA/100
[   99.928813] ata1: EH complete
[   99.983838] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  100.073971] Linux agpgart interface v0.103
[  100.076067] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  100.076074] ata1.00: BMDMA2 stat 0x82d0009
[  100.076082] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  100.076084]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  100.076088] ata1.00: status: { DRDY ERR }
[  100.076090] ata1.00: error: { ABRT }
[  100.100740] ata1.00: configured for UDMA/100
[  100.100773] ata1: EH complete
[  100.247782] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  100.247789] ata1.00: BMDMA2 stat 0x82d0009
[  100.247797] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  100.247799]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  100.247802] ata1.00: status: { DRDY ERR }
[  100.247805] ata1.00: error: { ABRT }
[  100.268734] ata1.00: configured for UDMA/100
[  100.268750] ata1: EH complete
[  100.415788] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  100.415793] ata1.00: BMDMA2 stat 0x82d0009
[  100.415800] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  100.415801]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  100.415805] ata1.00: status: { DRDY ERR }
[  100.415807] ata1.00: error: { ABRT }
[  100.436707] ata1.00: configured for UDMA/100
[  100.436723] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  100.436729] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  100.436735] Descriptor sense data with sense descriptors (in hex):
[  100.436738]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  100.436748]         00 00 00 00 
[  100.436752] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  100.436757] end_request: I/O error, dev sda, sector 0
[  100.436762] Buffer I/O error on device sda, logical block 0
[  100.436775] ata1: EH complete
[  100.437352] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  100.437388] sd 0:0:0:0: [sda] Write Protect is off
[  100.437391] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  100.437422] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  100.437461] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  100.437478] sd 0:0:0:0: [sda] Write Protect is off
[  100.437481] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  100.437509] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  100.846183] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[  100.977629] acpi device:21: registered as cooling_device1
[  100.977982] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/device:1f/input/input7
[  100.980644] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  101.259947] cfg80211: World regulatory domain updated:
[  101.259955]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  101.259959]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  101.259962]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  101.259965]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  101.259968]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  101.259971]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  101.273505] yenta_cardbus 0000:09:04.0: CardBus bridge found [1179:ff00]
[  101.273545] yenta_cardbus 0000:09:04.0: Using CSCINT to route CSC interrupts to PCI
[  101.273548] yenta_cardbus 0000:09:04.0: Routing CardBus interrupts to PCI
[  101.273557] yenta_cardbus 0000:09:04.0: TI: mfunc 0x00111c12, devctl 0x44
[  101.467142] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[  101.495984] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[  101.508803] yenta_cardbus 0000:09:04.0: ISA IRQ mask 0x0ef8, PCI irq 17
[  101.508813] yenta_cardbus 0000:09:04.0: Socket status: 30000006
[  101.508822] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[  101.508826] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[  101.509155] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[  101.509205] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[  101.513051] ath5k_pci 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  101.513064] ath5k_pci 0000:02:00.0: setting latency timer to 64
[  101.513210] ath5k_pci 0000:02:00.0: registered as 'phy0'
[  101.606388] phy0: Selected rate control algorithm 'pid'
[  101.743361] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa0, PHY: 0x61)
[  101.928514] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  102.124760] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[  102.127245] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[  102.128312] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[  102.129172] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[  102.130102] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[  113.141895] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  113.141902] ata1.00: BMDMA2 stat 0x82d0009
[  113.141910] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  113.141912]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  113.141916] ata1.00: status: { DRDY ERR }
[  113.141919] ata1.00: error: { ABRT }
[  113.167939] ata1.00: configured for UDMA/100
[  113.167969] ata1: EH complete
[  113.315016] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  113.315023] ata1.00: BMDMA2 stat 0x82d0009
[  113.315031] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  113.315033]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  113.315037] ata1.00: status: { DRDY ERR }
[  113.315039] ata1.00: error: { ABRT }
[  113.336703] ata1.00: configured for UDMA/100
[  113.336725] ata1: EH complete
[  113.483736] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  113.483739] ata1.00: BMDMA2 stat 0x82d0009
[  113.483745] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  113.483747]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  113.483751] ata1.00: status: { DRDY ERR }
[  113.483753] ata1.00: error: { ABRT }
[  113.504701] ata1.00: configured for UDMA/100
[  113.504714] ata1: EH complete
[  113.651747] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  113.651751] ata1.00: BMDMA2 stat 0x82d0009
[  113.651757] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  113.651758]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  113.651762] ata1.00: status: { DRDY ERR }
[  113.651764] ata1.00: error: { ABRT }
[  113.672701] ata1.00: configured for UDMA/100
[  113.672713] ata1: EH complete
[  113.819653] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  113.819656] ata1.00: BMDMA2 stat 0x82d0009
[  113.819662] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  113.819664]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  113.819668] ata1.00: status: { DRDY ERR }
[  113.819670] ata1.00: error: { ABRT }
[  113.840702] ata1.00: configured for UDMA/100
[  113.840714] ata1: EH complete
[  113.987667] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  113.987670] ata1.00: BMDMA2 stat 0x82d0009
[  113.987676] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  113.987678]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  113.987681] ata1.00: status: { DRDY ERR }
[  113.987684] ata1.00: error: { ABRT }
[  114.008696] ata1.00: configured for UDMA/100
[  114.008717] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  114.008722] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  114.008728] Descriptor sense data with sense descriptors (in hex):
[  114.008731]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  114.008741]         00 00 00 00 
[  114.008745] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  114.008750] end_request: I/O error, dev sda, sector 0
[  114.008756] Buffer I/O error on device sda, logical block 0
[  114.008764] Buffer I/O error on device sda, logical block 1
[  114.008767] Buffer I/O error on device sda, logical block 2
[  114.008770] Buffer I/O error on device sda, logical block 3
[  114.008787] ata1: EH complete
[  114.155782] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  114.155786] ata1.00: BMDMA2 stat 0x82d0009
[  114.155792] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  114.155793]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  114.155797] ata1.00: status: { DRDY ERR }
[  114.155799] ata1.00: error: { ABRT }
[  114.176705] ata1.00: configured for UDMA/100
[  114.176717] ata1: EH complete
[  114.323690] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  114.323694] ata1.00: BMDMA2 stat 0x82d0009
[  114.323700] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  114.323701]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  114.323705] ata1.00: status: { DRDY ERR }
[  114.323707] ata1.00: error: { ABRT }
[  114.344702] ata1.00: configured for UDMA/100
[  114.344714] ata1: EH complete
[  114.491703] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  114.491706] ata1.00: BMDMA2 stat 0x82d0009
[  114.491712] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  114.491713]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  114.491717] ata1.00: status: { DRDY ERR }
[  114.491719] ata1.00: error: { ABRT }
[  114.512700] ata1.00: configured for UDMA/100
[  114.512712] ata1: EH complete
[  114.659715] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  114.659718] ata1.00: BMDMA2 stat 0x82d0009
[  114.659724] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  114.659726]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  114.659729] ata1.00: status: { DRDY ERR }
[  114.659732] ata1.00: error: { ABRT }
[  114.680703] ata1.00: configured for UDMA/100
[  114.680715] ata1: EH complete
[  114.827727] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  114.827730] ata1.00: BMDMA2 stat 0x82d0009
[  114.827736] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  114.827738]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  114.827741] ata1.00: status: { DRDY ERR }
[  114.827744] ata1.00: error: { ABRT }
[  114.848696] ata1.00: configured for UDMA/100
[  114.848708] ata1: EH complete
[  114.995739] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  114.995743] ata1.00: BMDMA2 stat 0x82d0009
[  114.995749] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  114.995750]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  114.995754] ata1.00: status: { DRDY ERR }
[  114.995756] ata1.00: error: { ABRT }
[  115.016703] ata1.00: configured for UDMA/100
[  115.016715] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  115.016719] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  115.016724] Descriptor sense data with sense descriptors (in hex):
[  115.016726]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  115.016736]         00 00 00 00 
[  115.016740] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  115.016745] end_request: I/O error, dev sda, sector 0
[  115.016750] Buffer I/O error on device sda, logical block 0
[  115.016763] ata1: EH complete
[  115.017814] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  115.017854] sd 0:0:0:0: [sda] Write Protect is off
[  115.017857] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  115.017889] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  115.017926] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  115.017943] sd 0:0:0:0: [sda] Write Protect is off
[  115.017946] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  115.017974] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  115.814915] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  115.814920] Bluetooth: BNEP filters: protocol multicast
[  115.873475] Bridge firewalling registered
[  121.369404] pci 0000:01:05.0: power state changed by ACPI to D0
[  121.369420] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  121.682828] [drm] Initialized drm 1.1.0 20060810
[  122.123112] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[  123.517526] lp: driver loaded but no devices found
[  123.566400] ppdev: user-space parallel port driver
[  123.616624] [drm] Setting GART location based on new memory map
[  123.617268] [drm] Loading R300 Microcode
[  123.617308] [drm] Num pipes: 4
[  123.617315] [drm] writeback test succeeded in 1 usecs
[  125.977670] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  126.008123] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  133.769801] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  133.769809] ata1.00: BMDMA2 stat 0x82d0009
[  133.769817] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  133.769819]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  133.769823] ata1.00: status: { DRDY ERR }
[  133.769825] ata1.00: error: { ABRT }
[  133.792762] ata1.00: configured for UDMA/100
[  133.792777] ata1: EH complete
[  133.939885] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  133.939892] ata1.00: BMDMA2 stat 0x82d0009
[  133.939901] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  133.939903]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  133.939906] ata1.00: status: { DRDY ERR }
[  133.939909] ata1.00: error: { ABRT }
[  133.967790] ata1.00: configured for UDMA/100
[  133.967824] ata1: EH complete
[  134.115238] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  134.115245] ata1.00: BMDMA2 stat 0x82d0009
[  134.115253] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  134.115255]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  134.115259] ata1.00: status: { DRDY ERR }
[  134.115261] ata1.00: error: { ABRT }
[  134.136792] ata1.00: configured for UDMA/100
[  134.136810] ata1: EH complete
[  134.283916] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  134.283922] ata1.00: BMDMA2 stat 0x82d0009
[  134.283929] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  134.283931]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  134.283935] ata1.00: status: { DRDY ERR }
[  134.283937] ata1.00: error: { ABRT }
[  134.308798] ata1.00: configured for UDMA/100
[  134.308812] ata1: EH complete
[  134.459584] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  134.459590] ata1.00: BMDMA2 stat 0x82d0009
[  134.459598] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  134.459599]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  134.459603] ata1.00: status: { DRDY ERR }
[  134.459606] ata1.00: error: { ABRT }
[  134.480732] ata1.00: configured for UDMA/100
[  134.480754] ata1: EH complete
[  134.627848] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  134.627853] ata1.00: BMDMA2 stat 0x82d0009
[  134.627859] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  134.627861]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  134.627864] ata1.00: status: { DRDY ERR }
[  134.627867] ata1.00: error: { ABRT }
[  134.648771] ata1.00: configured for UDMA/100
[  134.648792] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  134.648797] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  134.648803] Descriptor sense data with sense descriptors (in hex):
[  134.648806]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  134.648816]         00 00 00 00 
[  134.648820] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  134.648826] end_request: I/O error, dev sda, sector 0
[  134.648831] Buffer I/O error on device sda, logical block 0
[  134.648836] Buffer I/O error on device sda, logical block 1
[  134.648839] Buffer I/O error on device sda, logical block 2
[  134.648842] Buffer I/O error on device sda, logical block 3
[  134.648852] ata1: EH complete
[  134.795993] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  134.796000] ata1.00: BMDMA2 stat 0x82d0009
[  134.796030] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  134.796032]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  134.796036] ata1.00: status: { DRDY ERR }
[  134.796038] ata1.00: error: { ABRT }
[  134.820730] ata1.00: configured for UDMA/100
[  134.820750] ata1: EH complete
[  134.967841] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  134.967847] ata1.00: BMDMA2 stat 0x82d0009
[  134.967855] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  134.967857]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  134.967861] ata1.00: status: { DRDY ERR }
[  134.967863] ata1.00: error: { ABRT }
[  134.992767] ata1.00: configured for UDMA/100
[  134.992786] ata1: EH complete
[  135.139833] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  135.139840] ata1.00: BMDMA2 stat 0x82d0009
[  135.139848] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  135.139850]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  135.139854] ata1.00: status: { DRDY ERR }
[  135.139856] ata1.00: error: { ABRT }
[  135.160736] ata1.00: configured for UDMA/100
[  135.160755] ata1: EH complete
[  135.307846] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  135.307853] ata1.00: BMDMA2 stat 0x82d0009
[  135.307861] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  135.307863]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  135.307866] ata1.00: status: { DRDY ERR }
[  135.307869] ata1.00: error: { ABRT }
[  135.332749] ata1.00: configured for UDMA/100
[  135.332772] ata1: EH complete
[  135.479817] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  135.479823] ata1.00: BMDMA2 stat 0x82d0009
[  135.479832] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  135.479833]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  135.479837] ata1.00: status: { DRDY ERR }
[  135.479840] ata1.00: error: { ABRT }
[  135.504277] ata1.00: configured for UDMA/100
[  135.504313] ata1: EH complete
[  135.651357] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  135.651364] ata1.00: BMDMA2 stat 0x82d0009
[  135.651372] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  135.651374]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  135.651378] ata1.00: status: { DRDY ERR }
[  135.651380] ata1.00: error: { ABRT }
[  135.672758] ata1.00: configured for UDMA/100
[  135.672780] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  135.672786] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  135.672792] Descriptor sense data with sense descriptors (in hex):
[  135.672795]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  135.672805]         00 00 00 00 
[  135.672809] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  135.672814] end_request: I/O error, dev sda, sector 0
[  135.672820] Buffer I/O error on device sda, logical block 0
[  135.672841] ata1: EH complete
[  135.674229] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  135.675756] sd 0:0:0:0: [sda] Write Protect is off
[  135.675761] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  135.675824] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  135.675865] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  135.675882] sd 0:0:0:0: [sda] Write Protect is off
[  135.675885] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  135.675913] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  136.900045] eth0: no IPv6 routers present
[  221.400057] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  221.557057] usb 1-1: configuration #1 chosen from 1 choice
[  221.669995] Initializing USB Mass Storage driver...
[  221.670451] scsi4 : SCSI emulation for USB Mass Storage devices
[  221.670572] usbcore: registered new interface driver usb-storage
[  221.670576] USB Mass Storage support registered.
[  221.697314] usb-storage: device found at 4
[  221.697319] usb-storage: waiting for device to settle before scanning
[  226.696329] usb-storage: device scan complete
[  226.697429] scsi 4:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[  226.736912] sd 4:0:0:0: [sdb] 1981440 512-byte hardware sectors: (1.01 GB/967 MiB)
[  226.737861] sd 4:0:0:0: [sdb] Write Protect is off
[  226.737866] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  226.737869] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  226.742166] sd 4:0:0:0: [sdb] 1981440 512-byte hardware sectors: (1.01 GB/967 MiB)
[  226.743024] sd 4:0:0:0: [sdb] Write Protect is off
[  226.743027] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  226.743030] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  226.743038]  sdb: sdb1
[  226.847611] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  226.847706] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  402.244499] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  402.244504] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  402.244508] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[  402.397437] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  402.397443] ata1.00: BMDMA2 stat 0x82d0009
[  402.397452] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  402.397454]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  402.397457] ata1.00: status: { DRDY ERR }
[  402.397460] ata1.00: error: { ABRT }
[  402.420733] ata1.00: configured for UDMA/100
[  402.420751] ata1: EH complete
[  402.567822] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  402.567825] ata1.00: BMDMA2 stat 0x82d0009
[  402.567831] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  402.567833]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  402.567836] ata1.00: status: { DRDY ERR }
[  402.567839] ata1.00: error: { ABRT }
[  402.588749] ata1.00: configured for UDMA/100
[  402.588762] ata1: EH complete
[  402.735834] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  402.735837] ata1.00: BMDMA2 stat 0x82d0009
[  402.735843] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  402.735845]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  402.735848] ata1.00: status: { DRDY ERR }
[  402.735851] ata1.00: error: { ABRT }
[  402.756732] ata1.00: configured for UDMA/100
[  402.756744] ata1: EH complete
[  402.903752] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  402.903758] ata1.00: BMDMA2 stat 0x82d0009
[  402.903766] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  402.903768]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  402.903772] ata1.00: status: { DRDY ERR }
[  402.903774] ata1.00: error: { ABRT }
[  402.924756] ata1.00: configured for UDMA/100
[  402.924777] ata1: EH complete
[  403.071862] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  403.071866] ata1.00: BMDMA2 stat 0x82d0009
[  403.071872] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  403.071874]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  403.071877] ata1.00: status: { DRDY ERR }
[  403.071880] ata1.00: error: { ABRT }
[  403.096754] ata1.00: configured for UDMA/100
[  403.096766] ata1: EH complete
[  403.243809] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  403.243813] ata1.00: BMDMA2 stat 0x82d0009
[  403.243818] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  403.243820]          res 51/04:20:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  403.243824] ata1.00: status: { DRDY ERR }
[  403.243826] ata1.00: error: { ABRT }
[  403.264875] ata1.00: configured for UDMA/100
[  403.264894] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  403.264899] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  403.264905] Descriptor sense data with sense descriptors (in hex):
[  403.264908]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  403.264918]         00 00 00 00 
[  403.264922] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  403.264928] end_request: I/O error, dev sda, sector 0
[  403.264934] Buffer I/O error on device sda, logical block 0
[  403.264941] Buffer I/O error on device sda, logical block 1
[  403.264945] Buffer I/O error on device sda, logical block 2
[  403.264948] Buffer I/O error on device sda, logical block 3
[  403.264960] ata1: EH complete
[  403.265086] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  403.265107] sd 0:0:0:0: [sda] Write Protect is off
[  403.265110] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  403.265141] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  403.265174] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  403.265191] sd 0:0:0:0: [sda] Write Protect is off
[  403.265194] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  403.265222] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  403.412239] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  403.412243] ata1.00: BMDMA2 stat 0x82d0009
[  403.412249] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  403.412250]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  403.412254] ata1.00: status: { DRDY ERR }
[  403.412257] ata1.00: error: { ABRT }
[  403.436749] ata1.00: configured for UDMA/100
[  403.436778] ata1: EH complete
[  403.583798] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  403.583803] ata1.00: BMDMA2 stat 0x82d0009
[  403.583811] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  403.583812]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  403.583816] ata1.00: status: { DRDY ERR }
[  403.583819] ata1.00: error: { ABRT }
[  403.604757] ata1.00: configured for UDMA/100
[  403.604769] ata1: EH complete
[  403.751809] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  403.751813] ata1.00: BMDMA2 stat 0x82d0009
[  403.751819] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  403.751820]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  403.751824] ata1.00: status: { DRDY ERR }
[  403.751826] ata1.00: error: { ABRT }
[  403.772734] ata1.00: configured for UDMA/100
[  403.772745] ata1: EH complete
[  403.919730] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  403.919733] ata1.00: BMDMA2 stat 0x82d0009
[  403.919739] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  403.919741]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  403.919744] ata1.00: status: { DRDY ERR }
[  403.919747] ata1.00: error: { ABRT }
[  403.940730] ata1.00: configured for UDMA/100
[  403.940742] ata1: EH complete
[  404.087850] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  404.087856] ata1.00: BMDMA2 stat 0x82d0009
[  404.087864] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  404.087865]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  404.087869] ata1.00: status: { DRDY ERR }
[  404.087872] ata1.00: error: { ABRT }
[  404.112732] ata1.00: configured for UDMA/100
[  404.112752] ata1: EH complete
[  404.259811] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  404.259814] ata1.00: BMDMA2 stat 0x82d0009
[  404.259820] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  404.259822]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  404.259825] ata1.00: status: { DRDY ERR }
[  404.259828] ata1.00: error: { ABRT }
[  404.280744] ata1.00: configured for UDMA/100
[  404.280762] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  404.280767] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  404.280773] Descriptor sense data with sense descriptors (in hex):
[  404.280775]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  404.280786]         00 00 00 00 
[  404.280790] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  404.280795] end_request: I/O error, dev sda, sector 0
[  404.280801] Buffer I/O error on device sda, logical block 0
[  404.280822] ata1: EH complete
[  404.280880] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  404.280901] sd 0:0:0:0: [sda] Write Protect is off
[  404.280904] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  404.280935] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  404.280971] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  404.280988] sd 0:0:0:0: [sda] Write Protect is off
[  404.280991] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  404.281019] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  404.428139] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  404.428143] ata1.00: BMDMA2 stat 0x82d0009
[  404.428149] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  404.428151]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  404.428154] ata1.00: status: { DRDY ERR }
[  404.428157] ata1.00: error: { ABRT }
[  404.452736] ata1.00: configured for UDMA/100
[  404.452751] ata1: EH complete
[  404.599791] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  404.599794] ata1.00: BMDMA2 stat 0x82d0009
[  404.599801] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  404.599802]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  404.599806] ata1.00: status: { DRDY ERR }
[  404.599808] ata1.00: error: { ABRT }
[  404.620729] ata1.00: configured for UDMA/100
[  404.620741] ata1: EH complete
[  404.767836] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  404.767841] ata1.00: BMDMA2 stat 0x82d0009
[  404.767849] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  404.767851]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  404.767854] ata1.00: status: { DRDY ERR }
[  404.767857] ata1.00: error: { ABRT }
[  404.788749] ata1.00: configured for UDMA/100
[  404.788769] ata1: EH complete
[  404.935804] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  404.935807] ata1.00: BMDMA2 stat 0x82d0009
[  404.935813] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  404.935815]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  404.935819] ata1.00: status: { DRDY ERR }
[  404.935821] ata1.00: error: { ABRT }
[  404.956735] ata1.00: configured for UDMA/100
[  404.956746] ata1: EH complete
[  405.103731] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  405.103734] ata1.00: BMDMA2 stat 0x82d0009
[  405.103740] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  405.103742]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  405.103746] ata1.00: status: { DRDY ERR }
[  405.103748] ata1.00: error: { ABRT }
[  405.124755] ata1.00: configured for UDMA/100
[  405.124768] ata1: EH complete
[  405.271865] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  405.271871] ata1.00: BMDMA2 stat 0x82d0009
[  405.271879] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  405.271880]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  405.271884] ata1.00: status: { DRDY ERR }
[  405.271887] ata1.00: error: { ABRT }
[  405.296752] ata1.00: configured for UDMA/100
[  405.296769] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  405.296775] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  405.296781] Descriptor sense data with sense descriptors (in hex):
[  405.296784]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  405.296794]         00 00 00 00 
[  405.296798] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  405.296804] end_request: I/O error, dev sda, sector 0
[  405.296809] Buffer I/O error on device sda, logical block 0
[  405.296827] ata1: EH complete
[  405.296873] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  405.296894] sd 0:0:0:0: [sda] Write Protect is off
[  405.296897] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  405.296927] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  405.296961] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  405.296978] sd 0:0:0:0: [sda] Write Protect is off
[  405.296981] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  405.297009] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  405.444113] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  405.444117] ata1.00: BMDMA2 stat 0x82d0009
[  405.444123] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  405.444124]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  405.444128] ata1.00: status: { DRDY ERR }
[  405.444130] ata1.00: error: { ABRT }
[  405.468749] ata1.00: configured for UDMA/100
[  405.468760] ata1: EH complete
[  405.615789] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  405.615792] ata1.00: BMDMA2 stat 0x82d0009
[  405.615798] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  405.615800]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  405.615803] ata1.00: status: { DRDY ERR }
[  405.615806] ata1.00: error: { ABRT }
[  405.636731] ata1.00: configured for UDMA/100
[  405.636743] ata1: EH complete
[  405.783781] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  405.783785] ata1.00: BMDMA2 stat 0x82d0009
[  405.783791] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  405.783792]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  405.783796] ata1.00: status: { DRDY ERR }
[  405.783798] ata1.00: error: { ABRT }
[  405.804756] ata1.00: configured for UDMA/100
[  405.804769] ata1: EH complete
[  405.951832] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  405.951838] ata1.00: BMDMA2 stat 0x82d0009
[  405.951846] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  405.951847]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  405.951851] ata1.00: status: { DRDY ERR }
[  405.951854] ata1.00: error: { ABRT }
[  405.972736] ata1.00: configured for UDMA/100
[  405.972757] ata1: EH complete
[  406.119825] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  406.119829] ata1.00: BMDMA2 stat 0x82d0009
[  406.119835] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  406.119836]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  406.119840] ata1.00: status: { DRDY ERR }
[  406.119842] ata1.00: error: { ABRT }
[  406.140731] ata1.00: configured for UDMA/100
[  406.140742] ata1: EH complete
[  406.287817] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  406.287820] ata1.00: BMDMA2 stat 0x82d0009
[  406.287826] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  406.287828]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  406.287831] ata1.00: status: { DRDY ERR }
[  406.287834] ata1.00: error: { ABRT }
[  406.308745] ata1.00: configured for UDMA/100
[  406.308763] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  406.308768] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  406.308774] Descriptor sense data with sense descriptors (in hex):
[  406.308777]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  406.308787]         00 00 00 00 
[  406.308791] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  406.308796] end_request: I/O error, dev sda, sector 0
[  406.308802] Buffer I/O error on device sda, logical block 0
[  406.308823] ata1: EH complete
[  406.455967] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  406.455973] ata1.00: BMDMA2 stat 0x82d0009
[  406.455981] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  406.455983]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  406.455987] ata1.00: status: { DRDY ERR }
[  406.455989] ata1.00: error: { ABRT }
[  406.480743] ata1.00: configured for UDMA/100
[  406.480764] ata1: EH complete
[  406.627800] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  406.627804] ata1.00: BMDMA2 stat 0x82d0009
[  406.627810] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  406.627812]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  406.627815] ata1.00: status: { DRDY ERR }
[  406.627818] ata1.00: error: { ABRT }
[  406.648732] ata1.00: configured for UDMA/100
[  406.648744] ata1: EH complete
[  406.795824] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  406.795827] ata1.00: BMDMA2 stat 0x82d0009
[  406.795833] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  406.795835]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  406.795839] ata1.00: status: { DRDY ERR }
[  406.795841] ata1.00: error: { ABRT }
[  406.816751] ata1.00: configured for UDMA/100
[  406.816763] ata1: EH complete
[  406.963844] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  406.963847] ata1.00: BMDMA2 stat 0x82d0009
[  406.963853] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  406.963855]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  406.963858] ata1.00: status: { DRDY ERR }
[  406.963861] ata1.00: error: { ABRT }
[  406.984731] ata1.00: configured for UDMA/100
[  406.984742] ata1: EH complete
[  407.131759] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  407.131764] ata1.00: BMDMA2 stat 0x82d0009
[  407.131772] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  407.131774]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  407.131777] ata1.00: status: { DRDY ERR }
[  407.131780] ata1.00: error: { ABRT }
[  407.152757] ata1.00: configured for UDMA/100
[  407.152778] ata1: EH complete
[  407.299871] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  407.299876] ata1.00: BMDMA2 stat 0x82d0009
[  407.299883] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  407.299885]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  407.299889] ata1.00: status: { DRDY ERR }
[  407.299892] ata1.00: error: { ABRT }
[  407.324957] ata1.00: configured for UDMA/100
[  407.324975] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  407.324980] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  407.324986] Descriptor sense data with sense descriptors (in hex):
[  407.324988]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  407.324998]         00 00 00 00 
[  407.325003] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  407.325008] end_request: I/O error, dev sda, sector 0
[  407.325014] Buffer I/O error on device sda, logical block 0
[  407.325031] ata1: EH complete
[  407.325162] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  407.472175] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  407.472183] ata1.00: BMDMA2 stat 0x82d0009
[  407.472192] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  407.472193]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  407.472197] ata1.00: status: { DRDY ERR }
[  407.472200] ata1.00: error: { ABRT }
[  407.496751] ata1.00: configured for UDMA/100
[  407.496775] ata1: EH complete
[  407.643831] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  407.643837] ata1.00: BMDMA2 stat 0x82d0009
[  407.643845] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  407.643847]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  407.643850] ata1.00: status: { DRDY ERR }
[  407.643853] ata1.00: error: { ABRT }
[  407.664733] ata1.00: configured for UDMA/100
[  407.664754] ata1: EH complete
[  407.811819] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  407.811822] ata1.00: BMDMA2 stat 0x82d0009
[  407.811828] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  407.811830]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  407.811834] ata1.00: status: { DRDY ERR }
[  407.811836] ata1.00: error: { ABRT }
[  407.832756] ata1.00: configured for UDMA/100
[  407.832768] ata1: EH complete
[  407.979813] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  407.979817] ata1.00: BMDMA2 stat 0x82d0009
[  407.979823] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  407.979824]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  407.979828] ata1.00: status: { DRDY ERR }
[  407.979830] ata1.00: error: { ABRT }
[  408.000736] ata1.00: configured for UDMA/100
[  408.000748] ata1: EH complete
[  408.147750] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  408.147754] ata1.00: BMDMA2 stat 0x82d0009
[  408.147761] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  408.147762]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  408.147766] ata1.00: status: { DRDY ERR }
[  408.147768] ata1.00: error: { ABRT }
[  408.168731] ata1.00: configured for UDMA/100
[  408.168744] ata1: EH complete
[  408.315749] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  408.315755] ata1.00: BMDMA2 stat 0x82d0009
[  408.315763] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  408.315764]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  408.315768] ata1.00: status: { DRDY ERR }
[  408.315771] ata1.00: error: { ABRT }
[  408.336749] ata1.00: configured for UDMA/100
[  408.336772] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  408.336777] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  408.336783] Descriptor sense data with sense descriptors (in hex):
[  408.336786]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  408.336796]         00 00 00 00 
[  408.336800] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  408.336806] end_request: I/O error, dev sda, sector 0
[  408.336812] Buffer I/O error on device sda, logical block 0
[  408.336839] ata1: EH complete
[  408.337024] sd 0:0:0:0: [sda] Write Protect is off
[  408.337027] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  408.483953] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  408.483957] ata1.00: BMDMA2 stat 0x82d0009
[  408.483963] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  408.483965]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  408.483968] ata1.00: status: { DRDY ERR }
[  408.483971] ata1.00: error: { ABRT }
[  408.508748] ata1.00: configured for UDMA/100
[  408.508761] ata1: EH complete
[  408.655838] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  408.655842] ata1.00: BMDMA2 stat 0x82d0009
[  408.655847] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  408.655849]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  408.655853] ata1.00: status: { DRDY ERR }
[  408.655855] ata1.00: error: { ABRT }
[  408.676735] ata1.00: configured for UDMA/100
[  408.676746] ata1: EH complete
[  408.823732] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  408.823735] ata1.00: BMDMA2 stat 0x82d0009
[  408.823741] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  408.823743]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  408.823746] ata1.00: status: { DRDY ERR }
[  408.823749] ata1.00: error: { ABRT }
[  408.844758] ata1.00: configured for UDMA/100
[  408.844782] ata1: EH complete
[  408.991863] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  408.991867] ata1.00: BMDMA2 stat 0x82d0009
[  408.991875] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  408.991877]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  408.991880] ata1.00: status: { DRDY ERR }
[  408.991883] ata1.00: error: { ABRT }
[  409.016818] ata1.00: configured for UDMA/100
[  409.016831] ata1: EH complete
[  409.163813] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  409.163816] ata1.00: BMDMA2 stat 0x82d0009
[  409.163822] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  409.163824]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  409.163828] ata1.00: status: { DRDY ERR }
[  409.163830] ata1.00: error: { ABRT }
[  409.184737] ata1.00: configured for UDMA/100
[  409.184748] ata1: EH complete
[  409.331736] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  409.331741] ata1.00: BMDMA2 stat 0x82d0009
[  409.331747] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  409.331748]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  409.331752] ata1.00: status: { DRDY ERR }
[  409.331754] ata1.00: error: { ABRT }
[  409.352754] ata1.00: configured for UDMA/100
[  409.352769] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  409.352774] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  409.352780] Descriptor sense data with sense descriptors (in hex):
[  409.352783]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  409.352793]         00 00 00 00 
[  409.352797] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  409.352803] end_request: I/O error, dev sda, sector 0
[  409.352808] Buffer I/O error on device sda, logical block 0
[  409.352824] ata1: EH complete
[  409.499979] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  409.499985] ata1.00: BMDMA2 stat 0x82d0009
[  409.499993] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  409.499995]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  409.499999] ata1.00: status: { DRDY ERR }
[  409.500022] ata1.00: error: { ABRT }
[  409.524756] ata1.00: configured for UDMA/100
[  409.524776] ata1: EH complete
[  409.671808] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  409.671812] ata1.00: BMDMA2 stat 0x82d0009
[  409.671818] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  409.671819]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  409.671823] ata1.00: status: { DRDY ERR }
[  409.671825] ata1.00: error: { ABRT }
[  409.692733] ata1.00: configured for UDMA/100
[  409.692745] ata1: EH complete
[  409.839736] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  409.839739] ata1.00: BMDMA2 stat 0x82d0009
[  409.839745] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  409.839747]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  409.839750] ata1.00: status: { DRDY ERR }
[  409.839753] ata1.00: error: { ABRT }
[  409.860731] ata1.00: configured for UDMA/100
[  409.860742] ata1: EH complete
[  410.007721] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  410.007724] ata1.00: BMDMA2 stat 0x82d0009
[  410.007730] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  410.007731]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  410.007735] ata1.00: status: { DRDY ERR }
[  410.007737] ata1.00: error: { ABRT }
[  410.030245] ata1.00: configured for UDMA/100
[  410.030275] ata1: EH complete
[  410.177326] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  410.177331] ata1.00: BMDMA2 stat 0x82d0009
[  410.177338] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  410.177340]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  410.177344] ata1.00: status: { DRDY ERR }
[  410.177346] ata1.00: error: { ABRT }
[  410.200730] ata1.00: configured for UDMA/100
[  410.200742] ata1: EH complete
[  410.347727] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  410.347730] ata1.00: BMDMA2 stat 0x82d0009
[  410.347736] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  410.347738]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  410.347741] ata1.00: status: { DRDY ERR }
[  410.347744] ata1.00: error: { ABRT }
[  410.368729] ata1.00: configured for UDMA/100
[  410.368747] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  410.368752] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  410.368759] Descriptor sense data with sense descriptors (in hex):
[  410.368761]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  410.368771]         00 00 00 00 
[  410.368775] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  410.368781] end_request: I/O error, dev sda, sector 0
[  410.368787] Buffer I/O error on device sda, logical block 0
[  410.368807] ata1: EH complete
[  410.368953] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  410.515925] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  410.515929] ata1.00: BMDMA2 stat 0x82d0009
[  410.515935] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  410.515936]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  410.515940] ata1.00: status: { DRDY ERR }
[  410.515942] ata1.00: error: { ABRT }
[  410.540730] ata1.00: configured for UDMA/100
[  410.540742] ata1: EH complete
[  410.687841] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  410.687847] ata1.00: BMDMA2 stat 0x82d0009
[  410.687855] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  410.687856]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  410.687860] ata1.00: status: { DRDY ERR }
[  410.687863] ata1.00: error: { ABRT }
[  410.708744] ata1.00: configured for UDMA/100
[  410.708765] ata1: EH complete
[  410.855805] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  410.855809] ata1.00: BMDMA2 stat 0x82d0009
[  410.855815] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  410.855817]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  410.855820] ata1.00: status: { DRDY ERR }
[  410.855823] ata1.00: error: { ABRT }
[  410.876731] ata1.00: configured for UDMA/100
[  410.876744] ata1: EH complete
[  411.023732] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  411.023736] ata1.00: BMDMA2 stat 0x82d0009
[  411.023742] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  411.023744]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  411.023747] ata1.00: status: { DRDY ERR }
[  411.023750] ata1.00: error: { ABRT }
[  411.044755] ata1.00: configured for UDMA/100
[  411.044767] ata1: EH complete
[  411.191850] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  411.191854] ata1.00: BMDMA2 stat 0x82d0009
[  411.191860] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  411.191861]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  411.191865] ata1.00: status: { DRDY ERR }
[  411.191867] ata1.00: error: { ABRT }
[  411.212730] ata1.00: configured for UDMA/100
[  411.212741] ata1: EH complete
[  411.359754] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  411.359760] ata1.00: BMDMA2 stat 0x82d0009
[  411.359768] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  411.359770]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  411.359773] ata1.00: status: { DRDY ERR }
[  411.359776] ata1.00: error: { ABRT }
[  411.380730] ata1.00: configured for UDMA/100
[  411.380749] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  411.380754] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  411.380760] Descriptor sense data with sense descriptors (in hex):
[  411.380762]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  411.380773]         00 00 00 00 
[  411.380777] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  411.380782] end_request: I/O error, dev sda, sector 0
[  411.380788] Buffer I/O error on device sda, logical block 0
[  411.380804] ata1: EH complete
[  411.527963] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  411.527966] ata1.00: BMDMA2 stat 0x82d0009
[  411.527973] ata1.00: cmd c8/00:08:80:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  411.527974]          res 51/04:08:80:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  411.527978] ata1.00: status: { DRDY ERR }
[  411.527980] ata1.00: error: { ABRT }
[  411.552756] ata1.00: configured for UDMA/100
[  411.552769] ata1: EH complete
[  411.699823] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  411.699827] ata1.00: BMDMA2 stat 0x82d0009
[  411.699833] ata1.00: cmd c8/00:08:80:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  411.699835]          res 51/04:08:80:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  411.699838] ata1.00: status: { DRDY ERR }
[  411.699841] ata1.00: error: { ABRT }
[  411.720734] ata1.00: configured for UDMA/100
[  411.720747] ata1: EH complete
[  411.867765] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  411.867771] ata1.00: BMDMA2 stat 0x82d0009
[  411.867778] ata1.00: cmd c8/00:08:80:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  411.867780]          res 51/04:08:80:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  411.867784] ata1.00: status: { DRDY ERR }
[  411.867786] ata1.00: error: { ABRT }
[  411.888734] ata1.00: configured for UDMA/100
[  411.888754] ata1: EH complete
[  412.035768] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  412.035772] ata1.00: BMDMA2 stat 0x82d0009
[  412.035778] ata1.00: cmd c8/00:08:80:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  412.035779]          res 51/04:08:80:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  412.035783] ata1.00: status: { DRDY ERR }
[  412.035785] ata1.00: error: { ABRT }
[  412.056748] ata1.00: configured for UDMA/100
[  412.056761] ata1: EH complete
[  412.203755] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  412.203758] ata1.00: BMDMA2 stat 0x82d0009
[  412.203764] ata1.00: cmd c8/00:08:80:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  412.203766]          res 51/04:08:80:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  412.203769] ata1.00: status: { DRDY ERR }
[  412.203772] ata1.00: error: { ABRT }
[  412.224732] ata1.00: configured for UDMA/100
[  412.224744] ata1: EH complete
[  412.371777] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  412.371780] ata1.00: BMDMA2 stat 0x82d0009
[  412.371786] ata1.00: cmd c8/00:08:80:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  412.371788]          res 51/04:08:80:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  412.371791] ata1.00: status: { DRDY ERR }
[  412.371794] ata1.00: error: { ABRT }
[  412.392755] ata1.00: configured for UDMA/100
[  412.392773] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  412.392778] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  412.392784] Descriptor sense data with sense descriptors (in hex):
[  412.392787]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  412.392797]         00 00 00 80 
[  412.392801] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  412.392807] end_request: I/O error, dev sda, sector 128
[  412.392813] Buffer I/O error on device sda, logical block 16
[  412.392833] ata1: EH complete
[  412.392970] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  412.539925] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  412.539931] ata1.00: BMDMA2 stat 0x82d0009
[  412.539939] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  412.539940]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  412.539944] ata1.00: status: { DRDY ERR }
[  412.539947] ata1.00: error: { ABRT }
[  412.564753] ata1.00: configured for UDMA/100
[  412.564774] ata1: EH complete
[  412.711855] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  412.711858] ata1.00: BMDMA2 stat 0x82d0009
[  412.711864] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  412.711866]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  412.711870] ata1.00: status: { DRDY ERR }
[  412.711872] ata1.00: error: { ABRT }
[  412.732732] ata1.00: configured for UDMA/100
[  412.732743] ata1: EH complete
[  412.879784] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  412.879787] ata1.00: BMDMA2 stat 0x82d0009
[  412.879793] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  412.879795]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  412.879798] ata1.00: status: { DRDY ERR }
[  412.879801] ata1.00: error: { ABRT }
[  412.900730] ata1.00: configured for UDMA/100
[  412.900741] ata1: EH complete
[  413.047801] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  413.047806] ata1.00: BMDMA2 stat 0x82d0009
[  413.047814] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  413.047816]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  413.047820] ata1.00: status: { DRDY ERR }
[  413.047822] ata1.00: error: { ABRT }
[  413.068740] ata1.00: configured for UDMA/100
[  413.068761] ata1: EH complete
[  413.215791] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  413.215794] ata1.00: BMDMA2 stat 0x82d0009
[  413.215800] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  413.215802]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  413.215806] ata1.00: status: { DRDY ERR }
[  413.215808] ata1.00: error: { ABRT }
[  413.236730] ata1.00: configured for UDMA/100
[  413.236742] ata1: EH complete
[  413.383822] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  413.383826] ata1.00: BMDMA2 stat 0x82d0009
[  413.383832] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  413.383834]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  413.383838] ata1.00: status: { DRDY ERR }
[  413.383840] ata1.00: error: { ABRT }
[  413.404749] ata1.00: configured for UDMA/100
[  413.404766] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  413.404771] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  413.404777] Descriptor sense data with sense descriptors (in hex):
[  413.404780]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  413.404790]         00 00 00 00 
[  413.404794] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  413.404799] end_request: I/O error, dev sda, sector 0
[  413.404805] Buffer I/O error on device sda, logical block 0
[  413.404822] ata1: EH complete
[  413.404953] sd 0:0:0:0: [sda] Write Protect is off
[  413.404956] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  413.551909] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  413.551912] ata1.00: BMDMA2 stat 0x82d0009
[  413.551918] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  413.551920]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  413.551923] ata1.00: status: { DRDY ERR }
[  413.551926] ata1.00: error: { ABRT }
[  413.576745] ata1.00: configured for UDMA/100
[  413.576757] ata1: EH complete
[  413.723821] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  413.723827] ata1.00: BMDMA2 stat 0x82d0009
[  413.723835] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  413.723837]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  413.723840] ata1.00: status: { DRDY ERR }
[  413.723843] ata1.00: error: { ABRT }
[  413.744735] ata1.00: configured for UDMA/100
[  413.744756] ata1: EH complete
[  413.891812] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  413.891815] ata1.00: BMDMA2 stat 0x82d0009
[  413.891821] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  413.891823]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  413.891826] ata1.00: status: { DRDY ERR }
[  413.891829] ata1.00: error: { ABRT }
[  413.912756] ata1.00: configured for UDMA/100
[  413.912768] ata1: EH complete
[  414.059807] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  414.059810] ata1.00: BMDMA2 stat 0x82d0009
[  414.059816] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  414.059818]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  414.059821] ata1.00: status: { DRDY ERR }
[  414.059824] ata1.00: error: { ABRT }
[  414.080732] ata1.00: configured for UDMA/100
[  414.080744] ata1: EH complete
[  414.227732] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  414.227735] ata1.00: BMDMA2 stat 0x82d0009
[  414.227741] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  414.227743]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  414.227746] ata1.00: status: { DRDY ERR }
[  414.227749] ata1.00: error: { ABRT }
[  414.248732] ata1.00: configured for UDMA/100
[  414.248757] ata1: EH complete
[  414.395830] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  414.395834] ata1.00: BMDMA2 stat 0x82d0009
[  414.395842] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  414.395844]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  414.395848] ata1.00: status: { DRDY ERR }
[  414.395850] ata1.00: error: { ABRT }
[  414.416740] ata1.00: configured for UDMA/100
[  414.416760] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  414.416764] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  414.416771] Descriptor sense data with sense descriptors (in hex):
[  414.416773]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  414.416783]         00 00 00 00 
[  414.416787] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  414.416793] end_request: I/O error, dev sda, sector 0
[  414.416799] Buffer I/O error on device sda, logical block 0
[  414.416818] ata1: EH complete
[  414.563952] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  414.563956] ata1.00: BMDMA2 stat 0x82d0009
[  414.563963] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  414.563964]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  414.563968] ata1.00: status: { DRDY ERR }
[  414.563970] ata1.00: error: { ABRT }
[  414.588737] ata1.00: configured for UDMA/100
[  414.588752] ata1: EH complete
[  414.735830] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  414.735833] ata1.00: BMDMA2 stat 0x82d0009
[  414.735839] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  414.735841]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  414.735844] ata1.00: status: { DRDY ERR }
[  414.735847] ata1.00: error: { ABRT }
[  414.756728] ata1.00: configured for UDMA/100
[  414.756740] ata1: EH complete
[  414.903745] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  414.903751] ata1.00: BMDMA2 stat 0x82d0009
[  414.903759] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  414.903761]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  414.903765] ata1.00: status: { DRDY ERR }
[  414.903767] ata1.00: error: { ABRT }
[  414.924750] ata1.00: configured for UDMA/100
[  414.924770] ata1: EH complete
[  415.071854] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  415.071858] ata1.00: BMDMA2 stat 0x82d0009
[  415.071864] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  415.071865]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  415.071869] ata1.00: status: { DRDY ERR }
[  415.071871] ata1.00: error: { ABRT }
[  415.092734] ata1.00: configured for UDMA/100
[  415.092747] ata1: EH complete
[  415.239739] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  415.239742] ata1.00: BMDMA2 stat 0x82d0009
[  415.239748] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  415.239750]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  415.239753] ata1.00: status: { DRDY ERR }
[  415.239756] ata1.00: error: { ABRT }
[  415.260980] ata1.00: configured for UDMA/100
[  415.260993] ata1: EH complete
[  415.408068] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  415.408072] ata1.00: BMDMA2 stat 0x82d0009
[  415.408078] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  415.408080]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  415.408084] ata1.00: status: { DRDY ERR }
[  415.408086] ata1.00: error: { ABRT }
[  415.432750] ata1.00: configured for UDMA/100
[  415.432764] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  415.432769] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  415.432775] Descriptor sense data with sense descriptors (in hex):
[  415.432778]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  415.432788]         00 00 00 00 
[  415.432792] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  415.432798] end_request: I/O error, dev sda, sector 0
[  415.432803] Buffer I/O error on device sda, logical block 0
[  415.432818] ata1: EH complete
[  415.432947] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  415.579975] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  415.579981] ata1.00: BMDMA2 stat 0x82d0009
[  415.579989] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  415.579991]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  415.579995] ata1.00: status: { DRDY ERR }
[  415.579997] ata1.00: error: { ABRT }
[  415.604749] ata1.00: configured for UDMA/100
[  415.604770] ata1: EH complete
[  415.751800] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  415.751803] ata1.00: BMDMA2 stat 0x82d0009
[  415.751809] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  415.751811]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  415.751814] ata1.00: status: { DRDY ERR }
[  415.751817] ata1.00: error: { ABRT }
[  415.772732] ata1.00: configured for UDMA/100
[  415.772745] ata1: EH complete
[  415.919833] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  415.919836] ata1.00: BMDMA2 stat 0x82d0009
[  415.919842] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  415.919844]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  415.919847] ata1.00: status: { DRDY ERR }
[  415.919850] ata1.00: error: { ABRT }
[  415.940756] ata1.00: configured for UDMA/100
[  415.940768] ata1: EH complete
[  416.087845] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  416.087851] ata1.00: BMDMA2 stat 0x82d0009
[  416.087860] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  416.087861]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  416.087865] ata1.00: status: { DRDY ERR }
[  416.087868] ata1.00: error: { ABRT }
[  416.112755] ata1.00: configured for UDMA/100
[  416.112777] ata1: EH complete
[  416.259805] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  416.259808] ata1.00: BMDMA2 stat 0x82d0009
[  416.259814] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  416.259816]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  416.259820] ata1.00: status: { DRDY ERR }
[  416.259822] ata1.00: error: { ABRT }
[  416.280729] ata1.00: configured for UDMA/100
[  416.280741] ata1: EH complete
[  416.427822] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  416.427826] ata1.00: BMDMA2 stat 0x82d0009
[  416.427832] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  416.427833]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  416.427837] ata1.00: status: { DRDY ERR }
[  416.427839] ata1.00: error: { ABRT }
[  416.448731] ata1.00: configured for UDMA/100
[  416.448750] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  416.448755] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  416.448761] Descriptor sense data with sense descriptors (in hex):
[  416.448764]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  416.448774]         00 00 00 00 
[  416.448778] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  416.448783] end_request: I/O error, dev sda, sector 0
[  416.448789] Buffer I/O error on device sda, logical block 0
[  416.448809] ata1: EH complete
[  416.595921] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  416.595925] ata1.00: BMDMA2 stat 0x82d0009
[  416.595931] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  416.595932]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  416.595936] ata1.00: status: { DRDY ERR }
[  416.595938] ata1.00: error: { ABRT }
[  416.620755] ata1.00: configured for UDMA/100
[  416.620768] ata1: EH complete
[  416.767831] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  416.767836] ata1.00: BMDMA2 stat 0x82d0009
[  416.767844] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  416.767846]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  416.767850] ata1.00: status: { DRDY ERR }
[  416.767852] ata1.00: error: { ABRT }
[  416.788737] ata1.00: configured for UDMA/100
[  416.788757] ata1: EH complete
[  416.935799] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  416.935802] ata1.00: BMDMA2 stat 0x82d0009
[  416.935808] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  416.935810]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  416.935813] ata1.00: status: { DRDY ERR }
[  416.935816] ata1.00: error: { ABRT }
[  416.956732] ata1.00: configured for UDMA/100
[  416.956743] ata1: EH complete
[  417.103821] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  417.103825] ata1.00: BMDMA2 stat 0x82d0009
[  417.103831] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  417.103833]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  417.103836] ata1.00: status: { DRDY ERR }
[  417.103839] ata1.00: error: { ABRT }
[  417.124748] ata1.00: configured for UDMA/100
[  417.124761] ata1: EH complete
[  417.271860] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  417.271865] ata1.00: BMDMA2 stat 0x82d0009
[  417.271873] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  417.271875]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  417.271879] ata1.00: status: { DRDY ERR }
[  417.271881] ata1.00: error: { ABRT }
[  417.296742] ata1.00: configured for UDMA/100
[  417.296759] ata1: EH complete
[  417.443798] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  417.443801] ata1.00: BMDMA2 stat 0x82d0009
[  417.443807] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  417.443809]          res 51/04:08:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  417.443813] ata1.00: status: { DRDY ERR }
[  417.443815] ata1.00: error: { ABRT }
[  417.464732] ata1.00: configured for UDMA/100
[  417.464747] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  417.464752] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  417.464758] Descriptor sense data with sense descriptors (in hex):
[  417.464760]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  417.464770]         00 00 00 00 
[  417.464774] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  417.464780] end_request: I/O error, dev sda, sector 0
[  417.464785] Buffer I/O error on device sda, logical block 0
[  417.464800] ata1: EH complete
[  417.465555] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  417.465581] sd 0:0:0:0: [sda] Write Protect is off
[  417.465584] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  417.465615] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  417.465651] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[  417.465668] sd 0:0:0:0: [sda] Write Protect is off
[  417.465671] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  417.465890] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


**LSMOD**
Module                  Size  Used by
nls_iso8859_1          12032  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            82880  1 
binfmt_misc            16776  1 
ppdev                  15620  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
pcmcia                 44748  0 
snd_seq_dummy          10756  0 
ecb                    10752  2 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
joydev                 18368  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
ath5k                 107008  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 ath5k
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
led_class              12036  1 ath5k
ati_agp                14988  0 
video                  25360  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
output                 11008  1 video
soundcore              15200  1 snd
agpgart                42696  2 drm,ati_agp
shpchp                 40212  0 
serio_raw              13316  0 
i2c_piix4              18448  0 
pcspkr                 10496  0 
cfg80211               38032  2 ath5k,mac80211
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
squashfs               46344  1 
aufs                  165924  1 
exportfs               12544  1 aufs
nls_cp437              13696  2 
isofs                  39844  1 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

