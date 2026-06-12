---
title: "HP Envy 14 Ubuntu 12.04 Intel Integrated/ATI Radeon 5000 Series"
date: 2012-08-20
forum: Hardware
---

### Post by megamegerr on 2012-08-20
I am on an HP Envy 14 64 bit, and the proper resolution that I should be using  is 1366x768. This is not an option and I am stuck on 1024x768. I've also noticed that some colors in pictures are off, so I am assuming that this is a GPU issue. I am  using Linux 12.04, dual booting with Windows 7.

lspci | grep VGA: 

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

I also tried using the xrandr command:
  xrandr --newmode "1366x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
  But I get an error:
  xrandr: Failed to get size of gamma for output default

I have installed ATI/AMD proprietary FGLRX graphics driver (it showed up in Additional Drivers). But there is another one called ATI/AMD proprietary FGLRX graphics driver (post-release updates) which I have trouble installing because it gives me an error and tells me to look at some sort of jockey log.

lsmod returns the following: [http://paste.ubuntu.com/1156618/](http://paste.ubuntu.com/1156618/)
[SIZE=3]
Any help would be much appreciated!!!![/SIZE]

---

### Post by amaz1ng on 2012-09-07
I'm having the same problem. I've got a Lenovo IdeaPad Y460P. lspci | grep VGA returns

```

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

```

and my /var/log/jockey.log after clicking "Activate" on ATI/AMD propriatary FGLRX graphics driver (post-release updates) on "Additional Drivers":

```

2012-09-07 18:16:49,395 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c>
2012-09-07 18:16:50,523 DEBUG: reading modalias file /lib/modules/3.2.0-30-generic-pae/modules.alias
2012-09-07 18:16:50,714 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-09-07 18:16:50,733 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-09-07 18:16:51,782 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-09-07 18:16:52,036 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-09-07 18:16:52,046 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-09-07 18:16:52,046 DEBUG: fglrx.available: falling back to default
2012-09-07 18:16:53,510 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-07 18:16:53,516 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-09-07 18:16:53,522 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-09-07 18:16:53,523 DEBUG: fglrx.available: falling back to default
2012-09-07 18:16:53,575 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-09-07 18:16:53,576 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-09-07 18:16:53,605 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-09-07 18:16:53,605 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-09-07 18:16:53,606 DEBUG: cdv.available: falling back to default
2012-09-07 18:16:53,640 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-09-07 18:16:53,640 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-09-07 18:16:53,676 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-09-07 18:16:53,683 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-09-07 18:16:53,733 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-09-07 18:16:53,733 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-09-07 18:16:53,739 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-09-07 18:16:53,740 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-09-07 18:16:53,740 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-09-07 18:16:53,740 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-09-07 18:16:53,853 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-09-07 18:16:53,853 DEBUG: Firmware for DVB cards not available
2012-09-07 18:16:53,853 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-09-07 18:16:53,904 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-09-07 18:16:53,990 DEBUG: Software modem not available
2012-09-07 18:16:53,990 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-09-07 18:16:54,018 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-07 18:16:54,048 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-09-07 18:16:54,048 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-09-07 18:16:54,048 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-09-07 18:16:54,054 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-09-07 18:16:54,054 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-09-07 18:16:54,082 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-09-07 18:16:54,083 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-09-07 18:16:54,126 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-09-07 18:16:54,133 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-09-07 18:16:54,135 DEBUG: nvidia.available: falling back to default
2012-09-07 18:16:54,164 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-09-07 18:16:54,164 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-07 18:16:54,169 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-09-07 18:16:54,175 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-09-07 18:16:54,176 DEBUG: nvidia.available: falling back to default
2012-09-07 18:16:54,229 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-09-07 18:16:54,234 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-09-07 18:16:54,239 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-09-07 18:16:54,241 DEBUG: nvidia.available: falling back to default
2012-09-07 18:16:54,296 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-07 18:16:54,300 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-09-07 18:16:54,313 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-09-07 18:16:54,314 DEBUG: nvidia.available: falling back to default
2012-09-07 18:16:54,352 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-07 18:16:54,357 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-09-07 18:16:54,361 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-09-07 18:16:54,362 DEBUG: nvidia.available: falling back to default
2012-09-07 18:16:54,406 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-09-07 18:16:54,409 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-09-07 18:16:54,411 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-09-07 18:16:54,412 DEBUG: nvidia.available: falling back to default
2012-09-07 18:16:54,423 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-09-07 18:16:54,423 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-07 18:16:54,423 DEBUG: all custom handlers loaded
2012-09-07 18:16:54,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-09-07 18:16:54,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-07 18:16:54,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-07 18:16:54,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:54,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:16:54,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-09-07 18:16:54,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-09-07 18:16:54,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-07 18:16:54,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-07 18:16:54,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-09-07 18:16:54,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-09-07 18:16:54,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-07 18:16:54,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:54,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:16:54,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'platform:regulatory')
2012-09-07 18:16:54,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-07 18:16:54,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-09-07 18:16:54,921 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-09-07 18:16:54,921 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-09-07 18:16:54,922 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:54,922 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,922 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:16:54,922 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-07 18:16:54,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-09-07 18:16:54,924 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-09-07 18:16:54,924 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'platform:eisa')
2012-09-07 18:16:54,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-09-07 18:16:54,926 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-09-07 18:16:54,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'platform:ideapad')
2012-09-07 18:16:54,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-07 18:16:54,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-09-07 18:16:54,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-09-07 18:16:54,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:VPC2004:')
2012-09-07 18:16:54,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-07 18:16:54,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-09-07 18:16:54,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-09-07 18:16:54,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:54,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-09-07 18:16:55,370 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:16:55,371 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:16:54,931 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-09-07 18:16:55,377 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-09-07 18:16:55,385 DEBUG: fglrx.available: falling back to default
2012-09-07 18:16:55,427 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:16:55,427 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:16:55,410 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-09-07 18:16:55,427 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-09-07 18:16:55,437 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:16:55,438 DEBUG: fglrx is not the alternative in use
2012-09-07 18:16:55,428 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-09-07 18:16:55,440 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-09-07 18:16:55,443 DEBUG: fglrx.available: falling back to default
2012-09-07 18:16:55,475 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:16:55,476 DEBUG: fglrx is not the alternative in use
2012-09-07 18:16:55,455 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-09-07 18:16:55,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-07 18:16:55,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-09-07 18:16:55,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-07 18:16:55,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-07 18:16:55,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-09-07 18:16:55,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-09-07 18:16:55,477 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-09-07 18:16:55,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-09-07 18:16:55,478 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:55,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,478 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:16:55,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-07 18:16:55,478 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:55,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-07 18:16:55,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:55,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-07 18:16:55,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-07 18:16:55,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-07 18:16:55,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:16:55,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-09-07 18:16:55,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-09-07 18:16:55,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-07 18:16:55,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-07 18:16:55,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:55,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-09-07 18:16:55,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-09-07 18:16:55,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-09-07 18:16:55,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-09-07 18:16:55,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-09-07 18:16:55,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-09-07 18:16:55,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-09-07 18:16:55,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-09-07 18:16:55,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-09-07 18:16:55,496 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'platform:pcspkr')
2012-09-07 18:16:55,496 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-09-07 18:16:55,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,496 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-09-07 18:16:55,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,496 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-09-07 18:16:55,496 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:55,497 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,497 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:16:55,497 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-07 18:16:55,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-09-07 18:16:55,499 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-07 18:16:55,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,499 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-07 18:16:55,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-07 18:16:55,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-07 18:16:55,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-09-07 18:16:55,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-09-07 18:16:55,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-07 18:16:55,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:55,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-09-07 18:16:55,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-09-07 18:16:55,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-07 18:16:55,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:55,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:16:55,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-07 18:16:55,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:16:55,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:16:55,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7218a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-07 18:16:55,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-09-07 18:16:55,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-07 18:16:55,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-09-07 18:16:55,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'platform:regulatory')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'platform:eisa')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'platform:ideapad')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:VPC2004:')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-09-07 18:16:55,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'platform:pcspkr')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-09-07 18:16:55,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-07 18:16:55,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-07 18:16:55,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-07 18:16:55,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-09-07 18:16:55,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-07 18:16:55,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-07 18:16:55,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99ff56c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-07 18:16:55,570 DEBUG: handler xorg:fglrx_updates previously unseen
2012-09-07 18:16:55,570 DEBUG: handler xorg:fglrx previously unseen
2012-09-07 18:16:55,570 DEBUG: writing back check cache /var/cache/jockey/check
2012-09-07 18:16:55,591 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:16:55,591 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:16:55,609 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:16:55,609 DEBUG: fglrx is not the alternative in use
2012-09-07 18:16:55,646 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:16:55,646 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:17:45,278 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:17:45,278 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:17:45,475 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:17:45,475 DEBUG: fglrx is not the alternative in use
2012-09-07 18:17:45,516 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:17:45,516 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:17:45,580 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:17:45,581 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:17:45,617 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:17:45,618 DEBUG: fglrx is not the alternative in use
2012-09-07 18:17:49,469 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:17:49,469 DEBUG: fglrx is not the alternative in use
2012-09-07 18:17:50,310 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:17:50,310 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:17:52,308 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:17:52,308 DEBUG: fglrx is not the alternative in use
2012-09-07 18:17:57,299 DEBUG: Shutting down
2012-09-07 18:28:14,892 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c>
2012-09-07 18:28:16,040 DEBUG: reading modalias file /lib/modules/3.2.0-30-generic-pae/modules.alias
2012-09-07 18:28:16,105 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-09-07 18:28:16,106 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-09-07 18:28:16,159 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-09-07 18:28:16,170 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-09-07 18:28:16,178 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-09-07 18:28:16,178 DEBUG: fglrx.available: falling back to default
2012-09-07 18:28:16,278 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-07 18:28:16,285 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-09-07 18:28:16,293 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-09-07 18:28:16,293 DEBUG: fglrx.available: falling back to default
2012-09-07 18:28:16,360 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-09-07 18:28:16,360 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-09-07 18:28:16,369 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-09-07 18:28:16,370 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-09-07 18:28:16,370 DEBUG: cdv.available: falling back to default
2012-09-07 18:28:16,431 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-09-07 18:28:16,431 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-09-07 18:28:16,442 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-09-07 18:28:16,450 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-09-07 18:28:16,504 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-09-07 18:28:16,505 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-09-07 18:28:16,513 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-09-07 18:28:16,514 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-09-07 18:28:16,514 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-09-07 18:28:16,514 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-09-07 18:28:16,558 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-09-07 18:28:16,559 DEBUG: Firmware for DVB cards not available
2012-09-07 18:28:16,559 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-09-07 18:28:16,590 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-09-07 18:28:16,606 DEBUG: Software modem not available
2012-09-07 18:28:16,606 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-09-07 18:28:16,614 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-07 18:28:16,648 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-09-07 18:28:16,648 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-09-07 18:28:16,648 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-09-07 18:28:16,655 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-09-07 18:28:16,656 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-09-07 18:28:16,686 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-09-07 18:28:16,686 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-09-07 18:28:16,699 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-09-07 18:28:16,706 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-09-07 18:28:16,709 DEBUG: nvidia.available: falling back to default
2012-09-07 18:28:16,739 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-09-07 18:28:16,740 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-07 18:28:16,746 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-09-07 18:28:16,753 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-09-07 18:28:16,755 DEBUG: nvidia.available: falling back to default
2012-09-07 18:28:16,821 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-09-07 18:28:16,827 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-09-07 18:28:16,836 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-09-07 18:28:16,838 DEBUG: nvidia.available: falling back to default
2012-09-07 18:28:16,903 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-07 18:28:16,910 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-09-07 18:28:16,917 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-09-07 18:28:16,919 DEBUG: nvidia.available: falling back to default
2012-09-07 18:28:16,984 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-07 18:28:16,990 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-09-07 18:28:16,998 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-09-07 18:28:16,999 DEBUG: nvidia.available: falling back to default
2012-09-07 18:28:17,065 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-09-07 18:28:17,071 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-09-07 18:28:17,079 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-09-07 18:28:17,080 DEBUG: nvidia.available: falling back to default
2012-09-07 18:28:17,110 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-09-07 18:28:17,111 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-07 18:28:17,111 DEBUG: all custom handlers loaded
2012-09-07 18:28:17,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-09-07 18:28:17,346 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-07 18:28:17,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-07 18:28:17,418 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,418 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,418 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:28:17,418 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-09-07 18:28:17,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-09-07 18:28:17,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-07 18:28:17,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-07 18:28:17,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-09-07 18:28:17,626 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-09-07 18:28:17,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-07 18:28:17,626 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,626 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:28:17,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'platform:regulatory')
2012-09-07 18:28:17,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-07 18:28:17,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-09-07 18:28:17,639 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-09-07 18:28:17,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-09-07 18:28:17,639 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,639 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:28:17,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-07 18:28:17,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-09-07 18:28:17,642 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-09-07 18:28:17,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'platform:eisa')
2012-09-07 18:28:17,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-09-07 18:28:17,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-09-07 18:28:17,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'platform:ideapad')
2012-09-07 18:28:17,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-07 18:28:17,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-09-07 18:28:17,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-09-07 18:28:17,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:VPC2004:')
2012-09-07 18:28:17,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-07 18:28:17,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-09-07 18:28:17,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-09-07 18:28:17,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-09-07 18:28:17,670 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:17,671 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:17,649 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-09-07 18:28:17,677 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-09-07 18:28:17,685 DEBUG: fglrx.available: falling back to default
2012-09-07 18:28:17,742 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:17,743 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:17,720 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-09-07 18:28:17,743 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-09-07 18:28:17,766 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:17,766 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:17,744 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-09-07 18:28:17,773 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-09-07 18:28:17,780 DEBUG: fglrx.available: falling back to default
2012-09-07 18:28:17,837 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:17,838 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:17,815 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-09-07 18:28:17,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-07 18:28:17,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-09-07 18:28:17,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-07 18:28:17,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-07 18:28:17,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-09-07 18:28:17,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-09-07 18:28:17,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-09-07 18:28:17,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-09-07 18:28:17,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:28:17,842 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-07 18:28:17,842 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-07 18:28:17,843 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,843 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-07 18:28:17,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,844 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-07 18:28:17,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,844 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-07 18:28:17,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:28:17,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-09-07 18:28:17,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-09-07 18:28:17,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-07 18:28:17,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-07 18:28:17,860 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,860 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-09-07 18:28:17,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-09-07 18:28:17,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-09-07 18:28:17,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-09-07 18:28:17,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-09-07 18:28:17,863 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-09-07 18:28:17,863 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-09-07 18:28:17,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-09-07 18:28:17,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-09-07 18:28:17,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'platform:pcspkr')
2012-09-07 18:28:17,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-09-07 18:28:17,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-09-07 18:28:17,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-09-07 18:28:17,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:28:17,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-07 18:28:17,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-09-07 18:28:17,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-07 18:28:17,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-07 18:28:17,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-07 18:28:17,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-07 18:28:17,875 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-09-07 18:28:17,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,875 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-09-07 18:28:17,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-07 18:28:17,875 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-09-07 18:28:17,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-09-07 18:28:17,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-07 18:28:17,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-07 18:28:17,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-07 18:28:17,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-07 18:28:17,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7270a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'platform:regulatory')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'platform:eisa')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-09-07 18:28:17,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'platform:ideapad')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:VPC2004:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-09-07 18:28:17,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'platform:pcspkr')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-07 18:28:17,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9ffb56c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-07 18:28:17,972 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:17,972 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:18,009 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:18,009 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:18,060 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:18,060 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:18,124 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:18,124 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:18,169 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:18,169 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:23,797 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:23,797 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:24,931 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:24,932 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:25,076 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:25,076 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:28,903 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:28,904 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:30,930 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:30,931 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:45,064 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:45,065 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:50,713 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:50,714 DEBUG: fglrx is not the alternative in use
2012-09-07 18:28:51,656 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:51,656 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:54,572 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-09-07 18:28:54,572 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:28:58,023 DEBUG: Installing package: fglrx-updates
2012-09-07 18:28:58,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-09-07 18:28:58,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-09-07 18:28:58,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-09-07 18:28:58,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-09-07 18:28:58,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.002342
2012-09-07 18:28:58,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.161450
2012-09-07 18:28:58,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.164895
2012-09-07 18:28:58,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.355740
2012-09-07 18:28:58,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.360688
2012-09-07 18:28:59,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.182879
2012-09-07 18:28:59,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.639316
2012-09-07 18:29:00,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.503827
2012-09-07 18:29:00,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.168834
2012-09-07 18:29:01,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.842911
2012-09-07 18:29:01,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.504896
2012-09-07 18:29:02,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.169904
2012-09-07 18:29:02,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.828866
2012-09-07 18:29:03,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.466669
2012-09-07 18:29:03,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.128654
2012-09-07 18:29:04,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.805753
2012-09-07 18:29:04,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.425419
2012-09-07 18:29:05,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.069268
2012-09-07 18:29:05,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.755435
2012-09-07 18:29:06,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.420443
2012-09-07 18:29:06,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.049178
2012-09-07 18:29:07,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.744413
2012-09-07 18:29:07,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.382216
2012-09-07 18:29:08,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.053269
2012-09-07 18:29:08,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.709209
2012-09-07 18:29:09,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.362126
2012-09-07 18:29:09,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.021088
2012-09-07 18:29:10,061 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.674005
2012-09-07 18:29:10,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.332967
2012-09-07 18:29:11,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.991930
2012-09-07 18:29:11,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.650892
2012-09-07 18:29:12,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.303809
2012-09-07 18:29:12,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.962771
2012-09-07 18:29:13,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.630802
2012-09-07 18:29:13,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.271628
2012-09-07 18:29:14,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.918499
2012-09-07 18:29:14,573 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.595598
2012-09-07 18:29:15,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.248515
2012-09-07 18:29:15,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.913522
2012-09-07 18:29:16,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.560394
2012-09-07 18:29:16,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.225402
2012-09-07 18:29:17,079 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.878318
2012-09-07 18:29:17,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.531235
2012-09-07 18:29:18,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.199266
2012-09-07 18:29:18,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.852183
2012-09-07 18:29:19,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.514168
2012-09-07 18:29:19,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.145925
2012-09-07 18:29:20,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.807910
2012-09-07 18:29:20,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.472918
2012-09-07 18:29:21,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.122812
2012-09-07 18:29:21,591 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.790843
2012-09-07 18:29:22,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.443760
2012-09-07 18:29:22,594 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.093654
2012-09-07 18:29:23,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.755639
2012-09-07 18:29:23,597 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.408555
2012-09-07 18:29:24,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.055427
2012-09-07 18:29:24,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.717412
2012-09-07 18:29:25,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.376374
2012-09-07 18:29:25,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.032314
2012-09-07 18:29:26,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.670117
2012-09-07 18:29:26,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.326056
2012-09-07 18:29:27,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.009201
2012-09-07 18:29:27,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.659095
2012-09-07 18:29:28,114 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.318057
2012-09-07 18:29:28,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.949815
2012-09-07 18:29:29,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.626914
2012-09-07 18:29:29,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.285876
2012-09-07 18:29:30,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.944838
2012-09-07 18:29:30,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.597755
2012-09-07 18:29:31,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.247649
2012-09-07 18:29:31,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.915680
2012-09-07 18:29:32,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.565574
2012-09-07 18:29:32,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.227559
2012-09-07 18:29:33,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.499607
2012-09-07 18:29:33,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.488051
2012-09-07 18:29:34,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.174218
2012-09-07 18:29:34,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.848294
2012-09-07 18:29:35,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.498188
2012-09-07 18:29:35,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.166219
2012-09-07 18:29:36,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.807045
2012-09-07 18:29:36,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.472053
2012-09-07 18:29:37,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.127992
2012-09-07 18:29:37,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.780909
2012-09-07 18:29:38,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.436849
2012-09-07 18:29:38,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.092788
2012-09-07 18:29:39,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.751750
2012-09-07 18:29:39,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.404667
2012-09-07 18:29:40,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.057584
2012-09-07 18:29:40,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.716546
2012-09-07 18:29:41,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.381554
2012-09-07 18:29:41,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.040517
2012-09-07 18:29:42,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.693433
2012-09-07 18:29:42,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.340305
2012-09-07 18:29:43,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.990199
2012-09-07 18:29:43,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.643116
2012-09-07 18:29:44,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.317192
2012-09-07 18:29:44,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.967086
2012-09-07 18:29:45,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.623025
2012-09-07 18:29:45,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.266874
2012-09-07 18:29:46,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.937927
2012-09-07 18:29:46,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.557594
2012-09-07 18:29:47,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.237715
2012-09-07 18:29:47,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.902723
2012-09-07 18:29:48,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.652368
2012-09-07 18:29:48,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.438287
2012-09-07 18:29:49,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.166773
2012-09-07 18:29:49,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.831780
2012-09-07 18:29:50,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.496788
2012-09-07 18:29:50,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.143660
2012-09-07 18:29:51,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.811690
2012-09-07 18:29:51,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.461584
2012-09-07 18:29:52,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.132638
2012-09-07 18:29:52,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.791600
2012-09-07 18:29:53,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.444517
2012-09-07 18:29:53,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.106502
2012-09-07 18:29:54,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.756396
2012-09-07 18:29:54,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.418381
2012-09-07 18:29:55,192 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.080366
2012-09-07 18:29:55,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.736306
2012-09-07 18:29:56,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.380154
2012-09-07 18:29:56,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.042139
2012-09-07 18:29:57,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.701102
2012-09-07 18:29:57,699 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.357041
2012-09-07 18:29:58,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.022049
2012-09-07 18:29:58,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.681011
2012-09-07 18:29:59,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.330905
2012-09-07 18:29:59,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.977777
2012-09-07 18:30:00,207 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.645807
2012-09-07 18:30:00,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.274542
2012-09-07 18:30:01,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.954664
2012-09-07 18:30:01,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.583398
2012-09-07 18:30:02,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.245384
2012-09-07 18:30:02,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.934574
2012-09-07 18:30:03,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.578422
2012-09-07 18:30:03,716 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.243430
2012-09-07 18:30:04,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.883831
2012-09-07 18:30:04,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.003946
2012-09-07 18:30:04,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.007506
2012-09-07 18:30:04,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.636241
2012-09-07 18:30:05,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.322408
2012-09-07 18:30:05,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.951143
2012-09-07 18:30:06,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.601037
2012-09-07 18:30:06,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.281158
2012-09-07 18:30:07,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.946166
2012-09-07 18:30:07,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.602106
2012-09-07 18:30:08,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.255023
2012-09-07 18:30:08,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.920031
2012-09-07 18:30:09,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.563879
2012-09-07 18:30:09,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.234932
2012-09-07 18:30:10,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.884827
2012-09-07 18:30:10,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.546812
2012-09-07 18:30:11,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.205774
2012-09-07 18:30:11,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.849622
2012-09-07 18:30:12,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.505562
2012-09-07 18:30:12,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.161502
2012-09-07 18:30:13,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.826509
2012-09-07 18:30:13,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.449199
2012-09-07 18:30:14,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 100.000000
2012-09-07 18:30:14,449 DEBUG: install progress dpkg-exec 0.000000
2012-09-07 18:30:14,858 DEBUG: install progress dkms 0.000000
2012-09-07 18:30:14,959 DEBUG: install progress dkms 5.000000
2012-09-07 18:30:15,353 DEBUG: install progress dkms 10.000000
2012-09-07 18:30:15,429 DEBUG: install progress dkms 15.000000
2012-09-07 18:30:15,791 DEBUG: install progress fakeroot 15.000000
2012-09-07 18:30:15,891 DEBUG: install progress fakeroot 20.000000
2012-09-07 18:30:16,404 DEBUG: install progress fakeroot 25.000000
2012-09-07 18:30:16,493 DEBUG: install progress fakeroot 30.000000
2012-09-07 18:30:16,959 DEBUG: install progress fglrx-updates 30.000000
2012-09-07 18:30:17,060 DEBUG: install progress fglrx-updates 35.000000
2012-09-07 18:30:20,225 DEBUG: install progress fglrx-updates 40.000000
2012-09-07 18:30:20,312 DEBUG: install progress fglrx-updates 45.000000
2012-09-07 18:30:20,543 DEBUG: install progress fglrx-amdcccle-updates 45.000000
2012-09-07 18:30:20,644 DEBUG: install progress fglrx-amdcccle-updates 50.000000
2012-09-07 18:30:21,215 DEBUG: install progress fglrx-amdcccle-updates 55.000000
2012-09-07 18:30:21,312 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-09-07 18:30:21,406 DEBUG: install progress man-db 60.000000
2012-09-07 18:30:23,240 DEBUG: install progress ureadahead 60.000000
2012-09-07 18:30:23,630 DEBUG: install progress dpkg-exec 60.000000
2012-09-07 18:30:23,670 DEBUG: install progress dkms 60.000000
2012-09-07 18:30:25,806 DEBUG: install progress dkms 65.000000
2012-09-07 18:30:25,979 DEBUG: install progress dkms 70.000000
2012-09-07 18:30:26,120 DEBUG: install progress fakeroot 70.000000
2012-09-07 18:30:26,222 DEBUG: install progress fakeroot 75.000000
2012-09-07 18:30:26,519 DEBUG: install progress fakeroot 80.000000
2012-09-07 18:30:26,675 DEBUG: install progress fglrx-updates 80.000000
2012-09-07 18:30:27,125 DEBUG: install progress fglrx-updates 85.000000
2012-09-07 18:30:59,667 DEBUG: install progress fglrx-updates 90.000000
2012-09-07 18:31:00,039 DEBUG: install progress bamfdaemon 90.000000
2012-09-07 18:31:00,308 DEBUG: install progress fglrx-amdcccle-updates 90.000000
2012-09-07 18:31:00,410 DEBUG: install progress fglrx-amdcccle-updates 95.000000
2012-09-07 18:31:00,490 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-09-07 18:31:00,558 DEBUG: install progress initramfs-tools 100.000000
2012-09-07 18:31:15,232 DEBUG: install progress libc-bin 100.000000
2012-09-07 18:31:16,637 DEBUG: Selecting previously unselected package dkms.
(Reading database ... 169614 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx-updates (2:8.960-0ubuntu1.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-30-generic-pae
Building for architecture i686
Building initial module for 3.2.0-30-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-30-generic-pae/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-30-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-09-07 18:31:16,875 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-09-07 18:31:40,665 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:40,666 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:31:40,692 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:40,692 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:31:48,728 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:48,728 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:31:48,759 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:48,759 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:31:48,813 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:48,813 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-09-07 18:31:48,880 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:48,880 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:31:48,907 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:48,907 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:31:48,988 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:48,988 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:31:49,015 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:49,015 DEBUG: fglrx_updates is not the alternative in use
2012-09-07 18:31:49,065 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-07 18:31:49,065 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

```

---

### Post by QIII on 2012-09-07
The post release updates package is problematic for many users.  I recommend against it.  

Using the Additional Drivers method of installation does not always work.

There is also the problem of the Intel/ATI hybrid graphics, which is problematic for Linux all around.

For that, please see the ATI driver link in my signature.  A possible solution for the special case of Intel/ATI hybrid graphics by installing ATI's 12.6 driver is given.  Unfortunately it has been found not to work with GPUs other than 6xxx and 7xxx series.

I am not aware of any satisfactory solutions in your case other than disabling either the Intel graphics or the ATI graphics via BIOS settings.

Either that or use the open source driver and vgaswitcheroo.

If you only have ATI graphics, please see the "Using the Ubuntu repository, alternate command line method" section.

---

### Post by amaz1ng on 2012-11-27
For the record, my problem was solved by beelzebub's solution here: [http://ubuntuforums.org/showthread.php?t=2073125](http://ubuntuforums.org/showthread.php?t=2073125)

---

