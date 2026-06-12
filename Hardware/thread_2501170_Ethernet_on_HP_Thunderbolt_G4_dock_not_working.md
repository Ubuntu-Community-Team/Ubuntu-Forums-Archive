---
title: "Ethernet on HP Thunderbolt G4 dock not working"
date: 2024-09-25
forum: Hardware
---

### Post by dgibbs7 on 2024-09-25
Folks:

I've got a HP Thunderbolt G4 dock attached to my Elitebook 840 G10.

Up until recently, everything was working fine.

Suddenly the ethernet port on the dock stopped working. 

This has happened a few times.

Previously I was able to restore the Ethernet port by running 


```

echo 1 > /sys/bus/pci/devices/0000\:2b\:00.0/remove
echo 1 > /sys/bus/pci/rescan

```

Now, however, when I do that ... this appears in the dmesg output:
```
[ 1083.974094] pci 0000:2b:00.0: [8086:5502] type 00 class 0x020000 PCIe Endpoint
[ 1083.974148] pci 0000:2b:00.0: BAR 0 [mem 0x00000000-0x000fffff]
[ 1083.974206] pci 0000:2b:00.0: BAR 3 [mem 0x00000000-0x00003fff]
[ 1083.974547] pci 0000:2b:00.0: PME# supported from D0 D3hot D3cold
[ 1083.974973] pci 0000:2b:00.0: Adding to iommu group 23
[ 1083.975453] pci 0000:2b:00.0: BAR 0 [mem size 0x00100000]: can't assign; no space
[ 1083.975458] pci 0000:2b:00.0: BAR 0 [mem size 0x00100000]: failed to assign
[ 1083.975461] pci 0000:2b:00.0: BAR 3 [mem size 0x00004000]: can't assign; no space
[ 1083.975463] pci 0000:2b:00.0: BAR 3 [mem size 0x00004000]: failed to assign
[ 1083.975908] igc 0000:2b:00.0: PTM enabled, 4ns granularity
[ 1083.976320] igc: probe of 0000:2b:00.0 failed with error -5

```

I've also seen this in syslog ...
```

igc 0000:2b:00.0 (unnamed net_device) (uninitialized): PCIe link lost, device now detached

```

and this
```

igc: probe of 0000:2b:00.0 failed with error -13

```

I KNOW the ethernet on the dock works. When I attach my macbook to the dock the ethernet works fine.

Based on some forum posts elsewhere, I added "pcie_aspm=off pcie_port_pm=off" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, but it doesn't seem to have made a difference.

I know the dock supports linux. HP even states it here: [https://support.hp.com/us-en/document/ish_6213504-6213991-16](https://support.hp.com/us-en/document/ish_6213504-6213991-16)

As a workaround, I attached a usb c ethernet adapter to the dock and that's working fine.

Any suggestions on where I can look to resolve this issue.

---

### Post by dgibbs7 on 2024-09-27
Solved my own problem.

Looks like the modules were screwed up on the last kernel update,

I reinstalled the modules using ...

```
sudo apt --reinstall install linux-modules-extra-$(uname -r)
```


... rebooted and it worked correctly.

---

