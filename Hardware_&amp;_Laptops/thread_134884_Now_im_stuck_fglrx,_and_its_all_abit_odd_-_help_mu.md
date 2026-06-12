---
title: "Now im stuck fglrx, and its all abit odd - help much appreciated"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by combat squirrel on 2006-02-22
Hey all did the driver update for my Radeon 9100 AGP card from these instructions:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

all went well, all files complied etc and i even now have the ati control panel under applications

However it doesnt seem to want to be using the ATI driver and carrys on with the mesa driver, went to the xorg.conf and found this:


Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9100 (R200 QM)"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

*************************************** (yes 2 lines for ati stuff)

So obviously changed it to :


Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9100 (R200 QM)"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

*****************************************************

And rebooted, but again its still using the MESA driver, how do i force it use ati's driver?

cheers folks :)

---

### Post by combat squirrel on 2006-02-23
no ideas? :(

---

### Post by combat squirrel on 2006-02-23
Hey all did the driver update for my Radeon 9100 AGP card from these instructions:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

all went well, all files compiled etc and i even now have the ati control panel under applications

However it doesnt seem to want to be using the ATI driver and carrys on with the mesa driver, went to the xorg.conf and found this:


Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9100 (R200 QM)"
Driver "ati"
Option "UseFBDev" "true"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "ATI Graphics Adapter 0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

*************************************** (yes 2 lines for ati stuff)

So obviously changed it to :


Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9100 (R200 QM)"
Driver "fglrx"
Option "UseFBDev" "true"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "ATI Graphics Adapter 0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

************************************************** ***

And rebooted, but again its still using the MESA driver, how do i force it use ati's driver?

cheers folks


88888888888888888888888888888888888888888888888888888888
Could you paste the output of your Xorg.0.log file? (located in /var/log)
Why didn't you run the fglrxconfig tool?
8888888888888888888888888888888888888888888888888888888
__________________

	
Default Re: Discussion: ATI fglrx driver - latest version
Also iv just updated the kernal 2.6.12-10-686
as i was running the 386 version

rmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xe0b74000
(II) fglrx(0): [drm] mapped SAREA 0xe0b74000 to 0xb7a48000
(II) fglrx(0): [drm] framebuffer handle = 0xf0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0): Name: fglrx
(II) fglrx(0): Version: 8.16.20
(II) fglrx(0): Date: Aug 16 2005
(II) fglrx(0): Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0b74000 at 0xb7a48000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed! *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x04000000
(==) fglrx(0): Write-combining range (0xf0000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,76 (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 76

**********************************************************************8
	
Default Re: Discussion: ATI fglrx driver - latest version
ok think iv spotted it myself, 3d driver doesnt match kernal driver. i have JUST updated the 686 kernal driver to 2.6.12-10-686, how do I update this to the required driver from ATI ? I dont have a clue :S

*****************************************************************


ok iv been looking back through this thread and found instructions like:

rm /usr/src/fglrx-kernel*.deb to rebuild the kernal driver for 686 etc, i get the jist of what I have to do:
1)update kernal again to the kernal supported by ati driver
2) rebuild fglrx stuff match this kernal
3) force it to work and load with ubuntu

then should have working 3d acceleration, but im not sure of the commands to type, when i ran rm /usr/src/fglrx-kernel*.deb, it said permission denied

************************************************************************
OK just reinstalled all the ATI stuff, but same prob, not loadin fglrx, same prob as above, PLEASE SOMEONE HELP !

---

