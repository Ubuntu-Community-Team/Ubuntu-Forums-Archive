---
title: "Installation of driver failed - nvidia proprietary driver"
date: 2010-04-09
forum: Hardware
---

### Post by kenweill on 2010-04-09
I tried to install the NVIDIA accelerated graphics driver (version 173) on Ubuntu 10.04 Beta 2 and got an error:

Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

Anyone knows how to fix this?

jockey.log

```

2010-04-09 20:57:13,894 DEBUG: Updating repository indexes...
2010-04-09 21:01:33,698 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c>
2010-04-09 21:01:33,708 DEBUG: reading modalias file /lib/modules/2.6.32-19-generic/modules.alias
2010-04-09 21:01:33,982 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-09 21:01:33,991 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-09 21:01:34,045 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-09 21:01:34,047 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-09 21:01:34,053 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-09 21:01:34,056 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-09 21:01:34,063 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-09 21:01:34,149 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-09 21:01:34,245 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-09 21:01:34,245 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-09 21:01:34,261 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-09 21:01:34,261 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-09 21:01:34,261 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-09 21:01:34,273 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-09 21:01:34,296 DEBUG: Software modem not available
2010-04-09 21:01:34,297 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-09 21:01:34,303 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-09 21:01:34,304 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-09 21:01:34,304 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-09 21:01:34,305 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-09 21:01:34,353 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-09 21:01:34,353 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-09 21:01:34,363 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 21:01:34,367 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-09 21:01:34,368 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-09 21:01:34,377 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 21:01:34,377 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-09 21:01:34,398 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-09 21:01:34,398 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-09 21:01:34,408 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 21:01:34,408 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-09 21:01:34,450 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-04-09 21:01:34,453 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-09 21:01:34,459 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-09 21:01:34,469 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-09 21:01:34,469 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-09 21:01:34,469 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-09 21:01:34,476 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-09 21:01:34,476 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-09 21:01:34,485 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-09 21:01:34,485 DEBUG: all custom handlers loaded
2010-04-09 21:01:34,486 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v000010DEd00000326sv00000000sd00000000bc03sc00i00')
2010-04-09 21:01:35,402 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:35,402 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:35,407 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-09 21:01:35,408 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 21:01:36,102 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-09 21:01:36,103 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 21:01:36,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001043sd00008227bc04sc01i00')
2010-04-09 21:01:36,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-09 21:01:36,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-09 21:01:36,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-09 21:01:36,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-09 21:01:36,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 21:01:36,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-04-09 21:01:36,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-09 21:01:36,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'platform:eisa')
2010-04-09 21:01:36,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-09 21:01:36,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001043sd00008157bc06sc00i00')
2010-04-09 21:01:36,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2010-04-09 21:01:36,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-09 21:01:36,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-09 21:01:36,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-09 21:01:36,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-09 21:01:36,762 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-09 21:01:36,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-09 21:01:36,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1501:bd12/26/2007:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerInc.:rnP5PE-VM:rvrRev1.00:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-04-09 21:01:36,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-09 21:01:36,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 21:01:36,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-04-09 21:01:36,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-09 21:01:36,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2010-04-09 21:01:36,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'skge', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-09 21:01:36,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2010-04-09 21:01:36,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:device:')
2010-04-09 21:01:36,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-09 21:01:36,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001043sd000080A6bc0Csc03i20')
2010-04-09 21:01:36,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-09 21:01:36,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v000010DEd00000326sv00000000sd00000000bc03sc00i00')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001043sd00008227bc04sc01i00')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'platform:eisa')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001043sd00008157bc06sc00i00')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1501:bd12/26/2007:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerInc.:rnP5PE-VM:rvrRev1.00:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:device:')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001043sd000080A6bc0Csc03i20')
2010-04-09 21:01:36,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-09 21:01:36,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-09 21:01:37,002 DEBUG: handler xorg:nvidia_173 previously unseen
2010-04-09 21:01:37,144 DEBUG: handler xorg:nvidia_96 previously unseen
2010-04-09 21:01:37,241 DEBUG: writing back check cache /var/cache/jockey/check
2010-04-09 21:18:58,746 DEBUG: Installing package: nvidia-173
2010-04-09 21:34:13,648 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-04-09 21:34:15,232 DEBUG: install progress statusChange dkms 0.000000
2010-04-09 21:34:15,233 DEBUG: install progress statusChange dkms 4.000000
2010-04-09 21:34:15,666 DEBUG: install progress statusChange dkms 8.000000
2010-04-09 21:34:15,694 DEBUG: install progress statusChange dkms 12.000000
2010-04-09 21:34:15,802 DEBUG: install progress statusChange fakeroot 12.000000
2010-04-09 21:34:15,803 DEBUG: install progress statusChange fakeroot 16.000000
2010-04-09 21:34:16,000 DEBUG: install progress statusChange fakeroot 20.000000
2010-04-09 21:34:16,091 DEBUG: install progress statusChange fakeroot 24.000000
2010-04-09 21:34:16,161 DEBUG: install progress statusChange patch 24.000000
2010-04-09 21:34:16,163 DEBUG: install progress statusChange patch 28.000000
2010-04-09 21:34:16,316 DEBUG: install progress statusChange patch 32.000000
2010-04-09 21:34:16,369 DEBUG: install progress statusChange patch 36.000000
2010-04-09 21:34:16,462 DEBUG: install progress statusChange nvidia-173 36.000000
2010-04-09 21:34:16,463 DEBUG: install progress statusChange nvidia-173 40.000000
2010-04-09 21:34:21,203 DEBUG: install progress statusChange nvidia-173 44.000000
2010-04-09 21:34:21,262 DEBUG: install progress statusChange nvidia-173 48.000000
2010-04-09 21:34:21,436 DEBUG: install progress statusChange nvidia-settings 48.000000
2010-04-09 21:34:21,437 DEBUG: install progress statusChange nvidia-settings 52.000000
2010-04-09 21:34:21,585 DEBUG: install progress statusChange nvidia-settings 56.000000
2010-04-09 21:34:21,637 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-04-09 21:34:21,692 DEBUG: install progress statusChange man-db 60.000000
2010-04-09 21:34:23,720 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-04-09 21:34:23,817 DEBUG: install progress statusChange dkms 60.000000
2010-04-09 21:34:24,287 DEBUG: install progress statusChange dkms 64.000000
2010-04-09 21:34:24,361 DEBUG: install progress statusChange dkms 68.000000
2010-04-09 21:34:24,397 DEBUG: install progress statusChange fakeroot 68.000000
2010-04-09 21:34:24,415 DEBUG: install progress statusChange fakeroot 72.000000
2010-04-09 21:34:24,886 DEBUG: install progress statusChange fakeroot 76.000000
2010-04-09 21:34:24,936 DEBUG: install progress statusChange patch 76.000000
2010-04-09 21:34:25,026 DEBUG: install progress statusChange patch 80.000000
2010-04-09 21:34:25,064 DEBUG: install progress statusChange patch 84.000000
2010-04-09 21:34:25,107 DEBUG: install progress statusChange nvidia-173 84.000000
2010-04-09 21:34:25,125 DEBUG: install progress statusChange nvidia-173 88.000000
2010-04-09 21:35:06,811 DEBUG: install progress statusChange nvidia-173 92.000000
2010-04-09 21:35:06,967 DEBUG: install progress statusChange nvidia-settings 92.000000
2010-04-09 21:35:07,047 DEBUG: install progress statusChange nvidia-settings 96.000000
2010-04-09 21:35:07,079 DEBUG: install progress statusChange nvidia-settings 100.000000
2010-04-09 21:35:07,098 DEBUG: install progress statusChange python-gmenu 100.000000
2010-04-09 21:35:08,071 DEBUG: install progress statusChange initramfs-tools 100.000000
2010-04-09 21:35:17,552 DEBUG: install progress statusChange python-support 100.000000
2010-04-09 21:35:19,157 DEBUG: Selecting previously deselected package dkms.
(Reading database ... 122324 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-173.
Unpacking nvidia-173 (from .../nvidia-173_173.14.22-0ubuntu10_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up patch (2.6-2ubuntu1) ...
Setting up nvidia-173 (173.14.22-0ubuntu10) ...
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

depmod.......

DKMS: install Completed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-19-generic
Processing triggers for python-support ...

2010-04-09 21:35:20,253 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n']})

```

---

### Post by dannyboy79 on 2010-04-09
> **kenweill said:**
> I tried to install the NVIDIA accelerated graphics driver (version 173) on Ubuntu 10.04 Beta 2 and got an error:

Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

Anyone knows how to fix this?

jockey.log

```

2010-04-09 20:57:13,894 DEBUG: Updating repository indexes...
2010-04-09 21:01:33,698 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c>
2010-04-09 21:01:33,708 DEBUG: reading modalias file /lib/modules/2.6.32-19-generic/modules.alias
2010-04-09 21:01:33,982 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-09 21:01:33,991 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-09 21:01:34,045 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-09 21:01:34,047 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-09 21:01:34,053 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-09 21:01:34,056 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-09 21:01:34,063 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-09 21:01:34,149 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-09 21:01:34,245 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-09 21:01:34,245 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-09 21:01:34,261 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-09 21:01:34,261 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-09 21:01:34,261 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-09 21:01:34,273 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-09 21:01:34,296 DEBUG: Software modem not available
2010-04-09 21:01:34,297 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-09 21:01:34,303 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-09 21:01:34,304 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-09 21:01:34,304 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-09 21:01:34,305 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-09 21:01:34,353 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-09 21:01:34,353 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-09 21:01:34,363 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 21:01:34,367 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-09 21:01:34,368 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-09 21:01:34,377 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 21:01:34,377 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-09 21:01:34,398 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-09 21:01:34,398 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-09 21:01:34,408 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-09 21:01:34,408 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-09 21:01:34,450 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-04-09 21:01:34,453 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-09 21:01:34,459 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-09 21:01:34,469 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-09 21:01:34,469 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-09 21:01:34,469 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-09 21:01:34,476 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-09 21:01:34,476 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-09 21:01:34,485 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-09 21:01:34,485 DEBUG: all custom handlers loaded
2010-04-09 21:01:34,486 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v000010DEd00000326sv00000000sd00000000bc03sc00i00')
2010-04-09 21:01:35,402 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:35,402 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:35,407 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-09 21:01:35,408 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 21:01:36,102 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-09 21:01:36,103 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-09 21:01:36,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001043sd00008227bc04sc01i00')
2010-04-09 21:01:36,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-09 21:01:36,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-09 21:01:36,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-09 21:01:36,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-09 21:01:36,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 21:01:36,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-04-09 21:01:36,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-09 21:01:36,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'platform:eisa')
2010-04-09 21:01:36,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-09 21:01:36,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001043sd00008157bc06sc00i00')
2010-04-09 21:01:36,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2010-04-09 21:01:36,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-09 21:01:36,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-09 21:01:36,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-09 21:01:36,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-09 21:01:36,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-09 21:01:36,762 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-09 21:01:36,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-09 21:01:36,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1501:bd12/26/2007:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerInc.:rnP5PE-VM:rvrRev1.00:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-04-09 21:01:36,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-09 21:01:36,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 21:01:36,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-04-09 21:01:36,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-09 21:01:36,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2010-04-09 21:01:36,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'skge', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-09 21:01:36,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2010-04-09 21:01:36,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:device:')
2010-04-09 21:01:36,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-09 21:01:36,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001043sd000080A6bc0Csc03i20')
2010-04-09 21:01:36,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-09 21:01:36,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa27290c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v000010DEd00000326sv00000000sd00000000bc03sc00i00')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D5sv00001043sd00008227bc04sc01i00')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-09 21:01:36,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d00002576sv00000000sd00000000bc08sc80i00')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'platform:eisa')
2010-04-09 21:01:36,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024DEsv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d00002570sv00001043sd00008157bc06sc00i00')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-09 21:01:36,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d00002571sv00000000sd00000000bc06sc04i00')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-09 21:01:36,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D0sv00000000sd00000000bc06sc01i00')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1501:bd12/26/2007:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerInc.:rnP5PE-VM:rvrRev1.00:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-09 21:01:36,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D2sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D4sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:device:')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024D7sv00001043sd000080A6bc0Csc03i00')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-09 21:01:36,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'pci:v00008086d000024DDsv00001043sd000080A6bc0Csc03i20')
2010-04-09 21:01:36,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-09 21:01:36,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa66d98c> about HardwareID('modalias', 'acpi:PNP0401:')
2010-04-09 21:01:37,002 DEBUG: handler xorg:nvidia_173 previously unseen
2010-04-09 21:01:37,144 DEBUG: handler xorg:nvidia_96 previously unseen
2010-04-09 21:01:37,241 DEBUG: writing back check cache /var/cache/jockey/check
2010-04-09 21:18:58,746 DEBUG: Installing package: nvidia-173
2010-04-09 21:34:13,648 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-04-09 21:34:15,232 DEBUG: install progress statusChange dkms 0.000000
2010-04-09 21:34:15,233 DEBUG: install progress statusChange dkms 4.000000
2010-04-09 21:34:15,666 DEBUG: install progress statusChange dkms 8.000000
2010-04-09 21:34:15,694 DEBUG: install progress statusChange dkms 12.000000
2010-04-09 21:34:15,802 DEBUG: install progress statusChange fakeroot 12.000000
2010-04-09 21:34:15,803 DEBUG: install progress statusChange fakeroot 16.000000
2010-04-09 21:34:16,000 DEBUG: install progress statusChange fakeroot 20.000000
2010-04-09 21:34:16,091 DEBUG: install progress statusChange fakeroot 24.000000
2010-04-09 21:34:16,161 DEBUG: install progress statusChange patch 24.000000
2010-04-09 21:34:16,163 DEBUG: install progress statusChange patch 28.000000
2010-04-09 21:34:16,316 DEBUG: install progress statusChange patch 32.000000
2010-04-09 21:34:16,369 DEBUG: install progress statusChange patch 36.000000
2010-04-09 21:34:16,462 DEBUG: install progress statusChange nvidia-173 36.000000
2010-04-09 21:34:16,463 DEBUG: install progress statusChange nvidia-173 40.000000
2010-04-09 21:34:21,203 DEBUG: install progress statusChange nvidia-173 44.000000
2010-04-09 21:34:21,262 DEBUG: install progress statusChange nvidia-173 48.000000
2010-04-09 21:34:21,436 DEBUG: install progress statusChange nvidia-settings 48.000000
2010-04-09 21:34:21,437 DEBUG: install progress statusChange nvidia-settings 52.000000
2010-04-09 21:34:21,585 DEBUG: install progress statusChange nvidia-settings 56.000000
2010-04-09 21:34:21,637 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-04-09 21:34:21,692 DEBUG: install progress statusChange man-db 60.000000
2010-04-09 21:34:23,720 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-04-09 21:34:23,817 DEBUG: install progress statusChange dkms 60.000000
2010-04-09 21:34:24,287 DEBUG: install progress statusChange dkms 64.000000
2010-04-09 21:34:24,361 DEBUG: install progress statusChange dkms 68.000000
2010-04-09 21:34:24,397 DEBUG: install progress statusChange fakeroot 68.000000
2010-04-09 21:34:24,415 DEBUG: install progress statusChange fakeroot 72.000000
2010-04-09 21:34:24,886 DEBUG: install progress statusChange fakeroot 76.000000
2010-04-09 21:34:24,936 DEBUG: install progress statusChange patch 76.000000
2010-04-09 21:34:25,026 DEBUG: install progress statusChange patch 80.000000
2010-04-09 21:34:25,064 DEBUG: install progress statusChange patch 84.000000
2010-04-09 21:34:25,107 DEBUG: install progress statusChange nvidia-173 84.000000
2010-04-09 21:34:25,125 DEBUG: install progress statusChange nvidia-173 88.000000
2010-04-09 21:35:06,811 DEBUG: install progress statusChange nvidia-173 92.000000
2010-04-09 21:35:06,967 DEBUG: install progress statusChange nvidia-settings 92.000000
2010-04-09 21:35:07,047 DEBUG: install progress statusChange nvidia-settings 96.000000
2010-04-09 21:35:07,079 DEBUG: install progress statusChange nvidia-settings 100.000000
2010-04-09 21:35:07,098 DEBUG: install progress statusChange python-gmenu 100.000000
2010-04-09 21:35:08,071 DEBUG: install progress statusChange initramfs-tools 100.000000
2010-04-09 21:35:17,552 DEBUG: install progress statusChange python-support 100.000000
2010-04-09 21:35:19,157 DEBUG: Selecting previously deselected package dkms.
(Reading database ... 122324 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-173.
Unpacking nvidia-173 (from .../nvidia-173_173.14.22-0ubuntu10_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up patch (2.6-2ubuntu1) ...
Setting up nvidia-173 (173.14.22-0ubuntu10) ...
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

depmod.......

DKMS: install Completed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-19-generic
Processing triggers for python-support ...

2010-04-09 21:35:20,253 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n']})

```
see here:
[http://ubuntuforums.org/showthread.php?t=1445972&highlight=nvidia-settings](http://ubuntuforums.org/showthread.php?t=1445972&highlight=nvidia-settings)
OR here:
[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)
and read the section on jocky and nvidia install

---

### Post by kenweill on 2010-04-10
Thanks. Problem solved.
I just did configure using the NVIDIA configurator set to 1024x768 resolution and set 60Hz. 70-80Hz doesnt work. Only  60Hz.

---

