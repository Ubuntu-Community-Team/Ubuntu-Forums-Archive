---
title: "Lenovo USB CD/DVD writer, blank DVD not recognized"
date: 2010-08-13
forum: Hardware
---

### Post by Rifester on 2010-08-13
I have a Lenovo CD/DVD USB Drive (with Lenovo S10 Netbook), I have not used it since upgrading to the latest LTS version. I am trying to write a 1G ISO to DVD, when I install the drive with a blank dvd it no longer shows up in places... Here is terminal output:


mark@Rife-Netbook:~$ lshal | grep dvd
storage.cdrom.dvd = true (bool)
storage.cdrom.dvdplusr = true (bool)
storage.cdrom.dvdplusrdl = true (bool)
storage.cdrom.dvdplusrw = true (bool)
storage.cdrom.dvdplusrwdl = false (bool)
storage.cdrom.dvdr = true (bool)
storage.cdrom.dvdram = true (bool)
storage.cdrom.dvdrdl = true (bool)
storage.cdrom.dvdrw = true (bool)
storage.cdrom.hddvd = false (bool)
storage.cdrom.hddvdr = false (bool)
storage.cdrom.hddvdrw = false (bool)
udi = '/org/freedesktop/Hal/devices/volume_empty_dvd_r'
info.udi = '/org/freedesktop/Hal/devices/volume_empty_dvd_r' (string)
volume.disc.type = 'dvd_r' (string)
mark@Rife-Netbook:~$ lshal | grep cd
udi = '/org/freedesktop/Hal/devices/volume_uuid_73e67ef2_8394_48d8_92cd_b8986acf9b4c'
info.udi = '/org/freedesktop/Hal/devices/volume_uuid_73e67ef2_8394_48d8_92cd_b8986acf9b4c' (string)
volume.uuid = '73e67ef2-8394-48d8-92cd-b8986acf9b4c' (string)
info.linux.driver = 'ehci_hcd' (string)
usb_device.device_revision_bcd = 518 (0x206) (int)
usb_device.device_revision_bcd = 51 (0x33) (int)
usb.device_revision_bcd = 51 (0x33) (int)
scsi.type = 'cdrom' (string)
info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
storage.cdrom.bd = false (bool)
storage.cdrom.bdr = false (bool)
storage.cdrom.bdre = false (bool)
storage.cdrom.cdr = true (bool)
storage.cdrom.cdrw = true (bool)
storage.cdrom.dvd = true (bool)
storage.cdrom.dvdplusr = true (bool)
storage.cdrom.dvdplusrdl = true (bool)
storage.cdrom.dvdplusrw = true (bool)
storage.cdrom.dvdplusrwdl = false (bool)
storage.cdrom.dvdr = true (bool)
storage.cdrom.dvdram = true (bool)
storage.cdrom.dvdrdl = true (bool)
storage.cdrom.dvdrw = true (bool)
storage.cdrom.hddvd = false (bool)
storage.cdrom.hddvdr = false (bool)
storage.cdrom.hddvdrw = false (bool)
storage.cdrom.mo = false (bool)
storage.cdrom.mrw = true (bool)
storage.cdrom.mrw_w = true (bool)
storage.cdrom.read_speed = 4234 (0x108a) (int)
storage.cdrom.support_media_changed = true (bool)
storage.cdrom.support_multisession = true (bool)
storage.cdrom.write_speed = 4234 (0x108a) (int)
storage.cdrom.write_speeds = {'4234', '3528', '2822', '1764'} (string list)
storage.drive_type = 'cdrom' (string)
volume.disc.type = 'cd_rom' (string)
usb_device.device_revision_bcd = 13719 (0x3597) (int)
usb.device_revision_bcd = 13719 (0x3597) (int)
usb.device_revision_bcd = 13719 (0x3597) (int)
usb.device_revision_bcd = 518 (0x206) (int)
info.linux.driver = 'uhci_hcd' (string)
usb_device.device_revision_bcd = 518 (0x206) (int)
usb.device_revision_bcd = 518 (0x206) (int)
info.linux.driver = 'uhci_hcd' (string)
usb_device.device_revision_bcd = 518 (0x206) (int)
usb.device_revision_bcd = 518 (0x206) (int)
info.linux.driver = 'uhci_hcd' (string)
usb_device.device_revision_bcd = 518 (0x206) (int)
usb.device_revision_bcd = 518 (0x206) (int)
info.linux.driver = 'uhci_hcd' (string)
usb_device.device_revision_bcd = 518 (0x206) (int)
usb.device_revision_bcd = 518 (0x206) (int)

Brasero won't recognize the blank dvd drive either...  I have verified the drive still works with video dvd and live cd, spent all evening on google and searching forums for answers. Please help if you can!

---

### Post by earthpigg on 2010-08-13
i had this problem before.

it's a brasero problem. 

i think the eventual solution for me was to use some KDE burning app with my external usb cd/dvd burner. let me dig around.

---

### Post by earthpigg on 2010-08-13
yup, ***k3b*** was the first burning app i came across that was smart enough to check USB ports for cd/dvd burners. there may be others, but that was the first one i found that fulfilled my needs and was easy to use, so i stuck with it.

burning 10.04's .iso to a cd on my external USB cd/dvd burner as we speak.

---

### Post by Rifester on 2010-08-14
K3B recognized my USB drive fine with a blank DVD in it.  Thank you so much!

---

