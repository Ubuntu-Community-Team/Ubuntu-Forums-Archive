---
title: "WiFi Dead After Update Lenovo S-10"
date: 2010-05-10
forum: Hardware
---

### Post by jssepos on 2010-05-10
Just ran a routine update this afternoon, following the restart my WiFi is dead. I looked in my hardware drivers and while the Broadcom drivers are there they will not work here is the error:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

I have the code down below since it is so long.

I also tried my original fix since WiFi doesn't work out of the box on the S-10 with Ubuntu. That is found here: [http://www.s10lenovo.com/viewtopic.php?f=41&t=3511](http://www.s10lenovo.com/viewtopic.php?f=41&t=3511)

Any help would be much appreciated! Having a laptop without wireless is pretty much pointless haha!

(Also I looked for a thread on this and didn't find one, if it is a repeat I do apologize and feel free to send me to a fix elsewhere.)

Thanks!

```
2010-05-10 13:25:19,497 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c>
2010-05-10 13:25:19,505 DEBUG: reading modalias file /lib/modules/2.6.32-22-generic/modules.alias
2010-05-10 13:25:20,356 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 13:25:20,376 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 13:25:20,534 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 13:25:20,540 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 13:25:20,551 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 13:25:20,560 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 13:25:20,575 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 13:25:21,414 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-10 13:25:21,470 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-10 13:25:21,541 DEBUG: Software modem not available
2010-05-10 13:25:21,542 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-10 13:25:21,609 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-10 13:25:21,612 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-10 13:25:21,613 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-10 13:25:21,614 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-10 13:25:21,671 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-10 13:25:21,674 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-10 13:25:21,696 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:25:21,703 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-10 13:25:21,704 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-10 13:25:21,724 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:25:21,724 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-10 13:25:21,750 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-10 13:25:21,752 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-10 13:25:21,780 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:25:21,780 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-10 13:25:21,858 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-10 13:25:21,859 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-10 13:25:21,891 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-10 13:25:21,893 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-10 13:25:21,893 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-10 13:25:21,903 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:25:21,922 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-10 13:25:21,923 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-10 13:25:21,923 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-10 13:25:21,937 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-10 13:25:21,939 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-10 13:25:21,969 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-10 13:25:21,970 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-10 13:25:22,044 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-10 13:25:22,046 DEBUG: Firmware for DVB cards not available
2010-05-10 13:25:22,047 DEBUG: all custom handlers loaded
2010-05-10 13:25:22,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027A6sv000017AAsd00003870bc03sc80i00')
2010-05-10 13:25:22,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 13:25:23,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-10 13:25:23,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 13:25:23,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027D8sv000017AAsd00003BF8bc04sc03i00')
2010-05-10 13:25:23,511 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0001v10ECp0269e0001-e0,12,kramls1,2,fw')
2010-05-10 13:25:23,513 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-10 13:25:23,515 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,515 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:25:23,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 13:25:23,614 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-10 13:25:23,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 13:25:23,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027CBsv000017AAsd0000380Abc0Csc03i00')
2010-05-10 13:25:23,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 13:25:23,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027ACsv000017AAsd0000386Fbc06sc00i00')
2010-05-10 13:25:23,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:SYN1024:SYN1000:SYN0002:PNP0F13:')
2010-05-10 13:25:23,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-10 13:25:23,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027AEsv000017AAsd00003870bc03sc00i00')
2010-05-10 13:25:23,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-10 13:25:23,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 13:25:23,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 13:25:23,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:VPC2004:')
2010-05-10 13:25:23,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-05-10 13:25:23,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027C8sv000017AAsd00003807bc0Csc03i00')
2010-05-10 13:25:23,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027DAsv000017AAsd0000380Fbc0Csc05i00')
2010-05-10 13:25:23,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 13:25:23,703 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0003v5986p0241e1404-e0,1,kD4,ramlsfw')
2010-05-10 13:25:23,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-10 13:25:23,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v000014E4d00004315sv000014E4sd000004B5bc02sc80i00')
2010-05-10 13:25:23,889 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,895 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:25:23,897 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:25:23,896 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-10 13:25:23,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr14CN67WW:bd04/29/2009:svnLENOVO:pnLenovo:pvrLenovo:rvnLenovo:rnMariana:rvrRev1.0:cvnLenovo:ct10:cvrRev1.0:')
2010-05-10 13:25:23,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 13:25:23,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 13:25:23,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:25:23,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 13:25:23,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-10 13:25:23,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 13:25:23,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027B9sv000017AAsd0000380Dbc06sc01i00')
2010-05-10 13:25:23,972 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v000014E4d00001713sv000017AAsd00003A23bc02sc00i00')
2010-05-10 13:25:23,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:23,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 13:25:23,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027C9sv000017AAsd00003808bc0Csc03i00')
2010-05-10 13:25:24,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-05-10 13:25:24,003 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:24,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-10 13:25:24,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 13:25:24,006 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027CAsv000017AAsd00003809bc0Csc03i00')
2010-05-10 13:25:24,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 13:25:24,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:24,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:24,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'pci:v00008086d000027CCsv000017AAsd0000380Bbc0Csc03i20')
2010-05-10 13:25:24,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 13:25:24,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:25:24,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8840b4c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-10 13:25:24,068 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027A6sv000017AAsd00003870bc03sc80i00')
2010-05-10 13:25:24,068 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 13:25:24,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-10 13:25:24,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 13:25:24,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027D8sv000017AAsd00003BF8bc04sc03i00')
2010-05-10 13:25:24,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0001v10ECp0269e0001-e0,12,kramls1,2,fw')
2010-05-10 13:25:24,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-10 13:25:24,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:25:24,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 13:25:24,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-10 13:25:24,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 13:25:24,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027CBsv000017AAsd0000380Abc0Csc03i00')
2010-05-10 13:25:24,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 13:25:24,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027ACsv000017AAsd0000386Fbc06sc00i00')
2010-05-10 13:25:24,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:SYN1024:SYN1000:SYN0002:PNP0F13:')
2010-05-10 13:25:24,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-10 13:25:24,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027AEsv000017AAsd00003870bc03sc00i00')
2010-05-10 13:25:24,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-10 13:25:24,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 13:25:24,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 13:25:24,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:VPC2004:')
2010-05-10 13:25:24,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-05-10 13:25:24,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027C8sv000017AAsd00003807bc0Csc03i00')
2010-05-10 13:25:24,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027DAsv000017AAsd0000380Fbc0Csc05i00')
2010-05-10 13:25:24,078 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 13:25:24,078 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0003v5986p0241e1404-e0,1,kD4,ramlsfw')
2010-05-10 13:25:24,078 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-10 13:25:24,079 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v000014E4d00004315sv000014E4sd000004B5bc02sc80i00')
2010-05-10 13:25:24,079 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr14CN67WW:bd04/29/2009:svnLENOVO:pnLenovo:pvrLenovo:rvnLenovo:rnMariana:rvrRev1.0:cvnLenovo:ct10:cvrRev1.0:')
2010-05-10 13:25:24,080 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 13:25:24,081 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 13:25:24,081 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:25:24,082 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 13:25:24,082 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-10 13:25:24,082 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 13:25:24,083 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027B9sv000017AAsd0000380Dbc06sc01i00')
2010-05-10 13:25:24,083 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v000014E4d00001713sv000017AAsd00003A23bc02sc00i00')
2010-05-10 13:25:24,083 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 13:25:24,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027C9sv000017AAsd00003808bc0Csc03i00')
2010-05-10 13:25:24,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-05-10 13:25:24,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-10 13:25:24,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 13:25:24,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027CAsv000017AAsd00003809bc0Csc03i00')
2010-05-10 13:25:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 13:25:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'pci:v00008086d000027CCsv000017AAsd0000380Bbc0Csc03i20')
2010-05-10 13:25:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 13:25:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3380c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-10 13:25:24,239 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:25:24,399 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:25:24,537 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:25:31,214 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:25:36,056 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:25:36,058 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-10 13:25:36,178 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:25:40,415 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:25:40,502 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:25:40,643 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:26:03,339 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:26:03,990 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:26:03,991 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-10 13:26:04,090 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:26:05,557 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:26:05,633 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:26:05,771 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:26:06,732 DEBUG: Shutting down
2010-05-10 13:34:52,143 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec>
2010-05-10 13:34:52,145 DEBUG: reading modalias file /lib/modules/2.6.32-22-generic/modules.alias
2010-05-10 13:34:52,611 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 13:34:52,612 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 13:34:52,760 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 13:34:52,765 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 13:34:52,775 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 13:34:52,782 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 13:34:52,795 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 13:34:53,594 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-10 13:34:53,616 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-10 13:34:53,637 DEBUG: Software modem not available
2010-05-10 13:34:53,638 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-10 13:34:53,646 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-10 13:34:53,648 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-10 13:34:53,648 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-10 13:34:53,649 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-10 13:34:53,662 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-10 13:34:53,663 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-10 13:34:53,683 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:34:53,689 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-10 13:34:53,690 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-10 13:34:53,717 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:34:53,718 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-10 13:34:53,727 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-10 13:34:53,728 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-10 13:34:53,748 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:34:53,748 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-10 13:34:53,777 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-10 13:34:53,778 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-10 13:34:53,787 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-10 13:34:53,788 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-10 13:34:53,789 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-10 13:34:53,800 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:34:53,825 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-10 13:34:53,825 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-10 13:34:53,826 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-10 13:34:53,836 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-10 13:34:53,837 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-10 13:34:53,855 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-10 13:34:53,856 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-10 13:34:53,882 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-10 13:34:53,884 DEBUG: Firmware for DVB cards not available
2010-05-10 13:34:53,884 DEBUG: all custom handlers loaded
2010-05-10 13:34:53,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:hp;MDL:color LaserJet 4600;')
2010-05-10 13:34:53,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027A6sv000017AAsd00003870bc03sc80i00')
2010-05-10 13:34:54,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 13:34:55,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2015 Series;')
2010-05-10 13:34:55,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-10 13:34:55,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:device:')
2010-05-10 13:34:55,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027D8sv000017AAsd00003BF8bc04sc03i00')
2010-05-10 13:34:55,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0001v10ECp0269e0001-e0,12,kramls1,2,fw')
2010-05-10 13:34:55,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'platform:pcspkr')
2010-05-10 13:34:55,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:34:55,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P4015;')
2010-05-10 13:34:55,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:HP LaserJet P2055dn;DES:HP LaserJet P2055dn;CMD:PJL,POSTSCRIPT,PCL,PCLXL;')
2010-05-10 13:34:55,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 13:34:55,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-10 13:34:55,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'platform:eisa')
2010-05-10 13:34:55,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027CBsv000017AAsd0000380Abc0Csc03i00')
2010-05-10 13:34:55,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 13:34:55,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027ACsv000017AAsd0000386Fbc06sc00i00')
2010-05-10 13:34:55,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:HP LaserJet P2035n;')
2010-05-10 13:34:55,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:SYN1024:SYN1000:SYN0002:PNP0F13:')
2010-05-10 13:34:55,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-10 13:34:55,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027AEsv000017AAsd00003870bc03sc00i00')
2010-05-10 13:34:55,323 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-10 13:34:55,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 13:34:55,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 13:34:55,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet 4100 Series ;')
2010-05-10 13:34:55,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2055dn;')
2010-05-10 13:34:55,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:VPC2004:')
2010-05-10 13:34:55,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-05-10 13:34:55,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027C8sv000017AAsd00003807bc0Csc03i00')
2010-05-10 13:34:55,360 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 4200L;')
2010-05-10 13:34:55,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:Lexmark;MDL:7100 Series;')
2010-05-10 13:34:55,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027DAsv000017AAsd0000380Fbc0Csc05i00')
2010-05-10 13:34:55,377 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 13:34:55,378 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0003v5986p0241e1404-e0,1,kD4,ramlsfw')
2010-05-10 13:34:55,379 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-10 13:34:55,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,382 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v000014E4d00004315sv000014E4sd000004B5bc02sc80i00')
2010-05-10 13:34:55,557 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,564 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:34:55,566 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:34:55,565 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-10 13:34:55,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 4200;')
2010-05-10 13:34:55,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr14CN67WW:bd04/29/2009:svnLENOVO:pnLenovo:pvrLenovo:rvnLenovo:rnMariana:rvrRev1.0:cvnLenovo:ct10:cvrRev1.0:')
2010-05-10 13:34:55,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 13:34:55,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:Fiery;MDL:EX260 Color Server PS;')
2010-05-10 13:34:55,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 13:34:55,625 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:Adobe;MDL:PDF;')
2010-05-10 13:34:55,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:34:55,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 13:34:55,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-10 13:34:55,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 13:34:55,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:Xerox;MDL:XXP4595;')
2010-05-10 13:34:55,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027B9sv000017AAsd0000380Dbc06sc01i00')
2010-05-10 13:34:55,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v000014E4d00001713sv000017AAsd00003A23bc02sc00i00')
2010-05-10 13:34:55,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 13:34:55,662 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027C9sv000017AAsd00003808bc0Csc03i00')
2010-05-10 13:34:55,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:DesignJet 800 (C7780B);')
2010-05-10 13:34:55,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-05-10 13:34:55,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-10 13:34:55,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 13:34:55,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027CAsv000017AAsd00003809bc0Csc03i00')
2010-05-10 13:34:55,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 1320 series;')
2010-05-10 13:34:55,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 13:34:55,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'pci:v00008086d000027CCsv000017AAsd0000380Bbc0Csc03i20')
2010-05-10 13:34:55,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet 4000 Series;')
2010-05-10 13:34:55,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:hp color LaserJet 3500;')
2010-05-10 13:34:55,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 13:34:55,741 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:34:55,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b32fec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-10 13:34:55,742 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:hp;MDL:color LaserJet 4600;')
2010-05-10 13:34:55,743 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027A6sv000017AAsd00003870bc03sc80i00')
2010-05-10 13:34:55,743 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 13:34:55,744 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2015 Series;')
2010-05-10 13:34:55,744 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-10 13:34:55,744 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 13:34:55,745 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027D8sv000017AAsd00003BF8bc04sc03i00')
2010-05-10 13:34:55,745 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0001v10ECp0269e0001-e0,12,kramls1,2,fw')
2010-05-10 13:34:55,745 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-10 13:34:55,746 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:34:55,746 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P4015;')
2010-05-10 13:34:55,747 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:HP LaserJet P2055dn;DES:HP LaserJet P2055dn;CMD:PJL,POSTSCRIPT,PCL,PCLXL;')
2010-05-10 13:34:55,747 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 13:34:55,747 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-10 13:34:55,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 13:34:55,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027CBsv000017AAsd0000380Abc0Csc03i00')
2010-05-10 13:34:55,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 13:34:55,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027ACsv000017AAsd0000386Fbc06sc00i00')
2010-05-10 13:34:55,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:HP LaserJet P2035n;')
2010-05-10 13:34:55,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:SYN1024:SYN1000:SYN0002:PNP0F13:')
2010-05-10 13:34:55,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-10 13:34:55,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027AEsv000017AAsd00003870bc03sc00i00')
2010-05-10 13:34:55,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-10 13:34:55,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 13:34:55,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 13:34:55,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet 4100 Series ;')
2010-05-10 13:34:55,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2055dn;')
2010-05-10 13:34:55,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:VPC2004:')
2010-05-10 13:34:55,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-05-10 13:34:55,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027C8sv000017AAsd00003807bc0Csc03i00')
2010-05-10 13:34:55,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 4200L;')
2010-05-10 13:34:55,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:Lexmark;MDL:7100 Series;')
2010-05-10 13:34:55,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027DAsv000017AAsd0000380Fbc0Csc05i00')
2010-05-10 13:34:55,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 13:34:55,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0003v5986p0241e1404-e0,1,kD4,ramlsfw')
2010-05-10 13:34:55,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-10 13:34:55,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v000014E4d00004315sv000014E4sd000004B5bc02sc80i00')
2010-05-10 13:34:55,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 4200;')
2010-05-10 13:34:55,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr14CN67WW:bd04/29/2009:svnLENOVO:pnLenovo:pvrLenovo:rvnLenovo:rnMariana:rvrRev1.0:cvnLenovo:ct10:cvrRev1.0:')
2010-05-10 13:34:55,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 13:34:55,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:Fiery;MDL:EX260 Color Server PS;')
2010-05-10 13:34:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 13:34:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:Adobe;MDL:PDF;')
2010-05-10 13:34:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:34:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 13:34:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-10 13:34:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 13:34:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:Xerox;MDL:XXP4595;')
2010-05-10 13:34:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027B9sv000017AAsd0000380Dbc06sc01i00')
2010-05-10 13:34:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v000014E4d00001713sv000017AAsd00003A23bc02sc00i00')
2010-05-10 13:34:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 13:34:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027C9sv000017AAsd00003808bc0Csc03i00')
2010-05-10 13:34:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:DesignJet 800 (C7780B);')
2010-05-10 13:34:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-05-10 13:34:55,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-10 13:34:55,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 13:34:55,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027CAsv000017AAsd00003809bc0Csc03i00')
2010-05-10 13:34:55,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 1320 series;')
2010-05-10 13:34:55,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 13:34:55,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'pci:v00008086d000027CCsv000017AAsd0000380Bbc0Csc03i20')
2010-05-10 13:34:55,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet 4000 Series;')
2010-05-10 13:34:55,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:hp color LaserJet 3500;')
2010-05-10 13:34:55,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 13:34:55,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ec688c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-10 13:34:55,896 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:34:55,968 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:34:56,105 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:34:58,506 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:35:00,063 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:35:04,985 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:35:04,986 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-10 13:35:05,069 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:35:06,595 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:35:06,666 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:35:06,798 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:35:18,136 DEBUG: Shutting down
2010-05-10 13:50:12,144 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec>
2010-05-10 13:50:12,146 DEBUG: reading modalias file /lib/modules/2.6.32-22-generic/modules.alias
2010-05-10 13:50:12,644 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 13:50:12,645 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 13:50:12,802 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 13:50:12,808 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 13:50:12,819 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 13:50:12,826 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 13:50:12,839 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 13:50:13,695 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-10 13:50:13,719 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-10 13:50:13,744 DEBUG: Software modem not available
2010-05-10 13:50:13,745 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-10 13:50:13,754 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-10 13:50:13,755 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-10 13:50:13,756 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-10 13:50:13,756 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-10 13:50:13,774 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-10 13:50:13,775 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-10 13:50:13,800 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:50:13,807 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-10 13:50:13,808 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-10 13:50:13,838 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:50:13,838 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-10 13:50:13,846 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-10 13:50:13,847 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-10 13:50:13,868 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 13:50:13,868 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-10 13:50:13,901 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-10 13:50:13,902 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-10 13:50:13,910 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-10 13:50:13,911 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-10 13:50:13,912 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-10 13:50:13,920 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:50:13,943 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-10 13:50:13,944 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-10 13:50:13,945 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-10 13:50:13,956 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-10 13:50:13,957 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-10 13:50:13,987 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-10 13:50:13,988 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-10 13:50:14,019 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-10 13:50:14,021 DEBUG: Firmware for DVB cards not available
2010-05-10 13:50:14,022 DEBUG: all custom handlers loaded
2010-05-10 13:50:14,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:hp;MDL:color LaserJet 4600;')
2010-05-10 13:50:14,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027A6sv000017AAsd00003870bc03sc80i00')
2010-05-10 13:50:15,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 13:50:15,378 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2015 Series;')
2010-05-10 13:50:15,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-10 13:50:15,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:device:')
2010-05-10 13:50:15,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027D8sv000017AAsd00003BF8bc04sc03i00')
2010-05-10 13:50:15,395 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0001v10ECp0269e0001-e0,12,kramls1,2,fw')
2010-05-10 13:50:15,396 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'platform:pcspkr')
2010-05-10 13:50:15,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:50:15,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P4015;')
2010-05-10 13:50:15,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:HP LaserJet P2055dn;DES:HP LaserJet P2055dn;CMD:PJL,POSTSCRIPT,PCL,PCLXL;')
2010-05-10 13:50:15,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 13:50:15,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-10 13:50:15,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'platform:eisa')
2010-05-10 13:50:15,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027CBsv000017AAsd0000380Abc0Csc03i00')
2010-05-10 13:50:15,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 13:50:15,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027ACsv000017AAsd0000386Fbc06sc00i00')
2010-05-10 13:50:15,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:HP LaserJet P2035n;')
2010-05-10 13:50:15,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:SYN1024:SYN1000:SYN0002:PNP0F13:')
2010-05-10 13:50:15,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-10 13:50:15,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027AEsv000017AAsd00003870bc03sc00i00')
2010-05-10 13:50:15,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-10 13:50:15,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 13:50:15,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 13:50:15,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2055dn;')
2010-05-10 13:50:15,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:VPC2004:')
2010-05-10 13:50:15,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-05-10 13:50:15,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027C8sv000017AAsd00003807bc0Csc03i00')
2010-05-10 13:50:15,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 4200L;')
2010-05-10 13:50:15,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:Lexmark;MDL:7100 Series;')
2010-05-10 13:50:15,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027DAsv000017AAsd0000380Fbc0Csc05i00')
2010-05-10 13:50:15,598 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 13:50:15,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0003v5986p0241e1404-e0,1,kD4,ramlsfw')
2010-05-10 13:50:15,600 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-10 13:50:15,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v000014E4d00004315sv000014E4sd000004B5bc02sc80i00')
2010-05-10 13:50:15,800 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,806 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:50:15,808 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:50:15,807 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-10 13:50:15,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 4200;')
2010-05-10 13:50:15,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr14CN67WW:bd04/29/2009:svnLENOVO:pnLenovo:pvrLenovo:rvnLenovo:rnMariana:rvrRev1.0:cvnLenovo:ct10:cvrRev1.0:')
2010-05-10 13:50:15,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 13:50:15,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:Fiery;MDL:EX260 Color Server PS;')
2010-05-10 13:50:15,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 13:50:15,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet 4100 Series ;')
2010-05-10 13:50:15,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:50:15,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 13:50:15,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-10 13:50:15,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 13:50:15,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:Xerox;MDL:XXP4595;')
2010-05-10 13:50:15,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027B9sv000017AAsd0000380Dbc06sc01i00')
2010-05-10 13:50:15,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v000014E4d00001713sv000017AAsd00003A23bc02sc00i00')
2010-05-10 13:50:15,892 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 13:50:15,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027C9sv000017AAsd00003808bc0Csc03i00')
2010-05-10 13:50:15,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:DesignJet 800 (C7780B);')
2010-05-10 13:50:15,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-05-10 13:50:15,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:Adobe;MDL:PDF;')
2010-05-10 13:50:15,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-10 13:50:15,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 13:50:15,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027CAsv000017AAsd00003809bc0Csc03i00')
2010-05-10 13:50:15,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 1320 series;')
2010-05-10 13:50:15,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 13:50:15,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'pci:v00008086d000027CCsv000017AAsd0000380Bbc0Csc03i20')
2010-05-10 13:50:15,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet 4000 Series;')
2010-05-10 13:50:15,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:hp color LaserJet 3500;')
2010-05-10 13:50:15,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 13:50:15,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 13:50:15,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b43fec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-10 13:50:15,995 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:hp;MDL:color LaserJet 4600;')
2010-05-10 13:50:15,996 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027A6sv000017AAsd00003870bc03sc80i00')
2010-05-10 13:50:15,996 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 13:50:15,997 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2015 Series;')
2010-05-10 13:50:15,997 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-05-10 13:50:15,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 13:50:15,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027D8sv000017AAsd00003BF8bc04sc03i00')
2010-05-10 13:50:15,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0001v10ECp0269e0001-e0,12,kramls1,2,fw')
2010-05-10 13:50:15,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-10 13:50:15,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:50:16,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P4015;')
2010-05-10 13:50:16,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:HP LaserJet P2055dn;DES:HP LaserJet P2055dn;CMD:PJL,POSTSCRIPT,PCL,PCLXL;')
2010-05-10 13:50:16,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 13:50:16,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-05-10 13:50:16,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 13:50:16,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027CBsv000017AAsd0000380Abc0Csc03i00')
2010-05-10 13:50:16,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 13:50:16,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027ACsv000017AAsd0000386Fbc06sc00i00')
2010-05-10 13:50:16,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:HP LaserJet P2035n;')
2010-05-10 13:50:16,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:SYN1024:SYN1000:SYN0002:PNP0F13:')
2010-05-10 13:50:16,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-05-10 13:50:16,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027AEsv000017AAsd00003870bc03sc00i00')
2010-05-10 13:50:16,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-05-10 13:50:16,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 13:50:16,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 13:50:16,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2055dn;')
2010-05-10 13:50:16,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:VPC2004:')
2010-05-10 13:50:16,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-05-10 13:50:16,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027C8sv000017AAsd00003807bc0Csc03i00')
2010-05-10 13:50:16,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 4200L;')
2010-05-10 13:50:16,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:Lexmark;MDL:7100 Series;')
2010-05-10 13:50:16,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027DAsv000017AAsd0000380Fbc0Csc05i00')
2010-05-10 13:50:16,009 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 13:50:16,009 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0003v5986p0241e1404-e0,1,kD4,ramlsfw')
2010-05-10 13:50:16,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-05-10 13:50:16,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v000014E4d00004315sv000014E4sd000004B5bc02sc80i00')
2010-05-10 13:50:16,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 4200;')
2010-05-10 13:50:16,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr14CN67WW:bd04/29/2009:svnLENOVO:pnLenovo:pvrLenovo:rvnLenovo:rnMariana:rvrRev1.0:cvnLenovo:ct10:cvrRev1.0:')
2010-05-10 13:50:16,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 13:50:16,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:Fiery;MDL:EX260 Color Server PS;')
2010-05-10 13:50:16,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 13:50:16,013 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet 4100 Series ;')
2010-05-10 13:50:16,013 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 13:50:16,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 13:50:16,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-10 13:50:16,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 13:50:16,015 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:Xerox;MDL:XXP4595;')
2010-05-10 13:50:16,015 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027B9sv000017AAsd0000380Dbc06sc01i00')
2010-05-10 13:50:16,016 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v000014E4d00001713sv000017AAsd00003A23bc02sc00i00')
2010-05-10 13:50:16,016 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 13:50:16,017 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027C9sv000017AAsd00003808bc0Csc03i00')
2010-05-10 13:50:16,017 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:DesignJet 800 (C7780B);')
2010-05-10 13:50:16,017 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-05-10 13:50:16,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:Adobe;MDL:PDF;')
2010-05-10 13:50:16,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-10 13:50:16,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'usb:v5986p0241d1404dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 13:50:16,019 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027CAsv000017AAsd00003809bc0Csc03i00')
2010-05-10 13:50:16,019 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:hp;MDL:LaserJet 1320 series;')
2010-05-10 13:50:16,020 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 13:50:16,020 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'pci:v00008086d000027CCsv000017AAsd0000380Bbc0Csc03i20')
2010-05-10 13:50:16,020 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet 4000 Series;')
2010-05-10 13:50:16,021 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('printer_deviceid', 'MFG:Hewlett-Packard;MDL:hp color LaserJet 3500;')
2010-05-10 13:50:16,021 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 13:50:16,022 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ed750c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-05-10 13:50:16,211 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:50:16,316 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:50:16,466 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:50:19,567 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:50:24,649 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 13:50:24,651 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-10 13:50:24,755 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:51:06,410 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:51:06,485 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:51:06,625 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 13:51:07,088 DEBUG: Shutting down
```

---

### Post by NUboon2Age on 2010-05-12
I'm having a similar problem (similar error message in jockey.log) on a Ubuntu 10.4 live pendrive.  It sees the driver and jockey tries to install but fails and I can't tell from the jockey.log message what the problem is or where to go from here.  Help for the other person will probably help me too...

---

### Post by NUboon2Age on 2010-05-12
Two pages that might help:

[http://ubuntuforums.org/showthread.php?p=8905380](http://ubuntuforums.org/showthread.php?p=8905380)

[http://docs.google.com/View?id=dhkq5635_11f3hjxdp6](http://docs.google.com/View?id=dhkq5635_11f3hjxdp6)

---

### Post by NUboon2Age on 2010-05-13
Check out the bug #Bug #511379
**"cannot load Broadcom STA wireless driver (BCM4311)"**
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379/](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379/)

I subscribed to this open bug and put myself on the list of people who were effected by it (I'd recommend you do this too so that it will get attention and get resolved).

This comment says they fixed it this way:
"However the solution was to remove the bcmwl-kernel driver using Synaptic, then going back into Hardware drivers as suggested here: 
[http://ubuntuforums.org/showpost.php?p=8628930&postcount=3](http://ubuntuforums.org/showpost.php?p=8628930&postcount=3). "

One of the other comments says they solved the problem by following the instructions found at:
[http://ubuntuforums.org/showthread.php?p=8747122#post8747122](http://ubuntuforums.org/showthread.php?p=8747122#post8747122)

I hope you'll write to say where you are at with this.  I haven't resolved it yet, but will probably try those instructions.

---

### Post by jssepos on 2010-08-03
I haven't found anything as of yet to fix this problem. I am currently running the Original release of 10.04 since I can enable WiFi in it, I would love to upgrade but I don't want to risk losing WiFi again. Any luck from anyone?

---

