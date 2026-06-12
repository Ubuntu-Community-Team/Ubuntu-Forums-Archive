---
title: "Newbie - need help with Compro VideoMate DVB-T300 install and TV App"
date: 2010-03-09
forum: Hardware
---

### Post by comprodtv on 2010-03-09
G'Day Guru's,
 
My seond post - Am still a newbie to Ubuntu - please be nice/patient with me.
 
Need some help how to get Compro VideoMate DVB-T300 to work and which TV App to use.
 
_**History:**_
Installed Ubuntu 9.10 (with latest kernel) a few weeks ago on PC. Made this a dual boot with my WinXP SP3. (aim is to eventually ditch WinXP :wink:).
 
_PC:_
Mobo: Asus A8N-E
CPU: AMD Athlon 64 3500+
TV Card: Compro DVB-T300
and some other stuff....
 
**_Problems:_**
Since making the Dual-boot, the ComproDTV App in WinXP started flashing up as soon as I log into WinXP. --- Strange as this card never had issue in WinXP. It seems like if i stop the T-300 remote app, it stops flashing up the ComproDTV App. Great, but, the Card does not want to display any Digital Channels. Am suspecting this has somthing to do with the Ubuntu install.
 
Am hoping to try and get this card working in Ubuntu as this may solve the issues in WinXP.
 
_Questions:_
1) Has enyone encountered this problem with dual-boot before?
2) What TV App from the Ubuntu Software Center can I download for Digital DV watching (Aust-Sydney)?
3) What do I need to do to get this card working (as i read some of these threads and seems like this card is having issues with Ubuntu - albeit the posts were using an older version of Ubuntu).
 
 
 
Some stuff i read about:
Need to add to Options via Terminal (but do not want to as yet as other solutions may be available...):
For the Australian **[COLOR=#ff0000]Compro[/COLOR]** VideoMate DVB-T300
saa7134 **[COLOR=#ff0000]card[/COLOR]**=70 tuner=67
 
 
 
appreciate your support.

---

### Post by comprodtv on 2010-03-17
can someone please help this newbie.  linux is his mater at this stage and needs some help to make it linux the slave.

---

### Post by comprodtv on 2010-03-22
sudo lshw -C multimedia *-multimedia 
        description: Multimedia controller 
        product: SAA7134/SAA7135HL Video Broadcast Decoder 
        vendor: Philips Semiconductors 
        physical id: 7 
        bus info: pci@0000:05:07.0 
        version: 01 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list 
        configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=20 
        resources: irq:17 memory:d0010000-d00103ff 





   	 	 	 	 	 	  

 dmesg | grep saa


 [   18.293973] saa7130/34: v4l2 driver version 0.2.15 loaded 
 [   18.294227] saa7134 0000:05:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17 
 [   18.294234] saa7134[0]: found at 0000:05:07.0, rev: 1, irq: 17, latency: 32, mmio: 0xd0010000 
 [   18.294240] saa7134[0]: subsystem: 1850:0000, board: UNKNOWN/GENERIC [card=0,autodetected] 
 [   18.294252] saa7134[0]: board init: gpio is 843f00 
 [   18.294259] IRQ 17/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs 
 [   18.591062] saa7134[0]: i2c eeprom 00: 02 10 00 01 04 00 1c 00 40 03 00 10 04 00 82 10 
 [   18.591072] saa7134[0]: i2c eeprom 10: 00 e7 02 00 01 00 10 26 52 41 c0 06 f8 ed cb 00 
 [   18.591080] saa7134[0]: i2c eeprom 20: 00 40 01 02 03 41 00 01 00 5e 00 06 40 e7 32 00 
 [   18.591087] saa7134[0]: i2c eeprom 30: 01 5f 20 77 ac 5e 00 88 53 71 32 8c c0 01 0f 50 
 [   18.591095] saa7134[0]: i2c eeprom 40: 26 02 00 00 02 00 67 00 00 50 51 2b 02 24 66 2b 
 [   18.591102] saa7134[0]: i2c eeprom 50: 00 24 67 50 70 e7 66 00 01 71 66 cc 03 50 26 0b 
 [   18.591110] saa7134[0]: i2c eeprom 60: 00 24 66 71 57 96 bc 9b 7f 38 57 05 0f 73 58 a0 
 [   18.591117] saa7134[0]: i2c eeprom 70: 57 38 57 7c 58 4e 9f 83 f2 ff 80 30 58 d5 b8 14 
 [   18.591124] saa7134[0]: i2c eeprom 80: 0c 5e db 58 f2 83 e7 ff bf 4e 81 5b 32 a1 58 3c 
 [   18.591132] saa7134[0]: i2c eeprom 90: 58 5b 1a 8c b3 50 31 8c a0 41 82 11 b5 21 c0 a2 
 [   18.591139] saa7134[0]: i2c eeprom a0: 58 8d fa 00 00 51 52 ed 34 00 00 50 62 2b 01 ed 
 [   18.591146] saa7134[0]: i2c eeprom b0: 32 00 00 50 a1 58 5a 50 80 58 5a 5e 18 ff f5 a6 
 [   18.591154] saa7134[0]: i2c eeprom c0: 32 96 bc cc fa 50 16 2b 01 24 34 2b 00 41 80 11 
 [   18.591161] saa7134[0]: i2c eeprom d0: a6 8d fa 00 80 51 32 ed 34 00 00 50 62 2b 01 ed 
 [   18.591168] saa7134[0]: i2c eeprom e0: 32 00 44 50 91 2b 00 50 70 2b 00 71 32 cc 4e 50 
 [   18.591176] saa7134[0]: i2c eeprom f0: 26 cc 39 50 16 2b 01 24 34 2b 44 52 a0 8d fa 00 
 [   18.591718] saa7134[0]: registered device video0 [v4l2] 
 [   18.591747] saa7134[0]: registered device vbi0 
 [   19.050853] saa7134 ALSA driver for DMA sound loaded 
 [   19.050866] IRQ 17/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs 
 [   19.050886] saa7134[0]/alsa: saa7134[0] at 0xd0010000 irq 17 registered as card -2 





Seems like Card is not detected (card=0)



When I do





 dmesg 


I just get a big list of stuff.  I do not get a reference to the ***card no*** or the ***tuner no***.




saa7134 **[COLOR=#ff0000]card[/COLOR]**=70 tuner=67   ----- so how do i know if this is correct for Australia Sydney and my T300 card?



Think i need to add this:


 	Code:
 	sudo gedit /etc/modprobe.d/options 
Add and Save:

 	Code:
 	options saa7134 **[COLOR=#ff0000]card[/COLOR]**=70 tuner=67 
Enable:

 	Code:
 	sudo modprobe saa7134 **[COLOR=#ff0000]card[/COLOR]**=70 tuner=67[COLOR=Red][/COLOR] 

What Ubuntu App do I need to install for Sydney DVT (Digital reception)?

---

### Post by comprodtv on 2010-03-22
Ok, did this

 	Code:
 	sudo gedit /etc/modprobe.d/options 
Add and Save:

 	Code:
 	options saa7134 **[COLOR=#ff0000]card[/COLOR]**=70 tuner=67 
Enable:

 	Code:
 	sudo modprobe saa7134 **[COLOR=#ff0000]card[/COLOR]**=70 tuner=67 

Card Shows-Up.
Code:
grep card= /var/log/dmesg
[   13.358318] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,insmod option]

Installed Kaffeine.
Go To Configure Television, Device TAB.  Name: Philips TDA10046H DVB-T.  Set Source.
Scan for Channels:  Get ERROR:  ¨No suitable device found¨

Is this a bug?  Or what else do I need to do?

---

### Post by comprodtv on 2010-03-22
> **comprodtv said:**
> Ok, did this

     Code:
     sudo gedit /etc/modprobe.d/options 
Add and Save:

     Code:
     options saa7134 **[COLOR=#ff0000]card[/COLOR]**=70 tuner=67 
Enable:

     Code:
     sudo modprobe saa7134 **[COLOR=#ff0000]card[/COLOR]**=70 tuner=67 

Card Shows-Up.
Code:
grep card= /var/log/dmesg
[   13.358318] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,insmod option]

Installed Kaffeine.
Go To Configure Television, Device TAB.  Name: Philips TDA10046H DVB-T.  Set Source.
Scan for Channels:  Get ERROR:  ¨No suitable device found¨

Is this a bug?  Or what else do I need to do?

Please help:

Code:
$ dmesg | grep saa

[   21.585135] saa7130/34: v4l2 driver version 0.2.15 loaded
[   21.585390] saa7134 0000:05:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   21.585396] saa7134[0]: found at 0000:05:07.0, rev: 1, irq: 17, latency: 32, mmio: 0xd0010000
[   21.585402] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,insmod option]
[   21.585414] saa7134[0]: board init: gpio is 843f00
[   21.585476] input: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:09.0/0000:05:07.0/input/input4
[   21.585511] IRQ 17/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   22.069142] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   22.069152] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   22.069160] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[   22.069167] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069175] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   22.069182] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   22.069190] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069198] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069205] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069213] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069220] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069228] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069235] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069247] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069255] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.069262] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   22.300111] tuner 2-0043: chip found @ 0x86 (saa7134[0])
[   22.317464] tuner 2-0061: chip found @ 0xc2 (saa7134[0])
[   22.380086] saa7134[0]: registered device video0 [v4l2]
[   22.380107] saa7134[0]: registered device vbi0
[   22.384875] saa7134 ALSA driver for DMA sound loaded
[   22.384887] IRQ 17/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   22.384908] saa7134[0]/alsa: saa7134[0] at 0xd0010000 irq 17 registered as card -2
[   22.892370] DVB: registering new adapter (saa7134[0])

---

### Post by comprodtv on 2010-03-22
Seems like MythTV likes to be the only DVT Apps (it claims the pci device).
Had to remove this completely.
Software Center - Remove
sudo apt-get remove mythtv
sudo apt-get autoremove mythtv
System >> Administration >> Synaptic Package Manager, click the button "status", select "Not Installed (residual config)" in the left panel, then right-click the MythTV packages and select "Mark for complete removal". Click "Apply". ---- I still have some MythTV packages left here, but the option for "Mark for complete removal" is not available for these......
 
At least now the **[COLOR=red]Kaffeine error[/COLOR]** ( ¨No suitable device found¨) is gone.
Scan for Channels finds some DVT Signals. However, when I click on a channel to watch it, I get messages: [COLOR=red]**Cannot find demultiplexer plugin for given media data**[/COLOR]
 
Running Kaffeine from Terminal
~$ demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
 
 
 
Code: ~$ dmesg 
[ 0.150252] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[ 0.150398] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[ 0.150545] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[ 0.150700] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[ 0.150854] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[ 0.151008] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[ 0.151179] SCSI subsystem initialized
[ 0.151245] libata version 3.00 loaded.
[ 0.151312] usbcore: registered new interface driver usbfs
[ 0.151326] usbcore: registered new interface driver hub
[ 0.151346] usbcore: registered new device driver usb
[ 0.151455] ACPI: WMI: Mapper loaded
[ 0.151457] PCI: Using ACPI for IRQ routing
[ 0.151583] Bluetooth: Core ver 2.15
[ 0.151604] NET: Registered protocol family 31
[ 0.151606] Bluetooth: HCI device and connection manager initialized
[ 0.151609] Bluetooth: HCI socket layer initialized
[ 0.151611] NetLabel: Initializing
[ 0.151612] NetLabel: domain hash size = 128
[ 0.151614] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.151625] NetLabel: unlabeled traffic allowed by default
[ 0.153117] pnp: PnP ACPI init
[ 0.153134] ACPI: bus type pnp registered
[ 0.157623] pnp: PnP ACPI: found 16 devices
[ 0.157625] ACPI: ACPI bus type pnp unregistered
[ 0.157629] PnPBIOS: Disabled by ACPI PNP
[ 0.157639] system 00:01: ioport range 0x4000-0x407f has been reserved
[ 0.157642] system 00:01: ioport range 0x4080-0x40ff has been reserved
[ 0.157645] system 00:01: ioport range 0x4400-0x447f has been reserved
[ 0.157647] system 00:01: ioport range 0x4480-0x44ff has been reserved
[ 0.157650] system 00:01: ioport range 0x4800-0x487f has been reserved
[ 0.157653] system 00:01: ioport range 0x4880-0x48ff has been reserved
[ 0.157658] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[ 0.157661] system 00:02: ioport range 0x800-0x805 has been reserved
[ 0.157663] system 00:02: ioport range 0x290-0x297 has been reserved
[ 0.157671] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[ 0.157676] system 00:0f: iomem range 0xf0000-0xf3fff could not be reserved
[ 0.157679] system 00:0f: iomem range 0xf4000-0xf7fff could not be reserved
[ 0.157682] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[ 0.157684] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[ 0.157687] system 00:0f: iomem range 0x7fff0000-0x7fffffff could not be reserved
[ 0.157690] system 00:0f: iomem range 0xffff0000-0xffffffff has been reserved
[ 0.157693] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[ 0.157696] system 00:0f: iomem range 0x100000-0x7ffeffff could not be reserved
[ 0.157699] system 00:0f: iomem range 0xfec00000-0xfec00fff could not be reserved
[ 0.157702] system 00:0f: iomem range 0xfee00000-0xfeefffff has been reserved
[ 0.157705] system 00:0f: iomem range 0xfefff000-0xfeffffff has been reserved
[ 0.157708] system 00:0f: iomem range 0xfff80000-0xfff80fff has been reserved
[ 0.157711] system 00:0f: iomem range 0xfff90000-0xfffbffff has been reserved
[ 0.157714] system 00:0f: iomem range 0xfffed000-0xfffeffff has been reserved
[ 0.192374] AppArmor: AppArmor Filesystem Enabled
[ 0.192402] pci 0000:00:09.0: PCI bridge, secondary bus 0000:05
[ 0.192405] pci 0000:00:09.0: IO window: 0xa000-0xafff
[ 0.192408] pci 0000:00:09.0: MEM window: 0xd0000000-0xd00fffff
[ 0.192411] pci 0000:00:09.0: PREFETCH window: disabled
[ 0.192414] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:04
[ 0.192416] pci 0000:00:0b.0: IO window: disabled
[ 0.192419] pci 0000:00:0b.0: MEM window: disabled
[ 0.192421] pci 0000:00:0b.0: PREFETCH window: disabled
[ 0.192424] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[ 0.192425] pci 0000:00:0c.0: IO window: disabled
[ 0.192428] pci 0000:00:0c.0: MEM window: disabled
[ 0.192430] pci 0000:00:0c.0: PREFETCH window: disabled
[ 0.192433] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:02
[ 0.192435] pci 0000:00:0d.0: IO window: disabled
[ 0.192438] pci 0000:00:0d.0: MEM window: disabled
[ 0.192440] pci 0000:00:0d.0: PREFETCH window: disabled
[ 0.192446] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:01
[ 0.192448] pci 0000:00:0e.0: IO window: disabled
[ 0.192451] pci 0000:00:0e.0: MEM window: 0xc8000000-0xcfffffff
[ 0.192454] pci 0000:00:0e.0: PREFETCH window: 0x000000c0000000-0x000000c7ffffff
[ 0.192463] pci 0000:00:09.0: setting latency timer to 64
[ 0.192468] pci 0000:00:0b.0: setting latency timer to 64
[ 0.192472] pci 0000:00:0c.0: setting latency timer to 64
[ 0.192476] pci 0000:00:0d.0: setting latency timer to 64
[ 0.192480] pci 0000:00:0e.0: setting latency timer to 64
[ 0.192484] pci_bus 0000:00: resource 0 io: [0x00-0xffff]
[ 0.192487] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[ 0.192490] pci_bus 0000:05: resource 0 io: [0xa000-0xafff]
[ 0.192492] pci_bus 0000:05: resource 1 mem: [0xd0000000-0xd00fffff]
[ 0.192495] pci_bus 0000:05: resource 3 io: [0x00-0xffff]
[ 0.192497] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[ 0.192500] pci_bus 0000:01: resource 1 mem: [0xc8000000-0xcfffffff]
[ 0.192503] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xc7ffffff]
[ 0.192537] NET: Registered protocol family 2
[ 0.192624] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.192935] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.193646] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.194021] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.194023] TCP reno registered
[ 0.194112] NET: Registered protocol family 1
[ 0.194175] Trying to unpack rootfs image as initramfs...
[ 0.196027] Switched to high resolution mode on CPU 0
[ 0.384147] Freeing initrd memory: 7467k freed
[ 0.388696] cpufreq-nforce2: No nForce2 chipset.
[ 0.388725] Scanning for low memory corruption every 60 seconds
[ 0.388821] audit: initializing netlink socket (disabled)
[ 0.388837] type=2000 audit(1269331655.388:1): initialized
[ 0.397064] highmem bounce pool size: 64 pages
[ 0.397069] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 0.398220] VFS: Disk quotas dquot_6.5.2
[ 0.398266] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.398760] fuse init (API version 7.12)
[ 0.398843] msgmni has been set to 1705
[ 0.399012] alg: No test for stdrng (krng)
[ 0.399022] io scheduler noop registered
[ 0.399024] io scheduler anticipatory registered
[ 0.399026] io scheduler deadline registered
[ 0.399062] io scheduler cfq registered (default)
[ 0.412076] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.412082] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[ 0.412089] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.412093] pci 0000:00:0b.0: Linking AER extended capability
[ 0.412128] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.412133] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[ 0.412140] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.412142] pci 0000:00:0c.0: Linking AER extended capability
[ 0.412180] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.412185] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[ 0.412192] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.412195] pci 0000:00:0d.0: Linking AER extended capability
[ 0.412236] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.412241] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[ 0.412248] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.412250] pci 0000:00:0e.0: Linking AER extended capability
[ 0.412265] pci 0000:01:00.0: Boot video device
[ 0.412345] alloc irq_desc for 24 on node -1
[ 0.412347] alloc kstat_irqs on node -1
[ 0.412356] pcieport-driver 0000:00:0b.0: irq 24 for MSI/MSI-X
[ 0.412361] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[ 0.412416] alloc irq_desc for 25 on node -1
[ 0.412418] alloc kstat_irqs on node -1
[ 0.412422] pcieport-driver 0000:00:0c.0: irq 25 for MSI/MSI-X
[ 0.412426] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[ 0.412479] alloc irq_desc for 26 on node -1
[ 0.412481] alloc kstat_irqs on node -1
[ 0.412485] pcieport-driver 0000:00:0d.0: irq 26 for MSI/MSI-X
[ 0.412489] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[ 0.412545] alloc irq_desc for 27 on node -1
[ 0.412546] alloc kstat_irqs on node -1
[ 0.412550] pcieport-driver 0000:00:0e.0: irq 27 for MSI/MSI-X
[ 0.412554] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[ 0.412602] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.412623] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.412728] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[ 0.412731] ACPI: Power Button [PWRF]
[ 0.412779] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[ 0.412781] ACPI: Power Button [PWRB]
[ 0.412831] fan PNP0C0B:00: registered as cooling_device0
[ 0.412835] ACPI: Fan [FAN] (on)
[ 0.413278] processor LNXCPU:00: registered as cooling_device1
[ 0.416982] thermal LNXTHERM:01: registered as thermal_zone0
[ 0.416989] ACPI: Thermal Zone [THRM] (40 C)
[ 0.417027] isapnp: Scanning for PnP cards...
[ 0.769579] isapnp: No Plug & Play device found
[ 0.770478] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 0.770569] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.770807] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.771740] brd: module loaded
[ 0.772143] loop: module loaded
[ 0.772210] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[ 0.772374] sata_nv 0000:00:07.0: version 3.5
[ 0.772723] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[ 0.772728] alloc irq_desc for 23 on node -1
[ 0.772730] alloc kstat_irqs on node -1
[ 0.772738] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[ 0.772784] sata_nv 0000:00:07.0: setting latency timer to 64
[ 0.772859] scsi0 : sata_nv
[ 0.772941] scsi1 : sata_nv
[ 0.773075] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[ 0.773078] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[ 0.773378] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[ 0.773381] alloc irq_desc for 22 on node -1
[ 0.773382] alloc kstat_irqs on node -1
[ 0.773387] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[ 0.773422] sata_nv 0000:00:08.0: setting latency timer to 64
[ 0.773484] scsi2 : sata_nv
[ 0.773546] scsi3 : sata_nv
[ 0.773673] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[ 0.773676] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[ 0.773747] pata_amd 0000:00:06.0: version 0.4.1
[ 0.773778] pata_amd 0000:00:06.0: setting latency timer to 64
[ 0.773829] scsi4 : pata_amd
[ 0.773894] scsi5 : pata_amd
[ 0.774524] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[ 0.774526] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[ 0.775093] Fixed MDIO Bus: probed
[ 0.775123] PPP generic driver version 2.4.2
[ 0.775213] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 0.775455] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[ 0.775459] alloc irq_desc for 21 on node -1
[ 0.775461] alloc kstat_irqs on node -1
[ 0.775468] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[ 0.775478] ehci_hcd 0000:00:02.1: setting latency timer to 64
[ 0.775481] ehci_hcd 0000:00:02.1: EHCI Host Controller
[ 0.775514] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[ 0.775537] ehci_hcd 0000:00:02.1: debug port 1
[ 0.775541] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[ 0.775553] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000
[ 0.784017] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[ 0.784092] usb usb1: configuration #1 chosen from 1 choice
[ 0.784116] hub 1-0:1.0: USB hub found
[ 0.784125] hub 1-0:1.0: 10 ports detected
[ 0.784174] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 0.784417] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[ 0.784420] alloc irq_desc for 20 on node -1
[ 0.784421] alloc kstat_irqs on node -1
[ 0.784427] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[ 0.784435] ohci_hcd 0000:00:02.0: setting latency timer to 64
[ 0.784437] ohci_hcd 0000:00:02.0: OHCI Host Controller
[ 0.784467] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[ 0.784484] ohci_hcd 0000:00:02.0: irq 20, io mem 0xd0104000
[ 0.842061] usb usb2: configuration #1 chosen from 1 choice
[ 0.842082] hub 2-0:1.0: USB hub found
[ 0.842090] hub 2-0:1.0: 10 ports detected
[ 0.842131] uhci_hcd: USB Universal Host Controller Interface driver
[ 0.842214] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 0.845074] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 0.845079] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 0.845132] mice: PS/2 mouse device common for all mice
[ 0.845217] rtc_cmos 00:04: RTC can wake from S4
[ 0.845248] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[ 0.845269] rtc0: alarms up to one year, y3k, 242 bytes nvram
[ 0.845354] device-mapper: uevent: version 1.0.3
[ 0.845443] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[ 0.845514] device-mapper: multipath: version 1.1.0 loaded
[ 0.845517] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.845639] EISA: Probing bus 0 at eisa.0
[ 0.845650] Cannot allocate resource for EISA slot 4
[ 0.845661] EISA: Detected 0 cards.
[ 0.845702] cpuidle: using governor ladder
[ 0.845704] cpuidle: using governor menu
[ 0.846145] TCP cubic registered
[ 0.846281] NET: Registered protocol family 10
[ 0.846653] lo: Disabled Privacy Extensions
[ 0.846916] NET: Registered protocol family 17
[ 0.846933] Bluetooth: L2CAP ver 2.13
[ 0.846934] Bluetooth: L2CAP socket layer initialized
[ 0.846937] Bluetooth: SCO (Voice Link) ver 0.6
[ 0.846938] Bluetooth: SCO socket layer initialized
[ 0.846961] Bluetooth: RFCOMM TTY layer initialized
[ 0.846964] Bluetooth: RFCOMM socket layer initialized
[ 0.846966] Bluetooth: RFCOMM ver 1.11
[ 0.846980] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[ 0.851211] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[ 0.851242] Using IPI No-Shortcut mode
[ 0.851294] PM: Resume from disk failed.
[ 0.851305] registered taskstats version 1
[ 0.851424] Magic number: 2:620:119
[ 0.851518] rtc_cmos 00:04: setting system clock to 2010-03-23 08:07:36 UTC (1269331656)
[ 0.851521] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 0.851523] EDD information not available.
[ 0.873257] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[ 0.944351] ata5.00: ATA-7: SAMSUNG SV1604E, VW100-06, max UDMA/133
[ 0.944354] ata5.00: 312581808 sectors, multi 1: LBA48 
[ 0.944380] ata5.01: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
[ 0.944403] ata5: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc7c50000) ACPI=0x7f01f (15:30:0x1f)
[ 0.944408] ata5: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc7c50000) ACPI=0x1f01f (15:30:0x1f)
[ 0.952292] ata5.00: configured for UDMA/133
[ 0.968197] ata5.01: configured for UDMA/66
[ 1.084069] ata1: SATA link down (SStatus 0 SControl 300)
[ 1.096022] usb 1-4: new high speed USB device using ehci_hcd and address 2
[ 1.228997] usb 1-4: configuration #1 chosen from 1 choice
[ 1.240028] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.248106] ata3.00: ATA-7: WDC WD2500JS-00MHB0, 02.01C03, max UDMA/133
[ 1.248109] ata3.00: 488397168 sectors, multi 1: LBA48 
[ 1.256120] ata3.00: configured for UDMA/133
[ 1.552024] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.566808] ata2.00: ATA-7: WDC WD3200AAKS-00SBA0, 12.01B01, max UDMA/133
[ 1.566811] ata2.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 0/32)
[ 1.580626] ata2.00: configured for UDMA/133
[ 1.580720] scsi 1:0:0:0: Direct-Access ATA WDC WD3200AAKS-0 12.0 PQ: 0 ANSI: 5
[ 1.580812] sd 1:0:0:0: Attached scsi generic sg0 type 0
[ 1.580845] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 1.580882] sd 1:0:0:0: [sda] Write Protect is off
[ 1.580885] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.580905] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.581009] sda:
[ 1.581139] scsi 2:0:0:0: Direct-Access ATA WDC WD2500JS-00M 02.0 PQ: 0 ANSI: 5
[ 1.581217] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 1.581243] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 1.581279] sd 2:0:0:0: [sdb] Write Protect is off
[ 1.581282] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 1.581300] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.581387] sdb: sda1
[ 1.589155] sd 1:0:0:0: [sda] Attached SCSI disk
[ 1.592567] sdb1
[ 1.592697] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 1.892021] ata4: SATA link down (SStatus 0 SControl 300)
[ 1.892089] scsi 4:0:0:0: Direct-Access ATA SAMSUNG SV1604E VW10 PQ: 0 ANSI: 5
[ 1.892171] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1.893884] sd 4:0:0:0: [sdc] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[ 1.893918] sd 4:0:0:0: [sdc] Write Protect is off
[ 1.893921] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[ 1.893939] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.894025] sdc: sdc1 sdc2 <
[ 1.906222] scsi 4:0:1:0: CD-ROM HL-DT-ST DVDRAM GSA-H42N RL00 PQ: 0 ANSI: 5
[ 1.934361] sdc5 >
[ 1.937770] sd 4:0:0:0: [sdc] Attached SCSI disk
[ 1.945659] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[ 1.945662] Uniform CD-ROM driver Revision: 3.20
[ 1.945718] sr 4:0:1:0: Attached scsi CD-ROM sr0
[ 1.945752] sr 4:0:1:0: Attached scsi generic sg3 type 5
[ 2.110813] Freeing unused kernel memory: 540k freed
[ 2.111162] Write protecting the kernel text: 4580k
[ 2.111190] Write protecting the kernel read-only data: 1840k
[ 2.230607] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[ 2.230883] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[ 2.230888] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[ 2.230892] forcedeth 0000:00:0a.0: setting latency timer to 64
[ 2.230926] nv_probe: set workaround bit for reversed mac addr
[ 2.269178] Floppy drive(s): fd0 is 1.44M
[ 2.293780] FDC 0 is a post-1991 82077
[ 2.371107] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[ 2.371113] alloc irq_desc for 18 on node -1
[ 2.371116] alloc kstat_irqs on node -1
[ 2.371124] ohci1394 0000:05:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[ 2.430060] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18] MMIO=[d0011000-d00117ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 2.748728] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 9, addr 00:13:d4:36:69:a3
[ 2.748733] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[ 3.712121] ieee1394: Host added: ID:BUS[0-00:1023] GUID[0011066600003cba]
[ 3.878438] PM: Starting manual resume from disk
[ 3.878443] PM: Resume from partition 8:37
[ 3.878445] PM: Checking hibernation image.
[ 3.878611] PM: Resume from disk failed.
[ 3.913730] EXT4-fs (sdc1): barriers enabled
[ 3.936605] kjournald2 starting: pid 394, dev sdc1:8, commit interval 5 seconds
[ 3.936634] EXT4-fs (sdc1): delayed allocation enabled
[ 3.936637] EXT4-fs: file extents enabled
[ 3.954511] EXT4-fs: mballoc enabled
[ 3.954526] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[ 4.788796] type=1505 audit(1269331660.437:2): operation="profile_load" pid=418 name=/usr/share/gdm/guest-session/Xsession
[ 4.810463] type=1505 audit(1269331660.456:3): operation="profile_load" pid=419 name=/sbin/dhclient3
[ 4.810731] type=1505 audit(1269331660.456:4): operation="profile_load" pid=419 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[ 4.810882] type=1505 audit(1269331660.456:5): operation="profile_load" pid=419 name=/usr/lib/connman/scripts/dhclient-script
[ 4.855130] type=1505 audit(1269331660.500:6): operation="profile_load" pid=420 name=/usr/bin/evince
[ 4.859654] type=1505 audit(1269331660.504:7): operation="profile_load" pid=420 name=/usr/bin/evince-previewer
[ 4.862328] type=1505 audit(1269331660.508:8): operation="profile_load" pid=420 name=/usr/bin/evince-thumbnailer
[ 4.872734] type=1505 audit(1269331660.520:9): operation="profile_load" pid=422 name=/usr/lib/cups/backend/cups-pdf
[ 4.873062] type=1505 audit(1269331660.520:10): operation="profile_load" pid=422 name=/usr/sbin/cupsd
[ 5.871673] Adding 6040400k swap on /dev/sdc5. Priority:-1 extents:1 across:6040400k 
[ 6.245544] EXT4-fs (sdc1): internal journal on sdc1:8
[ 7.734928] udev: starting version 147
[ 8.834929] lp: driver loaded but no devices found
[ 9.162134] parport_pc 00:09: reported by Plug and Play ACPI
[ 9.162184] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[ 9.260153] lp0: using parport0 (interrupt-driven).
[ 9.273474] ppdev: user-space parallel port driver
[ 9.407095] Linux agpgart interface v0.103
[ 9.545370] psmouse serio1: ID: 10 00 64
[ 9.836278] input: PS2++ Logitech MX Mouse as /devices/platform/i8042/serio1/input/input4
[ 10.362076] nvidia: module license 'NVIDIA' taints kernel.
[ 10.362081] Disabling lock debugging due to kernel taint
[ 10.653234] gameport: NS558 PnP Gameport is pnp00:0d/gameport0, io 0x201, speed 59659kHz
[ 10.654242] cfg80211: Calling CRDA to update world regulatory domain
[ 10.661675] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[ 10.661693] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[ 10.668366] nvidia 0000:01:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[ 10.668374] nvidia 0000:01:00.0: setting latency timer to 64
[ 10.668601] NVRM: loading NVIDIA UNIX x86 Kernel Module 185.18.36 Fri Aug 14 17:18:04 PDT 2009
[ 10.713834] Linux video capture interface: v2.00
[ 10.786705] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 11.336027] saa7130/34: v4l2 driver version 0.2.15 loaded
[ 11.336267] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[ 11.336272] alloc irq_desc for 17 on node -1
[ 11.336274] alloc kstat_irqs on node -1
[ 11.336283] saa7134 0000:05:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[ 11.336289] saa7134[0]: found at 0000:05:07.0, rev: 1, irq: 17, latency: 32, mmio: 0xd0010000
[ 11.336295] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,insmod option]
[ 11.336309] saa7134[0]: board init: gpio is 843f00
[ 11.336372] input: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:09.0/0000:05:07.0/input/input5
[ 11.336408] IRQ 17/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 11.488019] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 11.488028] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[ 11.488036] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[ 11.488044] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488051] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[ 11.488058] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[ 11.488066] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488073] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488080] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488088] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488095] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488102] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488110] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488117] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488124] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488132] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 11.488141] i2c-adapter i2c-2: Invalid 7-bit address 0x7a
[ 11.769885] cfg80211: World regulatory domain updated:
[ 11.769889] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 11.769893] (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 11.769896] (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 11.769898] (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 11.769901] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 11.769904] (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 11.918995] usbcore: registered new interface driver snd-usb-audio
[ 11.984602] tuner 2-0043: chip found @ 0x86 (saa7134[0])
[ 12.191000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[ 12.191007] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[ 12.191037] Intel ICH 0000:00:04.0: setting latency timer to 64
[ 12.259665] tda9887 2-0043: creating new instance
[ 12.259669] tda9887 2-0043: tda988[5/6/7] found
[ 12.269356] tuner 2-0061: chip found @ 0xc2 (saa7134[0])
[ 12.464018] tuner-simple 2-0061: creating new instance
[ 12.464023] tuner-simple 2-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[ 12.504083] saa7134[0]: registered device video0 [v4l2]
[ 12.504106] saa7134[0]: registered device vbi0
[ 12.506654] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[ 12.506660] alloc irq_desc for 16 on node -1
[ 12.506663] alloc kstat_irqs on node -1
[ 12.506671] ath9k 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[ 12.931532] intel8x0_measure_ac97_clock: measured 471967 usecs (22712 samples)
[ 12.931535] intel8x0: clocking to 48000
[ 12.951966] ath: EEPROM regdomain: 0x809c
[ 12.951970] ath: EEPROM indicates we should expect a country code
[ 12.951973] ath: doing EEPROM country->regdmn map search
[ 12.951974] ath: country maps to regdmn code: 0x52
[ 12.951977] ath: Country alpha2 being used: CN
[ 12.951978] ath: Regpair used: 0x52
[ 13.059156] saa7134 ALSA driver for DMA sound loaded
[ 13.059168] IRQ 17/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 13.059188] saa7134[0]/alsa: saa7134[0] at 0xd0010000 irq 17 registered as card -2
[ 13.286679] dvb_init() allocating 1 frontend
[ 13.493198] phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 13.493808] Registered led device: ath9k-phy0::radio
[ 13.493822] Registered led device: ath9k-phy0::assoc
[ 13.493835] Registered led device: ath9k-phy0::tx
[ 13.493849] Registered led device: ath9k-phy0::rx
[ 13.493867] phy0: Atheros AR5416 MAC/BB Rev:2 AR2133 RF Rev:81: mem=0xf8840000, irq=16
[ 13.508313] udev: renamed network interface wlan0 to wlan1
[ 13.708047] DVB: registering new adapter (saa7134[0])
[ 13.708053] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[ 13.756015] tda1004x: setting up plls for 48MHz sampling clock
[ 14.264017] tda1004x: found firmware revision 23 -- ok
[ 14.618390] cfg80211: Calling CRDA for country: CN
[ 14.621617] cfg80211: Regulatory domain changed to country: CN
[ 14.621622] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 14.621625] (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 14.621628] (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[ 15.475139] __ratelimit: 3 callbacks suppressed
[ 15.475143] type=1505 audit(1269292071.120:12): operation="profile_replace" pid=1056 name=/usr/share/gdm/guest-session/Xsession
[ 15.478377] type=1505 audit(1269292071.124:13): operation="profile_replace" pid=1057 name=/sbin/dhclient3
[ 15.478648] type=1505 audit(1269292071.124:14): operation="profile_replace" pid=1057 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[ 15.478799] type=1505 audit(1269292071.124:15): operation="profile_replace" pid=1057 name=/usr/lib/connman/scripts/dhclient-script
[ 15.483300] type=1505 audit(1269292071.128:16): operation="profile_replace" pid=1058 name=/usr/bin/evince
[ 15.488912] type=1505 audit(1269292071.136:17): operation="profile_replace" pid=1058 name=/usr/bin/evince-previewer
[ 15.491574] type=1505 audit(1269292071.136:18): operation="profile_replace" pid=1058 name=/usr/bin/evince-thumbnailer
[ 15.497362] type=1505 audit(1269292071.144:19): operation="profile_replace" pid=1060 name=/usr/lib/cups/backend/cups-pdf
[ 15.497692] type=1505 audit(1269292071.144:20): operation="profile_replace" pid=1060 name=/usr/sbin/cupsd
[ 15.503888] type=1505 audit(1269292071.148:21): operation="profile_replace" pid=1062 name=/usr/sbin/tcpdump
[ 26.488422] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 33.406105] eth0: no link during initialization.
[ 33.406519] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 36.711330] eth0: no link during initialization.
[ 36.711730] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 38.667882] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 40.594705] wlan1: authenticate with AP 00:24:21:ce:8b:28
[ 40.597792] wlan1: authenticated
[ 40.597798] wlan1: associate with AP 00:24:21:ce:8b:28
[ 40.605742] wlan1: RX AssocResp from 00:24:21:ce:8b:28 (capab=0x411 status=0 aid=2)
[ 40.605746] wlan1: associated
[ 40.610293] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 40.668853] cfg80211: Calling CRDA for country: AU
[ 40.670762] cfg80211: Received country IE:
[ 40.670766] cfg80211: Regulatory domain: AU
[ 40.670768] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 40.670771] (2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[ 40.670773] cfg80211: CRDA thinks this should applied:
[ 40.670775] cfg80211: Regulatory domain: AU
[ 40.670776] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 40.670779] (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 40.670781] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
[ 40.670784] (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
[ 40.670787] (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 40.670788] cfg80211: We intersect both of these and get:
[ 40.670790] cfg80211: Regulatory domain: 98
[ 40.670792] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 40.670794] (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 40.670799] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[ 40.670804] cfg80211: Current regulatory domain updated by AP to: AU
[ 40.670805] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 40.670808] (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 41.116253] padlock: VIA PadLock not detected.
[ 51.484020] wlan1: no IPv6 routers present
[ 388.804025] tda1004x: setting up plls for 48MHz sampling clock
[ 389.312037] tda1004x: found firmware revision 23 -- ok
[ 690.688015] tda1004x: setting up plls for 48MHz sampling clock
[ 691.212031] tda1004x: found firmware revision 23 -- ok
[ 707.168021] tda1004x: setting up plls for 48MHz sampling clock
[ 707.692022] tda1004x: found firmware revision 23 -- ok
[ 734.316130] wlan1: deauthenticated (Reason: 3)
[ 735.316022] wlan1: direct probe to AP 00:24:21:ce:8b:28 try 1
[ 735.317531] wlan1 direct probe responded
[ 735.317533] wlan1: authenticate with AP 00:24:21:ce:8b:28
[ 735.319085] wlan1: authenticated
[ 735.319087] wlan1: associate with AP 00:24:21:ce:8b:28
[ 735.326988] wlan1: RX ReassocResp from 00:24:21:ce:8b:28 (capab=0x411 status=0 aid=2)
[ 735.326991] wlan1: associated
[ 1161.392018] tda1004x: setting up plls for 48MHz sampling clock
[ 1161.916019] tda1004x: found firmware revision 23 -- ok
[ 1466.942679] wlan1: deauthenticated (Reason: 3)
[ 1468.948025] wlan1: direct probe to AP 00:24:21:ce:8b:28 try 1
[ 1468.951141] wlan1 direct probe responded
[ 1468.951144] wlan1: authenticate with AP 00:24:21:ce:8b:28
[ 1468.952784] wlan1: authenticated
[ 1468.952787] wlan1: associate with AP 00:24:21:ce:8b:28
[ 1468.960724] wlan1: RX ReassocResp from 00:24:21:ce:8b:28 (capab=0x411 status=0 aid=2)
[ 1468.960727] wlan1: associated
[ 1499.992018] tda1004x: setting up plls for 48MHz sampling clock
[ 1500.516017] tda1004x: found firmware revision 23 -- ok
 
 
Am now using Synaptic **to install libxine1-ffmpeg and libavcodec-unstripped-52**
(and installed - libxine1-all-plugins and linux-firmware-nonfree)
Also added User Privilege Use Video Devices to my Ubuntu User 
 
Works, great!

---

