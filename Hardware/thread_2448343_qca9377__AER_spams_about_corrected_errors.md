---
title: "qca9377 : AER spams about corrected errors"
date: 2020-08-06
forum: Hardware
---

### Post by logxx on 2020-08-06
So i've got a wifi+bluetooth card on my laptop (qca9377), but unless i have "pcie_aspm=off" in grub dmesg is full of messages about corrected pcie bus errors... Is there still no fixes besides workarounds like disabling pice_aspm or AER?

```

[ 1102.483805] pcieport 0000:00:01.7: AER: Corrected error received: 0000:00:01.0
[ 1102.483817] pcieport 0000:00:01.7: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)
[ 1102.483823] pcieport 0000:00:01.7: AER:   device [1022:15d3] error status/mask=00001000/00006000
[ 1102.483827] pcieport 0000:00:01.7: AER:    [12] Timeout 

```

lspci:
```

02:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)

```

---

