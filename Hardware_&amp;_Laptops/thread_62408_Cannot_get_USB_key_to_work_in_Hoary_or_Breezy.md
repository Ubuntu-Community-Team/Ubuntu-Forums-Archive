---
title: "Cannot get USB key to work in Hoary or Breezy"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by fadrian on 2005-09-04
I am having problems getting my Ubuntu system to hotplug USB keydrives.  This
functionality worked fine in Warty but broke for me when I upgraded to Hoary.  I have upgraded to
the Breezy RC to see if that might fix it, but still no go.  Because this
functionality worked for me in earlier versions and others seem to have no problems
with it, I assume there's something wrong in my system configuration.  So,
here are the particulars:

Distro: Ubuntu, Breezy Badger
Kernel version: 2.6.12-8

dmesg output:
[4294667.296000] Linux version 2.6.12-8-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Debian 3.4.4-6ubuntu6)) #1 Tue Aug 30 22:41:30 BST 2005
[4341820.002000] usb 2-2: new full speed USB device using uhci_hcd and address 2[4341820.731000] Initializing USB Mass Storage driver...
[4341820.783000] scsi0 : SCSI emulation for USB Mass Storage devices
[4341820.838000] usb-storage: device found at 2
[4341820.838000] usb-storage: waiting for device to settle before scanning
[4341820.839000] usbcore: registered new driver usb-storage
[4341820.839000] USB Mass Storage support registered.
[4341825.842000]   Vendor: SanDisk   Model: Cruzer Titanium   Rev: 0.4
[4341825.842000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4341825.940000] usb-storage: device scan complete

Note that the hotplug system seems to identify the device and load the scsi
emulation layer, but no /dev node gets created for the newly plugged device.

hotplug blacklist:
#
# Listing a module here prevents the hotplug scripts from loading it.
# Usually that'd be so that some other driver will bind it instead,
# no matter which driver happens to get probed first.  Sometimes user
# mode tools can also control driver binding.
#
# Syntax:  driver name alone (without any spaces) on a line. Other
# lines are ignored.
#

# uhci ... usb-uhci handles the same pci class
usb-uhci
# usbcore ... module is loaded implicitly, ignore it otherwise
#usbcore

#evbug is a debug tool and should be loaded explicitly
evbug

# these drivers are very simple, the HID drivers are usually preferred
usbmouse
usbkbd

# watchdog drivers should be loaded only if a watchdog daemon is installed
acquirewdt
advantechwdt
alim1535_wdt
alim7101_wdt
cpu5wdt
eurotechwdt
i810_tco
i8xx_tco
i810-tco
ib700wdt
indydog
machzwd
mixcomwd
pcwd
pcwd_pci
pcwd_usb
sa1100_wdt
sbc60xxwdt
sc1200wdt
sc520_wdt
scx200_wdt
shwdt
softdog
w83627hf_wdt
w83877f_wdt
wafer5823wdt
wdt285
wdt977
wdt
wdt_pci

# causes no end of confusion by creating unexpected network interfaces
eth1394

# eepro100 is obsoleted by e100 (Ubuntu bug #2156)
eepro100

#added by faa
hw_random

lsmod output:
Module                  Size  Used by
usb_storage            64704  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
sony_acpi               5516  0
pcc_acpi               11392  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  8
ohci1394               30644  0
i2c_i801                8204  0
i2c_core               19728  2 i2c_acpi_ec,i2c_i801
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  2 intel_agp
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
dm_mod                 50364  1
evdev                   9088  0
snd_intel8x0           30016  0
snd_ac97_codec         71804  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
sbp2                   21256  0
ieee1394               90936  2 ohci1394,sbp2
mousedev               10912  1
psmouse                25988  0
sr_mod                 15652  0
scsi_mod              124872  3 usb_storage,sbp2,sr_mod
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
e100                   32768  0
mii                     5248  1 e100
uhci_hcd               28048  0
usbcore               104188  3 usb_storage,uhci_hcd
piix                    9476  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,piix
unix                   24624  738
fbcon                  34176  0
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0
cfbcopyarea             4480  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
softcursor              2432  1 vesafb
capability              5000  0
commoncap               6784  1 capability

lsusb -vvv output:
Bus 002 Device 002: ID 0781:5200 SanDisk Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0781 SanDisk Corp.
  idProduct          0x5200
  bcdDevice            0.20
  iManufacturer           1 SanDisk Corporation
  iProduct                2 Cruzer Titanium
  iSerial                 3 SNDK5F3ED52015C05803
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
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
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-8-386 uhci_hcd
  iProduct                2 Intel Corporation 82801BA/BAM USB (Hub #2)
  iSerial                 1 0000:00:1f.4
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
  DeviceRemovable    0xd0
  PortPwrCtrlMask    0x80
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-8-386 uhci_hcd
  iProduct                2 Intel Corporation 82801BA/BAM USB (Hub #1)
  iSerial                 1 0000:00:1f.2
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
  DeviceRemovable    0x48
  PortPwrCtrlMask    0x81
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power

At this point, I am stumped.  Of course, any advice would be appreciated,
thanks in advance and all that.

---

