---
title: "Display problems after upgrading to 10.04 w/ Ati Radeon HD 4200"
date: 2010-07-31
forum: Hardware
---

### Post by scottnotbombs on 2010-07-31
My laptop is an HP Pavillion DV4-2045dx.  After upgrading to 10.04 I get 
"Sorry, the installation of this driver failed. Please have a look at the log file for details.: /var/log/jockey.log"  when I try installing through System>Administration>Hardware drivers.  
When I try to install the newest ATI driver, ati-driver-installer-10-7-x86.x86_64.run, if says it installs, but in the terminal it says, "DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install." and I can still only run in "low graphics mode" or whatever and when I go to "reconfigure display settings" on startup instead of "start in low graphics mode" it works, but I still can't turn on Extra Visual Effects... Thanks for your help :D

---

### Post by scottnotbombs on 2010-07-31
Here is fglrx-install.log

> Errors during DKMS module removal
Errors during DKMS module removal

Creating symlink /var/lib/dkms/fglrx/8.753/source ->
                 /usr/src/fglrx-8.753

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's  located, or you could install the linux-headers-2.6.31-17-generic  package.
[Error] Kernel Module : Failed to build fglrx-8.753 with DKMS
[Error] Kernel Module : Removing fglrx-8.753 from DKMS

------------------------------
Deleting module version: 8.753
completely from the DKMS tree.
------------------------------
Done.

---

### Post by scottnotbombs on 2010-07-31
Here is the jockey.log
```


2010-07-31 00:42:03,710 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e1bec>
2010-07-31 00:42:03,711 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2010-07-31 00:42:03,839 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-07-31 00:42:03,855 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-07-31 00:42:03,897 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-07-31 00:42:03,916 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-07-31 00:42:03,938 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-07-31 00:42:03,940 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-07-31 00:42:03,958 WARNING: Could not open DriverDB cache   /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such   file or directory:   '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-07-31 00:42:04,264 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-07-31 00:42:04,308 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-07-31 00:42:04,349 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-07-31 00:42:04,349 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-07-31 00:42:04,350 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-07-31 00:42:04,388 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-07-31 00:42:04,390 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-07-31 00:42:04,397 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 00:42:04,400 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-07-31 00:42:04,402 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-07-31 00:42:04,409 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 00:42:04,409 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-07-31 00:42:04,424 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-07-31 00:42:04,426 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-07-31 00:42:04,433 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 00:42:04,433 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-07-31 00:42:04,438 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 00:42:04,439 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-07-31 00:42:04,447 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-07-31 00:42:04,447 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-07-31 00:42:04,500 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-07-31 00:42:04,500 DEBUG: Firmware for DVB cards not available
2010-07-31 00:42:04,501 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-07-31 00:42:04,524 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-07-31 00:42:04,524 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-07-31 00:42:04,524 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-07-31 00:42:04,524 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-07-31 00:42:04,533 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-07-31 00:42:04,581 DEBUG: Software modem not available
2010-07-31 00:42:04,581 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-07-31 00:42:04,624 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-07-31 00:42:04,625 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-07-31 00:42:04,633 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-07-31 00:42:04,633 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-07-31 00:42:04,633 DEBUG: all custom handlers loaded
2010-07-31 00:42:04,633 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 00:42:04,916 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 00:42:08,700 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:42:04,925 DEBUG: got handler xorg:fglrx([FglrxDriver,   nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-07-31 00:42:09,177 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'radeon',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,177 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 00:42:09,181 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,181 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,193 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,193 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 00:42:09,193 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 00:42:09,193 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 00:42:09,197 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,197 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,197 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 00:42:09,198 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,198 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 00:42:09,198 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 00:42:09,221 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 00:42:09,221 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,222 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,222 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 00:42:09,222 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'platform:eisa')
2010-07-31 00:42:09,222 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 00:42:09,226 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,226 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,227 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'platform:regulatory')
2010-07-31 00:42:09,227 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,227 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 00:42:09,228 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 00:42:09,228 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 00:42:09,228 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 00:42:09,239 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'shpchp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,239 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 00:42:09,240 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 00:42:09,240 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 00:42:09,240 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 00:42:09,240 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 00:42:09,244 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 00:42:09,245 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,245 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,245 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 00:42:09,245 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,245 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 00:42:09,245 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,245 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 00:42:09,246 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,246 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 00:42:09,246 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,246 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,246 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,246 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 00:42:09,251 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'r8169',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,251 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 00:42:09,265 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 00:42:09,265 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 00:42:09,265 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,265 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 00:42:09,265 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 00:42:09,269 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,269 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 00:42:09,269 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 00:42:09,270 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,270 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 00:42:09,270 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,270 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 00:42:09,280 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,280 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 00:42:09,283 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 00:42:09,287 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 00:42:09,288 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,288 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,288 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 00:42:09,288 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,288 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 00:42:09,288 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 00:42:09,289 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 00:42:09,293 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,293 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 00:42:09,293 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 00:42:09,302 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,303 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,303 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 00:42:09,303 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,303 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 00:42:09,307 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 00:42:09,307 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,307 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 00:42:09,307 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:42:09,307 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x94e1bec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 00:42:09,307 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 00:42:09,307 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'platform:eisa')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 00:42:09,308 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'platform:regulatory')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 00:42:09,309 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 00:42:09,310 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 00:42:09,311 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 00:42:09,312 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 00:42:09,312 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 00:42:09,312 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 00:42:09,312 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 00:42:09,312 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x986872c>   about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 00:42:09,490 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:42:09,657 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:42:09,836 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:42:13,839 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:42:20,130 DEBUG: Installing package: linux-headers-2.6.31-17-generic
2010-07-31 00:42:20,448 DEBUG: Package linux-headers-2.6.31-17-generic does not exist, aborting
2010-07-31 00:42:20,896 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 00:42:20,897 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-07-31 00:42:20,897 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-07-31 00:42:53,379 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:42:53,589 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:49:17,864 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:49:17,977 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:49:18,134 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:49:18,272 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:49:18,454 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:49:18,622 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:50:01,098 DEBUG: Shutting down
2010-07-31 00:52:52,113 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x91dabec>
2010-07-31 00:52:52,114 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2010-07-31 00:52:52,243 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-07-31 00:52:52,243 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-07-31 00:52:52,280 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-07-31 00:52:52,281 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-07-31 00:52:52,285 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-07-31 00:52:52,287 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-07-31 00:52:52,290 WARNING: Could not open DriverDB cache   /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such   file or directory:   '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-07-31 00:52:52,612 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-07-31 00:52:52,615 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-07-31 00:52:52,622 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-07-31 00:52:52,623 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-07-31 00:52:52,623 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-07-31 00:52:52,629 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-07-31 00:52:52,631 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-07-31 00:52:52,638 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 00:52:52,641 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-07-31 00:52:52,643 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-07-31 00:52:52,650 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 00:52:52,650 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-07-31 00:52:52,654 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-07-31 00:52:52,655 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-07-31 00:52:52,662 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 00:52:52,662 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-07-31 00:52:52,679 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 00:52:52,682 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-07-31 00:52:52,696 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-07-31 00:52:52,696 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-07-31 00:52:52,715 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-07-31 00:52:52,715 DEBUG: Firmware for DVB cards not available
2010-07-31 00:52:52,715 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-07-31 00:52:52,719 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-07-31 00:52:52,720 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-07-31 00:52:52,720 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-07-31 00:52:52,720 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-07-31 00:52:52,728 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-07-31 00:52:52,736 DEBUG: Software modem not available
2010-07-31 00:52:52,736 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-07-31 00:52:52,747 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-07-31 00:52:52,747 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-07-31 00:52:52,751 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-07-31 00:52:52,751 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-07-31 00:52:52,751 DEBUG: all custom handlers loaded
2010-07-31 00:52:52,751 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 00:52:53,038 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 00:52:53,155 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 00:52:53,040 DEBUG: got handler xorg:fglrx([FglrxDriver,   nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-07-31 00:52:53,333 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'radeon',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,334 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 00:52:53,337 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,337 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,348 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,349 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 00:52:53,349 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 00:52:53,349 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 00:52:53,353 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,353 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,353 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 00:52:53,353 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,353 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 00:52:53,354 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 00:52:53,376 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 00:52:53,376 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,376 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,376 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 00:52:53,376 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'platform:eisa')
2010-07-31 00:52:53,377 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 00:52:53,380 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,381 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,381 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'platform:regulatory')
2010-07-31 00:52:53,381 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,381 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 00:52:53,382 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 00:52:53,382 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 00:52:53,382 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 00:52:53,393 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'shpchp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,394 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 00:52:53,394 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 00:52:53,394 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 00:52:53,394 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 00:52:53,394 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 00:52:53,398 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 00:52:53,398 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,398 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,398 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 00:52:53,398 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,399 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 00:52:53,399 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,399 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 00:52:53,399 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,399 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 00:52:53,399 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,399 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,399 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,400 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 00:52:53,404 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'r8169',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,405 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 00:52:53,418 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 00:52:53,418 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 00:52:53,418 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,418 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 00:52:53,419 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 00:52:53,422 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,422 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 00:52:53,422 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 00:52:53,422 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,422 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 00:52:53,422 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,423 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 00:52:53,432 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,432 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 00:52:53,436 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 00:52:53,441 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 00:52:53,442 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,442 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,442 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 00:52:53,442 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,442 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 00:52:53,442 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 00:52:53,443 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 00:52:53,447 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,447 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 00:52:53,447 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 00:52:53,456 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,456 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,456 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 00:52:53,457 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,457 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 00:52:53,460 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 00:52:53,461 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 00:52:53,461 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x91dabec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 00:52:53,461 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'platform:eisa')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'platform:regulatory')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 00:52:53,462 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 00:52:53,463 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 00:52:53,464 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 00:52:53,465 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x956172c>   about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 01:01:34,345 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x98d8bec>
2010-07-31 01:01:34,366 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2010-07-31 01:01:34,505 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-07-31 01:01:34,522 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-07-31 01:01:34,580 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-07-31 01:01:34,592 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-07-31 01:01:34,624 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-07-31 01:01:34,626 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-07-31 01:01:34,630 WARNING: Could not open DriverDB cache   /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such   file or directory:   '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-07-31 01:01:34,960 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-07-31 01:01:35,008 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-07-31 01:01:35,064 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-07-31 01:01:35,064 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-07-31 01:01:35,064 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-07-31 01:01:35,122 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-07-31 01:01:35,127 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-07-31 01:01:35,144 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:01:35,150 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-07-31 01:01:35,155 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-07-31 01:01:35,172 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:01:35,173 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-07-31 01:01:35,187 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-07-31 01:01:35,192 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-07-31 01:01:35,230 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:01:35,231 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-07-31 01:01:35,235 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:01:35,237 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-07-31 01:01:35,244 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-07-31 01:01:35,244 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-07-31 01:01:35,320 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-07-31 01:01:35,321 DEBUG: Firmware for DVB cards not available
2010-07-31 01:01:35,322 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-07-31 01:01:35,346 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-07-31 01:01:35,347 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-07-31 01:01:35,347 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-07-31 01:01:35,347 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-07-31 01:01:35,371 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-07-31 01:01:35,400 DEBUG: Software modem not available
2010-07-31 01:01:35,401 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-07-31 01:01:35,459 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-07-31 01:01:35,459 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-07-31 01:01:35,481 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-07-31 01:01:35,481 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-07-31 01:01:35,482 DEBUG: all custom handlers loaded
2010-07-31 01:01:35,482 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 01:01:35,797 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:01:37,533 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:01:35,799 DEBUG: got handler xorg:fglrx([FglrxDriver,   nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-07-31 01:01:37,944 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'radeon',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:37,945 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 01:01:37,948 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:37,948 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:37,963 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:37,964 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 01:01:37,964 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 01:01:37,964 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 01:01:37,968 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:37,968 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:37,968 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 01:01:37,968 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:37,968 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 01:01:37,968 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:01:38,000 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 01:01:38,001 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,001 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,001 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 01:01:38,001 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'platform:eisa')
2010-07-31 01:01:38,001 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 01:01:38,005 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,005 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,005 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'platform:regulatory')
2010-07-31 01:01:38,005 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:38,006 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 01:01:38,006 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 01:01:38,006 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 01:01:38,006 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 01:01:38,022 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'shpchp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,022 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 01:01:38,022 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 01:01:38,022 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 01:01:38,022 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 01:01:38,022 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 01:01:38,026 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 01:01:38,026 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,026 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:38,026 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 01:01:38,027 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,027 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 01:01:38,027 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,027 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 01:01:38,027 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,027 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 01:01:38,027 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,027 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,028 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,028 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 01:01:38,033 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'r8169',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,033 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 01:01:38,046 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 01:01:38,046 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 01:01:38,047 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,047 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:01:38,047 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 01:01:38,050 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,050 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 01:01:38,050 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 01:01:38,051 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,051 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 01:01:38,051 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:38,051 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 01:01:38,064 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,065 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 01:01:38,068 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 01:01:38,072 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 01:01:38,072 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,072 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,072 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:01:38,072 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,073 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 01:01:38,073 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 01:01:38,073 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 01:01:38,080 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,081 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 01:01:38,081 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 01:01:38,090 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,090 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,090 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 01:01:38,090 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,090 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 01:01:38,094 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:01:38,094 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,094 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 01:01:38,094 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x98d8bec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 01:01:38,095 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'platform:eisa')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'platform:regulatory')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 01:01:38,096 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 01:01:38,097 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:01:38,098 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 01:01:38,099 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x9c5f72c>   about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 01:01:38,303 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:01:38,505 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:01:38,711 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:01:45,376 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:01:45,572 DEBUG: Installing package: linux-headers-2.6.31-17-generic
2010-07-31 01:01:45,897 DEBUG: Package linux-headers-2.6.31-17-generic does not exist, aborting
2010-07-31 01:01:46,294 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:01:46,295 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-07-31 01:01:46,295 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-07-31 01:01:59,274 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:01:59,414 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:02,205 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:02,313 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:02,475 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:02,599 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:02,733 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:02,857 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:44,171 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:44,279 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:44,431 DEBUG: Installing package: linux-headers-2.6.31-17-generic
2010-07-31 01:02:44,744 DEBUG: Package linux-headers-2.6.31-17-generic does not exist, aborting
2010-07-31 01:02:45,150 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:02:45,151 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-07-31 01:02:45,151 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-07-31 01:02:54,766 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:54,890 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:58,344 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:58,468 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:58,617 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:58,726 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:58,866 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:02:59,003 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:03:01,632 DEBUG: Shutting down
2010-07-31 01:10:53,505 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b71bcc>
2010-07-31 01:10:53,507 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2010-07-31 01:10:53,620 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-07-31 01:10:53,620 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-07-31 01:10:53,657 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-07-31 01:10:53,658 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-07-31 01:10:53,662 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-07-31 01:10:53,663 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-07-31 01:10:53,666 WARNING: Could not open DriverDB cache   /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such   file or directory:   '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-07-31 01:10:53,975 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-07-31 01:10:53,981 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-07-31 01:10:53,997 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-07-31 01:10:53,997 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-07-31 01:10:53,998 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-07-31 01:10:54,011 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-07-31 01:10:54,012 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-07-31 01:10:54,028 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:10:54,034 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-07-31 01:10:54,035 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-07-31 01:10:54,042 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:10:54,043 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-07-31 01:10:54,046 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-07-31 01:10:54,046 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-07-31 01:10:54,062 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:10:54,062 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-07-31 01:10:54,072 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:10:54,073 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-07-31 01:10:54,091 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-07-31 01:10:54,091 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-07-31 01:10:54,116 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-07-31 01:10:54,117 DEBUG: Firmware for DVB cards not available
2010-07-31 01:10:54,118 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-07-31 01:10:54,126 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-07-31 01:10:54,127 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-07-31 01:10:54,128 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-07-31 01:10:54,128 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-07-31 01:10:54,154 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-07-31 01:10:54,173 DEBUG: Software modem not available
2010-07-31 01:10:54,173 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-07-31 01:10:54,199 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-07-31 01:10:54,200 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-07-31 01:10:54,208 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-07-31 01:10:54,209 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-07-31 01:10:54,209 DEBUG: all custom handlers loaded
2010-07-31 01:10:54,209 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 01:10:54,503 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:10:54,626 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:10:54,504 DEBUG: got handler xorg:fglrx([FglrxDriver,   nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-07-31 01:10:54,813 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'radeon',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,814 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 01:10:54,823 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,823 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,837 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,837 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 01:10:54,838 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 01:10:54,838 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 01:10:54,841 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,842 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,842 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 01:10:54,842 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,842 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 01:10:54,842 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:10:54,864 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 01:10:54,865 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,865 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,865 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 01:10:54,865 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'platform:eisa')
2010-07-31 01:10:54,865 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 01:10:54,869 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,869 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,869 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'platform:regulatory')
2010-07-31 01:10:54,869 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,870 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 01:10:54,871 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 01:10:54,872 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 01:10:54,872 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 01:10:54,883 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'shpchp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,883 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 01:10:54,883 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 01:10:54,883 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 01:10:54,883 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 01:10:54,883 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 01:10:54,887 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 01:10:54,887 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,887 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,888 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 01:10:54,888 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,888 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 01:10:54,888 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,888 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 01:10:54,888 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,888 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 01:10:54,889 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,889 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,889 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,889 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 01:10:54,894 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'r8169',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,894 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 01:10:54,908 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 01:10:54,908 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 01:10:54,908 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,908 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:10:54,909 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 01:10:54,912 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,912 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 01:10:54,912 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 01:10:54,912 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,912 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 01:10:54,912 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,913 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 01:10:54,922 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,922 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 01:10:54,926 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 01:10:54,930 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 01:10:54,930 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,930 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,930 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:10:54,930 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,930 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 01:10:54,931 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 01:10:54,931 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 01:10:54,935 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,935 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 01:10:54,935 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 01:10:54,944 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,944 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,944 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 01:10:54,945 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,945 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 01:10:54,948 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:10:54,948 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 01:10:54,949 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x8b71bcc> about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 01:10:54,949 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'platform:eisa')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'platform:regulatory')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 01:10:54,950 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 01:10:54,951 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 01:10:54,952 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 01:10:54,953 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8ef870c>   about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 01:10:55,145 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:10:55,292 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:10:55,450 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:10:59,568 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:10:59,721 DEBUG: Installing package: linux-headers-2.6.31-17-generic
2010-07-31 01:11:00,051 DEBUG: Package linux-headers-2.6.31-17-generic does not exist, aborting
2010-07-31 01:11:00,452 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:11:00,453 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-07-31 01:11:00,454 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-07-31 01:11:09,786 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:11:09,911 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:11:13,488 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:11:13,599 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:11:13,745 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:11:13,867 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:11:14,032 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:11:14,165 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:11:23,095 DEBUG: Shutting down
2010-07-31 01:13:21,673 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9614bcc>
2010-07-31 01:13:21,674 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2010-07-31 01:13:21,774 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-07-31 01:13:21,774 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-07-31 01:13:21,809 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-07-31 01:13:21,810 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-07-31 01:13:21,814 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-07-31 01:13:21,815 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-07-31 01:13:21,818 WARNING: Could not open DriverDB cache   /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such   file or directory:   '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-07-31 01:13:22,129 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-07-31 01:13:22,133 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-07-31 01:13:22,140 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-07-31 01:13:22,140 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-07-31 01:13:22,140 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-07-31 01:13:22,146 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-07-31 01:13:22,146 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-07-31 01:13:22,153 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:13:22,156 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-07-31 01:13:22,157 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-07-31 01:13:22,171 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:13:22,172 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-07-31 01:13:22,179 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-07-31 01:13:22,180 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-07-31 01:13:22,189 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 01:13:22,190 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-07-31 01:13:22,198 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:13:22,199 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-07-31 01:13:22,217 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-07-31 01:13:22,217 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-07-31 01:13:22,271 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-07-31 01:13:22,272 DEBUG: Firmware for DVB cards not available
2010-07-31 01:13:22,273 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-07-31 01:13:22,281 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-07-31 01:13:22,281 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-07-31 01:13:22,281 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-07-31 01:13:22,282 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-07-31 01:13:22,290 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-07-31 01:13:22,298 DEBUG: Software modem not available
2010-07-31 01:13:22,298 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-07-31 01:13:22,309 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-07-31 01:13:22,309 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-07-31 01:13:22,313 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-07-31 01:13:22,313 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-07-31 01:13:22,313 DEBUG: all custom handlers loaded
2010-07-31 01:13:22,313 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 01:13:22,594 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 01:13:22,702 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:13:22,595 DEBUG: got handler xorg:fglrx([FglrxDriver,   nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-07-31 01:13:22,844 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'radeon',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,845 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 01:13:22,848 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,848 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,860 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,860 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 01:13:22,860 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 01:13:22,860 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 01:13:22,864 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,864 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,864 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 01:13:22,864 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,864 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 01:13:22,865 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:13:22,887 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 01:13:22,888 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,888 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,888 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 01:13:22,888 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'platform:eisa')
2010-07-31 01:13:22,888 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 01:13:22,892 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,892 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,892 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'platform:regulatory')
2010-07-31 01:13:22,892 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,893 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 01:13:22,893 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 01:13:22,893 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 01:13:22,893 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 01:13:22,906 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'shpchp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,906 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 01:13:22,907 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 01:13:22,907 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 01:13:22,907 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 01:13:22,907 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 01:13:22,911 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 01:13:22,912 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,912 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,912 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 01:13:22,912 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,912 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 01:13:22,913 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,913 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 01:13:22,913 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,913 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 01:13:22,913 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,913 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,913 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,913 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 01:13:22,918 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'r8169',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,918 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 01:13:22,932 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 01:13:22,932 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 01:13:22,933 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,933 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:13:22,933 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 01:13:22,936 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,936 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 01:13:22,936 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 01:13:22,937 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,937 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 01:13:22,937 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,937 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 01:13:22,946 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,946 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 01:13:22,950 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 01:13:22,954 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 01:13:22,954 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,954 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,954 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:13:22,954 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,955 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 01:13:22,955 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 01:13:22,955 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 01:13:22,959 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,959 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 01:13:22,959 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 01:13:22,968 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,968 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,968 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 01:13:22,969 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,969 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 01:13:22,972 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:13:22,972 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 01:13:22,973 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x9614bcc> about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 01:13:22,973 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'platform:eisa')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'platform:regulatory')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 01:13:22,974 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 01:13:22,975 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 01:13:22,976 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 01:13:22,977 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x999b70c>   about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 01:13:23,333 DEBUG: handler xorg:fglrx previously unseen
2010-07-31 01:13:23,333 DEBUG: writing back check cache /var/cache/jockey/check
2010-07-31 01:13:23,441 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 01:13:23,566 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 09:54:14,335 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x89babcc>
2010-07-31 09:54:14,336 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2010-07-31 09:54:14,435 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-07-31 09:54:14,436 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-07-31 09:54:14,471 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-07-31 09:54:14,472 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-07-31 09:54:14,476 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-07-31 09:54:14,477 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-07-31 09:54:14,480 WARNING: Could not open DriverDB cache   /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such   file or directory:   '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-07-31 09:54:14,835 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-07-31 09:54:14,840 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-07-31 09:54:14,848 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-07-31 09:54:14,848 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-07-31 09:54:14,848 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-07-31 09:54:14,854 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-07-31 09:54:14,855 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-07-31 09:54:14,862 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 09:54:14,865 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-07-31 09:54:14,865 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-07-31 09:54:14,876 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 09:54:14,876 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-07-31 09:54:14,880 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-07-31 09:54:14,881 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-07-31 09:54:14,890 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-07-31 09:54:14,890 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-07-31 09:54:14,895 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 09:54:14,895 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-07-31 09:54:14,903 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-07-31 09:54:14,903 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-07-31 09:54:14,915 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-07-31 09:54:14,915 DEBUG: Firmware for DVB cards not available
2010-07-31 09:54:14,915 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-07-31 09:54:14,919 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-07-31 09:54:14,920 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-07-31 09:54:14,920 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-07-31 09:54:14,920 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-07-31 09:54:14,929 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-07-31 09:54:14,939 DEBUG: Software modem not available
2010-07-31 09:54:14,940 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-07-31 09:54:14,951 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-07-31 09:54:14,951 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-07-31 09:54:14,972 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-07-31 09:54:14,972 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-07-31 09:54:14,973 DEBUG: all custom handlers loaded
2010-07-31 09:54:14,973 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 09:54:15,287 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 09:54:15,398 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 09:54:15,288 DEBUG: got handler xorg:fglrx([FglrxDriver,   nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-07-31 09:54:15,539 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'radeon',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,539 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 09:54:15,542 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,542 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,554 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,554 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 09:54:15,554 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 09:54:15,554 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 09:54:15,558 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,558 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,558 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 09:54:15,558 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,558 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 09:54:15,559 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 09:54:15,583 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 09:54:15,583 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,584 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,584 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 09:54:15,584 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'platform:eisa')
2010-07-31 09:54:15,584 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 09:54:15,588 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,588 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,588 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'platform:regulatory')
2010-07-31 09:54:15,588 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,589 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 09:54:15,589 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 09:54:15,589 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 09:54:15,589 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 09:54:15,600 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'shpchp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,600 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 09:54:15,600 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 09:54:15,600 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 09:54:15,601 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 09:54:15,601 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 09:54:15,604 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 09:54:15,604 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,605 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,605 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 09:54:15,605 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,605 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 09:54:15,605 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,605 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 09:54:15,606 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,606 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 09:54:15,606 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,606 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'joydev',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,606 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,606 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 09:54:15,611 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'r8169',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,611 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 09:54:15,626 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 09:54:15,626 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 09:54:15,627 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,627 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 09:54:15,627 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 09:54:15,630 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,630 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 09:54:15,630 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 09:54:15,631 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,631 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 09:54:15,631 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,631 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 09:54:15,640 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,641 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 09:54:15,644 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 09:54:15,648 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 09:54:15,648 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,648 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,649 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 09:54:15,649 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,649 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 09:54:15,649 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 09:54:15,649 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 09:54:15,653 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,653 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 09:54:15,653 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 09:54:15,662 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,663 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,663 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 09:54:15,663 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,663 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 09:54:15,667 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 09:54:15,668 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,668 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 09:54:15,668 DEBUG: no corresponding handler available for   {'driver_type': 'kernel_module', 'kernel_module': 'evbug',   'jockey_handler': 'KernelModuleHandler'}
2010-07-31 09:54:15,668 DEBUG: querying driver db   <jockey.detection.LocalKernelModulesDriverDB instance at   0x89babcc> about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 09:54:15,668 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001002d00009712sv0000103Csd00003642bc03sc00i00')
2010-07-31 09:54:15,668 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-07-31 09:54:15,668 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,668 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,668 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0C02:')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001002d0000970Fsv0000103Csd00003642bc04sc03i00')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'platform:lis3lv02d')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0000:')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'platform:eisa')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001002d00004383sv0000103Csd00003642bc04sc03i00')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'platform:regulatory')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,669 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001022d00009601sv0000103Csd00003642bc06sc00i00')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:ENE0100:')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0C04:')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v0000103Cd00009602sv00000000sd00000000bc06sc04i00')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0B00:')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0800:')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0F13:')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001002d00004391sv0000103Csd00003642bc01sc06i01')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-07-31 09:54:15,670 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v000010ECd00008136sv0000103Csd00003642bc02sc00i00')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'dmi:bvnHewlett-Packard:bvrF.04:bd10/26/2009:svnHewlett-Packard:pnHPPaviliondv4NotebookPC:pvr039C200002241310000020000:rvnCompal:rn3642:rvr40.18:cvnCompal:ct10:cvrN/A:')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0100:')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc01ip00')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0C01:')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0303:')
2010-07-31 09:54:15,671 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v0000168Cd0000002Bsv0000103Csd0000303Fbc02sc80i00')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001002d00004396sv0000103Csd00003642bc0Csc03i20')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'platform:pcspkr')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'usb:v174Fp1107d0402dcEFdsc02dp01ic0Eisc02ip00')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001002d00004385sv0000103Csd00003642bc0Csc05i00')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-07-31 09:54:15,672 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'pci:v00001002d0000439Dsv0000103Csd00003642bc06sc01i00')
2010-07-31 09:54:15,673 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-07-31 09:54:15,673 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias',   'input:b0003v174Fp1107e0402-e0,1,kD4,ramlsfw')
2010-07-31 09:54:15,673 DEBUG: querying driver db   <jockey.detection.OpenPrintingDriverDB instance at 0x8d4170c>   about HardwareID('modalias', 'acpi:PNP0200:')
2010-07-31 09:54:15,877 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 09:54:16,019 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 09:54:16,162 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 09:54:19,451 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 09:54:23,778 DEBUG: Installing package: linux-headers-2.6.31-17-generic
2010-07-31 09:54:24,086 DEBUG: Package linux-headers-2.6.31-17-generic does not exist, aborting
2010-07-31 09:54:24,485 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-07-31 09:54:24,485 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-07-31 09:54:24,485 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-07-31 09:54:30,799 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 09:54:30,907 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 10:06:49,086 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 10:06:49,220 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 10:06:49,392 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 10:06:49,500 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 10:06:49,646 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 10:06:49,765 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-31 10:06:51,474 DEBUG: Shutting down
```

---

### Post by scottnotbombs on 2010-08-02
bump

---

### Post by ghendric on 2010-12-12
I'm having the same problem with an ATI driver. I downloaded the latest version from ATI and installed it just fine but then the extra visual effects that I had turned on stopped working. I tried un-installing that driver and go back to the last driver but now I get the error*** Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'.***

How do you fix that? I've tried just about everything that I can think of. 

I have an ATI 4870 PCIe video card...

---

