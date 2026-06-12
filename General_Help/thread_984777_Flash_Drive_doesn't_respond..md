---
title: "Flash Drive doesn't respond."
date: 2008-11-17
forum: General Help
---

### Post by Roasted on 2008-11-17
My flash drive does not respond in Ubuntu Intrepid 64 bit on my desktop. I have tested this flash drive on my Dell laptop running XP Pro along with the same problematic desktop with Vista Ultimate.

I rebooted the computer twice. Each time when I plug in the flash drive it doesn't work... whether in the front ports or the back. I'm not sure what else I can do. Any ideas?

EDIT - sudo fdisk -l and gparted both don't show the flash drive listed. And I also just tried a 3Com USB wireless adapter and it registered and connected to my wireless network just fine. So, we know that my flash drive works cause it works in Vista on this same computer, we know that Ubuntu recognizes my USB ports due to the fact my wireless adapter works, along with my usb mouse that I forgot to mention earlier.

But Ubuntu just isn't seeing my flash drive. Why?

---

### Post by Roasted on 2008-11-17
Ahhhhhhh! I still can't figure this out... and I rely on USB devices like no other. Anybody have any ideas?

---

### Post by amp_man on 2008-11-17
can you check lsusb, to make sure it's listed? Have you tried modprobe-ing usb-storage?

---

### Post by Roasted on 2008-11-17
lsusb

```
jason@jason-intrepid:~$ lsusb
Bus 008 Device 003: ID 04b8:0819 Seiko Epson Corp. Stylus CX4700/CX4800/DX4800 (PX-A750)
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 13ee:0003  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jason@jason-intrepid:~$ 

```

"sudo modprobe usb-storage" yielded no results. 

Just to clarify, I've established the following:
-Flash drive works in XP/Vista
-Flash drive works in this very computer in Vista
-USB ports work in Ubuntu because USB wireless adapter works
-My USB printer works on this computer in Ubuntu
-So the problem is clearly Ubuntu recognizing my flash drive

---

### Post by amp_man on 2008-11-18
Hmm, this is odd. I only get 2 google hits for 13ee:0003, and I'm assuming that's your flash drive. Can you run "lsusb -s 5:4 -v" just to confirm that it is? You may also want to request this be moved to the kernel forum, I don't know much about this and it may get more attention there.

---

### Post by Roasted on 2008-11-18
```
jason@jason-intrepid:~$ lsusb -s 5:4 -v

Bus 005 Device 004: ID 13ee:0003  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x13ee 
  idProduct          0x0003 
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)
jason@jason-intrepid:~$ 

```

Also, I tried a few LiveCDs here. Hardy 64, Intrepid 32, Intrepid 64... all of them couldn't mount my flash drive. I tried sudo fdisk -l as well as gparted. Yet my usb mouse and usb printer work fine.

Also, I have an 80 gb external hard drive. And it works fine in Intrepid 64... however, as I said, my flash drive doesn't work...

I can't believe this. What in the world happened?!

Edit - Just another note, lsusb takes forever to respond with my flash drive plugged in. When it's not plugged in, it responds instantly. If it is plugged in, it takes forever to respond.

---

### Post by amp_man on 2008-11-18
Oh, so it's not even showing up in lsusb. Something is very wrong there, I just wish I could tell you what. By any chance, is it possibly a Sandisk drive with the U3 "feature"?

---

### Post by Roasted on 2008-11-18
It's an 8gb A-DATA flash drive. It's 3 weeks old, from NewEgg.

It worked all the time until yesterday. :(

---

### Post by amp_man on 2008-11-18
RMA that thing and get a better drive, A-DATA sucks! I had a CF card from them last a little over a month, and it was only used maybe 3 times.

---

### Post by Roasted on 2008-11-18
> **amp_man said:**
> RMA that thing and get a better drive, A-DATA sucks! I had a CF card from them last a little over a month, and it was only used maybe 3 times.

That still doesn't solve the issue at hand, whether it be a crappy brand or not.

My Computer:
Vista Ultimate 64 bit - Works
Ubuntu Intrepid 64 bit - Doesn't Work

My Dell Laptop:
XP Pro - Works

---

### Post by tkpunk on 2008-11-18
Having pretty much the same problem a-data 8gb drive works in xp, not in kubuntu or ubuntu latest everything. Seems unlikely to be a problem with the physical drive itself if we're both seeing the same problem.

---

### Post by Roasted on 2008-11-18
Is it possible that these a-data drives have something unique about them that would prevent Ubuntu from recognizing it?

The thing is, I used this drive before. In Ubuntu. It worked. It was fully functional. Then bam... yesterday it stopped working.

---

### Post by tkpunk on 2008-11-18
I'm not completely linux savvy, but I update daily. Did you update between the drive working and not working? Could be something funky changed in the kernel or something?

---

### Post by amp_man on 2008-11-18
I'd say something internally stopped working that linux uses to detect the drive, but windows obviously doesn't. I'd suspect a kernel update or some other update broke it, but you've stated you've tried other livecds, which would be other/older kernel versions. One other thing, unplug the drive, and check dmesg. Plug the drive in, and check it again, see if anything pops up that might be interesting.

---

### Post by Roasted on 2008-11-18
I updated several times, yes, but I cannot remember exactly when I updated versus when this drive stopped working. But not only that, why is it when I used Hardy LiveCD (older version of Ubuntu) that it didn't work? How would updates effect a LiveCD that doesn't receive updates? 

This is weird...

dmesg without flash drive plugged in

```
[    0.765526] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.765530] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    0.765533] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.765537] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.765539] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.765543] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    0.765546] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.765551] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.765553] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.765557] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.765560] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f00fffff
[    0.765573] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.765576] pci 0000:00:01.0: setting latency timer to 64
[    0.765582] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.765585] pci 0000:00:1c.0: setting latency timer to 64
[    0.765591] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.765594] pci 0000:00:1c.4: setting latency timer to 64
[    0.765599] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.765603] pci 0000:00:1c.5: setting latency timer to 64
[    0.765608] pci 0000:00:1e.0: setting latency timer to 64
[    0.765611] bus: 00 index 0 io port: [0, ffff]
[    0.765612] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.765614] bus: 01 index 0 io port: [b000, bfff]
[    0.765615] bus: 01 index 1 mmio: [fa000000, fe8fffff]
[    0.765616] bus: 01 index 2 mmio: [c0000000, dfffffff]
[    0.765618] bus: 01 index 3 mmio: [0, 0]
[    0.765619] bus: 04 index 0 mmio: [0, 0]
[    0.765620] bus: 04 index 1 mmio: [0, 0]
[    0.765621] bus: 04 index 2 mmio: [f8f00000, f8ffffff]
[    0.765623] bus: 04 index 3 mmio: [0, 0]
[    0.765624] bus: 03 index 0 io port: [d000, dfff]
[    0.765625] bus: 03 index 1 mmio: [fea00000, feafffff]
[    0.765627] bus: 03 index 2 mmio: [0, 0]
[    0.765628] bus: 03 index 3 mmio: [0, 0]
[    0.765629] bus: 02 index 0 io port: [c000, cfff]
[    0.765631] bus: 02 index 1 mmio: [fe900000, fe9fffff]
[    0.765632] bus: 02 index 2 mmio: [0, 0]
[    0.765633] bus: 02 index 3 mmio: [0, 0]
[    0.765634] bus: 05 index 0 io port: [e000, efff]
[    0.765636] bus: 05 index 1 mmio: [feb00000, febfffff]
[    0.765637] bus: 05 index 2 mmio: [f0000000, f00fffff]
[    0.765638] bus: 05 index 3 io port: [0, ffff]
[    0.765640] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    0.765649] NET: Registered protocol family 2
[    0.808152] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.809219] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.812196] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.812562] TCP: Hash tables configured (established 524288 bind 65536)
[    0.812564] TCP reno registered
[    0.824114] NET: Registered protocol family 1
[    0.824211] checking if image is initramfs... it is
[    1.487283] Freeing initrd memory: 8441k freed
[    1.491273] audit: initializing netlink socket (disabled)
[    1.491291] type=2000 audit(1226969306.488:1): initialized
[    1.496635] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.498804] VFS: Disk quotas dquot_6.5.1
[    1.498871] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.498953] msgmni has been set to 7918
[    1.499047] io scheduler noop registered
[    1.499048] io scheduler anticipatory registered
[    1.499050] io scheduler deadline registered
[    1.499149] io scheduler cfq registered (default)
[    1.499302] pci 0000:01:00.0: Boot video device
[    1.499391] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.499414] pcieport-driver 0000:00:01.0: found MSI capability
[    1.499435] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.499468] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.499529] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.499554] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.499580] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.499613] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.499646] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.499714] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.499740] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.499765] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.499796] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.499827] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.499895] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.499921] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.499946] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.499977] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.500013] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.533439] hpet_resources: 0xfed00000 is busy
[    1.533544] Linux agpgart interface v0.103
[    1.533552] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.533698] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.534438] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.536786] brd: module loaded
[    1.536863] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.537006] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.537012] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.537477] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.557633] mice: PS/2 mouse device common for all mice
[    1.557788] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.557809] rtc0: alarms up to one month, y3k, hpet irqs
[    1.557863] cpuidle: using governor ladder
[    1.557865] cpuidle: using governor menu
[    1.558167] TCP cubic registered
[    1.558411] registered taskstats version 1
[    1.558519]   Magic number: 0:168:810
[    1.558573] tty ptys4: hash matches
[    1.558634] rtc_cmos 00:03: setting system clock to 2008-11-18 00:48:27 UTC (1226969307)
[    1.558641] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.558642] EDD information not available.
[    1.558674] Freeing unused kernel memory: 536k freed
[    1.558804] Write protecting the kernel read-only data: 4348k
[    1.580458] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.642121] fuse init (API version 7.9)
[    1.659307] ACPI: SSDT BFF8E0D0, 01F3 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.659651] processor ACPI0007:00: registered as cooling_device0
[    1.660016] ACPI: SSDT BFF8E2D0, 01F3 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.660343] processor ACPI0007:01: registered as cooling_device1
[    1.660711] ACPI: SSDT BFF8E4D0, 01F3 (r1 DpgPmm  P003Ist       12 INTL 20051117)
[    1.661035] processor ACPI0007:02: registered as cooling_device2
[    1.661397] ACPI: SSDT BFF8E6D0, 01F3 (r1 DpgPmm  P004Ist       12 INTL 20051117)
[    1.661724] processor ACPI0007:03: registered as cooling_device3
[    1.791847] usbcore: registered new interface driver usbfs
[    1.791880] usbcore: registered new interface driver hub
[    1.791922] usbcore: registered new device driver usb
[    1.793402] USB Universal Host Controller Interface driver v3.0
[    1.793448] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.793456] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.793459] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.793499] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.793534] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    1.793685] usb usb1: configuration #1 chosen from 1 choice
[    1.793707] hub 1-0:1.0: USB hub found
[    1.793713] hub 1-0:1.0: 2 ports detected
[    1.801477] No dock devices found.
[    1.810646] SCSI subsystem initialized
[    1.831845] libata version 3.00 loaded.
[    1.896807] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.896818] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.896822] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.896842] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    1.896880] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    1.896956] usb usb2: configuration #1 chosen from 1 choice
[    1.896976] hub 2-0:1.0: USB hub found
[    1.896982] hub 2-0:1.0: 2 ports detected
[    1.898640] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.001100] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.001113] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.001116] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.001141] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.001183] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[    2.001263] usb usb3: configuration #1 chosen from 1 choice
[    2.001284] hub 3-0:1.0: USB hub found
[    2.001291] hub 3-0:1.0: 2 ports detected
[    2.104820] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.104836] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.104840] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.104876] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.108778] ehci_hcd 0000:00:1a.7: debug port 1
[    2.108784] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.108791] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    2.125020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.125146] usb usb4: configuration #1 chosen from 1 choice
[    2.125169] hub 4-0:1.0: USB hub found
[    2.125176] hub 4-0:1.0: 6 ports detected
[    2.229376] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.229386] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.229390] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.229424] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.229456] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    2.229573] usb usb5: configuration #1 chosen from 1 choice
[    2.229594] hub 5-0:1.0: USB hub found
[    2.229600] hub 5-0:1.0: 2 ports detected
[    2.436681] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.436686] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.436689] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.436708] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.436739] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    2.436807] usb usb6: configuration #1 chosen from 1 choice
[    2.436826] hub 6-0:1.0: USB hub found
[    2.436831] hub 6-0:1.0: 2 ports detected
[    2.540260] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.540268] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.540271] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.540294] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.540319] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    2.540395] usb usb7: configuration #1 chosen from 1 choice
[    2.540416] hub 7-0:1.0: USB hub found
[    2.540422] hub 7-0:1.0: 2 ports detected
[    2.552014] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.644297] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.644310] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.644313] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.644344] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.648256] ehci_hcd 0000:00:1d.7: debug port 1
[    2.648261] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.648267] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    2.680009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.680105] usb usb8: configuration #1 chosen from 1 choice
[    2.680129] hub 8-0:1.0: USB hub found
[    2.680134] hub 8-0:1.0: 6 ports detected
[    2.890154] ahci 0000:00:1f.2: version 3.0
[    2.890167] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.890260] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    2.890262] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    2.890266] ahci 0000:00:1f.2: setting latency timer to 64
[    2.890502] scsi0 : ahci
[    2.890591] scsi1 : ahci
[    2.890640] scsi2 : ahci
[    2.890685] scsi3 : ahci
[    2.890734] scsi4 : ahci
[    2.890782] scsi5 : ahci
[    2.890887] ata1: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe900 irq 2299
[    2.890890] ata2: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe980 irq 2299
[    2.890893] ata3: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea00 irq 2299
[    2.890895] ata4: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea80 irq 2299
[    2.890897] ata5: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb00 irq 2299
[    2.890899] ata6: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb80 irq 2299
[    3.080012] usb 5-1: device not accepting address 2, error -71
[    3.136036] hub 5-0:1.0: unable to enumerate USB device on port 1
[    3.372013] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.373397] ata1.00: ATA-8: ST3500320AS, SD81, max UDMA/133
[    3.373400] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.375163] ata1.00: configured for UDMA/133
[    3.432013] usb 8-2: new high speed USB device using ehci_hcd and address 3
[    3.568817] usb 8-2: configuration #1 chosen from 1 choice
[    3.813511] usb 5-1: new low speed USB device using uhci_hcd and address 4
[    3.872013] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.873399] ata2.00: ATA-8: ST3500320AS, SD81, max UDMA/133
[    3.873402] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.875186] ata2.00: configured for UDMA/133
[    3.989560] usb 5-1: configuration #1 chosen from 1 choice
[    4.005584] usbcore: registered new interface driver hiddev
[    4.020164] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input2
[    4.041992] input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:1d.0-1
[    4.042010] usbcore: registered new interface driver usbhid
[    4.043317] usbhid: v2.6:USB HID core driver
[    4.372014] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.372479] ata3.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
[    4.372482] ata3.00: 490234752 sectors, multi 0: LBA48 NCQ (depth 1)
[    4.373040] ata3.00: configured for UDMA/133
[    4.872013] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.872488] ata4.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
[    4.872491] ata4.00: 490234752 sectors, multi 0: LBA48 NCQ (depth 1)
[    4.873023] ata4.00: configured for UDMA/133
[    5.208013] ata5: SATA link down (SStatus 0 SControl 300)
[    5.548019] ata6: SATA link down (SStatus 0 SControl 300)
[    5.564110] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD81 PQ: 0 ANSI: 5
[    5.564227] scsi 1:0:0:0: Direct-Access     ATA      ST3500320AS      SD81 PQ: 0 ANSI: 5
[    5.564323] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
[    5.564417] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
[    5.566293] via-rhine 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.571809] eth0: VIA Rhine III at 0xfebffc00, 00:1b:11:f2:43:16, IRQ 17.
[    5.572517] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[    5.572617] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.572646] pata_acpi 0000:03:00.0: setting latency timer to 64
[    5.572664] pata_acpi 0000:03:00.0: PCI INT A disabled
[    5.574474] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.574494] pata_marvell 0000:03:00.0: setting latency timer to 64
[    5.574554] scsi6 : pata_marvell
[    5.574643] scsi7 : pata_marvell
[    5.574681] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    5.574683] ata8: DUMMY
[    5.585073] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.585105] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    5.585848] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    5.585878] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[    5.598952] Driver 'sd' needs updating - please use bus_type methods
[    5.599053] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.599068] sd 0:0:0:0: [sda] Write Protect is off
[    5.599070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.599093] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.599154] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.599168] sd 0:0:0:0: [sda] Write Protect is off
[    5.599169] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.599195] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.599198]  sda:<6>usbcore: registered new interface driver libusual
[    5.604568]  sda1 sda2 sda3 sda4
[    5.604649] Initializing USB Mass Storage driver...
[    5.604773] scsi8 : SCSI emulation for USB Mass Storage devices
[    5.604877] usbcore: registered new interface driver usb-storage
[    5.604879] USB Mass Storage support registered.
[    5.604984] usb-storage: device found at 3
[    5.604985] usb-storage: waiting for device to settle before scanning
[    5.615621] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.615694] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.615709] sd 1:0:0:0: [sdb] Write Protect is off
[    5.615711] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.615736] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.615787] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.615801] sd 1:0:0:0: [sdb] Write Protect is off
[    5.615802] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.615827] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.615829]  sdb: sdb1
[    5.622916] sd 1:0:0:0: [sdb] Attached SCSI disk
[    5.622975] sd 2:0:0:0: [sdc] 490234752 512-byte hardware sectors (251000 MB)
[    5.622990] sd 2:0:0:0: [sdc] Write Protect is off
[    5.622992] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.623017] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.623072] sd 2:0:0:0: [sdc] 490234752 512-byte hardware sectors (251000 MB)
[    5.623086] sd 2:0:0:0: [sdc] Write Protect is off
[    5.623088] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.623112] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.623115]  sdc: sdc1
[    5.634591] sd 2:0:0:0: [sdc] Attached SCSI disk
[    5.634668] sd 3:0:0:0: [sdd] 490234752 512-byte hardware sectors (251000 MB)
[    5.634683] sd 3:0:0:0: [sdd] Write Protect is off
[    5.634685] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    5.634710] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.634766] sd 3:0:0:0: [sdd] 490234752 512-byte hardware sectors (251000 MB)
[    5.634780] sd 3:0:0:0: [sdd] Write Protect is off
[    5.634782] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    5.634807] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.634810]  sdd: sdd1
[    5.647985] sd 3:0:0:0: [sdd] Attached SCSI disk
[    5.856358] ata7.00: ATAPI: SONY DVD-ROM DDU1615, FYS2, max UDMA/33
[    5.856369] ata7.01: ATAPI: HP      DVD Writer 635d, JPS3, max UDMA/66
[    5.872357] ata7.00: configured for UDMA/33
[    5.888357] ata7.01: configured for UDMA/66
[    5.889014] scsi 6:0:0:0: CD-ROM            SONY     DVD-ROM DDU1615  FYS2 PQ: 0 ANSI: 5
[    5.889167] scsi 6:0:0:0: Attached scsi generic sg4 type 5
[    5.889980] scsi 6:0:1:0: CD-ROM            HP       DVD Writer 635d  JPS3 PQ: 0 ANSI: 5
[    5.890048] scsi 6:0:1:0: Attached scsi generic sg5 type 5
[    5.909923] Driver 'sr' needs updating - please use bus_type methods
[    5.911930] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[    5.911934] Uniform CD-ROM driver Revision: 3.20
[    5.912340] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    5.916341] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.916423] sr 6:0:1:0: Attached scsi CD-ROM sr1
[    6.134011] PM: Starting manual resume from disk
[    6.134013] PM: Resume from partition 8:2
[    6.134015] PM: Checking hibernation image.
[    6.134242] PM: Resume from disk failed.
[    6.146465] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.146468] EXT3-fs: write access will be enabled during recovery.
[    6.209188] kjournald starting.  Commit interval 5 seconds
[    6.209207] EXT3-fs: recovery complete.
[    6.210378] EXT3-fs: mounted filesystem with ordered data mode.
[   10.354980] udevd version 124 started
[   10.609854] usb-storage: device scan complete
[   10.610215] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   10.614069] scsi 8:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[   10.630076] sd 8:0:0:0: [sde] Attached SCSI removable disk
[   10.630173] sd 8:0:0:0: Attached scsi generic sg6 type 0
[   10.632048] ACPI: Power Button (FF) [PWRF]
[   10.632138] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   10.656576] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.664042] ACPI: Power Button (CM) [PWRB]
[   10.684782] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.914542] nvidia: module license 'NVIDIA' taints kernel.
[   11.175249] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.175261] nvidia 0000:01:00.0: setting latency timer to 64
[   11.175413] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   11.181230] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.181243] ATL1E 0000:02:00.0: setting latency timer to 64
[   11.188965] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.276908] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0819
[   11.276928] usbcore: registered new interface driver usblp
[   11.288790] C-Media PCI 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.350486] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.350518] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.382367] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.329083] lp: driver loaded but no devices found
[   12.441836] Adding 1020116k swap on /dev/sda2.  Priority:-1 extents:1 across:1020116k
[   12.985359] EXT3 FS on sda3, internal journal
[   14.904838] kjournald starting.  Commit interval 5 seconds
[   14.905290] EXT3 FS on sda4, internal journal
[   14.905295] EXT3-fs: mounted filesystem with ordered data mode.
[   14.922654] kjournald starting.  Commit interval 5 seconds
[   14.925969] EXT3 FS on sdb1, internal journal
[   14.925974] EXT3-fs: mounted filesystem with ordered data mode.
[   14.928125] kjournald starting.  Commit interval 5 seconds
[   14.928307] EXT3 FS on sdc1, internal journal
[   14.928311] EXT3-fs: mounted filesystem with ordered data mode.
[   14.930362] kjournald starting.  Commit interval 5 seconds
[   14.930531] EXT3 FS on sdd1, internal journal
[   14.930535] EXT3-fs: mounted filesystem with ordered data mode.
[   15.122570] type=1505 audit(1226987320.905:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5060
[   15.234707] type=1505 audit(1226987321.018:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5065
[   15.234852] type=1505 audit(1226987321.018:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5065
[   15.331672] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.758751] ACPI: WMI: Mapper loaded
[   16.458277] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   16.586839] ppdev: user-space parallel port driver
[   18.546898] NET: Registered protocol family 10
[   18.547334] lo: Disabled Privacy Extensions
[   19.453846] Bluetooth: Core ver 2.13
[   19.454490] NET: Registered protocol family 31
[   19.454496] Bluetooth: HCI device and connection manager initialized
[   19.454498] Bluetooth: HCI socket layer initialized
[   19.467749] Bluetooth: L2CAP ver 2.11
[   19.467754] Bluetooth: L2CAP socket layer initialized
[   19.477220] Bluetooth: SCO (Voice Link) ver 0.6
[   19.477225] Bluetooth: SCO socket layer initialized
[   19.485693] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.485698] Bluetooth: BNEP filters: protocol multicast
[   19.548249] Bridge firewalling registered
[   19.548489] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   19.661430] Bluetooth: RFCOMM socket layer initialized
[   19.661444] Bluetooth: RFCOMM TTY layer initialized
[   19.661446] Bluetooth: RFCOMM ver 1.10
[   23.734120] eth0: link down
[   23.734731] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.735563] ATL1E 0000:02:00.0: ATL1E: eth1 NIC Link is Up<100 Mbps Full Duplex>
[   23.736115] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   23.736735] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   23.865760] NET: Registered protocol family 17
[   33.760508] eth1: no IPv6 routers present
[   57.012044] usb 4-5: new high speed USB device using ehci_hcd and address 2
[   57.145621] usb 4-5: configuration #1 chosen from 1 choice
[   57.152391] scsi9 : SCSI emulation for USB Mass Storage devices
[   57.153422] usb-storage: device found at 2
[   57.153430] usb-storage: waiting for device to settle before scanning
[   62.152187] usb-storage: device scan complete
[   67.768037] usb 4-5: reset high speed USB device using ehci_hcd and address 2
[   82.876042] usb 4-5: device descriptor read/64, error -110
[   98.092044] usb 4-5: device descriptor read/64, error -110
[   98.308042] usb 4-5: reset high speed USB device using ehci_hcd and address 2
[  113.420017] usb 4-5: device descriptor read/64, error -110
[  128.636014] usb 4-5: device descriptor read/64, error -110
[  128.852015] usb 4-5: reset high speed USB device using ehci_hcd and address 2
[  139.260014] usb 4-5: device not accepting address 2, error -110
[  139.372013] usb 4-5: reset high speed USB device using ehci_hcd and address 2
[  149.780011] usb 4-5: device not accepting address 2, error -110
[  149.780053] usb 4-5: USB disconnect, address 2
[  149.780350] scsi 9:0:0:0: Device offlined - not ready after error recovery
[  149.892025] usb 4-5: new high speed USB device using ehci_hcd and address 3
[  165.008014] usb 4-5: device descriptor read/64, error -110
[  180.220014] usb 4-5: device descriptor read/64, error -110
[  180.436015] usb 4-5: new high speed USB device using ehci_hcd and address 4
[  195.549015] usb 4-5: device descriptor read/64, error -110
[  210.764020] usb 4-5: device descriptor read/64, error -110
[  210.980024] usb 4-5: new high speed USB device using ehci_hcd and address 5
[  221.388015] usb 4-5: device not accepting address 5, error -110
[  221.501027] usb 4-5: new high speed USB device using ehci_hcd and address 6
[  231.908512] usb 4-5: device not accepting address 6, error -110
[  231.908649] hub 4-0:1.0: unable to enumerate USB device on port 5
[  232.176014] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  247.288014] usb 3-1: device descriptor read/64, error -110
[  262.504512] usb 3-1: device descriptor read/64, error -110
[  262.720510] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  277.832018] usb 3-1: device descriptor read/64, error -110
[  293.048013] usb 3-1: device descriptor read/64, error -110
[  293.264012] usb 3-1: new full speed USB device using uhci_hcd and address 4
[  303.672009] usb 3-1: device not accepting address 4, error -110
[  303.784510] usb 3-1: new full speed USB device using uhci_hcd and address 5
[  314.192010] usb 3-1: device not accepting address 5, error -110
[  314.192145] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 2432.932016] usb 4-5: new high speed USB device using ehci_hcd and address 7
[ 2433.066224] usb 4-5: configuration #1 chosen from 1 choice
[ 2433.068180] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2433.069079] usb-storage: device found at 7
[ 2433.069085] usb-storage: waiting for device to settle before scanning
[ 2433.582346] usb 4-5: USB disconnect, address 7
jason@jason-intrepid:~$ 

```


dmesg with flash drive plugged in

```
[    0.765526] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.765530] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    0.765533] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.765537] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.765539] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.765543] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    0.765546] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.765551] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.765553] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.765557] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.765560] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f00fffff
[    0.765573] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.765576] pci 0000:00:01.0: setting latency timer to 64
[    0.765582] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.765585] pci 0000:00:1c.0: setting latency timer to 64
[    0.765591] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.765594] pci 0000:00:1c.4: setting latency timer to 64
[    0.765599] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.765603] pci 0000:00:1c.5: setting latency timer to 64
[    0.765608] pci 0000:00:1e.0: setting latency timer to 64
[    0.765611] bus: 00 index 0 io port: [0, ffff]
[    0.765612] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.765614] bus: 01 index 0 io port: [b000, bfff]
[    0.765615] bus: 01 index 1 mmio: [fa000000, fe8fffff]
[    0.765616] bus: 01 index 2 mmio: [c0000000, dfffffff]
[    0.765618] bus: 01 index 3 mmio: [0, 0]
[    0.765619] bus: 04 index 0 mmio: [0, 0]
[    0.765620] bus: 04 index 1 mmio: [0, 0]
[    0.765621] bus: 04 index 2 mmio: [f8f00000, f8ffffff]
[    0.765623] bus: 04 index 3 mmio: [0, 0]
[    0.765624] bus: 03 index 0 io port: [d000, dfff]
[    0.765625] bus: 03 index 1 mmio: [fea00000, feafffff]
[    0.765627] bus: 03 index 2 mmio: [0, 0]
[    0.765628] bus: 03 index 3 mmio: [0, 0]
[    0.765629] bus: 02 index 0 io port: [c000, cfff]
[    0.765631] bus: 02 index 1 mmio: [fe900000, fe9fffff]
[    0.765632] bus: 02 index 2 mmio: [0, 0]
[    0.765633] bus: 02 index 3 mmio: [0, 0]
[    0.765634] bus: 05 index 0 io port: [e000, efff]
[    0.765636] bus: 05 index 1 mmio: [feb00000, febfffff]
[    0.765637] bus: 05 index 2 mmio: [f0000000, f00fffff]
[    0.765638] bus: 05 index 3 io port: [0, ffff]
[    0.765640] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    0.765649] NET: Registered protocol family 2
[    0.808152] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.809219] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.812196] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.812562] TCP: Hash tables configured (established 524288 bind 65536)
[    0.812564] TCP reno registered
[    0.824114] NET: Registered protocol family 1
[    0.824211] checking if image is initramfs... it is
[    1.487283] Freeing initrd memory: 8441k freed
[    1.491273] audit: initializing netlink socket (disabled)
[    1.491291] type=2000 audit(1226969306.488:1): initialized
[    1.496635] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.498804] VFS: Disk quotas dquot_6.5.1
[    1.498871] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.498953] msgmni has been set to 7918
[    1.499047] io scheduler noop registered
[    1.499048] io scheduler anticipatory registered
[    1.499050] io scheduler deadline registered
[    1.499149] io scheduler cfq registered (default)
[    1.499302] pci 0000:01:00.0: Boot video device
[    1.499391] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.499414] pcieport-driver 0000:00:01.0: found MSI capability
[    1.499435] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.499468] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.499529] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.499554] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.499580] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.499613] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.499646] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.499714] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.499740] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.499765] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.499796] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.499827] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.499895] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.499921] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.499946] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.499977] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.500013] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.533439] hpet_resources: 0xfed00000 is busy
[    1.533544] Linux agpgart interface v0.103
[    1.533552] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.533698] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.534438] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.536786] brd: module loaded
[    1.536863] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.537006] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.537012] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.537477] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.557633] mice: PS/2 mouse device common for all mice
[    1.557788] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.557809] rtc0: alarms up to one month, y3k, hpet irqs
[    1.557863] cpuidle: using governor ladder
[    1.557865] cpuidle: using governor menu
[    1.558167] TCP cubic registered
[    1.558411] registered taskstats version 1
[    1.558519]   Magic number: 0:168:810
[    1.558573] tty ptys4: hash matches
[    1.558634] rtc_cmos 00:03: setting system clock to 2008-11-18 00:48:27 UTC (1226969307)
[    1.558641] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.558642] EDD information not available.
[    1.558674] Freeing unused kernel memory: 536k freed
[    1.558804] Write protecting the kernel read-only data: 4348k
[    1.580458] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.642121] fuse init (API version 7.9)
[    1.659307] ACPI: SSDT BFF8E0D0, 01F3 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.659651] processor ACPI0007:00: registered as cooling_device0
[    1.660016] ACPI: SSDT BFF8E2D0, 01F3 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.660343] processor ACPI0007:01: registered as cooling_device1
[    1.660711] ACPI: SSDT BFF8E4D0, 01F3 (r1 DpgPmm  P003Ist       12 INTL 20051117)
[    1.661035] processor ACPI0007:02: registered as cooling_device2
[    1.661397] ACPI: SSDT BFF8E6D0, 01F3 (r1 DpgPmm  P004Ist       12 INTL 20051117)
[    1.661724] processor ACPI0007:03: registered as cooling_device3
[    1.791847] usbcore: registered new interface driver usbfs
[    1.791880] usbcore: registered new interface driver hub
[    1.791922] usbcore: registered new device driver usb
[    1.793402] USB Universal Host Controller Interface driver v3.0
[    1.793448] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.793456] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.793459] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.793499] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.793534] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    1.793685] usb usb1: configuration #1 chosen from 1 choice
[    1.793707] hub 1-0:1.0: USB hub found
[    1.793713] hub 1-0:1.0: 2 ports detected
[    1.801477] No dock devices found.
[    1.810646] SCSI subsystem initialized
[    1.831845] libata version 3.00 loaded.
[    1.896807] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.896818] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.896822] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.896842] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    1.896880] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    1.896956] usb usb2: configuration #1 chosen from 1 choice
[    1.896976] hub 2-0:1.0: USB hub found
[    1.896982] hub 2-0:1.0: 2 ports detected
[    1.898640] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.001100] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.001113] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.001116] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.001141] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.001183] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[    2.001263] usb usb3: configuration #1 chosen from 1 choice
[    2.001284] hub 3-0:1.0: USB hub found
[    2.001291] hub 3-0:1.0: 2 ports detected
[    2.104820] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.104836] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.104840] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.104876] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.108778] ehci_hcd 0000:00:1a.7: debug port 1
[    2.108784] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.108791] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    2.125020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.125146] usb usb4: configuration #1 chosen from 1 choice
[    2.125169] hub 4-0:1.0: USB hub found
[    2.125176] hub 4-0:1.0: 6 ports detected
[    2.229376] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.229386] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.229390] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.229424] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.229456] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    2.229573] usb usb5: configuration #1 chosen from 1 choice
[    2.229594] hub 5-0:1.0: USB hub found
[    2.229600] hub 5-0:1.0: 2 ports detected
[    2.436681] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.436686] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.436689] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.436708] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.436739] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    2.436807] usb usb6: configuration #1 chosen from 1 choice
[    2.436826] hub 6-0:1.0: USB hub found
[    2.436831] hub 6-0:1.0: 2 ports detected
[    2.540260] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.540268] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.540271] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.540294] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.540319] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    2.540395] usb usb7: configuration #1 chosen from 1 choice
[    2.540416] hub 7-0:1.0: USB hub found
[    2.540422] hub 7-0:1.0: 2 ports detected
[    2.552014] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.644297] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.644310] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.644313] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.644344] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.648256] ehci_hcd 0000:00:1d.7: debug port 1
[    2.648261] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.648267] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    2.680009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.680105] usb usb8: configuration #1 chosen from 1 choice
[    2.680129] hub 8-0:1.0: USB hub found
[    2.680134] hub 8-0:1.0: 6 ports detected
[    2.890154] ahci 0000:00:1f.2: version 3.0
[    2.890167] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.890260] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    2.890262] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    2.890266] ahci 0000:00:1f.2: setting latency timer to 64
[    2.890502] scsi0 : ahci
[    2.890591] scsi1 : ahci
[    2.890640] scsi2 : ahci
[    2.890685] scsi3 : ahci
[    2.890734] scsi4 : ahci
[    2.890782] scsi5 : ahci
[    2.890887] ata1: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe900 irq 2299
[    2.890890] ata2: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe980 irq 2299
[    2.890893] ata3: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea00 irq 2299
[    2.890895] ata4: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea80 irq 2299
[    2.890897] ata5: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb00 irq 2299
[    2.890899] ata6: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb80 irq 2299
[    3.080012] usb 5-1: device not accepting address 2, error -71
[    3.136036] hub 5-0:1.0: unable to enumerate USB device on port 1
[    3.372013] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.373397] ata1.00: ATA-8: ST3500320AS, SD81, max UDMA/133
[    3.373400] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.375163] ata1.00: configured for UDMA/133
[    3.432013] usb 8-2: new high speed USB device using ehci_hcd and address 3
[    3.568817] usb 8-2: configuration #1 chosen from 1 choice
[    3.813511] usb 5-1: new low speed USB device using uhci_hcd and address 4
[    3.872013] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.873399] ata2.00: ATA-8: ST3500320AS, SD81, max UDMA/133
[    3.873402] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.875186] ata2.00: configured for UDMA/133
[    3.989560] usb 5-1: configuration #1 chosen from 1 choice
[    4.005584] usbcore: registered new interface driver hiddev
[    4.020164] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input2
[    4.041992] input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:1d.0-1
[    4.042010] usbcore: registered new interface driver usbhid
[    4.043317] usbhid: v2.6:USB HID core driver
[    4.372014] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.372479] ata3.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
[    4.372482] ata3.00: 490234752 sectors, multi 0: LBA48 NCQ (depth 1)
[    4.373040] ata3.00: configured for UDMA/133
[    4.872013] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.872488] ata4.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
[    4.872491] ata4.00: 490234752 sectors, multi 0: LBA48 NCQ (depth 1)
[    4.873023] ata4.00: configured for UDMA/133
[    5.208013] ata5: SATA link down (SStatus 0 SControl 300)
[    5.548019] ata6: SATA link down (SStatus 0 SControl 300)
[    5.564110] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD81 PQ: 0 ANSI: 5
[    5.564227] scsi 1:0:0:0: Direct-Access     ATA      ST3500320AS      SD81 PQ: 0 ANSI: 5
[    5.564323] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
[    5.564417] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
[    5.566293] via-rhine 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.571809] eth0: VIA Rhine III at 0xfebffc00, 00:1b:11:f2:43:16, IRQ 17.
[    5.572517] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[    5.572617] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.572646] pata_acpi 0000:03:00.0: setting latency timer to 64
[    5.572664] pata_acpi 0000:03:00.0: PCI INT A disabled
[    5.574474] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.574494] pata_marvell 0000:03:00.0: setting latency timer to 64
[    5.574554] scsi6 : pata_marvell
[    5.574643] scsi7 : pata_marvell
[    5.574681] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    5.574683] ata8: DUMMY
[    5.585073] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.585105] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    5.585848] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    5.585878] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[    5.598952] Driver 'sd' needs updating - please use bus_type methods
[    5.599053] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.599068] sd 0:0:0:0: [sda] Write Protect is off
[    5.599070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.599093] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.599154] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.599168] sd 0:0:0:0: [sda] Write Protect is off
[    5.599169] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.599195] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.599198]  sda:<6>usbcore: registered new interface driver libusual
[    5.604568]  sda1 sda2 sda3 sda4
[    5.604649] Initializing USB Mass Storage driver...
[    5.604773] scsi8 : SCSI emulation for USB Mass Storage devices
[    5.604877] usbcore: registered new interface driver usb-storage
[    5.604879] USB Mass Storage support registered.
[    5.604984] usb-storage: device found at 3
[    5.604985] usb-storage: waiting for device to settle before scanning
[    5.615621] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.615694] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.615709] sd 1:0:0:0: [sdb] Write Protect is off
[    5.615711] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.615736] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.615787] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.615801] sd 1:0:0:0: [sdb] Write Protect is off
[    5.615802] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.615827] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.615829]  sdb: sdb1
[    5.622916] sd 1:0:0:0: [sdb] Attached SCSI disk
[    5.622975] sd 2:0:0:0: [sdc] 490234752 512-byte hardware sectors (251000 MB)
[    5.622990] sd 2:0:0:0: [sdc] Write Protect is off
[    5.622992] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.623017] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.623072] sd 2:0:0:0: [sdc] 490234752 512-byte hardware sectors (251000 MB)
[    5.623086] sd 2:0:0:0: [sdc] Write Protect is off
[    5.623088] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.623112] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.623115]  sdc: sdc1
[    5.634591] sd 2:0:0:0: [sdc] Attached SCSI disk
[    5.634668] sd 3:0:0:0: [sdd] 490234752 512-byte hardware sectors (251000 MB)
[    5.634683] sd 3:0:0:0: [sdd] Write Protect is off
[    5.634685] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    5.634710] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.634766] sd 3:0:0:0: [sdd] 490234752 512-byte hardware sectors (251000 MB)
[    5.634780] sd 3:0:0:0: [sdd] Write Protect is off
[    5.634782] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    5.634807] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.634810]  sdd: sdd1
[    5.647985] sd 3:0:0:0: [sdd] Attached SCSI disk
[    5.856358] ata7.00: ATAPI: SONY DVD-ROM DDU1615, FYS2, max UDMA/33
[    5.856369] ata7.01: ATAPI: HP      DVD Writer 635d, JPS3, max UDMA/66
[    5.872357] ata7.00: configured for UDMA/33
[    5.888357] ata7.01: configured for UDMA/66
[    5.889014] scsi 6:0:0:0: CD-ROM            SONY     DVD-ROM DDU1615  FYS2 PQ: 0 ANSI: 5
[    5.889167] scsi 6:0:0:0: Attached scsi generic sg4 type 5
[    5.889980] scsi 6:0:1:0: CD-ROM            HP       DVD Writer 635d  JPS3 PQ: 0 ANSI: 5
[    5.890048] scsi 6:0:1:0: Attached scsi generic sg5 type 5
[    5.909923] Driver 'sr' needs updating - please use bus_type methods
[    5.911930] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[    5.911934] Uniform CD-ROM driver Revision: 3.20
[    5.912340] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    5.916341] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.916423] sr 6:0:1:0: Attached scsi CD-ROM sr1
[    6.134011] PM: Starting manual resume from disk
[    6.134013] PM: Resume from partition 8:2
[    6.134015] PM: Checking hibernation image.
[    6.134242] PM: Resume from disk failed.
[    6.146465] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.146468] EXT3-fs: write access will be enabled during recovery.
[    6.209188] kjournald starting.  Commit interval 5 seconds
[    6.209207] EXT3-fs: recovery complete.
[    6.210378] EXT3-fs: mounted filesystem with ordered data mode.
[   10.354980] udevd version 124 started
[   10.609854] usb-storage: device scan complete
[   10.610215] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   10.614069] scsi 8:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[   10.630076] sd 8:0:0:0: [sde] Attached SCSI removable disk
[   10.630173] sd 8:0:0:0: Attached scsi generic sg6 type 0
[   10.632048] ACPI: Power Button (FF) [PWRF]
[   10.632138] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   10.656576] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.664042] ACPI: Power Button (CM) [PWRB]
[   10.684782] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.914542] nvidia: module license 'NVIDIA' taints kernel.
[   11.175249] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.175261] nvidia 0000:01:00.0: setting latency timer to 64
[   11.175413] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   11.181230] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.181243] ATL1E 0000:02:00.0: setting latency timer to 64
[   11.188965] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.276908] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0819
[   11.276928] usbcore: registered new interface driver usblp
[   11.288790] C-Media PCI 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.350486] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.350518] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.382367] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.329083] lp: driver loaded but no devices found
[   12.441836] Adding 1020116k swap on /dev/sda2.  Priority:-1 extents:1 across:1020116k
[   12.985359] EXT3 FS on sda3, internal journal
[   14.904838] kjournald starting.  Commit interval 5 seconds
[   14.905290] EXT3 FS on sda4, internal journal
[   14.905295] EXT3-fs: mounted filesystem with ordered data mode.
[   14.922654] kjournald starting.  Commit interval 5 seconds
[   14.925969] EXT3 FS on sdb1, internal journal
[   14.925974] EXT3-fs: mounted filesystem with ordered data mode.
[   14.928125] kjournald starting.  Commit interval 5 seconds
[   14.928307] EXT3 FS on sdc1, internal journal
[   14.928311] EXT3-fs: mounted filesystem with ordered data mode.
[   14.930362] kjournald starting.  Commit interval 5 seconds
[   14.930531] EXT3 FS on sdd1, internal journal
[   14.930535] EXT3-fs: mounted filesystem with ordered data mode.
[   15.122570] type=1505 audit(1226987320.905:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5060
[   15.234707] type=1505 audit(1226987321.018:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5065
[   15.234852] type=1505 audit(1226987321.018:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5065
[   15.331672] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.758751] ACPI: WMI: Mapper loaded
[   16.458277] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   16.586839] ppdev: user-space parallel port driver
[   18.546898] NET: Registered protocol family 10
[   18.547334] lo: Disabled Privacy Extensions
[   19.453846] Bluetooth: Core ver 2.13
[   19.454490] NET: Registered protocol family 31
[   19.454496] Bluetooth: HCI device and connection manager initialized
[   19.454498] Bluetooth: HCI socket layer initialized
[   19.467749] Bluetooth: L2CAP ver 2.11
[   19.467754] Bluetooth: L2CAP socket layer initialized
[   19.477220] Bluetooth: SCO (Voice Link) ver 0.6
[   19.477225] Bluetooth: SCO socket layer initialized
[   19.485693] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.485698] Bluetooth: BNEP filters: protocol multicast
[   19.548249] Bridge firewalling registered
[   19.548489] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   19.661430] Bluetooth: RFCOMM socket layer initialized
[   19.661444] Bluetooth: RFCOMM TTY layer initialized
[   19.661446] Bluetooth: RFCOMM ver 1.10
[   23.734120] eth0: link down
[   23.734731] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.735563] ATL1E 0000:02:00.0: ATL1E: eth1 NIC Link is Up<100 Mbps Full Duplex>
[   23.736115] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   23.736735] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   23.865760] NET: Registered protocol family 17
[   33.760508] eth1: no IPv6 routers present
[   57.012044] usb 4-5: new high speed USB device using ehci_hcd and address 2
[   57.145621] usb 4-5: configuration #1 chosen from 1 choice
[   57.152391] scsi9 : SCSI emulation for USB Mass Storage devices
[   57.153422] usb-storage: device found at 2
[   57.153430] usb-storage: waiting for device to settle before scanning
[   62.152187] usb-storage: device scan complete
[   67.768037] usb 4-5: reset high speed USB device using ehci_hcd and address 2
[   82.876042] usb 4-5: device descriptor read/64, error -110
[   98.092044] usb 4-5: device descriptor read/64, error -110
[   98.308042] usb 4-5: reset high speed USB device using ehci_hcd and address 2
[  113.420017] usb 4-5: device descriptor read/64, error -110
[  128.636014] usb 4-5: device descriptor read/64, error -110
[  128.852015] usb 4-5: reset high speed USB device using ehci_hcd and address 2
[  139.260014] usb 4-5: device not accepting address 2, error -110
[  139.372013] usb 4-5: reset high speed USB device using ehci_hcd and address 2
[  149.780011] usb 4-5: device not accepting address 2, error -110
[  149.780053] usb 4-5: USB disconnect, address 2
[  149.780350] scsi 9:0:0:0: Device offlined - not ready after error recovery
[  149.892025] usb 4-5: new high speed USB device using ehci_hcd and address 3
[  165.008014] usb 4-5: device descriptor read/64, error -110
[  180.220014] usb 4-5: device descriptor read/64, error -110
[  180.436015] usb 4-5: new high speed USB device using ehci_hcd and address 4
[  195.549015] usb 4-5: device descriptor read/64, error -110
[  210.764020] usb 4-5: device descriptor read/64, error -110
[  210.980024] usb 4-5: new high speed USB device using ehci_hcd and address 5
[  221.388015] usb 4-5: device not accepting address 5, error -110
[  221.501027] usb 4-5: new high speed USB device using ehci_hcd and address 6
[  231.908512] usb 4-5: device not accepting address 6, error -110
[  231.908649] hub 4-0:1.0: unable to enumerate USB device on port 5
[  232.176014] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  247.288014] usb 3-1: device descriptor read/64, error -110
[  262.504512] usb 3-1: device descriptor read/64, error -110
[  262.720510] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  277.832018] usb 3-1: device descriptor read/64, error -110
[  293.048013] usb 3-1: device descriptor read/64, error -110
[  293.264012] usb 3-1: new full speed USB device using uhci_hcd and address 4
[  303.672009] usb 3-1: device not accepting address 4, error -110
[  303.784510] usb 3-1: new full speed USB device using uhci_hcd and address 5
[  314.192010] usb 3-1: device not accepting address 5, error -110
[  314.192145] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 2432.932016] usb 4-5: new high speed USB device using ehci_hcd and address 7
[ 2433.066224] usb 4-5: configuration #1 chosen from 1 choice
[ 2433.068180] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2433.069079] usb-storage: device found at 7
[ 2433.069085] usb-storage: waiting for device to settle before scanning
[ 2433.582346] usb 4-5: USB disconnect, address 7
jason@jason-intrepid:~$ 

```


I have no idea what in particular I'm looking for in the dmesg's of each... can anybody tell?


EDIT - just a random thing I came across. I have a Motorola Razr V3xx. It has a usb port on the side, and I just plugged it in to my computer. It mounted just fine. My external USB HDD mounted just fine. The wireless usb adapter works. My USB mouse works. Printer, etc... all work. EXCEPT MY FLASH DRIVE THAT I USE ALL THE FRICKEN TIME.

Ahh... I love it when things "just work." :) 

Who can we blame here? Ubuntu? A-Data? Where would the problem lie?

---

### Post by thejo on 2008-11-18
I have the same problem with my flashdrive and my usb harddisk. I have got a numericpad at my laptop with two usb ports, in one of it I have put my mouse on. When I put in the other my flashdisk or usb harddisk they both are automatically mounted and I can use them. I think that ubuntu only supports one usbport at the same time. When I am starting my system I am seeing the error message that usb don't accept an address resulting in error 110. I am a absolute beginner with ubuntu but I shall try an usbhub and see if the ports on the hub are all working. [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by Roasted on 2008-11-18
Do you have these devices plugged in while booting up? I don't know how the reaction with Ubuntu is when booting up, but when I shut down if my flash drive is plugged in I get the error 110 you spoke about. Once I disconnect it, the system reboots. It's as if it can't unmount the flash drive while the system is shutting down, so it errors out until I remove it.

And I hate to disagree with you but I don't think Ubuntu has a limitation on only supporting one USB device at once. Otherwise how did I get my cell phone, external HDD, mouse, and printer all hooked up and responding at the same time? In my case, it's ONLY my flash drive that is problematic... and unfortunately I don't have a second flash drive to test... the next best thing I got is an external HDD... which works fine...

What kind of flash drive do you have?

---

### Post by thejo on 2008-11-18
Yes I thought it was strange, if ubuntu supports only one usb port. But I have bought an usbhub and now I have attached a numpad, a mouse my dane elec 8 Gb flash disk, a usb teac harddisk (250 Gb) and all are working fine. When I put the flashdisk in a usb slot on the hub it is mounted automaticaly.All the other ports on my laptop are not working with ubuntu (I have got 4 usb ports on my laptop). Why, is a big mystery for me.

---

### Post by Roasted on 2008-11-18
Wait wait wait wait...

When you plug your flash drive into a USB port on your computer, it does NOT work.

But

When you plug a USB hub into a USB port on your computer, and then plug in your flash drive to the USB hub... it works?

Are you serious?

I have a PCI card with 2 USB ports on it laying around. Maybe I could try that for kicks and giggles??

---

### Post by tkpunk on 2008-11-18
Looks like my situation's a little different. dmesg produces:

```
[ 1411.060308] usb 5-1: new high speed USB device using ehci_hcd and address 8                                                                        
[ 1411.212873] usb 5-1: configuration #1 chosen from 1 choice              
[ 1411.257903] scsi8 : SCSI emulation for USB Mass Storage devices         
[ 1411.262374] usb-storage: device found at 8                              
[ 1411.262385] usb-storage: waiting for device to settle before scanning   
[ 1416.260330] usb-storage: device scan complete                           
[ 1416.261420] scsi 8:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2                                                           
[ 1416.275025] sd 8:0:0:0: [sdc] 15794176 512-byte hardware sectors (8087 MB)                                                                         
[ 1416.275886] sd 8:0:0:0: [sdc] Write Protect is off                      
[ 1416.275893] sd 8:0:0:0: [sdc] Mode Sense: 00 00 00 00                   
[ 1416.275897] sd 8:0:0:0: [sdc] Assuming drive cache: write through       
[ 1416.278638] sd 8:0:0:0: [sdc] 15794176 512-byte hardware sectors (8087 MB)                                                                         
[ 1416.279385] sd 8:0:0:0: [sdc] Write Protect is off                      
[ 1416.279392] sd 8:0:0:0: [sdc] Mode Sense: 00 00 00 00                   
[ 1416.279396] sd 8:0:0:0: [sdc] Assuming drive cache: write through       
[ 1416.279821]  sdc: sdc1                                                  
[ 1416.713089] sd 8:0:0:0: [sdc] Attached SCSI removable disk              
[ 1416.713489] sd 8:0:0:0: Attached scsi generic sg2 type 0                
[ 1456.602523] usb 5-1: USB disconnect, address 8                          
[ 1460.144087] usb 5-1: new high speed USB device using ehci_hcd and address 9                                                                        
[ 1460.278045] usb 5-1: configuration #1 chosen from 1 choice              
[ 1460.323189] scsi9 : SCSI emulation for USB Mass Storage devices         
[ 1460.332182] usb-storage: device found at 9                              
[ 1460.332191] usb-storage: waiting for device to settle before scanning   
[ 1465.332236] usb-storage: device scan complete                           
[ 1465.333212] scsi 9:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2                                                           
[ 1465.347310] sd 9:0:0:0: [sdc] 15794176 512-byte hardware sectors (8087 MB)                                                                         
[ 1465.348171] sd 9:0:0:0: [sdc] Write Protect is off                      
[ 1465.348179] sd 9:0:0:0: [sdc] Mode Sense: 00 00 00 00                   
[ 1465.348183] sd 9:0:0:0: [sdc] Assuming drive cache: write through       
[ 1465.350542] sd 9:0:0:0: [sdc] 15794176 512-byte hardware sectors (8087 MB)                                                                         
[ 1465.351291] sd 9:0:0:0: [sdc] Write Protect is off                      
[ 1465.351298] sd 9:0:0:0: [sdc] Mode Sense: 00 00 00 00                   
[ 1465.351301] sd 9:0:0:0: [sdc] Assuming drive cache: write through       
[ 1465.351722]  sdc: sdc1                                                  
[ 1465.784756] sd 9:0:0:0: [sdc] Attached SCSI removable disk              
[ 1465.791847] sd 9:0:0:0: Attached scsi generic sg2 type 0                
[ 1571.072178] usb 5-1: USB disconnect, address 9                          
[ 1572.948088] usb 5-1: new high speed USB device using ehci_hcd and address 10                                                                       
[ 1573.081992] usb 5-1: configuration #1 chosen from 1 choice              
[ 1573.090052] scsi10 : SCSI emulation for USB Mass Storage devices        
[ 1573.091855] usb-storage: device found at 10                             
[ 1573.091864] usb-storage: waiting for device to settle before scanning   
[ 1578.088314] usb-storage: device scan complete                           
[ 1578.089408] scsi 10:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2                                                          
[ 1578.103502] sd 10:0:0:0: [sdc] 15794176 512-byte hardware sectors (8087MB)
[ 1578.104815] sd 10:0:0:0: [sdc] Write Protect is off
[ 1578.104825] sd 10:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 1578.104828] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 1578.107250] sd 10:0:0:0: [sdc] 15794176 512-byte hardware sectors (8087MB)
[ 1578.108128] sd 10:0:0:0: [sdc] Write Protect is off
[ 1578.108135] sd 10:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 1578.108139] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 1578.108596]  sdc: sdc1
[ 1578.541910] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[ 1578.542295] sd 10:0:0:0: Attached scsi generic sg2 type 0

```

So it sees it, but I can't get to it?

---

### Post by Roasted on 2008-11-19
Do you guys think I should RMA this flash drive and see if a new one works? It makes no sense that it worked before, but not now.  Yet it works in Vista and XP, just not Ubuntu...

I have 4 days left that I can RMA this. Any thoughts?

---

### Post by tkpunk on 2008-11-19
okay, i think i got mine working now. I ran fsck and fixed what I think were a bunch of bad blocks, and was able to mount.

---

### Post by Roasted on 2008-11-19
Do you mind telling me exactly what you've done, step by step? I don't recall ever running fsck.

---

### Post by Roasted on 2008-11-20
So, tonight I bit the bullet. I found a Sandisk 8gb flash drive at wal mart for 24 bucks. My girlfriend and I were there looking for a flash drive for her since she didn't have one, and I saw tux the penguin on the back and just HAD to try it.

This flash drive mounts absolutely fine. I have no problems whatsoever. Yet my A-DATA does not mount as it should. I'm so confused, I could have sworn this thing was indeed working before. In fact I'd bet my car on it. I don't get what happened.

But I figured the smart thing to do was try a flash drive that says on the box it's supported by Linux. So, I did, and it works.

Ahhh!

Anybody have any clue what's up with the A-DATA? I have two days to RMA it. Should I give that a shot?

---

