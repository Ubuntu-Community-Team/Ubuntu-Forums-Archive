---
title: "Current LTS Nvidia drivers so old they fail"
date: 2013-02-09
forum: Hardware
---

### Post by LancerNZ on 2013-02-09
Ubuntu: 12.04-LTS - 32 bit
Driver: NVidia 295.40
Card: Evo-Nvidia GTX580 classified
Desired program: Latest Blender (test build) 2.66

I'm using LTS version of Ubuntu because I've had the bad experience of being on my own earlier on when a non-LTS expired and I was only given "you should upgrade" argument to any problem I had (usually graphics drivers versus kernel related).

So, LTS it is (I could do with support and not wanting to regularly reinstall) but that's backfiring on me big time. You see, the program I most want to run is Blender. They have a test build here: [http://download.blender.org/release/Blender2.66/](http://download.blender.org/release/Blender2.66/) I'm wanting to run the blender-2.66-testbuild1-linux-glibc211-i686.tar.bz2 version; 32 bit because I am sitting on a host of 32 bit programs I don't want to loose if any don't have good 64 bit versions (unlikely but possible - whose gamble is it to try?).

To cut all this short, I have found that my program works, but when I enable 3D hardware acceration (known as "Cycles") the graphics card (Nvidia 580GTX) freaks out.

Now, I've approached the Blender developers about it not working and they say it's because I'm using an outdated Nvidia driver. They are using Ubuntu 12.10 with the 310.90 Nvidia driver, whereas what I'm using: the current 12.04 LTS only offers the 295.40 driver for Nvidia.

So, yes... Ubuntu LTS is running outdated drivers. So outdated it seems, that I can't run new versions of my main program, Blender. Their devs are clearly pointing the finger at Ubuntu saying "Ubuntu LTS - why you so old?"

I had a go at updating the driver to the "experimental" one. There was a conflict with the current driver and I was then locked out with blank screen when I tried to restart. I needed some emergency prior-kernel / reinstall current (old) drivers to get back in action.

What gives with these ancient non-working drivers? Who should I go to in terms of the LTS and getting Blender running? Seems like everyone is going to blame every other third party for why they shouldn't do anything.

LTS... I'm not happy.

Blender bug tracker thread (closed because they say this is an Ubuntu using outdated Nvidia driver issue) here: [http://projects.blender.org/tracker/index.php?func=detail&aid=34173](http://projects.blender.org/tracker/index.php?func=detail&aid=34173)

P.S. The previous Blender 2.65 has no issue and works perfectly. I've pointed this out to the devs but they seem to think that any changes not working in the next release are entirely the fault of the driver I happen to be running. In other words; the one currently on offer through the LTS repos.

---

### Post by BicyclerBoy on 2013-02-09
My 10.04 LTS HTPC runs (pinned) 295..
My 12.04 LTS runs kernel 3.5 & nVidia 313..

LTS is meant to be stable & not use the latest drivers. Any one can obtain the latest driver from nVidia website.

304 & 310 are in the std repos for 12.04 LTS in precise-updates..
May be you need to run synaptic & select proprietary drivers & proposed updates.

You can get 313 from xorg-edgers or x-swat ppa but it will likely hit 12.04 in months..
Beware xorg-edgers updates kernel & all xorg packages, you should not pick & chose.. 

Note: 64 bit OS can run 32bit apps (even windows can). The default 32 bit kernel is PAE & is not limited to 3.2GB like WinXP 32bit.

---

### Post by LancerNZ on 2013-02-09
Great response - thanks. I'm currently performing a full backup before I play so I'll try searching for "updates" repos once that's done (was also going to try the GUI hardware updater "Jockey" rather than synaptic because it might sort the kernel for me, not just the nvidia driver and therefore be more compatable).

So - if I install 64bit linux, I won't hit problems if something's only compiled as 32bit? Is that right?!?


Edit: installing nvidia-experimental-310 (from repos) is what locked me out before. It had a conflict, failed to fully install and ended up with a kernel versus driver missmatch.

---

### Post by pqwoerituytrueiwoq on 2013-02-09
> **LancerNZ said:**
> Great response - thanks. I'm currently performing a full backup before I play so I'll try searching for "updates" repos once that's done (was also going to try the GUI hardware updater "Jockey" rather than synaptic because it might sort the kernel for me, not just the nvidia driver and therefore be more compatable).

So - if I install 64bit linux, I won't hit problems if something's only compiled as 32bit? Is that right?!?
you will just need to instal the ia32-libs package, it will be a dependency of a 32bit app packaged for 64bit

---

### Post by LancerNZ on 2013-02-09
Through Jockey install of 310:

Sorry, installation of this driver failed. Please have a look at the log files for details: /var/log/jockey.log

```
2013-02-10 15:40:44,039 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c>
2013-02-10 15:40:44,905 DEBUG: reading modalias file /lib/modules/3.2.0-37-generic-pae/modules.alias
2013-02-10 15:40:44,988 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-10 15:40:45,001 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-10 15:40:45,034 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-10 15:40:45,071 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-10 15:40:45,073 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-10 15:40:45,073 DEBUG: cdv.available: falling back to default
2013-02-10 15:40:45,344 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-02-10 15:40:45,345 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-10 15:40:45,350 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-10 15:40:45,355 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-10 15:40:45,355 DEBUG: fglrx.available: falling back to default
2013-02-10 15:40:45,469 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-10 15:40:45,472 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-10 15:40:45,493 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-10 15:40:45,493 DEBUG: fglrx.available: falling back to default
2013-02-10 15:40:45,578 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-10 15:40:45,580 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-10 15:40:45,585 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-10 15:40:45,586 DEBUG: fglrx.available: falling back to default
2013-02-10 15:40:45,695 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-02-10 15:40:45,695 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-10 15:40:45,705 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-10 15:40:45,711 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-10 15:40:45,712 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:45,821 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-10 15:40:45,870 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-10 15:40:45,871 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:45,982 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-10 15:40:45,991 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-10 15:40:45,991 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:46,109 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-10 15:40:46,112 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-10 15:40:46,118 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-10 15:40:46,119 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:46,134 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-02-10 15:40:46,135 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-10 15:40:46,138 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-10 15:40:46,143 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-10 15:40:46,144 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:46,255 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-10 15:40:46,258 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-10 15:40:46,263 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-10 15:40:46,264 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:46,373 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-10 15:40:46,376 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-10 15:40:46,397 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-10 15:40:46,398 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:46,484 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-10 15:40:46,487 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-10 15:40:46,508 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-10 15:40:46,508 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:46,601 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-10 15:40:46,601 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-10 15:40:46,605 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-10 15:40:46,606 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-10 15:40:46,606 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-10 15:40:46,606 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-10 15:40:46,623 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-10 15:40:46,656 DEBUG: Software modem not available
2013-02-10 15:40:46,656 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-10 15:40:46,661 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-10 15:40:46,667 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-10 15:40:46,763 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-10 15:40:46,763 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-10 15:40:46,767 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-10 15:40:46,767 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-10 15:40:46,783 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-10 15:40:46,784 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-10 15:40:46,877 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-10 15:40:46,878 DEBUG: Firmware for DVB cards not available
2013-02-10 15:40:46,878 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-10 15:40:46,882 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-10 15:40:46,899 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-10 15:40:46,900 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-10 15:40:46,900 DEBUG: all custom handlers loaded
2013-02-10 15:40:46,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d00000122sv00001458sd0000D000bc03sc80i00')
2013-02-10 15:40:47,065 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-02-10 15:40:47,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-10 15:40:47,156 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:47,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d00001C02sv00001458sd0000B005bc01sc06i01')
2013-02-10 15:40:47,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d00001C44sv00001458sd00005001bc06sc01i00')
2013-02-10 15:40:47,160 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2013-02-10 15:40:47,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-10 15:40:47,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-10 15:40:47,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001458sd00001C3Abc07sc80i00')
2013-02-10 15:40:47,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-02-10 15:40:47,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-10 15:40:47,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:47,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'platform:regulatory')
2013-02-10 15:40:47,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-02-10 15:40:47,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001458sd00005001bc0Csc05i00')
2013-02-10 15:40:47,171 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-10 15:40:47,171 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-10 15:40:47,171 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:47,171 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,171 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-10 15:40:47,171 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-10 15:40:47,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-10 15:40:47,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001458sd00001000bc0Csc00i10')
2013-02-10 15:40:47,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-10 15:40:47,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'platform:eisa')
2013-02-10 15:40:47,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-10 15:40:47,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-02-10 15:40:47,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:47,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v000010DEd00001080sv00003842sd00001588bc03sc00i00')
2013-02-10 15:40:47,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-02-10 15:40:47,426 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:47,426 DEBUG: nvidia_current is not the alternative in use
2013-02-10 15:40:47,326 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-10 15:40:47,433 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:47,541 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:47,541 DEBUG: nvidia_current is not the alternative in use
2013-02-10 15:40:47,529 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-10 15:40:47,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-02-10 15:40:47,553 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:47,553 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-10 15:40:47,541 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-10 15:40:47,556 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-10 15:40:47,562 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:47,662 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:47,662 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-10 15:40:47,650 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-10 15:40:47,662 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-02-10 15:40:47,674 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:47,728 DEBUG: KMH enabled: True
2013-02-10 15:40:47,663 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-10 15:40:47,795 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:47,903 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:47,959 DEBUG: KMH enabled: True
2013-02-10 15:40:47,892 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-10 15:40:48,016 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-02-10 15:40:48,028 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:48,028 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-10 15:40:48,016 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-10 15:40:48,031 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-10 15:40:48,037 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:48,140 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:48,140 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-10 15:40:48,129 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-10 15:40:48,141 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-02-10 15:40:48,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,141 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-02-10 15:40:48,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,141 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2013-02-10 15:40:48,152 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:48,153 DEBUG: nvidia_current is not the alternative in use
2013-02-10 15:40:48,141 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-10 15:40:48,159 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:48,265 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:48,265 DEBUG: nvidia_current is not the alternative in use
2013-02-10 15:40:48,253 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-10 15:40:48,265 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates'}
2013-02-10 15:40:48,276 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:48,339 DEBUG: KMH enabled: True
2013-02-10 15:40:48,265 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-10 15:40:48,404 DEBUG: nvidia.available: falling back to default
2013-02-10 15:40:48,507 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:48,565 DEBUG: KMH enabled: True
2013-02-10 15:40:48,495 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-10 15:40:48,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'usb:v13B1p0020d0001dc00dsc00dp00icFFiscFFipFF')
2013-02-10 15:40:48,634 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb'}
2013-02-10 15:40:48,634 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0303:')
2013-02-10 15:40:48,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-10 15:40:48,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v000010DEd00000E09sv00003842sd00001588bc04sc03i00')
2013-02-10 15:40:48,637 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-10 15:40:48,637 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-10 15:40:48,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-10 15:40:48,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-10 15:40:48,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-10 15:40:48,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-02-10 15:40:48,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001458sd0000A132bc04sc03i00')
2013-02-10 15:40:48,639 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-10 15:40:48,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,639 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-10 15:40:48,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001458sd00005006bc0Csc03i20')
2013-02-10 15:40:48,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-10 15:40:48,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:48,641 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0003v056Ap00D1e0106-e0,1,3,k140,141,14A,14B,14C,ra0,1,18,19,mlsfw')
2013-02-10 15:40:48,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:48,641 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-10 15:40:48,641 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-10 15:40:48,641 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-10 15:40:48,641 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'usb:v056Ap00D1d0106dc00dsc00dp00ic03isc00ip00')
2013-02-10 15:40:48,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wacom'}
2013-02-10 15:40:48,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'wacom', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-10 15:40:48,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0003v045Ep0053e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2013-02-10 15:40:48,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:48,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-10 15:40:48,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-10 15:40:48,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd10/12/2011:svnGigabyteTechnologyCo.,Ltd.:pnZ68X-UD3H-B3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnZ68X-UD3H-B3:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-10 15:40:48,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-02-10 15:40:48,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-10 15:40:48,668 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:48,668 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-02-10 15:40:48,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'usb:v045Ep0053d0300dc00dsc00dp00ic03isc01ip02')
2013-02-10 15:40:48,696 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-10 15:40:48,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,696 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-10 15:40:48,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-10 15:40:48,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-10 15:40:48,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00001B4Bd0000917Asv00001458sd0000B000bc01sc01i8f')
2013-02-10 15:40:48,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'usb:v056Ap00D1d0106dc00dsc00dp00ic03isc01ip02')
2013-02-10 15:40:48,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wacom'}
2013-02-10 15:40:48,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'wacom', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-10 15:40:48,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-10 15:40:48,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001458sd00005006bc0Csc03i20')
2013-02-10 15:40:48,700 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-10 15:40:48,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-02-10 15:40:48,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005001bc06sc04i01')
2013-02-10 15:40:48,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-02-10 15:40:48,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:48,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-10 15:40:48,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-10 15:40:48,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-02-10 15:40:48,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00001283d00008892sv00001458sd00005000bc06sc04i01')
2013-02-10 15:40:48,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'platform:pcspkr')
2013-02-10 15:40:48,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-10 15:40:48,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-10 15:40:48,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'pci:v00001B6Fd00007023sv00001458sd00005007bc0Csc03i30')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-10 15:40:48,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:48,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'input:b0003v056Ap00D1e0106-e0,1,3,k110,111,115,116,145,14A,14D,ra0,1,2F,35,36,39,mlsfw')
2013-02-10 15:40:48,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-10 15:40:48,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-10 15:40:48,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-10 15:40:48,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-10 15:40:48,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x920c02c> about HardwareID('modalias', 'acpi:ICD0001:PNP0C02:')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d00000122sv00001458sd0000D000bc03sc80i00')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d00001C02sv00001458sd0000B005bc01sc06i01')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d00001C44sv00001458sd00005001bc06sc01i00')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001458sd00001C3Abc07sc80i00')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'platform:regulatory')
2013-02-10 15:40:48,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001458sd00005001bc0Csc05i00')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001458sd00001000bc0Csc00i10')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'platform:eisa')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v000010DEd00001080sv00003842sd00001588bc03sc00i00')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'usb:v13B1p0020d0001dc00dsc00dp00icFFiscFFipFF')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0303:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v000010DEd00000E09sv00003842sd00001588bc04sc03i00')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001458sd0000A132bc04sc03i00')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001458sd00005006bc0Csc03i20')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0003v056Ap00D1e0106-e0,1,3,k140,141,14A,14B,14C,ra0,1,18,19,mlsfw')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'usb:v056Ap00D1d0106dc00dsc00dp00ic03isc00ip00')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0003v045Ep0053e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd10/12/2011:svnGigabyteTechnologyCo.,Ltd.:pnZ68X-UD3H-B3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnZ68X-UD3H-B3:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'usb:v045Ep0053d0300dc00dsc00dp00ic03isc01ip02')
2013-02-10 15:40:48,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00001B4Bd0000917Asv00001458sd0000B000bc01sc01i8f')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'usb:v056Ap00D1d0106dc00dsc00dp00ic03isc01ip02')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001458sd00005006bc0Csc03i20')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005001bc06sc04i01')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00001283d00008892sv00001458sd00005000bc06sc04i01')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'platform:pcspkr')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'pci:v00001B6Fd00007023sv00001458sd00005007bc0Csc03i30')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'input:b0003v056Ap00D1e0106-e0,1,3,k110,111,115,116,145,14A,14D,ra0,1,2F,35,36,39,mlsfw')
2013-02-10 15:40:48,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x920d92c> about HardwareID('modalias', 'acpi:ICD0001:PNP0C02:')
2013-02-10 15:40:48,779 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:48,779 DEBUG: nvidia_current is not the alternative in use
2013-02-10 15:40:49,385 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:49,442 DEBUG: KMH enabled: True
2013-02-10 15:40:50,075 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:50,075 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-10 15:40:50,593 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:50,593 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-10 15:40:51,101 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:51,102 DEBUG: nvidia_current is not the alternative in use
2013-02-10 15:40:51,143 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:51,144 DEBUG: nvidia_current is not the alternative in use
2013-02-10 15:40:51,174 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:51,233 DEBUG: KMH enabled: True
2013-02-10 15:40:55,567 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:40:55,568 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-10 15:41:02,539 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:41:02,539 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-10 15:41:07,033 DEBUG: Installing package: nvidia-experimental-310
2013-02-10 15:41:07,977 DEBUG: install progress dpkg-exec 0.000000
2013-02-10 15:41:12,051 DEBUG: install progress nvidia-experimental-310 0.000000
2013-02-10 15:41:12,152 DEBUG: install progress nvidia-experimental-310 10.000000
2013-02-10 15:41:16,854 DEBUG: install progress nvidia-experimental-310 20.000000
2013-02-10 15:41:16,944 DEBUG: install progress nvidia-experimental-310 30.000000
2013-02-10 15:41:17,317 DEBUG: install progress nvidia-settings-experimental-310 30.000000
2013-02-10 15:41:17,415 DEBUG: install progress nvidia-settings-experimental-310 40.000000
2013-02-10 15:41:17,550 DEBUG: install progress man-db 40.000000
2013-02-10 15:41:19,709 DEBUG: install progress bamfdaemon 40.000000
2013-02-10 15:41:19,960 DEBUG: install progress desktop-file-utils 40.000000
2013-02-10 15:41:20,211 DEBUG: install progress gnome-menus 40.000000
2013-02-10 15:41:20,712 DEBUG: Selecting previously unselected package nvidia-experimental-310.
(Reading database ... 340824 files and directories currently installed.)
Unpacking nvidia-experimental-310 (from .../nvidia-experimental-310_310.14-0ubuntu0.3_i386.deb) ...
Unpacking nvidia-settings-experimental-310 (from .../nvidia-settings-experimental-310_310.14-0ubuntu0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-settings-experimental-310_310.14-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/nvidia-settings', which is also in package nvidia-settings-updates 304.43-0ubuntu0.2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-settings-experimental-310_310.14-0ubuntu0.1_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

2013-02-10 15:41:20,712 ERROR: Package failed to install:
Selecting previously unselected package nvidia-experimental-310.
(Reading database ... 340824 files and directories currently installed.)
Unpacking nvidia-experimental-310 (from .../nvidia-experimental-310_310.14-0ubuntu0.3_i386.deb) ...
Unpacking nvidia-settings-experimental-310 (from .../nvidia-settings-experimental-310_310.14-0ubuntu0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-settings-experimental-310_310.14-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/nvidia-settings', which is also in package nvidia-settings-updates 304.43-0ubuntu0.2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-settings-experimental-310_310.14-0ubuntu0.1_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

2013-02-10 15:41:20,832 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-10 15:41:20,833 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-02-10 15:41:20,836 ERROR: xorg:nvidia_experimental_310: get_alternative_by_name(nvidia-experimental-310) returned nothing
2013-02-10 15:41:20,917 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-10 15:41:20,917 DEBUG: nvidia_experimental_310 is not the alternative in use

```

> **pqwoerituytrueiwoq said:**
> you will just need to instal the ia32-libs package, it will be a dependency of a 32bit app packaged for 64bit
Okay - and after that, both 32 bit apps and 64 bit apps will run? Awesome, thanks.

---

### Post by BicyclerBoy on 2013-02-09
FWIK The exptal driver 310 install problem is caused by an omitting to require kernel drivers package.
You can pre-install "linux-headers-generic"..
Could uninstall/remove the old driver & reboot so the kernel module is gone.

The nVidia drivers have exemplary documentation, 2nd to none.

I had no problems with installing 310 or 313..but I had all toolchain/build tools installed.

My advice is never ever update the kernel & any critical driver at the same time..
The AMD/nVidia proprietary video drivers use KMS & require building against the installed kernel headers package.

I believe nVidia 313 is using dkms to build/install so should be a lot more robust with updates.

---

### Post by LancerNZ on 2013-02-09
Thanks **BicyclerBoy**.

Backup done, and now I've just successfully installed the 310.14 driver (through Jockey) but I had to deactivate the previous driver before it would allow me (Sounds simple, yet I thought such things would be automatic).

New Blender version I want still not wqorking, but I'm going back to their bugtracker to say the new driver made no difference... from a few I've been reading I think people on 32 bit systems have had problems ith their latest test build, including Win32 users.

---

