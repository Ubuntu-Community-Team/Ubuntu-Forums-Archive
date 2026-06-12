---
title: "HP tapedrive input/output error"
date: 2010-03-24
forum: Hardware
---

### Post by calyx on 2010-03-24
I'm trying to set a backup to tape of a machine using flexbackup. However any attempt to write to the tape drive (via either flexbackup or just tar) results in "/dev/st0: Input/output error"

The machine seems to recognise the drive ( HP Storageworks Ultrium 448 ) and that there's a tape in it and "mt status" seems to work... "mt -f /dev/st0 rewind" or "erase" throw no errors...

```
root@stor001:/# mt status
SCSI 2 tape drive:
File number=0, block number=0, partition=0.
Tape block size 0 bytes. Density code 0x42 (LTO-2).
Soft error count since last status=0
General status bits on (41010000):
 BOT ONLINE IM_REP_EN

root@stor001:/# cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVDRAM GSA-4084N Rev: KS02
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 03 Lun: 00
  Vendor: HP       Model: Ultrium 2-SCSI   Rev: S65D
  Type:   Sequential-Access                ANSI  SCSI revision: 03
```

"tell" does however

```
root@stor001:/# mt -f /dev/st0 tell
/dev/st0: Input/output error
```

Based on a forum post I found elsewhere, I tried:

```
root@stor001:/# dd if=/dev/zero of=/dev/nst0 bs=1024 count=10
10+0 records in
10+0 records out
10240 bytes (10 kB) copied, 5.0815 s, 2.0 kB/s
```

which gave the person on the forum an error but seems to work for me.

If anyone has any suggestions, I'd appreciate it

---

### Post by trundlenut on 2010-03-24
I had a similar problem with a Dell tape drive and a firmware update seemed to cure it.  It wasn't the easiest thing to do though.

Also there was a lot of dust inside the drive as it had not been used for a significant period so I also cleaned it out before upadting the firmware.

---

### Post by calyx on 2010-03-24
The tape drive was working fine on the same machine a little while ago when it had windows on it.

The HP website only has firmware updates that seem to be designed for RedHat or SUSE which I don't think will work properly in Ubuntu.

---

### Post by trundlenut on 2010-03-24
> **calyx said:**
> The HP website only has firmware updates that seem to be designed for RedHat or SUSE which I don't think will work properly in Ubuntu.

That's the problem I had, but some enterprising soul had come up with a way to make the update work with Ubuntu.

Is there an option to do the update from a boot disk?  This is how I updated the bios on my dell server - the boot disk option was listed under windows on their website as you needed to download and run a windows program to create the boot disk.

Unfortunately my HP server doesn't have a tape drive so I don't really know anything more about the HP drives.

---

### Post by calyx on 2010-03-29
> **trundlenut said:**
> That's the problem I had, but some enterprising soul had come up with a way to make the update work with Ubuntu.

Do you happen to have a link to the enterprising soul's fix? ;)

In the meantime, I'll look into the boot disk option. It's been a difficult problem for me to diagnose since I'm accessing the machine remotely

---

### Post by calyx on 2010-04-27
Thanks to someone on serverfault I found I needed to execute:

```
mt -f /dev/nst0 stsetoptions scsi2logical

```

on each load of a new tape. Works fine now...

---

