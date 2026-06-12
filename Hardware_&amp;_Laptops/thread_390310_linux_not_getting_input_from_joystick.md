---
title: "linux not getting input from joystick"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by CoRnJuLiOx on 2007-03-21
I'm on Ubuntu 6.06 right now, and recently I have discovered the joys of PSX emulation. I went out and picked up one of those cheap PSX->USB controller adapters (its got actual circuitry inside it, it doesn't just change the shape of the plug), thinking I could get it to work, but alas, it doesn't! I can't change the configuration in either ePSXe or PCSX, and the pad doesn't seem to work in game. Running ePSXe in a terminal shows me that the ammoQ plugin i'm using can open the device, it just doesn't get any usable input from it (and I can't figure out why). Heres a list of the things i've tried:

- tried both ePSXe(1.60) and PCSX (the kethipcsx package, downloaded from the ubuntu forums)
- tried different plugins with both emulators, ammoQ's plugin version 0.8 and 0.7, and Omnijoy with PCSX, nothing works, i can't use the pad in games and i can't change the configurations at all.
- jstest doesn't work in this release, according to one of the bug reports that was showed to me.
- tried a PS2 and PS1 controller, came to teh conclusion that the PS2 controller won't work (see below).
- cat /dev/input/js0 with a ps2 controller plugged in returns a 'device not found' error, while plugging a ps1 controller in gives me these random characters that don't change when i push the buttons.
- i've checked the modules to the best of my ability, everything i seem to need is loaded. usbhid, joydev, i don't know if i need anything else.

Heres the output from various console commands that i ran while trying to get this thing to work.

(dmesg, last few lines pertaining to the new USB device)

[49449.177159] usb 2-1: new low speed USB device using uhci_hcd and address 2
[49449.358077] usb 2-1: string descriptor 0 read error: -32
[49449.376099] usb 2-1: string descriptor 0 read error: -32
[49449.393098] usb 2-1: string descriptor 0 read error: -32
[49449.393266] usb 2-1: configuration #1 chosen from 2 choices
[49449.445036] usb 2-1: string descriptor 0 read error: -32
[49449.454128] input: HID 0925:8866 as /class/input/input3
[49449.454167] input: USB HID v1.00 Joystick [HID 0925:8866] on usb-0000:00:10.1-1



(lsmod)

Module                  Size  Used by
xpad                    5888  0
joydev                 10048  2
ext2                   68488  1
nls_utf8                2176  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
apm                    21228  1
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
sg                     37920  0
sd_mod                 19984  1
nls_iso8859_1           4224  1
vfat                   13440  2
fat                    53020  1 vfat
usb_storage            74304  1
scsi_mod              139496  3 sg,sd_mod,usb_storage
nls_cp437               5888  3
ntfs                  103536  1
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
floppy                 62148  0
pcspkr                  2180  0
psmouse                36100  0
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
serio_raw               7300  0
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
analog                 12320  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
rtc                    13492  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           117284  2 snd_emu10k1_synth
i2c_viapro              8980  0
snd_rawmidi            25504  4 snd_seq_virmidi,snd_mpu401_uart,snd_seq_midi,snd_emu10k1
snd_ac97_codec         93216  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
via_ircc               26900  0
snd_pcm                89864  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
irda                  187068  1 via_ircc
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
crc_ccitt               2304  1 irda
snd                    55268  17 snd_emux_synth,snd_seq_virmidi,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
nvidia               3921884  12
i2c_core               21904  1 i2c_viapro
soundcore              10208  1 snd
8139too                26880  0
mii                     5888  1 8139too
emu10k1_gp              3840  0
gameport               15496  3 analog,emu10k1_gp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
via_agp                 9856  1
agpgart                34888  2 nvidia,via_agp
tsdev                   8000  0
evdev                   9856  1
usbhid                 39904  0
ext3                  135944  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  6 xpad,usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  7
via82cxxx               9988  0 [permanent]
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
jrtuvera@jrtuvera-desktop:~$ lsmod
Module                  Size  Used by
xpad                    5888  0
joydev                 10048  2
ext2                   68488  1
nls_utf8                2176  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
apm                    21228  1
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
sg                     37920  0
sd_mod                 19984  1
nls_iso8859_1           4224  1
vfat                   13440  2
fat                    53020  1 vfat
usb_storage            74304  1
scsi_mod              139496  3 sg,sd_mod,usb_storage
nls_cp437               5888  3
ntfs                  103536  1
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
floppy                 62148  0
pcspkr                  2180  0
psmouse                36100  0
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
serio_raw               7300  0
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
analog                 12320  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
rtc                    13492  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           117284  2 snd_emu10k1_synth
i2c_viapro              8980  0
snd_rawmidi            25504  4 snd_seq_virmidi,snd_mpu401_uart,snd_seq_midi,snd_emu10k1
snd_ac97_codec         93216  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
via_ircc               26900  0
snd_pcm                89864  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
irda                  187068  1 via_ircc
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
crc_ccitt               2304  1 irda
snd                    55268  17 snd_emux_synth,snd_seq_virmidi,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
nvidia               3921884  12
i2c_core               21904  1 i2c_viapro
soundcore              10208  1 snd
8139too                26880  0
mii                     5888  1 8139too
emu10k1_gp              3840  0
gameport               15496  3 analog,emu10k1_gp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
via_agp                 9856  1
agpgart                34888  2 nvidia,via_agp
tsdev                   8000  0
evdev                   9856  1
usbhid                 39904  0
ext3                  135944  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  6 xpad,usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  7
via82cxxx               9988  0 [permanent]
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
[/QUOTE]


(sudo lsusb -v)

Bus 003 Device 004: ID 05ac:1301 Apple Computer, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x1301
  bcdDevice            1.00
  iManufacturer           1 Apple
  iProduct                2 iPod
  iSerial                 3 000A270010D169F4
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          5 High Power, High Speed
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              8 Mass Storage Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     2
    iConfiguration          4 Low Power, High Speed
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              8 Mass Storage Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      2
Device Status:     0x0000
  (Bus Powered)

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-28-386 ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:10.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0xc1
 Hub Port Status:
   Port 1: 0000.0000
   Port 2: 0000.0100 power
   Port 3: 0000.0000
   Port 4: 0000.0503 highspeed power enable connect
Device Status:     0x0001
  Self Powered

Bus 002 Device 002: ID 0925:8866 Lakeview Research WiseGroup Ltd, MP-8866 Dual J oypad
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0925 Lakeview Research
  idProduct          0x8866 WiseGroup Ltd, MP-8866 Dual Joypad
  bcdDevice            2.88
  iManufacturer           1
  iProduct                9
  iSerial                 4
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              400mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     195
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
        wMaxPacketSize     0x0007  1x 7 bytes
        bInterval              10
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              400mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     195
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
        wMaxPacketSize     0x0007  1x 7 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-28-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0xe0
  PortPwrCtrlMask    0x01
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc001 N48/M-BB48 [FirstMouse Plus]
  bcdDevice            4.00
  iManufacturer           1 Logitech
  iProduct                2 N48
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
    MaxPower               26mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      56
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-28-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0xd8
  PortPwrCtrlMask    0x02
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled



Can anyone help me? I'm almost out of ideas here, and I really want this thing to work because playing with the keyboard just isn't the same :-(. 
EDIT: HOLY CRAP. Text formatting issues. How do i fix that?

EDIT 2: Ok, I actually got it working. It took me nearly a week and a half and a kernel re-compile, but its working now (somewhat). It turns out theres a bug that is fixed by editing the hid_core.c fileand adding an entry (or something) for this particular device. Some guys have released a patch that nails the issue. Check this out --> [http://marc.info/?l=linux-usb-devel&m=114038593204406&w=2](http://marc.info/?l=linux-usb-devel&m=114038593204406&w=2)

---

### Post by halberd25 on 2007-06-22
I'm also on 6.06 and having the same problem.  I downloaded the patch, but I'm a bit of an amateur at Linux, would you mind telling me what to do with the patch?

I tried applying the patch, and this is what happened

ben@ben-laptop:~/Desktop$ patch -p1 <wisegroup.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux-2.6.14-ck8/drivers/usb/input/hid-core.c      2006-01-06 20:40:19.000000000 -0500
|+++ linux-2.6.14-ck5/drivers/usb/input/hid-core.c      2006-02-19 15:07:03.000000000 -0500
--------------------------
File to patch: 

any ideas?

edit:edit: Huh, I guess even though I got that error message, it must have worked.  My PS2 controller now works on zsnes, gens, and hugo.

---

