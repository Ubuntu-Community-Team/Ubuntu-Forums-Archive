---
title: "USB HD doesn't stay mounted"
date: 2009-08-25
forum: Hardware
---

### Post by dsmithnc on 2009-08-25
I have a Maxtor external hd that connects via usb to my pc running Ubuntu 9.04.  A problem has developed where the drive will sudden'y "unmount" and just disappear from view.  The only good way to get the pc to see it again is to restart it.

Any ideas, what other info would you need, etc.

Thanks

Dick

---

### Post by cariboo on 2009-08-25
The next time the drive disappears open a terminal and type:

```
dmesg | tail -n20
```

the above command should give you an indication of wqhat is happening and why the drive is disappearing. Paste the output in your next post if you don't understand what you are seeing.

---

### Post by dsmithnc on 2009-08-25
> **cariboo907 said:**
> The next time the drive disappears open a terminal and type:

```
dmesg | tail -n20
```

the above command should give you an indication of wqhat is happening and why the drive is disappearing. Paste the output in your next post if you don't understand what you are seeing.

Thanks, I'll do that.

Dick

---

### Post by dsmithnc on 2009-08-28
I ran the dmesg command and this is the output:

dick@ubuntu:~$ dmesg | tail -n20
[198820.566946] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[198820.567068] sd 6:0:0:0: Attached scsi generic sg4 type 0
[198820.631232] sd 6:0:0:0: [sdc] 15687680 512-byte hardware sectors: (8.03 GB/7.48 GiB)
[198820.636228] sd 6:0:0:0: [sdc] Write Protect is off
[198820.636232] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[198820.636234] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[198820.641227] sd 6:0:0:0: [sdc] 15687680 512-byte hardware sectors: (8.03 GB/7.48 GiB)
[198820.646217] sd 6:0:0:0: [sdc] Write Protect is off
[198820.646220] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[198820.646223] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[198820.646229]  sdc:<6>usb 2-1.7: reset full speed USB device using uhci_hcd and address 5
[198822.165961]  sdc1
[198844.368913] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[198854.509649] wlan0: authenticate with AP 00:18:4d:9c:30:ba
[198854.511682] wlan0: authenticated
[198854.511686] wlan0: associate with AP 00:18:4d:9c:30:ba
[198854.514648] wlan0: RX AssocResp from 00:18:4d:9c:30:ba (capab=0x431 status=0 aid=1)
[198854.514652] wlan0: associated
[198854.520048] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[198864.876026] wlan0: no IPv6 routers present
dick@ubuntu:~$ dmesg | tail -n50
[198813.775562] scsi6 : SCSI emulation for USB Mass Storage devices
[198813.777658] usb-storage: device found at 5
[198813.777662] usb-storage: waiting for device to settle before scanning
[198818.780024] usb-storage: device scan complete
[198818.782623] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 8GB    8.07 PQ: 0 ANSI: 2
[198818.830588] sd 6:0:0:0: [sdc] 15687680 512-byte hardware sectors: (8.03 GB/7.48 GiB)
[198818.833578] sd 6:0:0:0: [sdc] Write Protect is off
[198818.833582] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[198818.833585] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[198818.846594] sd 6:0:0:0: [sdc] 15687680 512-byte hardware sectors: (8.03 GB/7.48 GiB)
[198818.849583] sd 6:0:0:0: [sdc] Write Protect is off
[198818.849586] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[198818.849589] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[198818.849596]  sdc:<6>usb 2-1.7: reset full speed USB device using uhci_hcd and address 5
[198819.929366] usb 2-1.7: reset full speed USB device using uhci_hcd and address 5
[198820.440264] usb 2-1.7: reset full speed USB device using uhci_hcd and address 5
[198820.561247] end_request: I/O error, dev sdc, sector 0
[198820.561258] Buffer I/O error on device sdc, logical block 0
[198820.561311] Buffer I/O error on device sdc, logical block 0
[198820.561334] Buffer I/O error on device sdc, logical block 0
[198820.561350] Buffer I/O error on device sdc, logical block 0
[198820.561362] Buffer I/O error on device sdc, logical block 0
[198820.561368] ldm_validate_partition_table(): Disk read failed.
[198820.561377] Buffer I/O error on device sdc, logical block 0
[198820.561388] Buffer I/O error on device sdc, logical block 0
[198820.561399] Buffer I/O error on device sdc, logical block 0
[198820.561411] Buffer I/O error on device sdc, logical block 0
[198820.561416] Dev sdc: unable to read RDB block 0
[198820.561425] Buffer I/O error on device sdc, logical block 0
[198820.561479]  unable to read partition table
[198820.566946] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[198820.567068] sd 6:0:0:0: Attached scsi generic sg4 type 0
[198820.631232] sd 6:0:0:0: [sdc] 15687680 512-byte hardware sectors: (8.03 GB/7.48 GiB)
[198820.636228] sd 6:0:0:0: [sdc] Write Protect is off
[198820.636232] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[198820.636234] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[198820.641227] sd 6:0:0:0: [sdc] 15687680 512-byte hardware sectors: (8.03 GB/7.48 GiB)
[198820.646217] sd 6:0:0:0: [sdc] Write Protect is off
[198820.646220] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[198820.646223] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[198820.646229]  sdc:<6>usb 2-1.7: reset full speed USB device using uhci_hcd and address 5
[198822.165961]  sdc1
[198844.368913] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[198854.509649] wlan0: authenticate with AP 00:18:4d:9c:30:ba
[198854.511682] wlan0: authenticated
[198854.511686] wlan0: associate with AP 00:18:4d:9c:30:ba
[198854.514648] wlan0: RX AssocResp from 00:18:4d:9c:30:ba (capab=0x431 status=0 aid=1)
[198854.514652] wlan0: associated
[198854.520048] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[198864.876026] wlan0: no IPv6 routers present
dick@ubuntu:~$ 

It looks like some buffer errors but I'm not sure what they mean.  Thaks for your help.

Dick

---

