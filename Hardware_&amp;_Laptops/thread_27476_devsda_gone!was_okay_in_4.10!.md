---
title: "/dev/sda gone!::was okay in 4.10!"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by sadneophite on 2005-04-16
Sorry this is so long 

I have a thinkpad 600e
when I installed warthog 4.10 my usbstick was detected and I could mount it as blockdevice /dev/sdaN.

Now under the installation and after the installation (of hoary)I can no longer mount the usb-stick.

During installation of hoary I lsmod-ed and saw the modules:

```

Module                  Size  Used by
vfat                   13312  0 
fat                    41792  1 vfat
usb_storage            59200  0 
sd_mod                 20480  0 
scsi_mod              115148  2 sd_mod,usb_storage
usbserial              27240  0 
usbhid                 28864  0 
usbkbd                  6912  0 
uhci_hcd               29328  0 
usbcore               104292  7 usb_storage,usbserial,usbhid,usbkbd,uhci_hcd

```  
(I cut some out which I thought were irrelevant)

and I got this message upon unplugging and replugging the usbstick:

```

usb 1-1: USB disconnect, address 3
usb 1-1: new full speed USB device using address 4
scsi2 : SCSI emulation for USB Mass Storage devices
  Vendor: OTi       Model: Flash Disk        Rev: 2.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
sda: Unit Not Ready, sense:
Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda : READ CAPACITY failed.
sda : status=1, message=00, host=0, driver=08 
Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda: test WP failed, assume Write Enabled
sda: assuming drive cache: write through
sda: Unit Not Ready, sense:
Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda : READ CAPACITY failed.
sda : status=1, message=00, host=0, driver=08 
Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda: test WP failed, assume Write Enabled
sda: assuming drive cache: write through
sda: Unit Not Ready, sense:
Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
SCSI device sda: 1024000 512-byte hdwr sectors (524 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0: p1
 /dev/scsi/host2/bus0/target0/lun0: p1
devfs_mk_dev: could not append to parent for scsi/host2/bus0/target0/lun0/part1
kobject_register failed for sda1 (-17)
 [<c018bd27>] kobject_register+0x35/0x3d
 [<c0170b6e>] add_partition+0xfb/0x10f
 [<c0170cdb>] register_disk+0x11c/0x155
 [<c01dabcc>] add_disk+0x2d/0x3a
 [<c01dab81>] exact_match+0x0/0xa
 [<c01dab8b>] exact_lock+0x0/0x14
 [<ce97eb5c>] sd_probe+0x293/0x2f6 [sd_mod]
 [<c01d4537>] bus_match+0x2e/0x4d
 [<c01d4597>] device_attach+0x41/0x7d
 [<c01d47bb>] bus_add_device+0x3f/0x6e
 [<c01d3b84>] device_add+0x72/0xda
 [<ce8c816a>] scsi_sysfs_add_sdev+0x28/0x196 [scsi_mod]
 [<ce8c70e6>] scsi_add_lun+0x327/0x332 [scsi_mod]
 [<ce8c7220>] scsi_probe_and_add_lun+0x12f/0x1bd [scsi_mod]
 [<ce8c7843>] scsi_scan_target+0x53/0xa1 [scsi_mod]
 [<ce8c78d9>] scsi_scan_channel+0x48/0x7b [scsi_mod]
 [<ce8c7990>] scsi_scan_host_selected+0x84/0xb1 [scsi_mod]
 [<ce8c79ce>] scsi_scan_host+0x11/0x15 [scsi_mod]
 [<ce9194da>] storage_probe+0x16a/0x198 [usb_storage]
 [<ce87b03c>] usb_probe_interface+0x36/0x40 [usbcore]
 [<c01d4537>] bus_match+0x2e/0x4d
 [<c01d4597>] device_attach+0x41/0x7d
 [<c01d47bb>] bus_add_device+0x3f/0x6e
 [<c01d3b84>] device_add+0x72/0xda
 [<ce880a3a>] usb_set_configuration+0x2de/0x334 [usbcore]
 [<ce87cc25>] usb_new_device+0xb7/0x116 [usbcore]
 [<ce87d67c>] hub_port_connect_change+0x283/0x313 [usbcore]
 [<ce87d930>] hub_events+0x224/0x2da [usbcore]
 [<ce87d9e6>] hub_thread+0x0/0xe4 [usbcore]
 [<ce87da03>] hub_thread+0x1d/0xe4 [usbcore]
 [<c0117234>] autoremove_wake_function+0x0/0x3a
 [<c0105e72>] ret_from_fork+0x6/0x14
 [<ce87d9e6>] hub_thread+0x0/0xe4 [usbcore]
 [<c0117234>] autoremove_wake_function+0x0/0x3a
 [<c01041e1>] kernel_thread_helper+0x5/0xb
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
USB Mass Storage device found at 4

``` 
under 5.04 it however looked different and does not work

the contents of a rebooted ubuntu 5.04 with the usbstick inserted:

```

Module                  Size  Used by
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd

``` 
 (I cut some out which I thought were irrelevant)


no other usb relevant modules are loaded!! There are also no /dev/sdXN entries in the dev tree!
When I add the missing entries in lsmod I still have no /dev/sdXN entries in the dev tree

the dmesg looks like this after I remove and insert the usb-stick:

```

usb 1-1: new full speed USB device using uhci_hcd and address 4
usb 1-1: khubd timed out on ep0in
usb 1-1: khubd timed out on ep0out

``` 

what on earth is going on?

Thanks you for any help :)  

Do I have to downgrade to hoary?!!?

---

### Post by sadneophite on 2005-04-16
after examining the following threads:
[http://www.ubuntuforums.org/showthread.php?t=17946](http://www.ubuntuforums.org/showthread.php?t=17946)
[http://ubuntuforums.org/showthread.php?t=3101&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=3101&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=3836&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=3836&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=5938&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=5938&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=5135&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=5135&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=8805&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=8805&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=13196&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=13196&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=14409&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=14409&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=15019&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=15019&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=11352&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=11352&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=15777&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=15777&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=10455&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=10455&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=15703&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=15703&highlight=usb+problems)
especially:
[http://www.ubuntuforums.org/showthread.php?p=135077](http://www.ubuntuforums.org/showthread.php?p=135077)
but also:
[http://ubuntuforums.org/showthread.php?t=17946&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=17946&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=19069&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=19069&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=18876&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=18876&highlight=usb+problems)
[http://ubuntuforums.org/showthread.php?t=18306&highlight=usb+problems](http://ubuntuforums.org/showthread.php?t=18306&highlight=usb+problems)

I discovered very many possible solutions, I recomend that one reads all of these before making their own post.

The simplest solution was adding 
```
acpi=off pci=routeirq noapic
``` 
to the end of the grub boot options ie the kernel boot options

to test this, one has to press 'esc' when grub starts, then select the boot option, and 'e' over the boot option and then 'b' to boot the modified grub (do not go back to the main list of kernels (I made this mistake the first time).

 ```
acpi=off
``` 
worked for me, I will miss my wonderful acpi 4 fan 4 thermal zone motherboard



sorry to spam the lists.

---

### Post by Jussi Kukkonen on 2005-05-19
Thank you, sadneophite, for taking the time to write this. It saved my day.

 Just for the record: I have the same hardware except that it was my 160G external hard drive that wasn't showing up.

---

