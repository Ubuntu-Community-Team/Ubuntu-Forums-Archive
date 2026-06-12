---
title: "Debating..."
date: 2012-06-11
forum: Hardware
---

### Post by LinXNut on 2012-06-11
Hey guys I have a new laptop. Its a Compaq Presario CQ56. I had windows 7 64-bit installed on it, and I really want Ubuntu. The only thing I am debating over is the switch. I'm more of a person that would have one single OS on the computer rather than dual boot. However, I am a big gamer. I play EVE, Ultima, etc. I know most of the games I play are compatible with Ubuntu, but I wanted to make sure all my hardware is up to snuff. The link about my laptop can be found **[Here]("http://www.notebookcheck.net/Review-HP-Compaq-Presario-CQ56-Notebook.42285.0.html")**. I was just curious if anyone has ideas or suggestions? Thanks.
:popcorn:

---

### Post by hansdown on 2012-06-11
Hi LinXNut.

I would worry about the amount of ram.

You can make a live cd, or usb, and test to see if everything works, before installing.

---

### Post by Bucky Ball on 2012-06-11
> **hansdown said:**
> Hi LinXNut.

I would worry about the amount of ram.

You can make a live cd, or usb, and test to see if everything works, before installing.

+1. When you boot from the install cd that you create there is the options to install or 'Try Ubuntu'. Hit try and you will be taken to the desktop. If everything's working okay hardware-wise, you can install by clicking the icon on the desktop.

If things don't go well, post back and let us know what problems you're getting so we can try and fix things before you install. Sometimes you need to add an option or other tweak to get things running. We'll have a better idea once you boot from the CD. ;)

PS: Think that is the same model as my wife's laptop which worked faultlessly with 8.04 LTS and is now running 10.04 LTS nicely. Install was problem free from memory.

---

### Post by LinXNut on 2012-06-12
Hey guys thanks for the quick reply! I downloaded Ubuntu and booted from a flash drive. Everything seems to work perfectly. Sound, video, commands, boot, etc. The only thing that irks me is the video driver. The driver in use is "radeon", would this be equivalent to the driver in use on my laptop now?
Also, If I full install Ubuntu I will lose my windows 7 64-bit OS. Anyone know where I can get the disk in case I change my mind?

Thanks

---

### Post by TBABill on 2012-06-12
Windows 7 has an option to create a restore disk(s). If you do that in advance you'll be able to reinstall from those if you should either decide you want to start fresh or if you bork the install. And the video driver you were using is open source.  You wouldn't normally install the proprietary driver, if available, until you have the OS installed. It's like Windows in that regard where it will use a default (in this case open source) drive until the OS is running, then allow you to install the proper driver post-install.
 
I would recommend making those disks and maybe even do it twice to be absolutely certain you have a working copy of Windows ready in case you need it. Paying $100+ for a new copy isn't nearly as fun as spending the time up front to create a good backup. I say twice because errors can happen and the odds would decrease greatly by making 2 copies (or if you should lose one or break one).

---

### Post by LinXNut on 2012-06-12
Thanks Guys! Everything is going smoothly so far. I installed Ubuntu and updated and it all seems perfect. One thing I am a little confused with is the proprietary graphics drivers. It notified me that there were 2. The AMD proprietary graphics driver, and the "post-install" update for them. Well I activated the AMD graphics driver, and I think everything became a little more laggy. Also, after I rebooted, I went to install the update for the AMD proprietary driver, and it gave me this log after saying it could not install:

```
2012-06-12 13:56:36,431 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c>
2012-06-12 13:56:37,168 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-06-12 13:56:37,363 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-12 13:56:37,369 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-12 13:56:37,478 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-12 13:56:37,520 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-12 13:56:37,542 DEBUG: Software modem not available
2012-06-12 13:56:37,542 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-12 13:56:37,639 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-12 13:56:37,649 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-12 13:56:37,650 DEBUG: nvidia.available: falling back to default
2012-06-12 13:56:37,801 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 13:56:37,801 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 13:56:37,808 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-12 13:56:37,817 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-12 13:56:37,817 DEBUG: nvidia.available: falling back to default
2012-06-12 13:56:37,874 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-12 13:56:37,880 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-12 13:56:37,887 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-12 13:56:37,888 DEBUG: nvidia.available: falling back to default
2012-06-12 13:56:37,960 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 13:56:37,968 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-12 13:56:37,975 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-12 13:56:37,976 DEBUG: nvidia.available: falling back to default
2012-06-12 13:56:38,005 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 13:56:38,006 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 13:56:38,013 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-12 13:56:38,021 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-12 13:56:38,022 DEBUG: nvidia.available: falling back to default
2012-06-12 13:56:38,061 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 13:56:38,061 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 13:56:38,070 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-12 13:56:38,080 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-12 13:56:38,080 DEBUG: nvidia.available: falling back to default
2012-06-12 13:56:38,107 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 13:56:38,108 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 13:56:38,108 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-12 13:56:38,198 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 215, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package linux-firmware-nonfree does not exist
2012-06-12 13:56:38,223 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-12 13:56:38,232 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-12 13:56:38,239 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-12 13:56:38,240 DEBUG: fglrx.available: falling back to default
2012-06-12 13:56:38,294 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 13:56:38,299 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-12 13:56:38,307 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-12 13:56:38,308 DEBUG: fglrx.available: falling back to default
2012-06-12 13:56:38,370 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-12 13:56:38,371 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-12 13:56:38,379 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-12 13:56:38,380 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-12 13:56:38,380 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-12 13:56:38,380 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-12 13:56:38,388 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-12 13:56:38,388 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-12 13:56:38,412 DEBUG: VMWare Client Tools not available
2012-06-12 13:56:38,413 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-12 13:56:38,423 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-12 13:56:38,451 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-12 13:56:38,451 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-12 13:56:38,451 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-12 13:56:38,461 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-12 13:56:38,469 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-12 13:56:38,526 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-12 13:56:38,526 DEBUG: all custom handlers loaded
2012-06-12 13:56:38,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 13:56:39,355 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-12 13:56:39,408 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:56:39,408 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 13:56:39,355 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 13:56:39,416 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-12 13:56:39,427 DEBUG: fglrx.available: falling back to default
2012-06-12 13:56:39,485 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:56:39,485 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 13:56:39,460 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 13:56:39,485 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-12 13:56:39,510 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:56:39,510 DEBUG: fglrx is not the alternative in use
2012-06-12 13:56:39,485 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 13:56:39,517 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-12 13:56:39,526 DEBUG: fglrx.available: falling back to default
2012-06-12 13:56:39,583 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:56:39,583 DEBUG: fglrx is not the alternative in use
2012-06-12 13:56:39,556 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 13:56:39,584 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-12 13:56:39,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 13:56:39,816 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:39,816 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,816 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 13:56:39,816 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,816 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:39,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:39,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 13:56:39,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 13:56:39,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 13:56:39,873 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-06-12 13:56:39,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 13:56:39,873 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-12 13:56:39,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,874 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-12 13:56:39,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 13:56:39,874 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:39,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 13:56:39,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 13:56:39,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:39,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-06-12 13:56:39,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 13:56:39,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:39,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 13:56:39,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 13:56:39,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:39,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 13:56:39,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 13:56:39,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-06-12 13:56:39,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-06-12 13:56:39,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 13:56:39,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 13:56:39,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 13:56:39,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 13:56:39,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 13:56:39,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 13:56:39,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 13:56:39,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-06-12 13:56:39,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 13:56:39,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 13:56:39,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 13:56:39,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 13:56:39,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 13:56:39,957 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-12 13:56:39,957 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:39,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 13:56:39,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:39,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 13:56:39,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 13:56:39,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:39,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 13:56:39,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:39,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 13:56:39,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 13:56:39,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 13:56:39,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 13:56:39,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:39,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 13:56:39,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 13:56:40,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 13:56:40,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 13:56:40,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:40,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 13:56:40,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 13:56:40,037 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-12 13:56:40,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,038 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-12 13:56:40,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 13:56:40,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 13:56:40,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 13:56:40,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 13:56:40,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-06-12 13:56:40,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 13:56:40,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 13:56:40,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 13:56:40,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 13:56:40,066 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:40,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,067 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 13:56:40,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 13:56:40,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 13:56:40,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 13:56:40,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 13:56:40,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-06-12 13:56:40,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-06-12 13:56:40,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 13:56:40,106 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 13:56:40,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,106 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 13:56:40,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 13:56:40,112 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 13:56:40,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,112 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 13:56:40,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 13:56:40,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f2d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 13:56:40,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 13:56:40,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 13:56:40,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:40,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:40,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 13:56:40,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 13:56:40,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 13:56:40,114 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 13:56:40,119 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'platform:eisa')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 13:56:40,120 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 13:56:40,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68eb7ec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 13:56:40,186 DEBUG: handler xorg:fglrx_updates previously unseen
2012-06-12 13:56:40,187 DEBUG: handler xorg:fglrx previously unseen
2012-06-12 13:56:40,187 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-12 13:56:40,215 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:56:40,215 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 13:56:40,236 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:56:40,236 DEBUG: fglrx is not the alternative in use
2012-06-12 13:56:40,279 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:56:40,280 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 13:57:21,379 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:57:21,380 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 13:57:21,470 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:57:21,470 DEBUG: fglrx is not the alternative in use
2012-06-12 13:57:21,499 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:57:21,499 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 13:57:21,533 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:57:21,534 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 13:57:21,555 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:57:21,555 DEBUG: fglrx is not the alternative in use
2012-06-12 13:57:25,713 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:57:25,713 DEBUG: fglrx is not the alternative in use
2012-06-12 13:57:29,513 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:57:29,513 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 13:57:31,663 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 13:57:31,663 DEBUG: fglrx is not the alternative in use
2012-06-12 13:57:34,931 DEBUG: Shutting down
2012-06-12 14:15:24,158 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c>
2012-06-12 14:15:27,978 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-06-12 14:15:28,133 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-12 14:15:28,138 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-12 14:15:28,237 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-12 14:15:28,267 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-12 14:15:28,286 DEBUG: Software modem not available
2012-06-12 14:15:28,286 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-12 14:15:28,386 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-12 14:15:28,389 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-12 14:15:28,390 DEBUG: nvidia.available: falling back to default
2012-06-12 14:15:28,584 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:15:28,584 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:15:28,587 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-12 14:15:28,591 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-12 14:15:28,592 DEBUG: nvidia.available: falling back to default
2012-06-12 14:15:28,619 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-12 14:15:28,622 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-12 14:15:28,626 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-12 14:15:28,627 DEBUG: nvidia.available: falling back to default
2012-06-12 14:15:28,657 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:15:28,660 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-12 14:15:28,663 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-12 14:15:28,664 DEBUG: nvidia.available: falling back to default
2012-06-12 14:15:28,678 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:15:28,678 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:15:28,681 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-12 14:15:28,685 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-12 14:15:28,685 DEBUG: nvidia.available: falling back to default
2012-06-12 14:15:28,704 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:15:28,704 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:15:28,707 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-12 14:15:28,711 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-12 14:15:28,711 DEBUG: nvidia.available: falling back to default
2012-06-12 14:15:28,725 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:15:28,725 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:15:28,725 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-12 14:15:28,862 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-12 14:15:28,862 DEBUG: Firmware for DVB cards not available
2012-06-12 14:15:28,862 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-12 14:15:28,868 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-12 14:15:28,872 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-12 14:15:28,872 DEBUG: fglrx.available: falling back to default
2012-06-12 14:15:28,907 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:15:28,910 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-12 14:15:28,914 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-12 14:15:28,914 DEBUG: fglrx.available: falling back to default
2012-06-12 14:15:28,944 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-12 14:15:28,945 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-12 14:15:28,949 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-12 14:15:28,949 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-12 14:15:28,949 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-12 14:15:28,949 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-12 14:15:28,953 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-12 14:15:28,953 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-12 14:15:28,967 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-12 14:15:28,968 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-12 14:15:28,972 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-12 14:15:28,987 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-12 14:15:28,988 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-12 14:15:28,988 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-12 14:15:28,993 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-12 14:15:28,997 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-12 14:15:29,021 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-12 14:15:29,022 DEBUG: all custom handlers loaded
2012-06-12 14:15:29,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:15:29,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-12 14:15:29,439 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:29,439 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:15:29,350 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:15:29,444 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-12 14:15:29,449 DEBUG: fglrx.available: falling back to default
2012-06-12 14:15:29,480 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:29,480 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:15:29,466 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:15:29,480 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-12 14:15:29,493 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:29,493 DEBUG: fglrx is not the alternative in use
2012-06-12 14:15:29,480 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:15:29,501 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-12 14:15:29,505 DEBUG: fglrx.available: falling back to default
2012-06-12 14:15:29,536 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:29,537 DEBUG: fglrx is not the alternative in use
2012-06-12 14:15:29,523 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:15:29,537 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-12 14:15:29,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:15:29,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:15:29,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:15:29,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:15:29,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:15:29,727 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-06-12 14:15:29,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:15:29,731 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-12 14:15:29,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,732 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-12 14:15:29,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:15:29,732 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:15:29,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:15:29,766 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,767 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-06-12 14:15:29,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:15:29,767 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,767 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:15:29,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:15:29,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:15:29,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:15:29,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-06-12 14:15:29,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-06-12 14:15:29,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:15:29,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:15:29,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:15:29,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:15:29,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:15:29,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:15:29,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:15:29,774 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-06-12 14:15:29,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:15:29,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:15:29,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:15:29,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:15:29,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:15:29,786 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-12 14:15:29,787 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:15:29,787 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,787 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,787 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:15:29,787 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:15:29,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:15:29,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:15:29,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:15:29,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:15:29,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:15:29,789 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:15:29,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:15:29,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:15:29,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:15:29,807 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,807 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:15:29,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:15:29,821 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-12 14:15:29,821 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,822 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-12 14:15:29,822 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:15:29,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:15:29,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:15:29,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:15:29,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-06-12 14:15:29,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:15:29,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:15:29,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:15:29,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:15:29,837 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,837 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,837 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:15:29,837 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:15:29,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:15:29,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:15:29,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:15:29,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-06-12 14:15:29,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-06-12 14:15:29,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,853 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:15:29,857 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:15:29,857 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,857 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:15:29,857 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:15:29,857 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:15:29,857 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,858 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:15:29,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb726dd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,858 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:15:29,859 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:15:29,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:15:29,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:15:29,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:15:29,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:15:29,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:15:29,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:15:29,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:15:29,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:15:29,863 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:15:29,863 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:15:29,863 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:15:29,863 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:15:29,863 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb696682c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:15:29,921 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:29,921 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:15:30,050 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:30,050 DEBUG: fglrx is not the alternative in use
2012-06-12 14:15:30,079 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:30,079 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:15:30,122 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:30,122 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:15:30,147 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:30,150 DEBUG: fglrx is not the alternative in use
2012-06-12 14:15:34,189 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:34,190 DEBUG: fglrx is not the alternative in use
2012-06-12 14:15:35,405 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:35,406 DEBUG: fglrx is not the alternative in use
2012-06-12 14:15:36,857 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-12 14:15:36,858 DEBUG: fglrx is not the alternative in use
2012-06-12 14:15:41,331 DEBUG: Installing package: fglrx
2012-06-12 14:15:41,876 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-06-12 14:15:41,882 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-06-12 14:15:42,067 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-06-12 14:15:42,149 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-06-12 14:15:42,234 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-06-12 14:15:42,454 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.189744
2012-06-12 14:15:42,461 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.189744
2012-06-12 14:15:42,465 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.189744
2012-06-12 14:15:42,596 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.350914
2012-06-12 14:15:42,603 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.350914
2012-06-12 14:15:42,608 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.350914
2012-06-12 14:15:42,719 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.544867
2012-06-12 14:15:42,727 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.544867
2012-06-12 14:15:42,732 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.544867
2012-06-12 14:15:43,233 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.450545
2012-06-12 14:15:43,734 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.424709
2012-06-12 14:15:44,236 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.513855
2012-06-12 14:15:44,744 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.781865
2012-06-12 14:15:45,246 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.024323
2012-06-12 14:15:45,747 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.305108
2012-06-12 14:15:46,249 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.490075
2012-06-12 14:15:46,750 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.767666
2012-06-12 14:15:47,252 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.035676
2012-06-12 14:15:47,754 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.329237
2012-06-12 14:15:48,255 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.578083
2012-06-12 14:15:48,756 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.900390
2012-06-12 14:15:49,258 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.174788
2012-06-12 14:15:49,759 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.378918
2012-06-12 14:15:50,268 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.752329
2012-06-12 14:15:50,770 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.950071
2012-06-12 14:15:51,279 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.265990
2012-06-12 14:15:51,780 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.521224
2012-06-12 14:15:52,283 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.782634
2012-06-12 14:15:52,792 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.073213
2012-06-12 14:15:53,293 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.334834
2012-06-12 14:15:53,795 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.612426
2012-06-12 14:15:54,297 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.867660
2012-06-12 14:15:54,798 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.177191
2012-06-12 14:15:55,300 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.426037
2012-06-12 14:15:55,801 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.646137
2012-06-12 14:15:56,303 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.987608
2012-06-12 14:15:56,804 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.159798
2012-06-12 14:15:57,309 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.437390
2012-06-12 14:15:57,810 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.730951
2012-06-12 14:15:58,312 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.091586
2012-06-12 14:15:58,813 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.151987
2012-06-12 14:15:59,314 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.093505
2012-06-12 14:15:59,815 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.381384
2012-06-12 14:16:00,318 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.665364
2012-06-12 14:16:00,819 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.923792
2012-06-12 14:16:01,320 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.150279
2012-06-12 14:16:01,821 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.466199
2012-06-12 14:16:02,322 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.708656
2012-06-12 14:16:02,823 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.011800
2012-06-12 14:16:03,325 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.289391
2012-06-12 14:16:03,826 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.616551
2012-06-12 14:16:04,327 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.889290
2012-06-12 14:16:04,829 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.141330
2012-06-12 14:16:05,331 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.425309
2012-06-12 14:16:05,832 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.715677
2012-06-12 14:16:06,333 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.929389
2012-06-12 14:16:06,835 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.178235
2012-06-12 14:16:07,336 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.433468
2012-06-12 14:16:07,838 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.781327
2012-06-12 14:16:08,339 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.122799
2012-06-12 14:16:08,841 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.358868
2012-06-12 14:16:09,342 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.668400
2012-06-12 14:16:09,940 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.195122
2012-06-12 14:16:10,442 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.466325
2012-06-12 14:16:10,943 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.648097
2012-06-12 14:16:11,444 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.887361
2012-06-12 14:16:11,947 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.088297
2012-06-12 14:16:12,449 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.327561
2012-06-12 14:16:12,950 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.582795
2012-06-12 14:16:13,451 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.860386
2012-06-12 14:16:13,951 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.083680
2012-06-12 14:16:14,453 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.377242
2012-06-12 14:16:14,954 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.642057
2012-06-12 14:16:15,455 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.871739
2012-06-12 14:16:15,956 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.152525
2012-06-12 14:16:16,457 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.385400
2012-06-12 14:16:16,959 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.624664
2012-06-12 14:16:17,460 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.831988
2012-06-12 14:16:17,530 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.023020
2012-06-12 14:16:17,531 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.023020
2012-06-12 14:16:17,532 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.023020
2012-06-12 14:16:18,033 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.290955
2012-06-12 14:16:18,535 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.495085
2012-06-12 14:16:19,035 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.680051
2012-06-12 14:16:19,536 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.868211
2012-06-12 14:16:20,037 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.081923
2012-06-12 14:16:20,538 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.263696
2012-06-12 14:16:21,039 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.499765
2012-06-12 14:16:21,540 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.678344
2012-06-12 14:16:22,041 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.866504
2012-06-12 14:16:22,542 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.064246
2012-06-12 14:16:22,910 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 100.000000
2012-06-12 14:16:24,169 DEBUG: install progress dpkg-exec 0.000000
2012-06-12 14:16:26,891 DEBUG: install progress patch 0.000000
2012-06-12 14:16:26,894 DEBUG: install progress patch 4.000000
2012-06-12 14:16:27,531 DEBUG: install progress patch 8.000000
2012-06-12 14:16:27,638 DEBUG: install progress patch 12.000000
2012-06-12 14:16:27,977 DEBUG: install progress dkms 12.000000
2012-06-12 14:16:27,980 DEBUG: install progress dkms 16.000000
2012-06-12 14:16:28,489 DEBUG: install progress dkms 20.000000
2012-06-12 14:16:28,597 DEBUG: install progress dkms 24.000000
2012-06-12 14:16:28,924 DEBUG: install progress fakeroot 24.000000
2012-06-12 14:16:28,927 DEBUG: install progress fakeroot 28.000000
2012-06-12 14:16:29,366 DEBUG: install progress fakeroot 32.000000
2012-06-12 14:16:29,465 DEBUG: install progress fakeroot 36.000000
2012-06-12 14:16:30,007 DEBUG: install progress fglrx 36.000000
2012-06-12 14:16:30,011 DEBUG: install progress fglrx 40.000000
2012-06-12 14:16:33,385 DEBUG: install progress fglrx 44.000000
2012-06-12 14:16:33,493 DEBUG: install progress fglrx 48.000000
2012-06-12 14:16:33,743 DEBUG: install progress fglrx-amdcccle 48.000000
2012-06-12 14:16:33,746 DEBUG: install progress fglrx-amdcccle 52.000000
2012-06-12 14:16:34,414 DEBUG: install progress fglrx-amdcccle 56.000000
2012-06-12 14:16:34,513 DEBUG: install progress fglrx-amdcccle 60.000000
2012-06-12 14:16:34,620 DEBUG: install progress man-db 60.000000
2012-06-12 14:16:38,257 DEBUG: install progress ureadahead 60.000000
2012-06-12 14:16:38,666 DEBUG: install progress dpkg-exec 60.000000
2012-06-12 14:16:38,727 DEBUG: install progress patch 60.000000
2012-06-12 14:16:38,851 DEBUG: install progress patch 64.000000
2012-06-12 14:16:38,952 DEBUG: install progress patch 68.000000
2012-06-12 14:16:39,052 DEBUG: install progress dkms 68.000000
2012-06-12 14:16:40,471 DEBUG: install progress dkms 72.000000
2012-06-12 14:16:40,545 DEBUG: install progress dkms 76.000000
2012-06-12 14:16:40,618 DEBUG: install progress fakeroot 76.000000
2012-06-12 14:16:40,685 DEBUG: install progress fakeroot 80.000000
2012-06-12 14:16:41,168 DEBUG: install progress fakeroot 84.000000
2012-06-12 14:16:41,306 DEBUG: install progress fglrx 84.000000
2012-06-12 14:16:41,664 DEBUG: install progress fglrx 88.000000
2012-06-12 14:17:14,078 DEBUG: install progress fglrx 92.000000
2012-06-12 14:17:14,650 DEBUG: install progress bamfdaemon 92.000000
2012-06-12 14:17:15,131 DEBUG: install progress fglrx-amdcccle 92.000000
2012-06-12 14:17:15,242 DEBUG: install progress fglrx-amdcccle 96.000000
2012-06-12 14:17:15,354 DEBUG: install progress fglrx-amdcccle 100.000000
2012-06-12 14:17:15,467 DEBUG: install progress initramfs-tools 100.000000
2012-06-12 14:17:26,364 DEBUG: install progress libc-bin 100.000000
2012-06-12 14:17:27,468 DEBUG: Selecting previously unselected package patch.
(Reading database ... 140824 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-3_i386.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Selecting previously unselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.960-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-3) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic-pae
Building for architecture i686
Building initial module for 3.2.0-23-generic-pae
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic-pae/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-06-12 14:17:49,510 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:49,510 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:17:49,611 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:49,611 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:17:49,728 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:49,728 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:17:49,822 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:49,823 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:17:49,938 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:49,938 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:17:50,099 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:50,099 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:17:50,206 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:50,206 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:17:50,368 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:50,369 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:17:50,397 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:50,397 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:17:50,484 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:17:50,485 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:17:57,663 DEBUG: Shutting down
2012-06-12 14:19:31,836 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c>
2012-06-12 14:19:36,129 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-06-12 14:19:36,314 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-12 14:19:36,319 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-12 14:19:36,418 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-12 14:19:36,448 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-12 14:19:36,467 DEBUG: Software modem not available
2012-06-12 14:19:36,467 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-12 14:19:36,562 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-12 14:19:36,566 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-12 14:19:36,568 DEBUG: nvidia.available: falling back to default
2012-06-12 14:19:36,765 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:19:36,765 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:19:36,769 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-12 14:19:36,773 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-12 14:19:36,774 DEBUG: nvidia.available: falling back to default
2012-06-12 14:19:36,801 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-12 14:19:36,804 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-12 14:19:36,808 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-12 14:19:36,809 DEBUG: nvidia.available: falling back to default
2012-06-12 14:19:36,839 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:19:36,842 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-12 14:19:36,846 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-12 14:19:36,847 DEBUG: nvidia.available: falling back to default
2012-06-12 14:19:36,861 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:19:36,861 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:19:36,864 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-12 14:19:36,868 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-12 14:19:36,868 DEBUG: nvidia.available: falling back to default
2012-06-12 14:19:36,882 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:19:36,883 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:19:36,885 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-12 14:19:36,890 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-12 14:19:36,890 DEBUG: nvidia.available: falling back to default
2012-06-12 14:19:36,904 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:19:36,904 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:19:36,904 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-12 14:19:37,065 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-12 14:19:37,066 DEBUG: Firmware for DVB cards not available
2012-06-12 14:19:37,066 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-12 14:19:37,071 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-12 14:19:37,075 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-12 14:19:37,075 DEBUG: fglrx.available: falling back to default
2012-06-12 14:19:37,102 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:19:37,118 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-12 14:19:37,118 DEBUG: fglrx.available: falling back to default
2012-06-12 14:19:37,147 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-12 14:19:37,147 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-12 14:19:37,151 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-12 14:19:37,151 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-12 14:19:37,151 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-12 14:19:37,151 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-12 14:19:37,155 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-12 14:19:37,155 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-12 14:19:37,169 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-12 14:19:37,169 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-12 14:19:37,192 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-12 14:19:37,207 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-12 14:19:37,207 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-12 14:19:37,207 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-12 14:19:37,212 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-12 14:19:37,217 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-12 14:19:37,241 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-12 14:19:37,241 DEBUG: all custom handlers loaded
2012-06-12 14:19:37,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:19:37,605 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-12 14:19:37,678 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:37,679 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:19:37,606 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:19:37,682 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-12 14:19:37,686 DEBUG: fglrx.available: falling back to default
2012-06-12 14:19:37,715 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:37,715 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:19:37,701 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:19:37,715 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-12 14:19:37,738 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:37,738 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:19:37,715 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:19:37,842 DEBUG: fglrx.available: falling back to default
2012-06-12 14:19:37,869 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:37,869 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:19:37,857 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:19:37,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-12 14:19:38,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,070 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-06-12 14:19:38,082 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:38,082 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:19:38,070 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:19:38,172 DEBUG: fglrx.available: falling back to default
2012-06-12 14:19:38,199 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:38,199 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:19:38,186 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:19:38,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:19:38,277 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,278 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:19:38,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:19:38,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:19:38,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:19:38,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-06-12 14:19:38,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:19:38,303 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-12 14:19:38,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,303 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-12 14:19:38,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:19:38,303 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:19:38,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:19:38,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-06-12 14:19:38,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:19:38,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:19:38,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:19:38,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:19:38,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:19:38,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-06-12 14:19:38,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-06-12 14:19:38,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:19:38,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:19:38,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:19:38,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:19:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:19:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:19:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:19:38,337 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-06-12 14:19:38,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:19:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:19:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:19:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:19:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:19:38,346 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-12 14:19:38,346 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:19:38,347 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,347 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,347 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:19:38,347 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:19:38,347 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,347 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:19:38,347 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:19:38,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:19:38,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:19:38,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:19:38,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:19:38,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:19:38,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:19:38,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:19:38,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:19:38,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:19:38,376 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-12 14:19:38,376 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,377 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-12 14:19:38,377 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:19:38,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:19:38,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:19:38,381 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:19:38,381 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-06-12 14:19:38,382 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:19:38,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:19:38,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:19:38,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:19:38,391 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,391 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,391 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:19:38,391 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:19:38,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:19:38,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:19:38,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:19:38,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-06-12 14:19:38,404 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-06-12 14:19:38,404 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:19:38,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:19:38,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:19:38,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:19:38,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:19:38,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:19:38,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:19:38,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71afd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:19:38,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:19:38,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:19:38,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:19:38,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:19:38,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:19:38,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:19:38,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:19:38,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:19:38,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68a884c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:19:38,528 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:38,529 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:19:38,668 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:38,668 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:19:38,937 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:38,938 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:19:38,971 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:38,972 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:19:38,993 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:38,994 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:19:43,197 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:19:43,197 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:19:47,730 DEBUG: Installing package: fglrx-updates
2012-06-12 14:19:48,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-06-12 14:19:48,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-06-12 14:19:48,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-06-12 14:19:48,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-06-12 14:19:48,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-06-12 14:19:48,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.615912
2012-06-12 14:19:49,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.508706
2012-06-12 14:19:49,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.488211
2012-06-12 14:19:50,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.429178
2012-06-12 14:19:50,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.424740
2012-06-12 14:19:51,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.445994
2012-06-12 14:19:51,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.441556
2012-06-12 14:19:52,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.527040
2012-06-12 14:19:52,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.573986
2012-06-12 14:19:53,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.550279
2012-06-12 14:19:53,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.565110
2012-06-12 14:19:54,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.579941
2012-06-12 14:19:54,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.472735
2012-06-12 14:19:55,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.503624
2012-06-12 14:19:55,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.486340
2012-06-12 14:19:56,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.549343
2012-06-12 14:19:56,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.593077
2012-06-12 14:19:57,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.640023
2012-06-12 14:19:57,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.622739
2012-06-12 14:19:58,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.621513
2012-06-12 14:19:58,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.543211
2012-06-12 14:19:59,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.432794
2012-06-12 14:19:59,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.457259
2012-06-12 14:20:00,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.298670
2012-06-12 14:20:00,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.851046
2012-06-12 14:20:01,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.695668
2012-06-12 14:20:01,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.707288
2012-06-12 14:20:02,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.776714
2012-06-12 14:20:02,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.797968
2012-06-12 14:20:03,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.851337
2012-06-12 14:20:03,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.914340
2012-06-12 14:20:04,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.942017
2012-06-12 14:20:04,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.976117
2012-06-12 14:20:05,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.778990
2012-06-12 14:20:05,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.610766
2012-06-12 14:20:06,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.564578
2012-06-12 14:20:07,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.473430
2012-06-12 14:20:07,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.433666
2012-06-12 14:20:08,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.390690
2012-06-12 14:20:08,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.203197
2012-06-12 14:20:09,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.070300
2012-06-12 14:20:09,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.081919
2012-06-12 14:20:10,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.119231
2012-06-12 14:20:10,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.111581
2012-06-12 14:20:11,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.004376
2012-06-12 14:20:11,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.105917
2012-06-12 14:20:12,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.098267
2012-06-12 14:20:12,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.138790
2012-06-12 14:20:13,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.993047
2012-06-12 14:20:13,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.972551
2012-06-12 14:20:14,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.987382
2012-06-12 14:20:14,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.995790
2012-06-12 14:20:15,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.020256
2012-06-12 14:20:15,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.038298
2012-06-12 14:20:16,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.062764
2012-06-12 14:20:16,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.055115
2012-06-12 14:20:17,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.086003
2012-06-12 14:20:17,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.100834
2012-06-12 14:20:18,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.961513
2012-06-12 14:20:18,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.005248
2012-06-12 14:20:19,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.081097
2012-06-12 14:20:19,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.163369
2012-06-12 14:20:20,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.975877
2012-06-12 14:20:20,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.669559
2012-06-12 14:20:21,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.507758
2012-06-12 14:20:21,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.419821
2012-06-12 14:20:22,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.380057
2012-06-12 14:20:22,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.314600
2012-06-12 14:20:23,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.326220
2012-06-12 14:20:23,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.334628
2012-06-12 14:20:24,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.294864
2012-06-12 14:20:24,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.348232
2012-06-12 14:20:25,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.343794
2012-06-12 14:20:25,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.336145
2012-06-12 14:20:26,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.350976
2012-06-12 14:20:26,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.269462
2012-06-12 14:20:27,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.959933
2012-06-12 14:20:27,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.945860
2012-06-12 14:20:28,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.938211
2012-06-12 14:20:28,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.978734
2012-06-12 14:20:29,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.028891
2012-06-12 14:20:29,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.050145
2012-06-12 14:20:30,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.971843
2012-06-12 14:20:30,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.944925
2012-06-12 14:20:31,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.879469
2012-06-12 14:20:31,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.641426
2012-06-12 14:20:32,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.722174
2012-06-12 14:20:32,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.589967
2012-06-12 14:20:33,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.482761
2012-06-12 14:20:33,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.504015
2012-06-12 14:20:33,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.952546
2012-06-12 14:20:33,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.952546
2012-06-12 14:20:33,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.952546
2012-06-12 14:20:33,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.952546
2012-06-12 14:20:34,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.955067
2012-06-12 14:20:34,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.642326
2012-06-12 14:20:35,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.592928
2012-06-12 14:20:35,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.530683
2012-06-12 14:20:36,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.513399
2012-06-12 14:20:36,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.374078
2012-06-12 14:20:37,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.395332
2012-06-12 14:20:37,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.352357
2012-06-12 14:20:38,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.257997
2012-06-12 14:20:38,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.166849
2012-06-12 14:20:39,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.181680
2012-06-12 14:20:39,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.141915
2012-06-12 14:20:40,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.156746
2012-06-12 14:20:40,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.065598
2012-06-12 14:20:41,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.486303
2012-06-12 14:20:41,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.486303
2012-06-12 14:20:42,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.486303
2012-06-12 14:20:42,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.486303
2012-06-12 14:20:43,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.486303
2012-06-12 14:20:43,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.486303
2012-06-12 14:20:44,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.518418
2012-06-12 14:20:44,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 100.000000
2012-06-12 14:20:45,795 DEBUG: install progress dpkg-exec 0.000000
2012-06-12 14:20:48,804 DEBUG: install progress fglrx-amdcccle 0.000000
2012-06-12 14:20:48,804 DEBUG: install progress fglrx-amdcccle 6.250000
2012-06-12 14:20:48,953 DEBUG: install progress fglrx-amdcccle 12.500000
2012-06-12 14:20:49,257 DEBUG: install progress fglrx-amdcccle 18.750000
2012-06-12 14:20:49,812 DEBUG: install progress fglrx 18.750000
2012-06-12 14:20:49,815 DEBUG: install progress fglrx 25.000000
2012-06-12 14:21:07,014 DEBUG: install progress fglrx 31.250000
2012-06-12 14:21:08,562 DEBUG: install progress fglrx 37.500000
2012-06-12 14:21:08,832 DEBUG: install progress bamfdaemon 37.500000
2012-06-12 14:21:09,300 DEBUG: install progress ureadahead 37.500000
2012-06-12 14:21:09,536 DEBUG: install progress initramfs-tools 37.500000
2012-06-12 14:21:23,663 DEBUG: install progress libc-bin 37.500000
2012-06-12 14:21:24,180 DEBUG: install progress dpkg-exec 37.500000
2012-06-12 14:21:24,888 DEBUG: install progress fglrx-updates 37.500000
2012-06-12 14:21:24,893 DEBUG: install progress fglrx-updates 43.750000
2012-06-12 14:21:28,121 DEBUG: install progress fglrx-updates 50.000000
2012-06-12 14:21:28,212 DEBUG: install progress fglrx-updates 56.250000
2012-06-12 14:21:28,426 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2012-06-12 14:21:28,429 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2012-06-12 14:21:29,011 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2012-06-12 14:21:29,097 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2012-06-12 14:21:29,191 DEBUG: install progress ureadahead 75.000000
2012-06-12 14:21:29,604 DEBUG: install progress dpkg-exec 75.000000
2012-06-12 14:21:29,656 DEBUG: install progress fglrx-updates 75.000000
2012-06-12 14:21:30,108 DEBUG: install progress fglrx-updates 81.250000
2012-06-12 14:21:53,147 DEBUG: install progress fglrx-updates 87.500000
2012-06-12 14:21:53,642 DEBUG: install progress bamfdaemon 87.500000
2012-06-12 14:21:53,944 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2012-06-12 14:21:54,045 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2012-06-12 14:21:54,146 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-06-12 14:21:54,248 DEBUG: install progress initramfs-tools 100.000000
2012-06-12 14:22:05,677 DEBUG: install progress libc-bin 100.000000
2012-06-12 14:22:06,889 DEBUG: (Reading database ... 141164 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-updates.
(Reading database ... 140925 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic-pae
Building for architecture i686
Building initial module for 3.2.0-23-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-06-12 14:22:07,209 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-06-12 14:22:30,344 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:30,344 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:22:30,358 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:30,359 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:22:33,849 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:33,849 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:22:33,863 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:33,863 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:22:33,889 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:33,890 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:22:34,070 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:34,070 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:22:34,084 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:34,084 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:22:34,122 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:34,122 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:22:34,136 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:34,136 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:22:34,160 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:34,160 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:22:35,793 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:22:35,793 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:22:38,384 DEBUG: Shutting down
2012-06-12 14:28:23,216 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c>
2012-06-12 14:28:28,764 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-06-12 14:28:29,044 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-12 14:28:29,057 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-12 14:28:29,244 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-12 14:28:29,314 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-12 14:28:29,349 DEBUG: Software modem not available
2012-06-12 14:28:29,350 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-12 14:28:29,441 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-12 14:28:29,454 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-12 14:28:29,456 DEBUG: nvidia.available: falling back to default
2012-06-12 14:28:29,684 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:28:29,684 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:28:29,692 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-12 14:28:29,718 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-12 14:28:29,718 DEBUG: nvidia.available: falling back to default
2012-06-12 14:28:29,814 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-12 14:28:29,817 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-12 14:28:29,834 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-12 14:28:29,835 DEBUG: nvidia.available: falling back to default
2012-06-12 14:28:29,931 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:28:29,945 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-12 14:28:29,954 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-12 14:28:29,955 DEBUG: nvidia.available: falling back to default
2012-06-12 14:28:30,002 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:28:30,003 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:28:30,014 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-12 14:28:30,032 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-12 14:28:30,032 DEBUG: nvidia.available: falling back to default
2012-06-12 14:28:30,081 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:28:30,082 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:28:30,089 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-12 14:28:30,105 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-12 14:28:30,106 DEBUG: nvidia.available: falling back to default
2012-06-12 14:28:30,141 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:28:30,142 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:28:30,142 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-12 14:28:30,240 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-12 14:28:30,241 DEBUG: Firmware for DVB cards not available
2012-06-12 14:28:30,241 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-12 14:28:30,294 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-12 14:28:30,294 DEBUG: fglrx.available: falling back to default
2012-06-12 14:28:30,390 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:28:30,400 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-12 14:28:30,419 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-12 14:28:30,421 DEBUG: fglrx.available: falling back to default
2012-06-12 14:28:30,505 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-12 14:28:30,505 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-12 14:28:30,527 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-12 14:28:30,528 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-12 14:28:30,528 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-12 14:28:30,528 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-12 14:28:30,542 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-12 14:28:30,543 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-12 14:28:30,589 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-12 14:28:30,590 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-12 14:28:30,602 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-12 14:28:30,647 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-12 14:28:30,647 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-12 14:28:30,647 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-12 14:28:30,667 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-12 14:28:30,682 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-12 14:28:30,777 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-12 14:28:30,778 DEBUG: all custom handlers loaded
2012-06-12 14:28:30,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:28:31,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-12 14:28:32,019 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:32,019 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:28:31,902 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:28:32,039 DEBUG: fglrx.available: falling back to default
2012-06-12 14:28:32,131 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:32,132 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:28:32,082 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:28:32,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-12 14:28:32,174 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:32,175 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:28:32,132 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:28:32,184 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-12 14:28:32,207 DEBUG: fglrx.available: falling back to default
2012-06-12 14:28:32,291 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:32,291 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:28:32,246 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:28:32,292 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-12 14:28:32,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-06-12 14:28:32,571 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:32,571 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:28:32,520 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:28:32,586 DEBUG: fglrx.available: falling back to default
2012-06-12 14:28:32,686 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:32,686 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:28:32,644 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:28:32,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:28:32,700 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:32,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,701 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:28:32,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:32,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:32,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:28:32,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:28:32,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:28:32,782 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-06-12 14:28:32,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:28:32,783 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-12 14:28:32,783 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,783 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-12 14:28:32,783 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:28:32,784 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:32,784 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:28:32,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:28:32,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:32,837 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-06-12 14:28:32,837 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:28:32,847 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:32,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,847 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:28:32,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:28:32,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:32,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:28:32,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:28:32,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-06-12 14:28:32,864 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,864 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-06-12 14:28:32,864 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:28:32,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:28:32,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:28:32,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:28:32,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:28:32,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:28:32,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:28:32,870 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-06-12 14:28:32,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:28:32,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:28:32,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:28:32,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:28:32,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:28:32,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-12 14:28:32,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:32,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:28:32,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:32,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:28:32,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:28:32,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:32,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:28:32,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:32,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:28:32,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:28:32,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:28:32,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:28:32,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:28:32,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:28:32,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:28:32,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:28:32,956 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:32,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:28:32,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:28:32,991 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-12 14:28:32,992 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,992 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-12 14:28:32,992 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:32,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:28:32,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:28:32,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:28:33,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:28:33,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-06-12 14:28:33,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:28:33,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:28:33,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:28:33,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:28:33,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:33,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:28:33,048 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:28:33,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:28:33,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:28:33,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:28:33,105 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-06-12 14:28:33,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,106 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-06-12 14:28:33,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:28:33,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:28:33,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:28:33,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:28:33,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:28:33,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:28:33,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:28:33,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ced0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:33,116 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:28:33,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:28:33,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:28:33,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:28:33,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:28:33,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:28:33,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:28:33,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:28:33,129 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:28:33,129 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:28:33,129 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:28:33,129 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68c784c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:28:33,267 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:33,268 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:28:33,422 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:33,423 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:28:33,820 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:33,820 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:28:33,924 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:33,924 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:28:33,999 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:33,999 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:28:36,965 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:28:36,966 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:28:44,108 DEBUG: Shutting down
2012-06-12 14:34:17,720 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c>
2012-06-12 14:34:20,031 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-06-12 14:34:20,154 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-12 14:34:20,167 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-12 14:34:20,235 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-12 14:34:20,266 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-12 14:34:20,507 DEBUG: Software modem not available
2012-06-12 14:34:20,507 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-12 14:34:20,561 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-12 14:34:20,569 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-12 14:34:20,570 DEBUG: nvidia.available: falling back to default
2012-06-12 14:34:20,670 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:34:20,670 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:34:20,673 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-12 14:34:20,677 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-12 14:34:20,678 DEBUG: nvidia.available: falling back to default
2012-06-12 14:34:20,706 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-12 14:34:20,709 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-12 14:34:20,713 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-12 14:34:20,714 DEBUG: nvidia.available: falling back to default
2012-06-12 14:34:20,744 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:34:20,748 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-12 14:34:20,752 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-12 14:34:20,752 DEBUG: nvidia.available: falling back to default
2012-06-12 14:34:20,766 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:34:20,767 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:34:20,770 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-12 14:34:20,774 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-12 14:34:20,775 DEBUG: nvidia.available: falling back to default
2012-06-12 14:34:20,788 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:34:20,789 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:34:20,792 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-12 14:34:20,796 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-12 14:34:20,797 DEBUG: nvidia.available: falling back to default
2012-06-12 14:34:20,811 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:34:20,811 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:34:20,811 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-12 14:34:20,870 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-12 14:34:20,871 DEBUG: Firmware for DVB cards not available
2012-06-12 14:34:20,871 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-12 14:34:20,887 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-12 14:34:20,887 DEBUG: fglrx.available: falling back to default
2012-06-12 14:34:20,916 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:34:20,919 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-12 14:34:20,923 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-12 14:34:20,924 DEBUG: fglrx.available: falling back to default
2012-06-12 14:34:20,952 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-12 14:34:20,952 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-12 14:34:20,956 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-12 14:34:20,957 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-12 14:34:20,957 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-12 14:34:20,957 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-12 14:34:20,960 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-12 14:34:20,961 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-12 14:34:20,974 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-12 14:34:20,975 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-12 14:34:20,979 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-12 14:34:20,994 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-12 14:34:20,994 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-12 14:34:20,994 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-12 14:34:21,000 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-12 14:34:21,004 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-12 14:34:21,029 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-12 14:34:21,029 DEBUG: all custom handlers loaded
2012-06-12 14:34:21,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:34:21,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-12 14:34:21,688 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:21,689 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:34:21,668 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:34:21,693 DEBUG: fglrx.available: falling back to default
2012-06-12 14:34:21,719 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:21,720 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:34:21,707 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:34:21,720 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-12 14:34:21,732 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:21,732 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:34:21,720 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:34:21,735 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-12 14:34:21,739 DEBUG: fglrx.available: falling back to default
2012-06-12 14:34:21,765 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:21,765 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:34:21,753 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:34:21,765 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-12 14:34:21,836 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,836 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-06-12 14:34:21,848 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:21,848 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:34:21,836 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:34:21,852 DEBUG: fglrx.available: falling back to default
2012-06-12 14:34:21,902 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:21,902 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:34:21,875 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:34:21,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:34:21,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:21,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:34:21,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:21,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:21,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:34:21,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:34:21,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:34:21,937 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-06-12 14:34:21,937 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:34:21,937 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-12 14:34:21,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-12 14:34:21,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:34:21,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:21,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:34:21,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:34:21,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:21,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-06-12 14:34:21,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:34:21,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:21,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:34:21,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:34:21,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:21,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:34:21,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:34:21,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-06-12 14:34:21,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-06-12 14:34:21,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:34:21,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:34:21,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:34:21,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:34:21,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:34:21,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:34:21,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:34:21,961 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-06-12 14:34:21,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:34:21,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:34:21,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:34:21,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:34:21,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:34:21,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-12 14:34:21,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:21,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:34:21,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:21,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:34:21,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:34:21,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:21,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:34:21,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:21,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:34:21,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:34:21,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:34:21,972 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,972 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:34:21,972 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:34:21,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:34:21,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:34:21,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:34:21,988 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:21,988 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:21,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:34:21,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:34:22,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-12 14:34:22,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-12 14:34:22,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:34:22,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:34:22,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:34:22,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:34:22,005 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-06-12 14:34:22,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:34:22,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:34:22,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:34:22,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:34:22,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:22,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:34:22,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:34:22,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:34:22,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:34:22,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:34:22,027 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-06-12 14:34:22,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,028 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-06-12 14:34:22,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:34:22,032 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:34:22,032 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,032 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:34:22,032 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:34:22,033 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:34:22,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,033 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:34:22,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb717fd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:34:22,033 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:34:22,034 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:34:22,035 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:34:22,036 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb687884c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:34:22,130 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:22,130 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:34:22,217 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:22,217 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:34:22,411 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:22,411 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:34:22,447 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:22,447 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:34:22,470 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:22,470 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:34:24,160 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:24,160 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:34:25,456 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:34:25,456 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:34:30,048 DEBUG: Installing package: fglrx
2012-06-12 14:34:30,798 DEBUG: install progress dpkg-exec 0.000000
2012-06-12 14:34:32,861 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2012-06-12 14:34:32,864 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2012-06-12 14:34:32,960 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2012-06-12 14:34:33,197 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2012-06-12 14:34:33,749 DEBUG: install progress fglrx-updates 18.750000
2012-06-12 14:34:33,751 DEBUG: install progress fglrx-updates 25.000000
2012-06-12 14:34:47,454 DEBUG: install progress fglrx-updates 31.250000
2012-06-12 14:34:48,378 DEBUG: install progress fglrx-updates 37.500000
2012-06-12 14:34:48,671 DEBUG: install progress bamfdaemon 37.500000
2012-06-12 14:34:49,019 DEBUG: install progress ureadahead 37.500000
2012-06-12 14:34:49,198 DEBUG: install progress initramfs-tools 37.500000
2012-06-12 14:34:59,604 DEBUG: install progress libc-bin 37.500000
2012-06-12 14:35:00,073 DEBUG: install progress dpkg-exec 37.500000
2012-06-12 14:35:00,700 DEBUG: install progress fglrx 37.500000
2012-06-12 14:35:00,703 DEBUG: install progress fglrx 43.750000
2012-06-12 14:35:04,927 DEBUG: install progress fglrx 50.000000
2012-06-12 14:35:05,040 DEBUG: install progress fglrx 56.250000
2012-06-12 14:35:05,455 DEBUG: install progress fglrx-amdcccle 56.250000
2012-06-12 14:35:05,457 DEBUG: install progress fglrx-amdcccle 62.500000
2012-06-12 14:35:06,273 DEBUG: install progress fglrx-amdcccle 68.750000
2012-06-12 14:35:06,393 DEBUG: install progress fglrx-amdcccle 75.000000
2012-06-12 14:35:06,521 DEBUG: install progress ureadahead 75.000000
2012-06-12 14:35:06,977 DEBUG: install progress dpkg-exec 75.000000
2012-06-12 14:35:07,071 DEBUG: install progress fglrx 75.000000
2012-06-12 14:35:07,626 DEBUG: install progress fglrx 81.250000
2012-06-12 14:35:30,358 DEBUG: install progress fglrx 87.500000
2012-06-12 14:35:30,895 DEBUG: install progress bamfdaemon 87.500000
2012-06-12 14:35:31,131 DEBUG: install progress fglrx-amdcccle 87.500000
2012-06-12 14:35:31,198 DEBUG: install progress fglrx-amdcccle 93.750000
2012-06-12 14:35:31,279 DEBUG: install progress fglrx-amdcccle 100.000000
2012-06-12 14:35:31,347 DEBUG: install progress initramfs-tools 100.000000
2012-06-12 14:35:39,491 DEBUG: install progress libc-bin 100.000000
2012-06-12 14:35:40,701 DEBUG: (Reading database ... 144425 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx.
(Reading database ... 144187 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.960-0ubuntu1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.960 DKMS files...
Building only for 3.2.0-23-generic-pae
Building for architecture i686
Building initial module for 3.2.0-23-generic-pae
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-06-12 14:35:40,919 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:05.0
2012-06-12 14:36:01,258 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:01,258 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:36:01,352 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:01,352 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:36:01,463 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:01,464 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:36:01,599 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:01,599 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:36:01,733 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:01,733 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:36:01,924 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:01,924 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:36:02,016 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:02,016 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:36:02,132 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:02,132 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:36:02,156 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:02,156 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:36:02,248 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:36:02,248 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:36:13,819 DEBUG: Shutting down
2012-06-12 14:51:26,542 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c>
2012-06-12 14:51:29,704 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-06-12 14:51:29,869 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-12 14:51:29,875 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-12 14:51:29,951 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-12 14:51:29,989 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-12 14:51:30,016 DEBUG: Software modem not available
2012-06-12 14:51:30,017 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-12 14:51:30,115 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-12 14:51:30,125 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-12 14:51:30,128 DEBUG: nvidia.available: falling back to default
2012-06-12 14:51:30,220 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:51:30,220 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:51:30,223 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-12 14:51:30,227 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-12 14:51:30,228 DEBUG: nvidia.available: falling back to default
2012-06-12 14:51:30,255 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-12 14:51:30,259 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-12 14:51:30,263 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-12 14:51:30,263 DEBUG: nvidia.available: falling back to default
2012-06-12 14:51:30,294 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:51:30,297 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-12 14:51:30,301 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-12 14:51:30,302 DEBUG: nvidia.available: falling back to default
2012-06-12 14:51:30,316 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:51:30,316 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:51:30,319 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-12 14:51:30,323 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-12 14:51:30,324 DEBUG: nvidia.available: falling back to default
2012-06-12 14:51:30,345 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:51:30,345 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-12 14:51:30,349 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-12 14:51:30,354 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-12 14:51:30,354 DEBUG: nvidia.available: falling back to default
2012-06-12 14:51:30,368 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-12 14:51:30,368 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-12 14:51:30,368 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-12 14:51:30,465 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-12 14:51:30,466 DEBUG: Firmware for DVB cards not available
2012-06-12 14:51:30,466 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-12 14:51:30,499 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-12 14:51:30,504 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-12 14:51:30,504 DEBUG: fglrx.available: falling back to default
2012-06-12 14:51:30,532 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-12 14:51:30,547 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-12 14:51:30,548 DEBUG: fglrx.available: falling back to default
2012-06-12 14:51:30,576 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-12 14:51:30,577 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-12 14:51:30,581 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-12 14:51:30,581 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-12 14:51:30,581 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-12 14:51:30,581 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-12 14:51:30,585 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-12 14:51:30,585 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-12 14:51:30,599 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-12 14:51:30,600 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-12 14:51:30,604 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-12 14:51:30,619 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-12 14:51:30,619 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-12 14:51:30,620 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-12 14:51:30,625 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-12 14:51:30,629 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-12 14:51:30,654 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-12 14:51:30,654 DEBUG: all custom handlers loaded
2012-06-12 14:51:30,654 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:51:31,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-12 14:51:31,088 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:31,088 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:51:31,010 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:51:31,091 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-12 14:51:31,095 DEBUG: fglrx.available: falling back to default
2012-06-12 14:51:31,123 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:31,123 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:51:31,110 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-12 14:51:31,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-12 14:51:31,136 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:31,136 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:51:31,123 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:51:31,234 DEBUG: fglrx.available: falling back to default
2012-06-12 14:51:31,261 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:31,261 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:51:31,248 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:51:31,339 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-12 14:51:31,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-06-12 14:51:31,445 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:31,445 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:51:31,432 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:51:31,527 DEBUG: fglrx.available: falling back to default
2012-06-12 14:51:31,563 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:31,563 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:51:31,541 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-12 14:51:31,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:51:31,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:51:31,647 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:51:31,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:51:31,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:51:31,671 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-06-12 14:51:31,671 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:51:31,672 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-12 14:51:31,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,672 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-12 14:51:31,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:51:31,672 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,673 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:51:31,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:51:31,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-06-12 14:51:31,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:51:31,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:51:31,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:51:31,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:51:31,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:51:31,694 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-06-12 14:51:31,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,694 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-06-12 14:51:31,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:51:31,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:51:31,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:51:31,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:51:31,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:51:31,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:51:31,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:51:31,695 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-06-12 14:51:31,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:51:31,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:51:31,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:51:31,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:51:31,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:51:31,719 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-12 14:51:31,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:51:31,720 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,720 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:51:31,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:51:31,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:51:31,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:51:31,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:51:31,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-12 14:51:31,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:51:31,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:51:31,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:51:31,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:51:31,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:51:31,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,758 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:51:31,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:51:31,787 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-12 14:51:31,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-12 14:51:31,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:51:31,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:51:31,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:51:31,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:51:31,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-06-12 14:51:31,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:51:31,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:51:31,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:51:31,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:51:31,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:51:31,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:51:31,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:51:31,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:51:31,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:51:31,872 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-06-12 14:51:31,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,872 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-06-12 14:51:31,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:51:31,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:51:31,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-12 14:51:31,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:51:31,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-12 14:51:31,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-12 14:51:31,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725bd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001604bc03sc00i00')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-12 14:51:31,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'platform:hp-wmi')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001604bc0Csc05i00')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001604bc06sc00i00')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:SYN1E35:SYN1E00:SYN0002:PNP0F13:')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-12 14:51:31,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001604bc02sc00i00')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-06-12 14:51:31,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.18:bd04/18/2011:svnHewlett-Packard:pnPresarioCQ56NotebookPC:pvr058D100002242810010620100:rvnHewlett-Packard:rn1604:rvr88.17:cvnHewlett-Packard:ct10:cvrN/A:')
2012-06-12 14:51:31,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-12 14:51:31,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-06-12 14:51:31,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-12 14:51:31,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-06-12 14:51:31,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-06-12 14:51:31,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-12 14:51:31,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001604bc06sc01i00')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001604bc01sc06i01')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'platform:eisa')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001604bc0Csc03i20')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'platform:regulatory')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001604bc04sc03i00')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-06-12 14:51:31,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695484c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-12 14:51:32,036 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:32,036 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:51:32,176 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:32,176 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:51:32,439 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:32,439 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:51:32,473 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:32,473 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:51:32,496 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:32,496 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 14:51:40,160 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 14:51:40,160 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 14:51:41,993 DEBUG: Shutting down
```I have no idea what this means. Any help would be great! :popcorn:

---

### Post by Bucky Ball on 2012-06-12
Are you using 12.04 LTS? Not sure what the state of play is with the ATI graphics drivers there. They can be problematic generally. Is the machine still running okay but laggy? Can you open the Catalyst Control Centre? That controls the card with the ATI GUI. You might be able to tweak something there.

---

### Post by typhoon_tip on 2012-06-13
Welcome to Ubuntu !

About the lagginess with ATI, very simple to fix, do the following and you will see the true speed of the thing :popcorn:

```
sudo apt-get install compizconfig-settings-manager
```

It will install some stuff. After is done, go to the menu and search "compiz", then run the "CompizConfig Settings Manager" program. It gives a warning, be careful on using this tool as you can change more settings than you can imagine, but only stick for what I tell you here !

1) Click Open GL plugin icon
2) Texture Filter: best
3) Sync to VBlank: **untick**
4) Press Back button
5) Open Composite plugin icon
6) Detect Refresh Rate: **untick**
7) Refresh rate: set it to 60 or 80
8) Press Back button
9) Close the window

Try to move a window around now, you will notice a HUGE difference !

To make it even better, do this:

1) On the unity dash, type AMD
2) Open AMD Catalyst Control Center icon (not the administrative one, no necessary)
3) Go to the Display Options
4) Click on Tear Free item
5) Tick "Enable tear free desktop to reduce tearing"
6) Click apply, the entire display will flicker for a moment
7) Click OK
8) Try move windows around and play a video, you will notice perfect movements without tearing and perfect playback of the video as well.

Happy Ubuntu !

---

