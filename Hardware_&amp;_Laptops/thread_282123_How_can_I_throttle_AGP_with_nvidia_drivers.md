---
title: "How can I throttle AGP with nvidia drivers"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by savagex on 2006-10-22
Hello,

I encounter random X freezes with nvidia drivers (X at 99% CPU load, machine still responds to pings and I an log in via ssh to kill the X server - but I'd love to get rid of that). It seems there is no wonder cure for this problem.

However, if I switch the gfx card to PCI mode (option NvAGP 0 in xorg.conf) it's much more stable.

By default the card is driven in AGP 8x mode with SBA enabled. I'd love to throttle it back to 4x without SBA.

I tried several ways, nothing worked.

/etc/modprobe.d/nvidia-kernel-nkc:

> 
alias char-major-195* nvidia
options NVreg_EnableAGPSBA=0 NVreg_ReqAGPRate=4


/etc/modprobe.de/options

> # Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

options nvidia NVreg_EnableAGPSBA=0 NVreg_ReqAGPRate=4

/etc/X11/xorg.conf

> Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800 LE]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
#       Option          "RenderAccel"   "false"
#       Option          "NvAGP"         "0"
        Option          "AGPMode"       "4"
EndSection



It seems AGPGART is compiled into the Ubuntu standard kernel - but I can't find a reference with kernel boot options to configure AGPGART.

Anybody an idea?

---

### Post by tuke81 on 2006-10-29
Well do you use agpgart by linux kernel, nvagp might be more stable for you. Check what says **lsmod | grep agpgart**, if there is something like intel_agp via_agp or what ever similar, you have to blacklist them to get nvagp to work. I had via_agp so I did the following:

**sudo nano /etc/modprobe.d/blacklist**
And added following lines bottom of the file:
**blacklist via_agp**
**blacklist agpgart**

And next I had to configure my xorg.conf to use nvidias agpgart:
**sudo nano /etc/X11/xorg.conf**
in device section or screen section add following:
**Option         "NvAGP" "1"**
And reboot computer.

After booting dmesg should show:
[B]tuke@tippawaara:~$ dmesg | grep agp
[   39.623391] Linux agpgart interface v0.101 (c) Dave Jones[/B]

And agp status should be something like:
[B]tuke@tippawaara:~$ cat /proc/driver/nvidia/agp/status 
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
[/B]
(HOX Driver is NVIDIA not agpgart)

If everything runs fine and x is stable, then tux can smile again :mrgreen:

---

