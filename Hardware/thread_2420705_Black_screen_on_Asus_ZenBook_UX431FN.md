---
title: "Black screen on Asus ZenBook UX431FN"
date: 2019-06-09
forum: Hardware
---

### Post by robertorossetti3-14 on 2019-06-09
Hi

I'm trying to install Ubuntu 18.04.02 on my [Asus ZenBook UX431FN]("https://www.asus.com/it/Laptops/ASUS-ZenBook-14-UX431FN/") but I've many problem to solve a black screen issue.

to install Ubuntu i've to add nomodeset option to grub, in this way I can start the install of s.o. 
then I've installed the Nvidia driver for the MX150 graphic card with the command ubuntu-drivers install

everything seems to be going well but when I reboot i'me stuk in a completely black screen and also pressing alt+f2 to swith to another tty the screen still black
so adding again the nomodeset option i can login to the terminal, get the ip address so i can login via ssh

here some infos:

```
gx@bombozen:~$ sudo lshw -C display
[sudo] password di gx: 
  *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: iomemory:600-5ff iomemory:400-3ff irq:146 memory:6012000000-6012ffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GP108M [GeForce MX150]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:600-5ff iomemory:600-5ff irq:147 memory:80000000-80ffffff memory:6000000000-600fffffff memory:6010000000-6011ffffff ioport:3000(size=128) memory:81000000-8107ffff

```

```
gx@bombozen:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.18.0-21-generic/updates/dkms
Found nvidia module: nvidia-uvm.ko
Looking for amdgpu modules in /lib/modules/4.18.0-21-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:3ea0
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1d12
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Intel hybrid system
Creating /usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
Setting power control to "on" in /sys/bus/pci/devices/0000:01:00.0/power/control

```

```
gx@bombozen:~$ sudo nvidia-smi
Sun Jun  9 16:56:59 2019       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.116                Driver Version: 390.116                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce MX150       Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   37C    P8    N/A /  N/A |      0MiB /  2002MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```
```
gx@bombozen:~$ cat /usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
# DO NOT EDIT. AUTOMATICALLY GENERATED BY gpu-manager


Section "OutputClass"
    Identifier "Nvidia Prime"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    Option "IgnoreDisplayDevices" "CRT"
    Option "PrimaryGPU" "Yes"
    ModulePath "/x86_64-linux-gnu/nvidia/xorg"
EndSection

```
```
gx@bombozen:~$ tail -n 400 -f /var/log/syslog | grep -i nvidia
Jun  9 16:54:47 bombozen systemd[1]: Starting NVIDIA Persistence Daemon...
Jun  9 16:54:47 bombozen nvidia-persistenced: Verbose syslog connection opened
Jun  9 16:54:47 bombozen nvidia-persistenced: Now running with user ID 122 and group ID 127
Jun  9 16:54:47 bombozen systemd[1]: Started NVIDIA Persistence Daemon.
Jun  9 16:54:47 bombozen nvidia-persistenced: Started (1018)
Jun  9 16:54:47 bombozen nvidia-persistenced: device 0000:01:00.0 - registered
Jun  9 16:54:47 bombozen nvidia-persistenced: Local RPC service initialized

```
Thanks in advance to everyone

---

### Post by debbs2 on 2019-07-17
I'm facing the same issue, have you made any progress?

---

### Post by debbs2 on 2019-07-23
It's a problem with edid version 2.4 ([https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1821533](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1821533)).
Mine worked with "nomodeset", but you can plug it to an hdmi monitor as well (it works).

Here is the workaround:
1. download 1920x1080.bin from here ([https://github.com/akatrevorjay/edid-generator/blob/master/1920x1080.bin](https://github.com/akatrevorjay/edid-generator/blob/master/1920x1080.bin))
2. move it to /lib/firmware/edid/
3. edit /etc/default/grub and add this GRUB_CMDLINE_LINUX_DEFAULT="**drm.edid_firmware=eDP-1:edid/1920x1080.bin**"
4. run sudo update-grub
5. restart the computer

---

