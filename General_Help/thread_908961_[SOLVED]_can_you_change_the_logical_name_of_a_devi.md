---
title: "[SOLVED] can you change the logical name of a device?"
date: 2008-09-03
forum: General Help
---

### Post by harryliddic on 2008-09-03
I have been having trouble with dvdauthor and kino because they look for **/dev/dvd** but the logical name of my dvd is /dev/dvd1 as seen in this excerpt from **sudo lshw**. Can the logical name of a device be changed? I have only one dvd writer and the new name would not conflict with my cdrom.


 *-cdrom:1
                description: DVD-RAM writer
                product: DVD A  DH20A4P
                vendor: ATAPI
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 9P59
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open

---

### Post by mc4man on 2008-09-03
Shouldn't be a problem. Run this in a maximized terminal (helps reading

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

Should show what's taken /dev/scd0 and /dev/dvd, ect.

---

### Post by harryliddic on 2008-09-03
nothing is taking up the name of /dev/dvd because my dvd drive also reads cdroms all logical names have a "1" append to them.

harry@harry-desktop:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# NR-7800A (pci-0000:00:1f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
# DVD_A_DH20A4P (pci-0000:00:1f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
harry@harry-desktop:~$

---

### Post by mc4man on 2008-09-03
If you post the results I'll make a suggestion

---

### Post by harryliddic on 2008-09-03
I edited the last post with the readout

---

### Post by mc4man on 2008-09-03
what is the NR-7800A?, is it still on your system?

---

### Post by harryliddic on 2008-09-03
my cdrom

 *-cdrom:0
                description: CD-R/CD-RW writer
                product: NR-7800A
                vendor: _NEC
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.07
                serial: [_NEC    NR-7800A        1.0701071100
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open

---

### Post by mc4man on 2008-09-03
go ```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

Remove the 1 from dvd1 and dvdrw1

like this

```
# DVD_A_DH20A4P (pci-0000:00:1f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
```

Then reboot and ck. by running cat ..... again

---

### Post by harryliddic on 2008-09-03
It worked. You are a seer among linux gurus, Thank you.  *-cdrom:0
                description: CD-R/CD-RW writer
                product: NR-7800A
                vendor: _NEC
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.07
                serial: [_NEC    NR-7800A        1.0701071100
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD-RAM writer
                product: DVD A  DH20A4P
                vendor: ATAPI
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 9P59
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open

harry@harry-desktop:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# NR-7800A (pci-0000:00:1f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
# DVD_A_DH20A4P (pci-0000:00:1f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
harry@harry-desktop:~$

---

### Post by mc4man on 2008-09-03
Glad your back in business.

side note:

most audio player will default to /dev/cdrom, if at some point you want them to access your DVD A DH20A4P instead of the nec you can also switch those links, ie. give the nec cdrom1, cdrw1 and give the DVD A DH20A4P cdrom, cdrw.

The only thing you can't switch is scd0, scd1, sr0, sr1 - that's determined by drive position, ie. the optical drive that's in a master position will always get scd0, sr0

---

