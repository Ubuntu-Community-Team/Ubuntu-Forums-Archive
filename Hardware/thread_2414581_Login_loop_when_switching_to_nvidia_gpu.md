---
title: "Login loop when switching to nvidia gpu"
date: 2019-03-12
forum: Hardware
---

### Post by torydebra on 2019-03-12
I am get stuck in the (in)famous login loop after installing nvidia gpu drivers. I have Ubuntu 16.04, intel cpu, and nvidia geforce 840m.
  I installed (in various way, see below) driver, but when I switch to nvidia card with sudo prime-select nvidia and reboot, the login loop issue happens. If I switch back to sudo prime-select intel I manage to login.
  Looking here and over the internet I tried various solution:
  
[LIST]
[*]Installing various version of the driver (340, 380, 415, 418) 
[*]Installing them in different ways:
[LIST]
[*]```
sudo apt install nvidia-xxx
``` 
[*]```
sudo apt install nvidia-current
``` 
[*]```
sudo ubuntu-drivers autoinstall
``` 
[*]from software update 
[*]Running the .run file downloaded from nvidia website (last version, 418) 
[/LIST]
  
[*]Restarting lightdm, trying with gdm3 (gnome) 
[*]Secure boot deactivated 
[*].Xauthority check permission, and also remove it 
[*]nomodeset, acpi=off, acpi_osi= (once at time) in the grub before loading ubuntu 
[/LIST]
  Maybe other that will come up in my mind and I will update here.
  Anyone that can help me? I really need to use the nvidia GPU.
  Thanks

---

### Post by him610 on 2019-03-12
You did not say which model of Nvidia GFX you have.
> Installing various version of the driver (340, 380, 415, 418)
You don't need all of those drivers. You only need the one for your GFX. If you have a legacy board it might be 340 and nothing else. If you have a new board, it might be 415+.
I have a GeForce GTX 760 (maybe 3 years old) that tops out with driver 390.116. I always download the recommended drivers from Additional Drivers utility.

---

### Post by torydebra on 2019-03-13
Hi, thanks for answering.

> I have Ubuntu 16.04, intel cpu, and nvidia geforce 840m
I don't have a gtx, I have a Geforce 840m (for laptops) [URL="https://www.notebookcheck.net/NVIDIA-GeForce-840M.105681.0.html"]https://www.notebookcheck.net/NVIDIA-GeForce-840M.105681.0.html

[/URL]I have tried all those drivers because I don't know exactly what I need. From nvidia website, filling the form with gpu version and operating system version, it let me download the 418 (that I tried, and does not work).

I also tried to download from additional drivers utility, all those version, but the problem persists.

/var/log/Xorg.0.log errors **WITH ****340 driver**:
```

[    44.239] (EE) Screen 1 deleted because of no matching config section.
[    44.522] (EE) NVIDIA(0): Failed to initiate mode change.
[    44.522] (EE) NVIDIA(0): Failed to complete mode change

```
```

[  1927.112] (II) Module glx: vendor="NVIDIA Corporation"
[  1927.112] (II) NVIDIA GLX Module  340.107  Thu May 24 21:40:32 PDT 2018
[  1927.112] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1927.113] (II) NVIDIA dlloader X Driver  340.107  Thu May 24 21:18:05 PDT 2018
[  1927.113] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1927.119] (II) NVIDIA(0): Creating default Display subsection in Screen section
[  1927.119] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  1927.119] (==) NVIDIA(0): RGB weight 888
[  1927.119] (==) NVIDIA(0): Default visual is TrueColor
[  1927.119] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1927.119] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[  1927.119] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[  1927.119] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[  1927.119] (**) NVIDIA(0): Enabling 2D acceleration
[  1927.242] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[  1927.243] (II) NVIDIA(0): NVIDIA GPU GeForce 840M (GM108-A) at PCI:3:0:0 (GPU-0)
[  1927.243] (--) NVIDIA(0): Memory: 2097152 kBytes
[  1927.243] (--) NVIDIA(0): VideoBIOS: 82.08.15.00.15
[  1927.243] (II) NVIDIA(0): Detected PCI Express Link width: 4X
[  1927.243] (--) NVIDIA(0): Valid display device(s) on GeForce 840M at PCI:3:0:0
[  1927.243] (--) NVIDIA(0):     none
[  1927.243] (II) NVIDIA(0): Validated MetaModes:
[  1927.243] (II) NVIDIA(0):     "NULL"
[  1927.243] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[  1927.243] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[  1927.243] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[  1927.244] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[  1927.244] (II) NVIDIA:     access.
[  1927.249] (II) NVIDIA(0): Setting mode "NULL"
[  1927.249] (EE) NVIDIA(0): Failed to initiate mode change.
[  1927.249] (EE) NVIDIA(0): Failed to complete mode change
[  1927.258] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[  1927.262] (==) NVIDIA(0): Disabling shared memory pixmaps
[  1927.262] (==) NVIDIA(0): Backing store enabled
[  1927.262] (==) NVIDIA(0): Silken mouse enabled
[  1927.262] (==) NVIDIA(0): DPMS enabled
[  1927.262] (II) NVIDIA(0): [DRI2] Setup complete
[  1927.262] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia

```

/var/log/Xorg.0.log errors **WITH ****387 driver**:
some errors in the log disappear. Black screen at login remains (I only hear the ubuntu init sound).
```
[    47.214] (EE) Screen 1 deleted because of no matching config section.

```
```

[    48.441] (II) Module glx: vendor="NVIDIA Corporation"
[    48.462] (II) NVIDIA GLX Module  390.87  Tue Aug 21 16:10:56 PDT 2018
[    48.687] (II) Module nvidia: vendor="NVIDIA Corporation"
[    48.956] (II) NVIDIA dlloader X Driver  390.87  Tue Aug 21 15:44:49 PDT 2018
[    48.956] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    49.294] (II) NVIDIA(0): Creating default Display subsection in Screen section
[    49.294] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    49.294] (==) NVIDIA(0): RGB weight 888
[    49.294] (==) NVIDIA(0): Default visual is TrueColor
[    49.294] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    49.315] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    49.315] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    49.315] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    49.315] (**) NVIDIA(0): Enabling 2D acceleration
[    49.597] (II) NVIDIA(0): NVIDIA GPU GeForce 840M (GM108-A) at PCI:3:0:0 (GPU-0)
[    49.597] (--) NVIDIA(0): Memory: 2097152 kBytes
[    49.597] (--) NVIDIA(0): VideoBIOS: 82.08.15.00.15
[    49.597] (II) NVIDIA(0): Detected PCI Express Link width: 4X
[    49.597] (II) NVIDIA(0): Validated MetaModes:
[    49.597] (II) NVIDIA(0):     "NULL"
[    49.597] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    49.597] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    49.597] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    49.598] (II) NVIDIA: Using 6144.00 MB of virtual memory for indirect memory
[    49.598] (II) NVIDIA:     access.
[    49.743] (II) NVIDIA(0): Setting mode "NULL"
[    49.910] (==) NVIDIA(0): Disabling shared memory pixmaps
[    49.910] (==) NVIDIA(0): Backing store enabled
[    49.910] (==) NVIDIA(0): Silken mouse enabled
[    49.975] (==) NVIDIA(0): DPMS enabled
[    49.975] (II) NVIDIA(0): [DRI2] Setup complete
[    49.975] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia

```

Until now, to use the pc again I have to ctrl+alt+f1, change gpu with *sudo prime-select intel*, and restart the lightdm service


With nomodeset problem turns in the login loop:
/var/log/Xorg.0.log errors **WITH ****390 driver AND nomodeset option in grub**:
```

[   106.775] (EE) No devices detected.
[   106.780] (EE) [drm] Failed to open DRM device for (null): -2
[   106.781] (EE) Screen 0 deleted because of no matching config section.
[   106.786] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

---

### Post by torydebra on 2019-03-13
Let's say I solved, thanks to bumblebee

From [https://forums.linuxmint.com/viewtopic.php?t=236376](https://forums.linuxmint.com/viewtopic.php?t=236376)
1. Fall back to the noveau driver
2. Reboot
3. Now that the issue is gone, but video quality is not good change the  latest preferred Nvidia driver active again and DO NOT REBOOT
4. Use command line to set Intel card primary - use terminal and command sudo prime-select intel
5. Now You may reboot
6. do not rejoice there is still a missing sofware, perform the following steps in terminal: 
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```
7. Reboot

I also have to solve some config problem with bumblebee :
in /etc/bumblebee/xorg.conf.nvidia :

replace nvidia current with nvidia-390

and add


```

  Section "Screen"
         Identifier "Default Screen"
         Device "DiscreteNvidia"
     EndSection

```
at the end of the file[FONT=arial]


[/FONT][FONT=arial]now when I want use a program with nvidia gpu i launch it with optirun. 
Currently I am using nvidia driver-390 but *nvidia-prime query* return* intel* 
[/FONT]

---

