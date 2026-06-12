---
title: "&quot;Installation of drivers failed&quot;"
date: 2013-01-08
forum: Hardware
---

### Post by Kymus on 2013-01-08
I'm trying to update my NVIDIA drivers to v304 so that I can run steam. I did this previously without an issue and then earlier today I decided to try v310 that Steam was pestering me about. Yeah, that didn't go so well; now I'm booting to the terminal (separate issue). 

Anyway, after that, the NVIDIA drivers were disabled, so I tried v304 again and I got the error that the installation failed. Yippie! So then I tried the regular safe non-beta drivers and that went fine enough. I rebooted, logged back in, tried v304 again and........ yep, it failed, again. It mentioned to check the log, so here is the output:

> 2013-01-08 10:28:11,927 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c>
2013-01-08 10:28:13,228 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic-pae/modules.alias
2013-01-08 10:28:13,300 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 10:28:13,301 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 10:28:13,392 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 10:28:13,410 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 10:28:13,411 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 10:28:13,448 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 10:28:13,448 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 10:28:13,503 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 10:28:13,528 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 10:28:13,595 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:13,704 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 10:28:13,705 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 10:28:13,722 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 10:28:13,724 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:13,805 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 10:28:13,813 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 10:28:13,823 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 10:28:13,825 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:13,923 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 10:28:13,930 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 10:28:13,941 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 10:28:13,943 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:13,976 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 10:28:13,977 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 10:28:13,983 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 10:28:13,994 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 10:28:13,996 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:14,077 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 10:28:14,084 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 10:28:14,095 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 10:28:14,097 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:14,147 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 10:28:14,196 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 10:28:14,199 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:14,237 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 10:28:14,286 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 10:28:14,288 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:14,326 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 10:28:14,327 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 10:28:14,349 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 10:28:14,351 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 10:28:14,352 DEBUG: cdv.available: falling back to default
2013-01-08 10:28:14,423 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 10:28:14,423 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 10:28:14,464 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 10:28:14,517 DEBUG: Software modem not available
2013-01-08 10:28:14,517 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 10:28:14,529 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 10:28:14,539 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 10:28:14,539 DEBUG: fglrx.available: falling back to default
2013-01-08 10:28:14,620 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 10:28:14,627 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 10:28:14,637 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 10:28:14,638 DEBUG: fglrx.available: falling back to default
2013-01-08 10:28:14,716 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 10:28:14,716 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 10:28:14,725 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 10:28:14,766 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 10:28:14,767 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 10:28:14,767 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 10:28:14,779 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 10:28:14,790 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 10:28:14,857 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 10:28:14,858 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 10:28:14,908 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 10:28:14,909 DEBUG: Firmware for DVB cards not available
2013-01-08 10:28:14,910 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 10:28:14,919 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 10:28:14,920 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 10:28:14,920 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 10:28:14,920 DEBUG: all custom handlers loaded
2013-01-08 10:28:14,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 10:28:14,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 10:28:15,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 10:28:15,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:15,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:15,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 10:28:15,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 10:28:15,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 10:28:15,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 10:28:15,038 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:15,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 10:28:15,039 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 10:28:15,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 10:28:15,048 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:15,048 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,048 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 10:28:15,048 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 10:28:15,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 10:28:15,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 10:28:15,054 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 10:28:15,055 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 10:28:15,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 10:28:15,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 10:28:15,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 10:28:15,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 10:28:15,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 10:28:15,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 10:28:15,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 10:28:15,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 10:28:15,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:15,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 10:28:15,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 10:28:15,464 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 10:28:15,495 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:15,495 DEBUG: nvidia_current is not the alternative in use
2013-01-08 10:28:15,464 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 10:28:15,509 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:15,577 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:15,577 DEBUG: nvidia_current is not the alternative in use
2013-01-08 10:28:15,549 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 10:28:15,578 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 10:28:15,605 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:15,605 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 10:28:15,578 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 10:28:15,617 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:15,682 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:15,682 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 10:28:15,655 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 10:28:15,683 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 10:28:15,710 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:15,711 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 10:28:15,683 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 10:28:15,718 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 10:28:15,730 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:15,802 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:15,802 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 10:28:15,775 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 10:28:15,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 10:28:15,830 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:15,953 DEBUG: KMH enabled: True
2013-01-08 10:28:15,803 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 10:28:16,077 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:16,139 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:16,260 DEBUG: KMH enabled: True
2013-01-08 10:28:16,112 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 10:28:16,381 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 10:28:16,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:16,382 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 10:28:16,382 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:16,382 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 10:28:16,408 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:16,408 DEBUG: nvidia_current is not the alternative in use
2013-01-08 10:28:16,382 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 10:28:16,420 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:16,490 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:16,490 DEBUG: nvidia_current is not the alternative in use
2013-01-08 10:28:16,462 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 10:28:16,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310'}
2013-01-08 10:28:16,518 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:16,519 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 10:28:16,491 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 10:28:16,531 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:16,596 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:16,596 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 10:28:16,569 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 10:28:16,597 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304'}
2013-01-08 10:28:16,624 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:16,744 DEBUG: KMH enabled: True
2013-01-08 10:28:16,597 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 10:28:16,874 DEBUG: nvidia.available: falling back to default
2013-01-08 10:28:16,938 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:17,055 DEBUG: KMH enabled: True
2013-01-08 10:28:16,911 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 10:28:17,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 10:28:17,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 10:28:17,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 10:28:17,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 10:28:17,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 10:28:17,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 10:28:17,191 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 10:28:17,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 10:28:17,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 10:28:17,194 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 10:28:17,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 10:28:17,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 10:28:17,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 10:28:17,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 10:28:17,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:17,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 10:28:17,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 10:28:17,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:17,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 10:28:17,201 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 10:28:17,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 10:28:17,201 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:17,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,201 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 10:28:17,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 10:28:17,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 10:28:17,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 10:28:17,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 10:28:17,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 10:28:17,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 10:28:17,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 10:28:17,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 10:28:17,215 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 10:28:17,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,215 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 10:28:17,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 10:28:17,215 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:17,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,215 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 10:28:17,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 10:28:17,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 10:28:17,216 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 10:28:17,216 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,216 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 10:28:17,216 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 10:28:17,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 10:28:17,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 10:28:17,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 10:28:17,219 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 10:28:17,219 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,219 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 10:28:17,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 10:28:17,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 10:28:17,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 10:28:17,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 10:28:17,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 10:28:17,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 10:28:17,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 10:28:17,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 10:28:17,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 10:28:17,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 10:28:17,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 10:28:17,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 10:28:17,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 10:28:17,240 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 10:28:17,240 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 10:28:17,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 10:28:17,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 10:28:17,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:17,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 10:28:17,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 10:28:17,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 10:28:17,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94d8d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'platform:eisa')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 10:28:17,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 10:28:17,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 10:28:17,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x97729ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 10:28:17,307 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:17,307 DEBUG: nvidia_current is not the alternative in use
2013-01-08 10:28:18,171 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:18,171 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 10:28:18,921 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:19,025 DEBUG: KMH enabled: True
2013-01-08 10:28:19,983 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 10:28:19,983 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:12,763 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c>
2013-01-08 15:08:14,315 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic-pae/modules.alias
2013-01-08 15:08:14,410 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 15:08:14,425 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 15:08:14,543 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 15:08:14,579 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 15:08:14,580 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 15:08:14,628 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 15:08:14,628 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 15:08:14,687 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 15:08:14,720 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 15:08:14,751 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:14,931 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:08:14,931 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 15:08:14,991 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 15:08:14,993 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:15,069 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:08:15,076 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:08:15,086 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 15:08:15,089 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:15,176 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:08:15,183 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 15:08:15,193 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 15:08:15,196 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:15,233 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:08:15,233 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 15:08:15,240 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 15:08:15,250 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 15:08:15,253 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:15,335 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:08:15,342 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 15:08:15,352 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 15:08:15,355 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:15,436 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:08:15,524 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 15:08:15,527 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:15,564 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:08:15,640 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 15:08:15,642 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:15,679 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:08:15,680 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 15:08:15,689 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 15:08:15,691 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 15:08:15,692 DEBUG: cdv.available: falling back to default
2013-01-08 15:08:15,766 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 15:08:15,766 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 15:08:15,806 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 15:08:15,893 DEBUG: Software modem not available
2013-01-08 15:08:15,893 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 15:08:15,905 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 15:08:15,915 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 15:08:15,915 DEBUG: fglrx.available: falling back to default
2013-01-08 15:08:15,996 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:08:16,003 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 15:08:16,013 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 15:08:16,014 DEBUG: fglrx.available: falling back to default
2013-01-08 15:08:16,094 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 15:08:16,094 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 15:08:16,107 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 15:08:16,148 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 15:08:16,148 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 15:08:16,149 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 15:08:16,161 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 15:08:16,172 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 15:08:16,239 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 15:08:16,239 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 15:08:16,364 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 15:08:16,365 DEBUG: Firmware for DVB cards not available
2013-01-08 15:08:16,365 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 15:08:16,374 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 15:08:16,375 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 15:08:16,376 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 15:08:16,376 DEBUG: all custom handlers loaded
2013-01-08 15:08:16,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:08:16,395 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 15:08:16,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:08:16,539 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:16,539 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:16,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:08:16,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:08:16,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:08:16,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:08:16,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:16,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:08:16,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:08:16,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:08:16,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:16,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:08:16,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:08:16,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:08:16,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:08:16,567 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 15:08:16,567 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:08:16,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:08:16,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:08:16,796 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 15:08:16,796 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:08:16,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:08:16,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:08:16,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 15:08:16,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 15:08:16,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:16,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:08:16,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:08:17,017 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 15:08:17,130 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:17,131 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:17,017 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:08:17,144 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:17,214 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:17,215 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:17,186 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:08:17,215 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 15:08:17,243 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:17,243 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:17,215 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:08:17,256 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:17,323 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:17,323 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:17,295 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:08:17,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 15:08:17,351 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:17,352 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:08:17,324 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:08:17,359 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:08:17,372 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:17,445 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:17,445 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:08:17,417 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:08:17,446 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 15:08:17,473 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:17,649 DEBUG: KMH enabled: True
2013-01-08 15:08:17,446 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:08:17,781 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:17,846 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:17,974 DEBUG: KMH enabled: True
2013-01-08 15:08:17,818 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:08:18,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 15:08:18,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 15:08:18,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 15:08:18,119 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:18,120 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:18,094 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:08:18,132 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:18,199 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:18,200 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:18,173 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:08:18,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310'}
2013-01-08 15:08:18,228 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:18,228 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:18,201 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:08:18,241 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:18,307 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:18,307 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:18,279 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:08:18,308 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304'}
2013-01-08 15:08:18,337 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:18,458 DEBUG: KMH enabled: True
2013-01-08 15:08:18,308 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:08:18,592 DEBUG: nvidia.available: falling back to default
2013-01-08 15:08:18,658 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:18,782 DEBUG: KMH enabled: True
2013-01-08 15:08:18,630 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:08:18,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:08:18,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:08:18,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 15:08:18,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:08:18,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:08:18,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:08:18,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 15:08:18,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:08:18,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:08:18,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:08:18,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:08:18,926 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:08:18,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 15:08:18,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:08:18,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:18,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:08:18,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:08:18,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:18,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:08:18,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 15:08:18,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:08:18,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:18,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:08:18,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:08:18,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:08:18,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:08:18,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,931 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:08:18,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:08:18,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:08:18,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:08:18,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:08:18,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:08:18,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:08:18,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:08:18,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:18,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:08:18,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:08:18,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:08:18,945 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:08:18,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,945 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:08:18,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:08:18,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:08:18,948 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:08:18,948 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:08:18,948 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:08:18,948 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,948 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 15:08:18,948 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,948 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,949 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:08:18,949 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:08:18,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:08:18,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:08:18,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:08:18,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:08:18,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:08:18,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 15:08:18,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:08:18,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 15:08:18,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 15:08:18,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:08:18,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:08:18,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 15:08:18,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:08:18,972 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 15:08:18,972 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:08:18,973 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:18,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,973 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:08:18,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:08:18,973 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:08:18,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8e53d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:08:18,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:08:18,974 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:08:18,975 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:08:18,976 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:08:18,976 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:08:18,976 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:08:18,976 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:08:18,976 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:08:18,976 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:08:18,976 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:08:18,976 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90ed9ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:08:19,109 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:19,109 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:20,016 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:20,017 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:20,068 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:20,069 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:20,152 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:20,152 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:08:20,916 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:20,916 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:08:20,972 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:20,972 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:08:21,060 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:21,193 DEBUG: KMH enabled: True
2013-01-08 15:08:22,205 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:22,338 DEBUG: KMH enabled: True
2013-01-08 15:08:22,647 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:22,776 DEBUG: KMH enabled: True
2013-01-08 15:08:23,099 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:23,100 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:23,879 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:23,880 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:23,945 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:23,945 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:24,041 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,041 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:24,106 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,107 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:24,171 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,171 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:24,330 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,331 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:24,395 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,396 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:24,460 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,460 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:08:24,557 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,557 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:08:24,622 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,622 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:08:24,687 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,688 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:08:24,784 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:24,912 DEBUG: KMH enabled: True
2013-01-08 15:08:25,212 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:25,352 DEBUG: KMH enabled: True
2013-01-08 15:08:25,672 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:25,802 DEBUG: KMH enabled: True
2013-01-08 15:08:31,772 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:31,772 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:33,930 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:08:33,931 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:08:38,725 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n', '\tOption\t"NoLogo"\t"True"\n']})
2013-01-08 15:09:27,047 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:27,179 DEBUG: KMH enabled: True
2013-01-08 15:09:27,345 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:27,471 DEBUG: KMH enabled: True
2013-01-08 15:09:27,681 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:27,682 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:09:27,789 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:27,789 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:09:27,875 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:27,876 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:09:27,960 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:28,100 DEBUG: KMH enabled: True
2013-01-08 15:09:28,268 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:28,392 DEBUG: KMH enabled: True
2013-01-08 15:09:28,587 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:28,717 DEBUG: KMH enabled: True
2013-01-08 15:09:28,899 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:29,041 DEBUG: KMH enabled: True
2013-01-08 15:09:29,275 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:29,276 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:09:29,352 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:29,353 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:09:29,431 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:29,431 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:09:29,510 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:29,635 DEBUG: KMH enabled: True
2013-01-08 15:09:29,796 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:09:29,930 DEBUG: KMH enabled: True
2013-01-08 15:15:43,046 DEBUG: Shutting down
2013-01-08 15:15:44,890 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c>
2013-01-08 15:15:46,084 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic-pae/modules.alias
2013-01-08 15:15:46,162 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 15:15:46,162 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 15:15:46,236 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 15:15:46,245 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 15:15:46,245 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 15:15:46,283 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 15:15:46,283 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 15:15:46,299 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 15:15:46,310 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 15:15:46,319 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:46,432 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:15:46,432 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 15:15:46,450 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 15:15:46,452 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:46,533 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:15:46,540 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:15:46,550 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 15:15:46,553 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:46,638 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:15:46,645 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 15:15:46,653 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 15:15:46,656 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:46,693 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:15:46,693 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 15:15:46,700 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 15:15:46,711 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 15:15:46,713 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:46,794 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:15:46,802 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 15:15:46,812 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 15:15:46,815 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:46,897 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:15:46,944 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 15:15:46,947 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:46,979 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:15:47,028 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 15:15:47,030 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:47,057 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:15:47,058 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 15:15:47,067 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 15:15:47,068 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 15:15:47,068 DEBUG: cdv.available: falling back to default
2013-01-08 15:15:47,142 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 15:15:47,143 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 15:15:47,183 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 15:15:47,236 DEBUG: Software modem not available
2013-01-08 15:15:47,237 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 15:15:47,249 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 15:15:47,256 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 15:15:47,256 DEBUG: fglrx.available: falling back to default
2013-01-08 15:15:47,336 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:15:47,344 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 15:15:47,354 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 15:15:47,354 DEBUG: fglrx.available: falling back to default
2013-01-08 15:15:47,434 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 15:15:47,434 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 15:15:47,443 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 15:15:47,483 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 15:15:47,484 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 15:15:47,484 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 15:15:47,496 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 15:15:47,507 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 15:15:47,574 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 15:15:47,575 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 15:15:47,625 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 15:15:47,626 DEBUG: Firmware for DVB cards not available
2013-01-08 15:15:47,626 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 15:15:47,636 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 15:15:47,637 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 15:15:47,637 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 15:15:47,638 DEBUG: all custom handlers loaded
2013-01-08 15:15:47,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:15:47,657 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 15:15:47,769 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:47,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:15:47,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:47,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:47,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:47,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:15:47,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:15:47,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:15:47,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:15:47,783 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:47,783 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:47,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:15:47,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:15:47,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:15:47,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:47,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:47,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:47,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:47,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:15:47,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:15:47,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:15:47,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 15:15:47,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:47,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:15:47,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:15:47,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:15:48,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 15:15:48,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:48,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:15:48,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:15:48,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:15:48,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 15:15:48,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:48,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 15:15:48,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:48,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:15:48,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:15:48,250 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 15:15:48,274 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:48,275 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:15:48,250 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:15:48,287 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:48,357 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:48,358 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:15:48,329 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:15:48,358 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 15:15:48,386 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:48,514 DEBUG: KMH enabled: True
2013-01-08 15:15:48,358 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:48,638 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:48,703 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:48,829 DEBUG: KMH enabled: True
2013-01-08 15:15:48,675 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:48,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 15:15:48,984 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:48,985 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:15:48,959 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:15:48,992 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:15:49,005 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:49,078 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:49,078 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:15:49,050 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:15:49,079 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 15:15:49,106 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:49,107 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:15:49,079 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:49,120 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:49,186 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:49,186 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:15:49,158 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:49,187 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 15:15:49,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:49,187 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 15:15:49,188 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:49,188 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 15:15:49,215 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:49,216 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:15:49,188 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:15:49,228 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:49,299 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:49,299 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:15:49,270 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:15:49,300 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310'}
2013-01-08 15:15:49,328 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:49,453 DEBUG: KMH enabled: True
2013-01-08 15:15:49,300 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:49,606 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:49,664 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:49,790 DEBUG: KMH enabled: True
2013-01-08 15:15:49,636 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:49,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304'}
2013-01-08 15:15:49,946 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:49,946 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:15:49,920 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:49,958 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:50,024 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:50,024 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:15:49,996 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:50,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:15:50,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:15:50,037 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 15:15:50,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:15:50,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:15:50,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:15:50,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 15:15:50,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:15:50,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:15:50,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:50,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:15:50,052 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:15:50,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,053 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 15:15:50,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:15:50,053 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:50,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,053 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:50,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:15:50,053 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:50,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:15:50,054 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 15:15:50,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:15:50,054 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:50,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,054 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:50,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:15:50,057 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:15:50,057 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,057 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:15:50,057 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:15:50,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:15:50,069 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:50,069 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:15:50,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:15:50,070 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:50,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,070 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:15:50,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:15:50,070 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:50,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,070 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:50,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:15:50,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:15:50,071 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:50,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,071 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:15:50,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:15:50,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:15:50,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:15:50,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:15:50,074 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:50,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,075 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 15:15:50,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:15:50,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:15:50,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:15:50,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:15:50,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:15:50,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:15:50,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:15:50,096 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 15:15:50,096 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:15:50,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 15:15:50,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 15:15:50,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:15:50,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:15:50,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 15:15:50,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:15:50,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 15:15:50,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:15:50,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:50,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:50,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:15:50,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:50,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9273d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:15:50,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:15:50,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:15:50,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x950dfec> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:15:50,109 DEBUG: Shutting down
2013-01-08 15:15:52,137 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c>
2013-01-08 15:15:53,344 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic-pae/modules.alias
2013-01-08 15:15:53,411 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 15:15:53,411 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 15:15:53,474 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 15:15:53,482 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 15:15:53,482 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 15:15:53,519 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 15:15:53,520 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 15:15:53,535 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 15:15:53,546 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 15:15:53,550 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:53,652 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:15:53,653 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 15:15:53,670 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 15:15:53,672 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:53,753 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:15:53,760 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:15:53,770 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 15:15:53,773 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:53,860 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:15:53,867 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 15:15:53,877 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 15:15:53,879 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:53,917 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:15:53,917 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 15:15:53,924 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 15:15:53,934 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 15:15:53,937 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:54,017 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:15:54,024 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 15:15:54,035 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 15:15:54,037 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:54,118 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:15:54,172 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 15:15:54,175 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:54,212 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:15:54,266 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 15:15:54,269 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:54,306 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:15:54,306 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 15:15:54,316 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 15:15:54,318 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 15:15:54,318 DEBUG: cdv.available: falling back to default
2013-01-08 15:15:54,391 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 15:15:54,392 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 15:15:54,432 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 15:15:54,449 DEBUG: Software modem not available
2013-01-08 15:15:54,449 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 15:15:54,461 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 15:15:54,470 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 15:15:54,471 DEBUG: fglrx.available: falling back to default
2013-01-08 15:15:54,551 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:15:54,559 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 15:15:54,569 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 15:15:54,569 DEBUG: fglrx.available: falling back to default
2013-01-08 15:15:54,650 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 15:15:54,650 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 15:15:54,659 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 15:15:54,699 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 15:15:54,700 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 15:15:54,700 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 15:15:54,712 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 15:15:54,723 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 15:15:54,790 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 15:15:54,790 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 15:15:54,840 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 15:15:54,841 DEBUG: Firmware for DVB cards not available
2013-01-08 15:15:54,842 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 15:15:54,851 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 15:15:54,852 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 15:15:54,852 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 15:15:54,852 DEBUG: all custom handlers loaded
2013-01-08 15:15:54,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:15:54,863 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 15:15:54,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:54,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:15:54,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:54,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:54,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:54,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:15:54,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:15:54,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:15:54,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:15:54,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:54,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:54,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:15:54,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:15:54,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:15:54,981 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:54,981 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:54,981 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:54,981 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:54,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:15:54,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:15:54,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:15:54,988 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 15:15:54,988 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:54,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:15:54,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:15:54,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:15:55,215 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 15:15:55,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:55,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:15:55,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:15:55,234 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:15:55,237 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 15:15:55,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:55,237 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 15:15:55,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:55,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:15:55,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:15:55,434 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 15:15:55,458 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:55,459 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:15:55,434 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:15:55,472 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:55,542 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:55,543 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:15:55,515 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:15:55,543 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 15:15:55,571 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:55,694 DEBUG: KMH enabled: True
2013-01-08 15:15:55,544 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:55,823 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:55,889 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,014 DEBUG: KMH enabled: True
2013-01-08 15:15:55,861 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:56,137 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 15:15:56,166 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,166 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:15:56,138 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:15:56,174 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:15:56,187 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:56,260 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,260 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:15:56,231 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:15:56,261 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 15:15:56,288 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,289 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:15:56,261 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:56,301 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:56,368 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,368 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:15:56,339 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:56,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 15:15:56,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:56,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 15:15:56,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:56,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 15:15:56,398 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,398 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:15:56,370 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:15:56,411 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:56,481 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,481 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:15:56,453 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:15:56,482 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310'}
2013-01-08 15:15:56,510 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,650 DEBUG: KMH enabled: True
2013-01-08 15:15:56,482 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:56,783 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:56,849 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:56,972 DEBUG: KMH enabled: True
2013-01-08 15:15:56,822 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, enabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:57,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304'}
2013-01-08 15:15:57,121 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:57,122 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:15:57,095 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:57,134 DEBUG: nvidia.available: falling back to default
2013-01-08 15:15:57,198 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:57,198 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:15:57,170 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:15:57,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:15:57,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:15:57,211 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 15:15:57,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:15:57,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:15:57,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:15:57,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 15:15:57,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:15:57,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:15:57,216 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:57,216 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:15:57,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:15:57,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 15:15:57,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:15:57,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:57,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:57,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:15:57,223 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:57,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:15:57,223 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 15:15:57,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:15:57,223 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:57,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,223 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:57,224 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:15:57,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:15:57,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:15:57,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:15:57,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:15:57,238 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:57,238 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:15:57,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:15:57,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:57,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:15:57,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:15:57,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:57,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:57,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:15:57,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:15:57,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:57,240 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:15:57,240 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:15:57,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:15:57,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:15:57,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:15:57,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:15:57,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 15:15:57,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:15:57,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:15:57,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:15:57,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:15:57,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:15:57,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:15:57,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:15:57,265 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 15:15:57,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:15:57,266 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 15:15:57,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,266 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 15:15:57,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:15:57,266 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:15:57,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,266 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 15:15:57,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:15:57,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 15:15:57,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:15:57,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:57,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:15:57,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:15:57,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:15:57,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fbd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:15:57,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:15:57,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:15:57,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a95fec> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:15:57,332 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:15:57,458 DEBUG: KMH enabled: True
2013-01-08 15:16:24,939 DEBUG: Shutting down
2013-01-08 15:48:43,718 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c>
2013-01-08 15:48:45,034 DEBUG: reading modalias file /lib/modules/3.2.0-34-generic-pae/modules.alias
2013-01-08 15:48:45,121 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 15:48:45,128 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 15:48:45,196 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 15:48:45,226 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 15:48:45,227 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 15:48:45,281 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 15:48:45,281 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 15:48:45,339 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 15:48:45,349 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 15:48:45,352 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:45,507 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:48:45,507 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 15:48:45,552 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 15:48:45,554 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:45,631 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:48:45,637 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:48:45,647 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 15:48:45,649 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:45,732 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:48:45,738 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 15:48:45,748 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 15:48:45,750 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:45,785 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:48:45,786 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 15:48:45,792 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 15:48:45,801 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 15:48:45,803 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:45,880 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:48:45,887 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 15:48:45,896 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 15:48:45,898 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:45,975 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:48:45,981 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 15:48:46,026 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 15:48:46,028 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:46,063 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:48:46,070 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 15:48:46,114 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 15:48:46,116 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:46,152 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:48:46,152 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 15:48:46,161 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 15:48:46,163 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 15:48:46,164 DEBUG: cdv.available: falling back to default
2013-01-08 15:48:46,234 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 15:48:46,234 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 15:48:46,273 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 15:48:46,309 DEBUG: Software modem not available
2013-01-08 15:48:46,310 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 15:48:46,321 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 15:48:46,330 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 15:48:46,331 DEBUG: fglrx.available: falling back to default
2013-01-08 15:48:46,407 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:48:46,414 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 15:48:46,423 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 15:48:46,423 DEBUG: fglrx.available: falling back to default
2013-01-08 15:48:46,500 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 15:48:46,501 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 15:48:46,509 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 15:48:46,548 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 15:48:46,548 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 15:48:46,549 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 15:48:46,560 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 15:48:46,570 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 15:48:46,634 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 15:48:46,635 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 15:48:46,708 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 15:48:46,710 DEBUG: Firmware for DVB cards not available
2013-01-08 15:48:46,710 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 15:48:46,718 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 15:48:46,719 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 15:48:46,720 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 15:48:46,720 DEBUG: all custom handlers loaded
2013-01-08 15:48:46,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:48:46,739 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 15:48:46,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:46,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:48:46,872 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:46,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:46,872 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:46,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:48:46,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:48:46,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:48:46,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:48:46,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:46,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:46,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:48:46,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:48:46,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:48:46,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:46,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:46,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:48:46,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:46,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:48:46,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:48:46,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:48:46,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 15:48:46,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:46,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:48:46,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:48:46,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:48:47,100 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 15:48:47,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:48:47,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:48:47,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:48:47,120 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 15:48:47,120 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,120 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 15:48:47,120 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:48:47,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:48:47,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 15:48:47,371 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,371 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:48:47,296 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:48:47,384 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:47,448 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,448 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:48:47,424 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:48:47,449 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 15:48:47,473 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,474 DEBUG: KMH enabled: False
2013-01-08 15:48:47,449 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:48:47,480 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 15:48:47,492 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:47,553 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,553 DEBUG: KMH enabled: False
2013-01-08 15:48:47,528 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:48:47,554 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 15:48:47,578 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,578 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:48:47,554 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:48:47,585 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:48:47,597 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:47,663 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,664 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:48:47,639 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:48:47,664 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 15:48:47,689 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,689 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:48:47,665 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:48:47,696 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 15:48:47,707 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:47,768 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,768 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:48:47,743 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:48:47,769 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 15:48:47,769 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,769 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 15:48:47,770 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,770 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 15:48:47,794 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,794 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:48:47,770 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:48:47,806 DEBUG: nvidia.available: falling back to default
2013-01-08 15:48:47,869 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,870 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:48:47,845 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:48:47,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:48:47,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:48:47,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 15:48:47,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:48:47,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:48:47,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:48:47,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 15:48:47,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:48:47,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:48:47,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:48:47,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:48:47,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:48:47,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 15:48:47,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:48:47,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:47,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:48:47,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:48:47,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:47,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:48:47,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 15:48:47,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:48:47,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:47,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,895 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:48:47,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:48:47,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:48:47,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:48:47,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:48:47,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:48:47,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:48:47,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:48:47,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:48:47,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:48:47,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:48:47,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:48:47,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:47,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:48:47,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:48:47,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:48:47,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:48:47,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:48:47,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:48:47,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:48:47,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:48:47,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:48:47,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:48:47,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,913 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 15:48:47,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:48:47,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:48:47,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:48:47,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:48:47,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:48:47,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:48:47,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:48:47,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 15:48:47,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:48:47,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 15:48:47,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 15:48:47,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:48:47,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:48:47,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 15:48:47,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:48:47,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 15:48:47,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:48:47,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:47,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:48:47,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:48:47,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:48:47,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9404d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:48:47,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:48:47,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:48:47,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x969ee4c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:48:47,995 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:47,995 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:48:48,741 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:48,741 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:48:49,418 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:49,419 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:48:50,116 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:50,117 DEBUG: KMH enabled: False
2013-01-08 15:48:50,804 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:50,805 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:48:50,930 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:50,930 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:48:50,983 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:50,983 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:48:51,036 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:51,037 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:48:51,089 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:51,090 DEBUG: KMH enabled: False
2013-01-08 15:48:54,439 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:54,439 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:48:56,660 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-310/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf
2013-01-08 15:48:56,660 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:49:00,870 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 15:49:00,871 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-01-08 15:49:45,901 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:49:45,902 DEBUG: KMH enabled: False
2013-01-08 15:49:45,931 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:49:45,932 DEBUG: KMH enabled: False
2013-01-08 15:51:16,497 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,498 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:51:16,557 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,557 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:51:16,616 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,616 DEBUG: KMH enabled: False
2013-01-08 15:51:16,646 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,646 DEBUG: KMH enabled: False
2013-01-08 15:51:16,705 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,705 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:51:16,775 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,776 DEBUG: KMH enabled: False
2013-01-08 15:51:16,805 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,806 DEBUG: KMH enabled: False
2013-01-08 15:51:16,893 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,893 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:51:16,946 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:16,947 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:51:17,000 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:17,001 DEBUG: KMH enabled: False
2013-01-08 15:51:17,030 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:17,031 DEBUG: KMH enabled: False
2013-01-08 15:51:17,084 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:51:17,085 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:51:19,165 DEBUG: Shutting down
2013-01-08 15:54:56,166 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c>
2013-01-08 15:54:57,714 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic/modules.alias
2013-01-08 15:54:57,805 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 15:54:57,812 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 15:54:57,888 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 15:54:57,920 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 15:54:57,921 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 15:54:57,956 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 15:54:57,957 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 15:54:58,015 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 15:54:58,024 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 15:54:58,027 DEBUG: nvidia.available: falling back to default
2013-01-08 15:54:58,136 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:54:58,136 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 15:54:58,195 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 15:54:58,196 DEBUG: nvidia.available: falling back to default
2013-01-08 15:54:58,273 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:54:58,279 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:54:58,288 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 15:54:58,290 DEBUG: nvidia.available: falling back to default
2013-01-08 15:54:58,372 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:54:58,379 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 15:54:58,388 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 15:54:58,390 DEBUG: nvidia.available: falling back to default
2013-01-08 15:54:58,425 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 15:54:58,425 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 15:54:58,431 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 15:54:58,441 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 15:54:58,443 DEBUG: nvidia.available: falling back to default
2013-01-08 15:54:58,519 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:54:58,525 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 15:54:58,535 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 15:54:58,537 DEBUG: nvidia.available: falling back to default
2013-01-08 15:54:58,614 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 15:54:58,620 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 15:54:58,664 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 15:54:58,666 DEBUG: nvidia.available: falling back to default
2013-01-08 15:54:58,701 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:54:58,707 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 15:54:58,752 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 15:54:58,754 DEBUG: nvidia.available: falling back to default
2013-01-08 15:54:58,789 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 15:54:58,789 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 15:54:58,799 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 15:54:58,800 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 15:54:58,801 DEBUG: cdv.available: falling back to default
2013-01-08 15:54:58,870 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 15:54:58,870 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 15:54:58,909 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 15:54:58,943 DEBUG: Software modem not available
2013-01-08 15:54:58,943 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 15:54:58,954 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 15:54:58,963 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 15:54:58,964 DEBUG: fglrx.available: falling back to default
2013-01-08 15:54:59,040 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 15:54:59,046 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 15:54:59,055 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 15:54:59,056 DEBUG: fglrx.available: falling back to default
2013-01-08 15:54:59,132 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 15:54:59,133 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 15:54:59,141 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 15:54:59,179 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 15:54:59,180 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 15:54:59,180 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 15:54:59,192 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 15:54:59,201 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 15:54:59,264 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 15:54:59,265 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 15:54:59,341 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 15:54:59,342 DEBUG: Firmware for DVB cards not available
2013-01-08 15:54:59,342 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 15:54:59,351 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 15:54:59,352 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 15:54:59,352 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 15:54:59,352 DEBUG: all custom handlers loaded
2013-01-08 15:54:59,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:54:59,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 15:54:59,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:54:59,485 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:54:59,485 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:54:59,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:54:59,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:54:59,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:54:59,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:54:59,495 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:54:59,495 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:54:59,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:54:59,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:54:59,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:54:59,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:54:59,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:54:59,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:54:59,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:54:59,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 15:54:59,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:54:59,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:54:59,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:54:59,714 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 15:54:59,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:54:59,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:54:59,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:54:59,733 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 15:54:59,733 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,733 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 15:54:59,733 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:54:59,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:54:59,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:54:59,910 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 15:54:59,979 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:54:59,980 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:54:59,910 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:54:59,992 DEBUG: nvidia.available: falling back to default
2013-01-08 15:55:00,056 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,056 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:55:00,032 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:55:00,056 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 15:55:00,080 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,080 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:55:00,057 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:55:00,087 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 15:55:00,098 DEBUG: nvidia.available: falling back to default
2013-01-08 15:55:00,157 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,158 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:55:00,133 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:55:00,158 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 15:55:00,182 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,182 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:55:00,159 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:55:00,189 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 15:55:00,200 DEBUG: nvidia.available: falling back to default
2013-01-08 15:55:00,266 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,266 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:55:00,242 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 15:55:00,267 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 15:55:00,290 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,291 DEBUG: KMH enabled: False
2013-01-08 15:55:00,267 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:55:00,297 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 15:55:00,308 DEBUG: nvidia.available: falling back to default
2013-01-08 15:55:00,368 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,368 DEBUG: KMH enabled: False
2013-01-08 15:55:00,344 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 15:55:00,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 15:55:00,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 15:55:00,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 15:55:00,394 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,394 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:55:00,370 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:55:00,405 DEBUG: nvidia.available: falling back to default
2013-01-08 15:55:00,468 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,469 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:55:00,444 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 15:55:00,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:55:00,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:55:00,480 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 15:55:00,481 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:55:00,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:55:00,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:55:00,482 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 15:55:00,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:55:00,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:55:00,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:55:00,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:55:00,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:55:00,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 15:55:00,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:55:00,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:55:00,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:55:00,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:55:00,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:55:00,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:55:00,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 15:55:00,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:55:00,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:55:00,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:55:00,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:55:00,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:55:00,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 15:55:00,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:55:00,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:55:00,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:55:00,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:55:00,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:55:00,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:55:00,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:55:00,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:55:00,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:55:00,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:55:00,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:55:00,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:55:00,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:55:00,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 15:55:00,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:55:00,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:55:00,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:55:00,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:55:00,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 15:55:00,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 15:55:00,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:55:00,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:55:00,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:55:00,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:55:00,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:55:00,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:55:00,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:55:00,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 15:55:00,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:55:00,529 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 15:55:00,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,529 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 15:55:00,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:55:00,529 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 15:55:00,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,529 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 15:55:00,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:55:00,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 15:55:00,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:55:00,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:55:00,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 15:55:00,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:55:00,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 15:55:00,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 15:55:00,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa33dd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:55:00,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 15:55:00,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 15:55:00,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 15:55:00,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5d7a2c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 15:55:00,585 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:00,585 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:55:01,446 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:01,446 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:55:02,156 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:02,156 DEBUG: KMH enabled: False
2013-01-08 15:55:02,859 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:03,461 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:55:04,159 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:04,159 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:55:04,240 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:04,240 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:55:04,296 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:04,297 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:55:04,352 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:04,352 DEBUG: KMH enabled: False
2013-01-08 15:55:04,408 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:04,409 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:55:17,214 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 15:55:17,215 DEBUG: nvidia_current is not the alternative in use
2013-01-08 15:55:21,604 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n', '\tOption\t"NoLogo"\t"True"\n']})
2013-01-08 15:56:08,603 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:08,718 DEBUG: KMH enabled: True
2013-01-08 15:56:08,850 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:08,969 DEBUG: KMH enabled: True
2013-01-08 15:56:09,151 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:09,260 DEBUG: KMH enabled: True
2013-01-08 15:56:09,401 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:09,521 DEBUG: KMH enabled: True
2013-01-08 15:56:09,692 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:09,693 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:56:09,754 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:09,755 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:56:09,815 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:09,816 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:56:09,883 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:09,992 DEBUG: KMH enabled: True
2013-01-08 15:56:10,138 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:10,260 DEBUG: KMH enabled: True
2013-01-08 15:56:10,462 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:10,582 DEBUG: KMH enabled: True
2013-01-08 15:56:10,722 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:10,837 DEBUG: KMH enabled: True
2013-01-08 15:56:11,004 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:11,004 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 15:56:11,060 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:11,061 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 15:56:11,117 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 15:56:11,117 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 15:56:15,666 DEBUG: Shutting down
2013-01-08 18:38:40,334 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c>
2013-01-08 18:38:41,683 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic/modules.alias
2013-01-08 18:38:41,771 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 18:38:41,771 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 18:38:41,838 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 18:38:41,870 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 18:38:41,871 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 18:38:41,914 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 18:38:41,915 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 18:38:41,973 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 18:38:41,982 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 18:38:41,985 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:42,149 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 18:38:42,150 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 18:38:42,165 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 18:38:42,167 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:42,245 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 18:38:42,251 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 18:38:42,261 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 18:38:42,262 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:42,346 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:38:42,353 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 18:38:42,359 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 18:38:42,361 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:42,396 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 18:38:42,397 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 18:38:42,403 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 18:38:42,412 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 18:38:42,414 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:42,492 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:38:42,498 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 18:38:42,507 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 18:38:42,509 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:42,587 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 18:38:42,593 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 18:38:42,638 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 18:38:42,640 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:42,675 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 18:38:42,682 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:38:42,726 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 18:38:42,728 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:42,764 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 18:38:42,764 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 18:38:42,773 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 18:38:42,775 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 18:38:42,776 DEBUG: cdv.available: falling back to default
2013-01-08 18:38:42,846 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 18:38:42,846 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 18:38:42,886 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 18:38:42,909 DEBUG: Software modem not available
2013-01-08 18:38:42,910 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 18:38:42,916 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 18:38:42,926 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 18:38:42,926 DEBUG: fglrx.available: falling back to default
2013-01-08 18:38:43,004 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:38:43,010 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 18:38:43,020 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 18:38:43,020 DEBUG: fglrx.available: falling back to default
2013-01-08 18:38:43,097 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 18:38:43,097 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 18:38:43,106 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 18:38:43,145 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 18:38:43,146 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 18:38:43,146 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 18:38:43,158 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 18:38:43,168 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 18:38:43,232 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 18:38:43,232 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 18:38:43,308 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 18:38:43,309 DEBUG: Firmware for DVB cards not available
2013-01-08 18:38:43,310 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 18:38:43,319 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 18:38:43,320 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 18:38:43,320 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 18:38:43,320 DEBUG: all custom handlers loaded
2013-01-08 18:38:43,320 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 18:38:43,340 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 18:38:43,480 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 18:38:43,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:43,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:43,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 18:38:43,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 18:38:43,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 18:38:43,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 18:38:43,493 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:43,493 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 18:38:43,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 18:38:43,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 18:38:43,503 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:43,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,503 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:38:43,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 18:38:43,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 18:38:43,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 18:38:43,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 18:38:43,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 18:38:43,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 18:38:43,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 18:38:43,717 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 18:38:43,718 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 18:38:43,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 18:38:43,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 18:38:43,738 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 18:38:43,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,738 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 18:38:43,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:43,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 18:38:43,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 18:38:43,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 18:38:43,979 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:44,144 DEBUG: KMH enabled: True
2013-01-08 18:38:43,918 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:38:44,256 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:44,317 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:44,434 DEBUG: KMH enabled: True
2013-01-08 18:38:44,292 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:38:44,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 18:38:44,566 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:44,567 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:38:44,542 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:38:44,573 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 18:38:44,584 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:44,645 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:44,645 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:38:44,620 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:38:44,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 18:38:44,670 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:44,670 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:38:44,646 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 18:38:44,677 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 18:38:44,688 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:44,755 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:44,755 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:38:44,731 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 18:38:44,756 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 18:38:44,780 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:44,780 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:38:44,756 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:38:44,787 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:38:44,798 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:44,859 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:44,859 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:38:44,834 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:38:44,860 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 18:38:44,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:44,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 18:38:44,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:44,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 18:38:44,885 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:45,001 DEBUG: KMH enabled: True
2013-01-08 18:38:44,861 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:38:45,117 DEBUG: nvidia.available: falling back to default
2013-01-08 18:38:45,182 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:45,295 DEBUG: KMH enabled: True
2013-01-08 18:38:45,157 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:38:45,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 18:38:45,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 18:38:45,418 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 18:38:45,418 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 18:38:45,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 18:38:45,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 18:38:45,419 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 18:38:45,419 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,419 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 18:38:45,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:38:45,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:38:45,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 18:38:45,427 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 18:38:45,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,427 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 18:38:45,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 18:38:45,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:45,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:38:45,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 18:38:45,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:45,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 18:38:45,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 18:38:45,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 18:38:45,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:45,429 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,429 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:38:45,429 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 18:38:45,431 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 18:38:45,431 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,431 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 18:38:45,431 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 18:38:45,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:38:45,442 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:38:45,442 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 18:38:45,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:38:45,442 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:38:45,442 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,442 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 18:38:45,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 18:38:45,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:45,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:38:45,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 18:38:45,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:38:45,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:38:45,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 18:38:45,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:38:45,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 18:38:45,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 18:38:45,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 18:38:45,447 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:38:45,447 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,447 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 18:38:45,447 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 18:38:45,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 18:38:45,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 18:38:45,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 18:38:45,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 18:38:45,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:38:45,453 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 18:38:45,466 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 18:38:45,466 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 18:38:45,466 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 18:38:45,466 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,466 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 18:38:45,466 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 18:38:45,467 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 18:38:45,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,467 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 18:38:45,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 18:38:45,468 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 18:38:45,468 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,468 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,468 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 18:38:45,468 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:45,468 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,468 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:38:45,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 18:38:45,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:38:45,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c82d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'platform:eisa')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 18:38:45,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:38:45,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 18:38:45,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9f1c9ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 18:38:45,576 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:45,691 DEBUG: KMH enabled: True
2013-01-08 18:38:46,677 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:46,677 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:38:47,416 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:47,416 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:38:48,128 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:48,129 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:38:48,847 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:48,962 DEBUG: KMH enabled: True
2013-01-08 18:38:49,277 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:49,384 DEBUG: KMH enabled: True
2013-01-08 18:38:54,784 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:54,785 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:38:59,340 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:38:59,340 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:39:03,387 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:39:03,388 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-01-08 18:39:48,927 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:48,928 DEBUG: KMH enabled: False
2013-01-08 18:39:48,960 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:48,961 DEBUG: KMH enabled: False
2013-01-08 18:39:52,684 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:52,685 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:39:52,758 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:52,758 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:39:52,831 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:52,832 DEBUG: KMH enabled: False
2013-01-08 18:39:52,865 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:52,866 DEBUG: KMH enabled: False
2013-01-08 18:39:53,058 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:53,059 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:39:53,140 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:53,141 DEBUG: KMH enabled: False
2013-01-08 18:39:53,174 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:53,174 DEBUG: KMH enabled: False
2013-01-08 18:39:53,390 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:53,390 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:39:53,457 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:53,457 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:39:53,524 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:53,524 DEBUG: KMH enabled: False
2013-01-08 18:39:53,557 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:39:53,558 DEBUG: KMH enabled: False
2013-01-08 18:40:02,000 DEBUG: Shutting down
2013-01-08 18:41:15,139 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c>
2013-01-08 18:41:16,220 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic/modules.alias
2013-01-08 18:41:16,279 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 18:41:16,279 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 18:41:16,339 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 18:41:16,347 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 18:41:16,347 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 18:41:16,382 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 18:41:16,383 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 18:41:16,398 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 18:41:16,407 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 18:41:16,410 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:16,516 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 18:41:16,516 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 18:41:16,532 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 18:41:16,534 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:16,611 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 18:41:16,618 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 18:41:16,627 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 18:41:16,629 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:16,712 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:41:16,719 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 18:41:16,728 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 18:41:16,730 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:16,766 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 18:41:16,766 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 18:41:16,773 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 18:41:16,782 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 18:41:16,783 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:16,861 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:41:16,868 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 18:41:16,877 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 18:41:16,879 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:16,957 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 18:41:16,963 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 18:41:17,008 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 18:41:17,010 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:17,046 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 18:41:17,052 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:41:17,097 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 18:41:17,099 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:17,135 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 18:41:17,136 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 18:41:17,144 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 18:41:17,146 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 18:41:17,147 DEBUG: cdv.available: falling back to default
2013-01-08 18:41:17,217 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 18:41:17,218 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 18:41:17,256 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 18:41:17,273 DEBUG: Software modem not available
2013-01-08 18:41:17,274 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 18:41:17,284 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 18:41:17,294 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 18:41:17,294 DEBUG: fglrx.available: falling back to default
2013-01-08 18:41:17,373 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:41:17,379 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 18:41:17,389 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 18:41:17,389 DEBUG: fglrx.available: falling back to default
2013-01-08 18:41:17,468 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 18:41:17,468 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 18:41:17,477 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 18:41:17,516 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 18:41:17,516 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 18:41:17,516 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 18:41:17,528 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 18:41:17,538 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 18:41:17,602 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 18:41:17,602 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 18:41:17,650 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 18:41:17,651 DEBUG: Firmware for DVB cards not available
2013-01-08 18:41:17,651 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 18:41:17,660 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 18:41:17,661 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 18:41:17,661 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 18:41:17,661 DEBUG: all custom handlers loaded
2013-01-08 18:41:17,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 18:41:17,678 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 18:41:17,779 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:17,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 18:41:17,782 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:17,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:17,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:17,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 18:41:17,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 18:41:17,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 18:41:17,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 18:41:17,792 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:17,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:17,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 18:41:17,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 18:41:17,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 18:41:17,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:17,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:17,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:41:17,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:17,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 18:41:17,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 18:41:17,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 18:41:17,807 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 18:41:17,807 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:17,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 18:41:17,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 18:41:17,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 18:41:18,011 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 18:41:18,011 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 18:41:18,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 18:41:18,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 18:41:18,030 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 18:41:18,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,030 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 18:41:18,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 18:41:18,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 18:41:18,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 18:41:18,226 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,226 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:41:18,206 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 18:41:18,238 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:18,303 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,304 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:41:18,278 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 18:41:18,304 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 18:41:18,329 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,330 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:41:18,304 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:41:18,337 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 18:41:18,348 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:18,410 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,410 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:41:18,384 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:41:18,411 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 18:41:18,436 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,436 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:41:18,411 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 18:41:18,443 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 18:41:18,454 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:18,523 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,523 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:41:18,497 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 18:41:18,524 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 18:41:18,549 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,549 DEBUG: KMH enabled: False
2013-01-08 18:41:18,524 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:41:18,556 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:41:18,567 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:18,630 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,630 DEBUG: KMH enabled: False
2013-01-08 18:41:18,604 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:41:18,631 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 18:41:18,631 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 18:41:18,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 18:41:18,657 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,657 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:41:18,632 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 18:41:18,668 DEBUG: nvidia.available: falling back to default
2013-01-08 18:41:18,733 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,733 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:41:18,708 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-01-08 18:41:18,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 18:41:18,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 18:41:18,745 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 18:41:18,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 18:41:18,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 18:41:18,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 18:41:18,748 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 18:41:18,748 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 18:41:18,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:41:18,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:41:18,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 18:41:18,760 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 18:41:18,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,760 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 18:41:18,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 18:41:18,761 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:18,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,761 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:41:18,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 18:41:18,761 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:18,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 18:41:18,761 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 18:41:18,762 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 18:41:18,762 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:18,762 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,762 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:41:18,762 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 18:41:18,764 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 18:41:18,764 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,764 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 18:41:18,764 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 18:41:18,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:41:18,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:41:18,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 18:41:18,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:41:18,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:41:18,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 18:41:18,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 18:41:18,776 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:18,776 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,776 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:41:18,776 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 18:41:18,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:41:18,776 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:41:18,776 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,776 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 18:41:18,776 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:41:18,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 18:41:18,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 18:41:18,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 18:41:18,779 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:41:18,779 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,780 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 18:41:18,780 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 18:41:18,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 18:41:18,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 18:41:18,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 18:41:18,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 18:41:18,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:41:18,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 18:41:18,798 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 18:41:18,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 18:41:18,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 18:41:18,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 18:41:18,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 18:41:18,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 18:41:18,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 18:41:18,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 18:41:18,800 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 18:41:18,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 18:41:18,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:18,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:41:18,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 18:41:18,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:41:18,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8625d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 18:41:18,801 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'platform:eisa')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 18:41:18,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:41:18,803 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 18:41:18,804 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 18:41:18,804 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 18:41:18,804 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 18:41:18,804 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 18:41:18,804 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 18:41:18,804 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 18:41:18,804 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x88bf9ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 18:41:18,899 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:18,900 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:41:19,604 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:19,605 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:41:20,298 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:20,298 DEBUG: KMH enabled: False
2013-01-08 18:41:21,132 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:21,132 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:41:21,843 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:21,843 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:41:21,938 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:21,938 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:41:22,006 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt None other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:22,006 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:41:22,074 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:22,075 DEBUG: KMH enabled: False
2013-01-08 18:41:30,641 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:41:30,642 DEBUG: nvidia_current is not the alternative in use
2013-01-08 18:41:34,855 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n', '\tOption\t"NoLogo"\t"True"\n']})
2013-01-08 18:42:13,611 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:13,732 DEBUG: KMH enabled: True
2013-01-08 18:42:13,875 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:13,987 DEBUG: KMH enabled: True
2013-01-08 18:42:14,179 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:14,294 DEBUG: KMH enabled: True
2013-01-08 18:42:14,439 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:14,552 DEBUG: KMH enabled: True
2013-01-08 18:42:14,727 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:14,727 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:42:14,801 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:14,801 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:42:14,874 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:14,875 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:42:14,961 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:15,078 DEBUG: KMH enabled: True
2013-01-08 18:42:15,236 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:15,356 DEBUG: KMH enabled: True
2013-01-08 18:42:15,557 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:15,670 DEBUG: KMH enabled: True
2013-01-08 18:42:15,820 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:15,929 DEBUG: KMH enabled: True
2013-01-08 18:42:16,115 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:16,115 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:42:16,182 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:16,183 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:42:16,252 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:42:16,252 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:42:21,536 DEBUG: Shutting down
2013-01-08 18:46:32,830 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c>
2013-01-08 18:46:34,071 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic/modules.alias
2013-01-08 18:46:34,216 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 18:46:34,222 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 18:46:34,299 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 18:46:34,331 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 18:46:34,332 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 18:46:34,375 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 18:46:34,376 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 18:46:34,434 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 18:46:34,443 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 18:46:34,446 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:34,609 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 18:46:34,610 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 18:46:34,625 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 18:46:34,626 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:34,702 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 18:46:34,709 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 18:46:34,718 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 18:46:34,719 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:34,802 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:46:34,809 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 18:46:34,818 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 18:46:34,819 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:34,855 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 18:46:34,855 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 18:46:34,861 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 18:46:34,871 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 18:46:34,872 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:34,948 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:46:34,955 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 18:46:34,964 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 18:46:34,965 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:35,042 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 18:46:35,049 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 18:46:35,093 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 18:46:35,095 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:35,130 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 18:46:35,136 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:46:35,180 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 18:46:35,181 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:35,217 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 18:46:35,217 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 18:46:35,226 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 18:46:35,228 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 18:46:35,229 DEBUG: cdv.available: falling back to default
2013-01-08 18:46:35,298 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 18:46:35,299 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 18:46:35,337 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 18:46:35,362 DEBUG: Software modem not available
2013-01-08 18:46:35,362 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 18:46:35,373 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 18:46:35,382 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 18:46:35,383 DEBUG: fglrx.available: falling back to default
2013-01-08 18:46:35,459 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:46:35,466 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 18:46:35,475 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 18:46:35,475 DEBUG: fglrx.available: falling back to default
2013-01-08 18:46:35,552 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 18:46:35,553 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 18:46:35,561 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 18:46:35,600 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 18:46:35,601 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 18:46:35,601 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 18:46:35,613 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 18:46:35,623 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 18:46:35,686 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 18:46:35,687 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 18:46:35,769 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 18:46:35,770 DEBUG: Firmware for DVB cards not available
2013-01-08 18:46:35,770 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 18:46:35,778 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 18:46:35,779 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 18:46:35,780 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 18:46:35,780 DEBUG: all custom handlers loaded
2013-01-08 18:46:35,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 18:46:35,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 18:46:35,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:35,931 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 18:46:35,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:35,935 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:35,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:35,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 18:46:35,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 18:46:35,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 18:46:35,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 18:46:35,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:35,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:35,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 18:46:35,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 18:46:35,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 18:46:35,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:35,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:35,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:46:35,954 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:35,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 18:46:35,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 18:46:35,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 18:46:35,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 18:46:35,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:35,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 18:46:35,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 18:46:35,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 18:46:36,163 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 18:46:36,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:36,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 18:46:36,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 18:46:36,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 18:46:36,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 18:46:36,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:36,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 18:46:36,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:36,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 18:46:36,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 18:46:36,358 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 18:46:36,422 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:36,583 DEBUG: KMH enabled: True
2013-01-08 18:46:36,358 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:46:36,708 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:36,772 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:36,879 DEBUG: KMH enabled: True
2013-01-08 18:46:36,748 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:46:36,993 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 18:46:37,017 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:37,018 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:46:36,994 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:46:37,024 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 18:46:37,035 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:37,095 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:37,095 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:46:37,071 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:46:37,096 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 18:46:37,120 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:37,120 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:46:37,096 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 18:46:37,127 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 18:46:37,137 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:37,204 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:37,204 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:46:37,180 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 18:46:37,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 18:46:37,229 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:37,229 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:46:37,205 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:46:37,236 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:46:37,246 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:37,306 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:37,306 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:46:37,282 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:46:37,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 18:46:37,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,308 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 18:46:37,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,308 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 18:46:37,332 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:37,455 DEBUG: KMH enabled: True
2013-01-08 18:46:37,308 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:46:37,579 DEBUG: nvidia.available: falling back to default
2013-01-08 18:46:37,642 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:37,756 DEBUG: KMH enabled: True
2013-01-08 18:46:37,618 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:46:37,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 18:46:37,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 18:46:37,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 18:46:37,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 18:46:37,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 18:46:37,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 18:46:37,883 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 18:46:37,883 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 18:46:37,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:46:37,887 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:46:37,887 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 18:46:37,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 18:46:37,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 18:46:37,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 18:46:37,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:37,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:46:37,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 18:46:37,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:37,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 18:46:37,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 18:46:37,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 18:46:37,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:37,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:46:37,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 18:46:37,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 18:46:37,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 18:46:37,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 18:46:37,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:46:37,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:46:37,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 18:46:37,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:46:37,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:46:37,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 18:46:37,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 18:46:37,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:37,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:46:37,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 18:46:37,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:46:37,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:46:37,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 18:46:37,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:46:37,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 18:46:37,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 18:46:37,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 18:46:37,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:46:37,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 18:46:37,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 18:46:37,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 18:46:37,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 18:46:37,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 18:46:37,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 18:46:37,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:46:37,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 18:46:37,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 18:46:37,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,931 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 18:46:37,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 18:46:37,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 18:46:37,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 18:46:37,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 18:46:37,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 18:46:37,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 18:46:37,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 18:46:37,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 18:46:37,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:37,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:46:37,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 18:46:37,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:46:37,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f78d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'platform:eisa')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 18:46:37,934 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:46:37,935 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 18:46:37,936 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92129ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 18:46:38,029 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:38,141 DEBUG: KMH enabled: True
2013-01-08 18:46:39,115 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:39,116 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:46:39,820 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:39,820 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:46:40,512 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:40,513 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:46:41,198 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:41,319 DEBUG: KMH enabled: True
2013-01-08 18:46:41,617 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:46:41,732 DEBUG: KMH enabled: True
2013-01-08 18:46:57,406 DEBUG: Shutting down
2013-01-08 18:47:03,618 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c>
2013-01-08 18:47:04,705 DEBUG: reading modalias file /lib/modules/3.2.0-35-generic/modules.alias
2013-01-08 18:47:04,765 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-01-08 18:47:04,765 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-01-08 18:47:04,823 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-01-08 18:47:04,830 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-01-08 18:47:04,830 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-01-08 18:47:04,866 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-01-08 18:47:04,866 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-01-08 18:47:04,881 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-01-08 18:47:04,890 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-01-08 18:47:04,893 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:05,001 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 18:47:05,001 DEBUG: NVIDIA accelerated graphics driver not available
2013-01-08 18:47:05,017 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-01-08 18:47:05,018 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:05,095 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 18:47:05,102 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 18:47:05,111 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-01-08 18:47:05,112 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:05,194 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:47:05,200 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-01-08 18:47:05,209 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-01-08 18:47:05,210 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:05,246 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-01-08 18:47:05,247 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-01-08 18:47:05,253 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-01-08 18:47:05,262 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-01-08 18:47:05,264 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:05,340 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:47:05,346 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-01-08 18:47:05,355 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-01-08 18:47:05,357 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:05,434 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-01-08 18:47:05,440 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 18:47:05,484 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-01-08 18:47:05,486 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:05,521 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 18:47:05,527 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:47:05,571 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-01-08 18:47:05,573 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:05,608 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-01-08 18:47:05,609 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-01-08 18:47:05,617 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-01-08 18:47:05,619 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-01-08 18:47:05,620 DEBUG: cdv.available: falling back to default
2013-01-08 18:47:05,689 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-01-08 18:47:05,690 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-01-08 18:47:05,728 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-01-08 18:47:05,745 DEBUG: Software modem not available
2013-01-08 18:47:05,745 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-01-08 18:47:05,756 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-08 18:47:05,765 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-01-08 18:47:05,766 DEBUG: fglrx.available: falling back to default
2013-01-08 18:47:05,843 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-01-08 18:47:05,849 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-01-08 18:47:05,858 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-01-08 18:47:05,859 DEBUG: fglrx.available: falling back to default
2013-01-08 18:47:05,935 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-01-08 18:47:05,936 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-01-08 18:47:05,944 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-01-08 18:47:05,982 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-01-08 18:47:05,983 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-01-08 18:47:05,983 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-01-08 18:47:05,994 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-01-08 18:47:06,004 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-01-08 18:47:06,068 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-01-08 18:47:06,068 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-01-08 18:47:06,115 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-01-08 18:47:06,116 DEBUG: Firmware for DVB cards not available
2013-01-08 18:47:06,116 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-01-08 18:47:06,124 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-01-08 18:47:06,125 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-01-08 18:47:06,126 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-01-08 18:47:06,126 DEBUG: all custom handlers loaded
2013-01-08 18:47:06,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 18:47:06,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-01-08 18:47:06,235 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,235 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 18:47:06,238 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:06,238 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:06,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 18:47:06,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 18:47:06,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 18:47:06,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 18:47:06,247 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:06,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'platform:eisa')
2013-01-08 18:47:06,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 18:47:06,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 18:47:06,257 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:06,257 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,257 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:47:06,257 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 18:47:06,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 18:47:06,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 18:47:06,263 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-01-08 18:47:06,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 18:47:06,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 18:47:06,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 18:47:06,465 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-01-08 18:47:06,465 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 18:47:06,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 18:47:06,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 18:47:06,485 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-01-08 18:47:06,485 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,485 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-01-08 18:47:06,485 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:06,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 18:47:06,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 18:47:06,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-01-08 18:47:06,683 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:06,807 DEBUG: KMH enabled: True
2013-01-08 18:47:06,660 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:47:06,938 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:07,002 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,107 DEBUG: KMH enabled: True
2013-01-08 18:47:06,978 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:47:07,227 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-01-08 18:47:07,251 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,252 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:47:07,227 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:47:07,258 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-01-08 18:47:07,269 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:07,329 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,330 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:47:07,305 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:47:07,330 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-01-08 18:47:07,354 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,355 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:47:07,331 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 18:47:07,361 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-01-08 18:47:07,372 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:07,439 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,439 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:47:07,414 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-01-08 18:47:07,440 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-01-08 18:47:07,464 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,464 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:47:07,440 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:47:07,471 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:47:07,481 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:07,541 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,542 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:47:07,517 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-01-08 18:47:07,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-01-08 18:47:07,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:07,543 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-01-08 18:47:07,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:07,544 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-01-08 18:47:07,567 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,684 DEBUG: KMH enabled: True
2013-01-08 18:47:07,544 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:47:07,802 DEBUG: nvidia.available: falling back to default
2013-01-08 18:47:07,865 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:07,974 DEBUG: KMH enabled: True
2013-01-08 18:47:07,841 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2013-01-08 18:47:08,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 18:47:08,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 18:47:08,095 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-01-08 18:47:08,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 18:47:08,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 18:47:08,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 18:47:08,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-01-08 18:47:08,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 18:47:08,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:47:08,103 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:47:08,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 18:47:08,108 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 18:47:08,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,109 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-01-08 18:47:08,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 18:47:08,109 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:08,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,109 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:47:08,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 18:47:08,109 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:08,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 18:47:08,110 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-01-08 18:47:08,110 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 18:47:08,110 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:08,110 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,110 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:47:08,110 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 18:47:08,112 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 18:47:08,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,112 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-01-08 18:47:08,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 18:47:08,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:47:08,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:47:08,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 18:47:08,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:47:08,124 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:47:08,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,124 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 18:47:08,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 18:47:08,124 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:08,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,124 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:47:08,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 18:47:08,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:47:08,125 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:47:08,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,125 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-01-08 18:47:08,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:47:08,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 18:47:08,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 18:47:08,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 18:47:08,128 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-01-08 18:47:08,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,128 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-01-08 18:47:08,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 18:47:08,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 18:47:08,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 18:47:08,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 18:47:08,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 18:47:08,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:47:08,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 18:47:08,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-01-08 18:47:08,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 18:47:08,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-01-08 18:47:08,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-01-08 18:47:08,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 18:47:08,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-01-08 18:47:08,148 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,148 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-01-08 18:47:08,148 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 18:47:08,149 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-01-08 18:47:08,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 18:47:08,149 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:08,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,149 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-01-08 18:47:08,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 18:47:08,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-01-08 18:47:08,150 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ffdd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0800:')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'platform:eisa')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0501:')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc02ip00')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v000010DEd000005E2sv00003842sd00001257bc03sc00i00')
2013-01-08 18:47:08,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc01ip00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,A8,AB,AC,B6,D0,D2,D9,EA,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic01isc01ip00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0003v046DpC30Fe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001002sd00004383bc04sc03i00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1101:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A87TDEVO:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc00ip00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046DpC30Fd2300dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-01-08 18:47:08,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v046Dp082Dd0011dcEFdsc02dp01ic0Eisc02ip00')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000843Fbc01sc06i01')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'platform:pcspkr')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'usb:v058Fp6361d0100dc00dsc00dp00ic08isc06ip50')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0003v046Dp082De0011-e0,1,kD4,ramlsfw')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-01-08 18:47:08,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2979ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-01-08 18:47:08,252 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:08,375 DEBUG: KMH enabled: True
2013-01-08 18:47:09,283 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:09,284 DEBUG: nvidia_current_updates is not the alternative in use
2013-01-08 18:47:09,989 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:09,990 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:47:10,680 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt /usr/lib/nvidia-experimental-310/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-310/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:10,681 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-01-08 18:47:11,376 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:11,490 DEBUG: KMH enabled: True
2013-01-08 18:47:11,816 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:11,945 DEBUG: KMH enabled: True
2013-01-08 18:47:14,056 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:14,056 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:47:15,521 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:15,521 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:47:34,180 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-01-08 18:47:34,180 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-01-08 18:47:39,194 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-01-08 18:47:39,194 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-01-08 18:48:23,211 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:48:23,211 DEBUG: KMH enabled: False
2013-01-08 18:48:23,244 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt /usr/lib/nvidia-experimental-304/ld.so.conf current_alt /usr/lib/nvidia-experimental-304/ld.so.conf other target alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf other current alt /usr/lib/nvidia-experimental-304/alt_ld.so.conf
2013-01-08 18:48:23,244 DEBUG: KMH enabled: False

---

### Post by Kymus on 2013-01-15
bump

---

