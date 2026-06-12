---
title: "Disable HW wifi decryption, swcrypto=1 not working"
date: 2012-05-16
forum: Hardware
---

### Post by Saiot on 2012-05-16
Hi, 

i need to disable hw decryption on my intel wifi card, but using 
```

sudo rmmod iwlagn
sudo modprobe iwlagn swcrypto=1
```
it doesn't work (wireshark still sees my wpa2-encrypted traffic in clear)

my wifi card in accord to 
```
lspci -vv
```
is the following
```

02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 42
Region 0: Memory at f4c00000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: iwlagn
Kernel modules: iwlagn
```

(I know it's a strange question, but I need this in order to sniff my own encrypted traffic for a project,and i don't need unencrypted traffic)

Thanks a lot!

---

