---
title: "poor signal on WiFi connection, Ubuntu 16.04 LTS, BCM43142"
date: 2017-06-05
forum: Hardware
---

### Post by amir-vxj on 2017-06-05
I have Ubuntu 16.04 and Windows 10 pro on my system HP Pavilion 15. on  both OS I had poor signal and very slow and unstable connection &  Internet speed on Wifi. on Windows with updating the Driver for Broadcom  802.11 it works perfect now. but still have the same issue on Ubuntu. as I am new to Ubuntu after installing the OS I did choose suggested additional driver at software&updates but still have poor signal, so I fallowed some posts about this issue for Broadcom chips. this is the detailed info of the WiFi card.
```
Network controller: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365](rev 01)
    DeviceName: Broadcom BCM43142 802.11bgn 1x1 WiFi Adapter + BT 4.0 combo adapter
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at b5500000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl
```

I also did ```
sudo apt-get remove --purge bcmwl-kernel-source
``` and re-installed it. Also I wanted to change driver with ```
sudo apt-get install broadcom-sta-dkms
``` after removing bcmwl but it says> * broadcom-sta-dkms is already the newest version (6.30.223.271-3~16.04.1)* but there is not enable WiFi option.

  is there any solution for this problem? changing to older/newer driver versions? removing this *proprietary* driver and replace by other (open source) drivers? I am new to Ubuntu and this packagings and repositories made me confused. Thanks.

---

