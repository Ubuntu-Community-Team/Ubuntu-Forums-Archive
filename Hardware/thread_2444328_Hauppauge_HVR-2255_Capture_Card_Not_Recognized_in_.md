---
title: "Hauppauge HVR-2255 Capture Card Not Recognized in 20.04"
date: 2020-05-28
forum: Hardware
---

### Post by bilkay on 2020-05-28
This is a fresh installation of 20.04. I copied Hauppauge's firmware file to /lib/firmware, but it fails with the following:

```
May 28 10:56:10 Jupiter kernel: [   14.611442] saa7164 0000:04:00.0: enabling device (0000 -> 0002)
May 28 10:56:10 Jupiter kernel: [   14.611537] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=12,autodetected]
May 28 10:56:10 Jupiter kernel: [   14.611540] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 28, latency: 0, mmio: 0xfc400000
May 28 10:56:10 Jupiter kernel: [   14.822085] saa7164_downloadfirmware() no first image
May 28 10:56:10 Jupiter kernel: [   14.822097] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
May 28 10:56:10 Jupiter kernel: [   14.847408] saa7164 0000:04:00.0: Direct firmware load for NXP7164-2010-03-10.1.fw failed with error -2
May 28 10:56:10 Jupiter kernel: [   14.847411] saa7164_downloadfirmware() Upload failed. (file not found?)
May 28 10:56:10 Jupiter kernel: [   14.847414] Failed to boot firmware, no features registered
May 28 10:56:10 Jupiter kernel: [   14.847454] saa7164 driver loaded
```

This card worked in 14.04 and 16.04. I remember having to put in a 20 sec. delay for something, but I'll be damned if I remember how I did it, or if it solved this particular problem.

---

### Post by bilkay on 2020-05-28
Here's the relevant syslog entry in 16.04:

```
May 28 11:46:19 Jupiter kernel: [    5.169931] Linux video capture interface: v2.00
May 28 11:46:19 Jupiter kernel: [    5.182081] saa7164 driver loaded
May 28 11:46:19 Jupiter kernel: [    5.182217] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=12,autodetected]
May 28 11:46:19 Jupiter kernel: [    5.182221] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 28, latency: 0, mmio: 0xfc400000
May 28 11:46:19 Jupiter kernel: [    5.392108] saa7164_downloadfirmware() no first image
May 28 11:46:19 Jupiter kernel: [    5.392120] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
May 28 11:46:19 Jupiter kernel: [    5.479085] saa7164_downloadfirmware() firmware read 4019072 bytes.
May 28 11:46:19 Jupiter kernel: [    5.479087] saa7164_downloadfirmware() firmware loaded.
May 28 11:46:19 Jupiter kernel: [    5.479087] Firmware file header part 1:
May 28 11:46:19 Jupiter kernel: [    5.479087]  .FirmwareSize = 0x0
May 28 11:46:19 Jupiter kernel: [    5.479088]  .BSLSize = 0x0
May 28 11:46:19 Jupiter kernel: [    5.479088]  .Reserved = 0x3d538
May 28 11:46:19 Jupiter kernel: [    5.479088]  .Version = 0x3
May 28 11:46:19 Jupiter kernel: [    5.479089] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
May 28 11:46:19 Jupiter kernel: [    5.479095] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
May 28 11:46:19 Jupiter kernel: [    5.479095] saa7164_downloadfirmware() BSLSize = 0x0
May 28 11:46:19 Jupiter kernel: [    5.479096] saa7164_downloadfirmware() Reserved = 0x0
May 28 11:46:19 Jupiter kernel: [    5.479096] saa7164_downloadfirmware() Version = 0x1661c00
```

---

### Post by Yellow Pasque on 2020-05-28
Check permissions and filename capitalization:
```
sudo ls -la /lib/firmware/NXP7164-2010-03-10.1.fw
```

---

### Post by bilkay on 2020-05-28
That's not the problem, but looking at the directory listing, I noticed that the one I installed is different (size) from the one running under 16.04. I hope this solves it. Thanks for the tip.

---

