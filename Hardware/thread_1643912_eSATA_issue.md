---
title: "eSATA issue"
date: 2010-12-12
forum: Hardware
---

### Post by r_avital on 2010-12-12
Hello,
Lucid 10.0.4 64-bit on HP Pavilion dv8t-1200 Quad, the output of uname -a is:

2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64

situation: Hitachi 500Gb 2.5” drive in enclosure.  The enclosure has:
1. Straight USB cable for power and data - connected to USB, works fine.
2. USB Y-connector to DC round plug, plugs in to DC power connector on enclosure, provides power (blue led lights up).
3. When used with #2 above, one eSata connector, connected to USB/eSata connector on computer and eSata connector on enclosure. 

The eSata, connected with options 2+3 above (proper way to provide  power+data connection), has worked on this computer ONCE, and never  again.  I mean, during one session, I was able to issue “sudo  /sbin/rescan-scsi-bus.sh” at a terminal, and it nicely scanned all scsi  devices (install package scsi-tools if you want to try this). 

I was able to boot up with the drive connected with eSata (as in option  2+3 above) and Lucid 10.0.4 64-bit recognized the drive nice and pretty.   I was able to boot up without the drive plugged in, plug it via eSata  (same as above) then issue the rescan command as above, and the drive  would mount. 

Since then, I don't know what happened (probably some kernel update), but only the straight USB connection work.  No eSata.  The unit gets power, no data.

Here's the output of the rescan command:
```
sudo /sbin/rescan-scsi-bus.sh

Host adapter 0 (ahci) found.
Host adapter 1 (ahci) found.
Host adapter 2 (ahci) found.
Host adapter 3 (ahci) found.
Host adapter 4 (ahci) found.
Host adapter 5 (ahci) found.
Scanning SCSI subsystem for new devices
Scanning host 0 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 0 0 0 0 ...
OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: ATA      Model: Hitachi HTS72505 Rev: PC4O
      Type:   Direct-Access                    ANSI SCSI revision: 05
Scanning host 1 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 1 0 0 0 ...
OLD: Host: scsi1 Channel: 00 Id: 00 Lun: 00
      Vendor: hp       Model: CDDVDW TS-L633N  Rev: 0300
      Type:   CD-ROM                           ANSI SCSI revision: 05
Report Luns command not supported (support mandatory in SPC-3)
Scanning for device 1 0 0 0 ...
OLD: Host: scsi1 Channel: 00 Id: 00 Lun: 00
      Vendor: hp       Model: CDDVDW TS-L633N  Rev: 0300
      Type:   CD-ROM                           ANSI SCSI revision: 05
Scanning host 2 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 3 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 4 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 4 0 0 0 ...
OLD: Host: scsi4 Channel: 00 Id: 00 Lun: 00
      Vendor: ATA      Model: Hitachi HTS72505 Rev: PC4O
      Type:   Direct-Access                    ANSI SCSI revision: 05
Scanning host 5 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
0 new device(s) found.               
0 device(s) removed. 
```Before it gives the last two lines, it pauses on "NEW:" for a second, then of course "NEW:" disappears. It sees all the channel, just doesn't see a device attached to any ahci adapter.

What bugs me is that this used to work flawlessly, even if briefly.  Even tried two different eSata cables.

 Anyone experience anything similar? 
   Thanks in advance

---

