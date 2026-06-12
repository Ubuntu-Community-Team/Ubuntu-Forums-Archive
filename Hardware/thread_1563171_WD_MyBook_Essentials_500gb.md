---
title: "WD MyBook Essentials 500gb"
date: 2010-08-28
forum: Hardware
---

### Post by K3l3v on 2010-08-28
I have a WD MyBook Essentials 500gb external HD (Model WD5000H1U). It was working flawlessly for 4yrs with redhat, ubuntu (several versions), and mint. In June of this year, I had to replace the HD and power supply on my laptop (presumably due to multiple power failures). Yes, I did buy a UPS when I replaced the other parts.

Shortly after replacing the old HD and power supply, I noticed that I could not access the external HD anymore. Output from dmesg listed below. I've searched the ubuntu forums, mint forums, and WD website without success. Based on the 'dmesg' output, I suspect that the HD shut down uncleanly, and needs to be reset. Unfortunately, I don't know what needs to be done.

Any help is appreciated.
[HTML]
<blockquote>
[406249.508143] usb 1-8: new high speed USB device using ehci_hcd and address 3
[406249.641949] usb 1-8: configuration #1 chosen from 1 choice
[406249.862726] Initializing USB Mass Storage driver...
[406249.873296] scsi2 : SCSI emulation for USB Mass Storage devices
[406249.885189] usbcore: registered new interface driver usb-storage
[406249.885199] USB Mass Storage support registered.
[406249.886164] usb-storage: device found at 3
[406249.886167] usb-storage: waiting for device to settle before scanning
[406254.886917] usb-storage: device scan complete
[406254.887641] scsi 2:0:0:0: Direct-Access     WD                        1.65 PQ: 0 ANSI: 0
[406254.888652] sd 2:0:0:0: Attached scsi generic sg2 type 0
[406254.898474] sd 2:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[406254.899481] sd 2:0:0:0: [sdb] Using 0xffffffff as device size
[406254.899499] sd 2:0:0:0: [sdb] 4294967296 512-byte logical blocks: (2.19 TB/2.00 TiB)
[406254.903931] sd 2:0:0:0: [sdb] Write Protect is off
[406254.903942] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[406254.903948] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[406254.904879] sd 2:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[406254.907221] sd 2:0:0:0: [sdb] Using 0xffffffff as device size
[406254.907993] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[406254.908005]  sdb:
[406254.909319] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[406254.909336] sd 2:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[406254.909353] Info fld=0x0
[406254.909361] sd 2:0:0:0: [sdb] Add. Sense: Logical block address out of range
[406254.909379] end_request: I/O error, dev sdb, sector 0
[406254.909392] Buffer I/O error on device sdb, logical block 0
[406254.912694] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[406254.912704] sd 2:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[406254.912715] Info fld=0x0
[406254.912720] sd 2:0:0:0: [sdb] Add. Sense: Logical block address out of range
[406254.912733] end_request: I/O error, dev sdb, sector 0
[406254.912742] Buffer I/O error on device sdb, logical block 0
[406254.914192] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[406254.914202] sd 2:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[406254.914213] Info fld=0x0
[406254.914218] sd 2:0:0:0: [sdb] Add. Sense: Logical block address out of range
[406254.914230] end_request: I/O error, dev sdb, sector 0
[406254.914239] Buffer I/O error on device sdb, logical block 0
[406254.915943] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[406254.915953] sd 2:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[406254.915963] Info fld=0x0
[406254.915968] sd 2:0:0:0: [sdb] Add. Sense: Logical block address out of range
[406254.915981] end_request: I/O error, dev sdb, sector 0
[406254.915988] Buffer I/O error on device sdb, logical block 0
[406254.917317] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
</blockquote>
...etc for several hundred lines[/HTML]

---

### Post by Araja on 2010-08-28
I ran into the same problem with my MyBook too. This helped me out alot, hope it helps you too.

Here is the link. [http://ubuntuforums.org/showthread.p...t=unable+mount]("http://ubuntuforums.org/showthread.php?t=1518031&highlight=unable+mount")

---

### Post by K3l3v on 2010-09-11
Araja,

Thank you for your reply. I have spent a while researching the subject and trying several things.

I tried using ntfsfix as suggested [here]("http://ubuntuforums.org/showthread.php?t=1518031&highlight=unable+mount") and referencing [here]("http://art.ubuntuforums.org/showthread.php?p=8627316") and [here]("http://ubuntuforums.org/showthread.php?t=1144175"). Attempting to use ntfsfix still returned an I/O error. It also suggested that I use chkdsk. So, I scrounged a windoze box and tried to use chkdsk, but got an error with everything I tried (don't have the box here, so I can't reference the errors I received).

At this point, I think the Master File Table is corrupted and needs to be reflashed or reset. I have an email in to WD's help desk. I'll post if/when I can get something out of them. Unfortunately, this was my temporary back-up HD, so I actually need the files on it. Not sure where to go next to recover the files...

Thank you.

---

### Post by baldr on 2011-08-03
Hi K3l3v, 

bot sure if you got any were with this.  But im getting the exact same issue with a 750G version of the same disk.  Not got much further but i have managed to get a bit more information.  I installed udisk 

ad ran the following
```
udisks --show-info /dev/sdc 
```

and got the following 
```

Showing information for /org/freedesktop/UDisks/devices/sdc
  native-path:                 /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host22/target22:0:0/22:0:0:0/block/sdc
  device:                      8:32
  device-file:                 /dev/sdc
    presentation:              /dev/sdc
    by-id:                     /dev/disk/by-id/usb-WD_7500AAK_External_574341505430303431353830-0:0
    by-path:                   /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0
  detected at:                 Wed 03 Aug 2011 06:27:55 PM CEST
  system internal:             0
  removable:                   0
  has media:                   1 (detected at Wed 03 Aug 2011 06:27:55 PM CEST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        750156374016
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    WD
    model:                     7500AAK External
    revision:                  1.06
    serial:                    574341505430303431353830
    WWN:                       
    detachable:                1
    can spindown:              1
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 Updated at Wed 03 Aug 2011 06:28:26 PM CEST
      overall assessment:      Disk was used outside of design parameters in the past
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate         200|200| 51   good    0           Pre-fail Online 
 spin-up-time                214|  5| 21 FAIL_PAST 6.3 secs    Pre-fail Online 
 start-stop-count             99| 99|  0    n/a    1722        Old-age  Online 
 reallocated-sector-count    200|200|140   good    0 sectors   Pre-fail Online 
 seek-error-rate             200|200| 51   good    0           Old-age  Online 
 power-on-hours               77| 77|  0    n/a    717.5 days  Old-age  Online 
 spin-retry-count            100|100| 51   good    1           Old-age  Online 
 calibration-retry-count     100|100| 51   good    0           Old-age  Online 
 power-cycle-count           100|100|  0    n/a    152         Old-age  Online 
 power-off-retract-count     200|200|  0    n/a    39          Old-age  Online 
 load-cycle-count            200|200|  0    n/a    1747        Old-age  Online 
 temperature-celsius-2       122| 77|  0    n/a    30C / 86F   Old-age  Online 
 reallocated-event-count     200|200|  0    n/a    0           Old-age  Online 
 current-pending-sector      200|200|  0    n/a    0 sectors   Old-age  Online 
 offline-uncorrectable       200|200|  0    n/a    0 sectors   Old-age  Offline
 udma-crc-error-count        200|200|  0    n/a    0           Old-age  Online 
 multi-zone-error-rate       200|200| 51   good    0           Old-age  Offline

```

Looks like i get the following error
 spin-up-time                214|  5| 21 FAIL_PAST 6.3 secs    Pre-fail Online

I also note that the following is wrong
power-on-hours               77| 77|  0    n/a    717.5 days  Old-age  Online

not sure what this means or how to fix it though

I also installed sdparm

ran the following
```
 sdparm --long  /dev/sdc
```

and got this

```
    /dev/sdc: WD        7500AAK External  1.06
    Direct access device specific parameters: WP=0  DPOFUA=0
Read write error recovery [rw] mode page:
>>> warning: mode page seems malformed
   The page number field should be 0x01, but is 0x05; try '--flexible'
  AWRE        0  [cha: n, def:  0, sav:  0]  Automatic write reallocation enabled
  ARRE        0  [cha: n, def:  0, sav:  0]  Automatic read reallocation enabled
  PER         1  [cha: y, def:  1, sav:  1]  Post error
Caching (SBC) [ca] mode page:
>>> warning: mode page seems malformed
   The page number field should be 0x08, but is 0x05; try '--flexible'
  WCE         1  [cha: y, def:  1, sav:  1]  Write cache enable
  RCD         0  [cha: n, def:  0, sav:  0]  Read cache disable
Control [co] mode page:
>>> warning: mode page seems malformed
   The page number field should be 0x0a, but is 0x05; try '--flexible'
  SWP         0  [cha: n, def:  0, sav:  0]  Software write protect
Informational exceptions control [ie] mode page:
>>> warning: mode page seems malformed
   The page number field should be 0x1c, but is 0x05; try '--flexible'
  EWASC       0  [cha: n, def:  0, sav:  0]  Enable warning
  DEXCPT      1  [cha: y, def:  1, sav:  1]  Disable exceptions
  MRIE        0  [cha: n, def:  0, sav:  0]  Method of reporting informational exceptions
``` 

Which dosn't look good either.  I am guessing this is bricked.  ill keep on blindly running commands on it and let you know if things get better .... or worse :)

---

