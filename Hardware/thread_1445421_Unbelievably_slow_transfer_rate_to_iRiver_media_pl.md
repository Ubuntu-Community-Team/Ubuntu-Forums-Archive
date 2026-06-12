---
title: "Unbelievably slow transfer rate to iRiver media player"
date: 2010-04-02
forum: Hardware
---

### Post by BigGeoff on 2010-04-02
I recently purchased an iRiver P7 media player which I am using with Rhythmbox under Ubuntu 9.04. The transfer speed when uploading files to the player is phenomenally slow - the first 50 or so MB reported virtually instantly then the speed immediately drops to about 12-15KB/sec yes KB/sec so a 3-400MB video file takes hours to transfer to the player. This happens with the internal memory and the added memory (SD card) too, althoufg it is faster ror the SD card. No other devices have ever behaved like this on this system (and I have used 2 different Creative players, a different iRiver player and numerous memory sticks). The computer is dual booting with windows (for once that was useful) and under windows it doesn't happen, the speed is as expected so it isn't the hardware. I don't want to have to resort to damned windoze just for this.

dmesg after plugging in the player  shows it identifying both the internal storage and the added SD card but I don't understand the rest of it:

> [21043.540042] usb 1-8: new high speed USB device using ehci_hcd and address 8

[21043.673091] usb 1-8: configuration #1 chosen from 1 choice

[21043.673253] scsi11 : SCSI emulation for USB Mass Storage devices

[21043.673350] usb-storage: device found at 8

[21043.673353] usb-storage: waiting for device to settle before scanning

[21048.672200] usb-storage: device scan complete

[21048.674179] scsi 11:0:0:0: Direct-Access     iriver   P7K                   PQ: 0 ANSI: 0

[21048.674549] scsi 11:0:0:1: Direct-Access     iriver   P7K                   PQ: 0 ANSI: 0

[21048.675486] sd 11:0:0:0: [sdi] 32139264 512-byte hardware sectors: (16.4 GB/15.3 GiB)

[21048.796038] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21049.048015] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21049.300025] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21049.552027] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21049.804028] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21050.060032] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21050.193597] sd 11:0:0:0: [sdi] Write Protect is off

[21050.193601] sd 11:0:0:0: [sdi] Mode Sense: 00 00 00 00

[21050.193604] sd 11:0:0:0: [sdi] Assuming drive cache: write through

[21050.197533] sd 11:0:0:0: [sdi] 32139264 512-byte hardware sectors: (16.4 GB/15.3 GiB)

[21050.308033] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21050.560028] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21050.820034] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21051.068027] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21051.320028] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21051.568027] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21051.701402] sd 11:0:0:0: [sdi] Write Protect is off

[21051.701406] sd 11:0:0:0: [sdi] Mode Sense: 00 00 00 00

[21051.701409] sd 11:0:0:0: [sdi] Assuming drive cache: write through

[21051.701414]  sdi:

[21051.703128] sd 11:0:0:0: [sdi] Attached SCSI removable disk

[21051.703221] sd 11:0:0:0: Attached scsi generic sg9 type 0

[21051.704211] sd 11:0:0:1: [sdj] 15523840 512-byte hardware sectors: (7.94 GB/7.40 GiB)

[21051.820065] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21052.068043] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21052.316188] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21052.568043] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21052.820038] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21053.068063] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21053.201341] sd 11:0:0:1: [sdj] Write Protect is off

[21053.201343] sd 11:0:0:1: [sdj] Mode Sense: 00 00 00 00

[21053.201345] sd 11:0:0:1: [sdj] Assuming drive cache: write through

[21053.206069] sd 11:0:0:1: [sdj] 15523840 512-byte hardware sectors: (7.94 GB/7.40 GiB)

[21053.316039] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21053.564037] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21053.812038] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21054.060045] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21054.312038] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21054.560037] usb 1-8: reset high speed USB device using ehci_hcd and address 8

[21054.693262] sd 11:0:0:1: [sdj] Write Protect is off

[21054.693266] sd 11:0:0:1: [sdj] Mode Sense: 00 00 00 00

[21054.693269] sd 11:0:0:1: [sdj] Assuming drive cache: write through

[21054.693275]  sdj: sdj1

[21054.702787] sd 11:0:0:1: [sdj] Attached SCSI removable disk

[21054.702852] sd 11:0:0:1: Attached scsi generic sg10 type 0

[21054.809364] sd 11:0:0:0: [sdi] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY

[21054.809370] end_request: I/O error, dev sdi, sector 96

[21054.809374] __ratelimit: 118 callbacks suppressed

[21054.809377] Buffer I/O error on device sdi, logical block 12

[21054.809383] Buffer I/O error on device sdi, logical block 13

[21054.809387] Buffer I/O error on device sdi, logical block 14

[21054.809390] Buffer I/O error on device sdi, logical block 15

[21054.809394] Buffer I/O error on device sdi, logical block 16

[21054.809398] Buffer I/O error on device sdi, logical block 17

[21054.809401] Buffer I/O error on device sdi, logical block 18

[21054.809405] Buffer I/O error on device sdi, logical block 19

[21054.809408] Buffer I/O error on device sdi, logical block 20

[21054.809411] Buffer I/O error on device sdi, logical block 21

[21054.882107] sd 11:0:0:0: [sdi] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY

[21054.882112] end_request: I/O error, dev sdi, sector 336

[21055.204222] sd 11:0:0:1: [sdj] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY

[21055.204228] end_request: I/O error, dev sdj, sector 96

[21055.383960] sd 11:0:0:1: [sdj] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY




This last message gets repeated lots of times, and during transfers it seems to be issued continuously  and I suppose this is why the system is so slow because it is always retrying loads of times before a success.

Could someone please dig me out of this? I have found a number of similar threads including one or two on this forum but no real solution.

Thanks

Geoff

---

### Post by BigGeoff on 2010-04-04
Please someone, point me in the right direction.........

---

