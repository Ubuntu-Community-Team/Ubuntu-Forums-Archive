---
title: "How to know my AMD Graphic Card"
date: 2017-12-24
forum: Hardware
---

### Post by augusto-pedraza08 on 2017-12-24
I bought a new Dell Inspiron 5567 to an external provider and I would like to know my graphic card, because my provider sell me an **AMD Radeon R7 M445 - 4 GB GDDR5 SDRAM **but my os says: **Radeon R7 M260/M265**[COLOR=#666666][FONT=&amp]
[/FONT][/COLOR]
I ran the command:

```
lspci -k | grep -EA3 'VGA|3D|Display'
```

getting the following result

```
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
    DeviceName:  Onboard IGD
    Subsystem: Dell Device 0767
    Kernel driver in use: i915
--
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] (rev c3)
    Subsystem: Dell Topaz XT [Radeon R7 M260/M265]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

```

Thanks in advance!!!

---

### Post by Yellow Pasque on 2017-12-24
It looks like they share a similar core and the same PCI ID: [https://pci-ids.ucw.cz/read/PC/1002/6900](https://pci-ids.ucw.cz/read/PC/1002/6900)

Run this and then look at lspci again:
```
sudo update-pciids
```

---

### Post by DuckHook on 2017-12-24
Welcome to the forums, augusto-pedraza08.

lspci reports data from /proc/bus/pci which in turn pulls the ID from the card itself. The ID is returned as a hex string pair and can be seen using the -n switch:```
lspci -n | egrep -iA10 'vga|3D|display'
```In my case, the ID string is:```
[1002:679a]
```

The OS then converts this hex pair into a readable description by looking up the hex ID from a system database. If the database is out of date or wrong, then your description will also be wrong. But the important info is the hex pair string and this can be googled online to confirm your card.

What does it say on your card? The model of card is usually stamped on the card itself. It is even possible to see the info etched onto the GPU, though you may need the right light angle and a magnifying glass.

EDIT

Ninja'd by Temüjin

---

