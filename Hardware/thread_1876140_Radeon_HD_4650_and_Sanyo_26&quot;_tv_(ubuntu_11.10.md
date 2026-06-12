---
title: "Radeon HD 4650 and Sanyo 26&quot; tv (ubuntu 11.10)"
date: 2011-11-05
forum: Hardware
---

### Post by Deminox on 2011-11-05
I have a Radeon HD 4650 graphics card. My on-board graphics is disabled
My desktop is a HP a6700f with an AMD Phenom XII quad 9150e quad core 1.8 ghz
I am using the HDMI output on the graphics card to my Sanyo TV (works great in Windows 7, have YET To get the aspect ration to work in any linux distro)

I have two problems. The FIRST is I cannot complete the upgrade for missing firmware for the graphics card. I get an error, I will post the error log after the next problem so the next problem does not get lost under hundreds of lines of code.

Problem two is in ANY linux distro, the screen when set to 16x9 fullscreen doesnt fit, its too big. The sides are off the screen by about a half an inch, and so far i have found nothing in linux to re-size the display manually. In Win7 (ad also in vista) this is not an issue, so i suspect its related to the graphics card. Yes, I can use 4x3 on the screen, it just seems such a waste. ALSO, i have tried using the different "PixShape" options built into the tv for dfferent aspect ratios. All have the same problem. I think Linux is just outputting to an area that doesnt full exist on my screen.

Anyways, here is the error log /var/log/jockey

2011-11-05 16:18:00,481 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0>
2011-11-05 16:18:03,316 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-11-05 16:18:03,583 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-05 16:18:03,594 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-05 16:18:03,652 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-05 16:18:03,683 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-05 16:18:03,724 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-05 16:18:03,764 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-05 16:18:03,765 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-05 16:18:03,765 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-05 16:18:03,789 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 16:18:03,795 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-05 16:18:03,795 DEBUG: fglrx.available: falling back to default
2011-11-05 16:18:04,017 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 16:18:04,022 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 16:18:04,032 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-05 16:18:04,033 DEBUG: fglrx.available: falling back to default
2011-11-05 16:18:04,117 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-05 16:18:04,117 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-05 16:18:04,126 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-05 16:18:04,128 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-05 16:18:04,128 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-05 16:18:04,128 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-05 16:18:04,143 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-05 16:18:04,154 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-05 16:18:04,154 DEBUG: nvidia.available: falling back to default
2011-11-05 16:18:04,230 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 16:18:04,238 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-05 16:18:04,249 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-05 16:18:04,250 DEBUG: nvidia.available: falling back to default
2011-11-05 16:18:04,331 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 16:18:04,336 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-05 16:18:04,345 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-05 16:18:04,345 DEBUG: nvidia.available: falling back to default
2011-11-05 16:18:04,402 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 16:18:04,402 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-05 16:18:04,419 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-05 16:18:04,430 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-05 16:18:04,431 DEBUG: nvidia.available: falling back to default
2011-11-05 16:18:04,508 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 16:18:04,513 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-05 16:18:04,519 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-05 16:18:04,519 DEBUG: nvidia.available: falling back to default
2011-11-05 16:18:04,573 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 16:18:04,578 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-05 16:18:04,585 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-05 16:18:04,586 DEBUG: nvidia.available: falling back to default
2011-11-05 16:18:04,635 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 16:18:04,635 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-05 16:18:04,641 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-05 16:18:04,641 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-05 16:18:04,665 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-05 16:18:04,666 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-05 16:18:04,761 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-05 16:18:04,763 DEBUG: Firmware for DVB cards not available
2011-11-05 16:18:04,763 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-05 16:18:04,801 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-05 16:18:04,843 DEBUG: Software modem not available
2011-11-05 16:18:04,843 DEBUG: all custom handlers loaded
2011-11-05 16:18:04,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 16:18:05,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2011-11-05 16:18:05,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 16:18:05,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 16:18:05,371 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 16:18:05,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 16:18:05,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 16:18:05,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 16:18:05,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 16:18:05,405 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 16:18:05,405 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 16:18:05,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,405 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 16:18:05,405 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 16:18:05,406 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-05 16:18:05,406 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,406 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-05 16:18:05,406 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 16:18:05,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 16:18:05,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 16:18:05,417 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2011-11-05 16:18:05,417 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 16:18:05,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 16:18:05,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 16:18:05,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 16:18:05,427 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 16:18:05,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 16:18:05,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:05,446 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-05 16:18:05,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:05,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 16:18:05,450 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb'}
2011-11-05 16:18:05,450 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 16:18:05,451 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 16:18:05,451 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 16:18:05,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 16:18:05,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 16:18:05,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 16:18:05,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 16:18:05,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 16:18:05,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-05 16:18:05,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 16:18:05,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:05,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 16:18:05,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:05,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 16:18:05,864 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2011-11-05 16:18:05,865 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 16:18:05,900 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 16:18:05,900 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,900 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-11-05 16:18:05,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 16:18:05,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 16:18:05,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 16:18:05,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 16:18:05,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 16:18:05,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 16:18:05,915 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-11-05 16:18:05,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,915 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-11-05 16:18:05,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 16:18:05,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 16:18:05,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 16:18:05,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 16:18:05,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 16:18:05,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:05,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-11-05 16:18:05,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 16:18:05,946 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-11-05 16:18:05,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 16:18:05,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-05 16:18:05,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:05,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-05 16:18:06,319 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 16:18:06,320 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 16:18:05,952 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 16:18:06,328 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 16:18:06,339 DEBUG: fglrx.available: falling back to default
2011-11-05 16:18:06,425 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 16:18:06,425 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 16:18:06,376 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 16:18:06,426 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-05 16:18:06,477 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 16:18:06,478 DEBUG: fglrx is not the alternative in use
2011-11-05 16:18:06,426 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 16:18:06,486 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 16:18:06,497 DEBUG: fglrx.available: falling back to default
2011-11-05 16:18:06,590 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 16:18:06,590 DEBUG: fglrx is not the alternative in use
2011-11-05 16:18:06,543 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 16:18:06,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 16:18:06,591 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 16:18:06,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:06,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 16:18:06,602 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2011-11-05 16:18:06,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 16:18:06,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x21778c0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 16:18:06,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 16:18:06,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 16:18:06,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 16:18:06,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 16:18:06,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 16:18:06,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 16:18:06,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 16:18:06,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 16:18:06,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 16:18:06,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 16:18:06,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 16:18:06,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 16:18:06,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 16:18:06,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 16:18:06,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 16:18:06,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 16:18:06,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 16:18:06,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 16:18:06,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:06,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:06,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 16:18:06,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 16:18:06,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 16:18:06,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 16:18:06,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 16:18:06,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 16:18:06,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:06,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 16:18:06,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:06,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 16:18:06,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 16:18:06,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 16:18:06,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 16:18:06,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 16:18:06,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 16:18:06,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x237ec20> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 16:18:06,655 DEBUG: handler xorg:fglrx_updates previously unseen
2011-11-05 16:18:06,657 DEBUG: handler xorg:fglrx previously unseen
2011-11-05 16:18:06,657 DEBUG: writing back check cache /var/cache/jockey/check
2011-11-05 16:18:06,700 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 16:18:06,701 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 16:18:06,753 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 16:18:06,754 DEBUG: fglrx is not the alternative in use
2011-11-05 16:18:06,834 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 16:18:06,834 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:37:33,244 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0>
2011-11-05 17:37:36,033 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-11-05 17:37:36,189 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-05 17:37:36,199 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-05 17:37:36,260 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-05 17:37:36,301 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-05 17:37:36,341 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-05 17:37:36,385 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-05 17:37:36,386 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-05 17:37:36,386 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-05 17:37:36,443 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:37:36,454 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-05 17:37:36,454 DEBUG: fglrx.available: falling back to default
2011-11-05 17:37:36,659 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:37:36,666 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:37:36,676 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-05 17:37:36,677 DEBUG: fglrx.available: falling back to default
2011-11-05 17:37:36,770 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-05 17:37:36,771 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-05 17:37:36,780 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-05 17:37:36,781 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-05 17:37:36,781 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-05 17:37:36,781 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-05 17:37:36,797 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-05 17:37:36,807 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-05 17:37:36,807 DEBUG: nvidia.available: falling back to default
2011-11-05 17:37:36,891 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:37:36,899 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-05 17:37:36,909 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-05 17:37:36,910 DEBUG: nvidia.available: falling back to default
2011-11-05 17:37:36,993 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:37:37,000 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-05 17:37:37,010 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-05 17:37:37,011 DEBUG: nvidia.available: falling back to default
2011-11-05 17:37:37,094 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:37:37,095 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-05 17:37:37,133 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-05 17:37:37,143 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-05 17:37:37,144 DEBUG: nvidia.available: falling back to default
2011-11-05 17:37:37,227 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:37:37,235 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-05 17:37:37,245 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-05 17:37:37,246 DEBUG: nvidia.available: falling back to default
2011-11-05 17:37:37,329 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:37:37,337 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-05 17:37:37,347 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-05 17:37:37,348 DEBUG: nvidia.available: falling back to default
2011-11-05 17:37:37,432 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:37:37,432 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-05 17:37:37,443 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-05 17:37:37,444 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-05 17:37:37,507 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-05 17:37:37,508 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-05 17:37:37,616 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-05 17:37:37,618 DEBUG: Firmware for DVB cards not available
2011-11-05 17:37:37,618 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-05 17:37:37,664 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-05 17:37:37,706 DEBUG: Software modem not available
2011-11-05 17:37:37,706 DEBUG: all custom handlers loaded
2011-11-05 17:37:37,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 17:37:38,082 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2011-11-05 17:37:38,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 17:37:38,249 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:37:38,250 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 17:37:38,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 17:37:38,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:37:38,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 17:37:38,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:37:38,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 17:37:38,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:37:38,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 17:37:38,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 17:37:38,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-05 17:37:38,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-05 17:37:38,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 17:37:38,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 17:37:38,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 17:37:38,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2011-11-05 17:37:38,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 17:37:38,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 17:37:38,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:37:38,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 17:37:38,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:37:38,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 17:37:38,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:38,325 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-05 17:37:38,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:38,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 17:37:38,329 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb'}
2011-11-05 17:37:38,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 17:37:38,330 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:37:38,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 17:37:38,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 17:37:38,725 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:37:38,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,726 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:37:38,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 17:37:38,726 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:37:38,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,726 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-05 17:37:38,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 17:37:38,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:38,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 17:37:38,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:38,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 17:37:38,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2011-11-05 17:37:38,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 17:37:38,787 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 17:37:38,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-11-05 17:37:38,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 17:37:38,789 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 17:37:38,789 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 17:37:38,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 17:37:38,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 17:37:38,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 17:37:38,802 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-11-05 17:37:38,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,802 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-11-05 17:37:38,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 17:37:38,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:37:38,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 17:37:38,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:37:38,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 17:37:38,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:38,805 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-11-05 17:37:38,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 17:37:38,833 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-11-05 17:37:38,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 17:37:38,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-05 17:37:38,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:38,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-05 17:37:39,192 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:39,193 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:37:38,839 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 17:37:39,201 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:37:39,212 DEBUG: fglrx.available: falling back to default
2011-11-05 17:37:39,313 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:39,313 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:37:39,262 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 17:37:39,314 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-05 17:37:39,365 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:39,366 DEBUG: fglrx is not the alternative in use
2011-11-05 17:37:39,314 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 17:37:39,374 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:37:39,384 DEBUG: fglrx.available: falling back to default
2011-11-05 17:37:39,485 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:39,485 DEBUG: fglrx is not the alternative in use
2011-11-05 17:37:39,434 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 17:37:39,486 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 17:37:39,486 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:37:39,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:39,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 17:37:39,497 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2011-11-05 17:37:39,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:37:39,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e78c0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 17:37:39,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 17:37:39,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 17:37:39,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 17:37:39,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 17:37:39,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:37:39,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 17:37:39,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:37:39,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 17:37:39,500 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 17:37:39,500 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 17:37:39,500 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 17:37:39,500 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 17:37:39,500 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 17:37:39,501 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 17:37:39,501 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 17:37:39,501 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:37:39,501 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 17:37:39,501 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 17:37:39,502 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:39,502 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:39,502 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 17:37:39,502 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 17:37:39,502 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 17:37:39,503 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 17:37:39,503 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 17:37:39,503 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 17:37:39,503 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:39,503 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 17:37:39,503 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:39,504 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 17:37:39,504 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 17:37:39,504 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 17:37:39,504 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 17:37:39,504 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 17:37:39,505 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 17:37:39,506 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 17:37:39,506 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 17:37:39,506 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24eec20> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 17:37:39,586 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:39,586 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:37:39,718 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:39,719 DEBUG: fglrx is not the alternative in use
2011-11-05 17:37:39,806 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:39,806 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:37:39,920 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:39,921 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:37:40,003 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:40,003 DEBUG: fglrx is not the alternative in use
2011-11-05 17:37:46,669 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:46,669 DEBUG: fglrx is not the alternative in use
2011-11-05 17:37:50,289 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:50,290 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:37:53,167 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:53,168 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:37:56,236 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:37:56,237 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:38:00,250 DEBUG: Installing package: fglrx-updates
2011-11-05 17:38:00,942 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2011-11-05 17:38:01,188 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:38:01,189 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-11-05 17:38:01,189 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-11-05 17:38:01,205 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-11-05 17:38:01,370 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:01,371 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:38:07,787 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:07,788 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:38:07,884 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:07,884 DEBUG: fglrx is not the alternative in use
2011-11-05 17:38:07,985 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:07,986 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:38:08,106 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:08,107 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:38:08,195 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:08,196 DEBUG: fglrx is not the alternative in use
2011-11-05 17:38:09,490 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:09,490 DEBUG: fglrx is not the alternative in use
2011-11-05 17:38:10,614 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:10,615 DEBUG: fglrx is not the alternative in use
2011-11-05 17:38:10,883 DEBUG: Installing package: fglrx
2011-11-05 17:38:11,572 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2011-11-05 17:38:11,830 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:38:11,831 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-11-05 17:38:11,832 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-11-05 17:38:11,849 ERROR: xorg:fglrx: get_alternative_by_name(fglrx) returned nothing
2011-11-05 17:38:11,976 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:11,977 DEBUG: fglrx is not the alternative in use
2011-11-05 17:38:15,693 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:15,693 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:38:15,799 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:15,799 DEBUG: fglrx is not the alternative in use
2011-11-05 17:38:15,909 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:15,909 DEBUG: fglrx is not the alternative in use
2011-11-05 17:38:16,049 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:16,050 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:38:16,154 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:38:16,154 DEBUG: fglrx is not the alternative in use
2011-11-05 17:38:20,949 DEBUG: Shutting down
2011-11-05 17:43:43,795 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8>
2011-11-05 17:43:46,832 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-11-05 17:43:46,957 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-05 17:43:46,958 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-05 17:43:47,010 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-05 17:43:47,052 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-05 17:43:47,063 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-05 17:43:47,109 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-05 17:43:47,110 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-05 17:43:47,111 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-05 17:43:47,125 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:43:47,137 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-05 17:43:47,138 DEBUG: fglrx.available: falling back to default
2011-11-05 17:43:47,343 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:43:47,352 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:43:47,364 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-05 17:43:47,365 DEBUG: fglrx.available: falling back to default
2011-11-05 17:43:47,463 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-05 17:43:47,464 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-05 17:43:47,474 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-05 17:43:47,476 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-05 17:43:47,476 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-05 17:43:47,476 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-05 17:43:47,493 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-05 17:43:47,504 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-05 17:43:47,505 DEBUG: nvidia.available: falling back to default
2011-11-05 17:43:47,592 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:43:47,601 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-05 17:43:47,613 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-05 17:43:47,614 DEBUG: nvidia.available: falling back to default
2011-11-05 17:43:47,702 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:43:47,711 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-05 17:43:47,722 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-05 17:43:47,723 DEBUG: nvidia.available: falling back to default
2011-11-05 17:43:47,811 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:43:47,812 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-05 17:43:47,822 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-05 17:43:47,833 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-05 17:43:47,834 DEBUG: nvidia.available: falling back to default
2011-11-05 17:43:47,922 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:43:47,931 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-05 17:43:47,943 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-05 17:43:47,944 DEBUG: nvidia.available: falling back to default
2011-11-05 17:43:48,031 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:43:48,040 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-05 17:43:48,052 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-05 17:43:48,053 DEBUG: nvidia.available: falling back to default
2011-11-05 17:43:48,141 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:43:48,142 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-05 17:43:48,152 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-05 17:43:48,153 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-05 17:43:48,196 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-05 17:43:48,197 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-05 17:43:48,253 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-05 17:43:48,254 DEBUG: Firmware for DVB cards not available
2011-11-05 17:43:48,255 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-05 17:43:48,302 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-05 17:43:48,322 DEBUG: Software modem not available
2011-11-05 17:43:48,323 DEBUG: all custom handlers loaded
2011-11-05 17:43:48,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 17:43:48,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2011-11-05 17:43:48,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 17:43:48,811 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:43:48,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 17:43:48,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 17:43:48,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:43:48,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 17:43:48,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:43:48,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 17:43:48,847 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:43:48,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 17:43:48,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 17:43:48,848 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-05 17:43:48,848 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,848 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-05 17:43:48,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 17:43:48,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 17:43:48,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 17:43:48,859 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2011-11-05 17:43:48,859 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 17:43:48,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 17:43:48,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:43:48,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 17:43:48,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:43:48,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 17:43:48,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:48,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-05 17:43:48,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:48,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 17:43:48,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb'}
2011-11-05 17:43:48,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 17:43:48,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:43:48,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:48,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 17:43:48,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 17:43:49,287 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:43:49,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,288 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:43:49,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 17:43:49,288 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:43:49,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,289 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-05 17:43:49,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 17:43:49,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:49,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 17:43:49,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:49,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 17:43:49,314 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2011-11-05 17:43:49,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 17:43:49,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 17:43:49,351 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,351 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-11-05 17:43:49,351 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 17:43:49,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 17:43:49,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 17:43:49,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 17:43:49,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 17:43:49,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 17:43:49,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-11-05 17:43:49,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-11-05 17:43:49,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 17:43:49,366 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:43:49,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 17:43:49,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:43:49,367 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 17:43:49,367 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:49,368 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-11-05 17:43:49,368 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,368 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 17:43:49,396 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-11-05 17:43:49,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 17:43:49,402 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-05 17:43:49,402 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,402 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-05 17:43:49,454 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:49,455 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:43:49,402 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 17:43:49,465 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:43:49,477 DEBUG: fglrx.available: falling back to default
2011-11-05 17:43:49,585 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:49,586 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:43:49,530 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 17:43:49,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-05 17:43:49,638 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:49,639 DEBUG: fglrx is not the alternative in use
2011-11-05 17:43:49,586 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 17:43:49,647 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:43:49,658 DEBUG: fglrx.available: falling back to default
2011-11-05 17:43:49,754 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:49,755 DEBUG: fglrx is not the alternative in use
2011-11-05 17:43:49,708 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 17:43:49,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 17:43:49,756 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:43:49,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 17:43:49,770 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2011-11-05 17:43:49,771 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:43:49,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1548ea8> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 17:43:49,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 17:43:49,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 17:43:49,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 17:43:49,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 17:43:49,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:43:49,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 17:43:49,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:43:49,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 17:43:49,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 17:43:49,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 17:43:49,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 17:43:49,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 17:43:49,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 17:43:49,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 17:43:49,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 17:43:49,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:43:49,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 17:43:49,775 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 17:43:49,775 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:49,775 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:49,775 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 17:43:49,775 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 17:43:49,775 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 17:43:49,776 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 17:43:49,776 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 17:43:49,776 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 17:43:49,776 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:49,776 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 17:43:49,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 17:43:49,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1750f38> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 17:43:49,915 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:49,916 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:43:50,018 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,019 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:43:50,088 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,089 DEBUG: fglrx is not the alternative in use
2011-11-05 17:43:50,190 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,241 DEBUG: fglrx is not the alternative in use
2011-11-05 17:43:50,311 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,312 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:43:50,403 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,404 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:43:50,519 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,520 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:43:50,613 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,614 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:43:50,674 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,675 DEBUG: fglrx is not the alternative in use
2011-11-05 17:43:50,769 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:43:50,770 DEBUG: fglrx is not the alternative in use
2011-11-05 17:48:44,321 DEBUG: Shutting down
2011-11-05 17:48:49,161 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0>
2011-11-05 17:48:51,880 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-11-05 17:48:52,008 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-05 17:48:52,009 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-05 17:48:52,061 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-05 17:48:52,104 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-05 17:48:52,116 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-05 17:48:52,161 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-05 17:48:52,161 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-05 17:48:52,162 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-05 17:48:52,177 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:48:52,189 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-05 17:48:52,190 DEBUG: fglrx.available: falling back to default
2011-11-05 17:48:52,359 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:48:52,367 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:48:52,379 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-05 17:48:52,380 DEBUG: fglrx.available: falling back to default
2011-11-05 17:48:52,481 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-05 17:48:52,482 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-05 17:48:52,493 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-05 17:48:52,494 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-05 17:48:52,495 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-05 17:48:52,495 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-05 17:48:52,511 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-05 17:48:52,523 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-05 17:48:52,524 DEBUG: nvidia.available: falling back to default
2011-11-05 17:48:52,612 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:48:52,622 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-05 17:48:52,634 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-05 17:48:52,635 DEBUG: nvidia.available: falling back to default
2011-11-05 17:48:52,724 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:48:52,733 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-05 17:48:52,745 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-05 17:48:52,746 DEBUG: nvidia.available: falling back to default
2011-11-05 17:48:52,834 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:48:52,835 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-05 17:48:52,845 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-05 17:48:52,857 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-05 17:48:52,858 DEBUG: nvidia.available: falling back to default
2011-11-05 17:48:52,946 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:48:52,956 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-05 17:48:52,968 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-05 17:48:52,969 DEBUG: nvidia.available: falling back to default
2011-11-05 17:48:53,057 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:48:53,067 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-05 17:48:53,079 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-05 17:48:53,080 DEBUG: nvidia.available: falling back to default
2011-11-05 17:48:53,168 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:48:53,169 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-05 17:48:53,178 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-05 17:48:53,179 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-05 17:48:53,224 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-05 17:48:53,224 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-05 17:48:53,281 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-05 17:48:53,282 DEBUG: Firmware for DVB cards not available
2011-11-05 17:48:53,282 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-05 17:48:53,331 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-05 17:48:53,351 DEBUG: Software modem not available
2011-11-05 17:48:53,352 DEBUG: all custom handlers loaded
2011-11-05 17:48:53,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 17:48:53,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2011-11-05 17:48:53,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 17:48:53,836 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:48:53,837 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 17:48:53,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 17:48:53,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:48:53,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 17:48:53,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:48:53,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 17:48:53,872 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:48:53,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,872 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 17:48:53,872 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 17:48:53,873 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-05 17:48:53,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,873 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-05 17:48:53,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 17:48:53,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 17:48:53,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 17:48:53,883 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2011-11-05 17:48:53,883 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 17:48:53,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 17:48:53,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:48:53,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 17:48:53,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:48:53,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 17:48:53,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:53,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-05 17:48:53,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:53,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 17:48:53,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb'}
2011-11-05 17:48:53,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 17:48:53,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:48:53,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:53,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 17:48:53,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 17:48:54,308 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:48:54,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,308 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:48:54,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 17:48:54,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:48:54,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-05 17:48:54,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 17:48:54,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:54,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 17:48:54,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:54,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 17:48:54,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2011-11-05 17:48:54,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 17:48:54,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 17:48:54,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-11-05 17:48:54,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,370 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 17:48:54,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 17:48:54,372 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,372 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 17:48:54,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 17:48:54,381 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 17:48:54,381 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 17:48:54,384 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-11-05 17:48:54,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,385 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-11-05 17:48:54,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 17:48:54,385 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:48:54,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 17:48:54,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:48:54,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 17:48:54,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:54,387 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-11-05 17:48:54,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 17:48:54,415 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-11-05 17:48:54,416 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 17:48:54,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-05 17:48:54,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-05 17:48:54,475 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:48:54,476 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:48:54,421 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 17:48:54,485 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:48:54,498 DEBUG: fglrx.available: falling back to default
2011-11-05 17:48:54,609 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:48:54,610 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:48:54,552 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 17:48:54,610 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-05 17:48:54,663 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:48:54,664 DEBUG: fglrx is not the alternative in use
2011-11-05 17:48:54,611 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 17:48:54,674 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:48:54,687 DEBUG: fglrx.available: falling back to default
2011-11-05 17:48:54,793 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:48:54,794 DEBUG: fglrx is not the alternative in use
2011-11-05 17:48:54,737 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 17:48:54,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 17:48:54,795 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:48:54,795 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 17:48:54,806 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2011-11-05 17:48:54,807 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:48:54,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16c88c0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 17:48:54,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 17:48:54,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 17:48:54,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 17:48:54,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 17:48:54,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 17:48:54,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 17:48:54,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 17:48:54,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 17:48:54,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18d0c20> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 17:48:54,919 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:48:54,919 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:49:00,442 DEBUG: Shutting down
2011-11-05 17:51:48,104 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0>
2011-11-05 17:51:51,749 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-11-05 17:51:51,905 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-05 17:51:51,916 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-05 17:51:51,999 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-05 17:51:52,041 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-05 17:51:52,100 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-05 17:51:52,142 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-05 17:51:52,142 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-05 17:51:52,143 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-05 17:51:52,192 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:51:52,203 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-05 17:51:52,203 DEBUG: fglrx.available: falling back to default
2011-11-05 17:51:52,448 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:51:52,456 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:51:52,466 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-05 17:51:52,466 DEBUG: fglrx.available: falling back to default
2011-11-05 17:51:52,558 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-05 17:51:52,559 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-05 17:51:52,567 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-05 17:51:52,568 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-05 17:51:52,568 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-05 17:51:52,568 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-05 17:51:52,583 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-05 17:51:52,593 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-05 17:51:52,594 DEBUG: nvidia.available: falling back to default
2011-11-05 17:51:52,676 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:51:52,684 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-05 17:51:52,694 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-05 17:51:52,695 DEBUG: nvidia.available: falling back to default
2011-11-05 17:51:52,778 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:51:52,786 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-05 17:51:52,795 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-05 17:51:52,796 DEBUG: nvidia.available: falling back to default
2011-11-05 17:51:52,879 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:51:52,879 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-05 17:51:52,908 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-05 17:51:52,918 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-05 17:51:52,919 DEBUG: nvidia.available: falling back to default
2011-11-05 17:51:53,002 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:51:53,010 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-05 17:51:53,020 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-05 17:51:53,021 DEBUG: nvidia.available: falling back to default
2011-11-05 17:51:53,104 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 17:51:53,111 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-05 17:51:53,121 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-05 17:51:53,122 DEBUG: nvidia.available: falling back to default
2011-11-05 17:51:53,205 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 17:51:53,205 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-05 17:51:53,214 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-05 17:51:53,215 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-05 17:51:53,274 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-05 17:51:53,274 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-05 17:51:53,341 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-05 17:51:53,342 DEBUG: Firmware for DVB cards not available
2011-11-05 17:51:53,342 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-05 17:51:53,388 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-05 17:51:53,415 DEBUG: Software modem not available
2011-11-05 17:51:53,416 DEBUG: all custom handlers loaded
2011-11-05 17:51:53,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 17:51:53,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2011-11-05 17:51:53,936 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:53,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 17:51:53,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:51:53,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:53,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 17:51:53,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 17:51:53,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:51:53,949 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 17:51:53,949 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:51:53,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 17:51:53,977 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:51:53,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:53,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 17:51:53,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 17:51:53,978 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-05 17:51:53,978 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:53,978 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-05 17:51:53,978 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:53,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 17:51:53,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 17:51:53,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 17:51:53,989 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2011-11-05 17:51:53,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:53,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 17:51:53,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 17:51:53,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:51:53,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 17:51:53,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:51:53,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 17:51:54,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:54,018 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-05 17:51:54,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:54,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 17:51:54,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb'}
2011-11-05 17:51:54,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 17:51:54,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:51:54,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 17:51:54,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 17:51:54,415 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:51:54,415 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,415 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 17:51:54,415 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 17:51:54,416 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:51:54,416 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,416 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-05 17:51:54,416 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 17:51:54,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:54,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 17:51:54,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:54,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 17:51:54,441 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2011-11-05 17:51:54,441 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 17:51:54,477 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 17:51:54,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,477 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-11-05 17:51:54,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 17:51:54,478 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 17:51:54,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 17:51:54,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 17:51:54,488 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 17:51:54,488 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 17:51:54,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-11-05 17:51:54,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-11-05 17:51:54,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 17:51:54,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:51:54,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 17:51:54,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:51:54,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 17:51:54,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:54,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-11-05 17:51:54,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 17:51:54,523 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-11-05 17:51:54,523 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 17:51:54,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-05 17:51:54,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:54,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-05 17:51:54,980 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:54,981 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:51:54,528 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 17:51:54,990 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 17:51:55,000 DEBUG: fglrx.available: falling back to default
2011-11-05 17:51:55,100 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:55,101 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:51:55,050 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 17:51:55,101 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-05 17:51:55,151 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:55,152 DEBUG: fglrx is not the alternative in use
2011-11-05 17:51:55,102 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 17:51:55,160 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 17:51:55,170 DEBUG: fglrx.available: falling back to default
2011-11-05 17:51:55,270 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:55,270 DEBUG: fglrx is not the alternative in use
2011-11-05 17:51:55,219 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 17:51:55,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 17:51:55,271 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 17:51:55,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:55,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 17:51:55,282 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2011-11-05 17:51:55,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 17:51:55,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298c8c0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 17:51:55,283 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A6Dbc0Csc05i00')
2011-11-05 17:51:55,283 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 17:51:55,284 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 17:51:55,284 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 17:51:55,284 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:51:55,284 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 17:51:55,284 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:51:55,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 17:51:55,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 17:51:55,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 17:51:55,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'platform:regulatory')
2011-11-05 17:51:55,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A6Dbc06sc01i00')
2011-11-05 17:51:55,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A6Dbc01sc01i8a')
2011-11-05 17:51:55,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 17:51:55,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 17:51:55,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A6Dbc05sc00i00')
2011-11-05 17:51:55,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A6Dbc04sc03i00')
2011-11-05 17:51:55,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 17:51:55,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:55,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:55,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-11-05 17:51:55,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 17:51:55,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 17:51:55,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001B0Asd0000AA38bc04sc03i00')
2011-11-05 17:51:55,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-11-05 17:51:55,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.28:bd12/18/2008:svnHP-Pavilion:pnFQ565AA-ABAa6700f:pvr:rvnECS:rnNettle3:rvr2.2:cvnHewlett-Packard:ct3:cvr:')
2011-11-05 17:51:55,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:55,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 17:51:55,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:55,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A6Dbc06sc80i00')
2011-11-05 17:51:55,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc01ip02')
2011-11-05 17:51:55,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'usb:v046DpC521d5701dc00dsc00dp00ic03isc00ip00')
2011-11-05 17:51:55,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2011-11-05 17:51:55,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A6Dbc0Csc03i20')
2011-11-05 17:51:55,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 17:51:55,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-11-05 17:51:55,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 17:51:55,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 17:51:55,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 17:51:55,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 17:51:55,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 17:51:55,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A6Dbc0Csc00i10')
2011-11-05 17:51:55,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v00001002d00009498sv00001B0Asd00009039bc03sc00i00')
2011-11-05 17:51:55,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'input:b0003v046DpC521e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-11-05 17:51:55,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A6Dbc01sc01i85')
2011-11-05 17:51:55,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b94c20> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 17:51:55,438 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:55,438 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:51:55,565 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:55,566 DEBUG: fglrx is not the alternative in use
2011-11-05 17:51:55,653 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:55,654 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:51:55,768 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:55,768 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:51:55,848 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:55,848 DEBUG: fglrx is not the alternative in use
2011-11-05 17:51:58,392 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-05 17:51:58,393 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:52:03,166 DEBUG: Installing package: fglrx-updates
2011-11-05 17:52:03,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-11-05 17:52:03,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-11-05 17:52:04,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-11-05 17:52:04,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-11-05 17:52:04,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.002477
2011-11-05 17:52:04,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.175544
2011-11-05 17:52:04,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.175544
2011-11-05 17:52:04,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.178165
2011-11-05 17:52:04,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.332784
2011-11-05 17:52:04,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.338104
2011-11-05 17:52:05,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.565444
2011-11-05 17:52:05,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.567321
2011-11-05 17:52:05,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.304233
2011-11-05 17:52:06,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.031698
2011-11-05 17:52:06,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.793804
2011-11-05 17:52:07,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.521269
2011-11-05 17:52:07,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.201495
2011-11-05 17:52:08,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.935258
2011-11-05 17:52:08,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.199791
2011-11-05 17:52:09,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.234432
2011-11-05 17:52:09,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.514711
2011-11-05 17:52:10,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.732005
2011-11-05 17:52:10,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.867421
2011-11-05 17:52:11,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.021732
2011-11-05 17:52:11,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.172893
2011-11-05 17:52:12,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.383889
2011-11-05 17:52:12,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.569692
2011-11-05 17:52:13,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.815330
2011-11-05 17:52:13,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.045221
2011-11-05 17:52:14,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.281411
2011-11-05 17:52:14,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.593181
2011-11-05 17:52:15,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.961638
2011-11-05 17:52:15,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.396227
2011-11-05 17:52:16,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.871756
2011-11-05 17:52:16,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.940333
2011-11-05 17:52:16,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.946671
2011-11-05 17:52:16,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.057935
2011-11-05 17:52:16,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.058246
2011-11-05 17:52:16,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.477089
2011-11-05 17:52:17,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.968364
2011-11-05 17:52:17,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.459639
2011-11-05 17:52:18,274 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.941466
2011-11-05 17:52:18,775 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.640588
2011-11-05 17:52:19,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.314516
2011-11-05 17:52:19,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.824686
2011-11-05 17:52:20,279 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.846731
2011-11-05 17:52:20,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.925461
2011-11-05 17:52:21,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.089219
2011-11-05 17:52:21,783 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.360050
2011-11-05 17:52:22,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.549002
2011-11-05 17:52:22,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.712760
2011-11-05 17:52:23,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.879668
2011-11-05 17:52:23,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.059172
2011-11-05 17:52:24,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.285914
2011-11-05 17:52:24,791 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.468568
2011-11-05 17:52:25,292 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.654370
2011-11-05 17:52:25,793 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.877963
2011-11-05 17:52:26,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.111004
2011-11-05 17:52:26,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.391283
2011-11-05 17:52:27,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.671561
2011-11-05 17:52:27,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.964437
2011-11-05 17:52:28,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.326594
2011-11-05 17:52:28,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.726542
2011-11-05 17:52:29,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.233563
2011-11-05 17:52:29,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.866552
2011-11-05 17:52:30,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.490093
2011-11-05 17:52:30,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.189215
2011-11-05 17:52:31,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.869442
2011-11-05 17:52:31,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.489834
2011-11-05 17:52:32,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.144867
2011-11-05 17:52:32,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.017195
2011-11-05 17:52:33,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.395098
2011-11-05 17:52:33,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.395098
2011-11-05 17:52:34,315 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.565155
2011-11-05 17:52:34,816 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.779301
2011-11-05 17:52:35,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.012341
2011-11-05 17:52:35,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.270575
2011-11-05 17:52:36,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.503616
2011-11-05 17:52:36,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.695717
2011-11-05 17:52:37,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.903564
2011-11-05 17:52:37,823 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.142903
2011-11-05 17:52:38,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.404287
2011-11-05 17:52:38,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.675118
2011-11-05 17:52:39,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.905009
2011-11-05 17:52:39,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.188437
2011-11-05 17:52:40,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.478163
2011-11-05 17:52:40,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.849769
2011-11-05 17:52:41,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.180434
2011-11-05 17:52:41,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.548890
2011-11-05 17:52:42,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.974032
2011-11-05 17:52:42,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.389726
2011-11-05 17:52:43,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.389726
2011-11-05 17:52:43,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.389726
2011-11-05 17:52:44,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.389726
2011-11-05 17:52:44,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.389726
2011-11-05 17:52:45,342 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.392875
2011-11-05 17:52:45,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.644811
2011-11-05 17:52:46,345 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.947134
2011-11-05 17:52:46,846 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.230562
2011-11-05 17:52:47,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.428962
2011-11-05 17:52:47,849 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.451006
2011-11-05 17:52:48,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.451006
2011-11-05 17:52:48,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.599018
2011-11-05 17:52:49,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.772224
2011-11-05 17:52:49,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.011563
2011-11-05 17:52:50,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.238305
2011-11-05 17:52:50,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.465048
2011-11-05 17:52:51,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.663447
2011-11-05 17:52:51,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.820907
2011-11-05 17:52:52,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.959472
2011-11-05 17:52:52,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.132678
2011-11-05 17:52:53,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.290137
2011-11-05 17:52:53,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.390912
2011-11-05 17:52:54,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.475940
2011-11-05 17:52:54,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.557819
2011-11-05 17:52:55,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.589311
2011-11-05 17:52:55,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.668041
2011-11-05 17:52:56,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.781412
2011-11-05 17:52:56,871 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.891634
2011-11-05 17:52:57,372 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.964066
2011-11-05 17:52:57,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.064840
2011-11-05 17:52:58,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.168764
2011-11-05 17:52:58,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.291582
2011-11-05 17:52:59,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.414401
2011-11-05 17:52:59,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.552966
2011-11-05 17:53:00,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.704127
2011-11-05 17:53:00,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.908825
2011-11-05 17:53:01,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.100926
2011-11-05 17:53:01,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.286729
2011-11-05 17:53:02,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.504024
2011-11-05 17:53:02,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.743363
2011-11-05 17:53:03,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.989000
2011-11-05 17:53:03,888 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.360605
2011-11-05 17:53:04,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.792045
2011-11-05 17:53:04,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.295917
2011-11-05 17:53:05,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.051725
2011-11-05 17:53:05,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.741399
2011-11-05 17:53:06,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.449968
2011-11-05 17:53:06,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.067211
2011-11-05 17:53:07,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.542740
2011-11-05 17:53:07,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.043463
2011-11-05 17:53:08,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.433963
2011-11-05 17:53:08,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.903194
2011-11-05 17:53:09,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.947282
2011-11-05 17:53:09,903 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.148831
2011-11-05 17:53:10,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.375573
2011-11-05 17:53:10,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.577122
2011-11-05 17:53:11,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.744029
2011-11-05 17:53:11,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.873146
2011-11-05 17:53:12,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.018010
2011-11-05 17:53:12,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.121933
2011-11-05 17:53:13,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.273095
2011-11-05 17:53:13,913 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.427405
2011-11-05 17:53:14,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.603760
2011-11-05 17:53:14,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.754922
2011-11-05 17:53:15,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.906083
2011-11-05 17:53:15,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.126527
2011-11-05 17:53:16,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.296584
2011-11-05 17:53:16,921 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.491834
2011-11-05 17:53:17,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.693383
2011-11-05 17:53:17,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.901230
2011-11-05 17:53:18,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.118525
2011-11-05 17:53:18,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.364162
2011-11-05 17:53:19,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.647590
2011-11-05 17:53:19,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.968808
2011-11-05 17:53:20,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.334115
2011-11-05 17:53:20,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.771853
2011-11-05 17:53:21,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.282023
2011-11-05 17:53:21,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.744956
2011-11-05 17:53:22,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.233081
2011-11-05 17:53:22,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.607836
2011-11-05 17:53:23,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.105409
2011-11-05 17:53:23,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.665966
2011-11-05 17:53:24,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.072213
2011-11-05 17:53:24,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.541443
2011-11-05 17:53:25,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.563488
2011-11-05 17:53:25,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.563488
2011-11-05 17:53:26,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.686306
2011-11-05 17:53:26,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.928795
2011-11-05 17:53:27,447 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.114597
2011-11-05 17:53:27,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.136642
2011-11-05 17:53:28,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.284654
2011-11-05 17:53:28,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.483053
2011-11-05 17:53:29,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.684602
2011-11-05 17:53:29,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.886151
2011-11-05 17:53:30,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.078252
2011-11-05 17:53:30,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.301845
2011-11-05 17:53:31,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.544333
2011-11-05 17:53:31,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.802567
2011-11-05 17:53:32,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.054503
2011-11-05 17:53:32,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.337931
2011-11-05 17:53:33,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.649701
2011-11-05 17:53:33,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.021307
2011-11-05 17:53:34,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.433852
2011-11-05 17:53:34,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.899933
2011-11-05 17:53:35,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.451043
2011-11-05 17:53:35,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.989555
2011-11-05 17:53:36,470 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.603649
2011-11-05 17:53:36,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.359457
2011-11-05 17:53:37,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.074324
2011-11-05 17:53:37,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.524660
2011-11-05 17:53:38,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.581345
2011-11-05 17:53:38,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.581345
2011-11-05 17:53:39,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.612837
2011-11-05 17:53:39,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.612837
2011-11-05 17:53:40,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.615986
2011-11-05 17:53:40,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.874221
2011-11-05 17:53:41,482 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.006487
2011-11-05 17:53:41,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.173394
2011-11-05 17:53:42,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.318258
2011-11-05 17:53:42,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.453673
2011-11-05 17:53:43,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.589089
2011-11-05 17:53:43,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.771742
2011-11-05 17:53:44,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.963843
2011-11-05 17:53:44,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.162243
2011-11-05 17:53:45,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.388985
2011-11-05 17:53:45,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.640921
2011-11-05 17:53:46,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.848768
2011-11-05 17:53:46,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.097554
2011-11-05 17:53:47,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.431369
2011-11-05 17:53:47,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.840765
2011-11-05 17:53:48,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.313145
2011-11-05 17:53:49,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.889448
2011-11-05 17:53:49,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.601167
2011-11-05 17:53:50,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.379019
2011-11-05 17:53:50,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.081290
2011-11-05 17:53:51,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.808754
2011-11-05 17:53:51,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.432295
2011-11-05 17:53:52,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.175506
2011-11-05 17:53:52,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.934463
2011-11-05 17:53:53,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.098221
2011-11-05 17:53:53,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.098221
2011-11-05 17:53:54,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.277725
2011-11-05 17:53:54,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.409992
2011-11-05 17:53:55,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.598944
2011-11-05 17:53:55,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.784746
2011-11-05 17:53:56,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.998892
2011-11-05 17:53:56,518 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.209888
2011-11-05 17:53:57,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.461824
2011-11-05 17:53:57,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.735804
2011-11-05 17:53:58,022 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.003486
2011-11-05 17:53:58,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.286914
2011-11-05 17:53:59,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.639624
2011-11-05 17:53:59,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.052169
2011-11-05 17:54:00,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.584383
2011-11-05 17:54:00,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.075658
2011-11-05 17:54:01,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.551187
2011-11-05 17:54:01,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.089700
2011-11-05 17:54:02,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.574676
2011-11-05 17:54:02,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.132084
2011-11-05 17:54:03,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.302141
2011-11-05 17:54:03,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.402915
2011-11-05 17:54:04,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.402915
2011-11-05 17:54:04,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.450153
2011-11-05 17:54:05,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.465899
2011-11-05 17:54:05,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.519436
2011-11-05 17:54:06,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.550928
2011-11-05 17:54:06,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.579270
2011-11-05 17:54:07,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.639105
2011-11-05 17:54:07,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.708387
2011-11-05 17:54:08,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.796565
2011-11-05 17:54:08,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.916234
2011-11-05 17:54:09,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.039053
2011-11-05 17:54:09,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.193364
2011-11-05 17:54:10,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.303586
2011-11-05 17:54:10,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.344525
2011-11-05 17:54:11,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.536626
2011-11-05 17:54:11,573 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.728728
2011-11-05 17:54:12,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.958619
2011-11-05 17:54:12,576 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.138123
2011-11-05 17:54:13,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.364865
2011-11-05 17:54:13,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.607354
2011-11-05 17:54:14,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.846693
2011-11-05 17:54:14,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.139568
2011-11-05 17:54:15,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.391504
2011-11-05 17:54:15,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.656037
2011-11-05 17:54:16,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.040239
2011-11-05 17:54:16,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.474828
2011-11-05 17:54:17,087 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.915716
2011-11-05 17:54:17,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.350305
2011-11-05 17:54:18,090 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.929757
2011-11-05 17:54:18,591 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.569045
2011-11-05 17:54:19,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.331150
2011-11-05 17:54:19,594 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.976736
2011-11-05 17:54:20,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.757737
2011-11-05 17:54:20,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.019121
2011-11-05 17:54:21,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.075806
2011-11-05 17:54:21,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.368681
2011-11-05 17:54:22,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.718242
2011-11-05 17:54:22,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.023715
2011-11-05 17:54:23,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.401618
2011-11-05 17:54:23,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.725986
2011-11-05 17:54:24,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.072397
2011-11-05 17:54:24,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.365273
2011-11-05 17:54:25,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.648701
2011-11-05 17:54:25,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.985665
2011-11-05 17:54:26,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.357270
2011-11-05 17:54:26,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.757218
2011-11-05 17:54:27,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.257941
2011-11-05 17:54:27,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.724022
2011-11-05 17:54:28,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.253087
2011-11-05 17:54:28,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.955358
2011-11-05 17:54:29,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.667077
2011-11-05 17:54:29,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.385094
2011-11-05 17:54:29,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.761928
2011-11-05 17:54:29,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.768622
2011-11-05 17:54:30,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.562220
2011-11-05 17:54:30,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.308580
2011-11-05 17:54:31,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.966762
2011-11-05 17:54:31,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.709973
2011-11-05 17:54:32,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.292575
2011-11-05 17:54:32,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.336663
2011-11-05 17:54:33,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.494123
2011-11-05 17:54:33,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.516168
2011-11-05 17:54:34,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.582301
2011-11-05 17:54:34,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.648434
2011-11-05 17:54:35,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.768103
2011-11-05 17:54:35,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.890922
2011-11-05 17:54:36,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.026338
2011-11-05 17:54:36,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.174350
2011-11-05 17:54:37,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.350705
2011-11-05 17:54:37,921 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.568000
2011-11-05 17:54:38,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.851427
2011-11-05 17:54:38,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.229331
2011-11-05 17:54:39,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.736352
2011-11-05 17:54:39,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.243373
2011-11-05 17:54:40,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.737797
2011-11-05 17:54:40,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.238519
2011-11-05 17:54:41,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.751839
2011-11-05 17:54:41,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.466707
2011-11-05 17:54:42,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.165829
2011-11-05 17:54:42,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.880696
2011-11-05 17:54:43,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.611310
2011-11-05 17:54:43,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.228553
2011-11-05 17:54:44,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.845796
2011-11-05 17:54:44,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 100.000000
2011-11-05 17:54:45,700 DEBUG: install progress dpkg-exec 0.000000
2011-11-05 17:54:47,353 DEBUG: install progress patch 0.000000
2011-11-05 17:54:47,454 DEBUG: install progress patch 2.857140
2011-11-05 17:54:48,196 DEBUG: install progress patch 5.714290
2011-11-05 17:54:48,400 DEBUG: install progress patch 8.571430
2011-11-05 17:54:48,987 DEBUG: install progress dkms 8.571430
2011-11-05 17:54:48,988 DEBUG: install progress dkms 11.428600
2011-11-05 17:54:49,764 DEBUG: install progress dkms 14.285700
2011-11-05 17:54:49,901 DEBUG: install progress dkms 17.142900
2011-11-05 17:54:50,414 DEBUG: install progress fakeroot 17.142900
2011-11-05 17:54:50,415 DEBUG: install progress fakeroot 20.000000
2011-11-05 17:54:51,014 DEBUG: install progress fakeroot 22.857100
2011-11-05 17:54:51,143 DEBUG: install progress fakeroot 25.714300
2011-11-05 17:54:51,796 DEBUG: install progress libc6-i386 25.714300
2011-11-05 17:54:51,797 DEBUG: install progress libc6-i386 28.571400
2011-11-05 17:54:52,774 DEBUG: install progress libc6-i386 31.428600
2011-11-05 17:54:52,912 DEBUG: install progress libc6-i386 34.285700
2011-11-05 17:54:53,495 DEBUG: install progress lib32gcc1 34.285700
2011-11-05 17:54:53,495 DEBUG: install progress lib32gcc1 37.142900
2011-11-05 17:54:53,771 DEBUG: install progress lib32gcc1 40.000000
2011-11-05 17:54:53,841 DEBUG: install progress lib32gcc1 42.857100
2011-11-05 17:54:54,496 DEBUG: install progress fglrx-updates 42.857100
2011-11-05 17:54:54,597 DEBUG: install progress fglrx-updates 45.714300
2011-11-05 17:54:57,432 DEBUG: install progress fglrx-updates 48.571400
2011-11-05 17:54:57,503 DEBUG: install progress fglrx-updates 51.428600
2011-11-05 17:54:57,758 DEBUG: install progress fglrx-amdcccle-updates 51.428600
2011-11-05 17:54:57,758 DEBUG: install progress fglrx-amdcccle-updates 54.285700
2011-11-05 17:54:58,297 DEBUG: install progress fglrx-amdcccle-updates 57.142900
2011-11-05 17:54:58,376 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2011-11-05 17:54:58,467 DEBUG: install progress man-db 60.000000
2011-11-05 17:55:02,195 DEBUG: install progress ureadahead 60.000000
2011-11-05 17:55:02,556 DEBUG: install progress dpkg-exec 60.000000
2011-11-05 17:55:02,620 DEBUG: install progress patch 60.000000
2011-11-05 17:55:02,732 DEBUG: install progress patch 62.857100
2011-11-05 17:55:02,808 DEBUG: install progress patch 65.714300
2011-11-05 17:55:02,891 DEBUG: install progress dkms 65.714300
2011-11-05 17:55:04,318 DEBUG: install progress dkms 68.571400
2011-11-05 17:55:04,418 DEBUG: install progress dkms 71.428600
2011-11-05 17:55:04,503 DEBUG: install progress fakeroot 71.428600
2011-11-05 17:55:04,595 DEBUG: install progress fakeroot 74.285700
2011-11-05 17:55:04,716 DEBUG: install progress fakeroot 77.142900
2011-11-05 17:55:04,780 DEBUG: install progress libc6-i386 77.142900
2011-11-05 17:55:04,948 DEBUG: install progress libc6-i386 80.000000
2011-11-05 17:55:05,151 DEBUG: install progress libc6-i386 82.857100
2011-11-05 17:55:05,427 DEBUG: install progress lib32gcc1 82.857100
2011-11-05 17:55:05,511 DEBUG: install progress lib32gcc1 85.714300
2011-11-05 17:55:05,695 DEBUG: install progress lib32gcc1 88.571400
2011-11-05 17:55:05,795 DEBUG: install progress fglrx-updates 88.571400
2011-11-05 17:55:06,256 DEBUG: install progress fglrx-updates 91.428600
2011-11-05 17:55:33,226 DEBUG: install progress fglrx-updates 94.285700
2011-11-05 17:55:34,129 DEBUG: install progress bamfdaemon 94.285700
2011-11-05 17:55:34,513 DEBUG: install progress gnome-menus 94.285700
2011-11-05 17:55:34,922 DEBUG: install progress fglrx-amdcccle-updates 94.285700
2011-11-05 17:55:35,106 DEBUG: install progress fglrx-amdcccle-updates 97.142900
2011-11-05 17:55:35,248 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-11-05 17:55:35,424 DEBUG: install progress libc-bin 100.000000
2011-11-05 17:55:35,852 DEBUG: install progress initramfs-tools 100.000000
2011-11-05 17:55:53,598 DEBUG: Selecting previously deselected package patch.
(Reading database ... 127254 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-2_amd64.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_amd64.deb) ...
Selecting previously deselected package libc6-i386.
Unpacking libc6-i386 (from .../libc6-i386_2.13-20ubuntu5_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.881-0ubuntu6.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.881-0ubuntu6.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-2) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libc6-i386 (2.13-20ubuntu5) ...
Setting up lib32gcc1 (1:4.6.1-9ubuntu3) ...
Setting up fglrx-updates (2:8.881-0ubuntu6.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.881 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.881-0ubuntu6.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic

2011-11-05 17:55:53,930 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-11-05 17:55:54,066 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-11-05 17:55:54,216 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 17:55:54,217 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 17:55:54,280 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 17:55:54,280 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 18:05:44,997 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 18:05:44,998 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 18:05:45,061 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 18:05:45,062 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 18:05:45,158 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 18:05:45,159 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-05 18:05:45,260 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 18:05:45,261 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 18:05:45,324 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 18:05:45,324 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 18:05:45,444 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 18:05:45,444 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 18:05:45,507 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 18:05:45,508 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 18:05:45,598 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 18:05:45,599 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-05 18:05:48,843 DEBUG: Shutting down

---

