---
title: "Frequent temporary freezes cause disk-related messages"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by jasampler on 2007-05-27
Hi, I recently purchased a PC with Ubuntu 7.04 pre-installed, from a local vendor. Then I burned a Desktop Ubuntu CD and reinstalled it. Both installations suffer the same problem:

The system freezes for some seconds very often, without repainting the windows and not responding to clicks, and after that everything runs again. Sometimes applications disappear after that time, even the GNOME panel. I don't have acceleration enabled or other configurations different from default.

I executed tail -f /var/log/messages to see what it says when system freezes, just if it could serve for figuring out what's happening, and this is the result (I replaced the name of the machine, "equipo-de-luis" with an "e" for brevity):

After a freeze, it prints:

May 27 05:38:14 e kernel: [ 1278.118238]          res 40/00:18:27:ea:d9/00:00:00:00:00/e9 Emask 0x4 (timeout)
May 27 05:38:14 e kernel: [ 1285.114877] ata3: port is slow to respond, please be patient (Status 0xd0)
May 27 05:38:14 e kernel: [ 1308.106647] ata3: soft resetting port
May 27 05:38:14 e kernel: [ 1308.270742] ata3.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
May 27 05:38:14 e kernel: [ 1308.278726] ata3.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
May 27 05:38:14 e kernel: [ 1308.278731] ata3.00: configured for UDMA/133
May 27 05:38:14 e kernel: [ 1308.278739] ata3: EH complete
May 27 05:38:14 e kernel: [ 1308.279141] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
May 27 05:38:14 e kernel: [ 1308.283890] sda: Write Protect is off
May 27 05:38:14 e kernel: [ 1308.295257] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Then the system is responsive again. Here is another longer example following the last one:

May 27 05:57:11 e kernel: [ 2444.411962]          res 40/00:18:27:ea:d9/00:00:00:00:00/e9 Emask 0x4 (timeout)
May 27 05:57:18 e kernel: [ 2451.409444] ata3: port is slow to respond, please be patient (Status 0xd0)
May 27 05:57:41 e kernel: [ 2474.414558] ata3: soft resetting port
May 27 05:57:41 e kernel: [ 2474.578650] ata3.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
May 27 05:57:41 e kernel: [ 2474.586641] ata3.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
May 27 05:57:41 e kernel: [ 2474.586646] ata3.00: configured for UDMA/133
May 27 05:57:41 e kernel: [ 2474.586655] ata3: EH complete
May 27 05:57:41 e kernel: [ 2474.599951] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
May 27 05:57:41 e kernel: [ 2474.602920] sda: Write Protect is off
May 27 05:57:41 e kernel: [ 2474.603208] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 05:57:42 e kernel: [ 2474.906768]          res 51/84:21:0e:f7:d9/00:00:00:00:00/e9 Emask 0x20 (host bus error)
May 27 05:57:42 e kernel: [ 2475.054352] ata3.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
May 27 05:57:42 e kernel: [ 2475.062246] ata3.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
May 27 05:57:42 e kernel: [ 2475.062251] ata3.00: configured for UDMA/133
May 27 05:57:42 e kernel: [ 2475.062259] ata3: EH complete
May 27 05:57:42 e kernel: [ 2475.062760] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
May 27 05:57:42 e kernel: [ 2475.062900] sda: Write Protect is off
May 27 05:57:42 e kernel: [ 2475.122180]          res 51/84:01:fe:f4:d9/00:00:00:00:00/e9 Emask 0x20 (host bus error)
May 27 05:57:42 e kernel: [ 2475.154816] ata3.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
May 27 05:57:42 e kernel: [ 2475.166893] ata3.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
May 27 05:57:42 e kernel: [ 2475.166899] ata3.00: configured for UDMA/133
May 27 05:57:42 e kernel: [ 2475.166905] ata3: EH complete
May 27 05:57:42 e kernel: [ 2475.167275] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 05:57:42 e kernel: [ 2475.168181] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
May 27 05:57:42 e kernel: [ 2475.169004] sda: Write Protect is off
May 27 05:57:42 e kernel: [ 2475.169269] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

I hope someone could help me telling me what to do with this.
Thank you very much.

Carlos

---

