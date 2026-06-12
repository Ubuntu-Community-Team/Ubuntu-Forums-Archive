---
title: "Lightdm won't start with Nvidia driver"
date: 2014-09-28
forum: Hardware
---

### Post by Kim Foltz on 2014-09-28
I am running Kubuntu 14.04 with kernel 3.13.0-36-generic. The video card is an GEFORCE 8400GS. System runs fine with nouveau driver but I lose sleep mode. Several Nvidia drivers install and boot until the point Lightdm should show the login screen and then the boot crashes. The same thing happens with Kdm as the display manager. Booting in Recovery Mode will produce the error initctl: Event Failed when the login screen should display. Signing on in terminal mode and attempting to start Kdm produces the message Kdm is already running. StartX doesn't run. I can purge the Nvidia drivers and reboot with nouveau but I would like to have sleep mode working. 

lspci -vnn | grep -i VGA -A 12 shows:

02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] [10de:10c3] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: eVga.com. Corp. Device [3842:1300]
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at ce000000 (64-bit, prefetchable) [size=32M]
        I/O ports at ec00 [size=128]
        Expansion ROM at fcf80000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nouveau

02:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
        Subsystem: eVga.com. Corp. Device [3842:1300]
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fcf7c000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel

Xorg log shows in part:

[   115.861] (WW) Falling back to old probe method for modesetting
[   115.861] (WW) Falling back to old probe method for fbdev
[   115.861] (II) Loading sub module "fbdevhw"
[   115.861] (II) LoadModule: "fbdevhw"
[   115.862] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   115.862] (II) Module fbdevhw: vendor="X.Org Foundation"
[   115.862] 	compiled for 1.15.1, module version = 0.0.2
[   115.862] 	ABI class: X.Org Video Driver, version 15.0
[   115.862] (EE) open /dev/fb0: No such file or directory
[   115.862] (WW) Falling back to old probe method for vesa
[   115.862] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   115.862] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   115.862] (==) NVIDIA(0): RGB weight 888
[   115.862] (==) NVIDIA(0): Default visual is TrueColor
[   115.862] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   115.863] (**) NVIDIA(0): Enabling 2D acceleration
[   115.912] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[   115.912] (EE) NVIDIA(GPU-0):     check your system's kernel log for additional error
[   115.913] (EE) NVIDIA(GPU-0):     messages and refer to Chapter 8: Common Problems in the
[   115.913] (EE) NVIDIA(GPU-0):     README for additional information.
[   115.913] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA graphics device!
[   115.913] (EE) NVIDIA(0): Failing initialization of X screen 0
[   115.913] (II) UnloadModule: "nvidia"
[   115.913] (II) UnloadSubModule: "wfb"
[   115.913] (II) UnloadSubModule: "fb"
[   115.913] (EE) Screen(s) found, but none have a usable configuration.


Syslog shows in part:
Sep 28 13:15:46 tennis-fan kernel: [   19.232609] nvidia 0000:02:00.0: irq 43 for MSI/MSI-X
Sep 28 13:15:46 tennis-fan avahi-daemon[1095]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::250:baff:feb3:6ac.
Sep 28 13:15:46 tennis-fan avahi-daemon[1095]: New relevant interface eth0.IPv6 for mDNS.
Sep 28 13:15:46 tennis-fan avahi-daemon[1095]: Registering new address record for fe80::250:baff:feb3:6ac on eth0.*.
Sep 28 13:15:46 tennis-fan kernel: [   19.525610] alloc_vmap_area: 114 callbacks suppressed
Sep 28 13:15:46 tennis-fan kernel: [   19.525614] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
Sep 28 13:15:46 tennis-fan kernel: [   19.525811] NVRM: RmInitAdapter failed! (0x25:0xffffffff:1156)
Sep 28 13:15:46 tennis-fan kernel: [   19.525818] NVRM: rm_init_adapter failed for device bearing minor number 0
Sep 28 13:15:46 tennis-fan kernel: [   19.525838] NVRM: nvidia_frontend_open: minor 0, module->open() failed, error -5
Sep 28 13:15:46 tennis-fan kdm[1018]: X server died during startup
Sep 28 13:15:46 tennis-fan kdm[1018]: X server for display :0 cannot be started, session disabled


Anyone know how to get Nvidia's proprietary drivers to work in 14.04?

---

### Post by kc1di on 2014-09-28
According[ to Nvidia]("http://www.geforce.com/drivers") the 334.x driver should work with that card.

But it's not in the Ubuntu repository. so there are two ways to get it. 

1. add the the xswat ppa - it goes up to 331. which may work.  [Here's how.]("http://askubuntu.com/questions/467743/how-do-i-install-nvidia-graphics-drivers-from-x-swat-ppa")

2. download 340.x driver[ from the Nvidia]("http://www.geforce.com/drivers") site and manually install it.  

Good luck

---

### Post by Kim Foltz on 2014-09-28
Driver 340.xx is recommended from xorg-edgers. It installs cleanly but has the problems described with Lightdm and Kdm. Driver 331.38 is recommended when using xswat and it installs cleanly but has the same problems. Driver 304.117 is recommended when nvidia-common is used and it produces the same results. All install cleanly and the system boots all the way to the sign-in screen before failing.

---

### Post by Kim Foltz on 2014-09-30
If I wanted to try removing lightdm and light locker and return to Kdm and xscreensaver how would I do that? Is it a simple purge and install?

---

### Post by kc1di on 2014-10-01
try this:

```
sudo apt-get purge lightdm
sudo apt-get install kdm
```

---

