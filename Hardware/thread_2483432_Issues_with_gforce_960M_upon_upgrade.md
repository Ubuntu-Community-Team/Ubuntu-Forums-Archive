---
title: "Issues with gforce 960M upon upgrade"
date: 2023-01-30
forum: Hardware
---

### Post by Princey on 2023-01-30
I've been running (K)ubuntu for many years now, solving most mini issues that creep up on my own or with a small Google search. However, lately, I've been stumped with graphical issues upon upgrade. I've been using 20.04 with practically no issues. However, recently, I've been getting pop-ups about end of life support for version 20.04. Further reading pointed me to Kubuntu variant is only supported for 3 years before EOL. So, I upgraded to 22.04 as I prefer the how much KDE offers in terms of customization. My specs are as follows:
Laptop:        Asus ROG GL552VW
Processor :  Intel i7-6700HQ CPU @2.60HZ
Memory:     16GB 
Graphics:    Intel HD Graphics 530 & NVDIDA GFORCE 960 M
HDD:          256 GB M.2 2280 && 1TB SATA 

The laptop runs smoothly enough for minor tasks but when it comes to videos, that's when the issues crop up such as blinking windows, failure of games to run and most programs that run under wine will start blinking or dimming after left unattended for a while. I've installed the nvidia drivers (distro non free) using ubuntu drivers. What I've noticed are:
1. The nvidia control panel doesn't allow to switch to the intel driver using the panel itself like I could when using 20.04. The only options are on demand or performance. 
2. To switch to intel gpu I must use the command "sudo prime select intel" in the command line and reboot.
3. 3d support in whatever virtual machine that I use (vbox or vmware) is like it doesn't exist. No difference in the vm.

```
sudo lshw -c display
``` gives > *-display                 
       description: 3D controller
       product: GM107M [GeForce GTX 960M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:129 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff

```
sudo ubuntu drivers devices
``` yields > == /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd0000139Bsv00001043sd00001C5Dbc03sc02i00
vendor   : NVIDIA Corporation
model    : GM107M [GeForce GTX 960M]
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : nvidia-driver-525 - distro non-free recommended
driver   : nvidia-driver-525-server - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-515 - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-515-server - distro non-free
driver   : nvidia-driver-510 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```
lspci -k | grep -EA3 'VGA|3D|Display'
``` gives ```
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
        Subsystem: ASUSTeK Computer Inc. HD Graphics 530
        Kernel driver in use: i915
        Kernel modules: i915
--
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
        Subsystem: ASUSTeK Computer Inc. GM107M [GeForce GTX 960M]
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```
```
nvidia-smi
``` results in > No devices were found There are two lines of note in kern.log > 33.430600] kernel: [drm:nv_drm_load [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to allocate NvKmsKapiDevice
[   33.430839] kernel: [drm:nv_drm_probe_devices [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to register device

Where do I go from here? Do note, none of those problems existed on 20.04. I even did a system image, wiped everything clean and did a fresh install hoping that it was some detritus from my upgrades over the years. I ran into the same stumbling block with the graphics. Put back 20.04, problem disappeared. I'm stuck as while the system says it recognizes the nvidia gpu and that the drivers is found, the nvidia software itself can't find the card. Using nouveau drivers is even worse. So, currently, games and anything with heavy graphics are a no-go for me. Any help would be appreciated.

2nd Edit:
[CODE[grep -r -E "nouveau|nvidiafb|nvidia" /etc/modprobe.d/[/CODE]Results in:> /etc/modprobe.d/blacklist-framebuffer.conf:blacklist nvidiafb
/etc/modprobe.d/nvidia-graphics-drivers-kms.conf:# This file was generated by nvidia-drivers-510
/etc/modprobe.d/nvidia-graphics-drivers-kms.conf: options nvidia-drm modeset=1

How do I unlist the blacklisted driver? I suspect that to be the issue.

---

### Post by TheFu on 2023-01-31
If you go into the Grub Advanced menu, you can see the older kernels and can probably boot them to see the older nvidia drivers working. Might be a useful exercise to see this before doing anything else.

The driver and the kernel need to work together.  An OS upgrade usually will install a new kernel, so the older kernels and older drivers tied to that kernel aren't too useful.  They can all be removed using 'synaptic' or 'apt' or 'apt-get'.  If it were me, I'd remove nvidia* to clean out all of them, then use the 'ubuntu-drivers' program to install the newest, production, nvidia drivers available and reboot.  We used to be able to use 
```
sudo ubuntu-drivers autoinstall
```
but it seems that was too easy, so the autoinstall option doesn't work any more and we have to specify the specific driver to be installed.  This is beyond my knowledge.  In theory, 'sudo ubuntu-drivers list' will show the drivers that apply to the current system, so from that list, 
```
sudo ubuntu-drivers install  [driver[:version]
```
 can be used. That's the theory.

I'd probably purge any older kernel "lines" from the system, including headers and modules too. Say you were running 20.04 with the 5.4.x kernel line.  22.04 uses the 5.15.x kernel line, so I'd remove any kernels (modules/headers) prior to 5.15.x.

---

### Post by Princey on 2023-01-31
Thanks for the reply. I did that based on the advise in another thread for a different model but same company graphics card. That didn't work. Thankfully, my home directory is on a separate partition so I downloaded a fresh copy of 22.04, wiped everything clean except /home. I deliberately left out installing the nvidia drivers. Nouveau was loaded, couldn't switch to the intel onboard chip so I had to install the nvidia drivers using the Ubuntu drivers command (installed version 515). Same issue. Still couldn't switch to the intel onboard gpu unless I use the command earlier mentioned in my first post. The nvidia settings gives two options, intel one is grayed out. Whether I select on demand or performance, the issue remains and the error of blacklisted modules is present on every boot up.

---

