---
title: "External USB Hard drive problem"
date: 2010-02-22
forum: Hardware
---

### Post by Morimando on 2010-02-22
First the situation when the error occurs:
The drive is connected, powered on, the I open Truecrypt and mount the partition. All works. After a while, I get errors when, for example, playing a video off it. 
The drive then doesn't respond correctly any more. The following is the error occuring during the process and what happens when I unplug the USB cable and then reattach it:
```
[29844.481292] Aborting journal on device dm-3:8.
[29844.481427] Buffer I/O error on device dm-3, logical block 121667584
[29844.481429] lost page write due to I/O error on dm-3
[29844.481433] JBD2: I/O error detected when updating journal superblock for dm-3:8.
[29855.066027] Buffer I/O error on device dm-3, logical block 0
[29855.066031] lost page write due to I/O error on dm-3
[29855.066795] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[29855.066799] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[29855.066800] EXT4-fs: mballoc: 0 generated and it took 0
[29855.066802] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[29855.066843] EXT4-fs error (device dm-3): ext4_put_super: Couldn't clean up the journal
[29855.066846] EXT4-fs (dm-3): Remounting filesystem read-only
[29872.253528] EXT4-fs (dm-3): barriers enabled
[29872.289951] kjournald2 starting: pid 15057, dev dm-3:8, commit interval 5 seconds
[29872.296701] EXT4-fs (dm-3): internal journal on dm-3:8
[29872.296706] EXT4-fs (dm-3): delayed allocation enabled
[29872.296708] EXT4-fs: file extents enabled
[29872.343818] EXT4-fs: mballoc enabled
[29872.343834] EXT4-fs (dm-3): recovery complete
[29872.345588] EXT4-fs (dm-3): mounted filesystem with ordered data mode
```

Now I reattach

```
[30007.301278] usb 1-9: reset high speed USB device using ehci_hcd and address 7
[30007.546623] usb 1-9: device descriptor read/all, error -71
[30007.672772] usb 1-9: reset high speed USB device using ehci_hcd and address 7
[30007.800019] usb 1-9: device descriptor read/64, error -32
[30008.031320] usb 1-9: device descriptor read/64, error -32
[30008.261274] usb 1-9: reset high speed USB device using ehci_hcd and address 7
[30008.386632] usb 1-9: device descriptor read/8, error -71
[30008.605622] usb 1-9: device descriptor read/8, error -71
[30008.831275] usb 1-9: reset high speed USB device using ehci_hcd and address 7
[30008.956621] usb 1-9: device descriptor read/8, error -71
[30009.175622] usb 1-9: device descriptor read/8, error -71
[30009.281311] usb 1-9: USB disconnect, address 7
[30009.281324] sd 11:0:0:0: [sdd] Unhandled error code
[30009.281327] sd 11:0:0:0: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[30009.281330] end_request: I/O error, dev sdd, sector 420075823
[30009.281377] sd 11:0:0:0: [sdd] Unhandled error code
[30009.281378] sd 11:0:0:0: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[30009.281380] end_request: I/O error, dev sdd, sector 420076063
[30009.281395] sd 11:0:0:0: [sdd] Unhandled error code
[30009.281396] sd 11:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[30009.281398] end_request: I/O error, dev sdd, sector 420076079

```
I don't know whether that's a hard drive option. It seems to have something to do with the encasing and its USB controller (?). It's a 1TB Iomega drive, completely encrypted and formatted with ext4.
Help is truly appreciated.

add: It seems to be a problem with autosuspend in USB devices. Since the problem occurs after a certain amount of time, I think that's reasonable. I just can't find out how to disable it for Karmic as of now.

---

