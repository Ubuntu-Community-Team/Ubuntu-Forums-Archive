---
title: "HELP!  Adaptec raid problem"
date: 2020-10-19
forum: Hardware
---

### Post by David_Partridge on 2020-10-19
Came to look at the system this morning and it was sick:

I'd left a jornalctl window open and was seeing lots of arrors reports against /dev/sda1 which is a hardware raid behind an Adaptec ASR-51245.

After rebooting I went back in the journal to find this in the wee small hours:

```
Oct 19 04:03:03 charon kernel: aacraid: Host adapter abort request.
                               aacraid: Outstanding commands on (0,0,0,0):
Oct 19 04:03:03 charon kernel: aacraid: Host adapter reset request. SCSI hang ?
Oct 19 04:03:18 charon kernel: aacraid: Host adapter reset request. SCSI hang ?
Oct 19 04:03:18 charon kernel: aacraid 0000:01:00.0: outstanding cmd: midlevel-0
Oct 19 04:03:18 charon kernel: aacraid 0000:01:00.0: outstanding cmd: lowlevel-0
Oct 19 04:03:18 charon kernel: aacraid 0000:01:00.0: outstanding cmd: error handler-0
Oct 19 04:03:18 charon kernel: aacraid 0000:01:00.0: outstanding cmd: firmware-1
Oct 19 04:03:18 charon kernel: aacraid 0000:01:00.0: outstanding cmd: kernel-0
Oct 19 04:03:48 charon kernel: sd 0:0:0:0: Device offlined - not ready after error recovery
Oct 19 04:03:48 charon kernel: sd 0:0:0:0: [sda] tag#215 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
Oct 19 04:03:48 charon kernel: sd 0:0:0:0: [sda] tag#215 CDB: Read(16) 88 00 00 00 00 00 00 05 27 48 00 00 00 08 00 00
Oct 19 04:03:48 charon kernel: blk_update_request: I/O error, dev sda, sector 337736 op 0x0:(READ) flags 0x1000 phys_seg 1 prio class 0
Oct 19 04:03:48 charon kernel: BTRFS error (device sda1): bdev /dev/sda1 errs: wr 1, rd 1, flush 0, corrupt 3, gen 0


```

So is this a hardware problem, a driver problem or ???

This might relate to system frozen reports I have made previously.

Help!!
David

---

### Post by scorp123 on 2020-10-19
Sounds like a defective disk. What do you get if you check SMART?

---

### Post by slickymaster on 2020-10-19
*Thread moved to **Hardware**.*

---

### Post by David_Partridge on 2020-10-19
I checked the SMART logs no errors

UPDATE:  btrfs scrub ran clean on the raid array.  Currently running Adaptec Storage Manager to get the card to run a "Verify" on the whole array (come back in a day or so).

D.

---

### Post by David_Partridge on 2020-10-19
It's possible I may have an explanation but would like to bounce it off the experts.

The timeout for the SCSI device /dev/sda is set to 45 seconds which is fine if the drives are spinning.  However the Adaptec Raid controller can power the drives down after a time (currently set to 30 minutes of inactivity).

I'm guessing that the problem above was encountered when the drives had been spun down by the controller.

How do I change the SCSI timeout for the drive permanently and what should I set it to in the case where the RAID controller can power the drives down.

cat /sys/block/sda/device/timeout returns the value 45 

David

David

---

### Post by David_Partridge on 2020-10-20
I'm trying to add a udev rule to set the timeout for disk sda

```
root@charon:/etc/udev/rules.d# udevadm info /sys/block/sda
P: /devices/pci0000:00/0000:00:01.0/0000:01:00.0/host0/target0:0:0/0:0:0:0/block/sda
N: sda
L: 0
S: disk/by-path/pci-0000:01:00.0-scsi-0:0:0:0
S: disk/by-id/scsi-229e91ab800d00000
E: DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:01:00.0/host0/target0:0:0/0:0:0:0/block/sda
E: DEVNAME=/dev/sda
E: DEVTYPE=disk
E: MAJOR=8
E: MINOR=0
E: SUBSYSTEM=block
E: USEC_INITIALIZED=1205420
E: ID_SCSI=1
E: ID_VENDOR=Adaptec
E: ID_VENDOR_ENC=Adaptec\x20
E: ID_MODEL=Shared
E: ID_MODEL_ENC=Shared\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=V1.0
E: ID_TYPE=disk
E: ID_SERIAL=229e91ab800d00000
E: ID_SERIAL_SHORT=29e91ab800d00000
E: ID_SCSI_SERIAL=B81AE929
E: ID_BUS=scsi
E: ID_PATH=pci-0000:01:00.0-scsi-0:0:0:0
E: ID_PATH_TAG=pci-0000_01_00_0-scsi-0_0_0_0
E: ID_PART_TABLE_UUID=f04a25a4-86c8-4f2b-8418-67c0eac8a674
E: ID_PART_TABLE_TYPE=gpt
E: DEVLINKS=/dev/disk/by-path/pci-0000:01:00.0-scsi-0:0:0:0 /dev/disk/by-id/scsi-229e91ab800d00000
E: TAGS=:systemd:

root@charon:/etc/udev/rules.d# 

```

```
root@charon:/etc/udev/rules.d# cat 99-aacraid.rules 
SUBSYSTEM=="block", ACTION=="add", ENV(ID_VENDOR)=="Adaptec", ENV(ID_MODEL)=="Shared", RUN+="/bin/sh -c 'echo 135 > /sys/block/%k/device/timeout'"

root@charon:/etc/udev/rules.d# 

```

but when I try to test it I get:

```
etc/udev/rules.d/99-aacraid.rules:1 Invalid key 'ENV(ID_VENDOR)'


```

What am I doing wrong please?

Argh!! I needed to use ENV{ID_VeNDOR}  (curly braces rather than round brackets)

---

