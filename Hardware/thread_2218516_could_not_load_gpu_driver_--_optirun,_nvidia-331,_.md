---
title: "could not load gpu driver -- optirun, nvidia-331, bumblebee"
date: 2014-04-21
forum: Hardware
---

### Post by chimaera666 on 2014-04-21
I recently installed UbuntuGnome 14.04 LTS and to use my nvidia card I installed Bumblebee and the most recent drivers by this guide:

[http://mylinuxexplore.blogspot.be/2014/03/solved-nvidia-cant-access-secondary-gpu.html](http://mylinuxexplore.blogspot.be/2014/03/solved-nvidia-cant-access-secondary-gpu.html)

But when I use optirun, I get the same error over and over again. I purged and reinstalled bumblebee, bumblebee-nvidia and primus but that didn't help. I'm stuck here :-s

My specs

Asus X75VC
UbuntuGnome 14.04LTS
Nvidia GT720M

> optirun -vv glxspheres
[ 1218.747115] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 1218.747585] [DEBUG]optirun version 3.2.1 starting...
[ 1218.747613] [DEBUG]Active configuration:
[ 1218.747629] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 1218.747644] [DEBUG] X display: :8
[ 1218.747655] [DEBUG] LD_LIBRARY_PATH: 
[ 1218.747667] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 1218.747679] [DEBUG] Accel/display bridge: auto
[ 1218.747690] [DEBUG] VGL Compression: proxy
[ 1218.747702] [DEBUG] VGLrun extra options: 
[ 1218.747713] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[ 1218.747762] [DEBUG]Using auto-detected bridge primus
[ 1218.749528] [INFO]Response: No - error: Could not load GPU driver

[ 1218.749559] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 1218.749581] [DEBUG]Socket closed.
[ 1218.749611] [ERROR]Aborting because fallback start is disabled.
[ 1218.749633] [DEBUG]Killing all remaining processes.


> # Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d

## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# [https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods](https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods)

## Section with nvidia driver specific options, only parsed if Driver=**nvidia**
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=**nvidia_331**
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/**nvidia-331**:/usr/lib32/**nvidia-331**
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/**nvidia-331**/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau


Bold is what I have changed, KernelDriver -- I have used nvidia-331 and nvidia_331

> find /lib/modules/$(uname -r) -name 'nvidia*.ko*'
/lib/modules/3.13.0-24-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.13.0-24-generic/updates/dkms/nvidia_331.ko


> find /usr/ -name 'nvidia_drv.so'
/usr/lib/nvidia-331/xorg/nvidia_drv.so


> lspci -k
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
	Kernel driver in use: pcieport
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: mei_me
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
	Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1)
	Subsystem: ASUSTeK Computer Inc. GeForce GT 720M
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8204
	Kernel driver in use: rtl8192ce
04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device 14c7
	Kernel driver in use: alx


if you need any more settings or information just let me now

regards,

Peter

---

### Post by chimaera666 on 2014-04-21
when I completly remove bumblebee-nvidia to remove the nvidia-304 drivers I get an unusable system -- wallpaper but nothing else :-( 

I just don't get it, 'cause when I check via software and update, the additional drivers section, the item "use the 331 ..." is selected

---

