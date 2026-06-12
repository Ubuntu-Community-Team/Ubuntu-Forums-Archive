---
title: "Hauppauge WinTV-quadHD-DVB(885) (DVB-T/T2/C) Only two tuners detected"
date: 2022-11-05
forum: Hardware
---

### Post by PaulRSte on 2022-11-05
Following the upgrade (reinstallation) of Ubuntu 18.04 from 16.04 last year (early 2021) I have not been able to get the system to detect all four tuners. It worked fine on 16.04 (non-HWE kernel). The firmware was installed as per the Hauppauge support site at [https://www.hauppauge.com/pages/support/support_linux.html](https://www.hauppauge.com/pages/support/support_linux.html) using the version for HWE kernels, and the 2 tuners have worked fine with this. 
I gave up on it after a few months but on returning from holiday this year and having to fix an issue with mythtv no longer downloading the EIT program guide (UK over the air), I thought I might take a second look at this tuner issue.
Having checked on the linuxtv.org pages [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-quadHD_(DVB-T/T2/C)](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-quadHD_(DVB-T/T2/C)) and compared the sample Kernel Output with journalctl output on my system, the significant differences are as follows:-

1) Board Name  - linuxtv Hauppauge WinTV-QuadHD-DVB          my system Hauppauge WinTV-QuadHD-DVB(885)
2) Card Type     -     56                                                                               60
3) Model           -           166100                                                                        166200
4) Revision        -       B216                                                                            B416
5. Firmware    -     4.0.2 when card detected                                               4.0.11 when mythtv backend loaded


From the Kernel documentation, [https://docs.kernel.org/admin-guide/media/cx23885-cardlist.html](https://docs.kernel.org/admin-guide/media/cx23885-cardlist.html), Card Type 56 has two PCI subsystems assigned to it, 0070:6a28 and 0070:6b28. Card type 60 does not have any subsystem assigned to it. The first dual tuner does get assigned to 0070:6a28 however. The second dual tuner does not get detected.
Again from the Hauppauge support site [https://www.hauppauge.com.sg/pages/support/support_linux.html](https://www.hauppauge.com.sg/pages/support/support_linux.html), if you choose the Raspberry Pi option, it states that :-

Firmware install instructions for Starburst 2 (PCI-e, DVB-S/S2)
Note: "Starburst 2" (model 150300 or 150310) is a digital satellite (DVB-S / DVB-S2) PCI-e TV tuner. Its DVB-S/DVB-S2 tuner is identical to the satellite tuner part on the WinTV-HVR-5525. While the WinTV-HVR-5525 is fully supported since Linux kernel 4.1, Starburst 2 is not detected "out of the box". But making it work is easy. By adding a configuration file cx23885.conf, the linux kernel treats the card as a WinTV-HVR-5525. Tested in kernel 4.13.0-21-generic.

I therefore created  cx23885.conf in /etc/modprobe.d as per the instructions, but specifying card type 56, and rebooted. This made no difference, the card was still autodetected as type 60. I suspect the difference may be because the Starburst 2 does not get detected at all whereas my tuner is detected(?).

Can anyone help with this at all please? Selected output from my journalctl  below.

```
Oct 26 11:33:04 PVR-1 kernel: cx23885: cx23885 driver version 0.0.4 loaded
Oct 26 11:33:05 PVR-1 kernel: cx23885: CORE cx23885[0]: subsystem: 0070:6a28, board: Hauppauge WinTV-QuadHD-DVB(885) [card=60,autodetected]
Oct 26 11:33:05 PVR-1 kernel: tveeprom: Hauppauge model 166200, rev B4I6, serial# 4036013461
Oct 26 11:33:05 PVR-1 kernel: tveeprom: MAC address is 00:0d:fe:90:ad:95
Oct 26 11:33:05 PVR-1 kernel: tveeprom: tuner model is SiLabs Si2157 (idx 186, type 4)
Oct 26 11:33:05 PVR-1 kernel: tveeprom: TV standards ATSC/DVB Digital (eeprom 0x80)
Oct 26 11:33:05 PVR-1 kernel: tveeprom: audio processor is CX23885 (idx 39)
Oct 26 11:33:05 PVR-1 kernel: tveeprom: decoder processor is CX23885 (idx 33)
Oct 26 11:33:05 PVR-1 kernel: tveeprom: has no radio, has IR receiver, has no IR transmitter
Oct 26 11:33:05 PVR-1 kernel: cx23885: cx23885[0]: hauppauge eeprom: model=166200
Oct 26 11:33:05 PVR-1 kernel: cx23885: cx23885_dvb_register() allocating 1 frontend(s)
Oct 26 11:33:05 PVR-1 kernel: cx23885: cx23885[0]: cx23885 based dvb card
Oct 26 11:33:05 PVR-1 kernel: cx23885: dvb_register(): board=60 port=1
Oct 26 11:33:05 PVR-1 kernel: i2c i2c-12: Added multiplexed i2c bus 15
Oct 26 11:33:05 PVR-1 kernel: si2168 12-0064: Silicon Labs Si2168-B40 successfully identified
Oct 26 11:33:05 PVR-1 kernel: si2168 12-0064: firmware version: B 4.0.2
Oct 26 11:33:05 PVR-1 kernel: si2157 13-0060: Silicon Labs Si2157 successfully attached
Oct 26 11:33:05 PVR-1 kernel: dvbdev: DVB: registering new adapter (cx23885[0])
Oct 26 11:33:05 PVR-1 kernel: cx23885 0000:04:00.0: DVB: registering adapter 0 frontend 0 (Silicon Labs Si2168)...
Oct 26 11:33:05 PVR-1 kernel: cx23885: cx23885_dvb_register() allocating 1 frontend(s)
Oct 26 11:33:05 PVR-1 kernel: cx23885: cx23885[0]: cx23885 based dvb card
Oct 26 11:33:05 PVR-1 kernel: cx23885: dvb_register(): board=60 port=2
Oct 26 11:33:05 PVR-1 kernel: i2c i2c-12: Added multiplexed i2c bus 16
Oct 26 11:33:05 PVR-1 kernel: si2168 12-0066: Silicon Labs Si2168-B40 successfully identified
Oct 26 11:33:05 PVR-1 kernel: si2168 12-0066: firmware version: B 4.0.2
Oct 26 11:33:05 PVR-1 kernel: si2157 13-0062: Silicon Labs Si2157 successfully attached
Oct 26 11:33:05 PVR-1 kernel: dvbdev: DVB: registering new adapter (cx23885[0])
Oct 26 11:33:05 PVR-1 kernel: cx23885 0000:04:00.0: DVB: registering adapter 1 frontend 0 (Silicon Labs Si2168)...
Oct 26 11:33:05 PVR-1 kernel: cx23885: cx23885_dev_checkrevision() Hardware revision = 0xa5
Oct 26 11:33:05 PVR-1 kernel: cx23885: cx23885[0]/0: found at 0000:04:00.0, rev: 4, irq: 17, latency: 0, mmio: 0xfe800000

Oct 26 11:33:12 PVR-1 kernel: si2168 12-0064: firmware version: B 4.0.11
Oct 26 11:33:12 PVR-1 kernel: si2157 13-0060: found a 'Silicon Labs Si2157-A30 ROM 0x50'
Oct 26 11:33:12 PVR-1 kernel: si2157 13-0060: downloading firmware from file 'dvb-tuner-si2157-a30-01.fw'
```

---

