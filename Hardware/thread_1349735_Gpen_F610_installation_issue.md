---
title: "Gpen F610 installation issue"
date: 2009-12-08
forum: Hardware
---

### Post by msknight on 2009-12-08
Hi Folks,

Kubuntu 64 bit 9.10.

Plugged the tablet in and the mouse responded but nothing to the buttons. Gimp had a Wacom tablet listed but wouldn't listen to anything on it.

Followed a couple of tutorials, [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) and [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)

...and now I've got nothing in Gimp and even the cursor doesn't want to listen.

However while...
 ./wizardpen-calibrate /dev/input/event6
...gives a permissions error ...
 sudo ./wizardpen-calibrate /dev/input/event6
...allows me to calibrate.

So... first off, I may be looking at a permissions issue.
/dev is rwxr-xr-x root root
/dev/input is rwxr-xr-x root root
/dev/input/event6 is rwxr----- root root
... so is this a permissions issue, or is some administration process not configured properly?

To assist troubleshooting on that score...

I tried wizardpen 0.6.0.2 and had to force it to install as it is 32 bit. Then I tried wizardpen 0.7.0-alpha2 - again forced install.

```
$ grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Cypress Sem PS2/USB Browser Combo Mouse"
N: Name="Microsoft SideWinder Game Voice"
N: Name="WALTOP International Corp. Slim Tablet"
N: Name="HDA Digital PCBeep"
```

I put the calibration figures in to this file...
```
cat /etc/hal/fdi/policy/99-x11-wizardpen.fdi
<?xml version="1.0" encoding="ISO-8859-1" ?>
 <deviceinfo version="0.2">
 <device>
 <!-- This MUST match with the name of your tablet -->
 <match key="info.product" contains="WALTOP International Corp. Slim Tablet">
 <merge key="input.x11_driver" type="string">wizardpen</merge>
 <merge key="input.x11_options.Device" type="string">/dev/input/event6</merge>
 <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
 <merge key="input.x11_options.TopX" type="string">373</merge>
 <merge key="input.x11_options.TopY" type="string">347</merge>
 <merge key="input.x11_options.BottomX" type="string">20000</merge>
 <merge key="input.x11_options.BottomY" type="string">12500</merge>
 <merge key="input.x11_options.MaxX" type="string">20000</merge>
 <merge key="input.x11_options.MaxY" type="string">12500</merge>
 </match>
 </device>
</deviceinfo>
```

However a different name shows up in...
```
$ cat /sys/bus/usb/devices/*/product
SideWinder Game Voice
Slim Tablet
PS2/USB Browser Combo Mouse
EHCI Host Controller
EHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
```

..and I may have done myself no favours following the other instructions which has got me...
```
$ cat /etc/udev/rules.d/010_local.rules
BUS=="usb", KERNEL=="event*", SYSFS{product}=="WALTOP International Corp. Slim Tablet", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"
```

...which may or may not be interfearing ... I don't know.

However ... I did notice this in /var/log/Xorg.0.log...
```
(II) config/hal: Adding input device WALTOP International Corp. Slim Tablet
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
dlopen: /usr/lib/xorg/modules/input//wizardpen_drv.so: wrong ELF class: ELFCLASS32
(EE) Failed to load /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) UnloadModule: "wizardpen"
(EE) Failed to load module "wizardpen" (loader failed, 7)
(EE) No input driver matching `wizardpen'
```

...and I'm pretty sure the // shouldn't be in there. However I don't know what file that entry is in so I don't know where to go to put the right slashes in.

(it isn't in xorg.conf)

Anyone help please?

---

### Post by Favux on 2009-12-08
Hi msknight,

Up until Karmic you could use the linuxwacom drivers for your Waltop tablet.  See this thread:  [http://ubuntuforums.org/showthread.php?t=1261407](http://ubuntuforums.org/showthread.php?t=1261407)

To get it working in Karmic we've hacked the wcmUSB.c so that the linuxwacom driver won't reject the Waltop tablet, see posts #95 and #93 here:  [http://ubuntuforums.org/showthread.php?t=1261407&page=10](http://ubuntuforums.org/showthread.php?t=1261407&page=10)

We're also trying to compile the Waltop Linux Driver from the Waltop site.  It's basically a cut down version of the linuxwacom driver.  We've made a little progress but unfortunately not having much luck.  See:  [http://ubuntuforums.org/showthread.php?t=1326789](http://ubuntuforums.org/showthread.php?t=1326789)

---

### Post by msknight on 2009-12-08
Hi Favux,

THanks for the reply.

In the mean time, I've folowed this - [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) and I've got the wacom driver installed and running, but not listening to the tablet.

I'll read up.

IN the mean time, I've posted feedback to Genius asking why there aren't any Linux drivers. We'll see how they live up to their auto response where they thanked me for my help in making them a better company!

---

### Post by Favux on 2009-12-08
Hi msknight,

> In the mean time, I've folowed this - [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) and I've got the wacom driver installed and running, but not listening to the tablet.
Right, that's because starting somewhere about linuxwacom 0.8.2-x the wcmUSB.c started including a table of Vendor and Product ID's that exclude any non-wacom tablet.  That's why we had to hack it for Karmic so it would accept the Waltop tablet.

My guess is Genius, if they respond, will refer you to the linux driver at the Waltop site.

---

### Post by msknight on 2009-12-08
Well, the device is there ...

```
According to your input you may put following
lines into your XF86Config file:

        Driver          "wizardpen"
        Option          "Device"        "/dev/input/event6"
        Option          "TopX"          "434"
        Option          "TopY"          "197"
        Option          "BottomX"       "20000"
        Option          "BottomY"       "12500"
        Option          "MaxX"          "20000"
        Option          "MaxY"          "12500"

```

... but like you say it doesn't want to know about the Genius. I have been working through the other post and the driver "seems" to work, but just won't see the pad.

Doh!

---

### Post by msknight on 2009-12-08
I've tried the hacked version and that didn't work either.

I'm starting to think that I've got so many drivers and altered configuration files in here, that the whole thing is probably irrevocably wrecked!!!

I'm going to bed.

Thanks for the help Favux,

If you have any further ideas, please let me know. I'll feed back with Genius response if I get one.

---

### Post by msknight on 2009-12-09
Well, I got somewhere with this site again - [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) ... with a difference.  I deleted the symlink entry from the /etc/udev/rules.d/010_local.rules file.

At the moment it seems to be responding to the device as "Slim Tablet"

The cursor is responding, but as of yet none of the buttons.

I've got to go on a course so it will be a good while before I'm back and able to carry on.

---

### Post by Favux on 2009-12-09
Hi msknight,

Interesting.  If you think it's worthwhile we could construct a symlink for your tablet.  We'd need to look at:
```
lshal>msknight_lshal.txt
```
to make sure we got the Vendor and Product ID's correct.

---

### Post by msknight on 2009-12-09
Well, here is a grep through info.product...
```
michelle@michelle:/dev$ lshal | grep info.product
  info.product = 'Computer'  (string)
  info.product = 'Networking Interface'  (string)
  info.product = 'Platform Device (vboxdrv.0)'  (string)
  info.product = 'Power Button'  (string)
  info.product = 'Power Button'  (string)
  info.product = 'AMD Phenom(tm) II X4 905e Processor'  (string)
  info.product = 'AMD Phenom(tm) II X4 905e Processor'  (string)
  info.product = 'AMD Phenom(tm) II X4 905e Processor'  (string)
  info.product = 'AMD Phenom(tm) II X4 905e Processor'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.product = 'Loopback device Interface'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.product = 'System Board'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.product = 'Standard LPT printer port'  (string)
  info.product = 'Parallel Port Device'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.product = 'PC standard floppy disk controller'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.product = 'PnP Device (PNP0103)'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.product = 'PCI Bus'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.product = 'AT Translated Set 2 keyboard'  (string)
  info.product = 'Platform Device (floppy.0)'  (string)
  info.product = 'PC Floppy Drive'  (string)
  info.product = 'Platform Device (Fixed MDIO bus.0)'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] Link Control'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] Miscellaneous Control'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] DRAM Controller'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] Address Map'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration'  (string)
  info.product = 'SB700/SB800 USB OHCI2 Controller'  (string)
  info.product = '1.1 root hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'SBx00 PCI to PCI Bridge'  (string)
  info.product = 'TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)'  (string)
  info.product = 'SB700/SB800 LPC host controller'  (string)
  info.product = 'SBx00 Azalia (Intel HDA)'  (string)
  info.product = 'HDA ATI SB Sound Card'  (string)
  info.product = 'ALC889A Analog ALSA Capture Device'  (string)
  info.product = 'ALC889A Digital ALSA Playback Device'  (string)
  info.product = 'ALC889A Digital ALSA Capture Device'  (string)
  info.product = 'ALC889A Analog ALSA Playback Device'  (string)
  info.product = 'ALC889A Analog ALSA Capture Device'  (string)
  info.product = 'ALC889A Analog OSS Control Device'  (string)
  info.product = 'HDA ATI SB ALSA hardware specific Device'  (string)
  info.product = 'ALC889A Analog OSS PCM Device'  (string)
  info.product = 'HDA ATI SB ALSA Control Device'  (string)
  info.product = 'ALC889A Analog OSS PCM Device'  (string)
  info.product = 'ALC889A Analog OSS PCM Device'  (string)
  info.product = 'HDA Digital PCBeep'  (string)
  info.product = 'SB700/SB800 IDE Controller'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Device'  (string)
  info.product = 'DVDRW LH-18A1P'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.product = 'SBx00 SMBus Controller'  (string)
  info.product = 'SB700/SB800 USB EHCI Controller'  (string)
  info.product = '2.0 root hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'SB700 USB OHCI1 Controller'  (string)
  info.product = '1.1 root hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  info.product = '1.1 root hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'SB700/SB800 USB EHCI Controller'  (string)
  info.product = '2.0 root hub'  (string)
  info.product = 'HighSpeed Hub'  (string)
  info.product = 'Slim Tablet'  (string)
  info.product = 'USB HID Interface'  (string)
  info.product = 'WALTOP International Corp. Slim Tablet'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'HighSpeed Hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'Unknown (0x2005)'  (string)
  info.product = 'USB HID Interface'  (string)
  info.product = 'SideWinder Game Voice'  (string)
  info.product = 'USB HID Interface'  (string)
  info.product = 'Microsoft SideWinder Game Voice'  (string)
  info.product = 'Microsoft SideWinder Game Voice'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'SB700 USB OHCI1 Controller'  (string)
  info.product = '1.1 root hub'  (string)
  info.product = 'Browser Mouse'  (string)
  info.product = 'USB HID Interface'  (string)
  info.product = 'Cypress Sem PS2/USB Browser Combo Mouse'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  info.product = '1.1 root hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'SB700/SB800 SATA Controller [IDE mode]'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Device'  (string)
  info.product = 'CDDVDW SH-S223B'  (string)
  info.product = 'LEMM3D'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Device'  (string)
  info.product = 'SAMSUNG HD502HJ'  (string)
  info.product = 'Volume'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.product = 'Volume (swap)'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.product = 'RS780 PCI to PCI bridge (PCIE port 5)'  (string)
  info.product = 'RTL8111/8168B PCI Express Gigabit Ethernet controller'  (string)
  info.product = 'Networking Interface'  (string)
  info.product = 'RS780 PCI to PCI bridge (ext gfx port 0)'  (string)
  info.product = 'Unknown (0x0be3)'  (string)
  info.product = 'GT200 [GeForce 210]'  (string)
  info.product = 'RS780 Host Bridge Alternate'  (string)
```

...which ends up with ...
```
udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.mouse', 'input.tablet', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  info.product = 'WALTOP International Corp. Slim Tablet'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  input.product = 'WALTOP International Corp. Slim Tablet'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'gb'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0/input/input8/event6'  (string)

```


...and if I don't leave now, I'll miss my train.  See you in 13 hours-ish.

---

### Post by Favux on 2009-12-09
Hi msknight,

Don't miss your train!

That shows part of it, but what we want is something like:
```
  usb_device.product_id = 147  (0x93)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
```
From the udi etc. it's probably something close to:

vendor_id = 172f (?)

product_id = 0x34 (?)

---

### Post by msknight on 2009-12-09
Well, here is the whole thing!  Hope it isn't too big...

```

Dumping 133 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.callouts.add = {'hal-storage-cleanup-all-mountpoints'} (string list)
  info.capabilities = {'cpufreq_control'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  org.freedesktop.Hal.version = '0.5.13'  (string)
  org.freedesktop.Hal.version.major = 0  (0x0)  (int)
  org.freedesktop.Hal.version.micro = 13  (0xd)  (int)
  org.freedesktop.Hal.version.minor = 5  (0x5)  (int)
  power_management.acpi.linux.version = '20090521'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.quirk.dpms_on = true  (bool)
  power_management.quirk.dpms_suspend = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbemode_restore = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.quirk.vga_mode_3 = true  (bool)
  power_management.type = 'acpi'  (string)
  system.board.product = 'GA-MA785GMT-UD2H'  (string)
  system.board.serial = ''  (string)
  system.board.vendor = 'Gigabyte Technology Co., Ltd.'  (string)
  system.board.version = 'x.x'  (string)
  system.chassis.manufacturer = 'Gigabyte Technology Co., Ltd.'  (string)
  system.chassis.type = 'Desktop'  (string)
  system.firmware.release_date = '08/06/2009'  (string)
  system.firmware.vendor = 'Award Software International, Inc.'  (string)
  system.firmware.version = 'F2'  (string)
  system.formfactor = 'desktop'  (string)
  system.hardware.primary_video.product = 2661  (0xa65)  (int)
  system.hardware.primary_video.vendor = 4318  (0x10de)  (int)
  system.hardware.product = 'GA-MA785GMT-UD2H'  (string)
  system.hardware.serial = ''  (string)
  system.hardware.uuid = '30303234-3144-4434-3043-3835FFFFFFFF'  (string)
  system.hardware.vendor = 'Gigabyte Technology Co., Ltd.'  (string)
  system.hardware.version = ''  (string)
  system.kernel.machine = 'x86_64'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.31-16-generic'  (string)
  system.kernel.version.major = 2  (0x2)  (int)
  system.kernel.version.micro = 31  (0x1f)  (int)
  system.kernel.version.minor = 6  (0x6)  (int)

udi = '/org/freedesktop/Hal/devices/net_0a_00_27_00_00_00'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_0a_00_27_00_00_00'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/vboxnet0'  (string)
  net.80203.mac_address = 10995770589184  (0xa0027000000)  (uint64)
  net.address = '0a:00:27:00:00:00'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'vboxnet0'  (string)
  net.linux.ifindex = 3  (0x3)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'
  info.linux.driver = 'vboxdrv'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (vboxdrv.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/vboxdrv.0'  (string)
  platform.id = 'vboxdrv.0'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event1'  (string)
  input.product = 'Power Button'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'gb'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Power Button'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'gb'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AMD Phenom(tm) II X4 905e Processor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU0'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_CPU1'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AMD Phenom(tm) II X4 905e Processor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU1'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU1'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_CPU2'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AMD Phenom(tm) II X4 905e Processor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU2'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU2'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_CPU3'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AMD Phenom(tm) II X4 905e Processor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU3'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU3'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 3  (0x3)  (int)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'  (string)
  linux.device_file = '/dev/snd/timer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'  (string)
  linux.device_file = '/dev/sequencer2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer2'  (string)
  oss.device_file = '/dev/sequencer2'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'  (string)
  linux.device_file = '/dev/sequencer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer'  (string)
  oss.device_file = '/dev/sequencer'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  alsa.device_file = '/dev/snd/seq'  (string)
  alsa.type = 'sequencer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'  (string)
  linux.device_file = '/dev/snd/seq'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'  (string)

udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.capabilities = {'net', 'net.loopback'} (string list)
  info.category = 'net.loopback'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Loopback device Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/lo'  (string)
  net.address = '00:00:00:00:00:00'  (string)
  net.arp_proto_hw_id = 772  (0x304)  (int)
  net.interface = 'lo'  (string)
  net.linux.ifindex = 1  (0x1)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'System Board'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0d'  (string)
  pnp.description = 'System Board'  (string)
  pnp.id = 'PNP0c01'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  info.linux.driver = 'i8042 kbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.id = 'PNP0303'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0400'
  info.linux.driver = 'parport_pc'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Standard LPT printer port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0400'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.description = 'Standard LPT printer port'  (string)
  pnp.id = 'PNP0400'  (string)

udi = '/org/freedesktop/Hal/devices/ppdev_parport0'
  info.capabilities = {'ppdev'} (string list)
  info.category = 'ppdev'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0400'  (string)
  info.product = 'Parallel Port Device'  (string)
  info.subsystem = 'ppdev'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ppdev_parport0'  (string)
  linux.device_file = '/dev/parport0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'ppdev'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a/ppdev/parport0'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  access_control.file = '/dev/ttyS0'  (string)
  access_control.type = 'color'  (string)
  info.capabilities = {'serial', 'access_control'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PC standard floppy disk controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = 'PC standard floppy disk controller'  (string)
  pnp.id = 'PNP0700'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06'  (string)
  pnp.description = 'AT-style speaker sound'  (string)
  pnp.id = 'PNP0800'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  info.linux.driver = 'rtc_cmos'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.description = 'AT Real-Time Clock'  (string)
  pnp.id = 'PNP0b00'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0103)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
  pnp.id = 'PNP0103'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.description = 'AT DMA Controller'  (string)
  pnp.id = 'PNP0200'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:01'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0a03'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PCI Bus'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a03'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:00'  (string)
  pnp.description = 'PCI Bus'  (string)
  pnp.id = 'PNP0a03'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'i8042'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.linux.driver = 'atkbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
  serio.id = 'serio0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.product = 'AT Translated Set 2 keyboard'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'gb'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/platform_floppy_0'
  info.linux.driver = 'floppy'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (floppy.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_floppy_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/floppy.0'  (string)
  platform.id = 'floppy.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy'
  block.device = '/dev/fd0'  (string)
  block.is_volume = false  (bool)
  block.major = 2  (0x2)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/platform_floppy_0'  (string)
  info.product = 'PC Floppy Drive'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy'  (string)
  info.vendor = ''  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/platform/floppy.0/block/fd0'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'platform'  (string)
  storage.drive_type = 'floppy'  (string)
  storage.hotpluggable = false  (bool)
  storage.media_check_enabled = false  (bool)
  storage.model = ''  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/platform_floppy_0'  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.requires_eject = false  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'PC Floppy Drive'  (string)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'uid='} (string list)

udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (Fixed MDIO bus.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'  (string)
  platform.id = 'Fixed MDIO bus.0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1022_1204'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] Link Control'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1204'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.4'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.4'  (string)
  pci.product = 'K10 [Opteron, Athlon64, Sempron] Link Control'  (string)
  pci.product_id = 4612  (0x1204)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_1203'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] Miscellaneous Control'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1203'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.3'  (string)
  pci.product = 'K10 [Opteron, Athlon64, Sempron] Miscellaneous Control'  (string)
  pci.product_id = 4611  (0x1203)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_1202'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] DRAM Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1202'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.2'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.2'  (string)
  pci.product = 'K10 [Opteron, Athlon64, Sempron] DRAM Controller'  (string)
  pci.product_id = 4610  (0x1202)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_1201'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] Address Map'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1201'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.1'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.1'  (string)
  pci.product = 'K10 [Opteron, Athlon64, Sempron] Address Map'  (string)
  pci.product_id = 4609  (0x1201)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_1200'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1200'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.0'  (string)
  pci.product = 'K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration'  (string)
  pci.product_id = 4608  (0x1200)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4399'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB OHCI2 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4399'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5'  (string)
  pci.product = 'SB700/SB800 USB OHCI2 Controller'  (string)
  pci.product_id = 17305  (0x4399)  (int)
  pci.subsys_product_id = 20484  (0x5004)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4399'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/007/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7'  (string)
  usb_device.bus_number = 7  (0x7)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:14.5'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0'  (string)
  usb.bus_number = 7  (0x7)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:14.5'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4384'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SBx00 PCI to PCI Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4384'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4'  (string)
  pci.product = 'SBx00 PCI to PCI Bridge'  (string)
  pci.product_id = 17284  (0x4384)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_104c_8024'
  info.linux.driver = 'ohci1394'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4384'  (string)
  info.product = 'TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_104c_8024'  (string)
  info.vendor = 'Texas Instruments'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:03:0e.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:03:0e.0'  (string)
  pci.product = 'TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)'  (string)
  pci.product_id = 32804  (0x8024)  (int)
  pci.subsys_product_id = 4096  (0x1000)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'Texas Instruments'  (string)
  pci.vendor_id = 4172  (0x104c)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_439d'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 LPC host controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439d'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.3'  (string)
  pci.product = 'SB700/SB800 LPC host controller'  (string)
  pci.product_id = 17309  (0x439d)  (int)
  pci.subsys_product_id = 17309  (0x439d)  (int)
  pci.subsys_vendor = 'ATI Technologies Inc'  (string)
  pci.subsys_vendor_id = 4098  (0x1002)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383'
  info.linux.driver = 'HDA Intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SBx00 Azalia (Intel HDA)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2'  (string)
  pci.product = 'SBx00 Azalia (Intel HDA)'  (string)
  pci.product_id = 17283  (0x4383)  (int)
  pci.subsys_product_id = 41218  (0xa102)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)
  info.product = 'HDA ATI SB Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0'  (string)
  sound.card = 0  (0x0)  (int)
  sound.card_id = 'HDA ATI SB'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_2'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 2  (0x2)  (int)
  alsa.device_file = '/dev/snd/pcmC0D2c'  (string)
  alsa.device_id = 'ALC889A Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Analog ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_2'  (string)
  linux.device_file = '/dev/snd/pcmC0D2c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D2c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1p'  (string)
  alsa.device_id = 'ALC889A Digital'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Digital ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D1p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1c'  (string)
  alsa.device_id = 'ALC889A Digital'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Digital ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'ALC889A Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Analog ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'ALC889A Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Analog ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_mixer__1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Analog OSS Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA ATI SB'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'ALC889A Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_hw_specific_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/hwC0D0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.type = 'hw_specific'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'HDA ATI SB ALSA hardware specific Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_hw_specific_0'  (string)
  linux.device_file = '/dev/snd/hwC0D0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/hwC0D0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA ATI SB'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'ALC889A Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.type = 'control'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'HDA ATI SB ALSA Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA ATI SB'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'ALC889A Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC889A Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_1'  (string)
  linux.device_file = '/dev/adsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/adsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA ATI SB'  (string)
  oss.device = 1  (0x1)  (int)
  oss.device_file = '/dev/adsp'  (string)
  oss.device_id = 'ALC889A Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)
  info.product = 'HDA Digital PCBeep'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)
  input.product = 'HDA Digital PCBeep'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/input/input7/event7'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c'
  info.linux.driver = 'pata_atiixp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 IDE Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 138  (0x8a)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1'  (string)
  pci.product = 'SB700/SB800 IDE Controller'  (string)
  pci.product_id = 17308  (0x439c)  (int)
  pci.subsys_product_id = 20482  (0x5002)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host5/scsi_host/host5'  (string)
  scsi_host.host = 5  (0x5)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/scsi_host/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 4  (0x4)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'DVDRW LH-18A1P'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'LITE-ON'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_18A1P'
  block.device = '/dev/sr1'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_18A1P'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0'  (string)
  info.product = 'DVDRW LH-18A1P'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_18A1P'  (string)
  info.vendor = 'LITE-ON'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0/block/sr1'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 8467  (0x2113)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 8467  (0x2113)  (int)
  storage.cdrom.write_speeds = {'8467', '7056', '5645', '4234', '2822', '2112', '1764', '1411', '706'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = 'GL03'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'DVDRW LH-18A1P'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'LITE-ON'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0/scsi_generic/sg2'  (string)
  scsi_generic.device = '/dev/sg2'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4385'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SBx00 SMBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4385'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 5  (0x5)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.0'  (string)
  pci.product = 'SBx00 SMBus Controller'  (string)
  pci.product_id = 17285  (0x4385)  (int)
  pci.subsys_product_id = 17285  (0x4385)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4396_0'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB EHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4396_0'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2'  (string)
  pci.product = 'SB700/SB800 USB EHCI Controller'  (string)
  pci.product_id = 17302  (0x4396)  (int)
  pci.subsys_product_id = 20484  (0x5004)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4396_0'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/002/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 6  (0x6)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:13.2'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 6  (0x6)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:13.2'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4398_0'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700 USB OHCI1 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4398_0'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1'  (string)
  pci.product = 'SB700 USB OHCI1 Controller'  (string)
  pci.product_id = 17304  (0x4398)  (int)
  pci.subsys_product_id = 20484  (0x5004)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4398_0'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/006/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6'  (string)
  usb_device.bus_number = 6  (0x6)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:13.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0'  (string)
  usb.bus_number = 6  (0x6)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:13.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4397_0'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4397_0'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0'  (string)
  pci.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  pci.product_id = 17303  (0x4397)  (int)
  pci.subsys_product_id = 20484  (0x5004)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4397_0'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/005/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:13.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:13.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4396'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB EHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4396'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2'  (string)
  pci.product = 'SB700/SB800 USB EHCI Controller'  (string)
  pci.product_id = 17302  (0x4396)  (int)
  pci.subsys_product_id = 20484  (0x5004)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4396'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 6  (0x6)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:12.2'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'  (string)
  info.product = 'HighSpeed Hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial'  (string)
  info.vendor = 'NEC Corp.'  (string)
  linux.device_file = '/dev/bus/usb/001/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 1  (0x1)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 4  (0x4)  (int)
  usb_device.product = 'HighSpeed Hub'  (string)
  usb_device.product_id = 90  (0x5a)  (int)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'NEC Corp.'  (string)
  usb_device.vendor_id = 1033  (0x409)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial'  (string)
  info.product = 'Slim Tablet'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'  (string)
  info.vendor = 'WALTOP International Corp.'  (string)
  linux.device_file = '/dev/bus/usb/001/008'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 4357  (0x1105)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 8  (0x8)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Slim Tablet'  (string)
  usb_device.product_id = 52  (0x34)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'WALTOP International Corp.'  (string)
  usb_device.vendor_id = 5935  (0x172f)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 4357  (0x1105)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 8  (0x8)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 52  (0x34)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'WALTOP International Corp.'  (string)
  usb.vendor_id = 5935  (0x172f)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.mouse', 'input.tablet', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  info.product = 'WALTOP International Corp. Slim Tablet'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  input.product = 'WALTOP International Corp. Slim Tablet'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'gb'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0/input/input8/event6'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 4  (0x4)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 90  (0x5a)  (int)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'NEC Corp.'  (string)
  usb.vendor_id = 1033  (0x409)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial'  (string)
  info.product = 'HighSpeed Hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial_0'  (string)
  info.vendor = 'NEC Corp.'  (string)
  linux.device_file = '/dev/bus/usb/001/006'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.4'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 1  (0x1)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 6  (0x6)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.4'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 4  (0x4)  (int)
  usb_device.product = 'HighSpeed Hub'  (string)
  usb_device.product_id = 90  (0x5a)  (int)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'NEC Corp.'  (string)
  usb_device.vendor_id = 1033  (0x409)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.4/1-4.4:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 6  (0x6)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.4/1-4.4:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 4  (0x4)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 90  (0x5a)  (int)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'NEC Corp.'  (string)
  usb.vendor_id = 1033  (0x409)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_971_2005_noserial'
  access_control.file = '/dev/bus/usb/001/007'  (string)
  access_control.type = 'color'  (string)
  info.capabilities = {'access_control'} (string list)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial_0'  (string)
  info.product = 'Unknown (0x2005)'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_971_2005_noserial'  (string)
  info.vendor = 'Gretag-Macbeth AG'  (string)
  linux.device_file = '/dev/bus/usb/001/007'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.4/1-4.4.4'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 1  (0x1)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 7  (0x7)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.4/1-4.4.4'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product_id = 8197  (0x2005)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Gretag-Macbeth AG'  (string)
  usb_device.vendor_id = 2417  (0x971)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_971_2005_noserial_if0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_971_2005_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_971_2005_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.4/1-4.4.4/1-4.4.4:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 1  (0x1)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 7  (0x7)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.4/1-4.4.4/1-4.4.4:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 8197  (0x2005)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Gretag-Macbeth AG'  (string)
  usb.vendor_id = 2417  (0x971)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_409_5a_noserial'  (string)
  info.product = 'SideWinder Game Voice'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial'  (string)
  info.vendor = 'Microsoft Corp.'  (string)
  linux.device_file = '/dev/bus/usb/001/004'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 257  (0x101)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 4  (0x4)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.1'  (string)
  usb_device.max_power = 80  (0x50)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'SideWinder Game Voice'  (string)
  usb_device.product_id = 59  (0x3b)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Microsoft Corp.'  (string)
  usb_device.vendor_id = 1118  (0x45e)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.1/1-4.1:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 257  (0x101)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 4  (0x4)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.1/1-4.1:1.0'  (string)
  usb.max_power = 80  (0x50)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 59  (0x3b)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Microsoft Corp.'  (string)
  usb.vendor_id = 1118  (0x45e)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0_hiddev'
  hiddev.application_pages = {'Unknown page 0xb0005'} (string list)
  hiddev.device = '/dev/usb/hiddev0'  (string)
  hiddev.product = 'Microsoft SideWinder Game Voice'  (string)
  info.capabilities = {'hiddev'} (string list)
  info.category = 'hiddev'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0'  (string)
  info.product = 'Microsoft SideWinder Game Voice'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0_hiddev'  (string)
  linux.device_file = '/dev/usb/hiddev0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.1/1-4.1:1.0/usb/hiddev0'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0'  (string)
  info.product = 'Microsoft SideWinder Game Voice'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_45e_3b_noserial_if0'  (string)
  input.product = 'Microsoft SideWinder Game Voice'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.1/1-4.1:1.0/input/input5/event5'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 6  (0x6)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:12.2'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4398'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700 USB OHCI1 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4398'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1'  (string)
  pci.product = 'SB700 USB OHCI1 Controller'  (string)
  pci.product_id = 17304  (0x4398)  (int)
  pci.subsys_product_id = 20484  (0x5004)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4398'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/004/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:12.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'  (string)
  info.product = 'Browser Mouse'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial'  (string)
  info.vendor = 'Chic Technology Corp.'  (string)
  linux.device_file = '/dev/bus/usb/004/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration = 'HID Mouse'  (string)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Browser Mouse'  (string)
  usb_device.product_id = 17  (0x11)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Chic Technology Corp.'  (string)
  usb_device.vendor_id = 1534  (0x5fe)  (int)
  usb_device.version = 1.0 (1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration = 'HID Mouse'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.description = 'EndPoint1 Int&#4709;'  (string)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 17  (0x11)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Chic Technology Corp.'  (string)
  usb.vendor_id = 1534  (0x5fe)  (int)
  usb.version = 1.0 (1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial_if0'  (string)
  info.product = 'Cypress Sem PS2/USB Browser Combo Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_5fe_11_noserial_if0'  (string)
  input.product = 'Cypress Sem PS2/USB Browser Combo Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4/event4'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:12.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4397'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4397'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0'  (string)
  pci.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  pci.product_id = 17303  (0x4397)  (int)
  pci.subsys_product_id = 20484  (0x5004)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4397'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/003/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:12.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:12.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390'
  info.linux.driver = 'ahci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 SATA Controller [IDE mode]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 6  (0x6)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0'  (string)
  pci.product = 'SB700/SB800 SATA Controller [IDE mode]'  (string)
  pci.product_id = 17296  (0x4390)  (int)
  pci.subsys_product_id = 45058  (0xb002)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_2'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host3/scsi_host/host3'  (string)
  scsi_host.host = 3  (0x3)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_1'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host2/scsi_host/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host1/scsi_host/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0'
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host1/target1:0:0/1:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 1  (0x1)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'CDDVDW SH-S223B'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'TSSTcorp'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223B'
  block.device = '/dev/sr0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223B'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'CDDVDW SH-S223B'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223B'  (string)
  info.vendor = 'TSSTcorp'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host1/target1:0:0/1:0:0:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 8468  (0x2114)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 8468  (0x2114)  (int)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = 'SB01'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'CDDVDW SH-S223B'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 526696448  (0x1f64c000)  (uint64)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'TSSTcorp'  (string)

udi = '/org/freedesktop/Hal/devices/volume_label_LEMM3D'
  block.device = '/dev/sr0'  (string)
  block.is_volume = true  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223B'  (string)
  info.capabilities = {'volume.disc', 'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume', 'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223B'  (string)
  info.product = 'LEMM3D'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_label_LEMM3D'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host1/target1:0:0/1:0:0:0/block/sr0/fakevolume'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'extra_options', 'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-eject', 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Eject', 'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'as', 'ssas', 'as', 'as'} (string list)
  volume.block_size = 2048  (0x800)  (int)
  volume.disc.capacity = 526696448  (0x1f64c000)  (uint64)
  volume.disc.has_audio = true  (bool)
  volume.disc.has_data = true  (bool)
  volume.disc.is_appendable = false  (bool)
  volume.disc.is_blank = false  (bool)
  volume.disc.is_rewritable = false  (bool)
  volume.disc.type = 'cd_rom'  (string)
  volume.fstype = 'iso9660'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = true  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = false  (bool)
  volume.label = 'LEMM3D'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'uid=', 'mode=', 'iocharset='} (string list)
  volume.mount_point = ''  (string)
  volume.num_blocks = 1028704  (0xfb260)  (uint64)
  volume.size = 526696448  (0x1f64c000)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host1/target1:0:0/1:0:0:0/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/scsi_host/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'SAMSUNG HD502HJ'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SAMSUNG HD502HJ'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '1AJ100E4'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'SAMSUNG HD502HJ'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 500107862016  (0x7470c06000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  storage.size = 500107862016  (0x7470c06000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda2'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = ''  (string)
  volume.fsusage = 'partitiontable'  (string)
  volume.fsversion = ''  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 2  (0x2)  (uint64)
  volume.partition.flags = {} (string list)
  volume.partition.label = ''  (string)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 50108405760  (0xbaab19800)  (uint64)
  volume.partition.type = '0x05'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 1024  (0x400)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_754f565b_24aa_4317_8abf_e3d174827dfb'
  block.device = '/dev/sda6'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 6  (0x6)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_754f565b_24aa_4317_8abf_e3d174827dfb'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda6'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext4'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec'} (string list)
  volume.mount_point = '/xp'  (string)
  volume.num_blocks = 97659072  (0x5d228c0)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 6  (0x6)  (int)
  volume.partition.start = 55101182976  (0xcd4495400)  (uint64)
  volume.size = 50001444864  (0xba4518000)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '754f565b-24aa-4317-8abf-e3d174827dfb'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_73c0cff2_66f0_4cf4_a06c_d2f5a9bb8dcd'
  block.device = '/dev/sda7'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 7  (0x7)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_73c0cff2_66f0_4cf4_a06c_d2f5a9bb8dcd'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda7'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext4'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec'} (string list)
  volume.mount_point = '/home'  (string)
  volume.num_blocks = 771489432  (0x2dfbfe98)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 7  (0x7)  (int)
  volume.partition.start = 105102660096  (0x18789b5200)  (uint64)
  volume.size = 395002589184  (0x5bf7fd3000)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '73c0cff2-66f0-4cf4-a06c-d2f5a9bb8dcd'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_1b6016de_1318_4571_a1b3_9410c6bc2d28'
  block.device = '/dev/sda5'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 5  (0x5)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.product = 'Volume (swap)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_1b6016de_1318_4571_a1b3_9410c6bc2d28'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda5'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'swap'  (string)
  volume.fsusage = 'other'  (string)
  volume.fsversion = '2'  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 9751392  (0x94cb60)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 5  (0x5)  (int)
  volume.partition.start = 50108438016  (0xbaab21600)  (uint64)
  volume.size = 4992712704  (0x12996c000)  (uint64)
  volume.uuid = '1b6016de-1318-4571-a1b3-9410c6bc2d28'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_6849e173_672c_4b8f_afff_982fb5461392'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502HJ_S20BJDWS832444'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_6849e173_672c_4b8f_afff_982fb5461392'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext4'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec'} (string list)
  volume.mount_point = '/'  (string)
  volume.num_blocks = 97867917  (0x5d5588d)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.size = 50108373504  (0xbaab11a00)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '6849e173-672c-4b8f-afff-982fb5461392'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1022_9609'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'RS780 PCI to PCI bridge (PCIE port 5)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9609'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0'  (string)
  pci.product = 'RS780 PCI to PCI bridge (PCIE port 5)'  (string)
  pci.product_id = 38409  (0x9609)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_10ec_8168'
  info.linux.driver = 'r8169'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9609'  (string)
  info.product = 'RTL8111/8168B PCI Express Gigabit Ethernet controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_10ec_8168'  (string)
  info.vendor = 'Realtek Semiconductor Co., Ltd.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0'  (string)
  pci.product = 'RTL8111/8168B PCI Express Gigabit Ethernet controller'  (string)
  pci.product_id = 33128  (0x8168)  (int)
  pci.subsys_product_id = 57344  (0xe000)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'Realtek Semiconductor Co., Ltd.'  (string)
  pci.vendor_id = 4332  (0x10ec)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_24_1d_d4_0c_85'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_10ec_8168'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_24_1d_d4_0c_85'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0/net/eth1'  (string)
  net.80203.mac_address = 155119258757  (0x241dd40c85)  (uint64)
  net.address = '00:24:1d:d4:0c:85'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth1'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_10ec_8168'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_1022_9603'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'RS780 PCI to PCI bridge (ext gfx port 0)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9603'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.product = 'RS780 PCI to PCI bridge (ext gfx port 0)'  (string)
  pci.product_id = 38403  (0x9603)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_10de_be3'
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9603'  (string)
  info.product = 'Unknown (0x0be3)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_be3'  (string)
  info.vendor = 'nVidia Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1'  (string)
  pci.product_id = 3043  (0xbe3)  (int)
  pci.subsys_product_id = 13525  (0x34d5)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'nVidia Corporation'  (string)
  pci.vendor_id = 4318  (0x10de)  (int)

udi = '/org/freedesktop/Hal/devices/pci_10de_a65'
  info.linux.driver = 'nvidia'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9603'  (string)
  info.product = 'GT200 [GeForce 210]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_a65'  (string)
  info.vendor = 'nVidia Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0'  (string)
  pci.product = 'GT200 [GeForce 210]'  (string)
  pci.product_id = 2661  (0xa65)  (int)
  pci.subsys_product_id = 13525  (0x34d5)  (int)
  pci.subsys_vendor = 'Giga-byte Technology'  (string)
  pci.subsys_vendor_id = 5208  (0x1458)  (int)
  pci.vendor = 'nVidia Corporation'  (string)
  pci.vendor_id = 4318  (0x10de)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_9601'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'RS780 Host Bridge Alternate'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9601'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = 'RS780 Host Bridge Alternate'  (string)
  pci.product_id = 38401  (0x9601)  (int)
  pci.subsys_product_id = 38401  (0x9601)  (int)
  pci.subsys_vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.subsys_vendor_id = 4130  (0x1022)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/fuse'
  access_control.file = '/dev/fuse'  (string)
  access_control.type = 'camera'  (string)
  info.capabilities = {'access_control'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9601'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/fuse'  (string)


Dumped 133 device(s) from the Global Device List.
------------------------------------------------

```

---

### Post by msknight on 2009-12-09
I had a brief look but couldn't find anything.  I'm only just back and exhausted. After dinner I'll come back and have another crack at it.

---

### Post by Favux on 2009-12-09
Hi msknight,

Hope your trip was productive.

This is what we wanted:
```
  usb_device.product = 'Slim Tablet'  (string)
  usb_device.product_id = 52  (0x34)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'WALTOP International Corp.'  (string)
  usb_device.vendor_id = 5935  (0x172f)  (int)
```
Assuming the vendor id is the generic Waltop one this should work for all Waltop tablets:
```
BUS=="usb", KERNEL=="event*", ATTRS{idVendor}=="172f", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"
```
to make it specific to your product:
```
BUS=="usb", KERNEL=="event*", ATTRS{idVendor}=="172f", ATTRS{idProduct}=="0034", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"
```
I don't quite understand the original WizardPen rule.  I'm not sure if:
```
BUS=="usb", 
```
is needed.

Since Waltops don't have touch I'd think something like:
```
# Link Waltop USB tablet to "/dev/input/waltop"
KERNEL=="event*", ATTRS{idVendor}=="172f", ATTRS{idProduct}=="0034", SYMLINK="input/waltop"
```
would work.  Of course not for the WizardPen driver.  The "+=" is to add it to a table.  What table?  I guess:
```
SYMLINK+="tablet-event", MODE="0666"
```
is required somewhere in the driver code.  Forgive the excursion.

As an aside if you right click on the lshal and use Create Archive you can attach the compressed file to your post with Manage Attachments.

---

### Post by msknight on 2009-12-09
Hi Favux,

I'll admit - at this stage, I'm lost. You'll have to tell me what to do!

Michelle.

---

### Post by Favux on 2009-12-09
Hi Michelle,

Sorry.  What I'm hoping is that if you substitute this rule:
```
BUS=="usb", KERNEL=="event*", ATTRS{idVendor}=="172f", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"
```
for your original WizardPen rule the WizardPen driver will work for your Waltop tablet.  From what you were saying it sounded like it almost was working.

---

### Post by msknight on 2009-12-09
Done. Still the same, mouse moves but no pressure and no buttons.

There is no sign of anything in the /dev/input apart from the normal event and mouse listings.

However...

In dev/input/by-id there is the following...

```
michelle@michelle:/dev/input/by-id$ ls -la
total 0
drwxr-xr-x 2 root root 120 2009-12-09 20:42 .
drwxr-xr-x 4 root root 320 2009-12-09 20:43 ..
lrwxrwxrwx 1 root root   9 2009-12-09 20:42 usb-Cypress_Sem_PS2_USB_Browser_Combo_Mouse-event-mouse -> ../event4
lrwxrwxrwx 1 root root   9 2009-12-09 20:42 usb-Cypress_Sem_PS2_USB_Browser_Combo_Mouse-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2009-12-09 20:42 usb-Microsoft_SideWinder_Game_Voice-event-if00 -> ../event5
lrwxrwxrwx 1 root root   9 2009-12-09 20:42 usb-WALTOP_International_Corp._Slim_Tablet-event-if00 -> ../event6

```

..but I still can't calibrate using this handle - still permission denied.

---

### Post by Favux on 2009-12-09
Hi Michelle,

OK, this may be a dead end.  It sounds like a mouse/touchpad .fdi (through evdev) is configuring.  Your first lshal showed:
```
  input.x11_driver = 'evdev'  (string)
```
What we'd want to see in lshal is probably a new section with the udi containing 172f and logicaldev_input where:
```
  input.x11_driver = 'wizardpen'  (string)
```
would indicate the WizardPen driver was picking up your tablet.

To figure out if evdev (or whatever) still has it we can look at, in addition to lshal:
```
xinput --list
```
and your Xorg.0.log in /var/log/.

We could try playing with the match lines on your .fdi but it just may be the WizardPen driver won't attach to your tablet.  The Xorg.0.log would show if it tried and then dropped it.  Maybe with some useful error messages.

---

### Post by msknight on 2009-12-09
Here is the first...
```
michelle@michelle:~/wizardpen-0.6.0.2/calibrate$ xinput --list                                                  
"Virtual core pointer"  id=0    [XPointer]                                                                      
        Num_buttons is 32                                                                                       
        Num_axes is 2                                                                                           
        Mode is Relative                                                                                        
        Motion_buffer is 256                                                                                    
        Axis 0 :                                                                                                
                Min_value is -1                                                                                 
                Max_value is -1                                                                                 
                Resolution is 0                                                                                 
        Axis 1 :                                                                                                
                Min_value is -1                                                                                 
                Max_value is -1                                                                                 
                Resolution is 0                                                                                 
"Virtual core keyboard" id=1    [XKeyboard]                                                                     
        Num_keys is 248                                                                                         
        Min_keycode is 8                                                                                        
        Max_keycode is 255                                                                                      
"WALTOP International Corp. Slim Tablet"        id=2    [XExtensionKeyboard]                                    
        Type is KEYBOARD                                                                                        
        Num_keys is 248                                                                                         
        Min_keycode is 8                                                                                        
        Max_keycode is 255                                                                                      
        Num_buttons is 13                                                                                       
        Num_axes is 20                                                                                          
        Mode is Absolute                                                                                        
        Motion_buffer is 256                                                                                    
        Axis 0 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 20000                                                                              
                Resolution is 10000                                                                             
        Axis 1 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 12500                                                                              
                Resolution is 10000                                                                             
        Axis 2 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 1023                                                                               
                Resolution is 10000                                                                             
        Axis 3 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 4 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 5 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 6 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 7 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 8 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 9 :                                                                                                
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 10 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 11 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 12 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 13 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 14 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 15 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 16 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 17 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 18 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
        Axis 19 :                                                                                               
                Min_value is 0                                                                                  
                Max_value is 255                                                                                
                Resolution is 10000                                                                             
"Power Button"  id=3    [XExtensionKeyboard]                                                                    
        Type is KEYBOARD                                                                                        
        Num_keys is 248                                                                                         
        Min_keycode is 8                                                                                        
        Max_keycode is 255
"AT Translated Set 2 keyboard"  id=4    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Power Button"  id=5    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Macintosh mouse button emulation"      id=6    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 5
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"Cypress Sem PS2/USB Browser Combo Mouse"       id=7    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 13
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1

```

---

### Post by msknight on 2009-12-09
Here is the second...
```
michelle@michelle:/var/log$ cat Xorg.0.log
                                                                                                                                              
X.Org X Server 1.6.4                                                                                                                          
Release Date: 2009-9-27                                                                                                                        
X Protocol Version 11, Revision 0                                                                                                              
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu                                                                                   
Current Operating System: Linux michelle 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009 x86_64                                   
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=6849e173-672c-4b8f-afff-982fb5461392 ro quiet splash                  
Build Date: 26 October 2009  05:19:56PM                                                                                                         
xorg-server 2:1.6.4-2ubuntu4 (buildd@)                                                                                                          
        Before reporting problems, check http://wiki.x.org                                                                                      
        to make sure that you have the latest version.                                                                                          
Markers: (--) probed, (**) from config file, (==) default setting,                                                                              
        (++) from command line, (!!) notice, (II) informational,                                                                                
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.                                                                           
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  9 20:43:04 2009                                                                            
(==) Using config file: "/etc/X11/xorg.conf"                                                                                                    
(==) ServerLayout "Layout0"                                                                                                                     
(**) |-->Screen "Screen0" (0)                                                                                                                   
(**) |   |-->Monitor "Monitor0"                                                                                                                 
(**) |   |-->Device "Device0"                                                                                                                   
(**) |-->Input Device "Keyboard0"                                                                                                               
(**) |-->Input Device "Mouse0"                                                                                                                  
(**) |-->Input Device "WizardPen Tablet"                                                                                                        
(**) Option "Xinerama" "0"                                                                                                                      
(==) Automatically adding devices                                                                                                               
(==) Automatically enabling devices                                                                                                             
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.                                                                              
        Entry deleted from font path.                                                                                                           
(==) FontPath set to:                                                                                                                           
        /usr/share/fonts/X11/misc,                                                                                                              
        /usr/share/fonts/X11/100dpi/:unscaled,                                                                                                  
        /usr/share/fonts/X11/75dpi/:unscaled,                                                                                                   
        /usr/share/fonts/X11/Type1,                                                                                                             
        /usr/share/fonts/X11/100dpi,                                                                                                            
        /usr/share/fonts/X11/75dpi,                                                                                                             
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,                                                                                       
        built-ins                                                                                                                               
(==) ModulePath set to "/usr/lib/xorg/modules"                                                                                                  
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.                                                 
(WW) Disabling Keyboard0                                                                                                                        
(WW) Disabling Mouse0                                                                                                                           
(II) Loader magic: 0xb40                                                                                                                        
(II) Module ABI versions:                                                                                                                       
        X.Org ANSI C Emulation: 0.4                                                                                                             
        X.Org Video Driver: 5.0                                                                                                                 
        X.Org XInput driver : 4.0                                                                                                               
        X.Org Server Extension : 2.0                                                                                                            
(II) Loader running on linux                                                                                                                    
(++) using VT number 7                                                                                                                          

(--) PCI:*(0:1:0:0) 10de:0a65:1458:34d5 nVidia Corporation GT200 [GeForce 210] rev 162, Mem @ 0xfb000000/16777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288                                                                                      
(II) Open ACPI successful (/var/run/acpid.socket)                                                                                                
(II) System resource ranges:                                                                                                                     
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.                                                 
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.                                                    
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.                                                    
(II) "record" will be loaded by default.                                                                                                         
(II) "dri" will be loaded by default.                                                                                                            
(II) "dri2" will be loaded by default.                                                                                                           
(II) LoadModule: "dbe"                                                                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so                                                                                         
(II) Module dbe: vendor="X.Org Foundation"                                                                                                       
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        Module class: X.Org Server Extension                                                                                                     
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension DOUBLE-BUFFER                                                                                                             
(II) LoadModule: "extmod"                                                                                                                        
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so                                                                                      
(II) Module extmod: vendor="X.Org Foundation"                                                                                                    
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        Module class: X.Org Server Extension                                                                                                     
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension MIT-SCREEN-SAVER                                                                                                          
(II) Loading extension XFree86-VidModeExtension                                                                                                  
(II) Loading extension XFree86-DGA                                                                                                               
(II) Loading extension DPMS                                                                                                                      
(II) Loading extension XVideo                                                                                                                    
(II) Loading extension XVideo-MotionCompensation                                                                                                 
(II) Loading extension X-Resource                                                                                                                
(II) LoadModule: "type1"                                                                                                                         
(WW) Warning, couldn't open module type1                                                                                                         
(II) UnloadModule: "type1"                                                                                                                       
(EE) Failed to load module "type1" (module does not exist, 0)                                                                                    
(II) LoadModule: "freetype"                                                                                                                      
(WW) Warning, couldn't open module freetype                                                                                                      
(II) UnloadModule: "freetype"                                                                                                                    
(EE) Failed to load module "freetype" (module does not exist, 0)                                                                                 
(II) LoadModule: "glx"                                                                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so                                                                                         
(II) Module glx: vendor="NVIDIA Corporation"                                                                                                     
        compiled for 4.0.2, module version = 1.0.0                                                                                               
        Module class: X.Org Server Extension                                                                                                     
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009                                                                                  
(II) Loading extension GLX                                                                                                                       
(II) LoadModule: "record"                                                                                                                        
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so                                                                                      
(II) Module record: vendor="X.Org Foundation"                                                                                                    
        compiled for 1.6.4, module version = 1.13.0                                                                                              
        Module class: X.Org Server Extension                                                                                                     
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension RECORD                                                                                                                    
(II) LoadModule: "dri"                                                                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so                                                                                         
(II) Module dri: vendor="X.Org Foundation"                                                                                                       
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension XFree86-DRI                                                                                                               
(II) LoadModule: "dri2"                                                                                                                          
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so                                                                                        
(II) Module dri2: vendor="X.Org Foundation"                                                                                                      
        compiled for 1.6.4, module version = 1.1.0                                                                                               
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension DRI2                                                                                                                      
(II) LoadModule: "nvidia"                                                                                                                        
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so                                                                                        
(II) Module nvidia: vendor="NVIDIA Corporation"                                                                                                  
        compiled for 4.0.2, module version = 1.0.0                                                                                               
        Module class: X.Org Video Driver                                                                                                         
(II) LoadModule: "wizardpen"                                                                                                                     
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                       
dlopen: /usr/lib/xorg/modules/input//wizardpen_drv.so: wrong ELF class: ELFCLASS32                                                               
(EE) Failed to load /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                
(II) UnloadModule: "wizardpen"                                                                                                                   
(EE) Failed to load module "wizardpen" (loader failed, 7)                                                                                        
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:51:02 PDT 2009                                                                           
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs                                                                                         
(II) Primary Device is: PCI 01@00:00:0                                                                                                           
(II) Loading sub module "fb"                                                                                                                     
(II) LoadModule: "fb"                                                                                                                            
(II) Loading /usr/lib/xorg/modules//libfb.so                                                                                                     
(II) Module fb: vendor="X.Org Foundation"                                                                                                        
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        ABI class: X.Org ANSI C Emulation, version 0.4                                                                                           
(II) Loading sub module "wfb"                                                                                                                    
(II) LoadModule: "wfb"                                                                                                                           
(II) Loading /usr/lib/xorg/modules//libwfb.so                                                                                                    
(II) Module wfb: vendor="X.Org Foundation"                                                                                                       
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        ABI class: X.Org ANSI C Emulation, version 0.4                                                                                           
(II) Loading sub module "ramdac"                                                                                                                 
(II) LoadModule: "ramdac"                                                                                                                        
(II) Module "ramdac" already built-in                                                                                                            
(II) resource ranges after probing:                                                                                                              
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32                                                                                                
(==) NVIDIA(0): RGB weight 888                                                                                                                   
(==) NVIDIA(0): Default visual is TrueColor                                                                                                      
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)                                                                                           
(**) NVIDIA(0): Option "TwinView" "1"                                                                                                            
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"                                               
(**) NVIDIA(0): Enabling RENDER acceleration                                                                                                     
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is                                                                    
(II) NVIDIA(0):     enabled.                                                                                                                     
(II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:1:0:0 (GPU-0)                                                                              
(--) NVIDIA(0): Memory: 1048576 kBytes                                                                                                           
(--) NVIDIA(0): VideoBIOS: 70.18.2d.00.04                                                                                                        
(II) NVIDIA(0): Detected PCI Express Link width: 16X                                                                                             
(--) NVIDIA(0): Interlaced video modes are supported on this GPU                                                                                 
(--) NVIDIA(0): Connected display device(s) on GeForce 210 at PCI:1:0:0:                                                                         
(--) NVIDIA(0):     AOC WJ1980PI (CRT-1)                                                                                                         
(--) NVIDIA(0):     Korea Data System KL2200DW (DFP-0)                                                                                           
(--) NVIDIA(0): AOC WJ1980PI (CRT-1): 400.0 MHz maximum pixel clock                                                                              
(--) NVIDIA(0): Korea Data System KL2200DW (DFP-0): 330.0 MHz maximum pixel                                                                      
(--) NVIDIA(0):     clock                                                                                                                        
(--) NVIDIA(0): Korea Data System KL2200DW (DFP-0): Internal Dual Link TMDS                                                                      
(**) NVIDIA(0): TwinView enabled                                                                                                                 
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-1, DFP-0                                                                       
(II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0                                                                                           
(II) NVIDIA(0): Validated modes:                                                                                                                 
(II) NVIDIA(0):                                                                                                                                  
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+1280+0"                                                                   
(II) NVIDIA(0): Virtual screen size determined to be 2960 x 1050                                                                                 
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config                                                                         
(--) NVIDIA(0):     option                                                                                                                       
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.                                                                                                
(--) Depth 24 pixmap format is 32 bpp                                                                                                            
(II) do I need RAC?  No, I don't.                                                                                                                
(II) resource ranges after preInit:                                                                                                              
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
(II) NVIDIA(0): Initialized GPU GART.                                                                                                            
(II) NVIDIA(0): Setting mode                                                                                                                     
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+1280+0"                                                                   
(II) Loading extension NV-GLX                                                                                                                    
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized                                                                                  
(==) NVIDIA(0): Disabling shared memory pixmaps                                                                                                  
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture                                                                                    
(==) NVIDIA(0): Backing store disabled                                                                                                           
(==) NVIDIA(0): Silken mouse enabled                                                                                                             
(**) Option "dpms"                                                                                                                               
(**) NVIDIA(0): DPMS enabled                                                                                                                     
(II) Loading extension NV-CONTROL                                                                                                                
(II) Loading extension XINERAMA                                                                                                                  
(==) RandR enabled                                                                                                                               
(II) Initializing built-in extension Generic Event Extension                                                                                     
(II) Initializing built-in extension SHAPE                                                                                                       
(II) Initializing built-in extension MIT-SHM                                                                                                     
(II) Initializing built-in extension XInputExtension                                                                                             
(II) Initializing built-in extension XTEST                                                                                                       
(II) Initializing built-in extension BIG-REQUESTS                                                                                                
(II) Initializing built-in extension SYNC                                                                                                        
(II) Initializing built-in extension XKEYBOARD                                                                                                   
(II) Initializing built-in extension XC-MISC                                                                                                     
(II) Initializing built-in extension SECURITY                                                                                                    
(II) Initializing built-in extension XINERAMA                                                                                                    
(II) Initializing built-in extension XFIXES                                                                                                      
(II) Initializing built-in extension RENDER                                                                                                      
(II) Initializing built-in extension RANDR                                                                                                       
(II) Initializing built-in extension COMPOSITE                                                                                                   
(II) Initializing built-in extension DAMAGE                                                                                                      
(II) Initializing extension GLX                                                                                                                  
(II) LoadModule: "wizardpen"                                                                                                                     
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                       
dlopen: /usr/lib/xorg/modules/input//wizardpen_drv.so: wrong ELF class: ELFCLASS32                                                               
(EE) Failed to load /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                
(II) UnloadModule: "wizardpen"                                                                                                                   
(EE) Failed to load module "wizardpen" (loader failed, 7)                                                                                        
(EE) No input driver matching `wizardpen'                                                                                                        
(II) config/hal: Adding input device WALTOP International Corp. Slim Tablet                                                                      
(II) LoadModule: "evdev"                                                                                                                         
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so                                                                                           
(II) Module evdev: vendor="X.Org Foundation"                                                                                                     
        compiled for 1.6.4, module version = 2.2.5                                                                                               
        Module class: X.Org XInput Driver                                                                                                        
        ABI class: X.Org XInput driver, version 4.0                                                                                              
(**) WALTOP International Corp. Slim Tablet: always reports core events                                                                          
(**) WALTOP International Corp. Slim Tablet: Device: "/dev/input/event6"                                                                         
(II) WALTOP International Corp. Slim Tablet: Found 9 mouse buttons                                                                               
(II) WALTOP International Corp. Slim Tablet: Found x and y relative axes                                                                         
(II) WALTOP International Corp. Slim Tablet: Found scroll wheel(s)                                                                               
(II) WALTOP International Corp. Slim Tablet: Found x and y absolute axes                                                                         
(II) WALTOP International Corp. Slim Tablet: Found absolute touchpad                                                                             
(II) WALTOP International Corp. Slim Tablet: Found keys                                                                                          
(II) WALTOP International Corp. Slim Tablet: Configuring as touchpad                                                                             
(II) WALTOP International Corp. Slim Tablet: Configuring as keyboard                                                                             
(**) WALTOP International Corp. Slim Tablet: YAxisMapping: buttons 4 and 5                                                                       
(**) WALTOP International Corp. Slim Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200                            
(II) XINPUT: Adding extended input device "WALTOP International Corp. Slim Tablet" (type: KEYBOARD)                                              
(**) Option "xkb_rules" "evdev"                                                                                                                  
(**) Option "xkb_model" "pc105"                                                                                                                  
(**) Option "xkb_layout" "gb"                                                                                                                    
(WW) WALTOP International Corp. Slim Tablet: touchpads and touchscreens ignore relative axes.                                                    
(**) WALTOP International Corp. Slim Tablet: (accel) keeping acceleration scheme 1                                                               
(**) WALTOP International Corp. Slim Tablet: (accel) filter chain progression: 2.00                                                              
(**) WALTOP International Corp. Slim Tablet: (accel) filter stage 0: 20.00 ms                                                                    
(**) WALTOP International Corp. Slim Tablet: (accel) set acceleration profile 0                                                                  
(II) WALTOP International Corp. Slim Tablet: initialized for absolute axes.                                                                      
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Cypress Sem PS2/USB Browser Combo Mouse
(**) Cypress Sem PS2/USB Browser Combo Mouse: always reports core events
(**) Cypress Sem PS2/USB Browser Combo Mouse: Device: "/dev/input/event4"
(II) Cypress Sem PS2/USB Browser Combo Mouse: Found 9 mouse buttons
(II) Cypress Sem PS2/USB Browser Combo Mouse: Found x and y relative axes
(II) Cypress Sem PS2/USB Browser Combo Mouse: Found scroll wheel(s)
(II) Cypress Sem PS2/USB Browser Combo Mouse: Configuring as mouse
(**) Cypress Sem PS2/USB Browser Combo Mouse: YAxisMapping: buttons 4 and 5
(**) Cypress Sem PS2/USB Browser Combo Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Cypress Sem PS2/USB Browser Combo Mouse" (type: MOUSE)
(**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) keeping acceleration scheme 1
(**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) filter chain progression: 2.00
(**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) filter stage 0: 20.00 ms
(**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) set acceleration profile 0
(II) Cypress Sem PS2/USB Browser Combo Mouse: initialized for relative axes.
(WW) WALTOP International Corp. Slim Tablet: unable to handle keycode 331

```

---

### Post by Favux on 2009-12-09
Hi Michelle,

The Xorg.0.log shows thats what's happening:
```
(II) LoadModule: "wizardpen"                                                                                                                     
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                       
dlopen: /usr/lib/xorg/modules/input//wizardpen_drv.so: wrong ELF class: ELFCLASS32                                                               
(EE) Failed to load /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                
(II) UnloadModule: "wizardpen"                                                                                                                   
(EE) Failed to load module "wizardpen" (loader failed, 7)                                                                                        
(EE) No input driver matching `wizardpen'                                                                                                        
(II) config/hal: Adding input device WALTOP International Corp. Slim Tablet                                                                      
(II) LoadModule: "evdev"                                                                                                                         
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so                                                                                           
(II) Module evdev: vendor="X.Org Foundation"                                                                                                     
        compiled for 1.6.4, module version = 2.2.5                                                                                               
        Module class: X.Org XInput Driver                                                                                                        
        ABI class: X.Org XInput driver, version 4.0                                                                                              
(**) WALTOP International Corp. Slim Tablet: always reports core events                                                    
```
The .fdi is working and it tries to load wizardpen and then drops it saying:
```
dlopen: /usr/lib/xorg/modules/input//wizardpen_drv.so: wrong ELF class: ELFCLASS32
```
I don't know what ELF class is.  Then evdev picks it up since it was dropped by wizardpen ending with:
```
(WW) WALTOP International Corp. Slim Tablet: unable to handle keycode 331
```
There's probably a way to get it to "work" with wizardpen, but I don't know what it is.

So we are back to the hacked wcmUSB.c as the only way to get Waltop to work in Karmic that I know of so far.

---

### Post by msknight on 2009-12-09
The ELFCLASS32 might be down to the fact that the driver is 32 bit and I had to force it to install in a 64 bit environment.

Do you think so?

I've managed to download, patch and compile the wcmUSB.c - but I'm not sure which files I need to replace/rename.

---

### Post by msknight on 2009-12-09
What do you make of this one?

```
michelle@michelle:/var/log$ cat Xorg.0.log                 

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux michelle 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=6849e173-672c-4b8f-afff-982fb5461392 ro quiet splash
Build Date: 26 October 2009  05:19:56PM                                                                                       
xorg-server 2:1.6.4-2ubuntu4 (buildd@)                                                                                        
        Before reporting problems, check http://wiki.x.org                                                                    
        to make sure that you have the latest version.                                                                        
Markers: (--) probed, (**) from config file, (==) default setting,                                                            
        (++) from command line, (!!) notice, (II) informational,                                                              
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.                                                         
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  9 22:02:13 2009                                                          
(==) Using config file: "/etc/X11/xorg.conf"                                                                                  
(==) ServerLayout "Layout0"                                                                                                   
(**) |-->Screen "Screen0" (0)                                                                                                 
(**) |   |-->Monitor "Monitor0"                                                                                               
(**) |   |-->Device "Device0"                                                                                                 
(**) |-->Input Device "Keyboard0"                                                                                             
(**) |-->Input Device "Mouse0"                                                                                                
(**) |-->Input Device "WizardPen Tablet"                                                                                      
(**) Option "Xinerama" "0"                                                                                                    
(==) Automatically adding devices                                                                                             
(==) Automatically enabling devices                                                                                           
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.                                                            
        Entry deleted from font path.                                                                                         
(==) FontPath set to:                                                                                                         
        /usr/share/fonts/X11/misc,                                                                                            
        /usr/share/fonts/X11/100dpi/:unscaled,                                                                                
        /usr/share/fonts/X11/75dpi/:unscaled,                                                                                 
        /usr/share/fonts/X11/Type1,                                                                                           
        /usr/share/fonts/X11/100dpi,                                                                                          
        /usr/share/fonts/X11/75dpi,                                                                                           
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,                                                                     
        built-ins                                                                                                             
(==) ModulePath set to "/usr/lib/xorg/modules"                                                                                
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.                                                  
(WW) Disabling Keyboard0                                                                                                                         
(WW) Disabling Mouse0                                                                                                                            
(II) Loader magic: 0xb40                                                                                                                         
(II) Module ABI versions:                                                                                                                        
        X.Org ANSI C Emulation: 0.4                                                                                                              
        X.Org Video Driver: 5.0                                                                                                                  
        X.Org XInput driver : 4.0                                                                                                                
        X.Org Server Extension : 2.0                                                                                                             
(II) Loader running on linux                                                                                                                     
(++) using VT number 7                                                                                                                           
                                                                                                                                                 
(--) PCI:*(0:1:0:0) 10de:0a65:1458:34d5 nVidia Corporation GT200 [GeForce 210] rev 162, Mem @ 0xfb000000/16777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288                                                                                      
(II) Open ACPI successful (/var/run/acpid.socket)                                                                                                
(II) System resource ranges:                                                                                                                     
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.                                                 
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.                                                    
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.                                                    
(II) "record" will be loaded by default.                                                                                                         
(II) "dri" will be loaded by default.                                                                                                            
(II) "dri2" will be loaded by default.                                                                                                           
(II) LoadModule: "dbe"                                                                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so                                                                                         
(II) Module dbe: vendor="X.Org Foundation"                                                                                                       
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        Module class: X.Org Server Extension                                                                                                     
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension DOUBLE-BUFFER                                                                                                             
(II) LoadModule: "extmod"                                                                                                                        
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so                                                                                      
(II) Module extmod: vendor="X.Org Foundation"                                                                                                    
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        Module class: X.Org Server Extension                                                                                                     
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension MIT-SCREEN-SAVER                                                                                                          
(II) Loading extension XFree86-VidModeExtension                                                                                                  
(II) Loading extension XFree86-DGA                                                                                                               
(II) Loading extension DPMS                                                                                                                      
(II) Loading extension XVideo                                                                                                                    
(II) Loading extension XVideo-MotionCompensation                                                                                                 
(II) Loading extension X-Resource                                                                                                                
(II) LoadModule: "type1"                                                                                                                         
(WW) Warning, couldn't open module type1                                                                                                         
(II) UnloadModule: "type1"                                                                                                                       
(EE) Failed to load module "type1" (module does not exist, 0)                                                                                    
(II) LoadModule: "freetype"                                                                                                                      
(WW) Warning, couldn't open module freetype                                                                                                      
(II) UnloadModule: "freetype"                                                                                                                    
(EE) Failed to load module "freetype" (module does not exist, 0)                                                                                 
(II) LoadModule: "glx"                                                                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so                                                                                         
(II) Module glx: vendor="NVIDIA Corporation"                                                                                                     
        compiled for 4.0.2, module version = 1.0.0                                                                                               
        Module class: X.Org Server Extension                                                                                                     
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009                                                                                  
(II) Loading extension GLX                                                                                                                       
(II) LoadModule: "record"                                                                                                                        
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so                                                                                      
(II) Module record: vendor="X.Org Foundation"                                                                                                    
        compiled for 1.6.4, module version = 1.13.0                                                                                              
        Module class: X.Org Server Extension                                                                                                     
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension RECORD                                                                                                                    
(II) LoadModule: "dri"                                                                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so                                                                                         
(II) Module dri: vendor="X.Org Foundation"                                                                                                       
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension XFree86-DRI                                                                                                               
(II) LoadModule: "dri2"                                                                                                                          
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so                                                                                        
(II) Module dri2: vendor="X.Org Foundation"                                                                                                      
        compiled for 1.6.4, module version = 1.1.0                                                                                               
        ABI class: X.Org Server Extension, version 2.0                                                                                           
(II) Loading extension DRI2                                                                                                                      
(II) LoadModule: "nvidia"                                                                                                                        
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so                                                                                        
(II) Module nvidia: vendor="NVIDIA Corporation"                                                                                                  
        compiled for 4.0.2, module version = 1.0.0                                                                                               
        Module class: X.Org Video Driver                                                                                                         
(II) LoadModule: "wizardpen"                                                                                                                     
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                       
(EE) LoadModule: Module wizardpen does not have a wizardpenModuleData data object.                                                               
(II) UnloadModule: "wizardpen"                                                                                                                   
(II) Unloading /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                     
(EE) Failed to load module "wizardpen" (invalid module, 0)                                                                                       
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:51:02 PDT 2009                                                                           
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs                                                                                         
(II) Primary Device is: PCI 01@00:00:0                                                                                                           
(II) Loading sub module "fb"                                                                                                                     
(II) LoadModule: "fb"                                                                                                                            
(II) Loading /usr/lib/xorg/modules//libfb.so                                                                                                     
(II) Module fb: vendor="X.Org Foundation"                                                                                                        
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        ABI class: X.Org ANSI C Emulation, version 0.4                                                                                           
(II) Loading sub module "wfb"                                                                                                                    
(II) LoadModule: "wfb"                                                                                                                           
(II) Loading /usr/lib/xorg/modules//libwfb.so                                                                                                    
(II) Module wfb: vendor="X.Org Foundation"                                                                                                       
        compiled for 1.6.4, module version = 1.0.0                                                                                               
        ABI class: X.Org ANSI C Emulation, version 0.4                                                                                           
(II) Loading sub module "ramdac"                                                                                                                 
(II) LoadModule: "ramdac"                                                                                                                        
(II) Module "ramdac" already built-in                                                                                                            
(II) resource ranges after probing:                                                                                                              
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32                                                                                                
(==) NVIDIA(0): RGB weight 888                                                                                                                   
(==) NVIDIA(0): Default visual is TrueColor                                                                                                      
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)                                                                                           
(**) NVIDIA(0): Option "TwinView" "1"                                                                                                            
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"                                               
(**) NVIDIA(0): Enabling RENDER acceleration                                                                                                     
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is                                                                    
(II) NVIDIA(0):     enabled.                                                                                                                     
(II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:1:0:0 (GPU-0)                                                                              
(--) NVIDIA(0): Memory: 1048576 kBytes                                                                                                           
(--) NVIDIA(0): VideoBIOS: 70.18.2d.00.04                                                                                                        
(II) NVIDIA(0): Detected PCI Express Link width: 16X                                                                                             
(--) NVIDIA(0): Interlaced video modes are supported on this GPU                                                                                 
(--) NVIDIA(0): Connected display device(s) on GeForce 210 at PCI:1:0:0:                                                                         
(--) NVIDIA(0):     AOC WJ1980PI (CRT-1)                                                                                                         
(--) NVIDIA(0):     Korea Data System KL2200DW (DFP-0)                                                                                           
(--) NVIDIA(0): AOC WJ1980PI (CRT-1): 400.0 MHz maximum pixel clock                                                                              
(--) NVIDIA(0): Korea Data System KL2200DW (DFP-0): 330.0 MHz maximum pixel                                                                      
(--) NVIDIA(0):     clock                                                                                                                        
(--) NVIDIA(0): Korea Data System KL2200DW (DFP-0): Internal Dual Link TMDS                                                                      
(**) NVIDIA(0): TwinView enabled                                                                                                                 
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-1, DFP-0                                                                       
(II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0                                                                                           
(II) NVIDIA(0): Validated modes:                                                                                                                 
(II) NVIDIA(0):                                                                                                                                  
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+1280+0"                                                                   
(II) NVIDIA(0): Virtual screen size determined to be 2960 x 1050                                                                                 
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config                                                                         
(--) NVIDIA(0):     option                                                                                                                       
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.                                                                                                
(--) Depth 24 pixmap format is 32 bpp                                                                                                            
(II) do I need RAC?  No, I don't.                                                                                                                
(II) resource ranges after preInit:                                                                                                              
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]                                                                                      
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                                                  
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                                                  
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                                                  
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                                                      
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]                                                                                      
(II) NVIDIA(0): Initialized GPU GART.                                                                                                            
(II) NVIDIA(0): Setting mode                                                                                                                     
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+1280+0"                                                                   
(II) Loading extension NV-GLX                                                                                                                    
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized                                                                                  
(==) NVIDIA(0): Disabling shared memory pixmaps                                                                                                  
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture                                                                                    
(==) NVIDIA(0): Backing store disabled                                                                                                           
(==) NVIDIA(0): Silken mouse enabled                                                                                                             
(**) Option "dpms"                                                                                                                               
(**) NVIDIA(0): DPMS enabled                                                                                                                     
(II) Loading extension NV-CONTROL                                                                                                                
(II) Loading extension XINERAMA                                                                                                                  
(==) RandR enabled                                                                                                                               
(II) Initializing built-in extension Generic Event Extension                                                                                     
(II) Initializing built-in extension SHAPE                                                                                                       
(II) Initializing built-in extension MIT-SHM                                                                                                     
(II) Initializing built-in extension XInputExtension                                                                                             
(II) Initializing built-in extension XTEST                                                                                                       
(II) Initializing built-in extension BIG-REQUESTS                                                                                                
(II) Initializing built-in extension SYNC                                                                                                        
(II) Initializing built-in extension XKEYBOARD                                                                                                   
(II) Initializing built-in extension XC-MISC                                                                                                     
(II) Initializing built-in extension SECURITY                                                                                                    
(II) Initializing built-in extension XINERAMA                                                                                                    
(II) Initializing built-in extension XFIXES                                                                                                      
(II) Initializing built-in extension RENDER                                                                                                      
(II) Initializing built-in extension RANDR                                                                                                       
(II) Initializing built-in extension COMPOSITE                                                                                                   
(II) Initializing built-in extension DAMAGE                                                                                                      
(II) Initializing extension GLX                                                                                                                  
(II) LoadModule: "wizardpen"                                                                                                                     
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                       
(EE) LoadModule: Module wizardpen does not have a wizardpenModuleData data object.                                                               
(II) UnloadModule: "wizardpen"                                                                                                                   
(II) Unloading /usr/lib/xorg/modules/input//wizardpen_drv.so                                                                                     
(EE) Failed to load module "wizardpen" (invalid module, 0)                                                                                       
(EE) No input driver matching `wizardpen'                                                                                                        
(II) config/hal: Adding input device AT Translated Set 2 keyboard                                                                                
(II) LoadModule: "evdev"                                                                                                                         
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so                                                                                           
(II) Module evdev: vendor="X.Org Foundation"                                                                                                     
        compiled for 1.6.4, module version = 2.2.5                                                                                               
        Module class: X.Org XInput Driver                                                                                                        
        ABI class: X.Org XInput driver, version 4.0                                                                                              
(**) AT Translated Set 2 keyboard: always reports core events                                                                                    
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"                                                                                   
(II) AT Translated Set 2 keyboard: Found keys                                                                                                    
(II) AT Translated Set 2 keyboard: Configuring as keyboard                                                                                       
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)                                                        
(**) Option "xkb_rules" "evdev"                                                                                                                  
(**) Option "xkb_model" "pc105"                                                                                                                  
(**) Option "xkb_layout" "gb"                                                                                                                    
(II) config/hal: Adding input device WALTOP International Corp. Slim Tablet                                                                      
(**) WALTOP International Corp. Slim Tablet: always reports core events                                                                          
(**) WALTOP International Corp. Slim Tablet: Device: "/dev/input/event6"                                                                         
(II) WALTOP International Corp. Slim Tablet: Found 9 mouse buttons                                                                               
(II) WALTOP International Corp. Slim Tablet: Found x and y relative axes                                                                         
(II) WALTOP International Corp. Slim Tablet: Found scroll wheel(s)                                                                               
(II) WALTOP International Corp. Slim Tablet: Found x and y absolute axes                                                                         
(II) WALTOP International Corp. Slim Tablet: Found absolute touchpad                                                                             
(II) WALTOP International Corp. Slim Tablet: Found keys                                                                                          
(II) WALTOP International Corp. Slim Tablet: Configuring as touchpad                                                                             
(II) WALTOP International Corp. Slim Tablet: Configuring as keyboard                                                                             
(**) WALTOP International Corp. Slim Tablet: YAxisMapping: buttons 4 and 5                                                                       
(**) WALTOP International Corp. Slim Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200                            
(II) XINPUT: Adding extended input device "WALTOP International Corp. Slim Tablet" (type: KEYBOARD)                                              
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(WW) WALTOP International Corp. Slim Tablet: touchpads and touchscreens ignore relative axes.
(**) WALTOP International Corp. Slim Tablet: (accel) keeping acceleration scheme 1
(**) WALTOP International Corp. Slim Tablet: (accel) filter chain progression: 2.00
(**) WALTOP International Corp. Slim Tablet: (accel) filter stage 0: 20.00 ms
(**) WALTOP International Corp. Slim Tablet: (accel) set acceleration profile 0
(II) WALTOP International Corp. Slim Tablet: initialized for absolute axes.
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Cypress Sem PS2/USB Browser Combo Mouse
(**) Cypress Sem PS2/USB Browser Combo Mouse: always reports core events
(**) Cypress Sem PS2/USB Browser Combo Mouse: Device: "/dev/input/event4"
(II) Cypress Sem PS2/USB Browser Combo Mouse: Found 9 mouse buttons
(II) Cypress Sem PS2/USB Browser Combo Mouse: Found x and y relative axes
(II) Cypress Sem PS2/USB Browser Combo Mouse: Found scroll wheel(s)
(II) Cypress Sem PS2/USB Browser Combo Mouse: Configuring as mouse
(**) Cypress Sem PS2/USB Browser Combo Mouse: YAxisMapping: buttons 4 and 5
(**) Cypress Sem PS2/USB Browser Combo Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Cypress Sem PS2/USB Browser Combo Mouse" (type: MOUSE)
(**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) keeping acceleration scheme 1
(**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) filter chain progression: 2.00
(**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) filter stage 0: 20.00 ms
(**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) set acceleration profile 0
(II) Cypress Sem PS2/USB Browser Combo Mouse: initialized for relative axes.
(WW) WALTOP International Corp. Slim Tablet: unable to handle keycode 331

```

---

### Post by Favux on 2009-12-09
Hi Michelle,

> The ELFCLASS32 might be down to the fact that the driver is 32 bit and I had to force it to install in a 64 bit environment.

Ah!  You did mention that earlier, didn't you.  I forgot.  If you want to give WizardPen another go try using Dr. Kurian's [HOW TO]("http://ubuntuforums.org/showthread.php?t=1337260") to compile it.

```
I've managed to download, patch and compile the wcmUSB.c - but I'm not sure which files I need to replace/rename. 
```
Not sure what you are asking.  If you followed the HOW TO on linuxwacom compiling and installing the new wacom_drv.so and wacom.ko should be in place.  The wacom.fdi modified for Waltop is on the first page of the thread.

---

### Post by msknight on 2009-12-09
In order to achieve the above, I renamed the driver file. There is one entry half way down proclaiming failure, but a further set of entries near the bottom that seems to relate to something working.

---

### Post by Favux on 2009-12-09
Oops, posting at the same time.  Go over my post above first.

---

### Post by msknight on 2009-12-09
It also shows up again in The Gimp as, "WALTOP International Corp. Slim Tablet" but nothing responds to buttons.

Indeed, if I hold down the "upper" button on the pen, then the cursor stops responding to movement as long as it is down.

---

### Post by msknight on 2009-12-09
...but what is happening here...
```
(II) config/hal: Adding input device WALTOP International Corp. Slim Tablet                                                                      
(**) WALTOP International Corp. Slim Tablet: always reports core events                                                                          
(**) WALTOP International Corp. Slim Tablet: Device: "/dev/input/event6"                                                                         
(II) WALTOP International Corp. Slim Tablet: Found 9 mouse buttons                                                                               
(II) WALTOP International Corp. Slim Tablet: Found x and y relative axes                                                                         
(II) WALTOP International Corp. Slim Tablet: Found scroll wheel(s)                                                                               
(II) WALTOP International Corp. Slim Tablet: Found x and y absolute axes                                                                         
(II) WALTOP International Corp. Slim Tablet: Found absolute touchpad                                                                             
(II) WALTOP International Corp. Slim Tablet: Found keys                                                                                          
(II) WALTOP International Corp. Slim Tablet: Configuring as touchpad                                                                             
(II) WALTOP International Corp. Slim Tablet: Configuring as keyboard                                                                             
(**) WALTOP International Corp. Slim Tablet: YAxisMapping: buttons 4 and 5                                                                       
(**) WALTOP International Corp. Slim Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200                            
(II) XINPUT: Adding extended input device "WALTOP International Corp. Slim Tablet" (type: KEYBOARD)                                              
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(WW) WALTOP International Corp. Slim Tablet: touchpads and touchscreens ignore relative axes.
(**) WALTOP International Corp. Slim Tablet: (accel) keeping acceleration scheme 1
(**) WALTOP International Corp. Slim Tablet: (accel) filter chain progression: 2.00
(**) WALTOP International Corp. Slim Tablet: (accel) filter stage 0: 20.00 ms
(**) WALTOP International Corp. Slim Tablet: (accel) set acceleration profile 0
(II) WALTOP International Corp. Slim Tablet: initialized for absolute axes.

```

---

### Post by Favux on 2009-12-09
Hi Michelle,

It looks like the evdev driver is trying to configure it again.  Which driver file did you rename?  To what?

Anyway I think you'd be better off with a properly compiled 64-bit WizardPen driver that isn't "forced".  So check out Dr. Kurian's HOW TO.

---

### Post by msknight on 2009-12-10
Um, I took the wacom_drv.so out of prebuilt/64

renamed it wizardpen_drv.so and overwrite the one in /usr/lib/xorg/modules/input

---

### Post by msknight on 2009-12-10
By the way, I'm having no luck with Genius UK. They don't want to know. I'm trying to push them in to doing the work they need to support Linux customers, but they don't seem to care less.  They didn't even point me at the wacom driver.

---

### Post by Favux on 2009-12-10
Hi Michelle,

> I took the wacom_drv.so out of prebuilt/64 renamed it wizardpen_drv.so and overwrite the one in /usr/lib/xorg/modules/input
Interesting experiment.

> I'm having no luck with Genius UK. They don't want to know. I'm trying to push them in to doing the work they need to support Linux customers, but they don't seem to care less. They didn't even point me at the wacom driver.
Fascinating business model they have.  Provide no customer support for linux.  A chicken and the egg quandary.  They won't have many linux customers if the don't provide linux support.  But they don't have many linux customers so why provide linux support?

---

### Post by msknight on 2009-12-11
Well, I did get this response back from them, after forwarding them some reasons that they need to consider Linux...
> Thank you for your suggestion and feedback.
I can understand your point.
Though we won't create Linux driver for G-Pen F610, I'll forward your mail 
to our PM & RD team and hope that they can consider your suggestion to 
create Linux driver for future products.

...and I'm completely at a loss now with the driver issue for the F610.

Help!

---

