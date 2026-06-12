---
title: "GT-240M  proprietary driver error"
date: 2011-10-17
forum: Hardware
---

### Post by heian on 2011-10-17
Hi,

Anyone who can help me out of this:

laptop     :  Lenovo y450
video card :  GT-240M

After a clean install Ubuntu 11.10 the screen resolution can be set only to 800x600 or 1024x768.

After installing the recommended proprietary driver, i get an error and the driver will not be installed.  (see error report below)

However, it is possible to install the (post-release updates)(version current updates). But after doing so, the brightness is not adjustable anymore. The bar is there with the moving 'line', but the screen is full bright only, and will not decrease brightness.

Seems this was earlier a well known video-card in more laptops, anyone who got a solution?

Many thanks in advance,

heian

(could not post everything, due to restrictions)
when needed, i will provide more info

'jockey_handler': 'KernelModuleHandler'}
2011-10-17 21:26:11,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d464c> about HardwareID('modalias', 'pci:v00008086d00004237sv00008086sd00001211bc02sc80i00')
2011-10-17 21:26:11,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-10-17 21:26:11,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 21:26:11,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d464c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 21:26:11,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 21:26:11,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 21:26:11,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d464c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 21:26:11,802 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 21:26:11,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 21:26:11,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d464c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-10-17 21:26:11,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c96ec> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv000017AAsd000038FFbc04sc03i00')
2011-10-17 21:26:11,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c96ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 21:26:11,802 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c96ec> about HardwareID('modalias', 
2011-10-17 21:26:13,626 DEBUG: KMH enabled: False
2011-10-17 21:26:13,670 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 21:26:13,670 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 21:27:58,891 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 21:27:58,891 DEBUG: KMH enabled: False
2011-10-17 21:28:08,985 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 21:28:08,985 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-17 21:28:31,601 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 21:28:31,601 DEBUG: KMH enabled: False
2011-10-17 21:28:31,633 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 21:28:31,634 DEBUG: KMH enabled: False
2011-10-17 21:29:40,709 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 21:29:40,710 DEBUG: KMH enabled: False
2011-10-17 21:29:40,775 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 21:29:40,776 DEBUG: KMH enabled: False
2011-10-17 21:29:40,884 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 21:29:40,884 DEBUG: nvidia_current_updates is not the alternative in use

2011-10-17 21:29:41,374 DEBUG: nvidia_current_updates is not the alternative in use

---

