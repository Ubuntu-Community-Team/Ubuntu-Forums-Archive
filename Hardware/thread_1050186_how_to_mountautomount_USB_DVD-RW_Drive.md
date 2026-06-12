---
title: "how to mount/automount USB DVD-RW Drive"
date: 2009-01-25
forum: Hardware
---

### Post by piagent on 2009-01-25
I have a Maddog Multimedia  - MegaStor - Triple Format DVD-RW Drive - 480 MBpps USB 2.0 - MD-16X3DVD9-8XE on hardy release 8.04, kernel 2.6..24-23 generic - Gnome 2.22.3

I looked over the following documents for help and I'm stuck.
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)     MountUSB
[https://help.ubuntu.com/community/UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto) UsbDriveDoSomethingHowto

How do I get this DVD recognized or hand installed? Also my USBview (and sudo usbview) does not work, it states that it can not open /proc/bus/usb/devices wants USB in the kernel, modules loaded and have the usbdevfs mounted.  Not sure how useful this would have been if it did run. It looks like part of the system can see it. Bus 001 Device 008: ID 13fd:0540 ?  What needs to be in the /var/lib/misc/usb.ids? What other places need update?

lsusb
Bus 001 Device 008: ID 13fd:0540  
Bus 001 Device 005: ID 0781:0002 SanDisk Corp. SDDR-31 ImageMate II CompactFlash Reader
Bus 001 Device 003: ID 050f:0003 KC Technology, Inc. KC82C160S Hub
Bus 001 Device 002: ID 04b8:0104 Seiko Epson Corp. Perfection 1200
Bus 001 Device 001: ID 0000:0000  

daemon log

Jan 25 09:09:42 main NetworkManager: <debug> [1232892582.707957] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fd_540_0010100500000000'). 
Jan 25 09:09:42 main NetworkManager: <debug> [1232892582.940573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fd_540_0010100500000000_if0'). 

debug log
Jan 25 09:09:42 main NetworkManager: <debug> [1232892582.707957] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fd_540_0010100500000000'). 
Jan 25 09:09:42 main kernel: [ 1035.074855] usb-storage: device found at 6
Jan 25 09:09:42 main kernel: [ 1035.074870] usb-storage: waiting for device to settle before scanning
kern log
Jan 25 09:09:42 main kernel: [ 1034.890414] usb 1-2.1: new full speed USB device using ohci_hcd and address 6
Jan 25 09:09:42 main kernel: [ 1035.004650] usb 1-2.1: configuration #1 chosen from 1 choice
Jan 25 09:09:42 main kernel: [ 1035.072904] scsi5 : SCSI emulation for USB Mass Storage devices
Jan 25 09:09:42 main kernel: [ 1035.074855] usb-storage: device found at 6
Jan 25 09:09:42 main kernel: [ 1035.074870] usb-storage: waiting for device to settle before scanning
Jan 25 09:09:47 main kernel: [ 1040.074447] usb-storage: device scan complete
Jan 25 09:09:53 main kernel: [ 1045.646254] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:03 main kernel: [ 1055.821167] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:19 main kernel: [ 1072.004912] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:19 main kernel: [ 1072.192854] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:30 main kernel: [ 1082.367802] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:30 main kernel: [ 1082.473797] scsi 5:0:0:0: Device offlined - not ready after error recovery


messages
Jan 25 09:09:42 main kernel: [ 1034.890414] usb 1-2.1: new full speed USB device using ohci_hcd and address 6
Jan 25 09:09:42 main kernel: [ 1035.004650] usb 1-2.1: configuration #1 chosen from 1 choice
Jan 25 09:09:42 main kernel: [ 1035.072904] scsi5 : SCSI emulation for USB Mass Storage devices
Jan 25 09:09:53 main kernel: [ 1045.646254] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:03 main kernel: [ 1055.821167] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:19 main kernel: [ 1072.004912] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:19 main kernel: [ 1072.192854] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:30 main kernel: [ 1082.367802] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:30 main kernel: [ 1082.473797] scsi 5:0:0:0: Device offlined - not ready after error recovery
Jan 25 09:18:49 main kernel: [ 1582.158605] usb 1-2.1: USB disconnect, address 6

syslog
Jan 25 09:09:42 main kernel: [ 1034.890414] usb 1-2.1: new full speed USB device using ohci_hcd and address 6
Jan 25 09:09:42 main kernel: [ 1035.004650] usb 1-2.1: configuration #1 chosen from 1 choice
Jan 25 09:09:42 main NetworkManager: <debug> [1232892582.707957] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fd_540_0010100500000000'). 
Jan 25 09:09:42 main kernel: [ 1035.072904] scsi5 : SCSI emulation for USB Mass Storage devices
Jan 25 09:09:42 main kernel: [ 1035.074855] usb-storage: device found at 6
Jan 25 09:09:42 main kernel: [ 1035.074870] usb-storage: waiting for device to settle before scanning
Jan 25 09:09:42 main NetworkManager: <debug> [1232892582.940573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fd_540_0010100500000000_if0'). 
Jan 25 09:09:47 main kernel: [ 1040.074447] usb-storage: device scan complete
Jan 25 09:09:53 main kernel: [ 1045.646254] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:03 main kernel: [ 1055.821167] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:19 main kernel: [ 1072.004912] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:19 main kernel: [ 1072.192854] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:30 main kernel: [ 1082.367802] usb 1-2.1: reset full speed USB device using ohci_hcd and address 6
Jan 25 09:10:30 main kernel: [ 1082.473797] scsi 5:0:0:0: Device offlined - not ready after error recovery

lsusb
Bus 001 Device 007: ID 13fd:0540  
Bus 001 Device 005: ID 0781:0002 SanDisk Corp. SDDR-31 ImageMate II CompactFlash Reader
Bus 001 Device 003: ID 050f:0003 KC Technology, Inc. KC82C160S Hub
Bus 001 Device 002: ID 04b8:0104 Seiko Epson Corp. Perfection 1200
Bus 001 Device 001: ID 0000:0000  

udevinfo -a -p $(udevinfo -q path -n /dev/sda1)
Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sda/sda1':
    KERNEL=="sda1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{dev}=="8:1"
    ATTR{start}=="63"
    ATTR{size}=="30491307"
    ATTR{stat}=="   57460  1141388      171      171"

  looking at parent device '/block/sda':
    KERNELS=="sda"
    SUBSYSTEMS=="block"
    DRIVERS==""
    ATTRS{dev}=="8:0"
    ATTRS{range}=="16"
    ATTRS{removable}=="0"
    ATTRS{size}=="40088160"
    ATTRS{stat}=="    8645    49219  1143108    32832       51      120      171      396        0    30924    33176"
    ATTRS{capability}=="12"

  looking at parent device '/devices/pci0000:00/0000:00:07.1/host0/target0:0:0/0:0:0:0':
    KERNELS=="0:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    ATTRS{model}=="IBM-DPTA-372050 "
    ATTRS{rev}=="P76O"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x2208"
    ATTRS{iodone_cnt}=="0x2208"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"

  looking at parent device '/devices/pci0000:00/0000:00:07.1/host0/target0:0:0':
    KERNELS=="target0:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:07.1/host0':
    KERNELS=="host0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:07.1':
    KERNELS=="0000:00:07.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="pata_amd"
    ATTRS{vendor}=="0x1022"
    ATTRS{device}=="0x7409"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x01018a"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00001022d00007409sv00000000sd00000000bc01sc01i8a"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

 sudo lshw -C disk
[sudo] password for user: 
  *-disk:0                
       description: ATA Disk
       product: IBM-DPTA-372050
       vendor: IBM
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: P76O
       serial: JMYJMT94098
       size: 19GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003d1cd
  *-disk:1
       description: ATA Disk
       product: Maxtor 53073U6
       vendor: Maxtor
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: DA62
       serial: K605VPJC
       size: 28GiB (30GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000379f2
  *-cdrom
       description: SCSI CD-ROM
       product: CD-ROM 50X
       vendor: E-IDE
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 33
       capabilities: removable audio
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: ImageMate II
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 1.30
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdc

---

### Post by piagent on 2009-01-26
Still looking for direction on how to give my system the data so it can automount this usb dvd-rw drive, and learn something along the way. What next? How/where does the usb get matched up to a driver and a device?

I've modified /var/lib/misc/usb.ids so Lsusb will read true with the following:

13fd  Maddog Multimedia
	0540  Triple Format DVD-RW Drive 480 MBpps USB 2.0
13fe  Kingston Technology Company Inc.
	1a00  512MB/1GB Flash Drive
	1a23  512MB Flash Drive
	1d00  DataTraveler 2.0 1GB Flash Drive

lsusb
Bus 001 Device 006: ID 13fd:0540 Maddog Multimedia Triple Format DVD-RW Drive 480 MBpps USB 2.0
Bus 001 Device 004: ID 0781:0002 SanDisk Corp. SDDR-31 ImageMate II CompactFlash Reader
Bus 001 Device 003: ID 050f:0003 KC Technology, Inc. KC82C160S Hub
Bus 001 Device 002: ID 04b8:0104 Seiko Epson Corp. Perfection 1200
Bus 001 Device 001: ID 0000:0000  

scsibus1:
wodim: Warning: controller returns wrong size for CD capabilities page.
	1,0,0	100) 'E-IDE   ' 'CD-ROM 50X      ' '33  ' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
 lsmod
Module                  Size  Used by
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
vboxdrv                61360  0 
ppdev                  10372  0 
ipv6                  267908  16 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
dock                   11280  0 
sbs                    15112  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_emu10k1           146880  4 snd_emu10k1_synth
snd_ac97_codec        101028  1 snd_emu10k1
ac97_bus                3072  1 snd_ac97_codec
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10500  2 snd_emux_synth,snd_emu10k1
usb_storage            73792  0 
libusual               19236  1 usb_storage
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  4 
snd_seq_dummy           4868  0 
psmouse                40336  0 
serio_raw               7940  0 
pcspkr                  4224  0 
snd_bt87x              16868  1 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_oss            35584  0 
snd_pcm                78596  4 snd_emu10k1,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_seq_midi            9376  0 
snd_rawmidi            25760  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_page_alloc         11400  3 snd_emu10k1,snd_bt87x,snd_pcm
bt878                  11832  0 
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
tvaudio                24732  0 
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
msp3400                32160  0 
snd                    56996  23 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hwdep,snd_seq_dummy,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bttv                  175860  1 bt878
button                  9232  0 
ir_common              36100  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7300  1 bttv
soundcore               8800  1 snd
videobuf_dma_sg        14980  1 bttv
videobuf_core          18820  2 bttv,videobuf_dma_sg
btcx_risc               5896  1 bttv
tveeprom               16656  1 bttv
emu10k1_gp              4608  0 
videodev               29440  1 bttv
v4l2_common            18304  5 tuner,tvaudio,msp3400,bttv,videodev
v4l1_compat            15492  2 bttv,videodev
gameport               16008  2 emu10k1_gp
i2c_amd756              7428  0 
shpchp                 34452  0 
amd_k7_agp              9612  1 
pci_hotplug            30880  1 shpchp
agpgart                34760  1 amd_k7_agp
i2c_core               24832  12 tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,tvaudio,msp3400,bttv,i2c_algo_bit,tveeprom,i2c_amd756
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
floppy                 59588  0 
ohci_hcd               26640  0 
3c59x                  46376  0 
mii                     6400  1 3c59x
initio                 19780  0 
usbcore               146412  4 usb_storage,libusual,ohci_hcd
pata_amd               14212  2 
libata                159600  3 ata_generic,pata_acpi,pata_amd
scsi_mod              151436  6 usb_storage,sg,sr_mod,sd_mod,initio,libata
thermal                16796  0 
processor              36488  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

lshal
...
udi = '/org/freedesktop/Hal/devices/usb_device_13fd_540_0010100500000000_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'usb-storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_13fd_540_0010100500000000'  (string)
  info.product = 'USB Mass Storage Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_13fd_540_0010100500000000_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.4/usb1/1-2/1-2.1/1-2.1:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = false  (bool)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 8  (0x8)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 80  (0x50)  (int)
  usb.interface.subclass = 6  (0x6)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 6  (0x6)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.4/usb1/1-2/1-2.1/1-2.1:1.0'  (string)
  usb.max_power = 2  (0x2)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Mass Storage Interface'  (string)
  usb.product_id = 1344  (0x540)  (int)
  usb.serial = '0010100500000000'  (string)
  usb.speed = 12.0 (12) (double)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.vendor = 'Initio'  (string)
  usb.vendor_id = 5117  (0x13fd)  (int)
  usb.version = 2.0 (2) (double)
  usb.version_bcd = 512  (0x200)  (int)
......

---

### Post by piagent on 2009-01-26
BTW, this device maybe a repackaged NEC brand DVD burner (ND-2500A)

---

### Post by piagent on 2009-01-26
I loaded the Device Manager - GNOME device manager based on HAL
It seems to show my USB port is under powered and under speed for this device.  I must have missed this as an error.

---

