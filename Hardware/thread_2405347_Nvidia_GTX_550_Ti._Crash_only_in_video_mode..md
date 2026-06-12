---
title: "Nvidia GTX 550 Ti. Crash only in video mode."
date: 2018-11-04
forum: Hardware
---

### Post by mazak23 on 2018-11-04
Hi.
I am on Ubuntu 18.04.1 LTS and have PC with graphic card identyfied as :
GF116 Geforce GTX 550 Ti
When watching video in any player some times picture freezes so badly that I cannot do anything, not even switch to other TTY.
But audio is still playing normally.
I am not sure where to search for logs but found only gpu-manager.log , maybe this will tell you something.

> log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-36-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-36-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:1244
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Found "/dev/dri/card0", driven by "nouveau"
output 0:
    card0-HDMI-A-1
Number of connected outputs for /dev/dri/card0: 1
Skipping "/dev/dri/card0", driven by "nouveau"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do



Regards
Mac
PS
sorry if I paste it wrong, as I cannot add that file here

---

### Post by Autodave on 2018-11-05
That card should be using the 410.66 driver. However, that driver is no longer available in the repositories.  It is available from Nvidia's site, but someone else will have to help you with installing that driver, sorry.

---

### Post by mazak23 on 2018-11-05
That is very helpfull. I'm just working on it. Found something.

---

