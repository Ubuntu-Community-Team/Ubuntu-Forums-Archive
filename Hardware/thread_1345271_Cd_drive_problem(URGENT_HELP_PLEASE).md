---
title: "Cd drive problem(URGENT HELP PLEASE)"
date: 2009-12-03
forum: Hardware
---

### Post by Gamesandluv on 2009-12-03
Okay well im new to ubuntu(9.10) and ive had it for about a week for the first couple days its been great but now i have a cd drive error and i dont know how to fix. Here are my details

Here is the error that i receive: 

"Unable to mount cdrom0
Mount: special device /dev/scd1 does not exist"

Here are my 70-persistant-cd.rules thing:

# CD-RW_GCE-8483B (pci-0000:00:02.5-scsi-1:0:1:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:02.5-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:02.5-scsi-1:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"

# DVD-ROM_GDR8162B (pci-0000:00:02.5-scsi-1:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:02.5-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:02.5-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"


Please help i use this computer for my college class:(

---

### Post by Gamesandluv on 2009-12-04
here is the output of the code
```
sudo lshw -C Disk
```

```
  *-disk                  
       description: ATA Disk
       product: HDS722580VLAT20
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: V32O
       serial: VNR21EC2T0WM4M
       size: 76GiB (82GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=2fe52fe4

```

---

### Post by HappyFeet on 2009-12-04
Is this a desktop computer with IDE drives? More than one optical drive perhaps?

See the second post on [this]("http://ubuntuforums.org/archive/index.php/t-917809.html") page.

---

