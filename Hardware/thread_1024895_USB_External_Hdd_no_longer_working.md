---
title: "USB External Hdd no longer working"
date: 2008-12-29
forum: Hardware
---

### Post by jwhal on 2008-12-29
I just bought an Iomega 1TB external USB hdd. It was plugged in to a WinXP machine and had several hundred photos copied to it. It was then removed (properly) and I plugged it into my Dell Inspiron 1525 (Intrepid). This is the output of my message log:
Dec 27 13:45:13 jon-laptop kernel: [87248.760332] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Dec 29 13:42:15 jon-laptop kernel: [259870.633179] usb 4-3: new high speed USB device using ehci_hcd and address 4
Dec 29 13:42:15 jon-laptop kernel: [259870.766541] usb 4-3: configuration #1 chosen from 1 choice
Dec 29 13:42:15 jon-laptop kernel: [259870.767715] scsi6 : SCSI emulation for USB Mass Storage devices
Dec 29 13:42:20 jon-laptop kernel: [259875.768920] scsi 6:0:0:0: Direct-Access     ST310003 40AS                  PQ: 0 ANSI: 2 CCS
Dec 29 13:42:20 jon-laptop kernel: [259875.771629] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Dec 29 13:42:20 jon-laptop kernel: [259875.772502] sd 6:0:0:0: [sdb] Write Protect is off
Dec 29 13:42:20 jon-laptop kernel: [259875.773447] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Dec 29 13:42:20 jon-laptop kernel: [259875.774354] sd 6:0:0:0: [sdb] Write Protect is off
Dec 29 13:42:22 jon-laptop kernel: [259875.774378]  sdb:<6>usb 4-3: USB disconnect, address 4
Dec 29 13:42:22 jon-laptop kernel: [259878.430214] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430244] __ratelimit: 5 callbacks suppressed
Dec 29 13:42:22 jon-laptop kernel: [259878.430327] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430400] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430463] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430527] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430615] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430678] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430740] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430802] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430845] Dev sdb: unable to read RDB block 0
Dec 29 13:42:22 jon-laptop kernel: [259878.430871] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.430935] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.431007] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.431060] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.431115] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.431169] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 29 13:42:22 jon-laptop kernel: [259878.431204]  unable to read partition table
Dec 29 13:42:22 jon-laptop kernel: [259878.434441] sd 6:0:0:0: [sdb] Attached SCSI disk
Dec 29 13:42:22 jon-laptop kernel: [259878.434685] sd 6:0:0:0: Attached scsi generic sg2 type 0

The drive was formatted with NTFS (at the shop, not reformatted by me). I did not have ntfs support installed before I plugged it in. It never showed up, I installed the ntfs-3g driver, rebooted and nothing. I've checked lsusb before and after plugging it in; tail -f /var/log/messages (after ntfs driver install and reboot); tail -f dmesg; and lshal -m....nothing. Is it possible my laptop fried the drive??? The drive will no longer show up under Intrepid or WinXP (on the other laptop). I've tried different USB ports, a different USB cable (that I know works) on both machines. Only thing I didn't try was a different power cord for the drive (don't have one handy). The power light does not come on on the drive; and no power button for it either.

Thoughts?

PS - I did not check my dmesg/lsusb/lshal before I rebooted....

Jon

---

