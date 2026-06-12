---
title: "SMART Enabled/Disabled problem"
date: 2010-06-10
forum: Hardware
---

### Post by g-a-c on 2010-06-10
Hi, I thought I had a HD problem recently, but now I think everything's OK. However, it prompted me to double check my smartmontools setup which used to be set up for daily short tests and weekly extended tests on my 4 disks (one internal SATA, 3 USB). However now, I can't seem to get it to work on the USB disks:

```
gavin@XBMCLive:~$ sudo smartctl -d sat,12 -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST9500325AS
Serial Number:    5VE0B1XK
Firmware Version: 0001BSM1
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Jun 10 08:00:27 2010 BST
SMART support is: Available - device has SMART capability.
[b]SMART support is: Enabled

SMART Disabled. Use option -s with argument 'on' to enable it.[/b]
```Running the suggested "-s on" command gives me:

```
gavin@XBMCLive:~$ sudo smartctl -d sat,12 -s on /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

[b]=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.
SMART Disabled. Use option -s with argument 'on' to enable it.[/b]
```This happens on all three external disks (all Seagate FreeAgent 500Gb drives). It used to work, I could use -a to see the full output and verify that the scheduled smartd.conf tests were running, but now I have no idea whether they're running or not and if they are, I can't see, to get the results! Any ideas why?

edit - worth noting is that these USB drives are part of a zfs-fuse RAIDZ array, however the version of zfs-fuse and smartmontools hasn't changed recently since I had the automated tests working before. SMART tests are FS-independent anyway, I believe? So that shouldn't be of relevance but merely worth noting?

---

### Post by g-a-c on 2010-06-16
Bump. I've now installed 10.04 (using the standard "sudo do-release-upgrade" command line), and I still have this issue. Further to what I posted above, smartd *seems* to be running (I have entries in /var/log/syslog saying smartd has found 3 ATA and 1 SCSI device, and occasional entries saying that attributes have changes) but I still can't use smartctl to check the verbose status like I used to be able to do.

---

### Post by amorangi on 2010-07-23
According to wikipedia SMART doesn't work very well (not at all) over USB or firewire.

---

### Post by g-a-c on 2010-07-23
> **amorangi said:**
> According to wikipedia SMART doesn't work very well (not at all) over USB or firewire.No, I know it's not really supported over USB. However smartmontools does have limited support for it, and it *was* working with my particular disks and the command line I noted above. The problem is that it's not working now, and I only had it set to email me on an error and so I don't know at what point it broke.

---

