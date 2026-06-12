---
title: "+ [xfce] CD/DVD Rom/RW Drives mount after reboot then &quot;fade out&quot; (break / unmount)"
date: 2009-01-17
forum: Hardware
---

### Post by polc1410 on 2009-01-17
Intrepid 8.10
Motherboard: K8M890M01 Winfast AMD processor
DVD-ROM: HL-DT-STDVD-ROM GDR8
DVD-RW: LITE-ON DVDRW LH-20A

OK this is bizzarre, and I can't find anyone even mentioning anything simillar.  Its been happening for some time (probably back at Gutsy) but I've not been able to pin point what's going wrong... hope someone can help.

I have two CD/DVD Drives.  When I boot into linux they mount exactly as you'd expect them to (/dev/scd0 and /dev/scd1 with folders created in /media named per the disk name).  I can read from them, and even burn cd's to the RW drive.  But if I don't use the drive for a while (I mean a couple of hours maybe not 6 months) then the drive no longer lists properly...

"New Device Notifier" in KDE4 doesn't list it, Dolphin doesn't etc.  Accessing either /dev/scd0 or /media/cdrom0 usually results in the window hanging - usually without error message or occasionally a 'time out' message.

sudo mount /media/cdrom0 says no fstab entry.  Adding an fstab entry results in a hung terminal window.  The drive is basically disabled.

**FSTAB File**
```

UUID=a035cb24-b179-47e9-8271-ec0eb9e8340c / ext3 defaults 0 1
UUID=2eff12c0-ad32-4286-a271-7fc9140855ab /home ext3 defaults 0 2
UUID=2ae1e43e-2037-4d79-ad67-07db6ff56716 swap swap sw 0 0
/dev/scd0 /media/cdrom udf,iso9660 users 0 0 #I added these
/dev/scd1 /media/cdrom1 udf,iso9660 group,users 0 0 # I added these

```
[B]
MTAB File[/B]
```

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
/dev/sda5 /home ext3 rw,relatime 0 0

```

From what I understand (not much) Ubuntu doesn't need fstab entries for CDRoms as it will mount them on detecting a new CD.  I also seem to remember reading that it will unmount after a period of inactivity.  That seems like what is happening but then I should be able to double click the drive and remount?  And Today I actually found it happened while ripping from a DVD - so the drive was active.

I'm pretty linux savvy - but have no idea where to begin on this one - anyone got any suggestions..

**EDIT...** Some addition info:
lshw hangs on SCSI (at least once the drive is not responding - not tested yet on reboot) if I disable the SCSI test it plays fine.

```

@Linux-PC:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: LITE-ON  Model: DVDRW LH-20A1P   Rev: KL0N
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 01 Lun: 00
  Vendor: HL-DT-ST Model: DVD-ROM GDR8163B Rev: 0L23
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD5000AAKS-6 Rev: 12.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic  Model: USB SD Reader    Rev: 1.00
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic  Model: USB CF Reader    Rev: 1.01
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 02
  Vendor: Generic  Model: USB SM Reader    Rev: 1.02
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 03
  Vendor: Generic  Model: USB MS Reader    Rev: 1.03
  Type:   Direct-Access                    ANSI  SCSI revision: 00

```

---

### Post by polc1410 on 2009-01-17
Have now tested when the drive is working and this is what lshw had to say:

```

     *-scsi
          physical id: 2
          bus info: usb@4:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde

```
and
```

           *-cdrom:0
                description: DVD-RAM writer
                product: DVDRW LH-20A1P
                vendor: LITE-ON
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom5
                logical name: /dev/cdrw5
                logical name: /dev/dvd5
                logical name: /dev/dvdrw5
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: KL0N
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,noexec state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom5
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,noexec state=mounted
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM GDR8163B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom4
                logical name: /dev/dvd4
                logical name: /dev/scd1
                logical name: /dev/sr1
                logical name: /media/cdrom1
                version: 0L23
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,noexec,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom4
                   logical name: /media/cdrom1
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,noexec,utf8 state=mounted

```

---

