---
title: "ubuntu showing PCIe3.0 card is only running in PCIe1.0 mode (on PCIe2.0 Mainboard)..?"
date: 2018-02-08
forum: Hardware
---

### Post by SomeITGuy on 2018-02-08
[B]Hello,

I don't know why this happens OR if it is perhaps just ubuntu/Linux showing me a wrong info here - Perhaps someone can give me a hint :) :[/B]
**My problem is that Ubuntu ([SIZE=1]Kubuntu 17.10 exactly - should't matter for hardware detection & sys infos in terminal/bash[/SIZE]) is telling me that my PCIe 3.0 compatible graphics card (Radeon RX 480) is currently only working in PCIe generation 1.0 mode (not talking about lanes here - 16 lanes are used as it seems), on a Motherboard (ASRock 990FX Extreme 3, AM3+ with 990FX chipset of course) wich definitely supports PCIe gen 2.0... :(**

My power supply is strong enough (680W bequiet). I use the latest BIOS on my Motherboard, and in the BIOS/UEFI there is no option to select/force PCIe mode.
Of course I use the first PEG slot (2.0 16x), according to the mainboard manual. I also checked PCIe state while running Unigine benchmarks, so power saving/idling should not be the reason for "PCIe 1.0 only". Some kind of 'lane splitting/sharing' should not happen on this board (the reason I wanted a 990FX instead a 970 or something... ;) ).

I also tried to 'force' PCIe somehow in (K)ubuntu via software -> edited GRUB (and updated of course):
```
GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm.policy=performance amdgpu.pcie_gen2=1"
```
...but no change.

**I have three questions and hope somenone can help me :) :**

[B]1. Is it possible that this is a software configuration issue or bug in my system? Or could it be only a problem with/in the hardware itself?

2. Are there other methods than 'lspci' or 'dmidecode' to check PCIe state via software on ubuntu?

3. Could it be just ubuntu showing me a wrong info (and the card is running 2.0 as expected on this board)...? [/B]


**_This is what I did (beside editing GRUB as mentioned above):_**

```
sudo lspci -vv -s 01:00.0 | grep LnkSta

               LnkSta: Speed [COLOR=#ff0000]2.5GT/s[/COLOR], Width x16, TrErr- Train- SlotClk+
DLActive- BWMgmt- ABWMgmt-
                LnkSta2: Current De-emphasis Level: -3.5dB,
EqualizationComplete-, EqualizationPhase1-
```
2.5GT/s is the speed of PCIe 1.0 per lane.

As you can see, other devices are running in PCIe 2.0 mode it seems (USB 3.0/Type-C card in a 4x slot):
```
DLActive- BWMgmt- ABWMgmt-
                LnkSta: Speed [COLOR=#008000]5GT/s[/COLOR], Width x2, TrErr- Train- SlotClk+
DLActive- BWMgmt- ABWMgmt-
                LnkSta2: Current De-emphasis Level: -6dB,
EqualizationComplete-, EqualizationPhase1-
```
5GT/s is the speed of PCIe 2.0 per lane.

I've read that sudo dmidecode | grep "PCI" should also show the PCIe mode/generation, but this is not the case here:
```
sudo dmidecode | grep "PCI"
                PCI is supported
        Designation: PCI1
        Type: 32-bit PCI
        Designation: PCI2
        Type: 32-bit PCI
        Designation: PCIE1
        Type: x1 PCI Express
        Designation: PCIE2
        Type: x16 PCI Express
        Designation: PCIE3
        Type: x16 PCI Express
        Designation: PCIE4
        Type: x4 PCI Express
```

PCIe ASPM policy is always default, even after editing GRUB:
```
cat /sys/module/pcie_aspm/parameters/policy
[default] performance powersave powersupersave
```


Finally: I know that it does not make a huuuge difference performance wise, but it's still annoying anyway (and I simply don't geht the reason of "PCIe 1.0 only)... :(


[B]Thanks for any reply! :)
Best Regards,
SomeITGuy[/B]

---

