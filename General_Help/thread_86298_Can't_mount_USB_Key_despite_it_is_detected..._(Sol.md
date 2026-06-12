---
title: "Can't mount USB Key despite it is detected... (Solved)"
date: 2005-11-04
forum: General Help
---

### Post by TomG on 2005-11-04
Hi

I cannot mount and access my USB key but it seems detected. 
The most curious is that I was able to access it when I was on Ubuntu ! I just switch to KDE (without reinstalling !) and under KDE, nothing...  :confused: 

I get :

[I]$ lsusb -v
Bus 002 Device 004: ID 05dc:a400 Lexar Media, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x05dc Lexar Media, Inc.
  idProduct          0xa400
  bcdDevice           30.00
  iManufacturer           1
  iProduct                2
  iSerial                 3
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
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             255
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted[/I]

After a plug of key, dmesg gives :

[I][4296403.463000] usb 2-1.2: new low speed USB device using ohci_hcd and address 5
[4296403.575000] input: USB HID v1.10 Joystick [Microsoft SideWinder Joystick] on usb-0000:00:02.3-1.2
[4296403.723000] usb 2-1.4: new full speed USB device using ohci_hcd and address 6
[4296403.776000] usb 2-1.4: not running at top speed; connect to a high speed hub
[4296403.825000] scsi1 : SCSI emulation for USB Mass Storage devices
[4296403.837000] usb-storage: device found at 6
[4296403.837000] usb-storage: waiting for device to settle before scanning
[4296405.677000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296405.677000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296405.815000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296405.815000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296406.235000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296406.235000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296406.423000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296406.423000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
... <several seconds>...
[4296406.423000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296408.844000]   Vendor: LEXAR     Model: JUMPDRIVE SECURE  Rev: 1000
[4296408.844000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4296408.869000] SCSI device sdb: 2030592 512-byte hdwr sectors (1040 MB)
[4296408.869000] sdb: assuming drive cache: write through
[4296408.886000] SCSI device sdb: 2030592 512-byte hdwr sectors (1040 MB)
[4296408.886000] sdb: assuming drive cache: write through
[4296408.886000]  /dev/scsi/host1/bus0/target0/lun0: p1 p2
[4296408.964000] Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
[4296408.978000] usb-storage: device scan complete
**[4296418.488000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!**    <---- problem ???
[4296424.541000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296424.541000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.[/I]

Does anyone know what happens ?
There is a few posts but situations seem different each time...
How to know on which device /dev/XXX the usb key is to try to mount it manually ?

Tx,
TomG

---

### Post by mlomker on 2005-11-04
You should be able to type **sudo fdisk -l** to get a list of available partitions.

---

### Post by TomG on 2005-11-04
You're right I forgot to check simply partitions. I got :
[I]Disque /dev/hdc: 10.2 Go, 10245537792 octets
/dev/hdc1   *           1        1190     9558643+  83  Linux
/dev/hdc2            1191        1245      441787+   5  Extended
/dev/hdc5            1191        1245      441756   82  Linux swap / Solaris
Disque /dev/sdb: 1039 Mo, 1039663104 octets
/dev/sdb1               1         101      811251    6  FAT16
/dev/sdb2             102         126      200812+  16  Hidden FAT16[/I]

Then I did :
*sudo mount /dev/sdb1 /media/PUBLIC/*
And it works ! :smile: 

I guess I will have to modify /etc/fstab as I have into it :
*/dev/sda        /media/usb0     auto    rw,user,noauto  0       0*

Thanks a lot.
Tom

---

### Post by mlomker on 2005-11-04
I'd go with **/dev/sda /media/usb0 vfat defaults,user,umask=000 0 0** unless you have other USB media devices and need to keep it generic.

---

