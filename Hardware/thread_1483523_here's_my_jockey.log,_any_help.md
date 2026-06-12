---
title: "here's my jockey.log, any help"
date: 2010-05-14
forum: Hardware
---

### Post by 3177 on 2010-05-14
i've been having trouble with my broadcom wireless card. When I go to hardware drivers, it give me the proprietary driver option, but upon clicking activate, it says it failed and refer to my jockey.log file. I don't understand what to do with what it says. [PHP]2010-05-14 14:13:47,405 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac>
2010-05-14 14:13:47,407 DEBUG: reading modalias file /lib/modules/2.6.32-22-generic/modules.alias
2010-05-14 14:13:47,573 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-14 14:13:47,583 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-14 14:13:47,644 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-14 14:13:47,663 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-14 14:13:47,680 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-14 14:13:47,697 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-14 14:13:47,714 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-14 14:13:48,038 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-14 14:13:48,069 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-14 14:13:48,128 DEBUG: Software modem not available
2010-05-14 14:13:48,129 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-14 14:13:48,176 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:13:48,193 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-14 14:13:48,194 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-14 14:13:48,194 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-14 14:13:48,257 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-14 14:13:48,258 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-14 14:13:48,289 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-14 14:13:48,290 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-14 14:13:48,290 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-14 14:13:48,357 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-14 14:13:48,358 DEBUG: Firmware for DVB cards not available
2010-05-14 14:13:48,358 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-14 14:13:48,435 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-14 14:13:48,436 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-14 14:13:48,444 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-14 14:13:48,445 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-14 14:13:48,452 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-14 14:13:48,453 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-14 14:13:48,462 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:13:48,465 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-14 14:13:48,466 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-14 14:13:48,475 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:13:48,476 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-14 14:13:48,481 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-14 14:13:48,481 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-14 14:13:48,490 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:13:48,490 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-14 14:13:48,496 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-14 14:13:48,496 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-14 14:13:48,496 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-14 14:13:48,497 DEBUG: all custom handlers loaded
2010-05-14 14:13:48,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Dbc03sc80i00')
2010-05-14 14:13:48,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-14 14:13:49,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Dbc08sc05i00')
2010-05-14 14:13:49,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-14 14:13:49,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-14 14:13:49,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-14 14:13:49,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-05-14 14:13:49,064 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'platform:acer-wmi')
2010-05-14 14:13:49,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:13:49,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00001180d00000843sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:13:49,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ricoh_mmc', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-14 14:13:49,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-14 14:13:49,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:13:49,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-14 14:13:49,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Dbc02sc00i00')
2010-05-14 14:13:49,148 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'platform:regulatory')
2010-05-14 14:13:49,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Dbc0Csc00i10')
2010-05-14 14:13:49,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Dbc06sc00i00')
2010-05-14 14:13:49,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-14 14:13:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-14 14:13:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Dbc03sc00i00')
2010-05-14 14:13:49,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:device:')
2010-05-14 14:13:49,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:SYN1B01:SYN1B00:SYN0002:PNP0F13:')
2010-05-14 14:13:49,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-14 14:13:49,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-14 14:13:49,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Dbc0Csc05i00')
2010-05-14 14:13:49,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:13:49,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:13:49,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-14 14:13:49,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-14 14:13:49,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-14 14:13:49,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'dmi:bvnAcer:bvrv1.3808:bd02/18/2008:svnAcer,inc.:pnAspire4720Z:pvrNotApplicable:rvnAcer,Inc.:rnNestos:rvrNotApplicable:cvnAcer,Inc.:ct1:cvrN/A:')
2010-05-14 14:13:49,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-14 14:13:49,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-14 14:13:49,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:13:49,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:13:49,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:WEC1020:')
2010-05-14 14:13:49,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-14 14:13:49,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,193 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Dbc04sc03i00')
2010-05-14 14:13:49,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'platform:pcspkr')
2010-05-14 14:13:49,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-05-14 14:13:49,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-14 14:13:49,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2010-05-14 14:13:49,203 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,206 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:13:49,207 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:13:49,207 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-14 14:13:49,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'platform:eisa')
2010-05-14 14:13:49,208 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Dbc06sc01i00')
2010-05-14 14:13:49,212 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-14 14:13:49,225 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,225 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'input:b0011v0002p0007e81B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-14 14:13:49,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:13:49,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x93b6bac> about HardwareID('modalias', 'acpi:INT0800:')
2010-05-14 14:13:49,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Dbc03sc80i00')
2010-05-14 14:13:49,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-14 14:13:49,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Dbc08sc05i00')
2010-05-14 14:13:49,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-14 14:13:49,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-14 14:13:49,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-14 14:13:49,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-05-14 14:13:49,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'platform:acer-wmi')
2010-05-14 14:13:49,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:13:49,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00001180d00000843sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:13:49,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-14 14:13:49,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-14 14:13:49,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:13:49,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-14 14:13:49,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Dbc02sc00i00')
2010-05-14 14:13:49,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'platform:regulatory')
2010-05-14 14:13:49,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Dbc0Csc00i10')
2010-05-14 14:13:49,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Dbc06sc00i00')
2010-05-14 14:13:49,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-14 14:13:49,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-14 14:13:49,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Dbc03sc00i00')
2010-05-14 14:13:49,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:device:')
2010-05-14 14:13:49,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:SYN1B01:SYN1B00:SYN0002:PNP0F13:')
2010-05-14 14:13:49,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-14 14:13:49,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-14 14:13:49,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Dbc0Csc05i00')
2010-05-14 14:13:49,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:13:49,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:13:49,238 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-14 14:13:49,238 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-14 14:13:49,238 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-14 14:13:49,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'dmi:bvnAcer:bvrv1.3808:bd02/18/2008:svnAcer,inc.:pnAspire4720Z:pvrNotApplicable:rvnAcer,Inc.:rnNestos:rvrNotApplicable:cvnAcer,Inc.:ct1:cvrN/A:')
2010-05-14 14:13:49,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-14 14:13:49,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-14 14:13:49,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:13:49,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:13:49,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:WEC1020:')
2010-05-14 14:13:49,240 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-14 14:13:49,240 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,240 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,240 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,240 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Dbc04sc03i00')
2010-05-14 14:13:49,241 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-14 14:13:49,241 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-05-14 14:13:49,241 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-14 14:13:49,241 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2010-05-14 14:13:49,241 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'platform:eisa')
2010-05-14 14:13:49,241 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Dbc06sc01i00')
2010-05-14 14:13:49,241 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-14 14:13:49,241 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:13:49,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'input:b0011v0002p0007e81B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-14 14:13:49,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x975294c> about HardwareID('modalias', 'acpi:INT0800:')
2010-05-14 14:13:49,291 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:13:49,380 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:13:49,454 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:13:54,794 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:14:03,122 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:14:09,420 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:14:09,420 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-14 14:14:09,465 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:14:13,995 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:14:14,024 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:14:14,077 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:17:27,857 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:17:32,464 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:17:32,732 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:17:32,733 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-14 14:17:32,798 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:17:35,284 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:17:35,314 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:17:35,368 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:29:53,978 DEBUG: Shutting down
2010-05-14 14:38:47,997 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc>
2010-05-14 14:38:47,999 DEBUG: reading modalias file /lib/modules/2.6.32-22-generic/modules.alias
2010-05-14 14:38:48,140 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-14 14:38:48,140 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-14 14:38:48,176 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-14 14:38:48,178 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-14 14:38:48,180 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-14 14:38:48,182 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-14 14:38:48,186 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-14 14:38:48,505 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-14 14:38:48,516 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-14 14:38:48,527 DEBUG: Software modem not available
2010-05-14 14:38:48,527 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-14 14:38:48,532 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:38:48,542 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-14 14:38:48,543 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-14 14:38:48,543 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-14 14:38:48,558 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-14 14:38:48,559 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-14 14:38:48,564 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-14 14:38:48,565 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-14 14:38:48,565 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-14 14:38:48,581 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-14 14:38:48,581 DEBUG: Firmware for DVB cards not available
2010-05-14 14:38:48,581 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-14 14:38:48,588 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-14 14:38:48,588 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-14 14:38:48,597 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-14 14:38:48,598 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-14 14:38:48,605 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-14 14:38:48,606 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-14 14:38:48,615 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:38:48,619 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-14 14:38:48,620 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-14 14:38:48,631 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:38:48,631 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-14 14:38:48,636 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-14 14:38:48,636 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-14 14:38:48,646 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:38:48,646 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-14 14:38:48,651 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-14 14:38:48,652 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-14 14:38:48,652 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-14 14:38:48,652 DEBUG: all custom handlers loaded
2010-05-14 14:38:48,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Dbc03sc80i00')
2010-05-14 14:38:48,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-14 14:38:49,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Dbc08sc05i00')
2010-05-14 14:38:49,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-14 14:38:49,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-14 14:38:49,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-14 14:38:49,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-05-14 14:38:49,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'platform:acer-wmi')
2010-05-14 14:38:49,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:38:49,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00001180d00000843sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:38:49,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ricoh_mmc', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-14 14:38:49,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-14 14:38:49,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:38:49,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-14 14:38:49,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Dbc02sc00i00')
2010-05-14 14:38:49,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'platform:regulatory')
2010-05-14 14:38:49,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Dbc0Csc00i10')
2010-05-14 14:38:49,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Dbc06sc00i00')
2010-05-14 14:38:49,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-14 14:38:49,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-14 14:38:49,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Dbc03sc00i00')
2010-05-14 14:38:49,231 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,231 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:device:')
2010-05-14 14:38:49,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:SYN1B01:SYN1B00:SYN0002:PNP0F13:')
2010-05-14 14:38:49,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-14 14:38:49,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-14 14:38:49,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Dbc06sc01i00')
2010-05-14 14:38:49,236 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,236 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:38:49,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:38:49,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-14 14:38:49,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-14 14:38:49,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-14 14:38:49,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'dmi:bvnAcer:bvrv1.3808:bd02/18/2008:svnAcer,inc.:pnAspire4720Z:pvrNotApplicable:rvnAcer,Inc.:rnNestos:rvrNotApplicable:cvnAcer,Inc.:ct1:cvrN/A:')
2010-05-14 14:38:49,260 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-14 14:38:49,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-14 14:38:49,260 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:38:49,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'usb:v050Dp705Cd4810dcFFdscFFdpFFicFFisc00ip00')
2010-05-14 14:38:49,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'zd1211rw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:WEC1020:')
2010-05-14 14:38:49,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-14 14:38:49,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Dbc0Csc05i00')
2010-05-14 14:38:49,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Dbc04sc03i00')
2010-05-14 14:38:49,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'platform:pcspkr')
2010-05-14 14:38:49,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-05-14 14:38:49,297 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-14 14:38:49,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2010-05-14 14:38:49,298 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,302 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:38:49,303 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:38:49,302 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-14 14:38:49,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'platform:eisa')
2010-05-14 14:38:49,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:38:49,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-14 14:38:49,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'input:b0011v0002p0007e81B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-14 14:38:49,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:38:49,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x992dbcc> about HardwareID('modalias', 'acpi:INT0800:')
2010-05-14 14:38:49,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Dbc03sc80i00')
2010-05-14 14:38:49,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-14 14:38:49,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Dbc08sc05i00')
2010-05-14 14:38:49,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-14 14:38:49,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-14 14:38:49,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-14 14:38:49,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-05-14 14:38:49,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'platform:acer-wmi')
2010-05-14 14:38:49,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:38:49,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00001180d00000843sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:38:49,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-14 14:38:49,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-14 14:38:49,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:38:49,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-14 14:38:49,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Dbc02sc00i00')
2010-05-14 14:38:49,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'platform:regulatory')
2010-05-14 14:38:49,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Dbc0Csc00i10')
2010-05-14 14:38:49,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Dbc06sc00i00')
2010-05-14 14:38:49,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-14 14:38:49,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-14 14:38:49,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Dbc03sc00i00')
2010-05-14 14:38:49,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:device:')
2010-05-14 14:38:49,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:SYN1B01:SYN1B00:SYN0002:PNP0F13:')
2010-05-14 14:38:49,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-14 14:38:49,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-14 14:38:49,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Dbc06sc01i00')
2010-05-14 14:38:49,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:38:49,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:38:49,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-14 14:38:49,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-14 14:38:49,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-14 14:38:49,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'dmi:bvnAcer:bvrv1.3808:bd02/18/2008:svnAcer,inc.:pnAspire4720Z:pvrNotApplicable:rvnAcer,Inc.:rnNestos:rvrNotApplicable:cvnAcer,Inc.:ct1:cvrN/A:')
2010-05-14 14:38:49,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-14 14:38:49,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-14 14:38:49,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:38:49,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'usb:v050Dp705Cd4810dcFFdscFFdpFFicFFisc00ip00')
2010-05-14 14:38:49,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:WEC1020:')
2010-05-14 14:38:49,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-14 14:38:49,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Dbc0Csc05i00')
2010-05-14 14:38:49,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Dbc04sc03i00')
2010-05-14 14:38:49,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-14 14:38:49,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-05-14 14:38:49,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-14 14:38:49,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2010-05-14 14:38:49,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'platform:eisa')
2010-05-14 14:38:49,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:38:49,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-14 14:38:49,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:38:49,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'input:b0011v0002p0007e81B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-14 14:38:49,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ce196c> about HardwareID('modalias', 'acpi:INT0800:')
2010-05-14 14:38:49,390 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:38:49,444 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:38:49,512 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:38:54,314 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:38:55,694 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:38:59,932 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:38:59,933 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-14 14:38:59,990 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:39:02,979 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:39:03,009 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:39:03,064 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:39:05,859 DEBUG: Shutting down
2010-05-14 14:48:12,048 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac>
2010-05-14 14:48:12,051 DEBUG: reading modalias file /lib/modules/2.6.32-22-generic/modules.alias
2010-05-14 14:48:12,181 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-14 14:48:12,181 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-14 14:48:12,217 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-14 14:48:12,219 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-14 14:48:12,221 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-14 14:48:12,223 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-14 14:48:12,227 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-14 14:48:12,541 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-14 14:48:12,551 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-14 14:48:12,562 DEBUG: Software modem not available
2010-05-14 14:48:12,562 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-14 14:48:12,567 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:48:12,576 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-14 14:48:12,577 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-14 14:48:12,577 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-14 14:48:12,592 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-14 14:48:12,592 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-14 14:48:12,597 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-14 14:48:12,598 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-14 14:48:12,598 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-14 14:48:12,612 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-14 14:48:12,613 DEBUG: Firmware for DVB cards not available
2010-05-14 14:48:12,613 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-14 14:48:12,619 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-14 14:48:12,619 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-14 14:48:12,628 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-14 14:48:12,628 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-14 14:48:12,635 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-14 14:48:12,636 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-14 14:48:12,645 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:48:12,649 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-14 14:48:12,649 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-14 14:48:12,662 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:48:12,663 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-14 14:48:12,667 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-14 14:48:12,668 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-14 14:48:12,677 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:48:12,677 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-14 14:48:12,682 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-14 14:48:12,683 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-14 14:48:12,683 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-14 14:48:12,683 DEBUG: all custom handlers loaded
2010-05-14 14:48:12,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Dbc03sc80i00')
2010-05-14 14:48:12,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-14 14:48:13,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Dbc08sc05i00')
2010-05-14 14:48:13,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-14 14:48:13,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-14 14:48:13,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-14 14:48:13,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-05-14 14:48:13,126 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'platform:acer-wmi')
2010-05-14 14:48:13,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:48:13,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00001180d00000843sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:48:13,155 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ricoh_mmc', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-14 14:48:13,155 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-14 14:48:13,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:48:13,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-14 14:48:13,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Dbc02sc00i00')
2010-05-14 14:48:13,210 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'platform:regulatory')
2010-05-14 14:48:13,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Dbc0Csc00i10')
2010-05-14 14:48:13,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Dbc06sc00i00')
2010-05-14 14:48:13,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-14 14:48:13,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-14 14:48:13,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Dbc03sc00i00')
2010-05-14 14:48:13,219 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,219 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:device:')
2010-05-14 14:48:13,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:SYN1B01:SYN1B00:SYN0002:PNP0F13:')
2010-05-14 14:48:13,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-14 14:48:13,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-14 14:48:13,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Dbc0Csc05i00')
2010-05-14 14:48:13,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:48:13,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:48:13,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-14 14:48:13,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-14 14:48:13,231 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-14 14:48:13,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'dmi:bvnAcer:bvrv1.3808:bd02/18/2008:svnAcer,inc.:pnAspire4720Z:pvrNotApplicable:rvnAcer,Inc.:rnNestos:rvrNotApplicable:cvnAcer,Inc.:ct1:cvrN/A:')
2010-05-14 14:48:13,246 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-14 14:48:13,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-14 14:48:13,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:48:13,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:48:13,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:WEC1020:')
2010-05-14 14:48:13,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-14 14:48:13,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Dbc04sc03i00')
2010-05-14 14:48:13,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'platform:pcspkr')
2010-05-14 14:48:13,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-05-14 14:48:13,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-14 14:48:13,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2010-05-14 14:48:13,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,271 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:48:13,272 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:13,272 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-14 14:48:13,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'platform:eisa')
2010-05-14 14:48:13,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Dbc06sc01i00')
2010-05-14 14:48:13,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-14 14:48:13,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'input:b0011v0002p0007e81B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-14 14:48:13,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:48:13,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0d7bac> about HardwareID('modalias', 'acpi:INT0800:')
2010-05-14 14:48:13,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Dbc03sc80i00')
2010-05-14 14:48:13,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-14 14:48:13,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Dbc08sc05i00')
2010-05-14 14:48:13,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-14 14:48:13,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-14 14:48:13,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-14 14:48:13,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-05-14 14:48:13,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'platform:acer-wmi')
2010-05-14 14:48:13,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:48:13,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00001180d00000843sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:48:13,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-14 14:48:13,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-14 14:48:13,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:48:13,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-14 14:48:13,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Dbc02sc00i00')
2010-05-14 14:48:13,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'platform:regulatory')
2010-05-14 14:48:13,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Dbc0Csc00i10')
2010-05-14 14:48:13,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Dbc06sc00i00')
2010-05-14 14:48:13,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-14 14:48:13,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-14 14:48:13,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Dbc03sc00i00')
2010-05-14 14:48:13,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:device:')
2010-05-14 14:48:13,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:SYN1B01:SYN1B00:SYN0002:PNP0F13:')
2010-05-14 14:48:13,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-14 14:48:13,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-14 14:48:13,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Dbc0Csc05i00')
2010-05-14 14:48:13,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:48:13,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:48:13,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-14 14:48:13,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-14 14:48:13,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-14 14:48:13,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'dmi:bvnAcer:bvrv1.3808:bd02/18/2008:svnAcer,inc.:pnAspire4720Z:pvrNotApplicable:rvnAcer,Inc.:rnNestos:rvrNotApplicable:cvnAcer,Inc.:ct1:cvrN/A:')
2010-05-14 14:48:13,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-14 14:48:13,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-14 14:48:13,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:48:13,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:48:13,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:WEC1020:')
2010-05-14 14:48:13,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-14 14:48:13,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Dbc04sc03i00')
2010-05-14 14:48:13,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-14 14:48:13,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-05-14 14:48:13,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-14 14:48:13,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2010-05-14 14:48:13,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'platform:eisa')
2010-05-14 14:48:13,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Dbc06sc01i00')
2010-05-14 14:48:13,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-14 14:48:13,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:48:13,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'input:b0011v0002p0007e81B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-14 14:48:13,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47394c> about HardwareID('modalias', 'acpi:INT0800:')
2010-05-14 14:48:13,687 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:13,720 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:13,747 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:13,788 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:13,858 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:13,903 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:26,494 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:30,798 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:48:30,799 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-14 14:48:30,856 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:35,519 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:35,549 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:48:35,604 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:51:49,848 DEBUG: Shutting down
2010-05-14 14:52:08,737 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac>
2010-05-14 14:52:08,741 DEBUG: reading modalias file /lib/modules/2.6.32-22-generic/modules.alias
2010-05-14 14:52:08,877 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-14 14:52:08,878 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-14 14:52:08,914 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-14 14:52:08,916 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-14 14:52:08,919 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-14 14:52:08,920 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-14 14:52:08,924 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-14 14:52:09,237 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-14 14:52:09,251 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-14 14:52:09,261 DEBUG: Software modem not available
2010-05-14 14:52:09,262 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-14 14:52:09,267 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:52:09,276 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-14 14:52:09,276 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-14 14:52:09,276 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-14 14:52:09,292 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-14 14:52:09,292 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-14 14:52:09,298 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-14 14:52:09,298 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-14 14:52:09,298 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-14 14:52:09,313 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-14 14:52:09,314 DEBUG: Firmware for DVB cards not available
2010-05-14 14:52:09,314 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-14 14:52:09,320 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-14 14:52:09,320 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-14 14:52:09,330 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-14 14:52:09,330 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-14 14:52:09,337 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-14 14:52:09,337 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-14 14:52:09,346 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:52:09,351 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-14 14:52:09,351 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-14 14:52:09,362 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:52:09,363 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-14 14:52:09,368 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-14 14:52:09,368 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-14 14:52:09,378 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-14 14:52:09,379 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-14 14:52:09,385 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-14 14:52:09,385 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-14 14:52:09,386 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-14 14:52:09,386 DEBUG: all custom handlers loaded
2010-05-14 14:52:09,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Dbc03sc80i00')
2010-05-14 14:52:09,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-14 14:52:09,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Dbc08sc05i00')
2010-05-14 14:52:09,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-14 14:52:09,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-14 14:52:09,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-14 14:52:09,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-05-14 14:52:09,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'platform:acer-wmi')
2010-05-14 14:52:09,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:52:09,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00001180d00000843sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:52:09,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ricoh_mmc', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-14 14:52:09,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-14 14:52:09,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:52:09,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-14 14:52:09,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Dbc02sc00i00')
2010-05-14 14:52:09,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'platform:regulatory')
2010-05-14 14:52:09,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Dbc0Csc00i10')
2010-05-14 14:52:09,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Dbc06sc00i00')
2010-05-14 14:52:09,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-14 14:52:09,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-14 14:52:09,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Dbc03sc00i00')
2010-05-14 14:52:09,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:device:')
2010-05-14 14:52:09,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:SYN1B01:SYN1B00:SYN0002:PNP0F13:')
2010-05-14 14:52:09,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-14 14:52:09,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-14 14:52:09,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Dbc0Csc05i00')
2010-05-14 14:52:09,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:52:09,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:52:09,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-14 14:52:09,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-14 14:52:09,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-14 14:52:09,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'dmi:bvnAcer:bvrv1.3808:bd02/18/2008:svnAcer,inc.:pnAspire4720Z:pvrNotApplicable:rvnAcer,Inc.:rnNestos:rvrNotApplicable:cvnAcer,Inc.:ct1:cvrN/A:')
2010-05-14 14:52:09,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-14 14:52:09,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-14 14:52:09,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:52:09,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:52:09,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:WEC1020:')
2010-05-14 14:52:09,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-14 14:52:09,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Dbc04sc03i00')
2010-05-14 14:52:09,949 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'platform:pcspkr')
2010-05-14 14:52:09,950 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,950 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-05-14 14:52:09,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-14 14:52:09,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2010-05-14 14:52:09,952 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,956 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-14 14:52:09,957 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-14 14:52:09,957 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-14 14:52:09,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'platform:eisa')
2010-05-14 14:52:09,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Dbc06sc01i00')
2010-05-14 14:52:09,962 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-14 14:52:09,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'input:b0011v0002p0007e81B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-14 14:52:09,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,978 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,978 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-14 14:52:09,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f5dbac> about HardwareID('modalias', 'acpi:INT0800:')
2010-05-14 14:52:09,978 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Dbc03sc80i00')
2010-05-14 14:52:09,978 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-14 14:52:09,978 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Dbc08sc05i00')
2010-05-14 14:52:09,978 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-14 14:52:09,979 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-14 14:52:09,979 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-14 14:52:09,979 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,979 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-05-14 14:52:09,979 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'platform:acer-wmi')
2010-05-14 14:52:09,979 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:52:09,979 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00001180d00000843sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:52:09,979 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-14 14:52:09,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-14 14:52:09,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:52:09,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-14 14:52:09,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Dbc02sc00i00')
2010-05-14 14:52:09,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'platform:regulatory')
2010-05-14 14:52:09,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Dbc0Csc00i10')
2010-05-14 14:52:09,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Dbc06sc00i00')
2010-05-14 14:52:09,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-14 14:52:09,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-14 14:52:09,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Dbc03sc00i00')
2010-05-14 14:52:09,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:device:')
2010-05-14 14:52:09,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:SYN1B01:SYN1B00:SYN0002:PNP0F13:')
2010-05-14 14:52:09,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-14 14:52:09,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-14 14:52:09,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Dbc0Csc05i00')
2010-05-14 14:52:09,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:52:09,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Dbc0Csc03i20')
2010-05-14 14:52:09,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-14 14:52:09,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-14 14:52:09,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-14 14:52:09,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'dmi:bvnAcer:bvrv1.3808:bd02/18/2008:svnAcer,inc.:pnAspire4720Z:pvrNotApplicable:rvnAcer,Inc.:rnNestos:rvrNotApplicable:cvnAcer,Inc.:ct1:cvrN/A:')
2010-05-14 14:52:09,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-14 14:52:09,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-14 14:52:09,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-14 14:52:09,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Dbc08sc80i00')
2010-05-14 14:52:09,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:WEC1020:')
2010-05-14 14:52:09,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-14 14:52:09,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Dbc04sc03i00')
2010-05-14 14:52:09,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-14 14:52:09,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-05-14 14:52:09,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-14 14:52:09,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2010-05-14 14:52:09,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'platform:eisa')
2010-05-14 14:52:09,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Dbc06sc01i00')
2010-05-14 14:52:09,985 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-14 14:52:09,985 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Dbc0Csc03i00')
2010-05-14 14:52:09,985 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'input:b0011v0002p0007e81B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-14 14:52:09,985 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2f994c> about HardwareID('modalias', 'acpi:INT0800:')
[/PHP]

Any help would be greatly appreciated.

---

### Post by 3177 on 2010-05-16
found all the help I needed right here:[http://ubuntuforums.org/showthread.php?t=1369975](http://ubuntuforums.org/showthread.php?t=1369975)

---

