---
title: "ATI/AMD proprietary FGLRX graphics driver (post-release updates)"
date: 2012-07-15
forum: Hardware
---

### Post by pgfan92 on 2012-07-15
I tried to install a driver that ubuntu said I needed, however, I got this message:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

I checked the log, but all I see is that parts of the drivers aren't available, but why would ubuntu ask me to install something that isn't available?  Here's the log if someone more knowledgeable would like to take a look.

```
2012-07-15 16:13:59,140 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c>
2012-07-15 16:14:00,480 DEBUG: reading modalias file /lib/modules/3.2.0-26-generic-pae/modules.alias
2012-07-15 16:14:00,683 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-15 16:14:00,704 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-15 16:14:00,805 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-15 16:14:00,879 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-15 16:14:00,880 DEBUG: Firmware for DVB cards not available
2012-07-15 16:14:00,880 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-15 16:14:00,900 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-15 16:14:00,921 DEBUG: Software modem not available
2012-07-15 16:14:00,921 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-15 16:14:00,957 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-15 16:14:00,966 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-15 16:14:00,966 DEBUG: fglrx.available: falling back to default
2012-07-15 16:14:01,105 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-15 16:14:01,115 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-15 16:14:01,123 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-15 16:14:01,123 DEBUG: fglrx.available: falling back to default
2012-07-15 16:14:01,152 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-15 16:14:01,153 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-15 16:14:01,176 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-15 16:14:01,196 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-15 16:14:01,196 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-15 16:14:01,196 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-15 16:14:01,205 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-15 16:14:01,208 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-15 16:14:01,231 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-15 16:14:01,231 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-15 16:14:01,257 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-15 16:14:01,257 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-15 16:14:01,271 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-15 16:14:01,272 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-15 16:14:01,278 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-15 16:14:01,279 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-15 16:14:01,279 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-15 16:14:01,279 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-15 16:14:01,339 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-15 16:14:01,348 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-15 16:14:01,366 DEBUG: nvidia.available: falling back to default
2012-07-15 16:14:01,382 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-15 16:14:01,383 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-15 16:14:01,385 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-15 16:14:01,388 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-15 16:14:01,389 DEBUG: nvidia.available: falling back to default
2012-07-15 16:14:01,412 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-07-15 16:14:01,415 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-15 16:14:01,419 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-15 16:14:01,419 DEBUG: nvidia.available: falling back to default
2012-07-15 16:14:01,455 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-15 16:14:01,459 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-15 16:14:01,463 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-15 16:14:01,469 DEBUG: nvidia.available: falling back to default
2012-07-15 16:14:01,481 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-15 16:14:01,481 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-15 16:14:01,483 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-15 16:14:01,486 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-15 16:14:01,487 DEBUG: nvidia.available: falling back to default
2012-07-15 16:14:01,502 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-15 16:14:01,502 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-15 16:14:01,505 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-15 16:14:01,510 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-15 16:14:01,510 DEBUG: nvidia.available: falling back to default
2012-07-15 16:14:01,529 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-15 16:14:01,529 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-15 16:14:01,529 DEBUG: all custom handlers loaded
2012-07-15 16:14:01,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001002d0000970Fsv0000103Csd00002A92bc04sc03i00')
2012-07-15 16:14:01,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-15 16:14:01,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-15 16:14:01,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'input:b0003v192Fp0416e0111-e0,1,2,4,k110,111,112,r0,1,6,8,am4,lsfw')
2012-07-15 16:14:01,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-15 16:14:01,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-15 16:14:01,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-15 16:14:01,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-15 16:14:01,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00002A92bc02sc00i00')
2012-07-15 16:14:01,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-07-15 16:14:01,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'input:b0003v0461p4D8Ae0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-15 16:14:01,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-15 16:14:01,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,921 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-15 16:14:01,921 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'platform:eisa')
2012-07-15 16:14:01,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-15 16:14:01,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-15 16:14:01,942 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-15 16:14:01,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,942 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-15 16:14:01,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-15 16:14:01,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-15 16:14:01,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:01,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-15 16:14:01,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-15 16:14:01,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-07-15 16:14:01,956 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-07-15 16:14:01,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-15 16:14:01,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00002A92bc04sc03i00')
2012-07-15 16:14:01,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-15 16:14:01,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-15 16:14:01,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-15 16:14:01,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00002A92bc06sc00i00')
2012-07-15 16:14:01,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-15 16:14:01,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00002A92bc06sc01i00')
2012-07-15 16:14:01,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-15 16:14:01,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00002A92bc0Csc03i20')
2012-07-15 16:14:01,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'usb:v0461p4D8Ad0100dc00dsc00dp00ic03isc01ip01')
2012-07-15 16:14:01,969 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-15 16:14:01,969 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,969 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-07-15 16:14:01,969 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A92bc0Csc00i10')
2012-07-15 16:14:01,992 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-07-15 16:14:01,992 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-15 16:14:01,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-15 16:14:01,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-15 16:14:01,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-15 16:14:01,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:01,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'input:b0003v0461p4D8Ae0111-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-15 16:14:01,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-15 16:14:01,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-15 16:14:02,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-15 16:14:02,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-15 16:14:02,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-15 16:14:02,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr6.09:bd09/07/2010:svnHewlett-Packard:pnp6550z:pvr:rvnFOXCONN:rn2A92:rvr1.01:cvnHewlett-Packard:ct3:cvr:')
2012-07-15 16:14:02,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-15 16:14:02,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-15 16:14:02,017 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-15 16:14:02,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'usb:v03F0p7604d0100dc00dsc00dp00ic07isc01ip02')
2012-07-15 16:14:02,027 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usblp'}
2012-07-15 16:14:02,027 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-15 16:14:02,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00002A92bc0Csc05i00')
2012-07-15 16:14:02,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-07-15 16:14:02,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-07-15 16:14:02,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-15 16:14:02,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'usb:v0461p4D8Ad0100dc00dsc00dp00ic03isc00ip00')
2012-07-15 16:14:02,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-15 16:14:02,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001002d00004392sv0000103Csd00002A92bc01sc04i00')
2012-07-15 16:14:02,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001002d00009710sv0000103Csd00002A92bc03sc00i00')
2012-07-15 16:14:02,037 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-15 16:14:02,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,038 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-15 16:14:02,134 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:02,134 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:14:02,038 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-15 16:14:02,137 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-15 16:14:02,140 DEBUG: fglrx.available: falling back to default
2012-07-15 16:14:02,163 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:02,163 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:14:02,152 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-15 16:14:02,163 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-15 16:14:02,173 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:02,174 DEBUG: fglrx is not the alternative in use
2012-07-15 16:14:02,163 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-15 16:14:02,177 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-15 16:14:02,181 DEBUG: fglrx.available: falling back to default
2012-07-15 16:14:02,223 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:02,223 DEBUG: fglrx is not the alternative in use
2012-07-15 16:14:02,200 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-15 16:14:02,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-15 16:14:02,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'usb:v192Fp0416d0200dc00dsc00dp00ic03isc01ip02')
2012-07-15 16:14:02,224 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-15 16:14:02,224 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,224 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-15 16:14:02,224 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'platform:pcspkr')
2012-07-15 16:14:02,225 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-15 16:14:02,225 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,225 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-15 16:14:02,225 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-15 16:14:02,225 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-15 16:14:02,225 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,225 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-07-15 16:14:02,225 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-07-15 16:14:02,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-15 16:14:02,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-15 16:14:02,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7256d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001002d0000970Fsv0000103Csd00002A92bc04sc03i00')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'input:b0003v192Fp0416e0111-e0,1,2,4,k110,111,112,r0,1,6,8,am4,lsfw')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00002A92bc02sc00i00')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'input:b0003v0461p4D8Ae0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'platform:eisa')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-15 16:14:02,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00002A92bc04sc03i00')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00002A92bc06sc00i00')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00002A92bc06sc01i00')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00002A92bc0Csc03i20')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'usb:v0461p4D8Ad0100dc00dsc00dp00ic03isc01ip01')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A92bc0Csc00i10')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-15 16:14:02,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'input:b0003v0461p4D8Ae0111-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr6.09:bd09/07/2010:svnHewlett-Packard:pnp6550z:pvr:rvnFOXCONN:rn2A92:rvr1.01:cvnHewlett-Packard:ct3:cvr:')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'usb:v03F0p7604d0100dc00dsc00dp00ic07isc01ip02')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-15 16:14:02,228 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00002A92bc0Csc05i00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'usb:v0461p4D8Ad0100dc00dsc00dp00ic03isc00ip00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001002d00004392sv0000103Csd00002A92bc01sc04i00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001002d00009710sv0000103Csd00002A92bc03sc00i00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'usb:v192Fp0416d0200dc00dsc00dp00ic03isc01ip02')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'platform:pcspkr')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-15 16:14:02,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e7cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-15 16:14:02,254 DEBUG: handler xorg:fglrx_updates previously unseen
2012-07-15 16:14:02,255 DEBUG: handler xorg:fglrx previously unseen
2012-07-15 16:14:02,259 DEBUG: writing back check cache /var/cache/jockey/check
2012-07-15 16:14:02,276 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:02,276 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:14:02,289 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:02,289 DEBUG: fglrx is not the alternative in use
2012-07-15 16:14:02,320 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:02,320 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:14:52,042 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:52,042 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:14:52,160 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:52,161 DEBUG: fglrx is not the alternative in use
2012-07-15 16:14:52,221 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:52,222 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:14:52,305 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:52,306 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:14:52,358 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:52,359 DEBUG: fglrx is not the alternative in use
2012-07-15 16:14:55,364 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-15 16:14:55,365 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:15:00,594 DEBUG: Installing package: fglrx-updates
2012-07-15 16:15:01,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-07-15 16:15:01,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-07-15 16:15:01,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-07-15 16:15:01,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-07-15 16:15:01,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.002495
2012-07-15 16:15:02,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.072374
2012-07-15 16:15:02,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.189745
2012-07-15 16:15:02,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.192398
2012-07-15 16:15:03,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.350916
2012-07-15 16:15:03,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.353715
2012-07-15 16:15:03,772 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.518885
2012-07-15 16:15:03,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.544869
2012-07-15 16:15:03,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.546784
2012-07-15 16:15:04,342 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.737364
2012-07-15 16:15:04,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.858066
2012-07-15 16:15:05,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.143937
2012-07-15 16:15:05,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.309107
2012-07-15 16:15:06,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.512393
2012-07-15 16:15:06,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.699797
2012-07-15 16:15:07,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.890378
2012-07-15 16:15:07,852 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.982492
2012-07-15 16:15:08,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.131780
2012-07-15 16:15:08,855 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.338243
2012-07-15 16:15:09,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.551058
2012-07-15 16:15:09,857 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.760697
2012-07-15 16:15:10,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.970335
2012-07-15 16:15:10,860 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.097389
2012-07-15 16:15:11,361 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.383260
2012-07-15 16:15:11,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.542078
2012-07-15 16:15:12,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.691366
2012-07-15 16:15:12,865 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.834302
2012-07-15 16:15:13,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.929592
2012-07-15 16:15:13,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.069351
2012-07-15 16:15:14,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.193229
2012-07-15 16:15:14,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.282166
2012-07-15 16:15:15,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.437807
2012-07-15 16:15:15,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.533098
2012-07-15 16:15:16,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.644270
2012-07-15 16:15:16,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.752265
2012-07-15 16:15:17,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.876143
2012-07-15 16:15:17,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.980962
2012-07-15 16:15:18,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.111193
2012-07-15 16:15:18,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.235070
2012-07-15 16:15:19,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.368477
2012-07-15 16:15:19,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.530470
2012-07-15 16:15:20,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.625761
2012-07-15 16:15:20,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.778225
2012-07-15 16:15:21,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.829047
2012-07-15 16:15:21,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.933866
2012-07-15 16:15:22,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.006922
2012-07-15 16:15:22,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.079978
2012-07-15 16:15:23,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.146681
2012-07-15 16:15:23,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.219737
2012-07-15 16:15:24,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.337262
2012-07-15 16:15:24,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.448434
2012-07-15 16:15:25,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.550077
2012-07-15 16:15:25,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.594546
2012-07-15 16:15:26,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.607251
2012-07-15 16:15:26,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.619957
2012-07-15 16:15:27,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.648544
2012-07-15 16:15:27,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.772421
2012-07-15 16:15:28,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.899475
2012-07-15 16:15:28,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.017000
2012-07-15 16:15:29,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.112290
2012-07-15 16:15:29,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.201228
2012-07-15 16:15:30,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.309224
2012-07-15 16:15:30,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.414043
2012-07-15 16:15:31,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.522039
2012-07-15 16:15:31,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.620506
2012-07-15 16:15:32,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.734854
2012-07-15 16:15:32,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.849203
2012-07-15 16:15:33,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.934964
2012-07-15 16:15:33,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.039783
2012-07-15 16:15:34,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.147779
2012-07-15 16:15:34,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.274833
2012-07-15 16:15:35,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.408239
2012-07-15 16:15:35,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.513059
2012-07-15 16:15:36,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.630584
2012-07-15 16:15:36,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.716345
2012-07-15 16:15:37,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.811635
2012-07-15 16:15:37,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.935513
2012-07-15 16:15:38,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.046685
2012-07-15 16:15:38,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.145152
2012-07-15 16:15:39,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.230913
2012-07-15 16:15:39,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.313498
2012-07-15 16:15:40,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.450081
2012-07-15 16:15:40,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.554900
2012-07-15 16:15:41,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.672425
2012-07-15 16:15:41,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.745481
2012-07-15 16:15:42,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.859829
2012-07-15 16:15:42,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.936062
2012-07-15 16:15:43,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.996412
2012-07-15 16:15:43,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.996412
2012-07-15 16:15:44,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.050410
2012-07-15 16:15:44,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.104408
2012-07-15 16:15:45,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.158406
2012-07-15 16:15:45,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.231462
2012-07-15 16:15:46,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.310871
2012-07-15 16:15:46,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.406161
2012-07-15 16:15:47,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.520509
2012-07-15 16:15:47,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.676150
2012-07-15 16:15:48,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.844497
2012-07-15 16:15:48,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.958845
2012-07-15 16:15:49,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.101781
2012-07-15 16:15:49,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.292361
2012-07-15 16:15:50,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.441650
2012-07-15 16:15:50,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.552822
2012-07-15 16:15:51,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.686228
2012-07-15 16:15:51,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.806929
2012-07-15 16:15:52,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.876809
2012-07-15 16:15:52,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.000686
2012-07-15 16:15:53,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.095977
2012-07-15 16:15:53,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.188091
2012-07-15 16:15:54,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.280205
2012-07-15 16:15:54,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.381848
2012-07-15 16:15:55,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.473962
2012-07-15 16:15:55,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.585134
2012-07-15 16:15:56,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.693130
2012-07-15 16:15:56,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.839242
2012-07-15 16:15:57,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.023470
2012-07-15 16:15:57,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.226756
2012-07-15 16:15:58,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.430042
2012-07-15 16:15:58,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.646034
2012-07-15 16:15:59,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.855672
2012-07-15 16:15:59,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.065311
2012-07-15 16:16:00,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.274950
2012-07-15 16:16:01,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.481412
2012-07-15 16:16:01,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.646582
2012-07-15 16:16:02,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.846692
2012-07-15 16:16:02,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.030920
2012-07-15 16:16:03,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.227854
2012-07-15 16:16:03,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.424787
2012-07-15 16:16:04,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.548665
2012-07-15 16:16:04,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.669366
2012-07-15 16:16:05,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.678895
2012-07-15 16:16:05,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.682071
2012-07-15 16:16:06,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.875828
2012-07-15 16:16:06,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.952061
2012-07-15 16:16:07,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.056880
2012-07-15 16:16:07,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.155347
2012-07-15 16:16:08,018 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.266519
2012-07-15 16:16:08,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.403102
2012-07-15 16:16:09,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.477005
2012-07-15 16:16:09,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.650857
2012-07-15 16:16:10,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.787439
2012-07-15 16:16:10,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.911317
2012-07-15 16:16:11,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.016136
2012-07-15 16:16:11,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.149543
2012-07-15 16:16:12,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.263891
2012-07-15 16:16:12,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.365534
2012-07-15 16:16:13,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.470354
2012-07-15 16:16:13,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.610113
2012-07-15 16:16:14,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.749872
2012-07-15 16:16:14,535 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.892808
2012-07-15 16:16:15,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.092918
2012-07-15 16:16:15,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.283498
2012-07-15 16:16:16,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.509019
2012-07-15 16:16:16,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.718658
2012-07-15 16:16:17,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.928297
2012-07-15 16:16:17,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.137935
2012-07-15 16:16:18,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.258636
2012-07-15 16:16:18,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.538155
2012-07-15 16:16:19,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.712854
2012-07-15 16:16:19,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.871671
2012-07-15 16:16:20,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.040018
2012-07-15 16:16:20,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.205188
2012-07-15 16:16:21,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.373534
2012-07-15 16:16:21,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.557762
2012-07-15 16:16:22,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.735637
2012-07-15 16:16:22,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.938923
2012-07-15 16:16:23,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.139033
2012-07-15 16:16:23,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.351848
2012-07-15 16:16:24,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.536076
2012-07-15 16:16:24,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.710775
2012-07-15 16:16:25,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.917238
2012-07-15 16:16:25,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.126877
2012-07-15 16:16:26,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.215814
2012-07-15 16:16:26,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.527096
2012-07-15 16:16:27,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.733559
2012-07-15 16:16:27,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.920963
2012-07-15 16:16:28,069 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.111544
2012-07-15 16:16:28,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.225892
2012-07-15 16:16:29,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.381533
2012-07-15 16:16:29,573 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.426002
2012-07-15 16:16:30,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.521292
2012-07-15 16:16:30,576 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.734108
2012-07-15 16:16:31,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.835751
2012-07-15 16:16:31,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.007273
2012-07-15 16:16:32,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.156562
2012-07-15 16:16:32,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.302674
2012-07-15 16:16:33,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.455138
2012-07-15 16:16:33,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.582192
2012-07-15 16:16:34,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.712422
2012-07-15 16:16:34,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.864887
2012-07-15 16:16:35,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.020528
2012-07-15 16:16:35,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.138052
2012-07-15 16:16:36,090 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.211108
2012-07-15 16:16:36,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.261930
2012-07-15 16:16:37,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.376278
2012-07-15 16:16:37,594 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.449334
2012-07-15 16:16:38,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.512861
2012-07-15 16:16:38,597 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.598623
2012-07-15 16:16:39,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.668502
2012-07-15 16:16:39,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.741558
2012-07-15 16:16:40,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.773322
2012-07-15 16:16:40,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.881317
2012-07-15 16:16:41,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.941668
2012-07-15 16:16:41,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.011548
2012-07-15 16:16:42,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.065545
2012-07-15 16:16:42,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.125896
2012-07-15 16:16:43,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.176718
2012-07-15 16:16:43,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.176718
2012-07-15 16:16:44,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.268832
2012-07-15 16:16:44,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.319653
2012-07-15 16:16:45,114 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.386356
2012-07-15 16:16:45,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.465765
2012-07-15 16:16:46,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.535645
2012-07-15 16:16:46,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.634111
2012-07-15 16:16:47,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.742107
2012-07-15 16:16:47,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.875514
2012-07-15 16:16:48,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.075623
2012-07-15 16:16:48,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.193148
2012-07-15 16:16:49,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.488548
2012-07-15 16:16:49,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.695011
2012-07-15 16:16:50,127 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.872886
2012-07-15 16:16:50,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.984058
2012-07-15 16:16:51,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.168286
2012-07-15 16:16:51,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.288987
2012-07-15 16:16:52,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.396983
2012-07-15 16:16:52,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.470039
2012-07-15 16:16:53,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.600269
2012-07-15 16:16:53,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.673325
2012-07-15 16:16:54,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.806732
2012-07-15 16:16:54,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.917904
2012-07-15 16:16:55,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.006842
2012-07-15 16:16:55,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.035429
2012-07-15 16:16:56,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.156130
2012-07-15 16:16:56,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.184717
2012-07-15 16:16:57,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.248244
2012-07-15 16:16:57,647 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.311771
2012-07-15 16:16:58,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.397532
2012-07-15 16:16:58,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.470588
2012-07-15 16:16:59,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.556349
2012-07-15 16:16:59,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.635758
2012-07-15 16:17:00,153 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.734225
2012-07-15 16:17:00,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.829515
2012-07-15 16:17:01,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.937511
2012-07-15 16:17:01,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.070917
2012-07-15 16:17:02,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.236087
2012-07-15 16:17:02,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.439374
2012-07-15 16:17:03,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.645836
2012-07-15 16:17:03,663 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.855475
2012-07-15 16:17:04,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.065114
2012-07-15 16:17:04,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.271576
2012-07-15 16:17:05,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.458981
2012-07-15 16:17:05,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.544742
2012-07-15 16:17:06,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.722617
2012-07-15 16:17:06,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.897316
2012-07-15 16:17:07,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.938609
2012-07-15 16:17:07,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.075192
2012-07-15 16:17:08,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.186364
2012-07-15 16:17:08,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.313418
2012-07-15 16:17:09,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.437295
2012-07-15 16:17:09,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.535762
2012-07-15 16:17:10,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.643757
2012-07-15 16:17:10,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.732695
2012-07-15 16:17:11,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.824809
2012-07-15 16:17:11,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.913747
2012-07-15 16:17:12,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.015390
2012-07-15 16:17:12,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.117033
2012-07-15 16:17:13,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.215500
2012-07-15 16:17:13,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.329848
2012-07-15 16:17:14,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.425139
2012-07-15 16:17:14,691 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.545840
2012-07-15 16:17:15,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.634777
2012-07-15 16:17:15,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.761831
2012-07-15 16:17:16,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.866651
2012-07-15 16:17:16,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.942883
2012-07-15 16:17:17,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.082642
2012-07-15 16:17:17,699 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.171580
2012-07-15 16:17:18,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.263694
2012-07-15 16:17:18,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.308163
2012-07-15 16:17:19,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.422511
2012-07-15 16:17:19,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.473333
2012-07-15 16:17:20,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.555918
2012-07-15 16:17:20,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.613092
2012-07-15 16:17:21,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.676619
2012-07-15 16:17:21,710 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.727440
2012-07-15 16:17:22,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.787791
2012-07-15 16:17:22,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.841789
2012-07-15 16:17:23,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.892610
2012-07-15 16:17:23,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.962490
2012-07-15 16:17:24,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.026017
2012-07-15 16:17:24,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.099073
2012-07-15 16:17:25,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.165776
2012-07-15 16:17:25,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.238832
2012-07-15 16:17:26,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.334122
2012-07-15 16:17:26,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.423060
2012-07-15 16:17:27,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.511998
2012-07-15 16:17:27,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.610464
2012-07-15 16:17:28,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.712107
2012-07-15 16:17:28,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.816927
2012-07-15 16:17:29,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.934452
2012-07-15 16:17:29,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.017037
2012-07-15 16:17:30,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.134561
2012-07-15 16:17:30,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.233028
2012-07-15 16:17:31,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.328319
2012-07-15 16:17:31,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.379140
2012-07-15 16:17:32,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.477607
2012-07-15 16:17:32,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.614190
2012-07-15 16:17:33,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.750773
2012-07-15 16:17:33,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.931824
2012-07-15 16:17:34,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.141463
2012-07-15 16:17:34,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.347926
2012-07-15 16:17:35,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.557564
2012-07-15 16:17:35,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.770380
2012-07-15 16:17:36,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.964137
2012-07-15 16:17:36,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.170599
2012-07-15 16:17:37,249 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.332593
2012-07-15 16:17:37,750 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.507292
2012-07-15 16:17:38,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.672462
2012-07-15 16:17:38,753 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.853513
2012-07-15 16:17:39,254 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.056800
2012-07-15 16:17:39,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.250557
2012-07-15 16:17:40,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.460195
2012-07-15 16:17:40,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.634894
2012-07-15 16:17:41,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.790535
2012-07-15 16:17:41,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.025585
2012-07-15 16:17:42,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.219342
2012-07-15 16:17:42,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.390865
2012-07-15 16:17:43,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.635443
2012-07-15 16:17:43,764 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.765674
2012-07-15 16:17:44,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.007076
2012-07-15 16:17:44,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.296123
2012-07-15 16:17:45,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.505762
2012-07-15 16:17:45,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.683638
2012-07-15 16:17:46,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.871042
2012-07-15 16:17:46,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.052094
2012-07-15 16:17:47,451 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.198206
2012-07-15 16:17:47,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.366552
2012-07-15 16:17:48,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.560309
2012-07-15 16:17:48,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.661952
2012-07-15 16:17:49,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.947823
2012-07-15 16:17:49,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.062172
2012-07-15 16:17:50,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.354395
2012-07-15 16:17:50,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.516389
2012-07-15 16:17:51,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.684735
2012-07-15 16:17:52,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.859434
2012-07-15 16:17:52,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.942019
2012-07-15 16:17:53,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.196127
2012-07-15 16:17:53,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.370826
2012-07-15 16:17:54,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.555054
2012-07-15 16:17:54,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.736106
2012-07-15 16:17:55,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.913981
2012-07-15 16:17:55,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.945745
2012-07-15 16:17:56,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.180794
2012-07-15 16:17:56,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.295143
2012-07-15 16:17:57,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.406315
2012-07-15 16:17:57,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.476194
2012-07-15 16:17:58,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.577837
2012-07-15 16:17:58,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.689010
2012-07-15 16:17:59,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.774771
2012-07-15 16:17:59,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.924059
2012-07-15 16:18:00,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.006644
2012-07-15 16:18:00,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.136874
2012-07-15 16:18:01,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.222636
2012-07-15 16:18:01,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.311573
2012-07-15 16:18:02,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.422745
2012-07-15 16:18:02,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.524388
2012-07-15 16:18:03,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.635561
2012-07-15 16:18:03,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.762614
2012-07-15 16:18:04,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.899197
2012-07-15 16:18:04,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.035780
2012-07-15 16:18:05,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.239066
2012-07-15 16:18:05,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.391531
2012-07-15 16:18:06,061 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.658344
2012-07-15 16:18:06,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.820338
2012-07-15 16:18:07,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.118914
2012-07-15 16:18:07,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.280908
2012-07-15 16:18:08,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.433372
2012-07-15 16:18:08,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.595366
2012-07-15 16:18:09,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.703362
2012-07-15 16:18:09,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.814534
2012-07-15 16:18:10,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.947940
2012-07-15 16:18:10,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.020996
2012-07-15 16:18:11,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.090876
2012-07-15 16:18:11,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.167108
2012-07-15 16:18:12,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.249693
2012-07-15 16:18:12,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.284633
2012-07-15 16:18:13,334 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.398981
2012-07-15 16:18:13,835 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.491095
2012-07-15 16:18:14,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.548270
2012-07-15 16:18:14,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.621326
2012-07-15 16:18:15,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.697558
2012-07-15 16:18:15,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.761085
2012-07-15 16:18:16,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.821435
2012-07-15 16:18:16,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.900844
2012-07-15 16:18:17,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.970724
2012-07-15 16:18:17,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.040603
2012-07-15 16:18:18,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.066014
2012-07-15 16:18:18,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.110483
2012-07-15 16:18:19,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.161304
2012-07-15 16:18:19,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.228008
2012-07-15 16:18:20,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.272476
2012-07-15 16:18:20,852 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.326474
2012-07-15 16:18:21,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.386825
2012-07-15 16:18:21,855 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.418588
2012-07-15 16:18:22,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.504350
2012-07-15 16:18:22,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.567877
2012-07-15 16:18:23,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.631403
2012-07-15 16:18:23,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.666343
2012-07-15 16:18:24,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.761634
2012-07-15 16:18:24,879 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.837866
2012-07-15 16:18:25,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.920451
2012-07-15 16:18:25,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.983978
2012-07-15 16:18:26,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.057034
2012-07-15 16:18:26,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.139619
2012-07-15 16:18:27,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.215851
2012-07-15 16:18:27,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.257144
2012-07-15 16:18:28,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.361963
2012-07-15 16:18:28,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.422314
2012-07-15 16:18:29,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.489017
2012-07-15 16:18:29,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.571602
2012-07-15 16:18:30,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.651010
2012-07-15 16:18:30,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.746301
2012-07-15 16:18:31,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.844768
2012-07-15 16:18:31,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.949587
2012-07-15 16:18:32,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.057583
2012-07-15 16:18:32,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.108404
2012-07-15 16:18:33,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.260869
2012-07-15 16:18:33,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.365688
2012-07-15 16:18:34,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.473684
2012-07-15 16:18:34,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.572151
2012-07-15 16:18:35,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.667441
2012-07-15 16:18:35,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.797671
2012-07-15 16:18:36,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.927901
2012-07-15 16:18:36,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.029545
2012-07-15 16:18:37,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.140717
2012-07-15 16:18:37,913 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.216949
2012-07-15 16:18:38,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.261418
2012-07-15 16:18:38,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.356708
2012-07-15 16:18:39,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.445646
2012-07-15 16:18:39,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.531407
2012-07-15 16:18:40,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.626698
2012-07-15 16:18:40,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.725164
2012-07-15 16:18:41,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.829984
2012-07-15 16:18:41,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.950685
2012-07-15 16:18:42,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.106326
2012-07-15 16:18:42,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.296906
2012-07-15 16:18:43,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.500193
2012-07-15 16:18:43,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.690773
2012-07-15 16:18:44,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.862296
2012-07-15 16:18:44,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.998879
2012-07-15 16:18:45,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.084640
2012-07-15 16:18:45,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.313337
2012-07-15 16:18:46,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.475331
2012-07-15 16:18:46,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.646853
2012-07-15 16:18:47,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.821552
2012-07-15 16:18:47,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.005781
2012-07-15 16:18:48,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.190009
2012-07-15 16:18:48,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.336120
2012-07-15 16:18:49,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.479056
2012-07-15 16:18:49,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.641050
2012-07-15 16:18:50,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.717282
2012-07-15 16:18:50,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.898334
2012-07-15 16:18:51,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.136560
2012-07-15 16:18:52,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.292201
2012-07-15 16:18:52,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.470076
2012-07-15 16:18:53,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.657480
2012-07-15 16:18:53,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.829003
2012-07-15 16:18:54,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.978291
2012-07-15 16:18:54,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.130756
2012-07-15 16:18:55,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.308631
2012-07-15 16:18:55,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.416627
2012-07-15 16:18:56,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.518270
2012-07-15 16:18:56,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.632618
2012-07-15 16:18:57,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.667558
2012-07-15 16:18:57,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.791436
2012-07-15 16:18:58,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.874021
2012-07-15 16:18:58,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.940724
2012-07-15 16:18:59,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.007427
2012-07-15 16:18:59,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.096365
2012-07-15 16:19:00,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.185303
2012-07-15 16:19:00,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.267888
2012-07-15 16:19:01,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.356825
2012-07-15 16:19:01,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.414000
2012-07-15 16:19:02,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.525172
2012-07-15 16:19:02,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.588699
2012-07-15 16:19:03,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.661754
2012-07-15 16:19:03,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.715752
2012-07-15 16:19:04,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.744339
2012-07-15 16:19:04,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.795161
2012-07-15 16:19:05,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.811043
2012-07-15 16:19:05,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.858688
2012-07-15 16:19:06,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.899980
2012-07-15 16:19:06,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.947626
2012-07-15 16:19:07,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.982565
2012-07-15 16:19:07,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.068327
2012-07-15 16:19:08,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.106443
2012-07-15 16:19:08,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.163617
2012-07-15 16:19:09,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.236673
2012-07-15 16:19:09,830 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.312905
2012-07-15 16:19:10,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.385961
2012-07-15 16:19:10,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.455841
2012-07-15 16:19:11,334 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.525721
2012-07-15 16:19:11,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.589247
2012-07-15 16:19:12,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.659127
2012-07-15 16:19:12,838 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.659127
2012-07-15 16:19:13,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.770299
2012-07-15 16:19:13,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.852884
2012-07-15 16:19:14,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.894177
2012-07-15 16:19:14,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.941822
2012-07-15 16:19:15,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.995820
2012-07-15 16:19:15,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.014878
2012-07-15 16:19:16,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.033936
2012-07-15 16:19:16,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.075228
2012-07-15 16:19:17,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.106992
2012-07-15 16:19:17,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.135579
2012-07-15 16:19:18,535 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.224517
2012-07-15 16:19:19,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.281691
2012-07-15 16:19:19,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.338865
2012-07-15 16:19:20,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.399216
2012-07-15 16:19:20,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.437332
2012-07-15 16:19:21,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.535798
2012-07-15 16:19:21,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.589796
2012-07-15 16:19:22,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.650147
2012-07-15 16:19:22,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.716850
2012-07-15 16:19:23,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.777201
2012-07-15 16:19:23,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.818493
2012-07-15 16:19:24,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.990016
2012-07-15 16:19:24,597 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.155186
2012-07-15 16:19:25,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.342590
2012-07-15 16:19:25,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.485526
2012-07-15 16:19:26,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.733281
2012-07-15 16:19:26,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.942920
2012-07-15 16:19:27,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.111266
2012-07-15 16:19:27,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.244672
2012-07-15 16:19:28,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.409842
2012-07-15 16:19:28,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.536896
2012-07-15 16:19:29,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.597247
2012-07-15 16:19:29,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.784651
2012-07-15 16:19:30,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.918058
2012-07-15 16:19:30,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.057817
2012-07-15 16:19:31,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.159460
2012-07-15 16:19:31,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.219811
2012-07-15 16:19:32,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.324630
2012-07-15 16:19:32,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.423097
2012-07-15 16:19:33,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.489800
2012-07-15 16:19:33,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.559680
2012-07-15 16:19:34,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.575561
2012-07-15 16:19:34,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.689910
2012-07-15 16:19:35,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.756613
2012-07-15 16:19:35,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.832845
2012-07-15 16:19:36,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.902725
2012-07-15 16:19:36,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.966252
2012-07-15 16:19:37,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.048837
2012-07-15 16:19:37,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.137775
2012-07-15 16:19:38,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.233065
2012-07-15 16:19:38,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.322003
2012-07-15 16:19:39,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.376000
2012-07-15 16:19:39,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.376000
2012-07-15 16:19:40,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.550699
2012-07-15 16:19:40,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.620579
2012-07-15 16:19:41,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.712693
2012-07-15 16:19:41,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.776220
2012-07-15 16:19:42,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.836571
2012-07-15 16:19:42,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.900098
2012-07-15 16:19:43,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.912803
2012-07-15 16:19:43,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.043033
2012-07-15 16:19:44,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.147852
2012-07-15 16:19:44,932 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.249496
2012-07-15 16:19:45,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.347962
2012-07-15 16:19:45,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.452782
2012-07-15 16:19:46,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.538543
2012-07-15 16:19:46,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.614775
2012-07-15 16:19:47,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.706889
2012-07-15 16:19:47,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.764064
2012-07-15 16:19:48,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.859354
2012-07-15 16:19:48,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.945115
2012-07-15 16:19:49,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.059464
2012-07-15 16:19:49,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.107109
2012-07-15 16:19:50,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.186518
2012-07-15 16:19:50,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.297690
2012-07-15 16:19:51,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.364393
2012-07-15 16:19:51,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.380275
2012-07-15 16:19:52,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.497799
2012-07-15 16:19:53,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.561326
2012-07-15 16:19:53,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.628030
2012-07-15 16:19:54,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.697909
2012-07-15 16:19:54,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.780494
2012-07-15 16:19:55,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.824963
2012-07-15 16:19:55,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.920253
2012-07-15 16:19:56,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.037778
2012-07-15 16:19:56,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.133069
2012-07-15 16:19:57,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.202948
2012-07-15 16:19:58,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.333178
2012-07-15 16:19:58,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.422116
2012-07-15 16:19:59,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.504701
2012-07-15 16:19:59,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.625402
2012-07-15 16:20:00,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.752456
2012-07-15 16:20:00,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.885863
2012-07-15 16:20:01,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.035151
2012-07-15 16:20:01,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.124088
2012-07-15 16:20:02,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.349609
2012-07-15 16:20:02,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.508426
2012-07-15 16:20:03,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.527484
2012-07-15 16:20:03,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.708536
2012-07-15 16:20:04,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.816532
2012-07-15 16:20:04,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.902293
2012-07-15 16:20:05,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.984878
2012-07-15 16:20:05,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.083345
2012-07-15 16:20:06,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.175459
2012-07-15 16:20:06,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.251691
2012-07-15 16:20:07,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.381921
2012-07-15 16:20:07,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.467683
2012-07-15 16:20:08,249 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.562973
2012-07-15 16:20:08,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.709085
2012-07-15 16:20:09,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.807552
2012-07-15 16:20:10,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.909195
2012-07-15 16:20:10,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.004485
2012-07-15 16:20:11,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.071188
2012-07-15 16:20:11,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.156950
2012-07-15 16:20:12,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.201419
2012-07-15 16:20:12,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.271298
2012-07-15 16:20:13,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.331649
2012-07-15 16:20:13,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.379294
2012-07-15 16:20:14,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.433292
2012-07-15 16:20:14,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.477761
2012-07-15 16:20:15,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.541288
2012-07-15 16:20:15,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.598462
2012-07-15 16:20:16,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.731868
2012-07-15 16:20:16,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.817630
2012-07-15 16:20:17,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.906567
2012-07-15 16:20:17,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.001858
2012-07-15 16:20:18,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.039974
2012-07-15 16:20:18,830 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.141617
2012-07-15 16:20:19,331 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.227378
2012-07-15 16:20:19,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.297258
2012-07-15 16:20:20,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.389372
2012-07-15 16:20:20,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.462428
2012-07-15 16:20:21,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.554542
2012-07-15 16:20:21,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.602187
2012-07-15 16:20:22,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.662538
2012-07-15 16:20:22,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.729241
2012-07-15 16:20:23,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.780062
2012-07-15 16:20:23,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.827708
2012-07-15 16:20:24,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.900764
2012-07-15 16:20:24,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.976996
2012-07-15 16:20:25,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.078639
2012-07-15 16:20:25,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.154871
2012-07-15 16:20:26,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.272396
2012-07-15 16:20:27,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.361334
2012-07-15 16:20:27,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.437566
2012-07-15 16:20:28,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.520151
2012-07-15 16:20:28,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.599560
2012-07-15 16:20:29,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.669439
2012-07-15 16:20:29,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.736143
2012-07-15 16:20:30,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.840962
2012-07-15 16:20:30,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.948958
2012-07-15 16:20:31,249 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.034719
2012-07-15 16:20:31,750 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.088717
2012-07-15 16:20:32,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.152244
2012-07-15 16:20:32,753 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.196713
2012-07-15 16:20:33,254 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.260240
2012-07-15 16:20:33,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.336472
2012-07-15 16:20:34,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.396822
2012-07-15 16:20:34,758 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.409528
2012-07-15 16:20:35,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.476231
2012-07-15 16:20:35,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.520700
2012-07-15 16:20:36,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.571521
2012-07-15 16:20:36,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.628696
2012-07-15 16:20:37,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.695399
2012-07-15 16:20:37,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.768455
2012-07-15 16:20:38,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.847864
2012-07-15 16:20:38,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.908214
2012-07-15 16:20:39,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.993975
2012-07-15 16:20:39,802 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.076560
2012-07-15 16:20:40,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.165498
2012-07-15 16:20:40,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.241730
2012-07-15 16:20:41,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.311610
2012-07-15 16:20:41,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.387842
2012-07-15 16:20:42,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.467251
2012-07-15 16:20:42,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.524425
2012-07-15 16:20:43,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.581599
2012-07-15 16:20:43,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.667361
2012-07-15 16:20:44,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.740417
2012-07-15 16:20:44,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.838883
2012-07-15 16:20:45,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.956408
2012-07-15 16:20:45,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.102520
2012-07-15 16:20:46,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.258161
2012-07-15 16:20:46,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.388391
2012-07-15 16:20:47,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.455094
2012-07-15 16:20:47,823 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.566267
2012-07-15 16:20:48,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.594854
2012-07-15 16:20:48,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.632970
2012-07-15 16:20:49,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.671086
2012-07-15 16:20:49,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.750495
2012-07-15 16:20:50,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.775905
2012-07-15 16:20:50,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.839432
2012-07-15 16:20:51,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.902959
2012-07-15 16:20:51,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.972839
2012-07-15 16:20:52,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.001426
2012-07-15 16:20:52,932 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.084011
2012-07-15 16:20:53,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.153891
2012-07-15 16:20:53,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.204712
2012-07-15 16:20:54,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.268239
2012-07-15 16:20:54,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.331766
2012-07-15 16:20:55,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.401646
2012-07-15 16:20:55,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.455643
2012-07-15 16:20:56,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.519170
2012-07-15 16:20:56,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.582697
2012-07-15 16:20:57,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.627166
2012-07-15 16:20:57,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.681164
2012-07-15 16:20:58,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.690693
2012-07-15 16:20:58,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.741514
2012-07-15 16:20:59,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.776454
2012-07-15 16:20:59,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.827276
2012-07-15 16:21:00,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.874921
2012-07-15 16:21:00,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.932095
2012-07-15 16:21:01,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.951153
2012-07-15 16:21:01,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.040091
2012-07-15 16:21:02,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.113147
2012-07-15 16:21:02,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.189379
2012-07-15 16:21:03,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.303728
2012-07-15 16:21:03,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.453016
2012-07-15 16:21:04,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.538777
2012-07-15 16:21:04,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.751592
2012-07-15 16:21:05,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.831001
2012-07-15 16:21:05,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.996171
2012-07-15 16:21:06,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.091461
2012-07-15 16:21:06,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.183575
2012-07-15 16:21:07,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.221692
2012-07-15 16:21:07,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.313806
2012-07-15 16:21:08,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.364627
2012-07-15 16:21:08,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.412272
2012-07-15 16:21:09,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.466270
2012-07-15 16:21:09,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.523444
2012-07-15 16:21:10,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.558384
2012-07-15 16:21:10,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.596500
2012-07-15 16:21:11,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.653675
2012-07-15 16:21:11,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.666380
2012-07-15 16:21:12,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.720378
2012-07-15 16:21:13,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.758494
2012-07-15 16:21:13,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.815668
2012-07-15 16:21:14,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.860137
2012-07-15 16:21:14,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.888724
2012-07-15 16:21:15,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.920488
2012-07-15 16:21:15,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.923664
2012-07-15 16:21:16,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.952251
2012-07-15 16:21:16,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.984015
2012-07-15 16:21:17,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.009425
2012-07-15 16:21:17,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.063423
2012-07-15 16:21:18,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.123774
2012-07-15 16:21:18,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.168243
2012-07-15 16:21:19,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.247651
2012-07-15 16:21:19,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.301649
2012-07-15 16:21:20,286 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.358823
2012-07-15 16:21:20,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.409645
2012-07-15 16:21:21,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.466819
2012-07-15 16:21:21,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.533522
2012-07-15 16:21:22,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.603402
2012-07-15 16:21:22,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.660576
2012-07-15 16:21:23,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.682811
2012-07-15 16:21:23,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.778101
2012-07-15 16:21:24,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.854333
2012-07-15 16:21:24,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.908331
2012-07-15 16:21:25,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.990916
2012-07-15 16:21:25,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.044914
2012-07-15 16:21:26,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.105265
2012-07-15 16:21:26,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.181497
2012-07-15 16:21:27,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.257729
2012-07-15 16:21:27,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.324433
2012-07-15 16:21:28,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.400665
2012-07-15 16:21:28,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.422899
2012-07-15 16:21:29,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.543600
2012-07-15 16:21:29,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.613480
2012-07-15 16:21:30,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.689712
2012-07-15 16:21:30,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.743710
2012-07-15 16:21:31,576 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.877117
2012-07-15 16:21:32,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.969231
2012-07-15 16:21:32,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.054992
2012-07-15 16:21:33,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.128048
2012-07-15 16:21:33,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.223338
2012-07-15 16:21:34,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.305923
2012-07-15 16:21:34,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.404390
2012-07-15 16:21:35,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.477446
2012-07-15 16:21:35,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.610853
2012-07-15 16:21:36,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.734730
2012-07-15 16:21:36,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.871313
2012-07-15 16:21:37,090 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.985661
2012-07-15 16:21:37,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.150831
2012-07-15 16:21:38,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.303296
2012-07-15 16:21:38,594 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.465290
2012-07-15 16:21:39,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.468466
2012-07-15 16:21:39,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.779748
2012-07-15 16:21:40,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.922683
2012-07-15 16:21:40,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.075148
2012-07-15 16:21:41,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.221260
2012-07-15 16:21:42,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.430899
2012-07-15 16:21:42,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.545247
2012-07-15 16:21:43,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.681830
2012-07-15 16:21:43,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.767591
2012-07-15 16:21:44,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.869234
2012-07-15 16:21:44,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.008994
2012-07-15 16:21:45,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.101108
2012-07-15 16:21:45,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.180516
2012-07-15 16:21:46,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.294865
2012-07-15 16:21:46,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.355215
2012-07-15 16:21:47,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.447329
2012-07-15 16:21:47,535 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.574383
2012-07-15 16:21:48,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.669673
2012-07-15 16:21:48,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.771317
2012-07-15 16:21:49,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.847549
2012-07-15 16:21:49,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.939663
2012-07-15 16:21:50,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.041306
2012-07-15 16:21:50,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.111186
2012-07-15 16:21:51,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.222358
2012-07-15 16:21:51,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.301766
2012-07-15 16:21:52,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.384351
2012-07-15 16:21:52,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.476465
2012-07-15 16:21:53,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.552698
2012-07-15 16:21:53,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.651164
2012-07-15 16:21:54,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.740102
2012-07-15 16:21:54,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.835392
2012-07-15 16:21:55,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.917977
2012-07-15 16:21:55,625 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.023637
2012-07-15 16:21:55,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.023637
2012-07-15 16:21:55,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.023637
2012-07-15 16:21:56,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.107874
2012-07-15 16:21:56,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.203165
2012-07-15 16:21:57,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.288926
2012-07-15 16:21:57,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.361982
2012-07-15 16:21:58,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.466801
2012-07-15 16:21:58,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.555739
2012-07-15 16:21:59,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.635148
2012-07-15 16:21:59,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.717733
2012-07-15 16:22:00,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.781260
2012-07-15 16:22:00,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.844787
2012-07-15 16:22:01,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.975017
2012-07-15 16:22:01,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.051249
2012-07-15 16:22:02,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.152892
2012-07-15 16:22:02,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.251359
2012-07-15 16:22:03,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.372060
2012-07-15 16:22:03,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.499114
2012-07-15 16:22:04,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.635697
2012-07-15 16:22:04,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.788161
2012-07-15 16:22:05,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.940626
2012-07-15 16:22:05,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.102619
2012-07-15 16:22:06,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.102619
2012-07-15 16:22:06,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.398020
2012-07-15 16:22:07,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.531426
2012-07-15 16:22:07,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.661656
2012-07-15 16:22:08,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.699772
2012-07-15 16:22:08,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.699772
2012-07-15 16:22:09,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.982467
2012-07-15 16:22:09,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.125403
2012-07-15 16:22:10,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.233399
2012-07-15 16:22:10,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.338218
2012-07-15 16:22:11,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.452566
2012-07-15 16:22:12,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.560562
2012-07-15 16:22:12,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.662205
2012-07-15 16:22:13,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.767025
2012-07-15 16:22:13,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.862315
2012-07-15 16:22:14,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.979840
2012-07-15 16:22:14,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.084659
2012-07-15 16:22:15,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.183126
2012-07-15 16:22:15,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.278416
2012-07-15 16:22:16,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.383236
2012-07-15 16:22:16,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.500761
2012-07-15 16:22:17,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.634167
2012-07-15 16:22:17,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.745339
2012-07-15 16:22:18,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.875569
2012-07-15 16:22:18,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.989918
2012-07-15 16:22:19,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.113795
2012-07-15 16:22:19,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.234496
2012-07-15 16:22:20,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.310729
2012-07-15 16:22:20,522 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.345668
2012-07-15 16:22:21,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.437783
2012-07-15 16:22:21,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.536249
2012-07-15 16:22:22,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.672832
2012-07-15 16:22:22,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.822120
2012-07-15 16:22:23,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.841178
2012-07-15 16:22:23,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.031759
2012-07-15 16:22:24,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.088933
2012-07-15 16:22:24,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.222340
2012-07-15 16:22:25,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.301749
2012-07-15 16:22:25,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.384334
2012-07-15 16:22:26,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.482800
2012-07-15 16:22:26,535 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.578091
2012-07-15 16:22:27,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.657499
2012-07-15 16:22:27,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.740084
2012-07-15 16:22:28,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.797258
2012-07-15 16:22:28,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.873491
2012-07-15 16:22:29,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.895725
2012-07-15 16:22:29,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.013250
2012-07-15 16:22:30,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.086306
2012-07-15 16:22:30,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.156186
2012-07-15 16:22:31,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.235594
2012-07-15 16:22:31,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.308650
2012-07-15 16:22:32,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.384882
2012-07-15 16:22:32,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.467467
2012-07-15 16:22:33,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.581816
2012-07-15 16:22:33,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.689812
2012-07-15 16:22:34,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.800984
2012-07-15 16:22:34,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.918509
2012-07-15 16:22:35,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.020152
2012-07-15 16:22:35,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.159911
2012-07-15 16:22:36,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.267907
2012-07-15 16:22:36,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.394960
2012-07-15 16:22:37,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.518838
2012-07-15 16:22:37,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.563307
2012-07-15 16:22:38,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.706242
2012-07-15 16:22:38,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.801533
2012-07-15 16:22:39,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.884118
2012-07-15 16:22:39,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.960350
2012-07-15 16:22:40,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.042935
2012-07-15 16:22:40,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.122344
2012-07-15 16:22:41,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.208105
2012-07-15 16:22:41,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.284337
2012-07-15 16:22:42,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.366922
2012-07-15 16:22:42,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.411391
2012-07-15 16:22:43,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.522563
2012-07-15 16:22:43,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.617854
2012-07-15 16:22:44,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.703615
2012-07-15 16:22:44,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.786200
2012-07-15 16:22:45,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.865608
2012-07-15 16:22:45,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.957723
2012-07-15 16:22:46,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.059366
2012-07-15 16:22:46,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.154656
2012-07-15 16:22:47,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.221359
2012-07-15 16:22:47,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.323002
2012-07-15 16:22:48,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.418293
2012-07-15 16:22:48,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.519936
2012-07-15 16:22:49,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.618402
2012-07-15 16:22:49,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.704164
2012-07-15 16:22:50,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.828041
2012-07-15 16:22:50,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.894745
2012-07-15 16:22:51,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.948742
2012-07-15 16:22:51,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.075796
2012-07-15 16:22:52,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.161558
2012-07-15 16:22:52,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.186968
2012-07-15 16:22:53,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.288611
2012-07-15 16:22:53,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.352138
2012-07-15 16:22:54,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.450605
2012-07-15 16:22:54,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.523661
2012-07-15 16:22:55,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.593541
2012-07-15 16:22:55,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.672949
2012-07-15 16:22:56,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.761887
2012-07-15 16:22:56,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.841296
2012-07-15 16:22:57,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.920704
2012-07-15 16:22:57,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.961997
2012-07-15 16:22:58,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.069992
2012-07-15 16:22:58,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.143048
2012-07-15 16:22:59,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.171635
2012-07-15 16:22:59,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.276455
2012-07-15 16:23:00,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.365393
2012-07-15 16:23:00,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.428920
2012-07-15 16:23:01,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.467036
2012-07-15 16:23:01,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.527386
2012-07-15 16:23:02,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.600442
2012-07-15 16:23:02,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.670322
2012-07-15 16:23:03,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.733849
2012-07-15 16:23:03,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.816434
2012-07-15 16:23:04,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.905371
2012-07-15 16:23:04,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.972075
2012-07-15 16:23:04,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 100.000000
2012-07-15 16:23:06,025 DEBUG: install progress dpkg-exec 0.000000
2012-07-15 16:23:07,259 DEBUG: install progress patch 0.000000
2012-07-15 16:23:07,261 DEBUG: install progress patch 4.000000
2012-07-15 16:23:07,685 DEBUG: install progress patch 8.000000
2012-07-15 16:23:07,756 DEBUG: install progress patch 12.000000
2012-07-15 16:23:08,077 DEBUG: install progress dkms 12.000000
2012-07-15 16:23:08,080 DEBUG: install progress dkms 16.000000
2012-07-15 16:23:08,636 DEBUG: install progress dkms 20.000000
2012-07-15 16:23:08,708 DEBUG: install progress dkms 24.000000
2012-07-15 16:23:09,017 DEBUG: install progress fakeroot 24.000000
2012-07-15 16:23:09,019 DEBUG: install progress fakeroot 28.000000
2012-07-15 16:23:09,362 DEBUG: install progress fakeroot 32.000000
2012-07-15 16:23:09,425 DEBUG: install progress fakeroot 36.000000
2012-07-15 16:23:10,464 DEBUG: install progress fglrx-updates 36.000000
2012-07-15 16:23:10,467 DEBUG: install progress fglrx-updates 40.000000
2012-07-15 16:23:13,871 DEBUG: install progress fglrx-updates 44.000000
2012-07-15 16:23:13,951 DEBUG: install progress fglrx-updates 48.000000
2012-07-15 16:23:14,186 DEBUG: install progress fglrx-amdcccle-updates 48.000000
2012-07-15 16:23:14,189 DEBUG: install progress fglrx-amdcccle-updates 52.000000
2012-07-15 16:23:15,377 DEBUG: install progress fglrx-amdcccle-updates 56.000000
2012-07-15 16:23:15,459 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-07-15 16:23:15,548 DEBUG: install progress man-db 60.000000
2012-07-15 16:23:18,007 DEBUG: install progress ureadahead 60.000000
2012-07-15 16:23:18,359 DEBUG: install progress dpkg-exec 60.000000
2012-07-15 16:23:18,399 DEBUG: install progress patch 60.000000
2012-07-15 16:23:18,485 DEBUG: install progress patch 64.000000
2012-07-15 16:23:18,553 DEBUG: install progress patch 68.000000
2012-07-15 16:23:18,621 DEBUG: install progress dkms 68.000000
2012-07-15 16:23:19,659 DEBUG: install progress dkms 72.000000
2012-07-15 16:23:19,741 DEBUG: install progress dkms 76.000000
2012-07-15 16:23:19,803 DEBUG: install progress fakeroot 76.000000
2012-07-15 16:23:19,888 DEBUG: install progress fakeroot 80.000000
2012-07-15 16:23:20,299 DEBUG: install progress fakeroot 84.000000
2012-07-15 16:23:20,375 DEBUG: install progress fglrx-updates 84.000000
2012-07-15 16:23:20,636 DEBUG: install progress fglrx-updates 88.000000
2012-07-15 16:23:50,001 DEBUG: install progress fglrx-updates 92.000000
2012-07-15 16:23:50,395 DEBUG: install progress bamfdaemon 92.000000
2012-07-15 16:23:50,773 DEBUG: install progress fglrx-amdcccle-updates 92.000000
2012-07-15 16:23:50,848 DEBUG: install progress fglrx-amdcccle-updates 96.000000
2012-07-15 16:23:50,932 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-07-15 16:23:51,041 DEBUG: install progress initramfs-tools 100.000000
2012-07-15 16:24:08,251 DEBUG: install progress libc-bin 100.000000
2012-07-15 16:24:09,355 DEBUG: Selecting previously unselected package patch.
(Reading database ... 168536 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-3_i386.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-3) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic-pae
Building for architecture i686
Building initial module for 3.2.0-26-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic-pae/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-07-15 16:24:09,563 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-07-15 16:24:31,025 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-15 16:24:31,026 DEBUG: fglrx_updates is not the alternative in use
2012-07-15 16:24:31,055 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-15 16:24:31,056 DEBUG: fglrx_updates is not the alternative in use
```

---

### Post by QIII on 2012-07-15
The "additional drivers" method of installation fails for some users.  fglrx-updates and fglrx-amdcccle-updates do not work for some users.

See the link in my signature and check out the section titled something like "Alternate command line method, including hardware acceleration."

Do you have hybrid graphics?  I have some notes in the wiki about that.

---

### Post by pgfan92 on 2012-08-03
Thank you for your help, solved.

---

### Post by gromacs on 2012-08-16
> **QIII said:**
> The "additional drivers" method of installation fails for some users.  fglrx-updates and fglrx-amdcccle-updates do not work for some users.

See the link in my signature and check out the section titled something like "Alternate command line method, including hardware acceleration."

Do you have hybrid graphics?  I have some notes in the wiki about that.
Thank you for this information, the Alternate Command Line Method worked perfectly for me. I was also able to enable hardware acceleration with this. Is there a rep system on these forums or some way to thank you?

The only difficulty I had was when Terminal asked "Do you want to continue [Y/n]?" and I kept entering Y wondering why it kept aborting. I almost had to post a thread about it, and then found out it only works if you type in "YES" in all caps lol.

---

