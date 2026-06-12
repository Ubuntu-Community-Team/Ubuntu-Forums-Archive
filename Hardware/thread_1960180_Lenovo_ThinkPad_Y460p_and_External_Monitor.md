---
title: "Lenovo ThinkPad Y460p and External Monitor"
date: 2012-04-16
forum: Hardware
---

### Post by amaz1ng on 2012-04-16
I'm having an issue with connecting my external monitor to my laptop. The issue is I can only connect the monitor in "mirror" mode and not "extend" mode. This means that on both screens the image is the same, rather than one "extended" desktop.

When I uncheck "mirror mode" and hit apply, I get this message:
> The selected configuration for displays could not be displayed
requested position/size for CRTC 148 is outside the allowed limit: position=(1280, 0), size=(1280, 720), maximum=(1366, 1366)

Some hardware information:

Laptop: **Lenovo IdeaPad Y460p**
Graphics card: AMD Radeon HD 5000M series

[QUOTE] lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Madison [AMD Radeon HD 5000M Series]
[/CODE]

External Monitor: Dell 19 inch, model 1907FPt

Ubuntu version: 11.10
--> installed via CD version 11.04, updated through Update Manager to 11.10. Shouldn't make a difference, but I've had Update Manager break things vs. direct from CD installs in the past.

Drivers
I have used the default open-source ones until I tried updating them to the proprietary drivers today, the **FLGRX** drivers.

In installing the "Post-release update" via "Additional Drivers", I get told to read /var/log/jockey.log . The contents in the next post.

Thanks in advance for any thoughts!

---

### Post by amaz1ng on 2012-04-16
jockey.log contents:

```


2012-04-16 21:49:22,598 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48>
2012-04-16 21:49:24,195 DEBUG: reading modalias file /lib/modules/3.0.0-17-generic/modules.alias
2012-04-16 21:49:24,329 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-16 21:49:24,339 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-16 21:49:24,367 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-04-16 21:49:24,396 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-16 21:49:24,443 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-16 21:49:24,445 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-16 21:49:24,445 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-16 21:49:24,445 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-16 21:49:24,453 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-16 21:49:24,475 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-16 21:49:24,475 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-16 21:49:24,475 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-16 21:49:24,480 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-16 21:49:24,481 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-16 21:49:24,495 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-16 21:49:24,496 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-16 21:49:24,549 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-16 21:49:24,550 DEBUG: Firmware for DVB cards not available
2012-04-16 21:49:24,550 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-16 21:49:24,611 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-16 21:49:24,617 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-16 21:49:24,620 DEBUG: nvidia.available: falling back to default
2012-04-16 21:49:24,702 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 21:49:24,708 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-16 21:49:24,716 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-16 21:49:24,718 DEBUG: nvidia.available: falling back to default
2012-04-16 21:49:24,759 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 21:49:24,764 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-16 21:49:24,769 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-16 21:49:24,770 DEBUG: nvidia.available: falling back to default
2012-04-16 21:49:24,828 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 21:49:24,829 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-04-16 21:49:24,844 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-16 21:49:24,852 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-16 21:49:24,852 DEBUG: nvidia.available: falling back to default
2012-04-16 21:49:24,908 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 21:49:24,910 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-16 21:49:24,913 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-16 21:49:24,914 DEBUG: nvidia.available: falling back to default
2012-04-16 21:49:24,963 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 21:49:24,971 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-16 21:49:24,981 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-16 21:49:24,982 DEBUG: nvidia.available: falling back to default
2012-04-16 21:49:25,014 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 21:49:25,015 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-16 21:49:25,023 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-16 21:49:25,023 DEBUG: fglrx.available: falling back to default
2012-04-16 21:49:25,054 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 21:49:25,057 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-16 21:49:25,061 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-16 21:49:25,061 DEBUG: fglrx.available: falling back to default
2012-04-16 21:49:25,104 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-16 21:49:25,104 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-16 21:49:25,119 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-16 21:49:25,151 DEBUG: Software modem not available
2012-04-16 21:49:25,151 DEBUG: all custom handlers loaded
2012-04-16 21:49:25,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 21:49:25,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 21:49:25,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:25,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 21:49:25,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 21:49:25,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 21:49:25,458 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 21:49:25,458 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,458 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 21:49:25,458 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 21:49:25,472 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 21:49:25,472 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:25,472 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-04-16 21:49:25,475 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 21:49:25,475 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 21:49:25,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 21:49:25,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 21:49:25,475 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-16 21:49:25,475 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,475 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-16 21:49:25,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 21:49:25,476 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:25,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 21:49:25,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 21:49:25,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 21:49:25,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 21:49:25,679 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2012-04-16 21:49:25,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 21:49:25,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 21:49:25,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 21:49:25,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 21:49:25,682 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-16 21:49:25,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:25,682 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-16 21:49:25,709 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:25,710 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:25,682 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 21:49:25,713 DEBUG: fglrx.available: falling back to default
2012-04-16 21:49:25,775 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:25,775 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:25,730 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 21:49:25,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-16 21:49:25,809 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:25,809 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:25,776 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 21:49:25,818 DEBUG: fglrx.available: falling back to default
2012-04-16 21:49:25,893 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:25,894 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:25,839 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 21:49:25,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-16 21:49:25,949 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:25,949 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:49:25,894 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 21:49:25,956 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-16 21:49:25,962 DEBUG: fglrx.available: falling back to default
2012-04-16 21:49:26,032 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:26,033 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:49:25,990 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 21:49:26,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 21:49:26,042 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 21:49:26,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,042 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 21:49:26,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 21:49:26,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 21:49:26,045 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-16 21:49:26,045 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 21:49:26,054 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-04-16 21:49:26,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 21:49:26,073 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-04-16 21:49:26,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-04-16 21:49:26,073 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 21:49:26,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 21:49:26,074 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 21:49:26,074 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 21:49:26,074 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,074 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 21:49:26,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,074 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 21:49:26,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,074 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 21:49:26,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 21:49:26,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 21:49:26,075 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-04-16 21:49:26,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 21:49:26,075 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 21:49:26,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 21:49:26,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 21:49:26,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 21:49:26,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 21:49:26,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 21:49:26,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 21:49:26,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 21:49:26,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-04-16 21:49:26,088 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 21:49:26,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 21:49:26,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 21:49:26,089 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-16 21:49:26,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 21:49:26,091 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-16 21:49:26,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 21:49:26,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-16 21:49:26,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 21:49:26,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 21:49:26,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 21:49:26,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 21:49:26,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 21:49:26,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 21:49:26,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 21:49:26,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 21:49:26,095 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 21:49:26,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 21:49:26,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 21:49:26,096 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,096 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 21:49:26,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 21:49:26,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 21:49:26,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 21:49:26,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 21:49:26,107 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-16 21:49:26,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,107 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-16 21:49:26,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 21:49:26,108 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 21:49:26,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 21:49:26,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-04-16 21:49:26,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 21:49:26,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1220b48> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 21:49:26,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 21:49:26,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 21:49:26,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 21:49:26,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 21:49:26,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 21:49:26,140 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 21:49:26,140 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 21:49:26,140 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 21:49:26,140 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1439f38> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 21:49:26,213 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:26,214 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:26,315 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:26,315 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:49:26,462 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:26,462 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:26,582 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:26,583 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:26,654 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:26,655 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:49:43,138 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:43,139 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:43,806 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:43,806 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:43,943 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:43,943 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:45,453 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:45,453 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:48,205 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-16 21:49:48,284 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-04-16 21:49:48,449 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:48,449 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:48,506 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:48,507 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:54,527 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:54,528 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:54,559 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:54,559 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:54,616 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:54,616 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:49:54,793 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:54,793 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:54,824 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:54,824 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:54,950 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:54,950 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:54,984 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:54,984 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:49:55,051 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:55,052 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:49:56,239 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:56,240 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:49:57,682 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:49:57,682 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:49:57,936 DEBUG: Installing package: fglrx
2012-04-16 21:49:58,327 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-04-16 21:49:58,328 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-04-16 21:49:58,407 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-04-16 21:49:58,489 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-04-16 21:49:58,626 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.002521
2012-04-16 21:49:59,127 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.352569
2012-04-16 21:49:59,628 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.807305
2012-04-16 21:50:00,130 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 1.334013
2012-04-16 21:50:00,631 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 1.455058
2012-04-16 21:50:01,132 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 1.563016
2012-04-16 21:50:01,633 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 1.654618
2012-04-16 21:50:02,135 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 1.772391
2012-04-16 21:50:02,636 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 1.922879
2012-04-16 21:50:03,137 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 2.063553
2012-04-16 21:50:03,638 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 2.217312
2012-04-16 21:50:04,140 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 2.377615
2012-04-16 21:50:04,641 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 2.570632
2012-04-16 21:50:05,142 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 2.770192
2012-04-16 21:50:05,642 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 2.933766
2012-04-16 21:50:06,144 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 3.162770
2012-04-16 21:50:06,645 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 3.372145
2012-04-16 21:50:07,147 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 3.591334
2012-04-16 21:50:07,648 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 3.830152
2012-04-16 21:50:08,149 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 4.052612
2012-04-16 21:50:08,651 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 4.304516
2012-04-16 21:50:09,152 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 4.523706
2012-04-16 21:50:09,653 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 4.677465
2012-04-16 21:50:10,154 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 4.831225
2012-04-16 21:50:10,656 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 4.955541
2012-04-16 21:50:11,157 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 5.138744
2012-04-16 21:50:11,658 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 5.305589
2012-04-16 21:50:12,160 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 5.482249
2012-04-16 21:50:12,661 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 5.701438
2012-04-16 21:50:13,162 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 5.874827
2012-04-16 21:50:13,664 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 6.041672
2012-04-16 21:50:14,165 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 6.241232
2012-04-16 21:50:14,667 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 6.404806
2012-04-16 21:50:15,168 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 6.568380
2012-04-16 21:50:15,669 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 6.712325
2012-04-16 21:50:16,170 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 6.918429
2012-04-16 21:50:16,671 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 7.095089
2012-04-16 21:50:17,172 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 7.265206
2012-04-16 21:50:17,673 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 7.428780
2012-04-16 21:50:18,175 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 7.589082
2012-04-16 21:50:18,676 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 7.798457
2012-04-16 21:50:19,177 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 8.030732
2012-04-16 21:50:19,679 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 8.213935
2012-04-16 21:50:20,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 8.420038
2012-04-16 21:50:20,682 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 8.635956
2012-04-16 21:50:21,183 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 8.845330
2012-04-16 21:50:21,685 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 9.025262
2012-04-16 21:50:22,186 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 9.221550
2012-04-16 21:50:22,687 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 9.444011
2012-04-16 21:50:23,189 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 9.633757
2012-04-16 21:50:23,690 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 9.862760
2012-04-16 21:50:24,191 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 10.095036
2012-04-16 21:50:24,693 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 10.366568
2012-04-16 21:50:25,194 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 10.625015
2012-04-16 21:50:25,695 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 10.939077
2012-04-16 21:50:26,196 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 11.184438
2012-04-16 21:50:26,698 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 11.455971
2012-04-16 21:50:27,199 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 11.688246
2012-04-16 21:50:27,700 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 12.012123
2012-04-16 21:50:28,202 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 12.247669
2012-04-16 21:50:28,703 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 12.466858
2012-04-16 21:50:29,204 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 12.659876
2012-04-16 21:50:29,705 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 12.901965
2012-04-16 21:50:30,207 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 13.130969
2012-04-16 21:50:30,709 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 13.366515
2012-04-16 21:50:31,211 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 13.615148
2012-04-16 21:50:31,712 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 13.876866
2012-04-16 21:50:32,213 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 14.161485
2012-04-16 21:50:32,714 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 14.400303
2012-04-16 21:50:33,216 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 14.665293
2012-04-16 21:50:33,717 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 14.972812
2012-04-16 21:50:34,218 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 15.313046
2012-04-16 21:50:34,720 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 15.676180
2012-04-16 21:50:35,221 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 16.055672
2012-04-16 21:50:35,722 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 16.395905
2012-04-16 21:50:36,223 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 16.732868
2012-04-16 21:50:36,725 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 17.024030
2012-04-16 21:50:37,226 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 17.432965
2012-04-16 21:50:37,728 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 17.828814
2012-04-16 21:50:38,229 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 18.126518
2012-04-16 21:50:38,730 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 18.398051
2012-04-16 21:50:39,231 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 18.649955
2012-04-16 21:50:39,733 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 18.859330
2012-04-16 21:50:40,234 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 19.052347
2012-04-16 21:50:40,735 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 19.278079
2012-04-16 21:50:41,237 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 19.503811
2012-04-16 21:50:41,738 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 19.716457
2012-04-16 21:50:42,240 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 19.935647
2012-04-16 21:50:42,741 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 20.181008
2012-04-16 21:50:43,242 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 20.416554
2012-04-16 21:50:43,744 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 20.573585
2012-04-16 21:50:44,245 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 20.704444
2012-04-16 21:50:44,747 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 20.848389
2012-04-16 21:50:45,248 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 21.011963
2012-04-16 21:50:45,750 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 21.221338
2012-04-16 21:50:46,251 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 21.417627
2012-04-16 21:50:46,752 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 21.627002
2012-04-16 21:50:47,254 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 21.895263
2012-04-16 21:50:47,755 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 22.242040
2012-04-16 21:50:48,257 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 22.703318
2012-04-16 21:50:48,758 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 23.315085
2012-04-16 21:50:49,258 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 23.845065
2012-04-16 21:50:49,759 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 24.293258
2012-04-16 21:50:50,260 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 24.666206
2012-04-16 21:50:50,762 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 25.058784
2012-04-16 21:50:51,263 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 25.428461
2012-04-16 21:50:51,764 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 25.726166
2012-04-16 21:50:52,266 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 25.870111
2012-04-16 21:50:52,767 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 26.066400
2012-04-16 21:50:53,269 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 26.210345
2012-04-16 21:50:53,770 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 26.351018
2012-04-16 21:50:54,271 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 26.494963
2012-04-16 21:50:54,772 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 26.671623
2012-04-16 21:50:55,273 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 26.884269
2012-04-16 21:50:55,775 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 27.077287
2012-04-16 21:50:56,275 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 27.234318
2012-04-16 21:50:56,776 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 27.394620
2012-04-16 21:50:57,277 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 27.584366
2012-04-16 21:50:57,778 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 27.800284
2012-04-16 21:50:58,279 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 27.983487
2012-04-16 21:50:58,780 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 28.186318
2012-04-16 21:50:59,282 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 28.392422
2012-04-16 21:50:59,783 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 28.591982
2012-04-16 21:51:00,285 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 28.820985
2012-04-16 21:51:00,787 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 29.033632
2012-04-16 21:51:01,288 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 29.200477
2012-04-16 21:51:01,789 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 29.409852
2012-04-16 21:51:02,290 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 29.589783
2012-04-16 21:51:02,791 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 29.776258
2012-04-16 21:51:03,293 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 29.962732
2012-04-16 21:51:03,794 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 30.178650
2012-04-16 21:51:04,295 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 30.374938
2012-04-16 21:51:04,797 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 30.633385
2012-04-16 21:51:05,298 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 30.810045
2012-04-16 21:51:05,799 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 30.986705
2012-04-16 21:51:06,300 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 31.153551
2012-04-16 21:51:06,802 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 31.369468
2012-04-16 21:51:07,303 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 31.572300
2012-04-16 21:51:07,805 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 31.762046
2012-04-16 21:51:08,306 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 31.915805
2012-04-16 21:51:08,807 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 32.027036
2012-04-16 21:51:09,309 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 32.164438
2012-04-16 21:51:09,810 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 32.314926
2012-04-16 21:51:10,311 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 32.478500
2012-04-16 21:51:10,813 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 32.697689
2012-04-16 21:51:11,314 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 32.897249
2012-04-16 21:51:11,815 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 33.073909
2012-04-16 21:51:12,316 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 33.224397
2012-04-16 21:51:12,818 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 33.420686
2012-04-16 21:51:13,319 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 33.558088
2012-04-16 21:51:13,820 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 33.751105
2012-04-16 21:51:14,322 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 33.944123
2012-04-16 21:51:14,822 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 34.071710
2012-04-16 21:51:15,323 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 34.254913
2012-04-16 21:51:15,825 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 34.506817
2012-04-16 21:51:16,326 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 34.739092
2012-04-16 21:51:16,827 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 35.007354
2012-04-16 21:51:17,328 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 35.236357
2012-04-16 21:51:17,829 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 35.458818
2012-04-16 21:51:18,331 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 35.592949
2012-04-16 21:51:18,832 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 35.779423
2012-04-16 21:51:19,333 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 35.939725
2012-04-16 21:51:19,834 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 36.090213
2012-04-16 21:51:20,336 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 36.230887
2012-04-16 21:51:20,837 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 36.404275
2012-04-16 21:51:21,338 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 36.571121
2012-04-16 21:51:21,839 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 36.760867
2012-04-16 21:51:22,340 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 36.963699
2012-04-16 21:51:22,842 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 37.143630
2012-04-16 21:51:23,343 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 37.375905
2012-04-16 21:51:23,844 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 37.591823
2012-04-16 21:51:24,345 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 37.811012
2012-04-16 21:51:24,846 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 38.056373
2012-04-16 21:51:25,347 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 38.291919
2012-04-16 21:51:25,848 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 38.599438
2012-04-16 21:51:26,350 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 38.880786
2012-04-16 21:51:26,851 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 39.132690
2012-04-16 21:51:27,353 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 39.463109
2012-04-16 21:51:27,854 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 39.757542
2012-04-16 21:51:28,356 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 40.074876
2012-04-16 21:51:28,856 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 40.323508
2012-04-16 21:51:29,357 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 40.503440
2012-04-16 21:51:29,858 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 40.683371
2012-04-16 21:51:30,360 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 40.876388
2012-04-16 21:51:30,860 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 41.082492
2012-04-16 21:51:31,361 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 41.259151
2012-04-16 21:51:31,863 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 41.416182
2012-04-16 21:51:32,364 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 41.560128
2012-04-16 21:51:32,865 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 41.717159
2012-04-16 21:51:33,366 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 41.923262
2012-04-16 21:51:33,868 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 42.113008
2012-04-16 21:51:34,369 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 42.263496
2012-04-16 21:51:34,870 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 42.410712
2012-04-16 21:51:35,371 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 42.567743
2012-04-16 21:51:35,872 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 42.695331
2012-04-16 21:51:36,373 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 42.858905
2012-04-16 21:51:36,874 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 43.015936
2012-04-16 21:51:37,375 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 43.192596
2012-04-16 21:51:37,877 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 43.415057
2012-04-16 21:51:38,378 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 43.627703
2012-04-16 21:51:38,879 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 43.863249
2012-04-16 21:51:39,381 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 44.121696
2012-04-16 21:51:39,882 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 44.363786
2012-04-16 21:51:40,383 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 44.612418
2012-04-16 21:51:40,884 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 44.779264
2012-04-16 21:51:41,386 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 44.923209
2012-04-16 21:51:41,887 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 45.060611
2012-04-16 21:51:42,388 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 45.214370
2012-04-16 21:51:42,889 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 45.410659
2012-04-16 21:51:43,390 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 45.603676
2012-04-16 21:51:43,892 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 45.822866
2012-04-16 21:51:44,393 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 46.058412
2012-04-16 21:51:44,895 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 46.287416
2012-04-16 21:51:45,396 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 46.506605
2012-04-16 21:51:45,897 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 46.689808
2012-04-16 21:51:46,399 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 46.876282
2012-04-16 21:51:46,900 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 46.922083
2012-04-16 21:51:47,402 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 47.039856
2012-04-16 21:51:47,903 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 47.200159
2012-04-16 21:51:48,405 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 47.409533
2012-04-16 21:51:48,906 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 47.599279
2012-04-16 21:51:49,407 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 47.815197
2012-04-16 21:51:49,909 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 48.054015
2012-04-16 21:51:50,410 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 48.312462
2012-04-16 21:51:50,911 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 48.590537
2012-04-16 21:51:51,414 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 48.881699
2012-04-16 21:51:51,916 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 49.202304
2012-04-16 21:51:52,417 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 49.653768
2012-04-16 21:51:52,918 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 50.134676
2012-04-16 21:51:53,420 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 50.507625
2012-04-16 21:51:53,921 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 50.762800
2012-04-16 21:51:54,423 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 51.034333
2012-04-16 21:51:54,924 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 51.390924
2012-04-16 21:51:55,425 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 51.672271
2012-04-16 21:51:55,927 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 51.940533
2012-04-16 21:51:56,428 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 52.208794
2012-04-16 21:51:56,930 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 52.480327
2012-04-16 21:51:57,431 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 52.647172
2012-04-16 21:51:57,933 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 52.823832
2012-04-16 21:51:58,434 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 52.957963
2012-04-16 21:51:58,935 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 53.105180
2012-04-16 21:51:59,437 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 53.255668
2012-04-16 21:51:59,938 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 53.468314
2012-04-16 21:52:00,439 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 53.658060
2012-04-16 21:52:00,941 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 53.870706
2012-04-16 21:52:01,442 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 54.109524
2012-04-16 21:52:01,944 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 54.351613
2012-04-16 21:52:02,445 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 54.636232
2012-04-16 21:52:02,946 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 54.865236
2012-04-16 21:52:03,448 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 55.081153
2012-04-16 21:52:03,949 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 55.300342
2012-04-16 21:52:04,450 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 55.490088
2012-04-16 21:52:04,961 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 55.696191
2012-04-16 21:52:05,462 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 55.967724
2012-04-16 21:52:05,964 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 56.196728
2012-04-16 21:52:06,465 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 56.429003
2012-04-16 21:52:06,966 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 56.684178
2012-04-16 21:52:07,468 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 56.988426
2012-04-16 21:52:07,969 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 57.299217
2012-04-16 21:52:08,470 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 57.518406
2012-04-16 21:52:08,972 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 57.674021
2012-04-16 21:52:09,473 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 57.845554
2012-04-16 21:52:09,974 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 57.992770
2012-04-16 21:52:10,475 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 58.166159
2012-04-16 21:52:10,977 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 58.355904
2012-04-16 21:52:11,478 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 58.539107
2012-04-16 21:52:11,979 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 58.738668
2012-04-16 21:52:12,481 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 58.944771
2012-04-16 21:52:12,982 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 59.141060
2012-04-16 21:52:13,483 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 59.370063
2012-04-16 21:52:13,985 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 59.582709
2012-04-16 21:52:14,486 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 59.749555
2012-04-16 21:52:14,988 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 60.008002
2012-04-16 21:52:15,489 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 60.250091
2012-04-16 21:52:15,990 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 60.501995
2012-04-16 21:52:16,492 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 60.763714
2012-04-16 21:52:16,993 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 61.051604
2012-04-16 21:52:17,494 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 61.323137
2012-04-16 21:52:17,996 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 61.627384
2012-04-16 21:52:18,498 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 61.967618
2012-04-16 21:52:18,999 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 62.327481
2012-04-16 21:52:19,501 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 62.684072
2012-04-16 21:52:20,002 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 63.017763
2012-04-16 21:52:20,503 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 63.364540
2012-04-16 21:52:21,005 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 63.652430
2012-04-16 21:52:21,506 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 63.923963
2012-04-16 21:52:22,008 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 64.143152
2012-04-16 21:52:22,509 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 64.362341
2012-04-16 21:52:23,011 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 64.574987
2012-04-16 21:52:23,512 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 64.800720
2012-04-16 21:52:24,013 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 65.036266
2012-04-16 21:52:24,515 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 65.294713
2012-04-16 21:52:25,016 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 65.540074
2012-04-16 21:52:25,518 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 65.765806
2012-04-16 21:52:26,019 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 66.011167
2012-04-16 21:52:26,520 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 66.249985
2012-04-16 21:52:27,022 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 66.485532
2012-04-16 21:52:27,523 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 66.734164
2012-04-16 21:52:28,024 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 67.022054
2012-04-16 21:52:28,526 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 67.267415
2012-04-16 21:52:29,027 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 67.496419
2012-04-16 21:52:29,528 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 67.731965
2012-04-16 21:52:30,030 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 68.010041
2012-04-16 21:52:30,531 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 68.252131
2012-04-16 21:52:31,032 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 68.536749
2012-04-16 21:52:31,533 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 68.844268
2012-04-16 21:52:32,035 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 69.096172
2012-04-16 21:52:32,536 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 69.344805
2012-04-16 21:52:33,037 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 69.567265
2012-04-16 21:52:33,539 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 69.802812
2012-04-16 21:52:34,040 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 70.071073
2012-04-16 21:52:34,541 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 70.385135
2012-04-16 21:52:35,042 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 70.689383
2012-04-16 21:52:35,544 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 70.983816
2012-04-16 21:52:36,045 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 71.261892
2012-04-16 21:52:36,547 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 71.507253
2012-04-16 21:52:37,048 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 71.723171
2012-04-16 21:52:37,549 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 71.971803
2012-04-16 21:52:38,051 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 72.207350
2012-04-16 21:52:38,552 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 72.436353
2012-04-16 21:52:39,054 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 72.642456
2012-04-16 21:52:39,555 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 72.861646
2012-04-16 21:52:40,056 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 73.097192
2012-04-16 21:52:40,558 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 73.349096
2012-04-16 21:52:41,059 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 73.617357
2012-04-16 21:52:41,560 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 73.934691
2012-04-16 21:52:42,061 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 74.235667
2012-04-16 21:52:42,563 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 74.490842
2012-04-16 21:52:43,064 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 74.827805
2012-04-16 21:52:43,565 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 75.033908
2012-04-16 21:52:44,067 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 75.240011
2012-04-16 21:52:44,568 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 75.491915
2012-04-16 21:52:45,070 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 75.717647
2012-04-16 21:52:45,571 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 76.041524
2012-04-16 21:52:46,072 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 76.290156
2012-04-16 21:52:46,574 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 76.535517
2012-04-16 21:52:47,075 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 76.797236
2012-04-16 21:52:47,576 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 77.055683
2012-04-16 21:52:48,078 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 77.219257
2012-04-16 21:52:48,579 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 77.376288
2012-04-16 21:52:49,081 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 77.575848
2012-04-16 21:52:49,582 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 77.719793
2012-04-16 21:52:50,083 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 77.893181
2012-04-16 21:52:50,585 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 78.073113
2012-04-16 21:52:51,086 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 78.282487
2012-04-16 21:52:51,587 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 78.485319
2012-04-16 21:52:52,089 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 78.697965
2012-04-16 21:52:52,590 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 78.913883
2012-04-16 21:52:53,091 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 79.123258
2012-04-16 21:52:53,593 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 79.299918
2012-04-16 21:52:54,094 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 79.453677
2012-04-16 21:52:54,595 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 79.659780
2012-04-16 21:52:55,096 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 79.875698
2012-04-16 21:52:55,597 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 80.091616
2012-04-16 21:52:56,099 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 80.343520
2012-04-16 21:52:56,600 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 80.569252
2012-04-16 21:52:57,102 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 80.808070
2012-04-16 21:52:57,603 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 81.040345
2012-04-16 21:52:58,104 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 81.246448
2012-04-16 21:52:58,606 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 81.449280
2012-04-16 21:52:59,107 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 81.652112
2012-04-16 21:52:59,608 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 81.864758
2012-04-16 21:53:00,110 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 82.113390
2012-04-16 21:53:00,611 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 82.345665
2012-04-16 21:53:01,112 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 82.653184
2012-04-16 21:53:01,614 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 82.898545
2012-04-16 21:53:02,115 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 83.075205
2012-04-16 21:53:02,618 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 83.242051
2012-04-16 21:53:03,119 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 83.454697
2012-04-16 21:53:03,621 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 83.657529
2012-04-16 21:53:04,122 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 83.883261
2012-04-16 21:53:04,623 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 84.102450
2012-04-16 21:53:05,124 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 84.324911
2012-04-16 21:53:05,626 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 84.514656
2012-04-16 21:53:06,127 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 84.694588
2012-04-16 21:53:06,628 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 84.861433
2012-04-16 21:53:07,129 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 85.093708
2012-04-16 21:53:07,631 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 85.296540
2012-04-16 21:53:08,132 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 85.499372
2012-04-16 21:53:08,634 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 85.738190
2012-04-16 21:53:09,135 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 85.996637
2012-04-16 21:53:09,636 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 86.245269
2012-04-16 21:53:10,138 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 86.493902
2012-04-16 21:53:10,226 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 86.541192
2012-04-16 21:53:10,227 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 86.561861
2012-04-16 21:53:10,728 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 86.725435
2012-04-16 21:53:11,230 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 86.892281
2012-04-16 21:53:11,730 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 87.104927
2012-04-16 21:53:12,232 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 87.304487
2012-04-16 21:53:12,733 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 87.507319
2012-04-16 21:53:13,235 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 87.755951
2012-04-16 21:53:13,736 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 88.011127
2012-04-16 21:53:14,237 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 88.295746
2012-04-16 21:53:14,739 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 88.583636
2012-04-16 21:53:15,240 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 88.933684
2012-04-16 21:53:15,741 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 89.336076
2012-04-16 21:53:16,243 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 89.895499
2012-04-16 21:53:16,744 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 90.379678
2012-04-16 21:53:17,245 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 90.808242
2012-04-16 21:53:17,747 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 91.164833
2012-04-16 21:53:18,248 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 91.442909
2012-04-16 21:53:18,749 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 91.740614
2012-04-16 21:53:19,252 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 92.048133
2012-04-16 21:53:19,753 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 92.411267
2012-04-16 21:53:20,255 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 92.748230
2012-04-16 21:53:20,756 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 93.144079
2012-04-16 21:53:21,258 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 93.428697
2012-04-16 21:53:21,759 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 93.674058
2012-04-16 21:53:22,261 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 93.883433
2012-04-16 21:53:22,762 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 94.092808
2012-04-16 21:53:23,264 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 94.354526
2012-04-16 21:53:23,766 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 94.629330
2012-04-16 21:53:24,268 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 94.910678
2012-04-16 21:53:24,769 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 95.172396
2012-04-16 21:53:25,270 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 95.450472
2012-04-16 21:53:25,772 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 95.748176
2012-04-16 21:53:26,273 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 96.029524
2012-04-16 21:53:26,774 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 96.337043
2012-04-16 21:53:27,276 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 96.647833
2012-04-16 21:53:27,777 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 96.958624
2012-04-16 21:53:28,278 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 97.220342
2012-04-16 21:53:28,779 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 97.449346
2012-04-16 21:53:29,281 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 97.668535
2012-04-16 21:53:29,782 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 97.900810
2012-04-16 21:53:30,283 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 98.139628
2012-04-16 21:53:30,785 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 98.391532
2012-04-16 21:53:31,286 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 98.712137
2012-04-16 21:53:31,787 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 98.947684
2012-04-16 21:53:32,289 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 99.173416
2012-04-16 21:53:32,790 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 99.412234
2012-04-16 21:53:33,292 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 99.608522
2012-04-16 21:53:33,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 99.814626
2012-04-16 21:53:34,225 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 100.000000
2012-04-16 21:53:34,440 DEBUG: install progress dpkg-exec 0.000000
2012-04-16 21:53:34,746 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2012-04-16 21:53:34,833 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2012-04-16 21:53:34,834 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2012-04-16 21:53:35,072 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2012-04-16 21:53:35,543 DEBUG: install progress fglrx-updates 18.750000
2012-04-16 21:53:35,543 DEBUG: install progress fglrx-updates 25.000000
2012-04-16 21:54:07,764 DEBUG: install progress fglrx-updates 31.250000
2012-04-16 21:54:08,729 DEBUG: install progress fglrx-updates 37.500000
2012-04-16 21:54:08,909 DEBUG: install progress bamfdaemon 37.500000
2012-04-16 21:54:09,112 DEBUG: install progress gnome-menus 37.500000
2012-04-16 21:54:09,304 DEBUG: install progress ureadahead 37.500000
2012-04-16 21:54:09,472 DEBUG: install progress initramfs-tools 37.500000
2012-04-16 21:54:21,224 DEBUG: install progress libc-bin 37.500000
2012-04-16 21:54:21,642 DEBUG: install progress dpkg-exec 37.500000
2012-04-16 21:54:22,183 DEBUG: install progress fglrx 37.500000
2012-04-16 21:54:22,183 DEBUG: install progress fglrx 43.750000
2012-04-16 21:54:25,679 DEBUG: install progress fglrx 50.000000
2012-04-16 21:54:25,758 DEBUG: install progress fglrx 56.250000
2012-04-16 21:54:25,991 DEBUG: install progress fglrx-amdcccle 56.250000
2012-04-16 21:54:26,092 DEBUG: install progress fglrx-amdcccle 62.500000
2012-04-16 21:54:26,606 DEBUG: install progress fglrx-amdcccle 68.750000
2012-04-16 21:54:26,691 DEBUG: install progress fglrx-amdcccle 75.000000
2012-04-16 21:54:26,776 DEBUG: install progress ureadahead 75.000000
2012-04-16 21:54:27,146 DEBUG: install progress dpkg-exec 75.000000
2012-04-16 21:54:27,180 DEBUG: install progress fglrx 75.000000
2012-04-16 21:54:27,539 DEBUG: install progress fglrx 81.250000
2012-04-16 21:54:47,249 DEBUG: install progress fglrx 87.500000
2012-04-16 21:54:47,734 DEBUG: install progress bamfdaemon 87.500000
2012-04-16 21:54:47,892 DEBUG: install progress gnome-menus 87.500000
2012-04-16 21:54:48,106 DEBUG: install progress fglrx-amdcccle 87.500000
2012-04-16 21:54:48,186 DEBUG: install progress fglrx-amdcccle 93.750000
2012-04-16 21:54:48,254 DEBUG: install progress fglrx-amdcccle 100.000000
2012-04-16 21:54:48,333 DEBUG: install progress initramfs-tools 100.000000
2012-04-16 21:54:59,203 DEBUG: install progress libc-bin 100.000000
2012-04-16 21:55:01,610 DEBUG: (Reading database ... 198266 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx.
(Reading database ... 198006 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.881 DKMS files...
Building only for 3.0.0-17-generic
Building for architecture x86_64
Building initial module for 3.0.0-17-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-17-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-04-16 21:55:01,816 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:00.0
2012-04-16 21:55:19,355 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:19,356 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:55:19,462 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:19,462 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:55:19,634 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:19,634 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:55:19,681 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:19,681 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:55:19,769 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:19,769 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:55:19,874 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:19,875 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:55:20,016 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:20,016 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:55:20,146 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:20,147 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:55:20,303 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:20,304 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:55:20,346 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:20,346 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 21:55:20,404 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:20,404 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:55:20,523 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 21:55:20,523 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 21:55:31,809 DEBUG: Shutting down
2012-04-16 22:06:43,515 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48>
2012-04-16 22:06:45,211 DEBUG: reading modalias file /lib/modules/3.0.0-17-generic/modules.alias
2012-04-16 22:06:45,323 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-16 22:06:45,332 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-16 22:06:45,371 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-04-16 22:06:45,390 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-16 22:06:45,438 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-16 22:06:45,439 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-16 22:06:45,439 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-16 22:06:45,439 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-16 22:06:45,449 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-16 22:06:45,486 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-16 22:06:45,487 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-16 22:06:45,487 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-16 22:06:45,495 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-16 22:06:45,496 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-16 22:06:45,530 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-16 22:06:45,530 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-16 22:06:45,573 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-16 22:06:45,574 DEBUG: Firmware for DVB cards not available
2012-04-16 22:06:45,575 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-16 22:06:45,637 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-16 22:06:45,645 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-16 22:06:45,646 DEBUG: nvidia.available: falling back to default
2012-04-16 22:06:45,779 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:06:45,782 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-16 22:06:45,786 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-16 22:06:45,786 DEBUG: nvidia.available: falling back to default
2012-04-16 22:06:45,833 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:06:45,842 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-16 22:06:45,850 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-16 22:06:45,850 DEBUG: nvidia.available: falling back to default
2012-04-16 22:06:45,892 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:06:45,892 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-04-16 22:06:45,917 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-16 22:06:45,925 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-16 22:06:45,927 DEBUG: nvidia.available: falling back to default
2012-04-16 22:06:46,013 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:06:46,016 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-16 22:06:46,023 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-16 22:06:46,024 DEBUG: nvidia.available: falling back to default
2012-04-16 22:06:46,082 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:06:46,090 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-16 22:06:46,101 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-16 22:06:46,103 DEBUG: nvidia.available: falling back to default
2012-04-16 22:06:46,162 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:06:46,163 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-16 22:06:46,168 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-16 22:06:46,176 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-16 22:06:46,176 DEBUG: fglrx.available: falling back to default
2012-04-16 22:06:46,223 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:06:46,236 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-16 22:06:46,236 DEBUG: fglrx.available: falling back to default
2012-04-16 22:06:46,281 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-16 22:06:46,281 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-16 22:06:46,311 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-16 22:06:46,330 DEBUG: Software modem not available
2012-04-16 22:06:46,331 DEBUG: all custom handlers loaded
2012-04-16 22:06:46,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 22:06:46,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 22:06:46,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:46,465 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:46,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 22:06:46,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 22:06:46,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 22:06:46,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:06:46,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:46,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 22:06:46,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 22:06:46,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 22:06:46,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:46,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:46,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 22:06:46,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 22:06:46,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 22:06:46,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 22:06:46,742 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-16 22:06:46,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:46,742 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-16 22:06:46,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:46,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 22:06:46,743 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:46,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:46,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 22:06:46,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 22:06:46,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 22:06:46,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 22:06:46,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2012-04-16 22:06:46,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:46,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:06:46,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 22:06:46,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 22:06:46,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 22:06:46,946 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-16 22:06:46,947 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:46,947 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-04-16 22:06:47,585 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:47,585 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:46,947 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 22:06:47,722 DEBUG: fglrx.available: falling back to default
2012-04-16 22:06:47,780 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:47,780 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:47,750 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 22:06:47,856 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-16 22:06:47,891 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:47,891 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:47,857 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:06:47,895 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-16 22:06:47,899 DEBUG: fglrx.available: falling back to default
2012-04-16 22:06:47,978 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:47,979 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:47,922 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:06:47,979 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-16 22:06:48,029 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:48,030 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:47,979 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 22:06:48,115 DEBUG: fglrx.available: falling back to default
2012-04-16 22:06:48,185 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:48,185 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:48,140 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 22:06:48,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 22:06:48,269 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:06:48,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,270 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:06:48,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 22:06:48,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 22:06:48,278 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-16 22:06:48,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 22:06:48,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-04-16 22:06:48,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-04-16 22:06:48,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:06:48,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 22:06:48,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-04-16 22:06:48,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 22:06:48,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 22:06:48,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 22:06:48,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:06:48,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:06:48,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:06:48,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 22:06:48,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 22:06:48,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-04-16 22:06:48,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 22:06:48,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,286 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 22:06:48,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 22:06:48,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 22:06:48,298 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 22:06:48,298 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,299 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 22:06:48,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 22:06:48,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 22:06:48,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 22:06:48,299 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 22:06:48,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 22:06:48,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-04-16 22:06:48,300 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:06:48,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 22:06:48,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-16 22:06:48,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 22:06:48,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-16 22:06:48,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 22:06:48,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 22:06:48,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:06:48,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 22:06:48,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 22:06:48,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 22:06:48,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-16 22:06:48,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 22:06:48,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 22:06:48,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 22:06:48,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-04-16 22:06:48,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:06:48,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 22:06:48,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 22:06:48,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:06:48,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:06:48,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 22:06:48,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 22:06:48,318 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-16 22:06:48,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,318 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-16 22:06:48,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 22:06:48,318 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:06:48,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 22:06:48,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-04-16 22:06:48,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x196ab48> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 22:06:48,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 22:06:48,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 22:06:48,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 22:06:48,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b85488> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 22:06:48,493 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:48,493 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:48,532 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:48,533 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:48,573 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:48,573 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:48,625 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:48,625 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:48,800 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:48,800 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:48,999 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,000 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:49,262 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,263 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:49,311 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,312 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:49,359 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,359 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:49,475 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,475 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:49,521 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,522 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:49,553 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,553 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:49,615 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,616 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:49,791 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,791 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:49,989 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:49,989 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:06:53,552 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:53,552 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:55,635 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:06:55,635 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:06:58,131 DEBUG: Installing package: fglrx-updates
2012-04-16 22:06:58,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2012-04-16 22:06:58,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2012-04-16 22:06:58,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2012-04-16 22:06:58,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2012-04-16 22:06:58,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.001743
2012-04-16 22:06:59,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.175905
2012-04-16 22:06:59,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.433755
2012-04-16 22:07:00,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.662201
2012-04-16 22:07:00,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.854458
2012-04-16 22:07:01,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.073856
2012-04-16 22:07:01,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.300041
2012-04-16 22:07:02,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.533011
2012-04-16 22:07:02,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.727529
2012-04-16 22:07:03,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.903953
2012-04-16 22:07:03,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.105257
2012-04-16 22:07:04,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.315608
2012-04-16 22:07:04,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.528222
2012-04-16 22:07:05,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.727264
2012-04-16 22:07:05,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.858451
2012-04-16 22:07:06,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.007732
2012-04-16 22:07:06,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.157014
2012-04-16 22:07:07,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.308558
2012-04-16 22:07:08,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.489505
2012-04-16 22:07:08,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.681762
2012-04-16 22:07:09,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.874018
2012-04-16 22:07:09,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.070799
2012-04-16 22:07:10,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.294721
2012-04-16 22:07:10,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.541262
2012-04-16 22:07:11,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.880539
2012-04-16 22:07:11,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.194935
2012-04-16 22:07:12,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.597543
2012-04-16 22:07:12,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.839560
2012-04-16 22:07:13,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.185622
2012-04-16 22:07:13,518 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.506804
2012-04-16 22:07:14,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.773701
2012-04-16 22:07:14,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.083574
2012-04-16 22:07:15,022 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.348210
2012-04-16 22:07:15,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.574394
2012-04-16 22:07:16,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.775698
2012-04-16 22:07:16,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.986049
2012-04-16 22:07:17,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.169259
2012-04-16 22:07:17,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.334373
2012-04-16 22:07:18,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.490441
2012-04-16 22:07:18,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.678173
2012-04-16 22:07:19,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.877216
2012-04-16 22:07:19,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.076258
2012-04-16 22:07:20,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.243634
2012-04-16 22:07:20,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.429105
2012-04-16 22:07:21,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.646242
2012-04-16 22:07:21,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.870165
2012-04-16 22:07:22,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.105397
2012-04-16 22:07:22,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.331581
2012-04-16 22:07:23,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.564551
2012-04-16 22:07:23,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.768117
2012-04-16 22:07:24,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.016919
2012-04-16 22:07:24,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.229533
2012-04-16 22:07:25,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.457979
2012-04-16 22:07:25,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.709043
2012-04-16 22:07:26,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.955584
2012-04-16 22:07:26,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.224744
2012-04-16 22:07:27,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.473547
2012-04-16 22:07:27,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.760801
2012-04-16 22:07:28,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.045793
2012-04-16 22:07:28,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.326261
2012-04-16 22:07:29,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.629348
2012-04-16 22:07:29,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.900770
2012-04-16 22:07:30,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.185762
2012-04-16 22:07:30,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.391590
2012-04-16 22:07:31,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.586108
2012-04-16 22:07:31,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.782889
2012-04-16 22:07:32,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.997764
2012-04-16 22:07:32,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.178711
2012-04-16 22:07:33,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.332516
2012-04-16 22:07:33,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.495369
2012-04-16 22:07:34,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.646913
2012-04-16 22:07:34,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.823336
2012-04-16 22:07:35,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.979404
2012-04-16 22:07:35,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.130947
2012-04-16 22:07:36,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.287014
2012-04-16 22:07:36,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.438558
2012-04-16 22:07:37,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.583316
2012-04-16 22:07:37,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.721288
2012-04-16 22:07:38,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.850213
2012-04-16 22:07:38,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.004019
2012-04-16 22:07:39,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.148777
2012-04-16 22:07:39,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.282225
2012-04-16 22:07:40,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.456387
2012-04-16 22:07:40,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.594360
2012-04-16 22:07:41,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.725547
2012-04-16 22:07:41,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.861257
2012-04-16 22:07:42,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.972088
2012-04-16 22:07:42,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.076132
2012-04-16 22:07:43,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.193748
2012-04-16 22:07:43,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.320411
2012-04-16 22:07:44,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.476479
2012-04-16 22:07:44,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.623498
2012-04-16 22:07:45,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.802184
2012-04-16 22:07:45,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.974084
2012-04-16 22:07:46,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.148246
2012-04-16 22:07:46,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.331455
2012-04-16 22:07:47,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.535021
2012-04-16 22:07:47,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.734063
2012-04-16 22:07:48,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.894654
2012-04-16 22:07:48,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.062031
2012-04-16 22:07:49,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.229407
2012-04-16 22:07:49,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.401307
2012-04-16 22:07:50,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.622968
2012-04-16 22:07:50,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.772250
2012-04-16 22:07:51,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.953197
2012-04-16 22:07:51,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.077598
2012-04-16 22:07:52,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.233666
2012-04-16 22:07:52,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.373900
2012-04-16 22:07:53,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.514134
2012-04-16 22:07:53,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.647583
2012-04-16 22:07:54,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.760675
2012-04-16 22:07:54,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.896386
2012-04-16 22:07:55,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.032096
2012-04-16 22:07:55,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.176854
2012-04-16 22:07:56,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.317088
2012-04-16 22:07:56,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.484465
2012-04-16 22:07:57,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.645056
2012-04-16 22:07:57,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.837312
2012-04-16 22:07:58,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.029569
2012-04-16 22:07:58,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.230873
2012-04-16 22:07:59,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.454796
2012-04-16 22:07:59,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.696813
2012-04-16 22:08:00,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.011209
2012-04-16 22:08:00,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.336915
2012-04-16 22:08:01,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.583455
2012-04-16 22:08:01,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.750832
2012-04-16 22:08:02,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.904637
2012-04-16 22:08:02,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.019991
2012-04-16 22:08:03,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.146654
2012-04-16 22:08:03,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.284627
2012-04-16 22:08:04,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.422599
2012-04-16 22:08:04,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.605809
2012-04-16 22:08:05,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.779971
2012-04-16 22:08:05,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.969965
2012-04-16 22:08:06,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.157698
2012-04-16 22:08:06,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.379359
2012-04-16 22:08:07,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.675660
2012-04-16 22:08:07,731 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.069221
2012-04-16 22:08:08,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.406236
2012-04-16 22:08:08,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.761345
2012-04-16 22:08:09,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.109669
2012-04-16 22:08:09,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.367519
2012-04-16 22:08:10,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.591442
2012-04-16 22:08:10,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.878696
2012-04-16 22:08:11,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.059643
2012-04-16 22:08:11,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.245114
2012-04-16 22:08:12,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.421538
2012-04-16 22:08:12,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.609271
2012-04-16 22:08:13,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.815099
2012-04-16 22:08:13,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.025450
2012-04-16 22:08:14,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.224493
2012-04-16 22:08:14,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.407702
2012-04-16 22:08:15,254 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.622577
2012-04-16 22:08:15,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.835190
2012-04-16 22:08:16,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.018400
2012-04-16 22:08:16,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.226489
2012-04-16 22:08:17,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.418746
2012-04-16 22:08:17,761 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.622312
2012-04-16 22:08:18,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.814568
2012-04-16 22:08:18,764 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.038491
2012-04-16 22:08:19,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.219438
2012-04-16 22:08:19,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.395862
2012-04-16 22:08:20,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.572286
2012-04-16 22:08:20,769 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.723829
2012-04-16 22:08:21,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.832398
2012-04-16 22:08:21,772 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.943228
2012-04-16 22:08:22,273 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.085724
2012-04-16 22:08:22,775 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.248577
2012-04-16 22:08:23,276 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.391073
2012-04-16 22:08:23,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.569759
2012-04-16 22:08:24,279 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.755230
2012-04-16 22:08:24,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.976891
2012-04-16 22:08:25,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.178195
2012-04-16 22:08:25,783 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.404379
2012-04-16 22:08:26,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.664491
2012-04-16 22:08:26,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.021862
2012-04-16 22:08:27,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.245785
2012-04-16 22:08:27,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.571490
2012-04-16 22:08:28,290 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.849697
2012-04-16 22:08:28,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.026121
2012-04-16 22:08:29,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.209330
2012-04-16 22:08:29,794 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.351826
2012-04-16 22:08:30,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.487537
2012-04-16 22:08:30,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.650389
2012-04-16 22:08:31,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.824551
2012-04-16 22:08:31,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.028117
2012-04-16 22:08:32,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.200017
2012-04-16 22:08:32,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.362870
2012-04-16 22:08:33,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.500842
2012-04-16 22:08:33,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.652386
2012-04-16 22:08:34,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.840119
2012-04-16 22:08:34,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.005233
2012-04-16 22:08:35,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.220109
2012-04-16 22:08:35,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.401056
2012-04-16 22:08:36,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.579742
2012-04-16 22:08:36,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.740333
2012-04-16 22:08:37,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.941637
2012-04-16 22:08:37,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.102227
2012-04-16 22:08:38,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.249247
2012-04-16 22:08:38,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.400791
2012-04-16 22:08:39,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.577215
2012-04-16 22:08:39,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.762686
2012-04-16 22:08:40,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.950419
2012-04-16 22:08:40,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.133628
2012-04-16 22:08:41,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.332670
2012-04-16 22:08:41,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.531712
2012-04-16 22:08:42,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.699089
2012-04-16 22:08:42,827 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.911702
2012-04-16 22:08:43,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.117530
2012-04-16 22:08:43,830 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.314310
2012-04-16 22:08:44,331 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.463592
2012-04-16 22:08:44,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.597041
2012-04-16 22:08:45,334 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.739537
2012-04-16 22:08:45,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.906913
2012-04-16 22:08:46,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.081075
2012-04-16 22:08:46,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.271070
2012-04-16 22:08:47,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.483683
2012-04-16 22:08:47,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.687249
2012-04-16 22:08:48,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.908910
2012-04-16 22:08:48,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.169022
2012-04-16 22:08:49,345 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.417824
2012-04-16 22:08:49,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.729959
2012-04-16 22:08:50,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.023998
2012-04-16 22:08:50,849 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.315776
2012-04-16 22:08:51,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.634696
2012-04-16 22:08:51,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.940045
2012-04-16 22:08:52,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.220514
2012-04-16 22:08:52,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.510029
2012-04-16 22:08:53,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.702286
2012-04-16 22:08:53,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.937518
2012-04-16 22:08:54,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.080014
2012-04-16 22:08:54,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.197630
2012-04-16 22:08:55,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.344650
2012-04-16 22:08:55,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.460004
2012-04-16 22:08:56,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.595714
2012-04-16 22:08:56,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.760829
2012-04-16 22:08:57,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.903325
2012-04-16 22:08:57,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.068439
2012-04-16 22:08:58,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.224507
2012-04-16 22:08:58,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.373788
2012-04-16 22:08:59,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.552474
2012-04-16 22:08:59,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.722112
2012-04-16 22:09:00,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.882703
2012-04-16 22:09:00,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.086269
2012-04-16 22:09:01,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.271740
2012-04-16 22:09:01,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.452688
2012-04-16 22:09:02,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.699228
2012-04-16 22:09:02,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.900533
2012-04-16 22:09:03,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.131241
2012-04-16 22:09:03,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.346116
2012-04-16 22:09:04,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.574562
2012-04-16 22:09:04,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.800746
2012-04-16 22:09:05,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.051811
2012-04-16 22:09:05,888 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.296090
2012-04-16 22:09:06,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.562987
2012-04-16 22:09:06,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.802743
2012-04-16 22:09:07,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.062855
2012-04-16 22:09:07,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.279992
2012-04-16 22:09:08,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.519747
2012-04-16 22:09:08,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.707480
2012-04-16 22:09:09,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.926879
2012-04-16 22:09:09,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.157587
2012-04-16 22:09:10,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.356629
2012-04-16 22:09:10,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.612217
2012-04-16 22:09:11,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.863282
2012-04-16 22:09:11,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.125656
2012-04-16 22:09:12,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.412910
2012-04-16 22:09:12,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.650403
2012-04-16 22:09:13,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.899206
2012-04-16 22:09:13,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.177413
2012-04-16 22:09:14,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.385502
2012-04-16 22:09:14,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.629782
2012-04-16 22:09:15,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.826562
2012-04-16 22:09:15,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.045961
2012-04-16 22:09:16,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.265360
2012-04-16 22:09:16,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.444045
2012-04-16 22:09:17,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.604636
2012-04-16 22:09:17,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.749394
2012-04-16 22:09:18,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.876057
2012-04-16 22:09:18,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.038910
2012-04-16 22:09:19,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.129384
2012-04-16 22:09:19,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.303546
2012-04-16 22:09:20,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.441518
2012-04-16 22:09:20,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.584014
2012-04-16 22:09:21,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.717463
2012-04-16 22:09:21,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.871268
2012-04-16 22:09:22,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.054478
2012-04-16 22:09:22,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.260305
2012-04-16 22:09:23,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.420896
2012-04-16 22:09:23,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.606367
2012-04-16 22:09:24,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.755649
2012-04-16 22:09:24,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.884574
2012-04-16 22:09:25,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.027070
2012-04-16 22:09:25,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.169566
2012-04-16 22:09:26,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.323372
2012-04-16 22:09:26,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.490748
2012-04-16 22:09:27,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.676219
2012-04-16 22:09:27,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.884309
2012-04-16 22:09:28,447 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.085613
2012-04-16 22:09:28,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.332154
2012-04-16 22:09:29,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.551553
2012-04-16 22:09:29,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.757380
2012-04-16 22:09:30,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.972255
2012-04-16 22:09:30,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.248200
2012-04-16 22:09:31,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.490217
2012-04-16 22:09:31,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.725449
2012-04-16 22:09:32,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.958419
2012-04-16 22:09:32,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.191389
2012-04-16 22:09:33,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.404002
2012-04-16 22:09:33,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.560069
2012-04-16 22:09:34,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.688994
2012-04-16 22:09:34,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.831491
2012-04-16 22:09:35,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.960416
2012-04-16 22:09:35,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.105174
2012-04-16 22:09:36,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.252193
2012-04-16 22:09:36,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.421832
2012-04-16 22:09:37,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.586946
2012-04-16 22:09:37,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.722657
2012-04-16 22:09:38,482 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.810869
2012-04-16 22:09:38,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.948841
2012-04-16 22:09:39,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.093599
2012-04-16 22:09:39,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.251928
2012-04-16 22:09:40,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.383115
2012-04-16 22:09:40,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.532397
2012-04-16 22:09:41,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.720130
2012-04-16 22:09:41,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.919172
2012-04-16 22:09:42,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.118214
2012-04-16 22:09:42,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.335351
2012-04-16 22:09:43,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.550226
2012-04-16 22:09:43,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.812600
2012-04-16 22:09:44,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.126996
2012-04-16 22:09:44,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.445916
2012-04-16 22:09:45,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.785193
2012-04-16 22:09:46,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.997806
2012-04-16 22:09:46,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.285060
2012-04-16 22:09:47,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.527077
2012-04-16 22:09:47,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.762309
2012-04-16 22:09:48,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.986231
2012-04-16 22:09:48,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.203368
2012-04-16 22:09:49,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.386578
2012-04-16 22:09:49,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.565263
2012-04-16 22:09:50,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.759782
2012-04-16 22:09:50,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.963348
2012-04-16 22:09:51,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.189532
2012-04-16 22:09:51,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.406669
2012-04-16 22:09:52,018 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.635115
2012-04-16 22:09:52,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.892965
2012-04-16 22:09:53,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.112364
2012-04-16 22:09:53,522 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.329501
2012-04-16 22:09:54,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.562471
2012-04-16 22:09:54,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.795441
2012-04-16 22:09:55,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.037458
2012-04-16 22:09:55,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.279475
2012-04-16 22:09:56,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.519231
2012-04-16 22:09:56,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.768033
2012-04-16 22:09:57,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.028145
2012-04-16 22:09:57,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.247544
2012-04-16 22:09:58,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.471467
2012-04-16 22:09:58,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.699913
2012-04-16 22:09:59,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.944192
2012-04-16 22:09:59,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.172638
2012-04-16 22:10:00,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.371680
2012-04-16 22:10:00,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.568461
2012-04-16 22:10:01,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.778812
2012-04-16 22:10:01,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.966545
2012-04-16 22:10:02,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.226657
2012-04-16 22:10:02,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.457365
2012-04-16 22:10:03,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.701644
2012-04-16 22:10:03,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.943661
2012-04-16 22:10:04,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.160798
2012-04-16 22:10:04,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.398292
2012-04-16 22:10:05,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.669713
2012-04-16 22:10:05,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.927563
2012-04-16 22:10:06,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.158271
2012-04-16 22:10:06,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.418383
2012-04-16 22:10:07,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.671710
2012-04-16 22:10:07,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.900156
2012-04-16 22:10:08,061 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.182886
2012-04-16 22:10:08,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.424903
2012-04-16 22:10:09,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.666921
2012-04-16 22:10:09,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.893105
2012-04-16 22:10:10,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.162264
2012-04-16 22:10:10,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.454042
2012-04-16 22:10:11,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.693797
2012-04-16 22:10:11,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.922244
2012-04-16 22:10:12,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.159737
2012-04-16 22:10:12,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.446991
2012-04-16 22:10:13,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.734245
2012-04-16 22:10:13,576 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.032809
2012-04-16 22:10:14,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.249946
2012-04-16 22:10:14,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.503272
2012-04-16 22:10:15,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.720409
2012-04-16 22:10:15,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.908142
2012-04-16 22:10:16,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.100399
2012-04-16 22:10:16,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.328845
2012-04-16 22:10:17,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.539196
2012-04-16 22:10:17,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.754071
2012-04-16 22:10:18,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.002874
2012-04-16 22:10:18,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.251677
2012-04-16 22:10:19,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.534407
2012-04-16 22:10:19,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.733450
2012-04-16 22:10:20,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.011656
2012-04-16 22:10:20,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.242364
2012-04-16 22:10:21,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.518309
2012-04-16 22:10:21,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.764850
2012-04-16 22:10:22,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.043057
2012-04-16 22:10:22,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.228528
2012-04-16 22:10:23,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.423047
2012-04-16 22:10:23,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.635660
2012-04-16 22:10:24,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.864106
2012-04-16 22:10:24,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.090290
2012-04-16 22:10:25,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.352664
2012-04-16 22:10:25,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.592419
2012-04-16 22:10:26,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.872888
2012-04-16 22:10:26,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.092287
2012-04-16 22:10:27,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.347875
2012-04-16 22:10:27,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.598940
2012-04-16 22:10:28,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.868099
2012-04-16 22:10:28,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.132735
2012-04-16 22:10:29,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.345348
2012-04-16 22:10:29,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.600936
2012-04-16 22:10:30,121 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.854263
2012-04-16 22:10:30,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.087233
2012-04-16 22:10:31,124 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.329250
2012-04-16 22:10:31,625 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.537339
2012-04-16 22:10:32,127 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.749953
2012-04-16 22:10:32,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.942209
2012-04-16 22:10:33,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.157084
2012-04-16 22:10:33,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.333508
2012-04-16 22:10:34,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.469219
2012-04-16 22:10:34,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.636595
2012-04-16 22:10:35,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.797186
2012-04-16 22:10:35,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.962301
2012-04-16 22:10:36,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.125153
2012-04-16 22:10:36,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.294792
2012-04-16 22:10:37,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.471215
2012-04-16 22:10:37,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.634068
2012-04-16 22:10:38,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.839896
2012-04-16 22:10:38,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.052509
2012-04-16 22:10:39,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.231110
2012-04-16 22:10:39,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.232944
2012-04-16 22:10:39,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.427463
2012-04-16 22:10:40,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.640076
2012-04-16 22:10:40,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.821023
2012-04-16 22:10:41,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.031375
2012-04-16 22:10:41,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.248512
2012-04-16 22:10:42,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.470172
2012-04-16 22:10:42,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.655643
2012-04-16 22:10:43,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.850162
2012-04-16 22:10:43,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.042419
2012-04-16 22:10:44,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.196224
2012-04-16 22:10:44,647 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.377171
2012-04-16 22:10:45,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.544548
2012-04-16 22:10:45,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.748114
2012-04-16 22:10:46,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.920014
2012-04-16 22:10:46,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.168817
2012-04-16 22:10:47,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.410834
2012-04-16 22:10:47,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.637018
2012-04-16 22:10:48,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.847370
2012-04-16 22:10:48,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.026055
2012-04-16 22:10:49,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.186646
2012-04-16 22:10:49,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.322357
2012-04-16 22:10:50,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.473900
2012-04-16 22:10:50,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.663895
2012-04-16 22:10:51,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.810915
2012-04-16 22:10:51,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.980553
2012-04-16 22:10:52,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.156977
2012-04-16 22:10:52,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.333401
2012-04-16 22:10:53,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.516610
2012-04-16 22:10:53,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.699819
2012-04-16 22:10:54,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.844577
2012-04-16 22:10:54,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.989335
2012-04-16 22:10:55,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.127308
2012-04-16 22:10:55,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.285637
2012-04-16 22:10:56,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.432656
2012-04-16 22:10:56,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.609080
2012-04-16 22:10:57,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.805861
2012-04-16 22:10:57,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.018474
2012-04-16 22:10:58,184 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.242396
2012-04-16 22:10:58,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.443700
2012-04-16 22:10:59,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.701551
2012-04-16 22:10:59,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.984281
2012-04-16 22:11:00,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.273797
2012-04-16 22:11:00,691 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.581408
2012-04-16 22:11:01,192 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.931993
2012-04-16 22:11:01,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.287103
2012-04-16 22:11:02,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.592452
2012-04-16 22:11:02,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.906848
2012-04-16 22:11:02,838 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 100.000000
2012-04-16 22:11:04,127 DEBUG: install progress dpkg-exec 0.000000
2012-04-16 22:11:06,617 DEBUG: install progress fglrx-amdcccle 0.000000
2012-04-16 22:11:06,716 DEBUG: install progress fglrx-amdcccle 6.250000
2012-04-16 22:11:06,717 DEBUG: install progress fglrx-amdcccle 12.500000
2012-04-16 22:11:07,044 DEBUG: install progress fglrx-amdcccle 18.750000
2012-04-16 22:11:07,547 DEBUG: install progress fglrx 18.750000
2012-04-16 22:11:07,647 DEBUG: install progress fglrx 25.000000
2012-04-16 22:11:27,430 DEBUG: install progress fglrx 31.250000
2012-04-16 22:11:28,324 DEBUG: install progress fglrx 37.500000
2012-04-16 22:11:28,517 DEBUG: install progress bamfdaemon 37.500000
2012-04-16 22:11:28,719 DEBUG: install progress gnome-menus 37.500000
2012-04-16 22:11:28,909 DEBUG: install progress ureadahead 37.500000
2012-04-16 22:11:29,112 DEBUG: install progress initramfs-tools 37.500000
2012-04-16 22:11:41,951 DEBUG: install progress libc-bin 37.500000
2012-04-16 22:11:42,415 DEBUG: install progress dpkg-exec 37.500000
2012-04-16 22:11:43,114 DEBUG: install progress fglrx-updates 37.500000
2012-04-16 22:11:43,215 DEBUG: install progress fglrx-updates 43.750000
2012-04-16 22:11:47,610 DEBUG: install progress fglrx-updates 50.000000
2012-04-16 22:11:47,689 DEBUG: install progress fglrx-updates 56.250000
2012-04-16 22:11:47,934 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2012-04-16 22:11:48,035 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2012-04-16 22:11:48,648 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2012-04-16 22:11:48,720 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2012-04-16 22:11:48,806 DEBUG: install progress ureadahead 75.000000
2012-04-16 22:11:49,226 DEBUG: install progress dpkg-exec 75.000000
2012-04-16 22:11:49,268 DEBUG: install progress fglrx-updates 75.000000
2012-04-16 22:11:49,656 DEBUG: install progress fglrx-updates 81.250000
2012-04-16 22:12:09,605 DEBUG: install progress fglrx-updates 87.500000
2012-04-16 22:12:10,124 DEBUG: install progress bamfdaemon 87.500000
2012-04-16 22:12:10,271 DEBUG: install progress gnome-menus 87.500000
2012-04-16 22:12:10,473 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2012-04-16 22:12:10,552 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2012-04-16 22:12:10,632 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-04-16 22:12:10,711 DEBUG: install progress initramfs-tools 100.000000
2012-04-16 22:12:22,170 DEBUG: install progress libc-bin 100.000000
2012-04-16 22:12:24,880 DEBUG: (Reading database ... 198250 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx-updates.
(Reading database ... 198006 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.911-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.911 DKMS files...
Building only for 3.0.0-17-generic
Building for architecture x86_64
Building initial module for 3.0.0-17-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-17-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.911-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-04-16 22:12:25,111 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-16 22:12:25,197 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-04-16 22:12:25,341 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:12:25,341 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:12:25,394 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:12:25,394 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:16:23,535 DEBUG: Shutting down
2012-04-16 22:16:52,267 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48>
2012-04-16 22:16:53,751 DEBUG: reading modalias file /lib/modules/3.0.0-17-generic/modules.alias
2012-04-16 22:16:53,826 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-16 22:16:53,826 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-16 22:16:53,854 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-04-16 22:16:53,878 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-16 22:16:53,886 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-16 22:16:53,887 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-16 22:16:53,887 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-16 22:16:53,887 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-16 22:16:53,894 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-16 22:16:53,930 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-16 22:16:53,931 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-16 22:16:53,931 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-16 22:16:53,938 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-16 22:16:53,939 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-16 22:16:53,974 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-16 22:16:53,975 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-16 22:16:54,008 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-16 22:16:54,009 DEBUG: Firmware for DVB cards not available
2012-04-16 22:16:54,010 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-16 22:16:54,022 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-16 22:16:54,031 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-16 22:16:54,034 DEBUG: nvidia.available: falling back to default
2012-04-16 22:16:54,140 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:16:54,148 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-16 22:16:54,157 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-16 22:16:54,159 DEBUG: nvidia.available: falling back to default
2012-04-16 22:16:54,243 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:16:54,251 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-16 22:16:54,260 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-16 22:16:54,261 DEBUG: nvidia.available: falling back to default
2012-04-16 22:16:54,345 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:16:54,346 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-04-16 22:16:54,353 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-16 22:16:54,368 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-16 22:16:54,371 DEBUG: nvidia.available: falling back to default
2012-04-16 22:16:54,417 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:16:54,423 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-16 22:16:54,432 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-16 22:16:54,433 DEBUG: nvidia.available: falling back to default
2012-04-16 22:16:54,490 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:16:54,496 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-16 22:16:54,504 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-16 22:16:54,506 DEBUG: nvidia.available: falling back to default
2012-04-16 22:16:54,567 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:16:54,567 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-16 22:16:54,589 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-16 22:16:54,589 DEBUG: fglrx.available: falling back to default
2012-04-16 22:16:54,673 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:16:54,680 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-16 22:16:54,690 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-16 22:16:54,690 DEBUG: fglrx.available: falling back to default
2012-04-16 22:16:54,772 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-16 22:16:54,773 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-16 22:16:54,799 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-16 22:16:54,813 DEBUG: Software modem not available
2012-04-16 22:16:54,814 DEBUG: all custom handlers loaded
2012-04-16 22:16:54,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 22:16:54,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 22:16:54,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:54,896 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:54,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 22:16:54,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 22:16:54,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 22:16:55,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:16:55,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 22:16:55,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 22:16:55,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 22:16:55,129 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,129 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 22:16:55,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 22:16:55,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 22:16:55,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 22:16:55,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-16 22:16:55,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-16 22:16:55,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 22:16:55,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 22:16:55,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 22:16:55,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 22:16:55,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 22:16:55,341 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2012-04-16 22:16:55,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:16:55,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 22:16:55,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 22:16:55,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 22:16:55,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-16 22:16:55,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-16 22:16:55,395 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:16:55,396 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:16:55,344 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:16:55,405 DEBUG: fglrx.available: falling back to default
2012-04-16 22:16:55,517 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:16:55,519 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:16:55,452 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:16:55,519 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-16 22:16:55,583 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:16:55,583 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:16:55,520 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:16:55,593 DEBUG: fglrx.available: falling back to default
2012-04-16 22:16:55,700 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:16:55,700 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:16:55,637 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:16:55,701 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-16 22:16:55,763 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:16:55,764 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:16:55,701 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 22:16:55,771 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-16 22:16:55,781 DEBUG: fglrx.available: falling back to default
2012-04-16 22:16:55,879 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:16:55,880 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:16:55,821 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 22:16:55,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 22:16:55,889 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:16:55,890 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:16:55,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 22:16:55,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 22:16:55,898 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-16 22:16:55,899 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 22:16:55,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-04-16 22:16:55,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-04-16 22:16:55,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:16:55,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 22:16:55,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-04-16 22:16:55,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 22:16:55,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 22:16:55,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 22:16:55,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:16:55,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:16:55,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:16:55,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 22:16:55,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 22:16:55,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-04-16 22:16:55,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 22:16:55,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 22:16:55,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 22:16:55,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 22:16:55,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 22:16:55,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 22:16:55,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 22:16:55,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 22:16:55,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 22:16:55,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 22:16:55,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 22:16:55,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-04-16 22:16:55,921 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:16:55,921 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 22:16:55,923 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-16 22:16:55,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 22:16:55,926 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-16 22:16:55,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 22:16:55,926 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 22:16:55,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:16:55,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 22:16:55,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 22:16:55,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 22:16:55,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-16 22:16:55,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 22:16:55,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 22:16:55,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 22:16:55,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-04-16 22:16:55,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:16:55,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 22:16:55,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 22:16:55,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:16:55,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:16:55,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 22:16:55,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 22:16:55,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-16 22:16:55,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-16 22:16:55,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 22:16:55,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:16:55,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 22:16:55,967 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-04-16 22:16:55,967 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fd1b48> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 22:16:55,967 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 22:16:55,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 22:16:55,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 22:16:55,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21ecf38> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 22:39:51,313 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48>
2012-04-16 22:39:52,877 DEBUG: reading modalias file /lib/modules/3.0.0-17-generic/modules.alias
2012-04-16 22:39:52,950 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-16 22:39:52,950 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-16 22:39:52,978 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-04-16 22:39:53,014 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-16 22:39:53,023 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-16 22:39:53,024 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-16 22:39:53,025 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-16 22:39:53,025 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-16 22:39:53,033 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-16 22:39:53,068 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-16 22:39:53,069 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-16 22:39:53,069 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-16 22:39:53,076 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-16 22:39:53,076 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-16 22:39:53,111 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-16 22:39:53,111 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-16 22:39:53,160 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-16 22:39:53,162 DEBUG: Firmware for DVB cards not available
2012-04-16 22:39:53,162 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-16 22:39:53,176 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-16 22:39:53,185 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-16 22:39:53,190 DEBUG: nvidia.available: falling back to default
2012-04-16 22:39:53,306 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:39:53,314 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-16 22:39:53,325 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-16 22:39:53,327 DEBUG: nvidia.available: falling back to default
2012-04-16 22:39:53,411 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:39:53,416 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-16 22:39:53,419 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-16 22:39:53,420 DEBUG: nvidia.available: falling back to default
2012-04-16 22:39:53,452 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:39:53,452 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-04-16 22:39:53,455 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-16 22:39:53,459 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-16 22:39:53,460 DEBUG: nvidia.available: falling back to default
2012-04-16 22:39:53,493 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:39:53,497 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-16 22:39:53,505 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-16 22:39:53,507 DEBUG: nvidia.available: falling back to default
2012-04-16 22:39:53,548 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 22:39:53,550 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-16 22:39:53,554 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-16 22:39:53,555 DEBUG: nvidia.available: falling back to default
2012-04-16 22:39:53,601 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:39:53,601 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-16 22:39:53,614 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-16 22:39:53,614 DEBUG: fglrx.available: falling back to default
2012-04-16 22:39:53,667 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 22:39:53,671 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-16 22:39:53,679 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-16 22:39:53,679 DEBUG: fglrx.available: falling back to default
2012-04-16 22:39:53,740 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-16 22:39:53,741 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-16 22:39:53,781 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-16 22:39:53,797 DEBUG: Software modem not available
2012-04-16 22:39:53,798 DEBUG: all custom handlers loaded
2012-04-16 22:39:53,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 22:39:53,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 22:39:53,810 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:53,877 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:53,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 22:39:53,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 22:39:53,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 22:39:54,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:39:54,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 22:39:54,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 22:39:54,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 22:39:54,113 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 22:39:54,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 22:39:54,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 22:39:54,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 22:39:54,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-16 22:39:54,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-16 22:39:54,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 22:39:54,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 22:39:54,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 22:39:54,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 22:39:54,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 22:39:54,328 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2012-04-16 22:39:54,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:39:54,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 22:39:54,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 22:39:54,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 22:39:54,331 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-16 22:39:54,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,331 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-16 22:39:54,380 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:54,380 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:39:54,331 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:39:54,387 DEBUG: fglrx.available: falling back to default
2012-04-16 22:39:54,488 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:54,489 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:39:54,426 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:39:54,489 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-16 22:39:54,554 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:54,555 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:39:54,490 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:39:54,560 DEBUG: fglrx.available: falling back to default
2012-04-16 22:39:54,600 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:54,600 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:39:54,576 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 22:39:54,601 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-16 22:39:54,639 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:54,639 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:39:54,601 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 22:39:54,645 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-16 22:39:54,655 DEBUG: fglrx.available: falling back to default
2012-04-16 22:39:54,769 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:54,770 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:39:54,700 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 22:39:54,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 22:39:54,780 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:39:54,781 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,781 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 22:39:54,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 22:39:54,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 22:39:54,785 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-16 22:39:54,785 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 22:39:54,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-04-16 22:39:54,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-04-16 22:39:54,790 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:39:54,790 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 22:39:54,790 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-04-16 22:39:54,790 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 22:39:54,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,791 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 22:39:54,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,791 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 22:39:54,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,791 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:39:54,791 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:39:54,791 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 22:39:54,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 22:39:54,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 22:39:54,792 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-04-16 22:39:54,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 22:39:54,792 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 22:39:54,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 22:39:54,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 22:39:54,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 22:39:54,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 22:39:54,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 22:39:54,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 22:39:54,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 22:39:54,805 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 22:39:54,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 22:39:54,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-04-16 22:39:54,806 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:39:54,806 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 22:39:54,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-16 22:39:54,808 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 22:39:54,810 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-16 22:39:54,810 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 22:39:54,810 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 22:39:54,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:39:54,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 22:39:54,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 22:39:54,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 22:39:54,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-16 22:39:54,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 22:39:54,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 22:39:54,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 22:39:54,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-04-16 22:39:54,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-16 22:39:54,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 22:39:54,813 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 22:39:54,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:39:54,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:39:54,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 22:39:54,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 22:39:54,822 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-16 22:39:54,823 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,823 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-16 22:39:54,823 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 22:39:54,823 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 22:39:54,823 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 22:39:54,856 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-04-16 22:39:54,857 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a2b48> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 22:39:54,857 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 22:39:54,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 22:39:54,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 22:39:54,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 22:39:54,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15bdf38> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 22:39:54,940 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:54,941 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:39:55,022 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:55,023 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 22:39:55,176 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:55,177 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:39:55,301 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:55,302 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 22:39:55,402 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 22:39:55,403 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:01:20,618 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70>
2012-04-16 23:01:22,089 DEBUG: reading modalias file /lib/modules/3.0.0-17-generic/modules.alias
2012-04-16 23:01:22,176 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-16 23:01:22,177 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-16 23:01:22,204 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-04-16 23:01:22,231 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-16 23:01:22,240 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-16 23:01:22,241 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-16 23:01:22,242 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-16 23:01:22,242 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-16 23:01:22,250 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-16 23:01:22,288 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-16 23:01:22,289 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-16 23:01:22,289 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-16 23:01:22,297 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-16 23:01:22,298 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-16 23:01:22,340 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-16 23:01:22,341 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-16 23:01:22,377 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-16 23:01:22,378 DEBUG: Firmware for DVB cards not available
2012-04-16 23:01:22,378 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-16 23:01:22,388 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-16 23:01:22,393 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-16 23:01:22,394 DEBUG: nvidia.available: falling back to default
2012-04-16 23:01:22,496 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 23:01:22,503 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-16 23:01:22,510 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-16 23:01:22,512 DEBUG: nvidia.available: falling back to default
2012-04-16 23:01:22,598 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 23:01:22,605 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-16 23:01:22,615 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-16 23:01:22,617 DEBUG: nvidia.available: falling back to default
2012-04-16 23:01:22,663 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 23:01:22,663 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-04-16 23:01:22,667 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-16 23:01:22,674 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-16 23:01:22,676 DEBUG: nvidia.available: falling back to default
2012-04-16 23:01:22,762 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 23:01:22,769 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-16 23:01:22,779 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-16 23:01:22,781 DEBUG: nvidia.available: falling back to default
2012-04-16 23:01:22,864 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 23:01:22,870 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-16 23:01:22,880 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-16 23:01:22,881 DEBUG: nvidia.available: falling back to default
2012-04-16 23:01:22,934 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 23:01:22,935 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-16 23:01:22,949 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-16 23:01:22,950 DEBUG: fglrx.available: falling back to default
2012-04-16 23:01:23,014 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 23:01:23,020 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-16 23:01:23,029 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-16 23:01:23,029 DEBUG: fglrx.available: falling back to default
2012-04-16 23:01:23,112 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-16 23:01:23,113 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-16 23:01:23,156 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-16 23:01:23,173 DEBUG: Software modem not available
2012-04-16 23:01:23,174 DEBUG: all custom handlers loaded
2012-04-16 23:01:23,174 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 23:01:23,174 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 23:01:23,186 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:23,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:23,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 23:01:23,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 23:01:23,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 23:01:23,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 23:01:23,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:23,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 23:01:23,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 23:01:23,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 23:01:23,499 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:23,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:23,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 23:01:23,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 23:01:23,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 23:01:23,499 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-16 23:01:23,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:23,499 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-16 23:01:23,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 23:01:23,500 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:23,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 23:01:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 23:01:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 23:01:23,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 23:01:23,692 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2012-04-16 23:01:23,692 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:23,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 23:01:23,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 23:01:23,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 23:01:23,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 23:01:23,695 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-16 23:01:23,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:23,695 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-16 23:01:23,757 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:01:23,758 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:01:23,695 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 23:01:23,768 DEBUG: fglrx.available: falling back to default
2012-04-16 23:01:23,851 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:01:23,852 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:01:23,797 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 23:01:23,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-16 23:01:23,917 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:01:23,918 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:01:23,853 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 23:01:23,928 DEBUG: fglrx.available: falling back to default
2012-04-16 23:01:24,022 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:01:24,023 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:01:23,974 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 23:01:24,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-16 23:01:24,087 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:01:24,088 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:01:24,023 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 23:01:24,096 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-16 23:01:24,108 DEBUG: fglrx.available: falling back to default
2012-04-16 23:01:24,193 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:01:24,194 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:01:24,150 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 23:01:24,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 23:01:24,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 23:01:24,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 23:01:24,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 23:01:24,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 23:01:24,208 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-16 23:01:24,208 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,208 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 23:01:24,211 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-04-16 23:01:24,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 23:01:24,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-04-16 23:01:24,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 23:01:24,230 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 23:01:24,230 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 23:01:24,230 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,230 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 23:01:24,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,230 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 23:01:24,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,230 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 23:01:24,231 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 23:01:24,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 23:01:24,231 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-04-16 23:01:24,231 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 23:01:24,231 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,231 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 23:01:24,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 23:01:24,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 23:01:24,243 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 23:01:24,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,243 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 23:01:24,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 23:01:24,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 23:01:24,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 23:01:24,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 23:01:24,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 23:01:24,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-16 23:01:24,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 23:01:24,246 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-16 23:01:24,246 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 23:01:24,248 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-16 23:01:24,249 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 23:01:24,249 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,249 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 23:01:24,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 23:01:24,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 23:01:24,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 23:01:24,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 23:01:24,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 23:01:24,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 23:01:24,250 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,250 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 23:01:24,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 23:01:24,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 23:01:24,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 23:01:24,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 23:01:24,253 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 23:01:24,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 23:01:24,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 23:01:24,261 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-16 23:01:24,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,261 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-16 23:01:24,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 23:01:24,261 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:01:24,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 23:01:24,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-04-16 23:01:24,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:01:24,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1b55a70> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 23:01:24,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 23:01:24,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 23:01:24,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 23:01:24,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 23:01:24,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 23:01:24,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 23:01:24,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 23:01:24,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 23:01:24,295 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d6df38> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 23:01:24,355 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:01:24,356 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:01:28,480 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:01:28,480 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:01:30,915 DEBUG: Installing package: fglrx
2012-04-16 23:01:31,543 DEBUG: install progress dpkg-exec 0.000000
2012-04-16 23:01:31,846 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2012-04-16 23:01:31,846 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2012-04-16 23:01:31,922 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2012-04-16 23:01:32,094 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2012-04-16 23:01:32,604 DEBUG: install progress fglrx-updates 18.750000
2012-04-16 23:01:32,705 DEBUG: install progress fglrx-updates 25.000000
2012-04-16 23:01:36,808 DEBUG: install progress fglrx-updates 31.250000
2012-04-16 23:01:37,515 DEBUG: install progress fglrx-updates 37.500000
2012-04-16 23:01:37,695 DEBUG: install progress bamfdaemon 37.500000
2012-04-16 23:01:37,864 DEBUG: install progress gnome-menus 37.500000
2012-04-16 23:01:37,999 DEBUG: install progress ureadahead 37.500000
2012-04-16 23:01:38,157 DEBUG: install progress initramfs-tools 37.500000
2012-04-16 23:01:48,279 DEBUG: install progress libc-bin 37.500000
2012-04-16 23:01:48,687 DEBUG: install progress dpkg-exec 37.500000
2012-04-16 23:01:49,233 DEBUG: install progress fglrx 37.500000
2012-04-16 23:01:49,233 DEBUG: install progress fglrx 43.750000
2012-04-16 23:01:53,444 DEBUG: install progress fglrx 50.000000
2012-04-16 23:01:53,523 DEBUG: install progress fglrx 56.250000
2012-04-16 23:01:53,766 DEBUG: install progress fglrx-amdcccle 56.250000
2012-04-16 23:01:53,766 DEBUG: install progress fglrx-amdcccle 62.500000
2012-04-16 23:01:54,501 DEBUG: install progress fglrx-amdcccle 68.750000
2012-04-16 23:01:54,578 DEBUG: install progress fglrx-amdcccle 75.000000
2012-04-16 23:01:54,661 DEBUG: install progress ureadahead 75.000000
2012-04-16 23:01:55,082 DEBUG: install progress dpkg-exec 75.000000
2012-04-16 23:01:55,117 DEBUG: install progress fglrx 75.000000
2012-04-16 23:01:55,490 DEBUG: install progress fglrx 81.250000
2012-04-16 23:02:12,176 DEBUG: install progress fglrx 87.500000
2012-04-16 23:02:12,783 DEBUG: install progress bamfdaemon 87.500000
2012-04-16 23:02:13,015 DEBUG: install progress gnome-menus 87.500000
2012-04-16 23:02:13,300 DEBUG: install progress fglrx-amdcccle 87.500000
2012-04-16 23:02:13,401 DEBUG: install progress fglrx-amdcccle 93.750000
2012-04-16 23:02:13,491 DEBUG: install progress fglrx-amdcccle 100.000000
2012-04-16 23:02:13,581 DEBUG: install progress initramfs-tools 100.000000
2012-04-16 23:02:23,789 DEBUG: install progress libc-bin 100.000000
2012-04-16 23:02:26,297 DEBUG: (Reading database ... 198266 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx.
(Reading database ... 198006 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.881 DKMS files...
Building only for 3.0.0-17-generic
Building for architecture x86_64
Building initial module for 3.0.0-17-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-17-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-04-16 23:02:26,464 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:00.0
2012-04-16 23:02:46,907 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:46,907 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:02:47,045 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:47,046 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:02:47,223 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:47,223 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:02:47,338 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:47,339 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:02:47,480 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:47,481 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:02:47,638 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:47,639 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:02:47,794 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:47,795 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:02:48,012 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:48,012 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:02:48,121 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:48,121 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:02:48,262 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:02:48,263 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:04:19,705 DEBUG: Shutting down
2012-04-16 23:21:53,607 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70>
2012-04-16 23:22:00,701 DEBUG: reading modalias file /lib/modules/3.0.0-17-generic/modules.alias
2012-04-16 23:22:00,949 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-16 23:22:00,970 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-16 23:22:01,024 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-04-16 23:22:01,060 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-16 23:22:01,141 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-16 23:22:01,142 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-16 23:22:01,143 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-16 23:22:01,143 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-16 23:22:01,150 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-16 23:22:01,180 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-16 23:22:01,180 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-16 23:22:01,181 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-16 23:22:01,199 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-16 23:22:01,199 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-16 23:22:01,243 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-16 23:22:01,243 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-16 23:22:01,331 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-16 23:22:01,331 DEBUG: Firmware for DVB cards not available
2012-04-16 23:22:01,331 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-16 23:22:01,454 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-16 23:22:01,459 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-16 23:22:01,460 DEBUG: nvidia.available: falling back to default
2012-04-16 23:22:01,866 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 23:22:01,871 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-16 23:22:01,878 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-16 23:22:01,879 DEBUG: nvidia.available: falling back to default
2012-04-16 23:22:01,920 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 23:22:01,923 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-16 23:22:01,929 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-16 23:22:01,930 DEBUG: nvidia.available: falling back to default
2012-04-16 23:22:01,988 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 23:22:01,989 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-04-16 23:22:02,030 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-16 23:22:02,038 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-16 23:22:02,039 DEBUG: nvidia.available: falling back to default
2012-04-16 23:22:02,077 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 23:22:02,081 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-16 23:22:02,085 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-16 23:22:02,086 DEBUG: nvidia.available: falling back to default
2012-04-16 23:22:02,128 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-16 23:22:02,132 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-16 23:22:02,137 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-16 23:22:02,138 DEBUG: nvidia.available: falling back to default
2012-04-16 23:22:02,167 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 23:22:02,167 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-16 23:22:02,200 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-16 23:22:02,205 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-16 23:22:02,205 DEBUG: fglrx.available: falling back to default
2012-04-16 23:22:02,235 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-16 23:22:02,245 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-16 23:22:02,245 DEBUG: fglrx.available: falling back to default
2012-04-16 23:22:02,276 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-16 23:22:02,276 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-16 23:22:02,337 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-16 23:22:02,647 DEBUG: Software modem not available
2012-04-16 23:22:02,647 DEBUG: all custom handlers loaded
2012-04-16 23:22:02,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 23:22:02,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 23:22:02,655 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:02,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:02,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 23:22:02,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 23:22:02,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 23:22:03,135 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 23:22:03,135 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:03,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 23:22:03,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 23:22:03,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 23:22:03,149 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:03,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:03,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 23:22:03,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 23:22:03,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 23:22:03,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-16 23:22:03,150 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:03,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-16 23:22:03,150 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:03,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 23:22:03,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:03,150 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:03,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 23:22:03,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 23:22:03,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 23:22:03,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 23:22:03,341 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2012-04-16 23:22:03,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:03,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 23:22:03,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 23:22:03,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 23:22:03,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 23:22:03,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-16 23:22:03,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:03,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-04-16 23:22:06,910 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:06,910 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:22:03,344 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 23:22:07,138 DEBUG: fglrx.available: falling back to default
2012-04-16 23:22:07,173 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:07,173 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:22:07,153 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 23:22:07,238 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-16 23:22:07,261 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:07,262 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:22:07,239 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 23:22:07,264 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-16 23:22:07,268 DEBUG: fglrx.available: falling back to default
2012-04-16 23:22:07,304 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:07,304 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:22:07,284 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-16 23:22:07,304 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-16 23:22:07,324 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:07,324 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:22:07,304 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 23:22:07,391 DEBUG: fglrx.available: falling back to default
2012-04-16 23:22:07,426 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:07,426 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:22:07,406 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-16 23:22:07,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 23:22:07,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 23:22:07,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-16 23:22:07,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 23:22:07,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 23:22:07,497 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-16 23:22:07,497 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 23:22:07,500 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-04-16 23:22:07,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 23:22:07,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-04-16 23:22:07,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 23:22:07,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 23:22:07,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 23:22:07,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,522 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,522 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 23:22:07,522 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,522 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 23:22:07,522 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,522 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-16 23:22:07,522 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 23:22:07,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 23:22:07,522 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-04-16 23:22:07,522 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 23:22:07,522 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,523 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 23:22:07,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 23:22:07,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 23:22:07,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 23:22:07,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-04-16 23:22:07,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 23:22:07,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 23:22:07,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 23:22:07,536 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,536 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 23:22:07,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 23:22:07,537 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-16 23:22:07,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 23:22:07,539 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-16 23:22:07,539 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 23:22:07,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-16 23:22:07,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 23:22:07,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 23:22:07,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 23:22:07,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 23:22:07,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 23:22:07,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 23:22:07,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 23:22:07,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 23:22:07,543 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 23:22:07,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 23:22:07,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 23:22:07,544 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 23:22:07,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 23:22:07,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 23:22:07,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 23:22:07,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 23:22:07,554 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-16 23:22:07,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,555 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-16 23:22:07,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 23:22:07,555 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-16 23:22:07,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 23:22:07,589 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-04-16 23:22:07,590 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xff6a70> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00001002d0000AA60sv000017AAsd00003977bc04sc03i00')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'platform:ideapad')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,kE3,EE,F0,ram4,lsfw')
2012-04-16 23:22:07,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0003v046Dp0825e0010-e0,1,kD4,ramlsfw')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'platform:regulatory')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00000104sv000017AAsd00003975bc06sc00i00')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'wmi:ABBC0F20-8EA1-11D1-00A0-C90629100000')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-16 23:22:07,591 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00001002d000068C1sv000017AAsd00003977bc03sc00i00')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v0000197Bd00002388sv000017AAsd00003923bc08sc80i00')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc01ip00')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:SYN1043:SYN1000:SYN0002:PNP0F13:')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v0000197Bd00002386sv000017AAsd00003922bc08sc05i01')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr3FCN19WW:bd02/11/2011:svnLENOVO:pnIdeaPadY460p:pvrRev1.0:rvnLENOVO:rnKL2:rvrRev1.0:cvnLENOVO:ct10:cvrRev1.0:')
2012-04-16 23:22:07,592 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v0000197Bd00002389sv000017AAsd00003924bc08sc80i00')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc01ip00')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:VPC2004:')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'wmi:ABBC0F40-8EA1-11D1-00A0-C90629100000')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'platform:reg-dummy')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic01isc02ip00')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'usb:v046Dp0825d0010dcEFdsc02dp01ic0Eisc02ip00')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-16 23:22:07,593 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-04-16 23:22:07,594 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-04-16 23:22:07,594 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v0000197Bd00002387sv000017AAsd00003921bc08sc80i00')
2012-04-16 23:22:07,594 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-16 23:22:07,594 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-04-16 23:22:07,594 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'pci:v000014E4d00001692sv000017AAsd00003975bc02sc00i00')
2012-04-16 23:22:07,594 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x120e3b0> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-16 23:22:07,657 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:07,658 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:22:07,823 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:07,823 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:22:08,269 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:08,270 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:22:08,316 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:08,316 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:22:08,355 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:22:08,740 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:25:24,737 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:25:24,737 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:25:26,143 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:25:26,143 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:25:28,805 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:25:28,806 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:25:34,873 DEBUG: Installing package: fglrx-updates
2012-04-16 23:25:36,715 DEBUG: install progress dpkg-exec 0.000000
2012-04-16 23:25:39,659 DEBUG: install progress fglrx-amdcccle 0.000000
2012-04-16 23:25:39,760 DEBUG: install progress fglrx-amdcccle 6.250000
2012-04-16 23:25:40,054 DEBUG: install progress fglrx-amdcccle 12.500000
2012-04-16 23:25:41,181 DEBUG: install progress fglrx-amdcccle 18.750000
2012-04-16 23:25:42,175 DEBUG: install progress fglrx 18.750000
2012-04-16 23:25:42,275 DEBUG: install progress fglrx 25.000000
2012-04-16 23:26:06,015 DEBUG: install progress fglrx 31.250000
2012-04-16 23:26:06,953 DEBUG: install progress fglrx 37.500000
2012-04-16 23:26:07,110 DEBUG: install progress bamfdaemon 37.500000
2012-04-16 23:26:07,313 DEBUG: install progress gnome-menus 37.500000
2012-04-16 23:26:07,483 DEBUG: install progress ureadahead 37.500000
2012-04-16 23:26:07,674 DEBUG: install progress initramfs-tools 37.500000
2012-04-16 23:26:19,347 DEBUG: install progress libc-bin 37.500000
2012-04-16 23:26:19,832 DEBUG: install progress dpkg-exec 37.500000
2012-04-16 23:26:20,601 DEBUG: install progress fglrx-updates 37.500000
2012-04-16 23:26:20,702 DEBUG: install progress fglrx-updates 43.750000
2012-04-16 23:26:26,206 DEBUG: install progress fglrx-updates 50.000000
2012-04-16 23:26:26,286 DEBUG: install progress fglrx-updates 56.250000
2012-04-16 23:26:26,483 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2012-04-16 23:26:26,583 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2012-04-16 23:26:27,342 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2012-04-16 23:26:27,407 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2012-04-16 23:26:27,480 DEBUG: install progress ureadahead 75.000000
2012-04-16 23:26:27,879 DEBUG: install progress dpkg-exec 75.000000
2012-04-16 23:26:27,920 DEBUG: install progress fglrx-updates 75.000000
2012-04-16 23:26:28,308 DEBUG: install progress fglrx-updates 81.250000
2012-04-16 23:26:48,004 DEBUG: install progress fglrx-updates 87.500000
2012-04-16 23:26:48,635 DEBUG: install progress bamfdaemon 87.500000
2012-04-16 23:26:48,782 DEBUG: install progress gnome-menus 87.500000
2012-04-16 23:26:49,084 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2012-04-16 23:26:49,165 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2012-04-16 23:26:49,244 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-04-16 23:26:49,322 DEBUG: install progress initramfs-tools 100.000000
2012-04-16 23:26:58,989 DEBUG: install progress libc-bin 100.000000
2012-04-16 23:27:01,596 DEBUG: (Reading database ... 198250 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx-updates.
(Reading database ... 198006 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.911-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.911 DKMS files...
Building only for 3.0.0-17-generic
Building for architecture x86_64
Building initial module for 3.0.0-17-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-17-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.911-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-04-16 23:27:01,838 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-16 23:27:01,921 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-04-16 23:27:02,066 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:02,066 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:27:02,094 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:02,094 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:27:05,154 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:05,154 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:27:05,176 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:05,176 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:27:05,216 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:05,216 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-16 23:27:05,390 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:05,390 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:27:05,412 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:05,412 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:27:05,453 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:05,453 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:27:05,475 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:05,475 DEBUG: fglrx_updates is not the alternative in use
2012-04-16 23:27:05,507 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-16 23:27:05,507 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking


```

---

### Post by amaz1ng on 2012-04-17
Any thoughts guys? I'm stuck, I've tried all the standard "make sure it's plugged in, update your drivers" stuff.

---

### Post by amaz1ng on 2012-11-27
in case anyone stumbles on this error, the way that worked for me is in beelzebub's reply here: [http://ubuntuforums.org/showthread.php?t=2073125](http://ubuntuforums.org/showthread.php?t=2073125)

---

