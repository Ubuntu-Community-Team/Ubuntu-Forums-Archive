---
title: "Ortek WKB-2000 (AKA Xenta) Wireless keybord with touchpad Multi-touch problem"
date: 2012-07-08
forum: Hardware
---

### Post by david davidson on 2012-07-08
There have been other threads about this but they are all quite old now and generally deal with getting the keyboard to work rather than this specific issue.

The keyboard/touchpad in question is this: 
[http://www.ebuyer.com/product/158377](http://www.ebuyer.com/product/158377)


The keyboard works. The touchpad moves the cursor, left and right click work, tap to click works, two finger click works as a mouse wheel click (open link in new tab etc) but there is no scrolling function at all. I have tried two finger scrolling and scrolling at the side of the touchpad but neither work.

In the mouse settings there is no tab for touchpad settings (I would expect options to disable tap to click etc).

I have tried Xubuntu 12.04, Ubuntu 12.04, Xubuntu 12.10 alpha 2, Linux Mint 13 and Fedora 17. Same situation with all of them. I have also tried different machines just to be sure.


In Xubuntu 11.10 alpha 2 there are some options in Additional Drivers that seem to be relevant but when attempting to install them I get an error (see attached screenshots)

The entire jockey.log is as follows:

```
2012-07-08 12:03:42,639 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec>
2012-07-08 12:03:45,430 DEBUG: reading modalias file /lib/modules/3.5.0-1-generic/modules.alias
2012-07-08 12:03:45,618 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-08 12:03:45,620 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-08 12:03:45,715 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-08 12:03:45,730 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-08 12:03:45,751 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-08 12:03:45,752 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-08 12:03:45,752 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-08 12:03:45,787 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-08 12:03:45,787 DEBUG: Firmware for DVB cards not available
2012-07-08 12:03:45,788 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-08 12:03:45,792 WARNING: Invalid custom handler module /usr/share/jockey/handlers/fglrx.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/fglrx.py", line 11, in <module>
    from NvidiaDetector.alternatives import Alternatives
ImportError: No module named NvidiaDetector.alternatives
2012-07-08 12:03:45,793 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-08 12:03:45,800 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-08 12:03:45,800 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-08 12:03:45,801 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-08 12:03:45,801 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-08 12:03:45,805 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 12, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2012-07-08 12:03:45,806 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-08 12:03:45,815 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-08 12:03:45,821 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-08 12:03:45,918 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-08 12:03:45,918 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-08 12:03:45,942 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-08 12:03:45,958 DEBUG: Software modem not available
2012-07-08 12:03:45,958 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-08 12:03:45,964 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-08 12:03:45,965 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-08 12:03:45,986 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-08 12:03:45,986 DEBUG: all custom handlers loaded
2012-07-08 12:03:45,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd0000027Esv00000000sd00000000bc05sc00i00')
2012-07-08 12:03:46,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-07-08 12:03:46,449 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:46,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-08 12:03:46,527 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-07-08 12:03:46,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-08 12:03:46,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-08 12:03:46,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-08 12:03:46,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2012-07-08 12:03:46,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k8temp'}
2012-07-08 12:03:46,558 DEBUG: got handler kmod:k8temp([KernelModuleHandler, free, enabled] AMD K8 core temperature monitor)
2012-07-08 12:03:46,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd00000269sv0000103Csd000030B7bc06sc80i00')
2012-07-08 12:03:46,565 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2012-07-08 12:03:46,580 DEBUG: got handler kmod:forcedeth([KernelModuleHandler, free, enabled] Reverse Engineered nForce ethernet driver)
2012-07-08 12:03:46,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-08 12:03:46,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2012-07-08 12:03:46,582 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:46,582 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,582 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-08 12:03:46,582 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,582 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-08 12:03:46,582 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,582 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-08 12:03:46,583 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-07-08 12:03:46,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2012-07-08 12:03:46,607 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'usb:v05A4p2000d1110dc00dsc00dp00ic03isc01ip01')
2012-07-08 12:03:46,608 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-08 12:03:46,619 DEBUG: got handler kmod:usbhid([KernelModuleHandler, free, enabled] USB HID core driver)
2012-07-08 12:03:46,619 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-07-08 12:03:46,625 DEBUG: got handler kmod:usbkbd([KernelModuleHandler, free, disabled] USB HID Boot Protocol keyboard driver)
2012-07-08 12:03:46,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:SYN012A:SYN0100:SYN0002:PNP0F13:')
2012-07-08 12:03:46,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-08 12:03:46,625 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:46,625 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-08 12:03:46,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-08 12:03:46,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'platform:eisa')
2012-07-08 12:03:46,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2012-07-08 12:03:46,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'platform:NV_TCO')
2012-07-08 12:03:46,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-07-08 12:03:46,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd0000026Csv0000103Csd000030B7bc04sc03i00')
2012-07-08 12:03:46,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-08 12:03:46,641 DEBUG: got handler kmod:snd_hda_intel([KernelModuleHandler, free, enabled] Intel HDA driver)
2012-07-08 12:03:46,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-08 12:03:46,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2012-07-08 12:03:46,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2012-07-08 12:03:46,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd000002FFsv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:46,654 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-08 12:03:46,654 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd00000244sv0000103Csd000030B7bc03sc00i00')
2012-07-08 12:03:46,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-07-08 12:03:46,674 DEBUG: got handler kmod:nvidiafb([KernelModuleHandler, free, disabled] Framebuffer driver for nVidia graphics chipset)
2012-07-08 12:03:46,675 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-07-08 12:03:46,691 DEBUG: got handler kmod:nouveau([KernelModuleHandler, free, enabled] nVidia Riva/TNT/GeForce)
2012-07-08 12:03:46,692 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-07-08 12:03:46,697 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-08 12:03:46,724 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-08 12:03:46,725 DEBUG: got handler kmod:nvidia_current([KernelModuleHandler, nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU library)
2012-07-08 12:03:46,725 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2012-07-08 12:03:46,730 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-08 12:03:46,756 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-08 12:03:46,757 DEBUG: got handler kmod:nvidia_173_updates([KernelModuleHandler, nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU library)
2012-07-08 12:03:46,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96_updates', 'package': 'nvidia-96-updates'}
2012-07-08 12:03:46,762 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-08 12:03:46,789 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-08 12:03:46,789 DEBUG: got handler kmod:nvidia_96_updates([KernelModuleHandler, nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU library)
2012-07-08 12:03:46,789 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96', 'package': 'nvidia-96'}
2012-07-08 12:03:46,794 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-08 12:03:46,821 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-08 12:03:46,821 DEBUG: got handler kmod:nvidia_96([KernelModuleHandler, nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU library)
2012-07-08 12:03:46,822 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2012-07-08 12:03:46,827 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-08 12:03:46,853 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-08 12:03:46,854 DEBUG: got handler kmod:nvidia_173([KernelModuleHandler, nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU library)
2012-07-08 12:03:46,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-07-08 12:03:46,859 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-08 12:03:46,886 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-08 12:03:46,887 DEBUG: got handler kmod:nvidia_current_updates([KernelModuleHandler, nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU library)
2012-07-08 12:03:46,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-07-08 12:03:46,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-07-08 12:03:46,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd00000270sv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:46,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-08 12:03:46,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd0000027Fsv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:46,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-08 12:03:46,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-08 12:03:46,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,915 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-07-08 12:03:46,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-08 12:03:46,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0003v05A4p2000e0110-e0,1,2,3,4,11,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,110,111,112,113,114,r0,1,8,a28,29,2A,2B,2C,2D,m4,l8,9,A,B,C,D,E,sfw')
2012-07-08 12:03:46,915 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:46,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-08 12:03:46,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-08 12:03:46,916 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-07-08 12:03:46,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-08 12:03:46,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:46,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-08 12:03:46,917 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-07-08 12:03:46,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd00000271sv0000103Csd000030B7bc0Bsc40i00')
2012-07-08 12:03:46,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd00000264sv0000103Csd000030B7bc0Csc05i00')
2012-07-08 12:03:46,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2012-07-08 12:03:46,935 DEBUG: got handler kmod:i2c_nforce2([KernelModuleHandler, free, enabled] nForce2/3/4/5xx SMBus driver)
2012-07-08 12:03:46,936 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nv_tco'}
2012-07-08 12:03:46,942 DEBUG: got handler kmod:nv_tco([KernelModuleHandler, free, enabled] TCO timer driver for NV chipsets)
2012-07-08 12:03:46,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.3D:bd11/22/2007:svnHewlett-Packard:pnPresarioV6000(RM484EA#ABU):pvrRev1:rvnQuanta:rn30B7:rvr65.2B:cvnQuanta:ct10:cvrN/A:')
2012-07-08 12:03:46,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd000002F9sv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:46,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-07-08 12:03:46,972 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:46,972 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:46,972 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-08 12:03:46,973 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-07-08 12:03:46,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:HPQ0006:')
2012-07-08 12:03:46,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'usb:v05A4p2000d1110dc00dsc00dp00ic03isc01ip02')
2012-07-08 12:03:46,973 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-08 12:03:46,974 DEBUG: got handler kmod:usbhid([KernelModuleHandler, free, enabled] USB HID core driver)
2012-07-08 12:03:46,974 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-08 12:03:46,980 DEBUG: got handler kmod:usbmouse([KernelModuleHandler, free, disabled] USB HID Boot Protocol mouse driver)
2012-07-08 12:03:46,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'usb:v058Fp6387d0103dc00dsc00dp00ic08isc06ip50')
2012-07-08 12:03:46,983 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-07-08 12:03:46,994 DEBUG: got handler kmod:uas([KernelModuleHandler, free, enabled] uas)
2012-07-08 12:03:46,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-08 12:03:46,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd00000260sv0000103Csd000030B7bc06sc01i00')
2012-07-08 12:03:47,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-07-08 12:03:47,002 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:47,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:47,002 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-08 12:03:47,002 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-07-08 12:03:47,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd000002FEsv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,008 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd00000266sv0000103Csd000030B7bc01sc01i85')
2012-07-08 12:03:47,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2012-07-08 12:03:47,026 DEBUG: got handler kmod:sata_nv([KernelModuleHandler, free, enabled] low-level driver for NVIDIA nForce SATA controller)
2012-07-08 12:03:47,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd000002F0sv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-08 12:03:47,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd00000265sv0000103Csd000030B7bc01sc01i8a')
2012-07-08 12:03:47,038 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2012-07-08 12:03:47,049 DEBUG: got handler kmod:pata_amd([KernelModuleHandler, free, enabled] low-level driver for AMD and Nvidia PATA IDE)
2012-07-08 12:03:47,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd000002FAsv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'platform:pcspkr')
2012-07-08 12:03:47,056 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-08 12:03:47,065 DEBUG: got handler kmod:pcspkr([KernelModuleHandler, free, disabled] PC Speaker beeper driver)
2012-07-08 12:03:47,065 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-08 12:03:47,065 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:47,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd000002F8sv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'hid:b0003g0000v000005A4p00002000')
2012-07-08 12:03:47,149 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_ortek'}
2012-07-08 12:03:47,155 DEBUG: got handler kmod:hid_ortek([KernelModuleHandler, free, enabled] hid_ortek)
2012-07-08 12:03:47,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2012-07-08 12:03:47,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2012-07-08 12:03:47,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'platform:hp-wmi')
2012-07-08 12:03:47,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-08 12:03:47,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'x86cpu:vendor:0002:family:000F:model:0048:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0017,0018,0019,001A,001C,0020,0021,0022,0023,0024,0025,0026,0027,0028,0029,002B,002C,002D,002E,002F,0030,0031,0034,0036,0037,0038,0039,003B,003D,003E,003F,0064,006A,0071,007A,0080,008D,00C0,00C1,00C2,00C3,00C4')
2012-07-08 12:03:47,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_amd'}
2012-07-08 12:03:47,172 DEBUG: got handler kmod:kvm_amd([KernelModuleHandler, free, enabled] kvm_amd)
2012-07-08 12:03:47,172 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2012-07-08 12:03:47,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:47,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-08 12:03:47,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-08 12:03:47,173 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:47,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:47,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'pci:v000010DEd0000026Esv0000103Csd000030B7bc0Csc03i20')
2012-07-08 12:03:47,179 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0003v05A4p2000e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2012-07-08 12:03:47,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:47,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:47,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-08 12:03:47,180 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-07-08 12:03:47,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-08 12:03:47,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-08 12:03:47,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-08 12:03:47,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-08 12:03:47,181 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-07-08 12:03:47,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8da0aec> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-07-08 12:03:47,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-07-08 12:03:47,187 DEBUG: got handler kmod:hp_wmi([KernelModuleHandler, free, enabled] HP laptop WMI hotkeys driver)
2012-07-08 12:03:47,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd0000027Esv00000000sd00000000bc05sc00i00')
2012-07-08 12:03:47,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-07-08 12:03:47,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-08 12:03:47,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-08 12:03:47,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-08 12:03:47,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd00000269sv0000103Csd000030B7bc06sc80i00')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'usb:v05A4p2000d1110dc00dsc00dp00ic03isc01ip01')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:SYN012A:SYN0100:SYN0002:PNP0F13:')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-08 12:03:47,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'platform:eisa')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'platform:NV_TCO')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd0000026Csv0000103Csd000030B7bc04sc03i00')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd000002FFsv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-08 12:03:47,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd00000244sv0000103Csd000030B7bc03sc00i00')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd00000270sv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd0000027Fsv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0003v05A4p2000e0110-e0,1,2,3,4,11,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,110,111,112,113,114,r0,1,8,a28,29,2A,2B,2C,2D,m4,l8,9,A,B,C,D,E,sfw')
2012-07-08 12:03:47,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd00000271sv0000103Csd000030B7bc0Bsc40i00')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd00000264sv0000103Csd000030B7bc0Csc05i00')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.3D:bd11/22/2007:svnHewlett-Packard:pnPresarioV6000(RM484EA#ABU):pvrRev1:rvnQuanta:rn30B7:rvr65.2B:cvnQuanta:ct10:cvrN/A:')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd000002F9sv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:HPQ0006:')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'usb:v05A4p2000d1110dc00dsc00dp00ic03isc01ip02')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'usb:v058Fp6387d0103dc00dsc00dp00ic08isc06ip50')
2012-07-08 12:03:47,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd00000260sv0000103Csd000030B7bc06sc01i00')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd000002FEsv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd00000266sv0000103Csd000030B7bc01sc01i85')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd000002F0sv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd00000265sv0000103Csd000030B7bc01sc01i8a')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd000002FAsv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'platform:pcspkr')
2012-07-08 12:03:47,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd000002F8sv0000103Csd000030B7bc05sc00i00')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'hid:b0003g0000v000005A4p00002000')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'x86cpu:vendor:0002:family:000F:model:0048:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0017,0018,0019,001A,001C,0020,0021,0022,0023,0024,0025,0026,0027,0028,0029,002B,002C,002D,002E,002F,0030,0031,0034,0036,0037,0038,0039,003B,003D,003E,003F,0064,006A,0071,007A,0080,008D,00C0,00C1,00C2,00C3,00C4')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'pci:v000010DEd0000026Esv0000103Csd000030B7bc0Csc03i20')
2012-07-08 12:03:47,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0003v05A4p2000e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2012-07-08 12:03:47,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-08 12:03:47,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8da0e0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-07-08 12:03:47,234 DEBUG: handler kmod:mac_hid previously unseen
2012-07-08 12:03:47,234 DEBUG: handler kmod:mac_hid previously unused
2012-07-08 12:03:47,235 DEBUG: handler kmod:nvidia_173 previously unseen
2012-07-08 12:03:47,235 DEBUG: handler kmod:nvidia_173_updates previously unseen
2012-07-08 12:03:47,235 DEBUG: handler kmod:i2c_nforce2 previously unseen
2012-07-08 12:03:47,235 DEBUG: handler kmod:i2c_nforce2 previously unused
2012-07-08 12:03:47,235 DEBUG: handler kmod:nvidia_current previously unseen
2012-07-08 12:03:47,235 DEBUG: handler kmod:usbmouse previously unseen
2012-07-08 12:03:47,235 DEBUG: handler kmod:usbkbd previously unseen
2012-07-08 12:03:47,235 DEBUG: handler kmod:nv_tco previously unseen
2012-07-08 12:03:47,235 DEBUG: handler kmod:nv_tco previously unused
2012-07-08 12:03:47,235 DEBUG: handler kmod:forcedeth previously unseen
2012-07-08 12:03:47,236 DEBUG: handler kmod:forcedeth previously unused
2012-07-08 12:03:47,236 DEBUG: handler kmod:nvidia_current_updates previously unseen
2012-07-08 12:03:47,236 DEBUG: handler kmod:kvm_amd previously unseen
2012-07-08 12:03:47,236 DEBUG: handler kmod:pcspkr previously unseen
2012-07-08 12:03:47,236 DEBUG: handler kmod:nvidia_96 previously unseen
2012-07-08 12:03:47,236 DEBUG: handler kmod:hid_ortek previously unseen
2012-07-08 12:03:47,236 DEBUG: handler kmod:hid_ortek previously unused
2012-07-08 12:03:47,236 DEBUG: handler kmod:uas previously unseen
2012-07-08 12:03:47,236 DEBUG: handler kmod:sata_nv previously unseen
2012-07-08 12:03:47,236 DEBUG: handler kmod:sata_nv previously unused
2012-07-08 12:03:47,237 DEBUG: handler kmod:usbhid previously unseen
2012-07-08 12:03:47,237 DEBUG: handler kmod:usbhid previously unused
2012-07-08 12:03:47,237 DEBUG: handler kmod:k8temp previously unseen
2012-07-08 12:03:47,237 DEBUG: handler kmod:k8temp previously unused
2012-07-08 12:03:47,237 DEBUG: handler kmod:pata_amd previously unseen
2012-07-08 12:03:47,237 DEBUG: handler kmod:pata_amd previously unused
2012-07-08 12:03:47,237 DEBUG: handler kmod:snd_hda_intel previously unseen
2012-07-08 12:03:47,237 DEBUG: handler kmod:snd_hda_intel previously unused
2012-07-08 12:03:47,237 DEBUG: handler kmod:nouveau previously unseen
2012-07-08 12:03:47,237 DEBUG: handler kmod:nouveau previously unused
2012-07-08 12:03:47,237 DEBUG: handler kmod:nvidia_96_updates previously unseen
2012-07-08 12:03:47,238 DEBUG: handler kmod:hp_wmi previously unseen
2012-07-08 12:03:47,238 DEBUG: handler kmod:hp_wmi previously unused
2012-07-08 12:03:47,238 DEBUG: handler kmod:nvidiafb previously unseen
2012-07-08 12:03:47,238 DEBUG: writing back check cache /var/cache/jockey/check
2012-07-08 12:03:47,238 DEBUG: kmod:mac_hid is already enabled or not available, not announcing
2012-07-08 12:03:47,238 DEBUG: kmod:i2c_nforce2 is already enabled or not available, not announcing
2012-07-08 12:03:47,238 DEBUG: kmod:nv_tco is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:forcedeth is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:kvm_amd is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:hid_ortek is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:uas is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:sata_nv is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:usbhid is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:k8temp is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:pata_amd is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:snd_hda_intel is already enabled or not available, not announcing
2012-07-08 12:03:47,239 DEBUG: kmod:nouveau is already enabled or not available, not announcing
2012-07-08 12:03:47,240 DEBUG: kmod:hp_wmi is already enabled or not available, not announcing
```

---

### Post by AndresC on 2012-12-02
Hi, 

Just the same, every seems to work fine, but no two finger scroll.

I installed a Mythbuntu distro.

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

Linux ariasnunes 3.2.0-34-generic #53-Ubuntu SMP Thu Nov 15 10:48:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```The thing is that "Mouse and Touchpad" do not show anything in the pulldown menu next to device, and the pad is not recognized as a touch pad.




```
Bus 002 Device 005: ID 05a4:2000 Ortek Technology, Inc. WKB-2000 Wireless Keyboard with Touchpad
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05a4 Ortek Technology, Inc.
  idProduct          0x2000 WKB-2000 Wireless Keyboard with Touchpad
  bcdDevice            2.01
  iManufacturer           1      
  iProduct                2                 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      54
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     202
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled
```

It seems that in kernel 2.6.32.3 a patch was provided, and though it works, the functionality is not complete.

Mine is bought in Spain and reselled as Inves at some deparment store.

---

