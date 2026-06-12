---
title: "DVD Drive Incorrectly Recognized"
date: 2009-05-28
forum: Hardware
---

### Post by thebombquam on 2009-05-28
I recently installed Ubuntu 9.04 and have run into an issue with my DVD drives.  I am using two drives, one DVD-ROM and one DVD-RW.  The DVD-ROM works perfectly.  The DVD-RW (the slave drive) can only read CDs.  It is unable to mount DVDs at all.  Any help/advice is appreciated.

Here is some info:
```
sudo lshw -C disk
  *-cdrom:0
       description: DVD reader
       product: DVD-ROM DDU1613
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 9YS1
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: SCSI CD-ROM
       physical id: 1
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio
       configuration: status=nodisc

``````
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:1f.2-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
#  (pci-0000:00:1f.2-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:1:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
```Thanks in advance.

---

### Post by Steelmourne on 2009-05-28
Try connecting both drives via SATA. Otherwise check the jumpers on the slave dvd drive. One drive should be master, the other slave.

---

### Post by thebombquam on 2009-06-01
I should have mentioned this in my first post, both drives worked as expected in Windows XP.  I don't believe it's a problem with the jumpers.

---

### Post by thebombquam on 2009-06-04
I've found a workaround for the problem.  For some reason, the drive works perfectly fine if I change it to the master drive (switching the jumpers too).  So for now, I'm just running both drives as masters on separate IDE connections and they are working perfectly.

---

