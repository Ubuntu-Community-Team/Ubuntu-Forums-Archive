---
title: "Dell Precision m3800 wifi &quot;hardware disabled&quot;"
date: 2015-04-07
forum: Hardware
---

### Post by librarianbryan on 2015-04-07
Network applet lists wifi as "Hardware Disabled." If I go to Software & Updates > Additional Drivers it indicates "Broadcom Corporation: BCM4352 802.11ac Wireless Adapter. This device is using an alternative driver." The following option is checked "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)." If I run 
```

lspci -vvnn | grep -A 9 Network

```

I get: 
```

06:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at eca00000 (64-bit, non-prefetchable) [size=32K]
    Region 2: Memory at ec800000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: wl

```

1) Fn + PrtScr has no effect. There are not wireless options in the BIOS I can't find it. 

2) I have purged and reinstalled bcmwl-kernel-source to no effect.

3) When I run rfkill list I get:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: nfc0: NFC
    Soft blocked: no
    Hard blocked: no

```

So I run rfkill unblock 1 to no effect.

4) I have tried this to no effect:
```

cd /etc/modprobe.d/
mkdir tmp
mv iwlwifi.conf tmp

```

I have poked other around /etc/modprobe.d files to no effect. Any files I touched I changed back to their original state before trying something else. 

Any help would be much appreciated.

---

