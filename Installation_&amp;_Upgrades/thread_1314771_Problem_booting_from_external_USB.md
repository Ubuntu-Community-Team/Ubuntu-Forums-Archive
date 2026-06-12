---
title: "Problem booting from external USB"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by MicheleZ on 2009-11-04
Hello,

After upgrading to Karmic I have problems booting from my external USB drive. Jaunty (on the same external HD) used to boot in a couple of minutes max, Karmic instead takes more than 5 and most of the time is spent resetting the high speed USB device ehci_hcd.

Here's an excerpt from dmesg

The external HD is found (I guess)

```
[    1.808210] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.941201] usb 2-1: configuration #1 chosen from 1 choice
```
Then a few seconds later the file system is mounted
```
[    7.687707] scsi 4:0:0:0: Direct-Access     SAMSUNG  HM320JX               PQ: 0 ANSI: 2 CCS
[    7.688419] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    7.689387] sd 4:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    7.690131] sd 4:0:0:0: [sdb] Write Protect is off
[    7.690134] sd 4:0:0:0: [sdb] Mode Sense: 34 00 00 00
[    7.690136] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.691523] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.691528]  sdb: sdb1 sdb2 < sdb5 sdb6 > sdb3 sdb4
[    7.743166] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.743170] sd 4:0:0:0: [sdb] Attached SCSI disk
[    8.160461] PM: Starting manual resume from disk
[    8.160465] PM: Resume from partition 8:22
[    8.160467] PM: Checking hibernation image.
[    8.161052] PM: Resume from disk failed.
[    8.185865] kjournald starting.  Commit interval 5 seconds
[    8.185878] EXT3-fs: mounted filesystem with writeback data mode.
[    9.187621] type=1505 audit(1257372942.177:2): operation="profile_load" pid=519 name=/usr/share/gdm/guest-session/Xsession
[    9.230005] type=1505 audit(1257372942.222:3): operation="profile_load" pid=520 name=/sbin/dhclient3
[    9.230700] type=1505 audit(1257372942.222:4): operation="profile_load" pid=520 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.231063] type=1505 audit(1257372942.222:5): operation="profile_load" pid=520 name=/usr/lib/connman/scripts/dhclient-script
[    9.276323] type=1505 audit(1257372942.269:6): operation="profile_load" pid=521 name=/usr/bin/evince
[    9.286756] type=1505 audit(1257372942.277:7): operation="profile_load" pid=521 name=/usr/bin/evince-previewer
[    9.292875] type=1505 audit(1257372942.285:8): operation="profile_load" pid=521 name=/usr/bin/evince-thumbnailer
[    9.331757] type=1505 audit(1257372942.321:9): operation="profile_load" pid=523 name=/usr/lib/cups/backend/cups-pdf
[    9.332615] type=1505 audit(1257372942.325:10): operation="profile_load" pid=523 name=/usr/sbin/cupsd
[    9.356240] type=1505 audit(1257372942.349:11): operation="profile_replace" info="invalid profile format" pid=524
[   10.640410] Adding 2931820k swap on /dev/sdb6.  Priority:-1 extents:1 across:2931820k 
[   11.293538] EXT3 FS on sdb1, internal journal
[   11.609894] udev: starting version 147
[   13.193937] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.326275] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   13.394731] lp: driver loaded but no devices found
[   13.529088] cfg80211: Calling CRDA to update world regulatory domain
[   14.611028] kjournald starting.  Commit interval 5 seconds
[   14.611663] EXT3 FS on sdb4, internal journal
[   14.611671] EXT3-fs: mounted filesystem with writeback data mode.
[   14.643770] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01f9]
[   14.643797] yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
[   14.643799] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst
[   14.678489] kjournald starting.  Commit interval 5 seconds
[   14.679028] EXT3 FS on sdb5, internal journal
[   14.679036] EXT3-fs: mounted filesystem with writeback data mode.

```
then the problem occurs:
Ubuntu takes 31 seconds to reset the high speed USB device followed by another reset (only 8 seconds long)
```

[   32.141947] [drm] TV-16: set mode NTSC 480i 0
[   41.928248] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[   72.916231] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[   80.928236] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[   81.105740] tg3 0000:09:00.0: PME# disabled

```
And again 30 odd seconds + 8 seconds to reset the high speed USB device
```
[   81.165799] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   93.928240] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[  124.916248] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[  132.928247] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[  134.540618] [drm] TV-16: set mode NTSC 480i 0

```

Then, after some time doing something strange with [drm] TV-16 etc... (spending another 90 seconds or so) it resets again:
```
[  135.722338] [drm] TV-16: set mode NTSC 480i 0
[  162.987413] [drm] TV-16: set mode NTSC 480i 0
[  163.152465] [drm] TV-16: set mode NTSC 480i 0
[  163.476947] [drm] TV-16: set mode NTSC 480i 0
[  163.643010] [drm] TV-16: set mode NTSC 480i 0
[  163.967614] [drm] TV-16: set mode NTSC 480i 0
[  164.133035] [drm] TV-16: set mode NTSC 480i 0
[  166.865906] [drm] TV-16: set mode NTSC 480i 0
[  167.031510] [drm] TV-16: set mode NTSC 480i 0
[  216.570181] [drm] TV-16: set mode NTSC 480i 0
[  216.736116] [drm] TV-16: set mode NTSC 480i 0
[  313.945068] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  314.164158] usb 3-2: configuration #1 chosen from 1 choice
```

Finally, after 5 minutes I am allowed to log in...

Any idea how to solve this issue?

Thanks a lot.

MicheleZ

---

