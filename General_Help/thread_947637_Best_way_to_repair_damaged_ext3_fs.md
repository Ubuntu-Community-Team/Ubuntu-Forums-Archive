---
title: "Best way to repair damaged ext3 fs?"
date: 2008-10-14
forum: General Help
---

### Post by rado3105 on 2008-10-14
I have external disk formatted to ext3, it is 90%full. I want to repair it, but I am nost sure what command is best and most secure.
I was thinking of:
e2fsck -f -v -y

This shows dmesg:
> usb 1-2: new high speed USB device using ehci_hcd and address 56
hub 1-0:1.0: unable to enumerate USB device on port 2
usb 1-2: new high speed USB device using ehci_hcd and address 57
hub 1-0:1.0: unable to enumerate USB device on port 2
usb 1-2: new high speed USB device using ehci_hcd and address 58
hub 1-0:1.0: unable to enumerate USB device on port 2
usb 1-2: new high speed USB device using ehci_hcd and address 59
hub 1-0:1.0: unable to enumerate USB device on port 2
usb 1-2: new high speed USB device using ehci_hcd and address 60
hub 1-0:1.0: unable to enumerate USB device on port 2
usb 2-2: new full speed USB device using uhci_hcd and address 4
usb 2-2: not running at top speed; connect to a high speed hub
usb 2-2: configuration #1 chosen from 1 choice
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
scsi 2:0:0:0: Direct-Access     WDC WD10 00FYPS-01ZKB0    1B01 PQ: 0 ANSI: 2 CCS
sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 38 00 00
sd 2:0:0:0: [sda] Assuming drive cache: write through
sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 38 00 00
sd 2:0:0:0: [sda] Assuming drive cache: write through
 sda: sda1
sd 2:0:0:0: [sda] Attached SCSI disk
sd 2:0:0:0: Attached scsi generic sg0 type 0
usb-storage: device scan complete
kjournald starting.  Commit interval 5 seconds
EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
EXT3 FS on sda1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.


---

### Post by cariboo on 2008-10-14
Make sure that the usb drive is unmounted and use the -p option with e2fsck

> From man e2fsck
 -p     Automatically repair ("preen") the  file  system.   This  option
              will  cause  e2fsck to automatically fix any filesystem problems
              that can be safely fixed without human intervention.  If  e2fsck
              discovers  a  problem which may require the system administrator
              to take  additional  corrective  action,  e2fsck  will  print  a
              description  of the problem and then exit with the value 4 logi&#8208;
              cally or’ed into the exit code.  (See the  EXIT  CODE  section.)
              This  option  is normally used by the system’s boot scripts.  It
              may not be specified at the same time as the -n or -y options.

Jim

---

### Post by rado3105 on 2008-10-14
> r-c r-c # e2fsck -p -v /dev/sda1
WD1TB contains a file system with errors, check forced.
Error reading block 135734817 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 67862530.  

WD1TB: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

this showed me, I dont know now what to do

---

### Post by rado3105 on 2008-10-15
disk has 1TB and I have no other 1TB disk
just now I executed fsck /dev/disk
it has been showing me a lot of read errors and asks me to owervrite:

> Error reading block 162038050 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 162038051 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 162038052 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 162038053 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 162038054 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 162038055 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>? yes

Force rewrite<y>? yes


Can you tell me what fsck do when I press yes on error question?
Is that good solution or is any better?

---

### Post by rado3105 on 2008-10-16
It helped this command:
fsck.ext3 -y /dev/disk
it is important to write type of filesystem, because if there is nothing written can be done more damage like without running fsck.
-y means answear on every question yes.

---

