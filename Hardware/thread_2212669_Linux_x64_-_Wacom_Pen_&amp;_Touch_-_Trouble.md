---
title: "Linux x64 - Wacom Pen &amp; Touch - Trouble"
date: 2014-03-22
forum: Hardware
---

### Post by john173 on 2014-03-22
[SIZE=3]_**ATTENTION:**_> [SIZE=2]To know i am such a linux newbie user.. only installed some "things" I can't solve almost anything since 2-3 days and am asking your help :( [/SIZE][/SIZE]



 
Hello there i am having hard issues with my Wacom pen & touch ..graphics tablet..I have read all these stuff from SourceForge.net ( [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Downloads](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Downloads) ) the point is that i can not get what i am doing wrong My linux Mint recognize my Tablet 

```
user@user-desktop ~ $ lsusb
```
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 056a:0303 Wacom Co., Ltd 
Bus 003 Device 002: ID 1c4f:0027 SiGma Micro 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 1bcf:0901 Sunplus Innovation Technology Inc. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

But After all nothing else is going good
Not GIMP recognizes 
Nor MyPaint 

I have downloaded the latest from xf86-input-wacom form << [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/) >>following [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

And [https://www.linux.com/learn/tutorials/347367-using-a-bamboo-tablet-with-ubuntu-1004](https://www.linux.com/learn/tutorials/347367-using-a-bamboo-tablet-with-ubuntu-1004) using [http://sourceforge.net/projects/linuxwacom/files/linuxwacom/](http://sourceforge.net/projects/linuxwacom/files/linuxwacom/) ( linuxwacom ) << I know its for bamboo tablet but it shows that it was going well enough Before the step "" Issue the command *make *to build the drivers for your system ""and after 

Although I have read most of the ubuntu forums and other but nothing was like mine's

And if needed:
```
Linux user-desktop 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```


 Linux Mint 16 "Petra" Thanks for your patience:)

---

### Post by pdc on 2014-03-22
Hi John; I suspect there are very few who use these devices; 

what about checking through this Arch guide; as it was last edited 8th March 2014: the ubuntu guides all seem to be about 10.04 and 10.10;

[https://wiki.archlinux.org/index.php/Wacom_Tablet](https://wiki.archlinux.org/index.php/Wacom_Tablet)

first up they suggest the command to copy and paste (to see if kernel drivers are needed)

> [COLOR="#FF0000"]dmesg | grep -i wacom[/COLOR]

and they say to look in > [COLOR="#FF8C00"]/proc/bus/input/devices[/COLOR] ........ you know how to find that?

...........likely all is good ...............

_________________

then they say to install [COLOR="#008000"]xf86-input-wacom[/COLOR] *which in ubuntu is labelled* [COLOR="#006400"]**xserver-xorg-input-wacom**[/COLOR] so use synaptic or your package manager to check: ours is already installed ...... do I sense you had trouble "making" the tar.gaz version from sourceforge?

_____________

My reading of this page 

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Downloads](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Downloads)

is:

1) **kernel driver**: *[COLOR="#EE82EE"]only install if your tablet is not recognized as an input device by the system[/COLOR]*. (So you need to do the dmesg as above to work that out ..)
2) **xf86-input-wacom** (aka xserver-xorg-input-wacom in ubuntu/mint) *[COLOR="#EE82EE"]only install if your tablet is recognized but missing functionality[/COLOR]*.
3) **libwacom** *[COLOR="#EE82EE"]only install if your tablet is not recognized by the control panel[/COLOR]*. (it is installed in our mint system as default)

_____________________________

so to cover the above, the dmesg command will tell if 1) is ok; if you use your package manager, you can check if 2) and 3) are already installed: I suspect they are

_______________

the guide then says:

> [COLOR="#EE82EE"]Newer versions of X should be able to automatically detect and configure your device[/COLOR]

to test this, paste into a terminal

> [COLOR="#FF0000"]xsetwacom --list devices[/COLOR]

.............can you copy and paste back here what you get?

_________________

If recognised the ubuntu guide [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) still says you have to specifically configure GIMP and gives a good description how to do this

____________

can we ask you to tell how you did with all three steps as mentioned above?

---

### Post by john173 on 2014-03-22
Neither the command shows anything ```
[COLOR=#FF0000]dmesg | grep -i wacom[/COLOR]
```
Nor                  >>>>>>               the ```
[COLOR=#FF0000]xsetwacom --list devices[/COLOR]
```
The dmesg is already installed and says scroll down and you will see the bolded line 
```
[    1.682385] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.682413] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.682415] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.682416] usb usb1: Product: EHCI Host Controller
[    1.682418] usb usb1: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
[    1.682419] usb usb1: SerialNumber: 0000:00:12.2
[    1.682582] hub 1-0:1.0: USB hub found
[    1.682588] hub 1-0:1.0: 5 ports detected
[    1.682791] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.682795] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.682799] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.682810] ehci-pci 0000:00:13.2: debug port 1
[    1.682836] ehci-pci 0000:00:13.2: irq 17, io mem 0xfef4d000
[    1.694378] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.694404] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.694406] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.694408] usb usb2: Product: EHCI Host Controller
[    1.694409] usb usb2: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
[    1.694411] usb usb2: SerialNumber: 0000:00:13.2
[    1.694596] hub 2-0:1.0: USB hub found
[    1.694604] hub 2-0:1.0: 5 ports detected
[    1.694698] ehci-platform: EHCI generic platform driver
[    1.694707] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.694708] ohci-pci: OHCI PCI platform driver
[    1.694829] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.694834] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.694859] ohci-pci 0000:00:12.0: irq 18, io mem 0xfef50000
[    1.754360] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.754364] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.754366] usb usb3: Product: OHCI PCI host controller
[    1.754367] usb usb3: Manufacturer: Linux 3.11.0-18-generic ohci_hcd
[    1.754369] usb usb3: SerialNumber: 0000:00:12.0
[    1.754566] hub 3-0:1.0: USB hub found
[    1.754574] hub 3-0:1.0: 5 ports detected
[    1.754763] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.754768] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.754782] ohci-pci 0000:00:13.0: irq 18, io mem 0xfef4e000
[    1.814337] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.814341] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.814343] usb usb4: Product: OHCI PCI host controller
[    1.814344] usb usb4: Manufacturer: Linux 3.11.0-18-generic ohci_hcd
[    1.814345] usb usb4: SerialNumber: 0000:00:13.0
[    1.814537] hub 4-0:1.0: USB hub found
[    1.814546] hub 4-0:1.0: 5 ports detected
[    1.814734] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.814739] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 5
[    1.814754] ohci-pci 0000:00:14.5: irq 18, io mem 0xfef4c000
[    1.874319] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.874323] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.874325] usb usb5: Product: OHCI PCI host controller
[    1.874327] usb usb5: Manufacturer: Linux 3.11.0-18-generic ohci_hcd
[    1.874328] usb usb5: SerialNumber: 0000:00:14.5
[    1.874515] hub 5-0:1.0: USB hub found
[    1.874523] hub 5-0:1.0: 2 ports detected
[    1.874590] ohci-platform: OHCI generic platform driver
[    1.874598] uhci_hcd: USB Universal Host Controller Interface driver
[    1.874733] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.874738] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.874942] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    1.874947] xhci_hcd 0000:00:10.0: irq 43 for MSI/MSI-X
[    1.874953] xhci_hcd 0000:00:10.0: irq 44 for MSI/MSI-X
[    1.874958] xhci_hcd 0000:00:10.0: irq 45 for MSI/MSI-X
[    1.874964] xhci_hcd 0000:00:10.0: irq 46 for MSI/MSI-X
[    1.875045] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    1.875047] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.875048] usb usb6: Product: xHCI Host Controller
[    1.875050] usb usb6: Manufacturer: Linux 3.11.0-18-generic xhci_hcd
[    1.875051] usb usb6: SerialNumber: 0000:00:10.0usb 3-4: Manufacturer: Wacom Co.,Ltd
[    1.875215] xHCI xhci_add_endpoint called for root hub
[    1.875218] xHCI xhci_check_bandwidth called for root hub
[    1.875243] hub 6-0:1.0: USB hub found
[    1.875250] hub 6-0:1.0: 2 ports detected
[    1.875310] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.875313] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    1.878343] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
[    1.878345] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.878347] usb usb7: Product: xHCI Host Controller
[    1.878348] usb usb7: Manufacturer: Linux 3.11.0-18-generic xhci_hcd
[    1.878349] usb usb7: SerialNumber: 0000:00:10.0
[    1.878481] xHCI xhci_add_endpoint called for root hub
[    1.878484] xHCI xhci_check_bandwidth called for root hub
[    1.878511] hub 7-0:1.0: USB hub found
[    1.878520] hub 7-0:1.0: 2 ports detected
[    1.886510] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.886519] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    1.886729] xhci_hcd 0000:00:10.1: irq 47 for MSI/MSI-X
[    1.886734] xhci_hcd 0000:00:10.1: irq 48 for MSI/MSI-X
[    1.886740] xhci_hcd 0000:00:10.1: irq 49 for MSI/MSI-X
[    1.886745] xhci_hcd 0000:00:10.1: irq 50 for MSI/MSI-X
[    1.886751] xhci_hcd 0000:00:10.1: irq 51 for MSI/MSI-X
[    1.886837] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.886839] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.886841] usb usb8: Product: xHCI Host Controller
[    1.886842] usb usb8: Manufacturer: Linux 3.11.0-18-generic xhci_hcd
[    1.886844] usb usb8: SerialNumber: 0000:00:10.1
[    1.887002] xHCI xhci_add_endpoint called for root hub
[    1.887005] xHCI xhci_check_bandwidth called for root hub
[    1.887031] hub 8-0:1.0: USB hub found
[    1.887037] hub 8-0:1.0: 2 ports detected
[    1.887104] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.887108] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
[    1.890123] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.890125] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.890126] usb usb9: Product: xHCI Host Controller
[    1.890128] usb usb9: Manufacturer: Linux 3.11.0-18-generic xhci_hcd
[    1.890129] usb usb9: SerialNumber: 0000:00:10.1
[    1.890295] xHCI xhci_add_endpoint called for root hub
[    1.890298] xHCI xhci_check_bandwidth called for root hub
[    1.890324] hub 9-0:1.0: USB hub found
[    1.890334] hub 9-0:1.0: 2 ports detected
[    1.902449] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.905668] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.905680] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.905949] mousedev: PS/2 mouse device common for all mice
[    1.906339] rtc_cmos 00:05: RTC can wake from S4
[    1.906491] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.906515] rtc_cmos 00:05: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.906573] device-mapper: uevent: version 1.0.3
[    1.906628] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.906669] cpuidle: using governor ladder
[    1.906745] cpuidle: using governor menu
[    1.906756] ledtrig-cpu: registered to indicate activity on CPUs
[    1.906830] TCP: cubic registered
[    1.906902] NET: Registered protocol family 10
[    1.907058] NET: Registered protocol family 17
[    1.907066] Key type dns_resolver registered
[    1.907280] PM: Hibernation image not present or could not be loaded.
[    1.907283] Loading module verification certificates
[    1.908095] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 9d94dc8d073854d044b3fa3652786ac75597c2f5'
[    1.908104] registered taskstats version 1
[    1.910684] Key type trusted registered
[    1.912387] Key type encrypted registered
[    1.913831] AppArmor: AppArmor sha1 policy hashing enabled
[    1.914137]   Magic number: 6:605:239
[    1.914224] rtc_cmos 00:05: setting system clock to 2014-03-22 17:13:45 UTC (1395508425)
[    1.914354] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.914487] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.914488] EDD information not available.
[    1.915626] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    1.915630] Write protecting the kernel read-only data: 12288k
[    1.917996] Freeing unused kernel memory: 1028K (ffff8800016ff000 - ffff880001800000)
[    1.919642] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[    1.933361] systemd-udevd[115]: starting version 204
[    1.951120] scsi0 : pata_atiixp
[    1.951384] scsi1 : pata_atiixp
[    1.951578] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf100 irq 14
[    1.951580] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf108 irq 15
[    1.952179] ahci 0000:00:11.0: version 3.0
[    1.952386] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.952390] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    1.953035] scsi2 : ahci
[    1.953223] scsi3 : ahci
[    1.953264] [drm] Initialized drm 1.1.0 20060810
[    1.953366] scsi4 : ahci
[    1.953489] scsi5 : ahci
[    1.953547] ata3: SATA max UDMA/133 abar m2048@0xfef51000 port 0xfef51100 irq 19
[    1.953550] ata4: SATA max UDMA/133 abar m2048@0xfef51000 port 0xfef51180 irq 19
[    1.953552] ata5: SATA max UDMA/133 abar m2048@0xfef51000 port 0xfef51200 irq 19
[    1.953554] ata6: SATA max UDMA/133 abar m2048@0xfef51000 port 0xfef51280 irq 19
[    1.955319] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.955558] r8169 0000:03:00.0: irq 52 for MSI/MSI-X
[    1.955723] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000634000, 00:25:22:d8:94:74, XID 0c900800 IRQ 52
[    1.955725] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.978215] [drm] radeon kernel modesetting enabled.
[    1.978601] [drm] initializing kernel modesetting (SUMO 0x1002:0x9640 0x1849:0x9640).
[    1.978733] [drm] register mmio base: 0xFEF00000
[    1.978734] [drm] register mmio size: 262144
[    1.978882] ATOM BIOS: General
[    1.978929] radeon 0000:00:01.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
[    1.978931] radeon 0000:00:01.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[    1.978933] [drm] Detected VRAM RAM=256M, BAR=256M
[    1.978934] [drm] RAM width 32bits DDR
[    1.980306] [TTM] Zone  kernel: Available graphics memory: 1883962 kiB
[    1.980310] [TTM] Initializing pool allocator
[    1.980314] [TTM] Initializing DMA pool allocator
[    1.980334] [drm] radeon: 256M of VRAM memory ready
[    1.980336] [drm] radeon: 512M of GTT memory ready.
[    1.980589] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.988870] [drm] Loading SUMO Microcode
[    1.989608] [drm] PCIE GART of 512M enabled (table at 0x0000000000273000).
[    1.989737] radeon 0000:00:01.0: WB enabled
[    1.989740] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000010000c00 and cpu addr 0xffff880123721c00
[    1.989742] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000010000c0c and cpu addr 0xffff880123721c0c
[    1.990485] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90010932118
[    1.990487] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.990488] [drm] Driver supports precise vblank timestamp query.
[    1.990509] radeon 0000:00:01.0: irq 53 for MSI/MSI-X
[    1.990521] radeon 0000:00:01.0: radeon: using MSI.
[    1.990544] [drm] radeon: irq initialized.
[    2.006981] [drm] ring test on 0 succeeded in 1 usecs
[    2.007040] [drm] ring test on 3 succeeded in 1 usecs
[    2.062633] [drm] ring test on 5 succeeded in 1 usecs
[    2.062636] [drm] UVD initialized successfully.
[    2.082881] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.082913] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.103296] [drm] ib test on ring 5 succeeded
[    2.124130] [drm] Radeon Display Connectors
[    2.124132] [drm] Connector 0:
[    2.124133] [drm]   HDMI-A-1
[    2.124134] [drm]   HPD2
[    2.124135] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    2.124136] [drm]   Encoders:
[    2.124137] [drm]     DFP1: INTERNAL_UNIPHY2
[    2.124138] [drm] Connector 1:
[    2.124139] [drm]   VGA-1
[    2.124140] [drm]   HPD1
[    2.124141] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    2.124142] [drm]   Encoders:
[    2.124143] [drm]     CRT1: INTERNAL_UNIPHY2
[    2.124143] [drm]     CRT1: NUTMEG
[    2.141359] [drm] Internal thermal controller without fan control
[    2.141390] [drm] radeon: power management initialized
[    2.219650] [drm] fb mappable at 0xC0378000
[    2.219651] [drm] vram apper at 0xC0000000
[    2.219652] [drm] size 4325376
[    2.219653] [drm] fb depth is 24
[    2.219654] [drm]    pitch is 5632
[    2.219801] fbcon: radeondrmfb (fb0) is primary device
[    2.270273] ata6: SATA link down (SStatus 0 SControl 300)
[    2.271659] Console: switching to colour frame buffer device 170x48
[    2.274701] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    2.274703] radeon 0000:00:01.0: registered panic notifier
[    2.274708] [drm] Initialized radeon 2.34.0 20080528 for 0000:00:01.0 on minor 0
[    2.390186] usb 4-3: new low-speed USB device number 2 using ohci-pci
[    2.442178] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.442208] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.442238] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.442843] ata4.00: ATA-9: WDC WD10EZEX-00BN5A0, 01.01A01, max UDMA/133
[    2.442847] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.443571] ata4.00: configured for UDMA/133
[    2.443851] ata5.00: ATAPI: Optiarc DVD RW AD-7280S, 1.01, max UDMA/100
[    2.444314] ata3.00: ATA-8: WDC WD5000AAKX-00ERMA0, 15.01H15, max UDMA/133
[    2.444316] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.445721] ata5.00: configured for UDMA/100
[    2.445843] ata3.00: configured for UDMA/133
[    2.446088] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKX-0 15.0 PQ: 0 ANSI: 5
[    2.446405] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.446411] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.446626] sd 2:0:0:0: [sda] Write Protect is off
[    2.446633] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.446704] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EZEX-00B 01.0 PQ: 0 ANSI: 5
[    2.446745] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.446924] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.446926] sd 3:0:0:0: [sdb] 4096-byte physical blocks
[    2.446983] sd 3:0:0:0: [sdb] Write Protect is off
[    2.446989] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.446991] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.447017] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.447611] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7280S  1.01 PQ: 0 ANSI: 5
[    2.449521] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.449523] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.449609] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.449723] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    2.464418]  sda: sda1
[    2.465356] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.480158]  sdb: sdb1
[    2.481115] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.570176] usb 4-3: New USB device found, idVendor=045e, idProduct=0084
[    2.570180] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.570182] usb 4-3: Product: Microsoft Basic Optical Mouse
[    2.570184] usb 4-3: Manufacturer: Microsoft
[    2.575268] hidraw: raw HID events driver (C) Jiri Kosina
[    2.583228] usbcore: registered new interface driver usbhid
[    2.583232] usbhid: USB HID core driver
[    2.584898] input: Microsoft Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb4/4-3/4-3:1.0/input/input2
[    2.585050] hid-generic 0003:045E:0084.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Basic Optical Mouse] on usb-0000:00:13.0-3/input0
[    2.618117] tsc: Refined TSC clocksource calibration: 2900.014 MHz
[    2.710090] usb 3-3: new low-speed USB device number 2 using ohci-pci
[    2.841824] xor: measuring software checksum speed
[    2.877980]    prefetch64-sse: 11348.000 MB/sec
[    2.880116] usb 3-3: New USB device found, idVendor=1c4f, idProduct=0027
[    2.880120] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.880122] usb 3-3: Product: USB Keyboard
[    2.880123] usb 3-3: Manufacturer: SIGMACHIP
[    2.887284] input: SIGMACHIP USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input3
[    2.887519] hid-generic 0003:1C4F:0027.0002: input,hidraw1: USB HID v1.10 Keyboard [SIGMACHIP USB Keyboard] on usb-0000:00:12.0-3/input0
[    2.895125] input: SIGMACHIP USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input4
[    2.895290] hid-generic 0003:1C4F:0027.0003: input,hidraw2: USB HID v1.10 Device [SIGMACHIP USB Keyboard] on usb-0000:00:12.0-3/input1
[    2.917967]    generic_sse: 10308.000 MB/sec
[    2.917969] xor: using function: prefetch64-sse (11348.000 MB/sec)
[    2.919871] device-mapper: dm-raid45: initialized v0.2594b
[    3.070467] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.133972] usb 6-1: new full-speed USB device number 2 using xhci_hcd
[    3.273982] usb 6-1: New USB device found, idVendor=1bcf, idProduct=0901
[    3.273986] usb 6-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    3.273988] usb 6-1: Product: USB Laser Game Mouse
[    3.274146] usb 6-1: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.274151] usb 6-1: ep 0x84 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.321210] input: USB Laser Game Mouse as /devices/pci0000:00/0000:00:10.0/usb6/6-1/6-1:1.0/input/input5
[    3.321486] hid-generic 0003:1BCF:0901.0004: input,hidraw3: USB HID v1.10 Mouse [USB Laser Game Mouse] on usb-0000:00:10.0-1/input0
[    3.352160] input: USB Laser Game Mouse as /devices/pci0000:00/0000:00:10.0/usb6/6-1/6-1:1.1/input/input6
[    3.352417] hid-generic 0003:1BCF:0901.0005: input,hidraw4: USB HID v1.10 Keyboard [USB Laser Game Mouse] on usb-0000:00:10.0-1/input1
[    3.383124] hid-generic 0003:1BCF:0901.0006: invalid report_count 65535
[    3.383128] hid-generic 0003:1BCF:0901.0006: item 0 2 1 9 parsing failed
[    3.383140] hid-generic: probe of 0003:1BCF:0901.0006 failed with error -22
[    3.493874] usb 8-1: new high-speed USB device number 2 using xhci_hcd
[    3.521781] usb 8-1: New USB device found, idVendor=0cf3, idProduct=9271
[    3.521786] usb 8-1: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[    3.521787] usb 8-1: Product: USB2.0 WLAN
[    3.521801] usb 8-1: Manufacturer: ATHEROS
[    3.521803] usb 8-1: SerialNumber: 12345
[    3.617986] Switched to clocksource tsc
[   11.466759] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.682607] systemd-udevd[371]: starting version 204
[   12.104005] parport_pc 00:03: reported by Plug and Play ACPI
[   12.104039] parport0: PC-style at 0x378, irq 5 [PCSPP,EPP]
[   12.141873] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.216682] lp0: using parport0 (interrupt-driven).
[   12.217506] microcode: CPU0: patch_level=0x03000027
[   12.304145] device-mapper: multipath: version 1.6.0 loaded
[   12.373590] microcode: CPU1: patch_level=0x03wacom000027
[   12.373633] microcode: CPU2: patch_level=0x03000027
[   12.373647] microcode: CPU3: patch_level=0x03000027
[   12.373786] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.406067] cfg80211: Calling CRDA to update world regulatory domain
[   12.406154] hda-intel 0000:00:01.1: Using LPIB position fix
[   12.406195] snd_hda_intel 0000:00:01.1: irq 54 for MSI/MSI-X
[   12.408683] hda-intel 0000:00:01.1: Enable sync_write for stable communication
[   12.454854] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input7
[   12.455389] hda-intel 0000:00:14.2: Using LPIB position fix
[   12.458903] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   12.465907] kvm: Nested Virtualization enabled
[   12.465911] kvm: Nested Paging enabled
[   12.528870] ppdev: user-space parallel port driver
[   12.558495] SKU: Nid=0x1d sku_cfg=0x4005e601
[   12.558499] SKU: port_connectivity=0x1
[   12.558500] SKU: enable_pcbeep=0x0
[   12.558501] SKU: check_sum=0x00000005
[   12.558502] SKU: customization=0x000000e6
[   12.558503] SKU: external_amp=0x0
[   12.558504] SKU: platform_type=0x0
[   12.558505] SKU: swap=0x0
[   12.558506] SKU: override=0x1
[   12.558850] autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   12.558851]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.558852]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.558853]    mono: mono_out=0x0
[   12.558854]    dig-out=0x1e/0x0
[   12.558855]    inputs:
[   12.558857]      Front Mic=0x19
[   12.558858]      Rear Mic=0x18
[   12.558859]      Line=0x1a
[   12.558860] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[   12.558862] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0892
[   12.571322] input: HD-Audio Generic Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   12.571460] input: HD-Audio Generic Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[   12.571526] input: HD-Audio Generic Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   12.571619] input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   12.571678] input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input12
[   12.759260] cfg80211: World regulatory domain updated:
[   12.759265] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.759267] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.759268] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.759270] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.759271] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.759272] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.922936] usb 8-1: ath9k_htc: Firmware htc_9271.fw requested
[   12.923025] usbcore: registered new interface driver ath9k_htc
[   13.373342] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.661786] usb 8-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   13.897677] ath9k_htc 8-1:1.0: ath9k_htc: HTC initialized with 33 credits
[   14.128479] ath9k_htc 8-1:1.0: ath9k_htc: FW Version: 1.3
[   14.128484] ath: EEPROM regdomain: 0x809c
[   14.128485] ath: EEPROM indicates we should expect a country code
[   14.128487] ath: doing EEPROM country->regdmn map search
[   14.128487] ath: country maps to regdmn code: 0x52
[   14.128489] ath: Country alpha2 being used: CN
[   14.128489] ath: Regpair used: 0x52
[   14.212770] ieee80211 phy0: Atheros AR9271 Rev:1
[   14.212791] cfg80211: Calling CRDA for country: CN
[   14.216540] cfg80211: Regulatory domain changed to country: CN
[   14.216544] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.216546] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   14.216548] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   14.216549] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
[   14.216550] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm)
[   14.216552] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
[   14.247268] init: failsafe main process (745) killed by TERM signal
[   15.024171] init: avahi-cups-reload main process (843) terminated with status 1
[   15.196291] Bluetooth: Core ver 2.16
[   15.196320] NET: Registered protocol family 31
[   15.196322] Bluetooth: HCI device and connection manager initialized
[   15.196332] Bluetooth: HCI socket layer initialized
[   15.196335] Bluetooth: L2CAP socket layer initialized
[   15.196347] Bluetooth: SCO socket layer initialized
[   15.234621] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.234625] Bluetooth: BNEP filters: protocol multicast
[   15.234634] Bluetooth: BNEP socket layer initialized
[   15.341822] Bluetooth: RFCOMM TTY layer initialized
[   15.341839] Bluetooth: RFCOMM socket layer initialized
[   15.341840] Bluetooth: RFCOMM ver 1.11
[   16.580439] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.580780] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.772095] r8169 0000:03:00.0 eth0: link down
[   16.772143] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.772481] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.017127] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   19.019957] vboxdrv: Found 4 processor cores.
[   19.020460] vboxdrv: fAsync=0 offMin=0x4f9 offMax=0xa3b5
[   19.020545] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.020547] vboxdrv: Successfully loaded version 4.3.8 (interface 0x001a0007).
[   19.357835] wlan0: authenticate with 08:76:ff:bf:5b:c0
[   19.383519] vboxpci: IOMMU not found (not registered)
[   19.658177] wlan0: send auth to 08:76:ff:bf:5b:c0 (try 1/3)
[   19.660183] wlan0: authenticated
[   19.660387] ath9k_htc 8-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   19.661194] wlan0: associate with 08:76:ff:bf:5b:c0 (try 1/3)
[   19.666503] wlan0: RX AssocResp from 08:76:ff:bf:5b:c0 (capab=0x411 status=0 aid=1)
[   19.673170] wlan0: associated
[   19.673215] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.933243] init: plymouth-stop pre-start process (1342) terminated with status 1
[ 6224.970488] systemd-timedated[3082]: /etc/localtime should be a symbolic link to a timezone data file in /usr/share/zoneinfo/.
[13200.006151] usb 3-4: new full-speed USB device number 3 using ohci-pci
[13200.179683] usb 3-4: New USB device found, idVendor=056a, idProduct=0303
[13200.179695] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[13200.179702] usb 3-4: Product: Intuos PTM
[13200.179707] _**usb 3-4: Manufacturer: Wacom Co.,Ltd**_.
```


 And the "device" archive after I open it doesn't shows anything any word about wacom in here if you mean that [COLOR=#FF8C00]/proc/bus/input/devices 

[/COLOR]And i dont understand the step 1.3 Automatical Setup 
Only tells my how to check my tablet is working good

Therefore, [COLOR=#006400]**xserver-xorg-input-wacom is installed and [COLOR=#006400][B]xserver-xorg-input-wacom-dbg (just saying)**[/COLOR][/B][/COLOR]

Although should I follow the following Methos 1,2.... in there [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) ?


And the end as you said
> 
1) **kernel driver**: *[COLOR=#EE82EE]only install if your tablet is not recognized as an input device by the system[/COLOR]*. (So you need to do the dmesg as above to work that out ..)
2) **xf86-input-wacom** (aka xserver-xorg-input-wacom in ubuntu/mint) *[COLOR=#EE82EE]only install if your tablet is recognized but missing functionality[/COLOR]*.
3) **libwacom** *[COLOR=#EE82EE]only install if your tablet is not recognized by the control panel[/COLOR]*. (it is installed in our mint system as default)


1)My kernel recognize the tablet
2)Is the "aka xserver-xorg-input-wacom" a terminal command if it is I oppened a terminal and coded it there 
the result :
user@user-desktop ~ $ ```
aka xserver-xorg-input-wacom
```
```
No command 'aka' found, did you mean:
 Command 'aha' from package 'aha' (universe)
 Command 'ara' from package 'ara' (universe)
 Command 'aa' from package 'astronomical-almanac' (universe)
aka: command not found
```
3)I checked it anyway and it installed and not only this other similar things

---

### Post by pdc on 2014-03-23
1) I don't think your system is recognising the needed module, because dmesg | grep -i wacom doesn't show anything

eg from this post current on Mint [http://forums.linuxmint.com/viewtopic.php?f=49&t=163013](http://forums.linuxmint.com/viewtopic.php?f=49&t=163013)

dmesg gave

> ~ $ dmesg | grep -i wacom
[    3.220501] usb 1-6.2.4: Manufacturer: Wacom Co.,Ltd.
[    5.805533] usbcore: registered new interface driver wacom

that post also had to edit [COLOR="#EE82EE"]/etc/modules[/COLOR] to add wacom to the end of the list

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
wacom

so I am thinking you need input-wacom [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom) which is a daunting install for one unused to such things............do you feel able to battle through this?

_____________

last my apologies for misleading you with "aka xserver-xorg-input-wacom"

aka was a short-cut for* also known as * so the programme was [COLOR="#008080"]xserver-xorg-input-wacom[/COLOR]

---

### Post by dioioib on 2014-03-23
Here is my ubuntu 13.04 dmsg for my wacom.

```

dmesg | grep -i wacom
[    6.372065] input: Wacom Cintiq 21UX2 as /devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.0/input/input14
[    6.375874] usbcore: registered new interface driver wacom

```

and 

```

$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc

```

I'm running an older version of input wacom from input-wacom-0.16.0.tar.bz2 or xf86-input-wacom-0.20.0 under Gnome using xrandr. I remember it took me a while to setup because I have a dual head (2 monitor) setup. Even then it never worked well with Krita. GIMP was better but I had slight offset issues due to the two monitors.

---

### Post by pdc on 2014-03-23
> ~ $ dmesg | grep -i wacom
[ 3.220501] usb 1-6.2.4: Manufacturer: Wacom Co.,Ltd.
[ 5.805533] usbcore: registered new interface driver wacom 

so [COLOR="#EE82EE"]dioioib[/COLOR] does **NOT** need input-wacom

2) [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom) you have that installed?

3) I am unclear if you have libwacom installed 

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Libwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Libwacom)

the post on Mint talks of the /etc/modules file   ......and the need to edit it ..........one would use the command > gksudo gedit /etc/modules and add wacom as advised

_____________

next step should be configure Gimp

---

### Post by dioioib on 2014-03-23
> **pdc said:**
> 
3) I am unclear if you have libwacom installed 


you could run this to see if the drivers are there and installed:

```

$ sudo find . -name wacom\* | grep modules 

output
./usr/lib/xorg/modules/input/wacom_drv.so

$ lsmod | grep wacom

output
wacom                  57412  0 

```

And this article is detailed regarding the setup. 

[https://help.ubuntu.com/community/Install_linuxwacom_driver]("https://help.ubuntu.com/community/Install_linuxwacom_driver")

---

### Post by john173 on 2014-03-23
Yeah think you are right "dmesg gave" does not appear anything like this :

> usbcore: registered new interface driver wacom 
______________
------------------------
Also i added the wacom in modules archive as you said
_____________________
-------------------------------------
Also i followed this  [http://sourceforge.net/apps/mediawik...le=Input-wacom](http://sourceforge.net/apps/mediawik...le=Input-wacom) and stacked in the first command as it says
Is the bottom line ... is an error or not?
"0 upgraded, 0 newly installed, 0 to remove and 20 not upgrade"

Just opened a new terminal and coded 

user@user-desktop ~ $ ```
sudo apt-get install linux-headers-$(uname -r)
```



```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.11.0-18-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libpcre3-dev libpcrecpp0
Use 'apt-get autoremove' to remove them.
**0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded**.
```
___________________________________
-------------------------------------------------------------
-------------------------------------------------------------

Anyway i moved on and downloaded the package from there [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/)

.) unpackage it 
.)opened unpackaged folder  with terminal
.)coded *./configure* and the answer was this
Scroll down i got confused with this  

user@user-desktop ~/Downloads/input-wacom-0.20.0 $ ```
./configure
```


```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/user/Downloads/input-wacom-0.20.0/missing: Unknown '--is-lightweight' option
Try '/home/user/Downloads/input-wacom-0.20.0/missing --help' for more information
configure: WARNING: 'missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/3.11.0-18-generic/build
checking kernel version... 3.11.0-18-generic

checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating 2.6.30/Makefile
config.status: creating 2.6.36/Makefile
config.status: creating 2.6.38/Makefile
config.status: creating 3.7/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/home/user/Downloads/input-wacom-0.20.0'
Making all in 3.7
make[2]: Entering directory `/home/user/Downloads/input-wacom-0.20.0/3.7'
    Building input-wacom drivers for 2.6 kernel.
make -C /lib/modules/3.11.0-18-generic/build M=/home/user/Downloads/input-wacom-0.20.0/3.7
make[3]: Entering directory `/usr/src/linux-headers-3.11.0-18-generic'
  Building modules, stage 2.
  MODPOST 2 modules
make[3]: Leaving directory `/usr/src/linux-headers-3.11.0-18-generic'
make[2]: Leaving directory `/home/user/Downloads/input-wacom-0.20.0/3.7'
make[2]: Entering directory `/home/user/Downloads/input-wacom-0.20.0'
make[2]: Leaving directory `/home/user/Downloads/input-wacom-0.20.0'
make[1]: Leaving directory `/home/user/Downloads/input-wacom-0.20.0'

----------------------------------------
  [U]BUILD ENVIRONMENT:
       linux kernel - yes 3.7
      kernel source - yes /lib/modules/3.11.0-18-generic/build

Your wacom.ko is available under 
    /home/user/Downloads/input-wacom-0.20.0/3.7
If you have an USB device, you can copy the driver by:
    cp 3.7/wacom.ko /lib/modules/3.11.0-18-generic/kernel/drivers/input/tablet
If you have a serial device, please copy the driver by:
    cp 3.7/wacom_w8001.ko /lib/modules/3.11.0-18-generic/kernel/drivers/input/touchscreen

NOTE: The kernel drivers included in this package are only
tested with the X Wacom driver built from xf86-input-wacom.
 If you are running an X server version older than 1.7, 
please use the drivers provided by linuxwacom package.[/U]
```

And YES I won't let an OS beat me I had to be a fun of the Linux Systems and i won't let it down . WINDOWS ARE SILLY!!!!!!!!! :guitar:

---

### Post by john173 on 2014-03-23
Forgot to say hello :D ):P
Anyway dioioib (what the hell name is this :D:D)
----------------------------------------------------------------
I have the libwacom installed as the Package Manager says
----------------------------------------------------------------
I runned your command $ "sudo find . -name wacom\* | grep modules"
Answer ::::::::

```
user@user-desktop ~ $ sudo find . -name wacom\* | grep modules
[sudo] password for user: 
user@user-desktop ~ $ 
```

And i have a folder in /usr/lib/xorg/modules/input/ with the name wacom_drv.so
--------------------------------------------------------------------------
And runned the lsmod | grep wacom

```
user@user-desktop ~ $ lsmod | grep wacom
user@user-desktop ~ $ 
```

---

### Post by john173 on 2014-03-23
Fast Respawn 

user@user-desktop ~ $```
 dmesg | grep -i wacom
```


```
[  422.858800] usb 3-4: Manufacturer: Wacom Co.,Ltd.
[10166.614603] usb 4-2: Manufacturer: Wacom Co.,Ltd.
[10276.286014] usb 3-4: Manufacturer: Wacom Co.,Ltd.
```

---

### Post by dioioib on 2014-03-23
> **john173 said:**
> Forgot to say hello :D ):P
Anyway dioioib (what the hell name is this :D:D)
lol. yeah the name it is based on the old army kilroy. 

I thought I had patched my kernel with the driver hence why the lsmod command shows "wacom"


But when I review my build notes for this rig I see I used an apt-get repo and aptitude. This is what I have written down
```

xinput --list

add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install wacom-dkms

xinput --list

#check /dev/input/wacom and /dev/input/*   
#where * is your device name such as bamboo-#x#

#Reverting to ubuntu driver
sudo aptitude reinstall xserver-xorg-input-wacom wacom-tools

```

After that I built some scripts to use xsetwacom.

What I am unsure of is if I wrote the revert command down just to be safe or if I was having issues with the apt repo.

---

### Post by john173 on 2014-03-24
I think u just had an issue with _sudo apt-get_ update 
> W: Failed to fetch [http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/saucy/main/source/Sources](http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/saucy/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Also after typing 
sudo apt-get [I]install wacom-dkms

[/I] shows[I] >  E: Unable to locate package wacom-dkms

[/I]
And in /dev/input/ no clue about wacom 



*Thank you both  for your support anyway*

---

### Post by pdc on 2014-03-24
I understand you can get wacom-dkms from here

[https://launchpad.net/~lekensteyn/+archive/wacom-tablet](https://launchpad.net/~lekensteyn/+archive/wacom-tablet)

all this ppa as he guides you to

> This repository provides the wacom-dkms package. This installs an updated kernel
module, "wacom", using DKMS. DKMS takes care of updating the kernel module each
time your kernel is upgraded, so you only have to install this package once.

> After installation, unload the old kernel driver and reload the new one with:

    sudo modprobe -v -r wacom; sudo modprobe -v wacom

---

### Post by john173 on 2014-03-25
I added the ppa in software sourced >> ppa 
And after it got updated shows 
> 
Failed to fetch [http://ppa.launchpad.net/lekensteyn/wacom-tablet/ubuntu/dists/saucy/main/source/Sources](http://ppa.launchpad.net/lekensteyn/wacom-tablet/ubuntu/dists/saucy/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/lekensteyn/wacom-tablet/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/lekensteyn/wacom-tablet/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/lekensteyn/wacom-tablet/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/lekensteyn/wacom-tablet/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.
Therefore i added the  *_sudo modprobe -v -r wacom; sudo modprobe -v wacom_* and shows : 
> rmmod wacom
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/input/tablet/wacom.ko 

---

### Post by john173 on 2014-03-25
Addition infos about **dioioib's** post 

```
user@user-desktop ~ $ dmesg | grep -i wacom
```

```

[ 2227.596511] usbcore: registered new interface driver wacom
[ 2242.138093] usbcore: deregistering interface driver wacom
[ 2242.167151] usbcore: registered new interface driver wacom
[ 2273.262734] usb 3-4: Manufacturer: Wacom Co.,Ltd.
[ 2275.532346] usbcore: deregistering interface driver wacom
[ 2275.561984] usbcore: registered new interface driver wacom
[ 2276.943929] usbcore: deregistering interface driver wacom
[ 2276.970659] usbcore: registered new interface driver wacom
[ 2309.486209] usbcore: deregistering interface driver wacom
[ 2309.514946] usbcore: registered new interface driver wacom
[ 3943.912397] usbcore: deregistering interface driver wacom
[ 3943.942001] usbcore: registered new interface driver wacom
[ 7016.268180] usb 3-4: Manufacturer: Wacom Co.,Ltd
```.

and 

```
user@user-desktop ~ $ cat /etc/modules
```


```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
```

---

### Post by pdc on 2014-03-25
John: we have never (I think) heard the device name and number that you have bought;

I say this because this thread [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)

and this thread [http://forums.linuxmint.com/viewtopic.php?f=49&t=163013](http://forums.linuxmint.com/viewtopic.php?f=49&t=163013) and the links that the poster gives late in the thread ...........suggest the wacom bamboo pad CTH-300 cannot be made to work on linux at present

---

### Post by john173 on 2014-03-25
I am using Wacom Pen & touch medium CTH680


[LIST]
[*]                     Pressure Levels                     1024
[*]                     Pen                     Intuos Pen with eraser
[*]                     Limited Warranty                     2-years in USA and Canada
 2-years in Latin America
[*]                     Multi-touch                     Yes
[*]                     Active Area                     216 x 135 mm 
 8.5 x 5.3 in
[*]                     Weight                     520 g approximately 
 18.3 oz 
[*]                     Product Type                     Pen tablet
[*]                     Wireless Support                     Yes (Sold separately)
[*]                     Cable Included                     Yes
[*]                     Model Number                     CTH680
[/LIST]

---

### Post by pdc on 2014-03-26
John: I borrowed a CTH680; and tried it on a Mint 15 install: mate; 32bit; I confess as it was a laptop that isn't used much: I installed a newer kernel: a 3-11

I think the key step is to install [COLOR="#008000"]input-wacom[/COLOR]; and I have worked through your posts; and I don't think it was installed:

I installed that on our system, and the wacom seems to work fine;

so one gets the file from here: [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/) and I downloaded the tar.gz version, [COLOR="#008000"]input-wacom-0.20.0.tar.gz [/COLOR]and saved it to the Downloads folder

and the instructions from here: 

the commands were:

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf input-wacom-0.20.0.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd input-wacom-0.20.0[/COLOR]

> [COLOR="#FF0000"]./configure[/COLOR]

................. near the end of that is a prompt: it says.......if you have a USB tablet, use what they tell you........so you copy that command; add a sudo in front of it

the command structure is sudo cp ./<kernel version>/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet

but the configure script very nicely works out all these things for you, and *you just need to spot it; in the terminal; copy it and paste it with the sudo in front*

Now this is where there is a potential uncertainty: the configure script says; (my reading of it:* if you have a serial tablet paste this command sudo cp ./<kernel version>/wacom_w8001.ko /lib/modules/`uname -r`/kernel/drivers/input/touchscreen* ..so I didn't paste it, and the wacom worked for me ..the reason I mention it is the instructions above.......which are really good and helpful .........seems to suggest both...........

...... you might be best to just copy the second command from the terminal, and (with sudo in front) paste it and action it .........

......so my reading is next step is 

> [COLOR="#FF0000"]sudo depmod -a[/COLOR] and then [COLOR="#FF0000"]**reboot**[/COLOR].............the desktop showed the pen being recognised and I think opened gimp: we have 2.8 so the input config is in its own menu entry in EDIT

..............I hope I am pointing you in the right direction ...............

any joy?

I

---

### Post by john173 on 2014-03-26
[SIZE=5]:KSI HAD TO EDIT THIS POST AS I HAD WROTE BULL**** thank you man i just love you[/SIZE]  :guitar:
[SIZE=3]love you both but more_ **pdc**_ sorry **[COLOR=#000000]dioioib[/COLOR]**[/SIZE]

**_I don't have words to say you saved all these days of searching_** 

***posting these answers as the results of the commands for sb new to know if he did it correct ***

so coded as you said ```
user@user-desktop ~/Downloads/input-wacom-0.20.0 $ sudo cp 3.7/wacom.ko /lib/modules/3.11.0-18-generic/kernel/drivers/input/tablet
user@user-desktop ~/Downloads/input-wacom-0.20.0 $ 

```
also dont know if needed but i did it 
```
user@user-desktop ~/Downloads/input-wacom-0.20.0 $ sudo cp 3.7/wacom_w8001.ko /lib/modules/3.11.0-18-generic/kernel/drivers/input/touchscreen
user@user-desktop ~/Downloads/input-wacom-0.20.0 $ 
```

> the command [COLOR=#FF0000]sudo depmod -a also [/COLOR]shows anything ( to us ) but its works perfectly

(i am using USB too)

Now updating the thread to solved thank both guys don't argue with me [SIZE=3]**[COLOR=#000000]dioioib ;)[/COLOR]**[/SIZE]


*Don't blame if you dont like the word (sity etc) just correct me :D :P*

---

### Post by pdc on 2014-03-26
........I am guessing it is all working!! Delighted to hear that; enjoy

(the hope is ubuntu 14.04 will work OOTB )

---

### Post by john173 on 2014-04-15
I don't know what OOTB means but I hope it :D

---

