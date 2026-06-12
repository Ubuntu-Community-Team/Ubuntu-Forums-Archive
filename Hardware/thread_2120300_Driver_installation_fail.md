---
title: "Driver installation fail"
date: 2013-02-26
forum: Hardware
---

### Post by Parckwart on 2013-02-26
Hello! I tried to install a "Video driver for the AMD graphics accelerators" in "Additional Drivers". I wasn't able to activate this driver. Heres the jockey.log. Has someone maybe a solve for the issue? Thanks :) 

> 2013-02-26 12:21:28,303 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488>
2013-02-26 12:21:30,448 DEBUG: reading modalias file /lib/modules/3.5.0-25-generic/modules.alias
2013-02-26 12:21:30,536 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-26 12:21:30,536 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-26 12:21:30,600 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-26 12:21:30,633 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-26 12:21:30,634 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-26 12:21:30,671 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-26 12:21:30,671 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-26 12:21:30,688 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-26 12:21:30,689 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-26 12:21:30,689 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-26 12:21:30,689 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-26 12:21:30,691 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 12, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2013-02-26 12:21:30,691 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-26 12:21:30,698 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-26 12:21:30,703 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-26 12:21:30,798 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-26 12:21:30,798 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-26 12:21:30,804 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-26 12:21:30,826 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-26 12:21:30,827 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-26 12:21:30,827 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-26 12:21:30,903 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-26 12:21:30,903 DEBUG: Firmware for DVB cards not available
2013-02-26 12:21:30,904 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-26 12:21:30,926 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-26 12:21:31,064 DEBUG: Software modem not available
2013-02-26 12:21:31,064 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-26 12:21:31,070 WARNING: Invalid custom handler module /usr/share/jockey/handlers/fglrx.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/fglrx.py", line 11, in <module>
    from NvidiaDetector.alternatives import Alternatives
ImportError: No module named NvidiaDetector.alternatives
2013-02-26 12:21:31,071 DEBUG: all custom handlers loaded
2013-02-26 12:21:31,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00001458sd0000026Fbc06sc04i01')
2013-02-26 12:21:31,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-26 12:21:31,253 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-26 12:21:31,378 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-26 12:21:31,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003EBsv00001458sd00000C11bc0Csc05i00')
2013-02-26 12:21:31,382 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2013-02-26 12:21:31,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003F0sv00001458sd0000A002bc04sc03i00')
2013-02-26 12:21:31,385 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-26 12:21:31,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'usb:v1307p0163d0100dc00dsc00dp00ic08isc06ip50')
2013-02-26 12:21:31,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-26 12:21:31,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-26 12:21:31,397 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-26 12:21:31,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-26 12:21:31,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-26 12:21:31,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-26 12:21:31,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'platform:pcspkr')
2013-02-26 12:21:31,398 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-26 12:21:31,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,398 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-26 12:21:31,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003F2sv00001458sd00005004bc0Csc03i20')
2013-02-26 12:21:31,401 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v00001002d000068BAsv00001787sd00002312bc03sc00i00')
2013-02-26 12:21:31,619 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-02-26 12:21:31,619 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,619 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-02-26 12:21:31,623 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-26 12:21:31,644 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-26 12:21:31,644 DEBUG: got handler kmod:fglrx_updates([KernelModuleHandler, nonfree, disabled] Video driver for the AMD graphics accelerators)
2013-02-26 12:21:31,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-02-26 12:21:31,648 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-26 12:21:31,675 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-26 12:21:31,675 DEBUG: got handler kmod:fglrx([KernelModuleHandler, nonfree, disabled] Video driver for the AMD graphics accelerators)
2013-02-26 12:21:31,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-26 12:21:31,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0400:')
2013-02-26 12:21:31,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003F5sv00001458sd00000C11bc05sc00i00')
2013-02-26 12:21:31,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003F6sv00001458sd0000B002bc01sc01i85')
2013-02-26 12:21:31,683 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2013-02-26 12:21:31,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-26 12:21:31,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,693 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2013-02-26 12:21:31,693 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'usb:v05FEp1011d0300dc00dsc00dp00ic03isc01ip02')
2013-02-26 12:21:31,693 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-26 12:21:31,693 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,693 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-26 12:21:31,693 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'x86cpu:vendor:0002:family:0010:model:0004:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0017,0018,0019,001A,001C,0020,0021,0022,0023,0024,0025,0026,0027,0028,0029,002B,002C,002D,002E,002F,0030,0031,0034,0036,0037,0038,0039,003A,003B,003D,003E,003F,0064,0068,006A,006E,0070,0071,0074,0078,007A,0080,0083,008D,0097,00C0,00C1,00C2,00C3,00C4,00C5,00C6,00C7,00C8,00C9,00CA,00CC,00CD,00E8,0105,0106,0107,0108')
2013-02-26 12:21:31,697 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_amd'}
2013-02-26 12:21:31,697 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_amd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,697 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-02-26 12:21:31,697 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-26 12:21:31,697 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-26 12:21:31,697 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,697 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-26 12:21:31,697 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'input:b0003v05FEp1011e0100-e0,1,2,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D1,D9,110,111,112,113,114,r0,1,6,8,am4,lsfw')
2013-02-26 12:21:31,697 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-26 12:21:31,697 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-26 12:21:31,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-26 12:21:31,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-26 12:21:31,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-26 12:21:31,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-26 12:21:31,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF1:bd12/24/2010:svnGigabyteTechnologyCo.,Ltd.:pnM68MT-D3P:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnM68MT-D3P:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-26 12:21:31,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-26 12:21:31,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-02-26 12:21:31,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-26 12:21:31,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-26 12:21:31,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-26 12:21:31,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'usb:v03EBp3301d0300dc09dsc00dp00ic09isc00ip00')
2013-02-26 12:21:31,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003E1sv00001458sd00000C11bc06sc01i00')
2013-02-26 12:21:31,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-26 12:21:31,715 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-26 12:21:31,715 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,715 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-26 12:21:31,715 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010ECd00008185sv000010ECsd00008225bc02sc00i00')
2013-02-26 12:21:31,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rtl8180'}
2013-02-26 12:21:31,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8180', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-26 12:21:31,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'platform:microcode')
2013-02-26 12:21:31,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-26 12:21:31,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003E2sv00001458sd00005001bc05sc00i00')
2013-02-26 12:21:31,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'hid:b0003g0001v000005FEp00001011')
2013-02-26 12:21:31,756 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-02-26 12:21:31,756 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'usb:v05FEp1011d0300dc00dsc00dp00ic03isc01ip01')
2013-02-26 12:21:31,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-26 12:21:31,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-26 12:21:31,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'platform:regulatory')
2013-02-26 12:21:31,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v000010DEd000003EFsv00001458sd0000E000bc06sc80i00')
2013-02-26 12:21:31,760 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2013-02-26 12:21:31,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-26 12:21:31,766 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-26 12:21:31,766 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,766 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'input:b0003v05FEp1011e0100-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-02-26 12:21:31,766 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-26 12:21:31,766 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,767 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-26 12:21:31,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'pci:v00001002d0000AA58sv00001787sd0000AA58bc04sc03i00')
2013-02-26 12:21:31,770 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-26 12:21:31,770 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ba2488> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00001458sd0000026Fbc06sc04i01')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003EBsv00001458sd00000C11bc0Csc05i00')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003F0sv00001458sd0000A002bc04sc03i00')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'usb:v1307p0163d0100dc00dsc00dp00ic08isc06ip50')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-26 12:21:31,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'platform:pcspkr')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003F2sv00001458sd00005004bc0Csc03i20')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v00001002d000068BAsv00001787sd00002312bc03sc00i00')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0400:')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003F5sv00001458sd00000C11bc05sc00i00')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003F6sv00001458sd0000B002bc01sc01i85')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'usb:v05FEp1011d0300dc00dsc00dp00ic03isc01ip02')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'x86cpu:vendor:0002:family:0010:model:0004:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0017,0018,0019,001A,001C,0020,0021,0022,0023,0024,0025,0026,0027,0028,0029,002B,002C,002D,002E,002F,0030,0031,0034,0036,0037,0038,0039,003A,003B,003D,003E,003F,0064,0068,006A,006E,0070,0071,0074,0078,007A,0080,0083,008D,0097,00C0,00C1,00C2,00C3,00C4,00C5,00C6,00C7,00C8,00C9,00CA,00CC,00CD,00E8,0105,0106,0107,0108')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'input:b0003v05FEp1011e0100-e0,1,2,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D1,D9,110,111,112,113,114,r0,1,6,8,am4,lsfw')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF1:bd12/24/2010:svnGigabyteTechnologyCo.,Ltd.:pnM68MT-D3P:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnM68MT-D3P:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-26 12:21:31,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'usb:v03EBp3301d0300dc09dsc00dp00ic09isc00ip00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003E1sv00001458sd00000C11bc06sc01i00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010ECd00008185sv000010ECsd00008225bc02sc00i00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'platform:microcode')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003E2sv00001458sd00005001bc05sc00i00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'hid:b0003g0001v000005FEp00001011')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'usb:v05FEp1011d0300dc00dsc00dp00ic03isc01ip01')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'platform:regulatory')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v000010DEd000003EFsv00001458sd0000E000bc06sc80i00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'input:b0003v05FEp1011e0100-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'pci:v00001002d0000AA58sv00001787sd0000AA58bc04sc03i00')
2013-02-26 12:21:31,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1ef8a28> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-26 12:21:39,545 DEBUG: Installing package: fglrx
2013-02-26 12:21:41,163 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.000000
2013-02-26 12:21:41,164 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.000000
2013-02-26 12:21:41,260 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.000000
2013-02-26 12:21:41,297 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.000000
2013-02-26 12:21:41,336 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.002881
2013-02-26 12:21:41,423 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.079994
2013-02-26 12:21:41,424 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.079994
2013-02-26 12:21:41,460 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.081288
2013-02-26 12:21:41,961 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 0.921790
2013-02-26 12:21:42,462 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 1.834889
2013-02-26 12:21:42,963 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 2.585049
2013-02-26 12:21:43,464 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 3.472336
2013-02-26 12:21:43,966 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 4.364463
2013-02-26 12:21:44,075 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 4.554423
2013-02-26 12:21:44,076 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 4.554423
2013-02-26 12:21:44,111 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 4.555692
2013-02-26 12:21:44,142 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 4.614103
2013-02-26 12:21:44,142 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 4.614103
2013-02-26 12:21:44,178 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 4.615398
2013-02-26 12:21:44,680 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 5.536563
2013-02-26 12:21:45,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 6.430303
2013-02-26 12:21:45,682 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 7.322429
2013-02-26 12:21:46,183 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 8.217782
2013-02-26 12:21:46,685 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 9.111522
2013-02-26 12:21:47,186 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 10.006875
2013-02-26 12:21:47,687 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 10.900615
2013-02-26 12:21:48,189 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 11.795968
2013-02-26 12:21:48,690 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 12.688094
2013-02-26 12:21:49,191 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 13.583447
2013-02-26 12:21:49,692 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 14.477187
2013-02-26 12:21:50,194 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 15.372540
2013-02-26 12:21:50,695 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 16.264667
2013-02-26 12:21:51,196 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 17.158406
2013-02-26 12:21:51,697 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 18.053759
2013-02-26 12:21:52,199 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 18.947499
2013-02-26 12:21:52,700 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 19.841239
2013-02-26 12:21:53,201 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 20.730139
2013-02-26 12:21:53,702 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 21.623879
2013-02-26 12:21:54,203 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 22.511165
2013-02-26 12:21:54,705 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 23.296817
2013-02-26 12:21:55,206 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 24.230888
2013-02-26 12:21:55,707 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 25.126241
2013-02-26 12:21:56,209 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 26.019981
2013-02-26 12:21:56,710 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 26.913721
2013-02-26 12:21:57,211 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 27.807461
2013-02-26 12:21:57,713 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 28.702814
2013-02-26 12:21:58,214 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 29.596554
2013-02-26 12:21:58,715 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 30.491907
2013-02-26 12:21:59,216 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 31.384033
2013-02-26 12:21:59,717 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 32.279386
2013-02-26 12:22:00,219 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 33.171513
2013-02-26 12:22:00,720 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 34.065252
2013-02-26 12:22:01,221 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 34.957379
2013-02-26 12:22:01,722 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 35.851119
2013-02-26 12:22:02,224 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 36.746472
2013-02-26 12:22:02,725 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 37.588587
2013-02-26 12:22:03,226 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 38.479101
2013-02-26 12:22:03,728 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 39.371227
2013-02-26 12:22:04,229 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 40.202050
2013-02-26 12:22:04,730 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 40.840897
2013-02-26 12:22:05,231 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 41.744316
2013-02-26 12:22:05,732 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 42.455759
2013-02-26 12:22:06,234 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 43.105898
2013-02-26 12:22:06,735 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 43.765717
2013-02-26 12:22:07,236 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 44.443281
2013-02-26 12:22:07,738 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 45.107939
2013-02-26 12:22:08,239 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 45.751626
2013-02-26 12:22:08,740 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 46.225921
2013-02-26 12:22:09,242 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 46.427577
2013-02-26 12:22:09,743 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 46.751840
2013-02-26 12:22:10,244 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 47.313250
2013-02-26 12:22:10,746 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 47.832716
2013-02-26 12:22:11,247 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 48.400580
2013-02-26 12:22:11,749 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 49.050719
2013-02-26 12:22:12,250 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 49.704085
2013-02-26 12:22:12,751 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 50.346158
2013-02-26 12:22:13,252 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 51.020496
2013-02-26 12:22:13,754 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 51.701287
2013-02-26 12:22:14,255 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 52.364332
2013-02-26 12:22:14,756 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 53.019311
2013-02-26 12:22:15,257 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 53.695262
2013-02-26 12:22:15,759 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 54.576096
2013-02-26 12:22:16,260 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 55.352068
2013-02-26 12:22:16,762 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 56.281300
2013-02-26 12:22:17,263 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 57.181492
2013-02-26 12:22:17,764 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 58.073619
2013-02-26 12:22:18,266 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 58.968972
2013-02-26 12:22:18,767 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 59.686868
2013-02-26 12:22:19,269 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 60.399923
2013-02-26 12:22:19,770 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 61.104913
2013-02-26 12:22:20,271 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 61.817969
2013-02-26 12:22:20,773 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 62.524572
2013-02-26 12:22:21,274 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 63.224722
2013-02-26 12:22:21,775 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 63.965203
2013-02-26 12:22:22,277 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 64.702458
2013-02-26 12:22:22,778 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 65.434873
2013-02-26 12:22:23,280 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 66.164061
2013-02-26 12:22:23,781 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 66.906155
2013-02-26 12:22:24,283 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 67.717619
2013-02-26 12:22:24,784 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 68.612972
2013-02-26 12:22:25,285 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 69.506712
2013-02-26 12:22:25,787 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 70.400452
2013-02-26 12:22:26,288 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 71.294192
2013-02-26 12:22:26,790 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 72.186318
2013-02-26 12:22:27,291 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 73.081671
2013-02-26 12:22:27,792 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 73.975411
2013-02-26 12:22:28,294 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 74.870764
2013-02-26 12:22:28,795 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 75.764504
2013-02-26 12:22:29,297 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 76.587247
2013-02-26 12:22:29,798 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 77.484213
2013-02-26 12:22:30,299 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 78.379566
2013-02-26 12:22:30,801 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 79.273306
2013-02-26 12:22:31,302 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 80.167046
2013-02-26 12:22:31,803 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 81.062399
2013-02-26 12:22:32,305 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 81.956139
2013-02-26 12:22:32,806 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 82.849878
2013-02-26 12:22:33,308 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 83.743618
2013-02-26 12:22:33,809 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 84.638971
2013-02-26 12:22:34,310 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 85.531098
2013-02-26 12:22:34,811 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 86.426451
2013-02-26 12:22:35,313 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 87.320190
2013-02-26 12:22:35,814 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 88.215543
2013-02-26 12:22:36,315 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 89.107670
2013-02-26 12:22:36,817 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 90.001410
2013-02-26 12:22:37,318 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 90.895149
2013-02-26 12:22:37,819 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 91.790502
2013-02-26 12:22:38,321 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 92.684242
2013-02-26 12:22:38,817 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 93.561848
2013-02-26 12:22:38,818 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 93.561848
2013-02-26 12:22:38,883 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 93.561848
2013-02-26 12:22:39,616 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 94.845678
2013-02-26 12:22:40,117 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 95.739418
2013-02-26 12:22:40,618 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 96.633158
2013-02-26 12:22:41,120 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 97.528511
2013-02-26 12:22:41,621 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 98.422251
2013-02-26 12:22:42,122 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 99.315990
2013-02-26 12:22:42,509 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:15981L> 100.000000
2013-02-26 12:22:42,909 DEBUG: install progress dpkg-exec 0.000000
2013-02-26 12:22:43,502 DEBUG: install progress dkms 0.000000
2013-02-26 12:22:43,603 DEBUG: install progress dkms 4.000000
2013-02-26 12:22:43,904 DEBUG: install progress dkms 8.000000
2013-02-26 12:22:43,968 DEBUG: install progress dkms 12.000000
2013-02-26 12:22:44,376 DEBUG: install progress libc6-i386 12.000000
2013-02-26 12:22:44,377 DEBUG: install progress libc6-i386 16.000000
2013-02-26 12:22:45,009 DEBUG: install progress libc6-i386 20.000000
2013-02-26 12:22:45,056 DEBUG: install progress libc6-i386 24.000000
2013-02-26 12:22:45,370 DEBUG: install progress lib32gcc1 24.000000
2013-02-26 12:22:45,371 DEBUG: install progress lib32gcc1 28.000000
2013-02-26 12:22:45,590 DEBUG: install progress lib32gcc1 32.000000
2013-02-26 12:22:45,638 DEBUG: install progress lib32gcc1 36.000000
2013-02-26 12:22:46,020 DEBUG: install progress fglrx 36.000000
2013-02-26 12:22:46,121 DEBUG: install progress fglrx 40.000000
2013-02-26 12:22:50,429 DEBUG: install progress fglrx 44.000000
2013-02-26 12:22:50,502 DEBUG: install progress fglrx 48.000000
2013-02-26 12:22:50,797 DEBUG: install progress fglrx-amdcccle 48.000000
2013-02-26 12:22:50,897 DEBUG: install progress fglrx-amdcccle 52.000000
2013-02-26 12:22:51,854 DEBUG: install progress fglrx-amdcccle 56.000000
2013-02-26 12:22:51,900 DEBUG: install progress fglrx-amdcccle 60.000000
2013-02-26 12:22:51,953 DEBUG: install progress man-db 60.000000
2013-02-26 12:22:53,295 DEBUG: install progress ureadahead 60.000000
2013-02-26 12:22:53,629 DEBUG: install progress dpkg-exec 60.000000
2013-02-26 12:22:53,701 DEBUG: install progress dkms 60.000000
2013-02-26 12:22:54,497 DEBUG: install progress dkms 64.000000
2013-02-26 12:22:54,566 DEBUG: install progress dkms 68.000000
2013-02-26 12:22:54,615 DEBUG: install progress libc6-i386 68.000000
2013-02-26 12:22:54,710 DEBUG: install progress libc6-i386 72.000000
2013-02-26 12:22:54,812 DEBUG: install progress libc6-i386 76.000000
2013-02-26 12:22:54,938 DEBUG: install progress lib32gcc1 76.000000
2013-02-26 12:22:54,980 DEBUG: install progress lib32gcc1 80.000000
2013-02-26 12:22:55,065 DEBUG: install progress lib32gcc1 84.000000
2013-02-26 12:22:55,140 DEBUG: install progress fglrx 84.000000
2013-02-26 12:22:55,488 DEBUG: install progress fglrx 88.000000
2013-02-26 12:22:57,136 DEBUG: install progress ureadahead 88.000000
2013-02-26 12:22:57,237 DEBUG: install progress bamfdaemon 88.000000
2013-02-26 12:22:57,287 DEBUG: install progress fglrx 92.000000
2013-02-26 12:22:57,840 DEBUG: install progress fglrx-amdcccle 92.000000
2013-02-26 12:22:57,891 DEBUG: install progress fglrx-amdcccle 96.000000
2013-02-26 12:22:57,933 DEBUG: install progress fglrx-amdcccle 100.000000
2013-02-26 12:22:57,985 DEBUG: install progress libc-bin 100.000000
2013-02-26 12:22:58,154 DEBUG: install progress initramfs-tools 100.000000
2013-02-26 12:23:16,206 DEBUG: Selecting previously unselected package dkms.
(Reading database ... 180472 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1.1_all.deb) ...
Selecting previously unselected package libc6-i386.
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu20_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.7.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a9.000-0ubuntu3_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a9.000-0ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up dkms (2.2.0.3-1.1ubuntu1.1) ...
Setting up libc6-i386 (2.15-0ubuntu20) ...
Setting up lib32gcc1 (1:4.7.2-2ubuntu1) ...
Setting up fglrx (2:9.000-0ubuntu3) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-9.000 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-25-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:9.000-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic

2013-02-26 12:23:16,337 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-26 12:23:16,337 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2013-02-26 12:23:31,726 DEBUG: Installing package: fglrx-updates
2013-02-26 12:23:32,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 0.000000
2013-02-26 12:23:32,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 0.000000
2013-02-26 12:23:32,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 0.000000
2013-02-26 12:23:32,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 0.000000
2013-02-26 12:23:32,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 0.016580
2013-02-26 12:23:33,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 0.551026
2013-02-26 12:23:33,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 1.129445
2013-02-26 12:23:34,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 1.739999
2013-02-26 12:23:34,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 2.375922
2013-02-26 12:23:35,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 3.074422
2013-02-26 12:23:35,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 4.009702
2013-02-26 12:23:36,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 4.950056
2013-02-26 12:23:36,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 5.787242
2013-02-26 12:23:37,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 6.729009
2013-02-26 12:23:37,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 7.665980
2013-02-26 12:23:38,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 8.602952
2013-02-26 12:23:38,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 9.539923
2013-02-26 12:23:39,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 10.476895
2013-02-26 12:23:39,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 11.415557
2013-02-26 12:23:40,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 12.354220
2013-02-26 12:23:40,750 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 13.291192
2013-02-26 12:23:41,251 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 14.228163
2013-02-26 12:23:41,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 15.165134
2013-02-26 12:23:42,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 16.103797
2013-02-26 12:23:42,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 17.040769
2013-02-26 12:23:43,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 17.977740
2013-02-26 12:23:43,758 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 18.914711
2013-02-26 12:23:44,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 19.853374
2013-02-26 12:23:44,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 20.790346
2013-02-26 12:23:45,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 21.729008
2013-02-26 12:23:45,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 22.665407
2013-02-26 12:23:46,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 23.604285
2013-02-26 12:23:46,766 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 24.539566
2013-02-26 12:23:47,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 25.381825
2013-02-26 12:23:47,769 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 26.328944
2013-02-26 12:23:48,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 27.267607
2013-02-26 12:23:48,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 28.204578
2013-02-26 12:23:49,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 29.141550
2013-02-26 12:23:49,774 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 29.730117
2013-02-26 12:23:50,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 30.266254
2013-02-26 12:23:50,777 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 30.805773
2013-02-26 12:23:51,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 31.330071
2013-02-26 12:23:51,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 31.850987
2013-02-26 12:23:52,281 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 32.691555
2013-02-26 12:23:52,782 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 33.628527
2013-02-26 12:23:53,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 34.563807
2013-02-26 12:23:53,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 35.502469
2013-02-26 12:23:54,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 36.439441
2013-02-26 12:23:54,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 37.376412
2013-02-26 12:23:55,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 38.313384
2013-02-26 12:23:55,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 39.252046
2013-02-26 12:23:56,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 40.189018
2013-02-26 12:23:56,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 41.125989
2013-02-26 12:23:57,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 42.064652
2013-02-26 12:23:57,794 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 43.001623
2013-02-26 12:23:58,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 43.938595
2013-02-26 12:23:58,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 44.875566
2013-02-26 12:23:59,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 45.813045
2013-02-26 12:23:59,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 46.750017
2013-02-26 12:24:00,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 47.686988
2013-02-26 12:24:00,802 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 48.498804
2013-02-26 12:24:01,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 49.462836
2013-02-26 12:24:01,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 50.399808
2013-02-26 12:24:02,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 51.336779
2013-02-26 12:24:02,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 52.275442
2013-02-26 12:24:03,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 53.212413
2013-02-26 12:24:03,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 54.151076
2013-02-26 12:24:04,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 55.088048
2013-02-26 12:24:04,813 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 56.025019
2013-02-26 12:24:05,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 56.961990
2013-02-26 12:24:05,816 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 57.898962
2013-02-26 12:24:06,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 58.769973
2013-02-26 12:24:06,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 59.762757
2013-02-26 12:24:07,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 60.711567
2013-02-26 12:24:07,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 61.648539
2013-02-26 12:24:08,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 62.587202
2013-02-26 12:24:08,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 63.525507
2013-02-26 12:24:09,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 64.462479
2013-02-26 12:24:09,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 65.399882
2013-02-26 12:24:10,328 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 66.336854
2013-02-26 12:24:10,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 67.077636
2013-02-26 12:24:11,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 68.127924
2013-02-26 12:24:11,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 69.064895
2013-02-26 12:24:12,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 70.001867
2013-02-26 12:24:12,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 70.938838
2013-02-26 12:24:13,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 71.877501
2013-02-26 12:24:13,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 72.814472
2013-02-26 12:24:14,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 73.749752
2013-02-26 12:24:14,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 74.688415
2013-02-26 12:24:15,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 75.625386
2013-02-26 12:24:15,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 76.564049
2013-02-26 12:24:16,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 77.501021
2013-02-26 12:24:16,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 78.437992
2013-02-26 12:24:17,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 79.376655
2013-02-26 12:24:17,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 80.313626
2013-02-26 12:24:18,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 81.250598
2013-02-26 12:24:18,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 82.187569
2013-02-26 12:24:19,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 83.126232
2013-02-26 12:24:19,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 84.063203
2013-02-26 12:24:20,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 85.001866
2013-02-26 12:24:20,855 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 85.938837
2013-02-26 12:24:21,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 86.635646
2013-02-26 12:24:21,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 87.704538
2013-02-26 12:24:22,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 88.369213
2013-02-26 12:24:22,860 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 88.815712
2013-02-26 12:24:23,361 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 89.385674
2013-02-26 12:24:23,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 90.168739
2013-02-26 12:24:24,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 90.664285
2013-02-26 12:24:24,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 91.266382
2013-02-26 12:24:25,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 92.203100
2013-02-26 12:24:25,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 93.138634
2013-02-26 12:24:25,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 93.250415
2013-02-26 12:24:25,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 93.250415
2013-02-26 12:24:26,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 93.251776
2013-02-26 12:24:26,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 94.198895
2013-02-26 12:24:27,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 95.161236
2013-02-26 12:24:27,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 96.099899
2013-02-26 12:24:28,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 97.036870
2013-02-26 12:24:28,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 97.973842
2013-02-26 12:24:29,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 98.912504
2013-02-26 12:24:29,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 99.849476
2013-02-26 12:24:29,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:15991L> 100.000000
2013-02-26 12:24:29,843 DEBUG: install progress dpkg-exec 0.000000
2013-02-26 12:24:30,230 DEBUG: install progress fglrx-amdcccle 0.000000
2013-02-26 12:24:30,315 DEBUG: install progress fglrx-amdcccle 6.250000
2013-02-26 12:24:30,316 DEBUG: install progress fglrx-amdcccle 12.500000
2013-02-26 12:24:30,445 DEBUG: install progress fglrx-amdcccle 18.750000
2013-02-26 12:24:30,785 DEBUG: install progress fglrx 18.750000
2013-02-26 12:24:30,886 DEBUG: install progress fglrx 25.000000
2013-02-26 12:24:31,864 DEBUG: install progress fglrx 31.250000
2013-02-26 12:24:32,427 DEBUG: install progress fglrx 37.500000
2013-02-26 12:24:32,545 DEBUG: install progress bamfdaemon 37.500000
2013-02-26 12:24:32,697 DEBUG: install progress ureadahead 37.500000
2013-02-26 12:24:32,825 DEBUG: install progress initramfs-tools 37.500000
2013-02-26 12:24:45,524 DEBUG: install progress libc-bin 37.500000
2013-02-26 12:24:45,834 DEBUG: install progress dpkg-exec 37.500000
2013-02-26 12:24:46,327 DEBUG: install progress fglrx-updates 37.500000
2013-02-26 12:24:46,427 DEBUG: install progress fglrx-updates 43.750000
2013-02-26 12:24:50,340 DEBUG: install progress fglrx-updates 50.000000
2013-02-26 12:24:50,392 DEBUG: install progress fglrx-updates 56.250000
2013-02-26 12:24:50,577 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2013-02-26 12:24:50,678 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2013-02-26 12:24:51,018 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2013-02-26 12:24:51,066 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2013-02-26 12:24:51,119 DEBUG: install progress ureadahead 75.000000
2013-02-26 12:24:51,409 DEBUG: install progress dpkg-exec 75.000000
2013-02-26 12:24:51,462 DEBUG: install progress fglrx-updates 75.000000
2013-02-26 12:24:51,727 DEBUG: install progress fglrx-updates 81.250000
2013-02-26 12:24:52,565 DEBUG: install progress fglrx-updates 87.500000
2013-02-26 12:24:52,844 DEBUG: install progress bamfdaemon 87.500000
2013-02-26 12:24:53,055 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2013-02-26 12:24:53,122 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2013-02-26 12:24:53,182 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2013-02-26 12:24:53,242 DEBUG: install progress initramfs-tools 100.000000
2013-02-26 12:25:06,033 DEBUG: install progress libc-bin 100.000000
2013-02-26 12:25:08,040 DEBUG: (Reading database ... 181118 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-updates.
(Reading database ... 180833 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a9.000-0ubuntu3_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a9.000-0ubuntu3_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:9.000-0ubuntu3) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-9.000 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-25-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:9.000-0ubuntu3) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2013-02-26 12:25:08,173 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-26 12:25:08,174 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-02-26 12:27:46,851 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-26 12:27:46,852 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-02-26 12:30:29,729 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-26 12:30:29,730 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-02-26 12:33:57,189 DEBUG: Installing package: fglrx
2013-02-26 12:33:58,016 DEBUG: install progress dpkg-exec 0.000000
2013-02-26 12:33:58,258 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2013-02-26 12:33:58,309 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2013-02-26 12:33:58,310 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2013-02-26 12:33:58,455 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2013-02-26 12:33:58,744 DEBUG: install progress fglrx-updates 18.750000
2013-02-26 12:33:58,845 DEBUG: install progress fglrx-updates 25.000000
2013-02-26 12:33:59,475 DEBUG: install progress fglrx-updates 31.250000
2013-02-26 12:33:59,962 DEBUG: install progress fglrx-updates 37.500000
2013-02-26 12:34:00,065 DEBUG: install progress bamfdaemon 37.500000
2013-02-26 12:34:00,191 DEBUG: install progress ureadahead 37.500000
2013-02-26 12:34:00,286 DEBUG: install progress initramfs-tools 37.500000
2013-02-26 12:34:11,463 DEBUG: install progress libc-bin 37.500000
2013-02-26 12:34:11,782 DEBUG: install progress dpkg-exec 37.500000
2013-02-26 12:34:12,259 DEBUG: install progress fglrx 37.500000
2013-02-26 12:34:12,360 DEBUG: install progress fglrx 43.750000
2013-02-26 12:34:16,305 DEBUG: install progress fglrx 50.000000
2013-02-26 12:34:16,357 DEBUG: install progress fglrx 56.250000
2013-02-26 12:34:16,534 DEBUG: install progress fglrx-amdcccle 56.250000
2013-02-26 12:34:16,635 DEBUG: install progress fglrx-amdcccle 62.500000
2013-02-26 12:34:16,984 DEBUG: install progress fglrx-amdcccle 68.750000
2013-02-26 12:34:17,039 DEBUG: install progress fglrx-amdcccle 75.000000
2013-02-26 12:34:17,099 DEBUG: install progress ureadahead 75.000000
2013-02-26 12:34:17,490 DEBUG: install progress dpkg-exec 75.000000
2013-02-26 12:34:17,546 DEBUG: install progress fglrx 75.000000
2013-02-26 12:34:17,833 DEBUG: install progress fglrx 81.250000
2013-02-26 12:34:18,711 DEBUG: install progress fglrx 87.500000
2013-02-26 12:34:19,050 DEBUG: install progress bamfdaemon 87.500000
2013-02-26 12:34:19,260 DEBUG: install progress fglrx-amdcccle 87.500000
2013-02-26 12:34:19,327 DEBUG: install progress fglrx-amdcccle 93.750000
2013-02-26 12:34:19,395 DEBUG: install progress fglrx-amdcccle 100.000000
2013-02-26 12:34:19,455 DEBUG: install progress initramfs-tools 100.000000
2013-02-26 12:34:31,814 DEBUG: install progress libc-bin 100.000000
2013-02-26 12:34:33,219 DEBUG: (Reading database ... 181118 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx.
(Reading database ... 180834 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a9.000-0ubuntu3_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a9.000-0ubuntu3_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:9.000-0ubuntu3) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-9.000 DKMS files...
Building only for 3.5.0-25-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:9.000-0ubuntu3) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2013-02-26 12:34:33,365 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-26 12:34:33,366 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2013-02-26 12:34:43,703 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-26 12:34:43,705 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver

---

### Post by Yellow Pasque on 2013-02-26
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

Do you have linux-headers-generic package installed?

---

### Post by Parckwart on 2013-02-26
I hadn't. But after I did it worked. Thanks a lot!

---

