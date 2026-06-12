---
title: "Can't install Nvidia Drivers for GeForce 5200 in ubuntu 10.04 Beta 2"
date: 2010-04-10
forum: Hardware
---

### Post by Cfhs_1 on 2010-04-10
So I'm testing ubuntu 10.04 Beta 2 and submitting bugs to help out. I can't get very far on my second test machine thought because It won't let me install either of the Nvidia drivers. (version 173 or 96) Each time it fails telling me to look at the Jockey log file. 
Here is the output of that log:

```
2010-04-09 16:33:36,690 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c>
2010-04-09 16:33:36,693 DEBUG: reading modalias file /lib/modules/2.6.32-19-generic/modules.alias
2010-04-09 16:33:36,993 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-09 16:33:37,006 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-09 16:33:37,059 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-09 16:33:37,063 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-09 16:33:37,071 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-09 16:33:37,077 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-09 16:33:37,086 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-09 16:33:37,488 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-09 16:33:37,620 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-09 16:33:37,621 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-09 16:33:37,661 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-09 16:33:37,662 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-09 16:33:37,812 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-09 16:33:37,813 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-09 16:33:37,874 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-09 16:33:37,874 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-09 16:33:37,874 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-09 16:33:37,918 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-09 16:33:37,919 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-09 16:33:37,930 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 16:33:37,935 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-09 16:33:37,936 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-09 16:33:37,947 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 16:33:37,948 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-09 16:33:37,974 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-09 16:33:37,975 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-09 16:33:37,986 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 16:33:37,987 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-09 16:33:38,003 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-09 16:33:38,015 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-09 16:33:38,015 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-09 16:33:38,016 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-09 16:33:38,082 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-09 16:33:38,083 DEBUG: Firmware for DVB cards not available
2010-04-09 16:33:38,084 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-09 16:33:38,113 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-09 16:33:38,114 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-09 16:33:38,114 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-09 16:33:38,114 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-09 16:33:38,141 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-09 16:33:38,172 DEBUG: Software modem not available
2010-04-09 16:33:38,173 DEBUG: all custom handlers loaded
2010-04-09 16:33:38,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v000010DEd00000322sv000010DEsd000001B9bc03sc00i00')
2010-04-09 16:33:38,887 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-09 16:33:38,888 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 16:33:40,019 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-09 16:33:40,020 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 16:33:40,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:40,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:40,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:40,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001028sd00000174bc04sc01i00')
2010-04-09 16:33:41,134 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:device:')
2010-04-09 16:33:41,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-09 16:33:41,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-09 16:33:41,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'platform:eisa')
2010-04-09 16:33:41,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 16:33:41,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-09 16:33:41,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-09 16:33:41,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-09 16:33:41,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-09 16:33:41,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'platform:dcdbas')
2010-04-09 16:33:41,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001028sd00000174bc06sc00i00')
2010-04-09 16:33:41,210 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-09 16:33:41,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-09 16:33:41,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-09 16:33:41,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-09 16:33:41,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-09 16:33:41,218 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-09 16:33:41,218 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-09 16:33:41,218 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 16:33:41,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:33:41,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-09 16:33:41,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d000024D3sv00001028sd00000174bc0Csc05i00')
2010-04-09 16:33:41,250 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,2,4,11,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2010-04-09 16:33:41,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:33:41,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'dmi:bvnDellComputerCorporation:bvrA12:bd08/26/2004:svnDellComputerCorporation:pnDimension4600i:pvr:rvnDellComputerCorp.:rn0F4491:rvr:cvnDellComputerCorporation:ct6:cvr:')
2010-04-09 16:33:41,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-09 16:33:41,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Deskjet D2400 series;DES:D2445;CMD:LDL,DYN;')
2010-04-09 16:33:41,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip01')
2010-04-09 16:33:41,347 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip02')
2010-04-09 16:33:41,349 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-09 16:33:41,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-09 16:33:41,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-09 16:33:41,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,357 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Deskjet D2400 series;DES:Deskjet D2400 series;')
2010-04-09 16:33:41,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:33:41,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d00001050sv00001028sd00000174bc02sc00i00')
2010-04-09 16:33:41,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e100', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001028sd00000174bc0Csc03i00')
2010-04-09 16:33:41,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-09 16:33:41,377 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-09 16:33:41,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'usb:v03F0p7A04d0100dc00dsc00dp00ic07isc01ip02')
2010-04-09 16:33:41,407 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001028sd00000174bc0Csc03i20')
2010-04-09 16:33:41,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-09 16:33:41,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,415 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-09 16:33:41,416 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,416 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'pci:v0000100Bd00000020sv00001385sd0000F311bc02sc00i00')
2010-04-09 16:33:41,429 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'natsemi', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2010-04-09 16:33:41,430 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:33:41,430 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c4498c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-09 16:33:41,430 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v000010DEd00000322sv000010DEsd000001B9bc03sc00i00')
2010-04-09 16:33:41,430 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001028sd00000174bc04sc01i00')
2010-04-09 16:33:41,430 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:device:')
2010-04-09 16:33:41,431 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-09 16:33:41,431 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-09 16:33:41,431 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'platform:eisa')
2010-04-09 16:33:41,431 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 16:33:41,431 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-09 16:33:41,432 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-09 16:33:41,432 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-09 16:33:41,432 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-09 16:33:41,432 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'platform:dcdbas')
2010-04-09 16:33:41,432 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001028sd00000174bc06sc00i00')
2010-04-09 16:33:41,432 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-09 16:33:41,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-09 16:33:41,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-09 16:33:41,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-09 16:33:41,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-09 16:33:41,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-09 16:33:41,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-09 16:33:41,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 16:33:41,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:33:41,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-09 16:33:41,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d000024D3sv00001028sd00000174bc0Csc05i00')
2010-04-09 16:33:41,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,2,4,11,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2010-04-09 16:33:41,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:33:41,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'dmi:bvnDellComputerCorporation:bvrA12:bd08/26/2004:svnDellComputerCorporation:pnDimension4600i:pvr:rvnDellComputerCorp.:rn0F4491:rvr:cvnDellComputerCorporation:ct6:cvr:')
2010-04-09 16:33:41,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-09 16:33:41,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Deskjet D2400 series;DES:D2445;CMD:LDL,DYN;')
2010-04-09 16:33:41,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip01')
2010-04-09 16:33:41,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip02')
2010-04-09 16:33:41,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-09 16:33:41,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-09 16:33:41,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-09 16:33:41,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Deskjet D2400 series;DES:Deskjet D2400 series;')
2010-04-09 16:33:41,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:33:41,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d00001050sv00001028sd00000174bc02sc00i00')
2010-04-09 16:33:41,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001028sd00000174bc0Csc03i00')
2010-04-09 16:33:41,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-09 16:33:41,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-09 16:33:41,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'usb:v03F0p7A04d0100dc00dsc00dp00ic07isc01ip02')
2010-04-09 16:33:41,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001028sd00000174bc0Csc03i20')
2010-04-09 16:33:41,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-09 16:33:41,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-09 16:33:41,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'pci:v0000100Bd00000020sv00001385sd0000F311bc02sc00i00')
2010-04-09 16:33:41,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2010-04-09 16:33:41,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fc7b8c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-09 16:33:42,340 DEBUG: handler xorg:nvidia_173 previously unseen
2010-04-09 16:33:42,677 DEBUG: handler xorg:nvidia_96 previously unseen
2010-04-09 16:33:42,786 DEBUG: writing back check cache /var/cache/jockey/check
2010-04-09 16:33:50,384 DEBUG: Installing package: nvidia-173
2010-04-09 16:36:23,948 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-04-09 16:36:36,863 DEBUG: install progress statusChange dkms 0.000000
2010-04-09 16:36:36,864 DEBUG: install progress statusChange dkms 4.000000
2010-04-09 16:36:37,475 DEBUG: install progress statusChange dkms 8.000000
2010-04-09 16:36:37,570 DEBUG: install progress statusChange dkms 12.000000
2010-04-09 16:36:37,692 DEBUG: install progress statusChange fakeroot 12.000000
2010-04-09 16:36:37,693 DEBUG: install progress statusChange fakeroot 16.000000
2010-04-09 16:36:38,129 DEBUG: install progress statusChange fakeroot 20.000000
2010-04-09 16:36:38,191 DEBUG: install progress statusChange fakeroot 24.000000
2010-04-09 16:36:38,299 DEBUG: install progress statusChange patch 24.000000
2010-04-09 16:36:38,301 DEBUG: install progress statusChange patch 28.000000
2010-04-09 16:36:38,648 DEBUG: install progress statusChange patch 32.000000
2010-04-09 16:36:38,730 DEBUG: install progress statusChange patch 36.000000
2010-04-09 16:36:38,866 DEBUG: install progress statusChange nvidia-173 36.000000
2010-04-09 16:36:38,867 DEBUG: install progress statusChange nvidia-173 40.000000
2010-04-09 16:36:46,221 DEBUG: install progress statusChange nvidia-173 44.000000
2010-04-09 16:36:46,302 DEBUG: install progress statusChange nvidia-173 48.000000
2010-04-09 16:36:46,464 DEBUG: install progress statusChange nvidia-settings 48.000000
2010-04-09 16:36:46,464 DEBUG: install progress statusChange nvidia-settings 52.000000
2010-04-09 16:36:46,831 DEBUG: install progress statusChange nvidia-settings 56.000000
2010-04-09 16:36:46,895 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-04-09 16:36:46,973 DEBUG: install progress statusChange man-db 60.000000
2010-04-09 16:36:51,354 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-04-09 16:36:51,568 DEBUG: install progress statusChange dkms 60.000000
2010-04-09 16:36:52,540 DEBUG: install progress statusChange dkms 64.000000
2010-04-09 16:36:52,624 DEBUG: install progress statusChange dkms 68.000000
2010-04-09 16:36:52,673 DEBUG: install progress statusChange fakeroot 68.000000
2010-04-09 16:36:52,745 DEBUG: install progress statusChange fakeroot 72.000000
2010-04-09 16:36:53,140 DEBUG: install progress statusChange fakeroot 76.000000
2010-04-09 16:36:53,253 DEBUG: install progress statusChange patch 76.000000
2010-04-09 16:36:53,338 DEBUG: install progress statusChange patch 80.000000
2010-04-09 16:36:53,426 DEBUG: install progress statusChange patch 84.000000
2010-04-09 16:36:53,511 DEBUG: install progress statusChange nvidia-173 84.000000
2010-04-09 16:36:53,597 DEBUG: install progress statusChange nvidia-173 88.000000
2010-04-09 16:38:48,175 DEBUG: install progress statusChange nvidia-173 92.000000
2010-04-09 16:38:49,648 DEBUG: install progress statusChange nvidia-settings 92.000000
2010-04-09 16:38:49,802 DEBUG: install progress statusChange nvidia-settings 96.000000
2010-04-09 16:38:49,954 DEBUG: install progress statusChange nvidia-settings 100.000000
2010-04-09 16:38:50,083 DEBUG: install progress statusChange python-gmenu 100.000000
2010-04-09 16:38:52,954 DEBUG: install progress statusChange initramfs-tools 100.000000
2010-04-09 16:39:16,970 DEBUG: install progress statusChange python-support 100.000000
2010-04-09 16:39:24,686 DEBUG: Selecting previously deselected package dkms.
(Reading database ... 123455 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-173.
Unpacking nvidia-173 (from .../nvidia-173_173.14.22-0ubuntu11_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up patch (2.6-2ubuntu1) ...
Setting up nvidia-173 (173.14.22-0ubuntu11) ...
update-alternatives: using /usr/lib/nvidia-173/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-173-173.14.22 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-19-generic
Building for architecture i686
Building initial module for 2.6.32-19-generic
Done.

nvidia-173.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-19-generic/updates/dkms/

depmod.....................

DKMS: install Completed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-19-generic
Processing triggers for python-support ...

2010-04-09 16:39:26,184 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n']})
2010-04-09 16:43:08,570 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tOption\t"NoLogo"\t"True"\n', '\tDriver\t"nvidia"\n']})
2010-04-09 16:51:55,362 DEBUG: Shutting down
2010-04-09 16:54:28,264 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c>
2010-04-09 16:54:28,279 DEBUG: reading modalias file /lib/modules/2.6.32-19-generic/modules.alias
2010-04-09 16:54:28,572 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-09 16:54:28,585 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-09 16:54:28,636 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-09 16:54:28,642 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-09 16:54:28,650 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-09 16:54:28,655 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-09 16:54:28,676 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-09 16:54:29,174 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-09 16:54:29,309 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-09 16:54:29,311 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-09 16:54:29,362 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-09 16:54:29,362 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-09 16:54:29,511 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-09 16:54:29,511 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-09 16:54:29,587 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-09 16:54:29,587 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-09 16:54:29,587 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-09 16:54:29,631 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-09 16:54:29,633 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-09 16:54:29,644 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 16:54:29,650 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-09 16:54:29,653 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-09 16:54:29,665 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 16:54:29,666 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-09 16:54:29,702 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-09 16:54:29,719 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 16:54:29,719 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-09 16:54:29,743 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-09 16:54:29,755 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-09 16:54:29,755 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-09 16:54:29,756 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-09 16:54:29,896 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-09 16:54:29,897 DEBUG: Firmware for DVB cards not available
2010-04-09 16:54:29,897 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-09 16:54:29,935 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-09 16:54:29,936 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-09 16:54:29,937 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-09 16:54:29,937 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-09 16:54:29,966 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-09 16:54:30,040 DEBUG: Software modem not available
2010-04-09 16:54:30,041 DEBUG: all custom handlers loaded
2010-04-09 16:54:30,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v000010DEd00000322sv000010DEsd000001B9bc03sc00i00')
2010-04-09 16:54:31,102 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 16:54:32,374 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-09 16:54:32,377 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 16:54:33,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:33,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:33,431 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 16:54:33,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:33,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001028sd00000174bc04sc01i00')
2010-04-09 16:54:34,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:device:')
2010-04-09 16:54:34,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-09 16:54:34,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-09 16:54:34,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'platform:eisa')
2010-04-09 16:54:34,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 16:54:34,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-09 16:54:34,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-09 16:54:34,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-09 16:54:34,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-09 16:54:34,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'platform:dcdbas')
2010-04-09 16:54:34,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001028sd00000174bc06sc00i00')
2010-04-09 16:54:34,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-09 16:54:34,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-09 16:54:34,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-09 16:54:34,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-09 16:54:34,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-09 16:54:34,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-09 16:54:34,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-09 16:54:34,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 16:54:34,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:54:34,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-09 16:54:34,360 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,361 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d000024D3sv00001028sd00000174bc0Csc05i00')
2010-04-09 16:54:34,368 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,368 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,2,4,11,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2010-04-09 16:54:34,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:54:34,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'dmi:bvnDellComputerCorporation:bvrA12:bd08/26/2004:svnDellComputerCorporation:pnDimension4600i:pvr:rvnDellComputerCorp.:rn0F4491:rvr:cvnDellComputerCorporation:ct6:cvr:')
2010-04-09 16:54:34,400 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-09 16:54:34,401 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Deskjet D2400 series;DES:D2445;CMD:LDL,DYN;')
2010-04-09 16:54:34,401 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip01')
2010-04-09 16:54:34,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip02')
2010-04-09 16:54:34,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-09 16:54:34,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-09 16:54:34,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-09 16:54:34,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Deskjet D2400 series;DES:Deskjet D2400 series;')
2010-04-09 16:54:34,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:54:34,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d00001050sv00001028sd00000174bc02sc00i00')
2010-04-09 16:54:34,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e100', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001028sd00000174bc0Csc03i00')
2010-04-09 16:54:34,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-09 16:54:34,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-09 16:54:34,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'usb:v03F0p7A04d0100dc00dsc00dp00ic07isc01ip02')
2010-04-09 16:54:34,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001028sd00000174bc0Csc03i20')
2010-04-09 16:54:34,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-09 16:54:34,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-09 16:54:34,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'pci:v0000100Bd00000020sv00001385sd0000F311bc02sc00i00')
2010-04-09 16:54:34,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'natsemi', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2010-04-09 16:54:34,556 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 16:54:34,556 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d0294c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-09 16:54:34,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v000010DEd00000322sv000010DEsd000001B9bc03sc00i00')
2010-04-09 16:54:34,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001028sd00000174bc04sc01i00')
2010-04-09 16:54:34,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:device:')
2010-04-09 16:54:34,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-09 16:54:34,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-09 16:54:34,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'platform:eisa')
2010-04-09 16:54:34,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 16:54:34,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-09 16:54:34,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-09 16:54:34,558 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-09 16:54:34,558 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-09 16:54:34,558 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'platform:dcdbas')
2010-04-09 16:54:34,558 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001028sd00000174bc06sc00i00')
2010-04-09 16:54:34,559 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-09 16:54:34,559 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-09 16:54:34,559 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-09 16:54:34,559 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-09 16:54:34,560 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-09 16:54:34,560 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-09 16:54:34,560 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-09 16:54:34,561 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 16:54:34,561 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:54:34,561 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-09 16:54:34,561 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d000024D3sv00001028sd00000174bc0Csc05i00')
2010-04-09 16:54:34,562 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,2,4,11,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2010-04-09 16:54:34,562 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:54:34,562 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'dmi:bvnDellComputerCorporation:bvrA12:bd08/26/2004:svnDellComputerCorporation:pnDimension4600i:pvr:rvnDellComputerCorp.:rn0F4491:rvr:cvnDellComputerCorporation:ct6:cvr:')
2010-04-09 16:54:34,563 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-09 16:54:34,563 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Deskjet D2400 series;DES:D2445;CMD:LDL,DYN;')
2010-04-09 16:54:34,563 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip01')
2010-04-09 16:54:34,564 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip02')
2010-04-09 16:54:34,564 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-09 16:54:34,564 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-09 16:54:34,565 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-09 16:54:34,565 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Deskjet D2400 series;DES:Deskjet D2400 series;')
2010-04-09 16:54:34,565 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001028sd00000174bc0Csc03i00')
2010-04-09 16:54:34,566 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d00001050sv00001028sd00000174bc02sc00i00')
2010-04-09 16:54:34,566 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001028sd00000174bc0Csc03i00')
2010-04-09 16:54:34,566 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-09 16:54:34,566 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-09 16:54:34,566 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'usb:v03F0p7A04d0100dc00dsc00dp00ic07isc01ip02')
2010-04-09 16:54:34,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001028sd00000174bc0Csc03i20')
2010-04-09 16:54:34,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-09 16:54:34,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-09 16:54:34,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'pci:v0000100Bd00000020sv00001385sd0000F311bc02sc00i00')
2010-04-09 16:54:34,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2010-04-09 16:54:34,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9083c0c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-09 16:56:36,515 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tOption\t"NoLogo"\t"True"\n', '\tDriver\t"nvidia"\n']})
2010-04-09 16:59:35,066 DEBUG: Installing package: nvidia-96
2010-04-09 17:01:09,126 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-04-09 17:01:22,084 DEBUG: install progress statusChange nvidia-96 0.000000
2010-04-09 17:01:22,185 DEBUG: install progress statusChange nvidia-96 20.000000
2010-04-09 17:01:28,570 DEBUG: install progress statusChange nvidia-96 40.000000
2010-04-09 17:01:28,652 DEBUG: install progress statusChange nvidia-96 60.000000
2010-04-09 17:01:28,744 DEBUG: install progress statusChange python-gmenu 60.000000
2010-04-09 17:01:29,559 DEBUG: install progress statusChange man-db 60.000000
2010-04-09 17:01:33,388 DEBUG: install progress statusChange python-support 60.000000
2010-04-09 17:01:38,908 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-04-09 17:01:39,067 DEBUG: install progress statusChange nvidia-96 60.000000
2010-04-09 17:01:39,238 DEBUG: install progress statusChange nvidia-96 80.000000
2010-04-09 17:03:01,580 DEBUG: install progress statusChange nvidia-96 100.000000
2010-04-09 17:03:01,878 DEBUG: install progress statusChange python-gmenu 100.000000
2010-04-09 17:03:02,540 DEBUG: install progress statusChange python-support 100.000000
2010-04-09 17:03:03,944 DEBUG: Selecting previously deselected package nvidia-96.
(Reading database ... 123659 files and directories currently installed.)
Unpacking nvidia-96 (from .../nvidia-96_96.43.14-0ubuntu12_i386.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up nvidia-96 (96.43.14-0ubuntu12) ...
Loading new nvidia-96-96.43.14 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-19-generic
Building for architecture i686
Building initial module for 2.6.32-19-generic
Done.

nvidia-96.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-19-generic/updates/dkms/

depmod.............

DKMS: install Completed.

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for python-support ...

2010-04-09 17:03:04,316 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tOption\t"NoLogo"\t"True"\n', '\tDriver\t"nvidia"\n']})
2010-04-09 17:08:48,110 DEBUG: nvidia_173 is not the alternative in use
2010-04-09 17:08:48,286 DEBUG: nvidia_173 is not the alternative in use
2010-04-09 17:08:50,077 DEBUG: nvidia_173 is not the alternative in use
2010-04-09 17:08:50,253 DEBUG: nvidia_173 is not the alternative in use
2010-04-09 17:08:50,390 DEBUG: Shutting down
2010-04-10 20:58:54,620 WARNING: cannot connect to cups; printer detection is not available
2010-04-10 20:58:54,637 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc>
2010-04-10 20:58:54,638 DEBUG: reading modalias file /lib/modules/2.6.32-19-generic/modules.alias
2010-04-10 20:58:54,904 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-10 20:58:54,917 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-10 20:58:54,969 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-10 20:58:54,984 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-10 20:58:55,002 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-10 20:58:55,020 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-10 20:58:55,029 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-10 20:58:55,439 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-10 20:58:55,571 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-10 20:58:55,573 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-10 20:58:55,604 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-10 20:58:55,605 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-10 20:58:55,703 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-10 20:58:55,703 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-10 20:58:55,758 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-10 20:58:55,759 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-10 20:58:55,759 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-10 20:58:55,804 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-10 20:58:55,816 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 20:58:55,821 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-10 20:58:55,823 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-10 20:58:55,834 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 20:58:55,835 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-10 20:58:55,957 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-10 20:58:55,969 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 20:58:55,970 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-10 20:58:55,994 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-10 20:58:56,006 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-10 20:58:56,006 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-10 20:58:56,007 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-10 20:58:56,074 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-10 20:58:56,075 DEBUG: Firmware for DVB cards not available
2010-04-10 20:58:56,075 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-10 20:58:56,104 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-10 20:58:56,105 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-10 20:58:56,105 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-10 20:58:56,105 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-10 20:58:56,132 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-10 20:58:56,197 DEBUG: Software modem not available
2010-04-10 20:58:56,197 DEBUG: all custom handlers loaded
2010-04-10 20:58:56,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v000010DEd00000322sv000010DEsd000001B9bc03sc00i00')
2010-04-10 20:58:57,969 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 20:58:56,872 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 20:58:57,971 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 20:58:58,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:58,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:58,352 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 20:58:58,707 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 20:58:58,533 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 20:58:58,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:58,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001028sd00000174bc04sc01i00')
2010-04-10 20:58:59,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,192 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:device:')
2010-04-10 20:58:59,192 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-10 20:58:59,193 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-10 20:58:59,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'platform:eisa')
2010-04-10 20:58:59,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 20:58:59,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-10 20:58:59,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-10 20:58:59,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-10 20:58:59,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-10 20:58:59,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'platform:dcdbas')
2010-04-10 20:58:59,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d00002570sv00001028sd00000174bc06sc00i00')
2010-04-10 20:58:59,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-10 20:58:59,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-10 20:58:59,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-10 20:58:59,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-10 20:58:59,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-10 20:58:59,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-10 20:58:59,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-10 20:58:59,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 20:58:59,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001028sd00000174bc0Csc03i00')
2010-04-10 20:58:59,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-10 20:58:59,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d000024D3sv00001028sd00000174bc0Csc05i00')
2010-04-10 20:58:59,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,2,4,11,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2010-04-10 20:58:59,312 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001028sd00000174bc0Csc03i00')
2010-04-10 20:58:59,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'dmi:bvnDellComputerCorporation:bvrA12:bd08/26/2004:svnDellComputerCorporation:pnDimension4600i:pvr:rvnDellComputerCorp.:rn0F4491:rvr:cvnDellComputerCorporation:ct6:cvr:')
2010-04-10 20:58:59,342 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-10 20:58:59,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip01')
2010-04-10 20:58:59,406 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip02')
2010-04-10 20:58:59,408 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-10 20:58:59,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-10 20:58:59,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-10 20:58:59,417 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,418 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001028sd00000174bc0Csc03i00')
2010-04-10 20:58:59,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d00001050sv00001028sd00000174bc02sc00i00')
2010-04-10 20:58:59,431 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e100', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001028sd00000174bc0Csc03i00')
2010-04-10 20:58:59,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-10 20:58:59,439 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-10 20:58:59,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'usb:v03F0p7A04d0100dc00dsc00dp00ic07isc01ip02')
2010-04-10 20:58:59,468 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,468 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001028sd00000174bc0Csc03i20')
2010-04-10 20:58:59,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'platform:pcspkr')
2010-04-10 20:58:59,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-10 20:58:59,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'pci:v0000100Bd00000020sv00001385sd0000F311bc02sc00i00')
2010-04-10 20:58:59,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'natsemi', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2010-04-10 20:58:59,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 20:58:59,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x92419cc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-10 20:58:59,491 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v000010DEd00000322sv000010DEsd000001B9bc03sc00i00')
2010-04-10 20:58:59,491 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001028sd00000174bc04sc01i00')
2010-04-10 20:58:59,491 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:device:')
2010-04-10 20:58:59,492 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-10 20:58:59,492 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-10 20:58:59,492 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'platform:eisa')
2010-04-10 20:58:59,492 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 20:58:59,492 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-10 20:58:59,492 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-10 20:58:59,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-10 20:58:59,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-10 20:58:59,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'platform:dcdbas')
2010-04-10 20:58:59,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001028sd00000174bc06sc00i00')
2010-04-10 20:58:59,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-10 20:58:59,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-10 20:58:59,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-10 20:58:59,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-10 20:58:59,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-10 20:58:59,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-10 20:58:59,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-10 20:58:59,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 20:58:59,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001028sd00000174bc0Csc03i00')
2010-04-10 20:58:59,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-10 20:58:59,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d000024D3sv00001028sd00000174bc0Csc05i00')
2010-04-10 20:58:59,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,2,4,11,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2010-04-10 20:58:59,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001028sd00000174bc0Csc03i00')
2010-04-10 20:58:59,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'dmi:bvnDellComputerCorporation:bvrA12:bd08/26/2004:svnDellComputerCorporation:pnDimension4600i:pvr:rvnDellComputerCorp.:rn0F4491:rvr:cvnDellComputerCorporation:ct6:cvr:')
2010-04-10 20:58:59,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-10 20:58:59,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip01')
2010-04-10 20:58:59,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'usb:v046DpC509d1904dc00dsc00dp00ic03isc01ip02')
2010-04-10 20:58:59,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-10 20:58:59,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-10 20:58:59,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-10 20:58:59,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001028sd00000174bc0Csc03i00')
2010-04-10 20:58:59,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d00001050sv00001028sd00000174bc02sc00i00')
2010-04-10 20:58:59,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001028sd00000174bc0Csc03i00')
2010-04-10 20:58:59,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-10 20:58:59,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-10 20:58:59,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'usb:v03F0p7A04d0100dc00dsc00dp00ic07isc01ip02')
2010-04-10 20:58:59,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001028sd00000174bc0Csc03i20')
2010-04-10 20:58:59,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-10 20:58:59,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-10 20:58:59,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'pci:v0000100Bd00000020sv00001385sd0000F311bc02sc00i00')
2010-04-10 20:58:59,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'input:b0003v046DpC509e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2010-04-10 20:58:59,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x962d74c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-10 20:58:59,761 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 20:59:00,674 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 20:59:01,021 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 20:59:10,716 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 20:59:15,146 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tOption\t"NoLogo"\t"True"\n', '\tDriver\t"nvidia"\n']})
```

Anybody got any ideas how to fix this so I can continue with my testing?

Thanks,
Nicholas C. Brown

---

### Post by krustysmith on 2010-04-10
Please let me know when u find a way to fix this

---

### Post by acompw on 2010-04-11
Same issue. Beta 2. GeForce 8600 GT.

---

### Post by ZuLuuuuuu on 2010-04-11
Same here, Nvidia 9300M. Ubuntu 10.04, Beta 2, 64-Bit. I'll try to install 32-Bit.

---

### Post by Cfhs_1 on 2010-04-12
The problem seems to have fixed it's self after some updates on my machine. It's working fine with the latest driver now. It's a relief to have Compiz-Fusion Running again.

Tell me if updating fixes this for you guys!:popcorn:

---

### Post by Onyx_47 on 2010-04-15
> **Cfhs_1 said:**
> The problem seems to have fixed it's self after some updates on my machine. It's working fine with the latest driver now. It's a relief to have Compiz-Fusion Running again.

Tell me if updating fixes this for you guys!:popcorn:

Confirming, just did a fresh install of 10.04 Beta 2, nvidia driver installation failed, executed dist-upgrade and it works perfectly now :)

---

### Post by mothes on 2010-04-30
I have the same problem. I just installed Ubuntu 10.04 and I have graphic card GeForce 8600 and I can't install the latest NVidia driver. Who know how to resolve this problem ?

---

