---
title: "ubuntu boot: udevadm stuck on recognizing an lvm2 partition."
date: 2011-04-22
forum: Hardware
---

### Post by eolonano on 2011-04-22
Hi, there!

I have installed ubuntu Karmic since 2009, and it worked fine. Recently,  I have changed  MB, and ubuntu kept to work fine. 

My current configuration is: intel q8400 quad core Duo, and a MB Asus p5q deluxe with a raid controller (fakeraid) intel ich10r.

Two days ago, I have installed on a raid0 (configured in bios, two sata3 disk of 500gb each one) fedora 14. 
Fedora create an LVM2 logical partition, and the system boots clean.

My intention is to boot using ubuntu Karmic (that has a dedicated HDD, plugged in the ich10r controller): when I try it, grub start regularly, but ubuntu stop loading when udevadm try to access other disks: I receive a message like this: 

```
udevadm settle - timeout of 180 seconds reached, the event queue contains: 
/sys/devices/pc/0000:00/0000:00:1f.2/.../target1:0:1/1:0:1:0/block/sdc (1967)  
```

the message above loops many times, for /block/sdc and /block/sdb either, and ubuntu doesn't start.

If I try booting ubuntu with fedora lvm2 unplugged, system starts well.   

I have tried to connect lvm2 after booting, and ubuntu sees two distinct drives; gparted instead sees the lvm2 volume. even though it can't modify the partition lvm2.
I have also tried to run grub-update (after grub-mkdevicemap) but the partition doen't semm to exist. 

Here a scan with udevadm: 
```

udevadm test /block/sdb
run_command: calling: test
udevadm_test: version 147
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/lib/udev/rules.d/40-gnupg.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-gnupg2.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-hplip.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ia64.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-infiniband.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-isdn.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-kino.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libgphoto2-2.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libpisock9.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libsane.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-pilot-links.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ppc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-zaptel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-firmware.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-udev-default.rules' as rules file
parse_file: reading '/lib/udev/rules.d/56-hpmud_support.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-cdrom_id.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-v4l.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-gnome-bluetooth-rfkill.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-mobile-action.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-option-modem-modeswitch.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/64-device-mapper.rules' as rules file
parse_file: reading '/lib/udev/rules.d/65-dmsetup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-acl.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-hid2hci.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-net-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-tty-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-ericsson-mbm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-zte-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-sound-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/79-fstab_import.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-drivers.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-dmraid.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-regulatory.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_1000.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_1005_series.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_1018.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_1020.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_p1005.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_p1006.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_p1007.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_p1008.rules' as rules file
parse_file: reading '/etc/udev/rules.d/86-hpmud-hp_laserjet_p1505.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-hal.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-pulseaudio.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-disks.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keymap.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-kpartx.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-udev-late.rules' as rules file
parse_file: reading '/lib/udev/rules.d/97-bluetooth.rules' as rules file
parse_file: reading '/etc/udev/rules.d/99-btnx.rules' as rules file
udev_rules_new: rules use 140472 bytes tokens (11706 * 12 bytes), 26194 bytes buffer
udev_rules_new: temporary index used 42160 bytes (2108 * 20 bytes)
udev_device_new_from_syspath: device 0x7fad0165a9f0 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb'
udev_device_new_from_syspath: device 0x7fad0165ae20 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb'
udev_device_read_db: device 0x7fad0165ae20 filled with db file data
udev_device_new_from_syspath: device 0x7fad0164ec40 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0'
udev_device_new_from_syspath: device 0x7fad0164fa90 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0'
udev_device_new_from_syspath: device 0x7fad0164fda0 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11'
udev_device_new_from_syspath: device 0x7fad01650090 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0'
udev_device_new_from_syspath: device 0x7fad01650380 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3'
udev_device_new_from_syspath: device 0x7fad01650670 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-1'
udev_device_new_from_syspath: device 0x7fad01650960 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2'
udev_device_new_from_syspath: device 0x7fad01650c40 has devpath '/devices/pci0000:00/0000:00:1d.7'
udev_device_new_from_syspath: device 0x7fad01650ef0 has devpath '/devices/pci0000:00'
udev_rules_apply_to_event: LINK 'block/8:16' /lib/udev/rules.d/50-udev-default.rules:3
udev_rules_apply_to_event: GROUP 6 /lib/udev/rules.d/50-udev-default.rules:73
udev_rules_apply_to_event: IMPORT 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb' /lib/udev/rules.d/60-persistent-storage.rules:31
util_run_program: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb' started
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR=Generic'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR_ENC=Generic\x20'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR_ID=05e3'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL=STORAGE_DEVICE'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL_ENC=STORAGE\x20DEVICE\x20\x20'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL_ID=0716'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_REVISION=9744'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL=Generic_STORAGE_DEVICE_000000009744-0:0'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL_SHORT=000000009744'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_TYPE=disk'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_INSTANCE=0:0'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_BUS=usb'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_INTERFACES=:080650:'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_INTERFACE_NUM=00'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_DRIVER=usb-storage'
util_run_program: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb' returned with exitcode 0
udev_rules_apply_to_event: LINK 'disk/by-id/usb-Generic_STORAGE_DEVICE_000000009744-0:0' /lib/udev/rules.d/60-persistent-storage.rules:39
udev_rules_apply_to_event: IMPORT 'path_id /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb' /lib/udev/rules.d/60-persistent-storage.rules:56
util_run_program: 'path_id /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb' started
util_run_program: '/lib/udev/path_id' (stdout) 'ID_PATH=pci-0000:00:1d.7-usb-0:1.3:1.0-scsi-0:0:0:0'
util_run_program: 'path_id /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb' returned with exitcode 0
udev_rules_apply_to_event: LINK 'disk/by-path/pci-0000:00:1d.7-usb-0:1.3:1.0-scsi-0:0:0:0' /lib/udev/rules.d/60-persistent-storage.rules:57
udev_rules_apply_to_event: IMPORT '/sbin/blkid -o udev -p /dev/sdb' /lib/udev/rules.d/60-persistent-storage.rules:69
util_run_program: '/sbin/blkid -o udev -p /dev/sdb' started
util_run_program: '/sbin/blkid -o udev -p /dev/sdb' returned with exitcode 2
udev_rules_apply_to_event: IMPORT 'edd_id --export /dev/sdb' /lib/udev/rules.d/61-persistent-storage-edd.rules:8
util_run_program: 'edd_id --export /dev/sdb' started
util_run_program: '/lib/udev/edd_id' (stderr) 'no kernel EDD support'
util_run_program: 'edd_id --export /dev/sdb' returned with exitcode 2
udev_rules_apply_to_event: RUN '/lib/udev/hdparm' /lib/udev/rules.d/85-hdparm.rules:2
udev_rules_apply_to_event: RUN 'socket:@/org/freedesktop/hal/udev_event' /lib/udev/rules.d/90-hal.rules:2
udev_rules_apply_to_event: IMPORT 'devkit-disks-part-id /dev/sdb' /lib/udev/rules.d/95-devkit-disks.rules:26
util_run_program: 'devkit-disks-part-id /dev/sdb' started
util_run_program: '/lib/udev/devkit-disks-part-id' (stdout) 'DKD_MEDIA_AVAILABLE=0'
util_run_program: '/lib/udev/devkit-disks-part-id' (stderr) 'Error opening /dev/sdb: Permission denied'
util_run_program: 'devkit-disks-part-id /dev/sdb' returned with exitcode 0
udev_rules_apply_to_event: RUN '/sbin/modprobe -Qba dm-multipath' /lib/udev/rules.d/95-kpartx.rules:10
udev_event_execute_rules: no node name set, will use kernel supplied name 'sdb'
udev_device_update_db: unable to create db file '/dev/.udev/db/block:sdb': Permission denied
udev_node_add: creating device node '/dev/sdb', devnum=8:16, mode=0660, uid=0, gid=6
udev_node_mknod: preserve file '/dev/sdb', because it has correct dev_t
node_symlink: preserve already existing symlink '/dev/block/8:16' to '../sdb'
link_find_prioritized: found '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb' claiming '/dev/.udev/links/disk\x2fby-id\x2fusb-Generic_STORAGE_DEVICE_000000009744-0:0'
link_update: creating link '/dev/disk/by-id/usb-Generic_STORAGE_DEVICE_000000009744-0:0' to '/dev/sdb'
node_symlink: preserve already existing symlink '/dev/disk/by-id/usb-Generic_STORAGE_DEVICE_000000009744-0:0' to '../../sdb'
link_find_prioritized: found '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb' claiming '/dev/.udev/links/disk\x2fby-path\x2fpci-0000:00:1d.7-usb-0:1.3:1.0-scsi-0:0:0:0'
link_update: creating link '/dev/disk/by-path/pci-0000:00:1d.7-usb-0:1.3:1.0-scsi-0:0:0:0' to '/dev/sdb'
node_symlink: preserve already existing symlink '/dev/disk/by-path/pci-0000:00:1d.7-usb-0:1.3:1.0-scsi-0:0:0:0' to '../../sdb'
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/host11/target11:0:0/11:0:0:0/block/sdb
udevadm_test: MAJOR=8
udevadm_test: MINOR=16
udevadm_test: DEVNAME=/dev/sdb
udevadm_test: DEVTYPE=disk
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=block
udevadm_test: DEVLINKS=/dev/block/8:16 /dev/disk/by-id/usb-Generic_STORAGE_DEVICE_000000009744-0:0 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:1.3:1.0-scsi-0:0:0:0
udevadm_test: ID_VENDOR=Generic
udevadm_test: ID_VENDOR_ENC=Generic\x20
udevadm_test: ID_VENDOR_ID=05e3
udevadm_test: ID_MODEL=STORAGE_DEVICE
udevadm_test: ID_MODEL_ENC=STORAGE\x20DEVICE\x20\x20
udevadm_test: ID_MODEL_ID=0716
udevadm_test: ID_REVISION=9744
udevadm_test: ID_SERIAL=Generic_STORAGE_DEVICE_000000009744-0:0
udevadm_test: ID_SERIAL_SHORT=000000009744
udevadm_test: ID_TYPE=disk
udevadm_test: ID_INSTANCE=0:0
udevadm_test: ID_BUS=usb
udevadm_test: ID_USB_INTERFACES=:080650:
udevadm_test: ID_USB_INTERFACE_NUM=00
udevadm_test: ID_USB_DRIVER=usb-storage
udevadm_test: ID_PATH=pci-0000:00:1d.7-usb-0:1.3:1.0-scsi-0:0:0:0
udevadm_test: DKD_MEDIA_AVAILABLE=0
udevadm_test: DKD_PRESENTATION_NOPOLICY=0
udevadm_test: run: '/lib/udev/hdparm'
udevadm_test: run: 'socket:@/org/freedesktop/hal/udev_event'
udevadm_test: run: '/sbin/modprobe -Qba dm-multipath'


```

Any ideas???

---

