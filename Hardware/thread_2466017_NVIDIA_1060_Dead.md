---
title: "NVIDIA 1060 Dead?"
date: 2021-08-17
forum: Hardware
---

### Post by jack-stokers on 2021-08-17
Hi everyone!

I have dabbled with linux in the past but am very much a noob when it comes to software and hardware.

Basically I have a MSI GS65 stealth that comes with a 1060 mobile graphics card. The laptop ran really well for a few years and then i broke the screen so let it sit for a few months before getting it repaired. When i did get it repaired the blokes fixing it told me they couldn't get the computer to run off the gpu and that it was stuck on integrated graphics. They tried everything they knew from within windows and even had a contact at MSI run through some stuff with them and couldn't get it to work. The general consensus was the gpu was cooked.

Anyways, thought i'd play around with ubuntu because by all accounts the integrated graphics is fine for everything apart from gaming. But now that I am here with the brains trust I wanted to see if anyone had an ideas on how to fix it. 

Here's what I have done so far and what I have come up against 

- clean install of ubuntu 
- downloaded recommended graphics driver
- nvidia-settings to change from intel graphics to NVIDIA

now here's where im getting error codes. 

$ nvidia-settings

ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system


(nvidia-settings:4579): GLib-GObject-CRITICAL **: 09:28:26.563: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 09:28:26.565: PRIME: Requires offloading
** Message: 09:28:26.565: PRIME: is it supported? yes
** Message: 09:28:26.588: PRIME: Usage: /usr/bin/prime-select nvidia|intel|on-demand|query
** Message: 09:28:26.588: PRIME: on-demand mode: "1"
** Message: 09:28:26.588: PRIME: is "on-demand" mode supported? yes


I have looked through an NVIDIA developers forum and it talked about getting a bug report through terminal which I have but have not attached. 

What are ya'll thinking, any other checks I can run?

---

### Post by Bashing-om on 2021-08-17
jack-stokers; Welcome to the Forum 

Well ...

We can take a stab at it and see what we come up with :D

Post back - between code tags - the outputs of terminal commands:
```

inxi -GCS
sudo lshw -C display
dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

which tells us your hardware, state of the driver install, and what the driver manager thinks.

[INDENT]a tale gets told
[/INDENT]

---

### Post by jack-stokers on 2021-08-17
Awesome! Ok here goes:

inxi GCS

```

$ inxi -GCS
System:
  Host: Learn Kernel: 5.11.0-27-generic x86_64 bits: 64 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
CPU:
  Topology: 6-Core model: Intel Core i7-8750H bits: 64 type: MT MCP 
  L2 cache: 9216 KiB 
  Speed: 800 MHz min/max: 800/4100 MHz Core speeds (MHz): 1: 880 2: 3779 
  3: 2666 4: 1784 5: 1202 6: 1036 7: 800 8: 800 9: 800 10: 800 11: 800 
  12: 800 
Graphics:
  Device-1: Intel UHD Graphics 630 driver: i915 v: kernel 
  Device-2: NVIDIA GP106M [GeForce GTX 1060 Mobile] driver: N/A 
  Display: x11 server: X.Org 1.20.9 driver: N/A resolution: 1920x1080~144Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2) v: 4.6 Mesa 21.0.3 

```

sudo lshw -C display 
```

$ sudo lshw -C display
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GP106M [GeForce GTX 1060 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:ac000000-acffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:4000(size=128) memory:ad000000-ad07ffff
  *-display
       description: VGA compatible controller
       product: UHD Graphics 630 (Mobile)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:159 memory:ab000000-abffffff memory:40000000-4fffffff ioport:5000(size=64) memory:c0000-dffff

```
dpkg -l | grep -i nvidia

```

$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-470:amd64                   470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-470                       470.57.02-0ubuntu0.20.04.1          all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-470:amd64                470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA libcompute package
ii  libnvidia-compute-470:i386                 470.57.02-0ubuntu0.20.04.1          i386         NVIDIA libcompute package
ii  libnvidia-decode-470:amd64                 470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-470:i386                  470.57.02-0ubuntu0.20.04.1          i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-470:amd64                 470.57.02-0ubuntu0.20.04.1          amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-470:i386                  470.57.02-0ubuntu0.20.04.1          i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-470:amd64                  470.57.02-0ubuntu0.20.04.1          amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-470:amd64                   470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-470:i386                    470.57.02-0ubuntu0.20.04.1          i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-470:amd64                     470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-470:i386                      470.57.02-0ubuntu0.20.04.1          i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-470:amd64                   470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-470:i386                    470.57.02-0ubuntu0.20.04.1          i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-340                                 340.108-0ubuntu5.20.04.2            amd64        NVIDIA binary driver - version 340.108
ii  nvidia-compute-utils-470                   470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA compute utilities
ii  nvidia-dkms-470                            470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA DKMS package
ii  nvidia-driver-470                          470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-470                   470.57.02-0ubuntu0.20.04.1          amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-470                   470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA kernel source package
rc  nvidia-opencl-icd-340                      340.108-0ubuntu5.20.04.2            amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                               0.8.16~0.20.04.1                    all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            470.57.01-0ubuntu0.20.04.1          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-470                           470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18build1                          all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-470              470.57.02-0ubuntu0.20.04.1          amd64        NVIDIA binary Xorg driver

```

cat /var/log/gpu-manager.log\
```

$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.11.0-27-generic/updates/dkms
Found nvidia module: nvidia-modeset.ko
Looking for amdgpu modules in /lib/modules/5.11.0-27-generic/updates/dkms
Is nvidia loaded? no
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
Vendor/Device Id: 8086:3e9b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c20
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver.
can't access /etc/u-d-c-nvidia-runtimepm-override file
can't open /sys/module/nvidia/version
Warning: cannot check the NVIDIA driver major version
Support for runtimepm not detected.
You can override this check at your own risk by creating the /etc/u-d-c-nvidia-runtimepm-override file.
Is nvidia runtime pm supported for "0x1c20"? no
Checking power status in /proc/driver/nvidia/gpus/0000:01:00.0/power
Error while opening /proc/driver/nvidia/gpus/0000:01:00.0/power
Is nvidia runtime pm enabled for "0x1c20"? no
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? no
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
NVIDIA hybrid system
Creating /usr/share/X11/xorg.conf.d/11-nvidia-offload.conf
Setting power control to "auto" in /sys/bus/pci/devices/0000:01:00.0/power/control
Loading nvidia with "no" parameters

``` 

Thanks!

---

### Post by Bashing-om on 2021-08-17
jack-stokers - Well

The good news is that the Nvidia card is seen; and that the correct driver is verified.
[https://www.nvidia.com/Download/driverResults.aspx/179599/en-us](https://www.nvidia.com/Download/driverResults.aspx/179599/en-us)

However - the bad news is that the driver fails to load :(

> 
6-Core model: Intel Core i7


I can accept that it is a UEFI system and as such that secure boot is a factor here.
show us:
```

mokutil --sb-state

```

as the Nvidia driver is 3rd party, secure boot must be disabled.

-gots to be a way-


and we consider what it will take to get the driver to load

---

### Post by jack-stokers on 2021-08-17
Hmmm ok. 
```

$ mokutil --sb-state
SecureBoot enabled

```

---

### Post by Bashing-om on 2021-08-17
jack-stokers; Uh Huh :D

Secure boot is doing its job.

OK, ya can guess what comes next.

In your bios firmware disable secure boot - you can re-enable once the Nvidia driver is loaded.

now let's see what results:
```

sudo apt remove --purge nvidia-*
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```

reboot to see the effect
[INDENT][INDENT]all better now ?
[/INDENT][/INDENT]

---

### Post by jack-stokers on 2021-08-18
im actually having trouble accessing the bios menu when i reboot the pc. it used to be F11 but now that only gives me one option which is to just boot in ubuntu.

---

### Post by Bashing-om on 2021-08-18
jack-stokers; Sorry

can not help much there as I know nothing of the i7 hardware. However, I would expect the path to the firmware to be long before you have a system boot option. Many times when booting, on the firmware splash screen is the advisory of which key accesses the firmware settings.

[INDENT]a know it all I am not
[/INDENT]

---

### Post by jack-stokers on 2021-08-18
OK FOUND IT!

however the three options I had were 

Boot mode select
- UEFI with CSM
-LEGACY
-UEFI

I changed it to legacy and it came up with a black screen stating
```

"INTEL UNDI, PXE-2.0 (build 083)
copyright (c) 1997-2000 Intel corporation

For Qualcom Atheros PCIE Ethernet Controller v2.1.1.5 (03/15/13)

Check cable connection! 

PXE-M0F: Exiting PXE ROM

Reboot and select proper boot device
or insert Boot Media in selected Boot device and press a key"

```

Booted into UEFI again to come back to the forum, started fine

---

### Post by jack-stokers on 2021-08-18
Now that I look at what I've done I realise that's probably not secure boot is it lol. I'll have to go back and have a look when I get home

---

### Post by Bashing-om on 2021-08-18
jack-stokers; welp

You are confusing what you are seeking.
Perfectly understandable with those boot options that in legacy mode does not boot.
There are 2 implements of boot code
1) in legacy where the boot code to boot the system resides in the (M) (B)oot (R)ecord
2) in UEFI where the boot code resides in a (E)fi (S)ystem (P)artition 
the two are incompatible, however if set up properly then there is the dual option "UEFI with CSM" - (C)ompatiblity (S)upport (M)odule.

Now that said, keep looking for the secure boot settings.
Maybe here Google is your close friend ?

[INDENT][INDENT]in the process
[INDENT][INDENT]of learning your system
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jack-stokers on 2021-08-18
Ok so its done. 

The only thing that looks odd is this 
```

 sudo ubuntu-drivers autoinstall
[sudo] password for jack: 
WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32gcc-s1 libc6-i386 libllvm11
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

---

### Post by jack-stokers on 2021-08-18
A couple of other notes to be made: 

```

$ nvidia-settings

ERROR: Unable to load info from any available system


(nvidia-settings:3089): GLib-GObject-CRITICAL **: 19:13:59.219: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 19:13:59.222: PRIME: Requires offloading
** Message: 19:13:59.222: PRIME: is it supported? yes
** Message: 19:13:59.245: PRIME: Usage: /usr/bin/prime-select nvidia|intel|on-demand|query
** Message: 19:13:59.245: PRIME: on-demand mode: "1"
** Message: 19:13:59.245: PRIME: is "on-demand" mode supported? yes


``` 

and when i re-ran one of the commands you had given me it said yes instead of no to the nvidia driver being installed

---

### Post by Bashing-om on 2021-08-18
jack-stokers; Hummm...

Looks to be advisories rather than errors,
However -
what shows:
```

sudo dkms status
dpkg -l | grep -i nvidia

```

[INDENT]we seek perfection
[/INDENT]

---

### Post by jack-stokers on 2021-08-18
```

$ sudo dkms status
[sudo] password for jack: 
nvidia, 470.57.02, 5.11.0-27-generic, x86_64: installed

```

and 

```

$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-470:amd64                   470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-470                       470.57.02-0ubuntu0.20.04.1            all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-470:amd64                470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-compute-470:i386                 470.57.02-0ubuntu0.20.04.1            i386         NVIDIA libcompute package
ii  libnvidia-decode-470:amd64                 470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-470:i386                  470.57.02-0ubuntu0.20.04.1            i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-470:amd64                 470.57.02-0ubuntu0.20.04.1            amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-470:i386                  470.57.02-0ubuntu0.20.04.1            i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-470:amd64                  470.57.02-0ubuntu0.20.04.1            amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-470:amd64                   470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-470:i386                    470.57.02-0ubuntu0.20.04.1            i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-470:amd64                     470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-470:i386                      470.57.02-0ubuntu0.20.04.1            i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-470:amd64                   470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-470:i386                    470.57.02-0ubuntu0.20.04.1            i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-340                                 340.108-0ubuntu5.20.04.2              amd64        NVIDIA binary driver - version 340.108
ii  nvidia-compute-utils-470                   470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA compute utilities
ii  nvidia-dkms-470                            470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA DKMS package
ii  nvidia-driver-470                          470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-470                   470.57.02-0ubuntu0.20.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-470                   470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA kernel source package
rc  nvidia-opencl-icd-340                      340.108-0ubuntu5.20.04.2              amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                               0.8.16~0.20.04.1                      all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            470.57.01-0ubuntu0.20.04.1            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-470                           470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18build1                            all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-470              470.57.02-0ubuntu0.20.04.1            amd64        NVIDIA binary Xorg driver

```

---

### Post by Bashing-om on 2021-08-18
jack-stokers ; Looks good.

working with no perceived issues now ?

I might suggest removing the "rc" [(R)emoved but (C)onfig files remain)} stragglers.
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

[INDENT]me likes
[INDENT][INDENT]clean behind
[/INDENT][/INDENT][/INDENT]

---

### Post by jack-stokers on 2021-08-18
How do I know it's running off the gpu and not integrated graphics? When I run 

```

$ inxi -GCS
System:
  Host: Learn Kernel: 5.11.0-27-generic x86_64 bits: 64 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
CPU:
  Topology: 6-Core model: Intel Core i7-8750H bits: 64 type: MT MCP 
  L2 cache: 9216 KiB 
  Speed: 800 MHz min/max: 800/4100 MHz Core speeds (MHz): 1: 842 2: 3784 
  3: 3183 4: 2204 5: 1126 6: 800 7: 800 8: 1147 9: 800 10: 800 11: 800 
  12: 800 
Graphics:
  Device-1: Intel UHD Graphics 630 driver: i915 v: kernel 
  Device-2: NVIDIA GP106M [GeForce GTX 1060 Mobile] driver: nvidia 
  v: 470.57.02 
  Display: x11 server: X.Org 1.20.11 driver: modesetting FAILED: nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 1920x1080~144Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2) v: 4.6 Mesa 21.0.3 

``` 

Doesn't ```
 OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2) v: 4.6 Mesa 21.0.3 
``` 
mean it's operating off integrated graphics? 

```

$ dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
(Reading database ... 190608 files and directories currently installed.)
Purging configuration files for nvidia-340 (340.108-0ubuntu5.20.04.2) ...
userdel: user nvidia-persistenced is currently used by process 865
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-opencl-icd-340 (340.108-0ubuntu5.20.04.2) ...
Processing triggers for initramfs-tools (0.136ubuntu6.6) ...
update-initramfs: Generating /boot/initrd.img-5.11.0-27-generic
jack@Learn:~$ dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P$ dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
dpkg: error: unknown option -$

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
dpkg: error: --purge needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
jack@Learn:~$ (Reading database ... 190608 files and directories currently installed.)
Reading: command not found
jack@Learn:~$ Purging configuration files for nvidia-340 (340.108-0ubuntu5.20.04.2) ...
bash: syntax error near unexpected token `('
jack@Learn:~$ userdel: user nvidia-persistenced is currently used by process 865
 
Command 'userdel:' not found, did you mean:

  command 'userdel' from deb passwd (1:4.8.1-1ubuntu5.20.04.1)

Try: sudo apt install <deb name>

jack@Learn:~$ update-initramfs: deferring update (trigger activated)
bash: syntax error near unexpected token `('
jack@Learn:~$ Purging configuration files for nvidia-opencl-icd-340 (340.108-0ubuntu5.20.04.2)$ dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
bash: syntax error near unexpected token `('
jack@Learn:~$ (Reading database ... 190608 files and directories currently installed.)
Reading: command not found
jack@Learn:~$ Purging configuration files for nvidia-340 (340.108-0ubuntu5.20.04.2) ...
bash: syntax error near unexpected token `('
jack@Learn:~$ userdel: user nvidia-persistenced is currently used by process 865
 
Command 'userdel:' not found, did you mean:

  command 'userdel' from deb passwd (1:4.8.1-1ubuntu5.20.04.1)

Try: sudo apt install <deb name>

jack@Learn:~$ update-initramfs: deferring update (trigger activated)
bash: syntax error near unexpected token `('
jack@Learn:~$ Purging configuration files for nvidia-opencl-icd-340 (340.108-0ubuntu5.20.04.2)$ dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
bash: syntax error near unexpected token `('
jack@Learn:~$ (Reading database ... 190608 files and directories currently installed.)
Reading: command not found
jack@Learn:~$ Purging configuration files for nvidia-340 (340.108-0ubuntu5.20.04.2) ...
bash: syntax error near unexpected token `('
jack@Learn:~$ userdel: user nvidia-persistenced is currently used by process 865
 
Command 'userdel:' not found, did you mean:

  command 'userdel' from deb passwd (1:4.8.1-1ubuntu5.20.04.1)

Try: sudo apt install <deb name>

jack@Learn:~$ update-initramfs: deferring update (trigger activated)
bash: syntax error near unexpected token `('
jack@Learn:~$ Purging configuration files for nvidia-opencl-icd-340 (340.108-0ubuntu5.20.04.2)jack@Learn:~$ Purging configuration files for nvidia-opencl-icd-340 (340.108-0ubuntu5.20.04.2)
bash: syntax error near unexpected token `('


```

---

### Post by Bashing-om on 2021-08-18
jack-stokers; Yuk

It is difficult for me to follow your thought process.
1)
> 
How do I know it's running off the gpu and not integrated graphics?


what shows:
```

dpkg -l nvidia-prime
prime-select query

```

2) and as to the update-initramfs; I have never seen it used without appropriate switches and operators.

3) userdel - again needs a target to work - also please see:
```

man userdel

```
(q to quit)
that the command is depreciated in favor of "deluser".

[INDENT]stupid computer
[INDENT][INDENT]will not read our minds
[/INDENT][/INDENT][/INDENT]

---

### Post by jack-stokers on 2021-08-18
Ok so

```

$ dpkg -l nvidia-prime
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version          Architecture Description
+++-==============-================-============-==============================>
ii  nvidia-prime   0.8.16~0.20.04.1 all          Tools to enable NVIDIA's Prime

```

```

$ prime-select query
nvidia

```

---

### Post by Bashing-om on 2021-08-18
jack-stokers; Hey :D

In this invocation you are indeed using the Nvidia card - 

[INDENT][INDENT]sweat condition 10 terminated ?
[/INDENT][/INDENT]

---

### Post by jack-stokers on 2021-08-18
Really? I tried to run OpenGL as a benchmarking tool 

```

sudo apt-get install glmark2

```

And ran it using 
```

glmark2 --fullscreen --show-all-options

```

and got 
```

$ glmark2 --fullscreen --show-all-options
=======================================================
    glmark2 2021.02
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel
    GL_RENDERER:   Mesa Intel(R) UHD Graphics 630 (CFL GT2)
    GL_VERSION:    4.6 (Compatibility Profile) Mesa 21.0.3
=======================================================
[build] duration=10.0:fps-pos=-1.0,-1.0:fps-size=0.03:fragment-precision=default,default,default,default:interleave=false:model=horse:nframes=:show-fps=false:title=:title-pos=-0.7,-1.0:title-size=0.03:use-vbo=false:vertex-precision=default,default,default,default: FPS: 2212 FrameTime: 0.452 ms
[build] duration=10.0:fps-pos=-1.0,-1.0:fps-size=0.03:fragment-precision=default,default,default,default:interleave=false:model=horse:nframes=:show-fps=false:title=:title-pos=-0.7,-1.0:title-size=0.03:use-vbo=true:vertex-precision=default,default,default,default: FPS: 2452 FrameTime: 0.408 ms
[texture] duration=10.0:fps-pos=-1.0,-1.0:fps-size=0.03:fragment-precision=default,default,default,default:model=cube:nframes=:show-fps=false:texgen=false:texture=crate-base:texture-filter=nearest:title=:title-pos=-0.7,-1.0:title-size=0.03:vertex-precision=default,default,default,default: FPS: 2462 FrameTime: 0.406 ms
[texture] duration=10.0:fps-pos=-1.0,-1.0:fps-size=0.03:fragment-precision=default,default,default,default:model=cube:nframes=:show-fps=false:texgen=false:texture=crate-base:texture-filter=linear:title=:title-pos=-0.7,-1.0:title-size=0.03:vertex-precision=default,default,default,default: FPS: 2475 FrameTime: 0.404 ms
[texture] duration=10.0:fps-pos=-1.0,-1.0:fps-size=0.03:fragment-precision=default,default,default,default:model=cube:nframes=:show-fps=false:texgen=false:texture=crate-base:texture-filter=mipmap:title=:title-pos=-0.7,-1.0:title-size=0.03:vertex-precision=default,default,default,default: FPS: 2476 FrameTime: 0.404 ms
[shading] duration=10.0:fps-pos=-1.0,-1.0:fps-size=0.03:fragment-precision=default,default,default,default:model=cat:nframes=:num-lights=1:shading=gouraud:show-fps=false:title=:title-pos=-0.7,-1.0:title-size=0.03:vertex-precision=default,default,default,default: FPS: 1882 FrameTime: 0.531 ms
=======================================================
                                  glmark2 Score: 2326 

```

---

### Post by Bashing-om on 2021-08-18
jack-stokers; umph

As I do not run dual graphics I am unable to duplicate.
However one can test and see what is taking place:
 You could try either - 
switch to intel, reboot, switch to nvidia, reboot, i.e
```

sudo prime-select intel
reboot
prime-select query


sudo prime-select nvidia
reboot
prime-select query

```

are the results as expected ?

[INDENT][INDENT]testing is good
[/INDENT][/INDENT]

---

### Post by jack-stokers on 2021-08-18
I think you might have done it! :D thank you so much for your help. Will run some more tests

---

### Post by Bashing-om on 2021-08-18
jack-stokers; Good deal :D

if this resolves the originating question -

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

and open a new thread on new issues.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

