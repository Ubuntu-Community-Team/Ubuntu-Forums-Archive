---
title: "Optiarc  DVD RW AD-7203A  1.09"
date: 2009-01-17
forum: Hardware
---

### Post by Jan Beranek on 2009-01-17
Hello All,
I just bought my new CD/DVD drive, type Sony Optiarc  DVD RW AD-7203A  fw 1.09. It is connected via IDE/USB converter and connected with standard (shielded and short) cables to USB 2.0 integrated on my desktop motherboard.

When I read standard CD (audio or data - it does not matter) everything works fine - audio rip si perfectly clear and fast, CD data copy also ok.

Problems start when I insert DVD (video or data, problems are the same). Directory listing works, but if I try to read any data from DVD (yes, I tried many DVD - some of them were just new and not dirty or scratched) I got this messages in dmesg log:

[11153.892078] usb 5-1: new high speed USB device using ehci_hcd and address 7
[11154.089560] usb 5-1: configuration #1 chosen from 1 choice
[11154.090411] scsi6 : SCSI emulation for USB Mass Storage devices
[11154.095696] usb-storage: device found at 7
[11154.095704] usb-storage: waiting for device to settle before scanning
[11159.092272] usb-storage: device scan complete
[11159.093998] scsi 6:0:0:0: CD-ROM            Optiarc  DVD RW AD-7203A  1.09 PQ: 0 ANSI: 0
[11159.101706] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[11159.104037] sr 6:0:0:0: Attached scsi CD-ROM sr0
[11159.105436] sr 6:0:0:0: Attached scsi generic sg6 type 5
[11159.441598] end_request: I/O error, dev sr0, sector 0
[11159.441612] __ratelimit: 10 callbacks suppressed
[11159.441617] Buffer I/O error on device sr0, logical block 0
[11159.441629] Buffer I/O error on device sr0, logical block 1
[11159.441634] Buffer I/O error on device sr0, logical block 2
[11159.441639] Buffer I/O error on device sr0, logical block 3
[11159.445725] end_request: I/O error, dev sr0, sector 0
[11159.445734] Buffer I/O error on device sr0, logical block 0
[11159.868861] end_request: I/O error, dev sr0, sector 0
[11159.868875] Buffer I/O error on device sr0, logical block 0
[11159.868889] Buffer I/O error on device sr0, logical block 1
... etc ...

I looked for solution, I did not find any helpful post here. I tried options libata dma=1 in modprobe.d/options, other IDE/USB converter - but I did not find any difference.

My system is:
uname -a
Linux jenda-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

System:
Core2DUo with Intel 945 (mobile) chipset.

CD is working without problems, but DVD without chance. Strange...

Can anybody help me?
Regards

Jan

Edit: DVD-RAM works without any problems. Ideas?

---

