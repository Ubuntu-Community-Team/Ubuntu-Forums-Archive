---
title: "Thinkpad T41: DVD drive can't play DVDs"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by artifactone on 2007-01-19
Hi.

I can't seem to play DVDs on my IBM Thinkpad T41. CD's can be read fine, I
can even access the 'data' section of the DVD (the .vob files etc.) but can't
actually watch the video.

I'm running the most recent stable release of Xubuntu.

I see errors like this in dmesg when trying to play a DVD:

```

[17179729.028000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17179729.028000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179729.028000] ide: failed opcode was: unknown
[17179729.028000] end_request: I/O error, dev hdc, sector 522752
[17179729.036000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17179729.036000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179729.036000] ide: failed opcode was: unknown
[17179729.036000] end_request: I/O error, dev hdc, sector 522736
[17179729.040000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17179729.040000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179729.040000] ide: failed opcode was: unknown
[17179729.040000] end_request: I/O error, dev hdc, sector 522736
[17179733.376000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17179733.376000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179733.376000] ide: failed opcode was: unknown
[17179733.376000] end_request: I/O error, dev hdc, sector 522736
[17179733.376000] printk: 60 messages suppressed.
[17179733.376000] Buffer I/O error on device hdc, logical block 130684
[17179733.380000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17179733.380000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179733.380000] ide: failed opcode was: unknown
[17179733.380000] end_request: I/O error, dev hdc, sector 522736

```

Any ideas?

---

