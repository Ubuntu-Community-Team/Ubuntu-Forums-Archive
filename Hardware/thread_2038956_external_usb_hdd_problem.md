---
title: "external usb hdd problem"
date: 2012-08-07
forum: Hardware
---

### Post by buszkiraly on 2012-08-07
I've been trying to use former 2.5" notebook drives as external usb drives with ubuntu 12.04 & 10.04 without much success. Many times mounting the drive fails due to file system errors. I've tried NTFS & EXT4, but it doesn't seem to have any effect on the issue. Also tried to mount with two different hdds, two different notebook, two different caddies. Both of the drives should be OK, because when I use them as internal drives they work flawlessly. The caddies are also OK, because the only time I have trouble is when I try to mount under Ubuntu. With Windows it works fine. Does anybody know what's going on?

---

### Post by ahallubuntu on 2012-08-07
I use internal drives with external enclosures and adapters all the time and I rarely have issues like you describe - almost never.  My primary OSes are Ubuntu 10.04 LTS and 11.04 .  I have several different adapters and many different drives, and I attach them all the time, NTFS and ext3/4.

As a sanity check, I would still make sure the drives have no S.M.A.R.T. issues.  You can try testing with smartmontools, though you may have to work with options to get S.M.A.R.T. info over USB.  (May not automatically work, better chance in 12.04 LTS.)

You might also post the hardware ID of the adapters you are using and dmesg output from Ubuntu during the time you are trying to use a drive unsuccessfully.

FYI, sometimes portable drives in these enclosures need more power than one USB port can supply.  That's why sometimes the cables have two USB plugs on one end, so you can use power from two ports.  Occasionally I need to do this though my laptop can supply enough power from one port.  Some laptops don't supply enough on the one port.  The results can be unpredictable if you don't have enough power.

---

### Post by buszkiraly on 2012-08-08
That's what I got with smartmontools:

```
Vendor:               WDC WD64
Product:              00BPVT-75HXZT1  
Revision:                 
User Capacity:        640.135.028.736 bytes [640 GB]
Logical block size:   512 bytes
Device type:          disk
Local Time is:        Wed Aug  8 08:02:46 2012 CEST
Device supports SMART and is Enabled
Temperature Warning Disabled or Not Supported
unable to enable Exception control and warning [unsupported scsi opcode]
SMART Health Status: OK

Error Counter logging not supported
Device does not support Self Test logging
```

And that's with dmesg:
```
zoltan@zoltan-Inspiron-N5110:~$ dmesg | tail
[ 3476.153647] sd 10:0:0:0: [sdc] Unhandled error code
[ 3476.153657] sd 10:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3476.153665] sd 10:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 3476.153685] end_request: I/O error, dev sdc, sector 0
[ 3476.153695] Buffer I/O error on device sdc, logical block 0
[ 3476.270671] usb 3-2: reset high-speed USB device number 6 using xhci_hcd
[ 3476.288746] xhci_hcd 0000:0b:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020dfcff00
[ 3476.288758] xhci_hcd 0000:0b:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88020dfcff40
[ 3476.288774] usb 3-2: ep 0x81 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 3476.288784] usb 3-2: ep 0x2 - rounding interval to 32768 microframes, ep desc says 0 microframes

```

Power: I use them with two cables, but that didn't solve the problem.

---

