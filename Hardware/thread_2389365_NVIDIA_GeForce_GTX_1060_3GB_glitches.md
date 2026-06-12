---
title: "NVIDIA GeForce GTX 1060 3GB glitches"
date: 2018-04-16
forum: Hardware
---

### Post by mitja.felicijan on 2018-04-16
[LIST]
[*]I am having some major problems with NVIDIA GeForce GTX 1060 3GB graphics card.
[*]There is a possibility of a hardware failure because sometimes even bios logo is not displayed.
[*]I have taken card out of motherboard and reattached it and then sometimes it works longer before problems.
[*]Also I randomly get desktop freezes (I use Ubuntu 17.10 with XORG).
[/LIST]

Do you guys have any idea what would be a solution?

```
&#10140;  ~ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 3GB] (rev a1)

```

```
&#10140;  ~ modinfo nvidia_390 
filename:       /lib/modules/4.13.0-38-generic/updates/dkms/nvidia_390.ko
alias:          char-major-195-*
version:        390.25
supported:      external
license:        NVIDIA
srcversion:     B5B1CA3087B567ADFADC070
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        ipmi_msghandler
name:           nvidia
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_CheckPCIConfigSpace:int
parm:           NVreg_EnablePCIeGen3:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_TCEBypassMode:int
parm:           NVreg_UseThreadedInterrupts:int
parm:           NVreg_EnableStreamMemOPs:int
parm:           NVreg_EnableBacklightHandler:int
parm:           NVreg_EnableUserNUMAManagement:int
parm:           NVreg_EnableIBMNPURelaxedOrderingMode:int
parm:           NVreg_MemoryPoolSize:int
parm:           NVreg_IgnoreMMIOCheck:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RegistryDwordsPerDevice:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_AssignGpus:charp
```


[IMG]https://imgur.com/2agJQum[/IMG]

[IMG]https://imgur.com/d0CtR9j[/IMG]

---

