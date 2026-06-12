---
title: "Problem accessing files on external hard drive"
date: 2009-04-21
forum: Hardware
---

### Post by ptklip on 2009-04-21
Could someone please give me a hand with this issue? I sure would appreciate it.

I'm having a problem with a Western Digital external USB drive.

My OS is Ubuntu 64 8.10.

Drive seems to be mounted but can't read files. Drive is always busy.

Some dmesg output. It's listed as sdf1, and I see that the filesystem is mounted.

[ 2409.916105] usb 8-5: new high speed USB device using ehci_hcd and address 4
[ 2410.050454] usb 8-5: configuration #1 chosen from 1 choice
[ 2410.051589] scsi11 : SCSI emulation for USB Mass Storage devices
[ 2410.053311] usb-storage: device found at 4
[ 2410.053317] usb-storage: waiting for device to settle before scanning
[ 2415.052298] usb-storage: device scan complete
[ 2415.052852] scsi 11:0:0:0: Direct-Access     WD       10EACS External  1.05 PQ: 0 ANSI: 4
[ 2415.056312] sd 11:0:0:0: [sdf] 1953525168 512-byte hardware sectors (1000205 MB)
[ 2415.057186] sd 11:0:0:0: [sdf] Write Protect is off
[ 2415.057193] sd 11:0:0:0: [sdf] Mode Sense: 21 00 00 00
[ 2415.057197] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 2415.057944] sd 11:0:0:0: [sdf] 1953525168 512-byte hardware sectors (1000205 MB)
[ 2415.058814] sd 11:0:0:0: [sdf] Write Protect is off
[ 2415.058819] sd 11:0:0:0: [sdf] Mode Sense: 21 00 00 00
[ 2415.058823] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 2415.058829]  sdf: sdf1
[ 2415.077246] sd 11:0:0:0: [sdf] Attached SCSI disk
[ 2415.079084] sd 11:0:0:0: Attached scsi generic sg6 type 0
[ 2415.466188] kjournald starting.  Commit interval 5 seconds
[ 2415.467000] EXT3 FS on sdf1, internal journal
[ 2415.467008] EXT3-fs: recovery complete.
[ 2415.467011] EXT3-fs: mounted filesystem with ordered data mode.
[ 2419.027579] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2419.027588] Info fld=0x0
[ 2419.027590] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
[ 2421.944428] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2421.944437] Info fld=0x0
[ 2421.944439] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
[ 2425.249638] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2425.249648] Info fld=0x0
[ 2425.249651] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
[ 2428.166496] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2428.166505] Info fld=0x0
[ 2428.166508] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
[ 2431.208491] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2431.208500] Info fld=0x0
[ 2431.208561] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
[ 2434.110325] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2434.110334] Info fld=0x0
[ 2434.110336] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
[ 2437.294413] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2437.294423] Info fld=0x0
[ 2437.294425] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
[ 2440.463516] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2440.463527] Info fld=0x0
[ 2440.463530] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
[ 2443.377357] sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 2443.377368] Info fld=0x0
[ 2443.377371] sd 11:0:0:0: [sdf] Add. Sense: No additional sense information

When I try to ls a subdirectory on it, it just hangs forever.

It shows up in df output:
peter@maui:~$ df
...
/dev/sdf1            961432072  63041556 849552516   7% /media/Jupiter

Here it is in mount -v output:
/dev/sdf1 on /media/Jupiter type ext3 (rw,nosuid,nodev,uhelper=hal)

How can I troubleshoot this and access my files?

---

