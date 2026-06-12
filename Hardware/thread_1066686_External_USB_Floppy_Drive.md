---
title: "External USB Floppy Drive"
date: 2009-02-11
forum: Hardware
---

### Post by fugazi32 on 2009-02-11
I can't seem to mount any disks in my external USB floppy drive, all I get is:

[I]Unable to mount "External Floppy Drive":

Given device "/org/freedesktop/Hal/devices/storage_serial_TEAC_TEAC_FD_05PUW" is not a volume or drive[/I]

I'm using some old (unformatted?) Atari ST disks, though I think they're DOS formatted too....i'll have a look for some of my old Windows floppies. Though I thought it could read any format of 3 1/2 inch floppy.

Any help would be much appreciated!
:P

---

### Post by martinbaselier on 2009-02-11
How do you mount your drives? With automount?
What happens when you use mount in a terminal?

---

### Post by fugazi32 on 2009-02-11
> **martinbaselier said:**
> How do you mount your drives? With automount?
What happens when you use mount in a terminal?

I haven't used the terminal yet, i've used it like a plug & play device and clicked on the icon when it appeared on the desktop......would you be able to run me through the commands?

---

### Post by martinbaselier on 2009-02-11
Very short instructions:

The floppies are unformatted:
sudo apt-get install gparted.
sudo gparted
There you should be able to select your fdd, create a partition table on it and format it. The graphical interface is pretty straightforward.

Alternatively you could use sudo cfdisk /dev/fd to create a partition
and sudo mkfs -t vfat /dev/fdx (replace x with the correct number; fdisk should show you the numer; see below) to create a filesystem on the disk and format it. 

sudo fdisk -l will show you the avaialable (mountable) drives.

**Mounting from the command line:**
mkdir fdd : will create a fdd directory in you home folder
sudo mount -t filesystem /dev/fdx fdd
will mount the floppy drive x (replace x with a number) in the folder fd.
I don't wich filesystem to use though. For dos floppies it wout be vfat.

Just ask if anything's not clear.

---

### Post by 00b00nt00 on 2009-02-11
One thing to bear in mind with disks formatted for the Atari ST is that they are double-sided, double-density disks meaning that you'll get about half the capacity of a standard high density disk (720KB vs 1.44MB).

Also, don't expect Ubuntu to read all of the disks because although the ST could format disks to the MSDOS 3.3 standard, many disks were formatted to an extended capacity (I regularly formatted disks to 820KB with no problems).

---

### Post by fugazi32 on 2009-02-11
> **martinbaselier said:**
> 
sudo fdisk -l will show you the avaialable (mountable) drives.


Hmmm, fdisk doesn't even recognize it, I can see my main & external HDs, but no floppy...even though there's an icon on the desktop. I installed GParted and it doesn't show any floppy devices in there either.
...I installed KFloppy @ someone else's recommendation, it's a GUI frontend for formatting floppies and that says I don't have a floppy device set up.

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19282   154882633+  83  Linux
/dev/sda2           19283       19457     1405687+   5  Extended
/dev/sda5           19283       19457     1405656   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a652027

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488386552+   b  W95 FAT32

```

> **00b00nt00 said:**
> One thing to bear in mind with disks formatted for the Atari ST is that they are double-sided, double-density disks meaning that you'll get about half the capacity of a standard high density disk (720KB vs 1.44MB).

Also, don't expect Ubuntu to read all of the disks because although the ST could format disks to the MSDOS 3.3 standard, many disks were formatted to an extended capacity (I regularly formatted disks to 820KB with no problems).

I don't mind having a smaller disk size, since i'm only really wanting to copy a small program to floppy to run on my Atari ST.

---

### Post by martinbaselier on 2009-02-11
I wonder what's not working there.
lshal | less
will show you the hal(hardware abstraction layer) devices. I'm quite curious what the details are from /org/freedesktop/Hal/devices/storage_serial_TEAC_TEAC_FD_05PUW (that is your floppy drive)
also lsusb will show you your usb-devices
lsusb -v -d [ID]
will show you the details of that particular usb device, you can copy the ID from the result of the first lsusb. Could you post that data here?

---

### Post by fugazi32 on 2009-02-11
> **martinbaselier said:**
> I wonder what's not working there.
lshal | less
will show you the hal(hardware abstraction layer) devices. I'm quite curious what the details are from /org/freedesktop/Hal/devices/storage_serial_TEAC_TEAC_FD_05PUW (that is your floppy drive)
also lsusb will show you your usb-devices
lsusb -v -d [ID]
will show you the details of that particular usb device, you can copy the ID from the result of the first lsusb. Could you post that data here?

```

lindsell@FUCKUP:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0644:0000 TEAC Corp. Floppy
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0d49:7410 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lindsell@FUCKUP:~$ lsusb -v -d 0644:0000

Bus 003 Device 003: ID 0644:0000 TEAC Corp. Floppy
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0644 TEAC Corp.
  idProduct          0x0000 Floppy
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      4 Floppy (UFI)
      bInterfaceProtocol      0 Control/Bulk/Interrupt
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
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              32
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```

Do you want me to post all of *lshal | less* or just find the floppy part? I'm scanning it now...quite a long list. Is there a command so I can dump the list to a TXT file to copy it easily?

---

### Post by fugazi32 on 2009-02-11
**Bump!**
:lolflag:

---

### Post by martinbaselier on 2009-02-12
lshal > hal.txt will output to txt; only the part about the floppy is necessary.
FYI: usually if you don't get permission, you'll need root access; putting sudo before a command will give you this.

EDIT: did a bit of searching on your usb-ID, apparently a usb floppy will be  mounted on the sd,, range, unlike an internal floppy drive. 
You have disks in the sda and the sdc range. Will gparted not show you disks in other ranges ?

---

### Post by fugazi32 on 2009-02-12
Might just be my eyes, but I can't seem to find the floppy...I did a search but to no avail...

```


Dumping 88 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.callouts.add = {'hal-acl-tool --remove-all', 'hal-storage-cleanup-all-mountpoints'} (string list)
  info.callouts.session_active = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_add = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_inactive = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_remove = {'hal-acl-tool --reconfigure'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  power_management.acpi.linux.version = '20080609'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.type = 'acpi'  (string)
  system.chassis.manufacturer = 'NEC COMPUTERS INTERNATIONAL'  (string)
  system.chassis.type = 'Desktop'  (string)
  system.firmware.release_date = '10/21/2005'  (string)
  system.firmware.vendor = 'Award Software International, Inc.'  (string)
  system.firmware.version = '1.0L'  (string)
  system.formfactor = 'desktop'  (string)
  system.hardware.primary_video.product = 25392  (0x6330)  (int)
  system.hardware.primary_video.vendor = 4153  (0x1039)  (int)
  system.hardware.product = '00000000000000000000000'  (string)
  system.hardware.serial = '049641020487'  (string)
  system.hardware.uuid = '3C4351ED-E156-DA11-8000-4E45435F4349'  (string)
  system.hardware.vendor = 'Packard Bell NEC'  (string)
  system.hardware.version = 'PB34218301'  (string)
  system.kernel.machine = 'i686'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.27-11-generic'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Celeron(R) CPU 2.93GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU0'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  access_control.file = '/dev/snd/timer'  (string)
  access_control.type = 'sound'  (string)
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
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
  access_control.file = '/dev/sequencer2'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
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
  access_control.file = '/dev/sequencer'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
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
  access_control.file = '/dev/snd/seq'  (string)
  access_control.type = 'sound'  (string)
  alsa.device_file = '/dev/snd/seq'  (string)
  alsa.type = 'sequencer'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'  (string)
  linux.device_file = '/dev/snd/seq'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button (CM)'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event3'  (string)
  input.product = 'Power Button (CM)'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button (FF)'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'Power Button (FF)'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'System Board'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.description = 'System Board'  (string)
  pnp.id = 'PNP0c01'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  info.linux.driver = 'i8042 kbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.id = 'PNP0303'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'
  info.linux.driver = 'i8042 aux'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PS/2 Port for PS/2-style Mice'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = 'PS/2 Port for PS/2-style Mice'  (string)
  pnp.id = 'PNP0f13'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0401'
  info.linux.driver = 'parport_pc'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ECP printer port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0401'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = 'ECP printer port'  (string)
  pnp.id = 'PNP0401'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
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
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.description = 'AT Real-Time Clock'  (string)
  pnp.id = 'PNP0b00'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'AT DMA Controller'  (string)
  pnp.id = 'PNP0200'  (string)

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
  info.linux.driver = 'pcspkr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  info.product = 'PC Speaker'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  input.product = 'PC Speaker'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr/input/input4/event4'  (string)

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

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.callouts.add = {'hal-probe-vmmouse'} (string list)
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'ImExPS/2 Generic Explorer Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'ImExPS/2 Generic Explorer Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input5/event5'  (string)

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
  input.device = '/dev/input/event1'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'gb'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (eisa.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/eisa.0'  (string)
  platform.id = 'eisa.0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_163c_3052'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SmartLink SmartPCI562 56K Modem'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_163c_3052'  (string)
  info.vendor = 'Smart Link Ltd.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0'  (string)
  pci.device_class = 7  (0x7)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0'  (string)
  pci.product = 'SmartLink SmartPCI562 56K Modem'  (string)
  pci.product_id = 12370  (0x3052)  (int)
  pci.subsys_product_id = 12370  (0x3052)  (int)
  pci.subsys_vendor = 'Aztech System Ltd'  (string)
  pci.subsys_vendor_id = 4653  (0x122d)  (int)
  pci.vendor = 'Smart Link Ltd.'  (string)
  pci.vendor_id = 5692  (0x163c)  (int)

udi = '/org/freedesktop/Hal/devices/pci_163c_3052_serial_platform_3'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_163c_3052'  (string)
  info.product = 'SmartLink SmartPCI562 56K Modem'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_163c_3052_serial_platform_3'  (string)
  linux.device_file = '/dev/ttyS3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/tty/ttyS3'  (string)
  serial.device = '/dev/ttyS3'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pci_163c_3052'  (string)
  serial.port = 3  (0x3)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pci_163c_3052_serial_platform_2'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_163c_3052'  (string)
  info.product = 'SmartLink SmartPCI562 56K Modem'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_163c_3052_serial_platform_2'  (string)
  linux.device_file = '/dev/ttyS2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/tty/ttyS2'  (string)
  serial.device = '/dev/ttyS2'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pci_163c_3052'  (string)
  serial.port = 2  (0x2)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pci_163c_3052_serial_platform_1'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_163c_3052'  (string)
  info.product = 'SmartLink SmartPCI562 56K Modem'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_163c_3052_serial_platform_1'  (string)
  linux.device_file = '/dev/ttyS1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/tty/ttyS1'  (string)
  serial.device = '/dev/ttyS1'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pci_163c_3052'  (string)
  serial.port = 1  (0x1)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_180'
  info.linux.driver = 'sata_sis'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'RAID bus controller 180 SATA/PATA  [SiS]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_180'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:05.0'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 133  (0x85)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:05.0'  (string)
  pci.product = 'RAID bus controller 180 SATA/PATA  [SiS]'  (string)
  pci.product_id = 384  (0x180)  (int)
  pci.subsys_product_id = 33569  (0x8321)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_180_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_180'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_180_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:05.0/host5/scsi_host/host5'  (string)
  scsi_host.host = 5  (0x5)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_180_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_180'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_180_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:05.0/host4/scsi_host/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_900'
  info.linux.driver = 'sis900'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SiS900 PCI Fast Ethernet'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_900'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0'  (string)
  pci.product = 'SiS900 PCI Fast Ethernet'  (string)
  pci.product_id = 2304  (0x900)  (int)
  pci.subsys_product_id = 33568  (0x8320)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_14_85_5b_9b_1d'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_900'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_14_85_5b_9b_1d'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/net/eth0'  (string)
  net.80203.mac_address = 88136719133  (0x14855b9b1d)  (uint64)
  net.address = '00:14:85:5b:9b:1d'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_1039_900'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_1039_7002'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'USB 2.0 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7002'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3'  (string)
  pci.product = 'USB 2.0 Controller'  (string)
  pci.product_id = 28674  (0x7002)  (int)
  pci.subsys_product_id = 33569  (0x8321)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_03_3'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7002'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_03_3'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 8  (0x8)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:03.3'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_03_3'  (string)
  info.product = 'Basics Desktop'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154'  (string)
  info.vendor = 'Maxtor'  (string)
  linux.device_file = '/dev/bus/usb/001/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 290  (0x122)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4'  (string)
  usb_device.max_power = 2  (0x2)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Basics Desktop'  (string)
  usb_device.product_id = 29712  (0x7410)  (int)
  usb_device.serial = '2HBEK154'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Maxtor'  (string)
  usb_device.vendor_id = 3401  (0xd49)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0'
  info.linux.driver = 'usb-storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154'  (string)
  info.product = 'USB Mass Storage Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4/1-4:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 290  (0x122)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 8  (0x8)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 80  (0x50)  (int)
  usb.interface.subclass = 6  (0x6)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4/1-4:1.0'  (string)
  usb.max_power = 2  (0x2)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Mass Storage Interface'  (string)
  usb.product_id = 29712  (0x7410)  (int)
  usb.serial = '2HBEK154'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Maxtor'  (string)
  usb.vendor_id = 3401  (0xd49)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4/1-4:1.0/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4/1-4:1.0/host2/scsi_host/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4/1-4:1.0/host2/target2:0:0/2:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 2  (0x2)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'Basics Desktop'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'Maxtor'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4/1-4:1.0/host2/target2:0:0/2:0:0:0/scsi_generic/sg3'  (string)
  scsi_generic.device = '/dev/sg3'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_Maxtor_Basics_Desktop_2HBEK154_0_0'
  block.device = '/dev/sdc'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 32  (0x20)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Maxtor_Basics_Desktop_2HBEK154_0_0'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0_scsi_host_scsi_device_lun0'  (string)
  info.product = 'Basics Desktop'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_Maxtor_Basics_Desktop_2HBEK154_0_0'  (string)
  info.vendor = 'Maxtor'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4/1-4:1.0/host2/target2:0:0/2:0:0:0/block/sdc'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'usb'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '0122'  (string)
  storage.hotpluggable = true  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'Basics Desktop'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/usb_device_d49_7410_2HBEK154_if0'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 500107862016  (0x7470c06000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'Maxtor_Basics_Desktop_2HBEK154-0:0'  (string)
  storage.size = 500107862016  (0x7470c06000)  (uint64)
  storage.vendor = 'Maxtor'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_ECBA_1213'
  block.device = '/dev/sdc1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 33  (0x21)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Maxtor_Basics_Desktop_2HBEK154_0_0'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_Maxtor_Basics_Desktop_2HBEK154_0_0'  (string)
  info.product = 'NATE'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_ECBA_1213'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-4/1-4:1.0/host2/target2:0:0/2:0:0:0/block/sdc/sdc1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'vfat'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = 'FAT32'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'NATE'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'dmask=', 'fmask=', 'uid=', 'flush'} (string list)
  volume.mount_point = '/media/NATE'  (string)
  volume.num_blocks = 976773105  (0x3a385ff1)  (uint64)
  volume.partition.flags = {} (string list)
  volume.partition.label = ''  (string)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.partition.type = '0x0b'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 500107829760  (0x7470bfe200)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'ECBA-1213'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_03_3_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_03_3'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_03_3_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-0:1.0'  (string)
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
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.3/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 8  (0x8)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:03.3'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_1039_7001_1'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'USB 1.1 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7001_1'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.2'  (string)
  pci.product = 'USB 1.1 Controller'  (string)
  pci.product_id = 28673  (0x7001)  (int)
  pci.subsys_product_id = 33569  (0x8321)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7001_1'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/004/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.2/usb4'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.2/usb4'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:03.2'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.2/usb4/4-0:1.0'  (string)
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
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.2/usb4/4-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:03.2'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1039_7001_0'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'USB 1.1 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7001_0'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.1'  (string)
  pci.product = 'USB 1.1 Controller'  (string)
  pci.product_id = 28673  (0x7001)  (int)
  pci.subsys_product_id = 33569  (0x8321)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7001_0'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/003/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.1/usb3'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.1/usb3'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:03.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.1/usb3/3-0:1.0'  (string)
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
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.1/usb3/3-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:03.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1039_7001'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'USB 1.1 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7001'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0'  (string)
  pci.product = 'USB 1.1 Controller'  (string)
  pci.product_id = 28673  (0x7001)  (int)
  pci.subsys_product_id = 33569  (0x8321)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7001'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/002/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:03.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb2/2-0:1.0'  (string)
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
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:03.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012'
  info.linux.driver = 'Intel ICH'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AC'97 Sound Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7'  (string)
  pci.product = 'AC'97 Sound Controller'  (string)
  pci.product_id = 28690  (0x7012)  (int)
  pci.subsys_product_id = 33567  (0x831f)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012'  (string)
  info.product = 'SiS SI7012 with ALC655 Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0'  (string)
  sound.card = 0  (0x0)  (int)
  sound.card_id = 'SiS SI7012 with ALC655'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_capture_1'
  access_control.file = '/dev/snd/pcmC0D1c'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'SiS SI7012 with ALC655'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1c'  (string)
  alsa.device_id = 'SiS SI7012 - MIC ADC'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  info.product = 'SiS SI7012 - MIC ADC ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_capture_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0/pcmC0D1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_playback_0'
  access_control.file = '/dev/snd/pcmC0D0p'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'SiS SI7012 with ALC655'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'SiS SI7012'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  info.product = 'SiS SI7012 ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_capture_0'
  access_control.file = '/dev/snd/pcmC0D0c'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'SiS SI7012 with ALC655'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'SiS SI7012'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  info.product = 'SiS SI7012 ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_oss_mixer__1'
  access_control.file = '/dev/mixer'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  info.product = 'SiS SI7012 OSS Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'SiS SI7012 with ALC655'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'SiS SI7012'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_oss_pcm_0_0'
  access_control.file = '/dev/dsp'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  info.product = 'SiS SI7012 OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'SiS SI7012 with ALC655'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'SiS SI7012'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_control__1'
  access_control.file = '/dev/snd/controlC0'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'SiS SI7012 with ALC655'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  alsa.type = 'control'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  info.product = 'SiS SI7012 with ALC655 ALSA Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_oss_pcm_0'
  access_control.file = '/dev/audio'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  info.product = 'SiS SI7012 OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'SiS SI7012 with ALC655'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'SiS SI7012'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_oss_pcm_1'
  access_control.file = '/dev/adsp'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  info.product = 'SiS SI7012 OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0_oss_pcm_1'  (string)
  linux.device_file = '/dev/adsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.7/sound/card0/adsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'SiS SI7012 with ALC655'  (string)
  oss.device = 1  (0x1)  (int)
  oss.device_file = '/dev/adsp'  (string)
  oss.device_id = 'SiS SI7012'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1039_7012_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513'
  info.linux.driver = 'pata_sis'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '5513 [IDE]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 138  (0x8a)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5'  (string)
  pci.product = '5513 [IDE]'  (string)
  pci.product_id = 21779  (0x5513)  (int)
  pci.subsys_product_id = 33569  (0x8321)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host1/scsi_host/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0'
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host1/target1:0:0/1:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 1  (0x1)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'DVDR1628P1'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'PHILIPS'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host1/target1:0:0/1:0:0:0/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_DVDR1628P1'
  access_control.file = '/dev/scd0'  (string)
  access_control.type = 'cdrom'  (string)
  block.device = '/dev/scd0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DVDR1628P1'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom', 'access_control', 'access_control'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'DVDR1628P1'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_DVDR1628P1'  (string)
  info.vendor = 'PHILIPS'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host1/target1:0:0/1:0:0:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'scsi'  (string)
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
  storage.cdrom.dvdram = false  (bool)
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
  storage.cdrom.write_speeds = {'8467', '7056', '5645', '4234', '2822', '2117'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'DVDR1628P1'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'PHILIPS'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host0/scsi_host/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host0/target0:0:0/0:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'ST3160021A'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_device_lun0'  (string)
  info.product = 'ST3160021A'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host0/target0:0:0/0:0:0:0/block/sda'  (string)
  storage.automount_enabled_hint = false  (bool)
  storage.bus = 'scsi'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '8.01'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'ST3160021A'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 160041885696  (0x25433d6000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = '1ATA_ST3160021A_5JS72R9F'  (string)
  storage.size = 160041885696  (0x25433d6000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host0/target0:0:0/0:0:0:0/block/sda/sda2'  (string)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = ''  (string)
  volume.fsusage = ''  (string)
  volume.fsversion = ''  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 2  (0x2)  (uint64)
  volume.partition.media_size = 160041885696  (0x25433d6000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.start = 158599848960  (0x24ed49a400)  (uint64)
  volume.size = 1024  (0x400)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_c1c8b775_b906_49d3_af15_6ac8814a0df1'
  block.device = '/dev/sda5'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 5  (0x5)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'  (string)
  info.product = 'Volume (swap)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_c1c8b775_b906_49d3_af15_6ac8814a0df1'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host0/target0:0:0/0:0:0:0/block/sda/sda5'  (string)
  storage.model = ''  (string)
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
  volume.num_blocks = 2811312  (0x2ae5b0)  (uint64)
  volume.partition.media_size = 160041885696  (0x25433d6000)  (uint64)
  volume.partition.number = 5  (0x5)  (int)
  volume.partition.start = 158599881216  (0x24ed4a2200)  (uint64)
  volume.size = 1439391744  (0x55cb6000)  (uint64)
  volume.uuid = 'c1c8b775-b906-49d3-af15-6ac8814a0df1'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_dd886f6f_213b_4a45_a7e2_071e1ab293c9'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3160021A_5JS72R9F'  (string)
  info.product = 'Volume (ext3)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_dd886f6f_213b_4a45_a7e2_071e1ab293c9'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.5/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext3'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'acl', 'user_xattr', 'data='} (string list)
  volume.mount_point = '/'  (string)
  volume.num_blocks = 309765267  (0x1276a493)  (uint64)
  volume.partition.flags = {'boot'} (string list)
  volume.partition.label = ''  (string)
  volume.partition.media_size = 160041885696  (0x25433d6000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.partition.type = '0x83'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 158599816704  (0x24ed492600)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'dd886f6f-213b-4a45-a7e2-071e1ab293c9'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1039_964'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SiS964 [MuTIOL Media IO]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_964'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.product = 'SiS964 [MuTIOL Media IO]'  (string)
  pci.product_id = 2404  (0x964)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_3'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SiS AGP Port (virtual PCI-to-PCI bridge)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_3'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'  (string)
  pci.product = 'SiS AGP Port (virtual PCI-to-PCI bridge)'  (string)
  pci.product_id = 3  (0x3)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_6330'
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_3'  (string)
  info.product = '661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_6330'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'  (string)
  pci.product = '661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter'  (string)
  pci.product_id = 25392  (0x6330)  (int)
  pci.subsys_product_id = 33566  (0x831e)  (int)
  pci.subsys_vendor = 'NEC Corporation'  (string)
  pci.subsys_vendor_id = 4147  (0x1033)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1039_661'
  info.linux.driver = 'agpgart-sis'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '661FX/M661FX/M661MX Host'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1039_661'  (string)
  info.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = '661FX/M661FX/M661MX Host'  (string)
  pci.product_id = 1633  (0x661)  (int)
  pci.subsys_product_id = 1633  (0x661)  (int)
  pci.subsys_vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.subsys_vendor_id = 4153  (0x1039)  (int)
  pci.vendor = 'Silicon Integrated Systems [SiS]'  (string)
  pci.vendor_id = 4153  (0x1039)  (int)

udi = '/org/freedesktop/Hal/devices/fuse'
  access_control.file = '/dev/fuse'  (string)
  access_control.type = 'camera'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'access_control'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1039_661'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/fuse'  (string)


Dumped 88 device(s) from the Global Device List.
------------------------------------------------

```

> **martinbaselier said:**
> lshal > hal.txt will output to txt; only the part about the floppy is necessary.
FYI: usually if you don't get permission, you'll need root access; putting sudo before a command will give you this.

EDIT: did a bit of searching on your usb-ID, apparently a usb floppy will be  mounted on the sd,, range, unlike an internal floppy drive. 
You have disks in the sda and the sdc range. Will gparted not show you disks in other ranges ?

Gparted shows my main internal hard disk & 500GB external hard drive, but no floppy i'm afraid :(

---

### Post by martinbaselier on 2009-02-12
It seems like a driver problem then. You got an error on a hal device when automounting, so I presumed it should be listed in hal, but apparently it isn't. Do you see any errors in dmesg, when attaching the usb.
dmesg | tail will show you the last messages in it. Just type it before and after you attach the device

---

### Post by fugazi32 on 2009-02-12
Before & after:

```

lindsell@FUCKUP:~$ dmesg | tail
[154972.536172] usb 3-2: new full speed USB device using ohci_hcd and address 4
[154972.797666] usb 3-2: configuration #1 chosen from 1 choice
[154972.800417] scsi10 : SCSI emulation for USB Mass Storage devices
[154972.801857] usb-storage: device found at 4
[154972.801868] usb-storage: waiting for device to settle before scanning
[154977.800272] usb-storage: device scan complete
[154977.822161] scsi 10:0:0:0: Direct-Access     TEAC     FD-05PUW         3000 PQ: 0 ANSI: 0 CCS
[154977.918713] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[154977.919464] sd 10:0:0:0: Attached scsi generic sg2 type 0
[158423.811147] usb 3-2: USB disconnect, address 4
lindsell@FUCKUP:~$ dmesg | tail
[158423.811147] usb 3-2: USB disconnect, address 4
[158460.816046] usb 3-2: new full speed USB device using ohci_hcd and address 5
[158461.118823] usb 3-2: configuration #1 chosen from 1 choice
[158461.144150] scsi11 : SCSI emulation for USB Mass Storage devices
[158461.150545] usb-storage: device found at 5
[158461.150558] usb-storage: waiting for device to settle before scanning
[158466.148282] usb-storage: device scan complete
[158466.176146] scsi 11:0:0:0: Direct-Access     TEAC     FD-05PUW         3000 PQ: 0 ANSI: 0 CCS
[158466.272339] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[158466.273092] sd 11:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by martinbaselier on 2009-02-12
So it is recognised and put on sdb. I presume that's done by the kernel. 
Are you sure you can't choose /dev/sdb in gparted?

EDIT: No, hal should put an extra layer on it, for you to actually be able to use the drive. So the problem seems to be, that hal won't load it. Can't really say, what's causing that and how to troubleshoot further. hmmm.

EDIT2: Have you tried mounting it from the live-cd. It should work with current linux versions, so I presume there's something wrong with your install.

---

### Post by fugazi32 on 2009-02-13
> **martinbaselier said:**
> So it is recognised and put on sdb. I presume that's done by the kernel. 
Are you sure you can't choose /dev/sdb in gparted?

EDIT: No, hal should put an extra layer on it, for you to actually be able to use the drive. So the problem seems to be, that hal won't load it. Can't really say, what's causing that and how to troubleshoot further. hmmm.

EDIT2: Have you tried mounting it from the live-cd. It should work with current linux versions, so I presume there's something wrong with your install.

I'll give it another go in gparted....and then i'll see if it works with the live CD. Cheers for the help anyways though! :)

**EDIT:** Can only see /dev/sda & /dev/sdc in *gparted*.
Just tried using a different USB port too, but getting the same problem.

---

### Post by nobody00 on 2009-09-15
I having a similar problem except that the external floppy is a Mitsumi SmartDisk FDD and generates the following when an attempt to mount or open it:

Unable to mount "External Floppy Drive":
Given device "/org/freedesktop/Hal/devices/storage_serial_MITSUMI_MITSUMI_USB_FDD_061M" is not a volume or drive

An shaded icon is generated for the floppy on the desktop and in Places, but it's not mounted.

The floppy hardware is not the problem because both the BIOS and Vista (dual-boot) properly access the drive. The OS is Xubuntu 9.04 with a 2.6.28-15-generic kernal.

lsusb lists:
Bus 006 Device 002: ID 03ee:6901 Mitsumi SmartDisk FDD

/dev/disk/by-id/MITSUMI_MITSUMI_USB_FDD_061M is linked to /dev/sdb

There is no floppy entires in /media. /dev has no fd0 or fd.

I reinstalled hal with no change in the problem.

Any help would be appreciated!

---

### Post by Shuryon on 2010-10-19
I was searching for something then I found something really helpful (thanks help.ubuntu.com). The truth is that I wasn't looking for you. >_<' But I found something.
I don't know if it can really help but for me actually worked. I'm using Ubuntu 10.04 but I guess it works like this for every GNU/Linux distro. The driver is a NEC Corp. Floppy. 
So now, the help itself:

Lookup for what is your USB Floppy (mine was /dev/sdc) with the following command:

```
sudo fdisk -l
```Now, we will create a folder in /media for your USB Floppy:

```
sudo mkdir /media/USB_Floppy_Drive
```The real deal is now. I guess you've missed up like me, 3 minutes before I've foud this (for more information, open the link at the bottom of this post).

After this, you can mount your USB Floppy by typing the command bellow. Change where it is necessary and then type:

```
sudo mount -t vfat /dev/sdb1 /media/USB_Floppy_Drive -o uid=1000,gid=100,utf8,dmask=027,fmask=137
```It was in case of FAT16/FAT32. For NTFS (you will need ntfs-3g driver, [click here]("https://help.ubuntu.com/community/MountingWindowsPartitions") for more information) , use this:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/USB_Floppy_Drive
```For unmounting, use the following command line (cause' u can't do normal unmounting through desktop):

```
sudo umount /media/USB_Floppy_Drive
```And this is what you need to do.
I'm crappy at this stuff so I don't know how to automatize this - you can say I'm more like jack of all trades, master of none.

I hope it helped and that Canonical do something for future :P

The credits:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[URL="https://help.ubuntu.com/community/Mount/USB"]https://help.ubuntu.com/community/MountingWindowsPartitions
[/URL]

---

### Post by schezel2000 on 2011-04-08
I found that all the other stuff was not needed you just need the following command to mount the external floppy. You

sudo mount -t vfat /dev/sdc /media 


your files will show up in the media file.

---

### Post by Shuryon on 2011-04-09
Yeah, you are right. For FAT types.

But if you use some Linux's distro, you will want to use the entire command. The explanation of those lines can be found at the links in 'credits'. =P

---

### Post by donut123 on 2011-08-06
Hello..I am having this same problem ..none of these solutuons are working. Can some one help me on this please?

---

### Post by edcompsci on 2011-12-03
I am also having a mounting of a new floppy drive problem, with a new teac external usb floppy drive. I just submitted it through ubuntu-bug, and just after that I was reading this and then i dewcided to look at sysinfo (get sysinfo with an apt-get install) and found that the drive is recognized as a separate scsi drive. I'm not sure where to go from that. It is currently plugged into a usb hub, but i also tried it on my laptop and on this desktop directly into the usb port on the computer. 

I wonder if this will help solve this, I am still unable to mount it.

---

