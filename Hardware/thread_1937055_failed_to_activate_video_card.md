---
title: "failed to activate video card"
date: 2012-03-07
forum: Hardware
---

### Post by drklunk on 2012-03-07
after the most recent updates to my laptop and the video card messed up. I tried to activate it in the Hardware Drivers gui and it cranked out a report, which I need help understanding and resolving. it is an on board ATI Mobility Radeon HD 4200:

```

2012-03-07 00:22:27,231 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c>
2012-03-07 00:22:27,233 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic/modules.alias
2012-03-07 00:22:27,407 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-03-07 00:22:27,421 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-03-07 00:22:27,474 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-03-07 00:22:27,477 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-03-07 00:22:27,483 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-03-07 00:22:27,517 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-03-07 00:22:27,526 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-03-07 00:22:27,926 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-03-07 00:22:27,966 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-03-07 00:22:28,015 DEBUG: Software modem not available
2012-03-07 00:22:28,015 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-03-07 00:22:28,098 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-07 00:22:28,101 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-03-07 00:22:28,120 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-03-07 00:22:28,120 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-03-07 00:22:28,135 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-03-07 00:22:28,136 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-03-07 00:22:28,136 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-03-07 00:22:28,136 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-03-07 00:22:28,149 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-03-07 00:22:28,166 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-03-07 00:22:28,167 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-03-07 00:22:28,167 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-03-07 00:22:28,234 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-03-07 00:22:28,235 DEBUG: Firmware for DVB cards not available
2012-03-07 00:22:28,235 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-03-07 00:22:28,249 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-03-07 00:22:28,251 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-03-07 00:22:28,270 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-07 00:22:28,277 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-03-07 00:22:28,279 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-03-07 00:22:28,298 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-07 00:22:28,299 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-03-07 00:22:28,319 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-03-07 00:22:28,321 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-03-07 00:22:28,337 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-07 00:22:28,338 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-03-07 00:22:28,422 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-03-07 00:22:28,422 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-03-07 00:22:28,450 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-03-07 00:22:28,451 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-03-07 00:22:28,451 DEBUG: all custom handlers loaded
2012-03-07 00:22:28,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001002d00009712sv00001025sd00000292bc03sc00i00')
2012-03-07 00:22:28,784 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-07 00:22:29,832 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:22:28,786 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-07 00:22:30,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2012-03-07 00:22:30,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-07 00:22:30,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:device:')
2012-03-07 00:22:30,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001002d0000970Fsv00001025sd00000292bc04sc03i00')
2012-03-07 00:22:30,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0003v064EpA103e0500-e0,1,kD4,ramlsfw')
2012-03-07 00:22:30,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'platform:eisa')
2012-03-07 00:22:30,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-03-07 00:22:30,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-07 00:22:30,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-07 00:22:30,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'platform:regulatory')
2012-03-07 00:22:30,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000292bc0Csc03i20')
2012-03-07 00:22:30,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-07 00:22:30,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001022d00009601sv00001025sd00000292bc06sc00i00')
2012-03-07 00:22:30,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-07 00:22:30,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-07 00:22:30,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001025d00009602sv00000000sd00000000bc06sc04i00')
2012-03-07 00:22:30,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-07 00:22:30,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:SYN1B21:SYN1B00:SYN0002:PNP0F13:')
2012-03-07 00:22:30,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-07 00:22:30,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-07 00:22:30,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-03-07 00:22:30,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-03-07 00:22:30,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-03-07 00:22:30,195 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-03-07 00:22:30,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-03-07 00:22:30,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-07 00:22:30,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.05:bd12/07/2009:svnGateway:pnNV53:pvr0100:rvnGateway:rnSJV50TR:rvrRev:cvnGateway:ct10:cvrNone:')
2012-03-07 00:22:30,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-03-07 00:22:30,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-03-07 00:22:30,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-03-07 00:22:30,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc01ip00')
2012-03-07 00:22:30,212 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-07 00:22:30,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-03-07 00:22:30,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000292bc06sc01i00')
2012-03-07 00:22:30,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001025sd00000207bc02sc00i00')
2012-03-07 00:22:30,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000292bc04sc03i00')
2012-03-07 00:22:30,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc02sc80i00')
2012-03-07 00:22:30,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-03-07 00:22:30,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-03-07 00:22:30,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc02ip00')
2012-03-07 00:22:30,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000292bc01sc06i01')
2012-03-07 00:22:30,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'platform:pcspkr')
2012-03-07 00:22:30,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-03-07 00:22:30,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000292bc0Csc05i00')
2012-03-07 00:22:30,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-03-07 00:22:30,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-03-07 00:22:30,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:22:30,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99adb2c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001002d00009712sv00001025sd00000292bc03sc00i00')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:device:')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001002d0000970Fsv00001025sd00000292bc04sc03i00')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0003v064EpA103e0500-e0,1,kD4,ramlsfw')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'platform:eisa')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-03-07 00:22:30,309 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'platform:regulatory')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000292bc0Csc03i20')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001022d00009601sv00001025sd00000292bc06sc00i00')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-07 00:22:30,310 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001025d00009602sv00000000sd00000000bc06sc04i00')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:SYN1B21:SYN1B00:SYN0002:PNP0F13:')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-07 00:22:30,311 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.05:bd12/07/2009:svnGateway:pnNV53:pvr0100:rvnGateway:rnSJV50TR:rvrRev:cvnGateway:ct10:cvrNone:')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0800:')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc01ip00')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000292bc06sc01i00')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001025sd00000207bc02sc00i00')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000292bc04sc03i00')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc02sc80i00')
2012-03-07 00:22:30,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc02ip00')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000292bc01sc06i01')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'platform:pcspkr')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000292bc0Csc05i00')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-03-07 00:22:30,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d797ac> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-07 00:22:30,482 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:22:30,735 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:22:31,022 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:22:37,993 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:22:41,745 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-07 00:22:41,746 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2012-03-07 00:22:41,747 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-03-07 00:22:55,117 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:22:55,238 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:02,810 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:02,941 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:03,123 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:03,243 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:03,470 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:03,592 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:17,209 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:17,330 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:17,731 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-07 00:23:17,733 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2012-03-07 00:23:17,733 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-03-07 00:23:26,964 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:27,086 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:29,302 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:29,425 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:29,570 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:29,690 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:29,916 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:23:30,038 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:25:38,634 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c>
2012-03-07 00:25:38,654 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic/modules.alias
2012-03-07 00:25:38,811 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-03-07 00:25:38,825 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-03-07 00:25:38,882 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-03-07 00:25:38,883 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-03-07 00:25:38,886 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-03-07 00:25:38,895 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-03-07 00:25:38,900 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-03-07 00:25:39,297 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-03-07 00:25:39,337 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-03-07 00:25:39,386 DEBUG: Software modem not available
2012-03-07 00:25:39,386 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-03-07 00:25:39,469 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-07 00:25:39,471 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-03-07 00:25:39,490 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-03-07 00:25:39,491 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-03-07 00:25:39,505 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-03-07 00:25:39,506 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-03-07 00:25:39,507 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-03-07 00:25:39,507 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-03-07 00:25:39,519 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-03-07 00:25:39,536 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-03-07 00:25:39,537 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-03-07 00:25:39,537 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-03-07 00:25:39,604 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-03-07 00:25:39,605 DEBUG: Firmware for DVB cards not available
2012-03-07 00:25:39,606 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-03-07 00:25:39,618 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-03-07 00:25:39,621 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-03-07 00:25:39,639 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-07 00:25:39,643 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-03-07 00:25:39,646 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-03-07 00:25:39,663 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-07 00:25:39,664 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-03-07 00:25:39,689 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-03-07 00:25:39,692 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-03-07 00:25:39,709 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-07 00:25:39,709 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-03-07 00:25:39,793 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-03-07 00:25:39,793 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-03-07 00:25:39,821 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-03-07 00:25:39,822 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-03-07 00:25:39,822 DEBUG: all custom handlers loaded
2012-03-07 00:25:39,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001002d00009712sv00001025sd00000292bc03sc00i00')
2012-03-07 00:25:40,150 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-07 00:25:41,245 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:25:40,153 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-07 00:25:41,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2012-03-07 00:25:41,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-07 00:25:41,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:device:')
2012-03-07 00:25:41,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001002d0000970Fsv00001025sd00000292bc04sc03i00')
2012-03-07 00:25:41,554 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0003v064EpA103e0500-e0,1,kD4,ramlsfw')
2012-03-07 00:25:41,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'platform:eisa')
2012-03-07 00:25:41,556 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-03-07 00:25:41,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-07 00:25:41,581 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-07 00:25:41,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'platform:regulatory')
2012-03-07 00:25:41,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000292bc0Csc03i20')
2012-03-07 00:25:41,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-07 00:25:41,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001022d00009601sv00001025sd00000292bc06sc00i00')
2012-03-07 00:25:41,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-07 00:25:41,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-07 00:25:41,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001025d00009602sv00000000sd00000000bc06sc04i00')
2012-03-07 00:25:41,588 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-07 00:25:41,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:SYN1B21:SYN1B00:SYN0002:PNP0F13:')
2012-03-07 00:25:41,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-07 00:25:41,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-07 00:25:41,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-03-07 00:25:41,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-03-07 00:25:41,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-03-07 00:25:41,593 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-03-07 00:25:41,594 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,594 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-03-07 00:25:41,594 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,594 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-07 00:25:41,594 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.05:bd12/07/2009:svnGateway:pnNV53:pvr0100:rvnGateway:rnSJV50TR:rvrRev:cvnGateway:ct10:cvrNone:')
2012-03-07 00:25:41,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-03-07 00:25:41,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-03-07 00:25:41,609 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-03-07 00:25:41,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc01ip00')
2012-03-07 00:25:41,610 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-07 00:25:41,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-03-07 00:25:41,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000292bc06sc01i00')
2012-03-07 00:25:41,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001025sd00000207bc02sc00i00')
2012-03-07 00:25:41,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000292bc04sc03i00')
2012-03-07 00:25:41,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc02sc80i00')
2012-03-07 00:25:41,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-03-07 00:25:41,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-03-07 00:25:41,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc02ip00')
2012-03-07 00:25:41,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000292bc01sc06i01')
2012-03-07 00:25:41,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'platform:pcspkr')
2012-03-07 00:25:41,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-03-07 00:25:41,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000292bc0Csc05i00')
2012-03-07 00:25:41,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-03-07 00:25:41,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-03-07 00:25:41,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-07 00:25:41,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87d5b2c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-07 00:25:41,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001002d00009712sv00001025sd00000292bc03sc00i00')
2012-03-07 00:25:41,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:device:')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001002d0000970Fsv00001025sd00000292bc04sc03i00')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0003v064EpA103e0500-e0,1,kD4,ramlsfw')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'platform:eisa')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-07 00:25:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'platform:regulatory')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000292bc0Csc03i20')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001022d00009601sv00001025sd00000292bc06sc00i00')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001025d00009602sv00000000sd00000000bc06sc04i00')
2012-03-07 00:25:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:SYN1B21:SYN1B00:SYN0002:PNP0F13:')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.05:bd12/07/2009:svnGateway:pnNV53:pvr0100:rvnGateway:rnSJV50TR:rvrRev:cvnGateway:ct10:cvrNone:')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0800:')
2012-03-07 00:25:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc01ip00')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000292bc06sc01i00')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001025sd00000207bc02sc00i00')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000292bc04sc03i00')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc02sc80i00')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-03-07 00:25:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc02ip00')
2012-03-07 00:25:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000292bc01sc06i01')
2012-03-07 00:25:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'platform:pcspkr')
2012-03-07 00:25:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-03-07 00:25:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000292bc0Csc05i00')
2012-03-07 00:25:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-03-07 00:25:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-03-07 00:25:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ba17ac> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-07 00:25:41,879 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:25:42,145 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:25:42,359 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:25:54,120 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:25:57,618 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-07 00:25:57,619 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2012-03-07 00:25:57,619 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-03-07 00:26:10,905 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2012-03-07 00:26:11,029 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches

```

---

### Post by drklunk on 2012-03-07
-bump-
is any more information needed?

---

### Post by drklunk on 2012-03-08
awesome, thanks for the help everyone!


... this is how you solve such an error: [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

