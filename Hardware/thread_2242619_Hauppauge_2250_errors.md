---
title: "Hauppauge 2250 errors"
date: 2014-09-02
forum: Hardware
---

### Post by chris-thelonghall on 2014-09-02
I am wit's end. Spent 8+ hours on this and still getting errors. The card works on my Windows 7 installation, but I want it on linux for my HTPC. Here's the result of dmseg:
```
chris@HTPC:~$ dmesg | grep saa7164
[   15.100541] saa7164 driver loaded
[   15.101391] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2200 [card=4,insmod option]
[   15.101395] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd800000
[   15.360444] saa7164_downloadfirmware() no first image
[   15.360458] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   17.539480] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   17.539485] saa7164_downloadfirmware() firmware loaded.
[   17.539495] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   17.539500] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   17.539502] saa7164_downloadfirmware() BSLSize = 0x0
[   17.539503] saa7164_downloadfirmware() Reserved = 0x0
[   17.539505] saa7164_downloadfirmware() Version = 0x1661c00
[   23.564017] saa7164_downloadimage() Image downloaded, booting...
[   23.668030] saa7164_downloadimage() Image booted successfully.
[   26.404028] saa7164_downloadimage() Image downloaded, booting...
[   28.172028] saa7164_downloadimage() Image booted successfully.
[   28.199488] saa7164_api_i2c_read() error, ret(1) = 0x13
[   28.458565] saa7164_api_i2c_read() error, ret(1) = 0x13
[   28.458581] saa7164_dvb_register() Frontend initialization failed
[   28.458583] saa7164_initdev() Failed to register dvb adapters on porta
[   28.459438] saa7164_api_i2c_read() error, ret(1) = 0x13
[   28.459443] saa7164_dvb_register() Frontend initialization failed
[   28.459445] saa7164_initdev() Failed to register dvb adapters on portb
[   28.459545] saa7164[0]: registered device video0 [mpeg]
[   28.695580] saa7164[0]: registered device video1 [mpeg]
[   28.907148] saa7164[0]: registered device vbi0 [vbi]
[   28.907242] saa7164[0]: registered device vbi1 [vbi]


```

Can anyone help me with the errors?

Thanks!

---

### Post by mikitz on 2014-09-16
This is the same issue as
[http://ubuntuforums.org/showthread.php?t=2241753&highlight=hauppauge+2250](http://ubuntuforums.org/showthread.php?t=2241753&highlight=hauppauge+2250)
and should probably be merged?

---

