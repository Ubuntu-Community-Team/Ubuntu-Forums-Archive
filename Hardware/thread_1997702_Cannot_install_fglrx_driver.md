---
title: "Cannot install fglrx driver"
date: 2012-06-05
forum: Hardware
---

### Post by 0011235813 on 2012-06-05
Hi,
I am trying to install fglrx driver on my newly upgraded 12.04. However, when I try to activate the driver from additional drivers, I get an error message stating that "Sorry, driver installation failed, please check /var/log/jockey.log".
Here is my jockey.log file:
```

2012-06-05 17:29:50,636 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050>
2012-06-05 17:29:55,822 DEBUG: reading modalias file /lib/modules/3.2.0-24-generic/modules.alias
2012-06-05 17:29:56,083 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-05 17:29:56,094 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-05 17:29:56,231 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-05 17:29:56,273 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-05 17:29:56,302 DEBUG: Software modem not available
2012-06-05 17:29:56,303 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-05 17:29:56,400 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-05 17:29:56,402 DEBUG: Firmware for DVB cards not available
2012-06-05 17:29:56,403 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-05 17:29:56,419 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-05 17:29:56,483 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-05 17:29:56,484 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-05 17:29:56,484 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-05 17:29:56,497 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-05 17:29:56,513 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-05 17:29:56,771 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-05 17:29:56,772 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-05 17:29:56,785 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-05 17:29:56,786 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-05 17:29:56,842 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-05 17:29:56,843 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-05 17:29:56,924 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-05 17:29:56,926 DEBUG: fglrx.available: falling back to default
2012-06-05 17:29:57,034 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-05 17:29:57,046 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-05 17:29:57,061 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-05 17:29:57,062 DEBUG: fglrx.available: falling back to default
2012-06-05 17:29:57,164 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-05 17:29:57,165 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-05 17:29:57,180 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-05 17:29:57,182 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-05 17:29:57,183 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-05 17:29:57,183 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-05 17:29:57,213 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-05 17:29:57,234 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-05 17:29:57,239 DEBUG: nvidia.available: falling back to default
2012-06-05 17:29:57,291 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-05 17:29:57,292 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-05 17:29:57,304 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-05 17:29:57,319 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-05 17:29:57,322 DEBUG: nvidia.available: falling back to default
2012-06-05 17:29:57,433 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-05 17:29:57,446 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-05 17:29:57,456 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-05 17:29:57,457 DEBUG: nvidia.available: falling back to default
2012-06-05 17:29:57,571 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-05 17:29:57,582 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-05 17:29:57,598 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-05 17:29:57,601 DEBUG: nvidia.available: falling back to default
2012-06-05 17:29:57,652 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-05 17:29:57,652 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-05 17:29:57,660 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-05 17:29:57,676 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-05 17:29:57,680 DEBUG: nvidia.available: falling back to default
2012-06-05 17:29:57,715 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-05 17:29:57,715 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-05 17:29:57,724 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-05 17:29:57,739 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-05 17:29:57,742 DEBUG: nvidia.available: falling back to default
2012-06-05 17:29:57,798 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-05 17:29:57,799 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-05 17:29:57,799 DEBUG: all custom handlers loaded
2012-06-05 17:29:57,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-05 17:29:57,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-05 17:29:57,821 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:58,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-05 17:29:58,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-05 17:29:58,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001002d00001314sv0000103Csd00003387bc04sc03i00')
2012-06-05 17:29:58,663 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-05 17:29:58,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'platform:pcspkr')
2012-06-05 17:29:58,665 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-05 17:29:58,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,665 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-05 17:29:58,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-05 17:29:58,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-05 17:29:58,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-05 17:29:58,695 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:58,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,695 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:29:58,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-05 17:29:58,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-05 17:29:58,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-05 17:29:58,697 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:58,697 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'platform:regulatory')
2012-06-05 17:29:58,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-05 17:29:58,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2012-06-05 17:29:58,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00003387bc04sc03i00')
2012-06-05 17:29:58,732 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-05 17:29:58,733 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,733 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-05 17:29:58,733 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:58,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-05 17:29:58,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-05 17:29:58,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:58,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-05 17:29:58,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001002d00009806sv0000103Csd00003387bc03sc00i00')
2012-06-05 17:29:58,742 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-05 17:29:58,883 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:58,884 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:29:58,743 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-05 17:29:58,901 DEBUG: fglrx.available: falling back to default
2012-06-05 17:29:58,992 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:58,993 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:29:58,947 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-05 17:29:58,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-05 17:29:59,036 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:59,037 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:29:58,994 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-05 17:29:59,051 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-05 17:29:59,068 DEBUG: fglrx.available: falling back to default
2012-06-05 17:29:59,153 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:59,154 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:29:59,120 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-05 17:29:59,155 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-05 17:29:59,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,156 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-06-05 17:29:59,200 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:59,201 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:29:59,156 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-05 17:29:59,217 DEBUG: fglrx.available: falling back to default
2012-06-05 17:29:59,315 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:59,316 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:29:59,274 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-05 17:29:59,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00003387bc0Csc05i00')
2012-06-05 17:29:59,330 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-06-05 17:29:59,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,331 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-06-05 17:29:59,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-05 17:29:59,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00003387bc02sc00i00')
2012-06-05 17:29:59,349 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-05 17:29:59,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'usb:v413Cp3012d4301dc00dsc00dp00ic03isc01ip02')
2012-06-05 17:29:59,379 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-05 17:29:59,379 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,380 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-05 17:29:59,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0003v413Cp3012e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-05 17:29:59,380 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,381 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:29:59,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,381 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0003v05C8p032Be0108-e0,1,kD4,ramlsfw')
2012-06-05 17:29:59,381 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,382 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,382 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:29:59,382 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-05 17:29:59,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:29:59,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-05 17:29:59,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000103Csd00001785bc02sc80i00')
2012-06-05 17:29:59,403 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-06-05 17:29:59,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-05 17:29:59,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,404 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-05 17:29:59,404 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-05 17:29:59,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,405 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-05 17:29:59,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,405 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:29:59,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-05 17:29:59,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.01:bd08/04/2011:svnHewlett-Packard:pnHPPaviliondm1NotebookPC:pvr0697100000204600000320100:rvnHewlett-Packard:rn3387:rvr36.0A:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-06-05 17:29:59,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,436 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-06-05 17:29:59,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-05 17:29:59,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-06-05 17:29:59,437 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,438 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,438 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-05 17:29:59,438 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'usb:v0CF3p311Dd0002dcE0dsc01dp01icE0isc01ip01')
2012-06-05 17:29:59,450 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath3k'}
2012-06-05 17:29:59,451 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath3k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,451 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-06-05 17:29:59,451 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-05 17:29:59,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'usb:v05C8p032Bd0108dcEFdsc02dp01ic0Eisc01ip00')
2012-06-05 17:29:59,453 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-06-05 17:29:59,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001002d00004394sv0000103Csd00003387bc01sc06i01')
2012-06-05 17:29:59,463 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,464 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-06-05 17:29:59,464 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,464 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,464 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:SYN1E50:PNP0F13:')
2012-06-05 17:29:59,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-05 17:29:59,465 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-06-05 17:29:59,465 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-05 17:29:59,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-05 17:29:59,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'usb:v413Cp2105d0351dc00dsc00dp00ic03isc01ip01')
2012-06-05 17:29:59,468 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-05 17:29:59,468 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,468 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-06-05 17:29:59,468 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-05 17:29:59,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:29:59,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-05 17:29:59,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'usb:v05C8p032Bd0108dcEFdsc02dp01ic0Eisc02ip00')
2012-06-05 17:29:59,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0003v413Cp2105e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-06-05 17:29:59,471 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,472 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:29:59,472 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,472 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'platform:lis3lv02d')
2012-06-05 17:29:59,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00003387bc0Csc03i20')
2012-06-05 17:29:59,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-05 17:29:59,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-05 17:29:59,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-06-05 17:29:59,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-06-05 17:29:59,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-05 17:29:59,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-05 17:29:59,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:29:59,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,508 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:29:59,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:29:59,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00003387bc06sc01i00')
2012-06-05 17:29:59,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bac050> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-05 17:29:59,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-05 17:29:59,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-05 17:29:59,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-05 17:29:59,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-05 17:29:59,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001002d00001314sv0000103Csd00003387bc04sc03i00')
2012-06-05 17:29:59,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'platform:pcspkr')
2012-06-05 17:29:59,518 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-05 17:29:59,518 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-05 17:29:59,518 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-05 17:29:59,518 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-05 17:29:59,518 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-05 17:29:59,518 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-05 17:29:59,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'platform:regulatory')
2012-06-05 17:29:59,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-05 17:29:59,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2012-06-05 17:29:59,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00003387bc04sc03i00')
2012-06-05 17:29:59,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-05 17:29:59,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-05 17:29:59,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-05 17:29:59,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001002d00009806sv0000103Csd00003387bc03sc00i00')
2012-06-05 17:29:59,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00003387bc0Csc05i00')
2012-06-05 17:29:59,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-05 17:29:59,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00003387bc02sc00i00')
2012-06-05 17:29:59,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'usb:v413Cp3012d4301dc00dsc00dp00ic03isc01ip02')
2012-06-05 17:29:59,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0003v413Cp3012e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-05 17:29:59,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0003v05C8p032Be0108-e0,1,kD4,ramlsfw')
2012-06-05 17:29:59,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-05 17:29:59,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-05 17:29:59,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000103Csd00001785bc02sc80i00')
2012-06-05 17:29:59,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-05 17:29:59,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-05 17:29:59,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.01:bd08/04/2011:svnHewlett-Packard:pnHPPaviliondm1NotebookPC:pvr0697100000204600000320100:rvnHewlett-Packard:rn3387:rvr36.0A:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-06-05 17:29:59,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-05 17:29:59,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-06-05 17:29:59,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'usb:v0CF3p311Dd0002dcE0dsc01dp01icE0isc01ip01')
2012-06-05 17:29:59,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-05 17:29:59,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'usb:v05C8p032Bd0108dcEFdsc02dp01ic0Eisc01ip00')
2012-06-05 17:29:59,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001002d00004394sv0000103Csd00003387bc01sc06i01')
2012-06-05 17:29:59,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-06-05 17:29:59,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:SYN1E50:PNP0F13:')
2012-06-05 17:29:59,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-05 17:29:59,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-05 17:29:59,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-05 17:29:59,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'usb:v413Cp2105d0351dc00dsc00dp00ic03isc01ip01')
2012-06-05 17:29:59,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-05 17:29:59,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-05 17:29:59,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'usb:v05C8p032Bd0108dcEFdsc02dp01ic0Eisc02ip00')
2012-06-05 17:29:59,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0003v413Cp2105e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-06-05 17:29:59,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'platform:lis3lv02d')
2012-06-05 17:29:59,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-06-05 17:29:59,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00003387bc0Csc03i20')
2012-06-05 17:29:59,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-05 17:29:59,526 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-05 17:29:59,526 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-05 17:29:59,526 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-05 17:29:59,526 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00003387bc06sc01i00')
2012-06-05 17:29:59,526 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2f2db48> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-05 17:29:59,690 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:59,691 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:29:59,746 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:59,747 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:29:59,800 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:29:59,801 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:30:00,202 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:30:00,203 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:30:00,557 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:30:00,558 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:30:00,660 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:30:00,661 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:30:00,800 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:30:00,801 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:30:00,901 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:30:00,902 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:30:00,966 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:30:00,967 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:30:01,361 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:30:01,362 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:30:05,213 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:30:05,214 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:30:15,523 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-06-05 17:31:22,421 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:22,422 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:31:22,462 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:22,463 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:31:29,199 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:29,199 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:31:29,242 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:29,242 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:31:29,314 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:29,315 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:31:29,718 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:29,719 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:31:29,753 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:29,754 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:31:29,857 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:29,858 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:31:29,893 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:29,894 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:31:29,958 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:31:29,958 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:31:32,627 DEBUG: Shutting down
2012-06-05 17:35:33,693 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050>
2012-06-05 17:35:38,928 DEBUG: reading modalias file /lib/modules/3.2.0-24-generic/modules.alias
2012-06-05 17:35:39,168 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-05 17:35:39,168 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-05 17:35:39,296 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-05 17:35:39,358 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-05 17:35:39,387 DEBUG: Software modem not available
2012-06-05 17:35:39,388 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-05 17:35:39,466 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-05 17:35:39,467 DEBUG: Firmware for DVB cards not available
2012-06-05 17:35:39,468 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-05 17:35:39,479 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-05 17:35:39,523 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-05 17:35:39,524 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-05 17:35:39,525 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-05 17:35:39,544 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-05 17:35:39,560 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-05 17:35:39,804 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-05 17:35:39,805 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-05 17:35:39,814 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-05 17:35:39,815 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-05 17:35:39,852 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-05 17:35:39,853 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-05 17:35:39,879 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-05 17:35:39,880 DEBUG: fglrx.available: falling back to default
2012-06-05 17:35:39,963 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-05 17:35:39,976 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-05 17:35:39,992 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-05 17:35:39,993 DEBUG: fglrx.available: falling back to default
2012-06-05 17:35:40,104 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-05 17:35:40,105 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-05 17:35:40,120 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-05 17:35:40,122 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-05 17:35:40,123 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-05 17:35:40,123 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-05 17:35:40,143 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-05 17:35:40,158 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-05 17:35:40,163 DEBUG: nvidia.available: falling back to default
2012-06-05 17:35:40,219 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-05 17:35:40,220 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-05 17:35:40,232 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-05 17:35:40,248 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-05 17:35:40,251 DEBUG: nvidia.available: falling back to default
2012-06-05 17:35:40,362 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-05 17:35:40,375 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-05 17:35:40,390 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-05 17:35:40,394 DEBUG: nvidia.available: falling back to default
2012-06-05 17:35:40,516 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-05 17:35:40,527 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-05 17:35:40,543 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-05 17:35:40,546 DEBUG: nvidia.available: falling back to default
2012-06-05 17:35:40,602 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-05 17:35:40,603 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-05 17:35:40,614 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-05 17:35:40,630 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-05 17:35:40,633 DEBUG: nvidia.available: falling back to default
2012-06-05 17:35:40,689 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-05 17:35:40,690 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-05 17:35:40,702 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-05 17:35:40,718 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-05 17:35:40,721 DEBUG: nvidia.available: falling back to default
2012-06-05 17:35:40,777 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-05 17:35:40,778 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-05 17:35:40,778 DEBUG: all custom handlers loaded
2012-06-05 17:35:40,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-05 17:35:40,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-05 17:35:40,797 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:41,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-05 17:35:41,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-05 17:35:41,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001002d00001314sv0000103Csd00003387bc04sc03i00')
2012-06-05 17:35:41,626 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-05 17:35:41,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'platform:pcspkr')
2012-06-05 17:35:41,628 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-05 17:35:41,629 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,629 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-05 17:35:41,629 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-05 17:35:41,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-05 17:35:41,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-05 17:35:41,658 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:41,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,658 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:35:41,659 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-05 17:35:41,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-05 17:35:41,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-05 17:35:41,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:41,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'platform:regulatory')
2012-06-05 17:35:41,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-05 17:35:41,662 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2012-06-05 17:35:41,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00003387bc04sc03i00')
2012-06-05 17:35:41,695 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-05 17:35:41,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,696 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-05 17:35:41,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:41,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-05 17:35:41,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-05 17:35:41,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:41,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-05 17:35:41,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001002d00009806sv0000103Csd00003387bc03sc00i00')
2012-06-05 17:35:41,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-05 17:35:41,746 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:35:41,747 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:35:41,706 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-05 17:35:41,763 DEBUG: fglrx.available: falling back to default
2012-06-05 17:35:41,864 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:35:41,864 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:35:41,818 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-05 17:35:41,865 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-05 17:35:41,911 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:35:41,912 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:35:41,866 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-05 17:35:41,924 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-05 17:35:41,940 DEBUG: fglrx.available: falling back to default
2012-06-05 17:35:42,043 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:35:42,044 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-05 17:35:41,997 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-05 17:35:42,045 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-05 17:35:42,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-06-05 17:35:42,091 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:35:42,092 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:35:42,046 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-05 17:35:42,108 DEBUG: fglrx.available: falling back to default
2012-06-05 17:35:42,212 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-05 17:35:42,212 DEBUG: fglrx_updates is not the alternative in use
2012-06-05 17:35:42,165 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-05 17:35:42,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00003387bc0Csc05i00')
2012-06-05 17:35:42,232 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-06-05 17:35:42,233 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,233 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-06-05 17:35:42,233 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-05 17:35:42,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,234 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00003387bc02sc00i00')
2012-06-05 17:35:42,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-05 17:35:42,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'usb:v413Cp3012d4301dc00dsc00dp00ic03isc01ip02')
2012-06-05 17:35:42,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-05 17:35:42,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-05 17:35:42,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0003v413Cp3012e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-05 17:35:42,282 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:35:42,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0003v05C8p032Be0108-e0,1,kD4,ramlsfw')
2012-06-05 17:35:42,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:35:42,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-05 17:35:42,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:35:42,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-05 17:35:42,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000103Csd00001785bc02sc80i00')
2012-06-05 17:35:42,304 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-06-05 17:35:42,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-05 17:35:42,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-05 17:35:42,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-05 17:35:42,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-05 17:35:42,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:35:42,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-05 17:35:42,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.01:bd08/04/2011:svnHewlett-Packard:pnHPPaviliondm1NotebookPC:pvr0697100000204600000320100:rvnHewlett-Packard:rn3387:rvr36.0A:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-06-05 17:35:42,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,338 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-06-05 17:35:42,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-05 17:35:42,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-06-05 17:35:42,339 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,340 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-05 17:35:42,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'usb:v0CF3p311Dd0002dcE0dsc01dp01icE0isc01ip01')
2012-06-05 17:35:42,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath3k'}
2012-06-05 17:35:42,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath3k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,353 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-06-05 17:35:42,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-05 17:35:42,354 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'usb:v05C8p032Bd0108dcEFdsc02dp01ic0Eisc01ip00')
2012-06-05 17:35:42,355 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-06-05 17:35:42,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001002d00004394sv0000103Csd00003387bc01sc06i01')
2012-06-05 17:35:42,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-06-05 17:35:42,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:SYN1E50:PNP0F13:')
2012-06-05 17:35:42,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-05 17:35:42,366 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-06-05 17:35:42,367 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,367 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-05 17:35:42,367 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-05 17:35:42,368 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'usb:v413Cp2105d0351dc00dsc00dp00ic03isc01ip01')
2012-06-05 17:35:42,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-05 17:35:42,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-06-05 17:35:42,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,370 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-05 17:35:42,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,371 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:35:42,371 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-05 17:35:42,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'usb:v05C8p032Bd0108dcEFdsc02dp01ic0Eisc02ip00')
2012-06-05 17:35:42,372 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0003v413Cp2105e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-06-05 17:35:42,372 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,373 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,373 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:35:42,373 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,373 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'platform:lis3lv02d')
2012-06-05 17:35:42,374 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00003387bc0Csc03i20')
2012-06-05 17:35:42,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-05 17:35:42,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-05 17:35:42,406 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-06-05 17:35:42,406 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,407 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-06-05 17:35:42,407 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-05 17:35:42,407 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,407 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-05 17:35:42,408 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-05 17:35:42,408 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,408 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-05 17:35:42,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-05 17:35:42,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00003387bc06sc01i00')
2012-06-05 17:35:42,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xeee050> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-05 17:35:42,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-05 17:35:42,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-05 17:35:42,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-05 17:35:42,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-05 17:35:42,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001002d00001314sv0000103Csd00003387bc04sc03i00')
2012-06-05 17:35:42,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'platform:pcspkr')
2012-06-05 17:35:42,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-05 17:35:42,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-05 17:35:42,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-05 17:35:42,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-05 17:35:42,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-05 17:35:42,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-05 17:35:42,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'platform:regulatory')
2012-06-05 17:35:42,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-05 17:35:42,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2012-06-05 17:35:42,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00003387bc04sc03i00')
2012-06-05 17:35:42,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-05 17:35:42,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-05 17:35:42,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-05 17:35:42,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001002d00009806sv0000103Csd00003387bc03sc00i00')
2012-06-05 17:35:42,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00003387bc0Csc05i00')
2012-06-05 17:35:42,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-05 17:35:42,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00003387bc02sc00i00')
2012-06-05 17:35:42,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'usb:v413Cp3012d4301dc00dsc00dp00ic03isc01ip02')
2012-06-05 17:35:42,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0003v413Cp3012e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-05 17:35:42,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0003v05C8p032Be0108-e0,1,kD4,ramlsfw')
2012-06-05 17:35:42,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-05 17:35:42,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-05 17:35:42,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000103Csd00001785bc02sc80i00')
2012-06-05 17:35:42,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-05 17:35:42,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-05 17:35:42,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.01:bd08/04/2011:svnHewlett-Packard:pnHPPaviliondm1NotebookPC:pvr0697100000204600000320100:rvnHewlett-Packard:rn3387:rvr36.0A:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-06-05 17:35:42,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-05 17:35:42,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-06-05 17:35:42,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'usb:v0CF3p311Dd0002dcE0dsc01dp01icE0isc01ip01')
2012-06-05 17:35:42,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-05 17:35:42,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'usb:v05C8p032Bd0108dcEFdsc02dp01ic0Eisc01ip00')
2012-06-05 17:35:42,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001002d00004394sv0000103Csd00003387bc01sc06i01')
2012-06-05 17:35:42,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-06-05 17:35:42,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:SYN1E50:PNP0F13:')
2012-06-05 17:35:42,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-05 17:35:42,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-05 17:35:42,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-05 17:35:42,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'usb:v413Cp2105d0351dc00dsc00dp00ic03isc01ip01')
2012-06-05 17:35:42,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-05 17:35:42,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-05 17:35:42,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'usb:v05C8p032Bd0108dcEFdsc02dp01ic0Eisc02ip00')
2012-06-05 17:35:42,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0003v413Cp2105e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-06-05 17:35:42,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'platform:lis3lv02d')
2012-06-05 17:35:42,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-06-05 17:35:42,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00003387bc0Csc03i20')
2012-06-05 17:35:42,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-05 17:35:42,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-05 17:35:42,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-05 17:35:42,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-05 17:35:42,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00003387bc06sc01i00')
2012-06-05 17:35:42,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x126eb90> about HardwareID('modalias', 'acpi:PNP0C02:')

```
Any help?

---

### Post by QIII on 2012-06-05
See the link in my signature.

---

### Post by 0011235813 on 2012-06-05
> **QIII said:**
> See the link in my signature.

Merci beaucoup.
But still, I wonder why the GUI method didn't work? Is this some sort of bug?

---

### Post by QIII on 2012-06-05
> **0011235813 said:**
> Merci beaucoup.
But still, I wonder why the GUI method didn't work? Is this some sort of bug?

An irritating one.

---

### Post by gudluck on 2012-06-06
My hp g6 1004tx gets too hot due to graphics card ati radeon... I want to disable it.. plz help..

---

### Post by ysNoi on 2012-06-07
> **gudluck said:**
> My hp g6 1004tx gets too hot due to graphics card ati radeon... I want to disable it.. plz help..

Hi gudluck...

Try the link below:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

HTH

---

