---
title: "kworld MCE 200/201 tv tuner card"
date: 2008-06-29
forum: Hardware
---

### Post by davedumas0 on 2008-06-29
i cant get it to work with xawtv or tvtime can some one plz help
btw im not a total noob but imstill learning 




thx

---

### Post by kessaris on 2008-06-30
We'll probably need some more information than that.

I suggest.. install hwinfo from the package manager and run it in the terminal.

It'll give you a bunch of output you can use to determine the situation of the hardware.

You can run

hwinfo > hardware.txt

and it'll create a text file with all your hardware info.  From there you have to search for any reference to *video* and see what's going on.

As a bare minimum you can post the output here and someone can help you trouble shoot your problem!

I suggest however, try to go through it and take out only the relevant sections that seem to pertain to video and not stuff like keyboard drivers and hard drives.

---

### Post by davedumas0 on 2008-06-30
here it is 

41: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux_0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0f.0/0000:02:0a.0/video4linux/video0'
  info.parent = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  info.product = 'UNKNOWN/GENERIC'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux_0'
  linux.hotplug_type = 2 (0x2)
  video4linux.device = '/dev/video0'
  linux.subsystem = 'video4linux'
  video4linux.version = '1'
  info.category = 'video4linux'
  access_control.file = '/dev/video0'
  info.capabilities = { 'video4linux', 'video4linux.video_capture', 'access_control' }
  linux.device_file = '/dev/video0'
  access_control.type = 'video4linux'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }

  42: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux'
42: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0f.0/0000:02:0a.0/video4linux/vbi0'
  info.parent = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  info.product = 'UNKNOWN/GENERIC'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux'
  linux.hotplug_type = 2 (0x2)
  video4linux.device = '/dev/vbi0'
  linux.subsystem = 'video4linux'
  video4linux.version = '1'
  info.category = 'video4linux'
  access_control.file = '/dev/vbi0'
  info.capabilities = { 'video4linux', 'video4linux.video_capture', 'access_control' }
  linux.device_file = '/dev/vbi0'
  access_control.type = 'video4linux'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
72: udi = '/org/freedesktop/Hal/devices/pci_14f1_8802'
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Conexant'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0f.0/0000:02:0a.2'
  info.subsystem = 'pci'
  info.vendor = 'Conexant'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_370'
  pci.product = 'CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]'
  info.product = 'CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0f.0/0000:02:0a.2'
  pci.subsys_vendor = 'KWorld Computer Co. Ltd.'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8802'
  pci.product_id = 34818 (0x8802)
  linux.hotplug_type = 2 (0x2)
  pci.vendor_id = 5361 (0x14f1)
  linux.subsystem = 'pci'
  pci.subsys_product_id = 2114 (0x842)
  pci.subsys_vendor_id = 6110 (0x17de)
  pci.device_class = 4 (0x4)
  pci.device_subclass = 128 (0x80)

  73: udi = '/org/freedesktop/Hal/devices/pci_14f1_8801'
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Conexant'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0f.0/0000:02:0a.1'
  info.subsystem = 'pci'
  info.vendor = 'Conexant'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_370'
  pci.product = 'CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]'
  info.product = 'CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0f.0/0000:02:0a.1'
  pci.subsys_vendor = 'KWorld Computer Co. Ltd.'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8801'
  pci.product_id = 34817 (0x8801)
  linux.hotplug_type = 2 (0x2)
  pci.vendor_id = 5361 (0x14f1)
  linux.subsystem = 'pci'
  info.linux.driver = 'cx88_audio'
  pci.subsys_product_id = 2114 (0x842)
  pci.subsys_vendor_id = 6110 (0x17de)
  pci.device_class = 4 (0x4)
  pci.device_subclass = 128 (0x80)
pci.product = 'CX23880/1/2/3 PCI Video and Audio Decoder'
  info.product = 'CX23880/1/2/3 PCI Video and Audio Decoder'

---

### Post by davedumas0 on 2008-07-04
anybody???

---

### Post by davedumas0 on 2008-07-31
hello?

---

