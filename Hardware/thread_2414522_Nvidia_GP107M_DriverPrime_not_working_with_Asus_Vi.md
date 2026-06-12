---
title: "Nvidia GP107M Driver/Prime not working with Asus Vivobook w/ Ryzen 5"
date: 2019-03-11
forum: Hardware
---

### Post by buffalobuffalobuffalo on 2019-03-11
I recently bought an Asus K570ZD with a Ryzen 5 APU and GTX 1050 Mobile GPU. I cannot get prime to work correctly and am unable to use the nvidia card. 

*(I had to add nouveau.modeset=0 to grub to get the computer to not freeze as soon as I login, I assume this can stay set to 0?). *

I then tried installing the nvidia proprietary drivers but when I open nvidia-settings I get an error message:

```

ERROR: Error querying enabled displays on GPU 0 (Missing Extension).


ERROR: Error querying connected displays on GPU 0 (Missing Extension).

** Message: 17:50:20.567: PRIME: No offloading required. Abort
** Message: 17:50:20.567: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.

```

I have tried to use the following commands found here: [https://ubuntuforums.org/showthread.php?t=2377560](https://ubuntuforums.org/showthread.php?t=2377560) to purge and reinstall but with the same results

```

sudo apt purge nvidia*
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade
```

secureboot is already disabled and mokutil --sb-state returns "SecureBoot disabled".

Here is my system info from inxi:

```
chase@chase-VivoBook-ASUSLaptop-X570ZD-K570ZD:~$ inxi -GFxxz
System:
  Host: chase-VivoBook-ASUSLaptop-X570ZD-K570ZD 
  Kernel: 4.18.0-16-generic x86_64 bits: 64 compiler: gcc v: 8.2.0 
  Desktop: Gnome 3.30.2 wm: gnome-shell dm: GDM3 
  Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Laptop System: ASUSTeK product: VivoBook_ASUSLaptop X570ZD_K570ZD 
  v: 1.0 serial: <filter> 
  Mobo: ASUSTeK model: X570ZD v: 1.0 serial: <filter> 
  UEFI: American Megatrends v: X570ZD.304 date: 08/29/2018 
Battery:
  ID-1: BAT0 charge: 47.1 Wh condition: 47.1/48.1 Wh (98%) volts: 11.7/11.7 
  model: ASUSTeK ASUS Battery serial: <filter> status: Not charging 
CPU:
  Topology: Quad Core model: AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx 
  bits: 64 type: MT MCP arch: Zen L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 31940 
  Speed: 1507 MHz min/max: 1600/2000 MHz Core speeds (MHz): 1: 1460 2: 1437 
  3: 1425 4: 1370 5: 1471 6: 1502 7: 1493 8: 1484 
Graphics:
  Device-1: NVIDIA GP107M [GeForce GTX 1050 Mobile] driver: nvidia 
  v: 390.116 bus ID: 01:00.0 chip ID: 10de:1c8d 
  Device-2: AMD Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] 
  driver: amdgpu v: kernel bus ID: 04:00.0 chip ID: 1002:15dd 
  Display: x11 server: X.Org 1.20.1 driver: amdgpu,ati,modesetting,nouveau 
  FAILED: nvidia unloaded: fbdev,vesa compositor: gnome-shell 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: N/A v: N/A direct render: N/A 
Audio:
  Device-1: AMD driver: snd_hda_intel v: kernel bus ID: 04:00.1 
  chip ID: 1002:15de 
  Device-2: AMD driver: snd_hda_intel v: kernel bus ID: 04:00.6 
  chip ID: 1022:15e3 
  Sound Server: ALSA v: k4.18.0-16-generic 
Network:
  Device-1: Realtek RTL8822BE 802.11a/b/g/n/ac WiFi adapter driver: r8822be 
  v: kernel port: e000 bus ID: 02:00.0 chip ID: 10ec:b822 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: 2.3LK-NAPI port: d000 bus ID: 03:00.0 chip ID: 10ec:8168 
  IF: enp3s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 238.47 GiB used: 6.08 GiB (2.6%) 
  ID-1: /dev/sda vendor: SanDisk model: SD9SN8W256G1002 size: 238.47 GiB 
  speed: 6.0 Gb/s serial: <filter> temp: 41 C 
Partition:
  ID-1: / size: 231.54 GiB used: 5.92 GiB (2.6%) fs: ext4 dev: /dev/dm-1 
  ID-2: /boot size: 704.5 MiB used: 161.5 MiB (22.9%) fs: ext4 
  dev: /dev/sda2 
  ID-3: swap-1 size: 976.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-2 
Sensors:
  System Temperatures: cpu: 49.1 C mobo: N/A gpu: amdgpu temp: 49 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 290 Uptime: 41m Memory: 6.81 GiB used: 2.11 GiB (30.9%) 
  Init: systemd v: 239 runlevel: 5 Compilers: gcc: 8.2.0 alt: 8 Shell: bash 
  v: 4.4.19 running in: gnome-terminal inxi: 3.0.24 
```

Is this laptop just not going to work with the Nvidia graphics card? Is an amd apu not compatible with nvidia prime? I notice "prime-select query" only  shows intel and nvidia as options.

---

### Post by disedorgue on 2019-03-13
Hi,
work for me with nvidia-390 and many actions:
-install package: xserver-xorg-input-kbd and xserver-xorg-input-libinput
-create /etc/X11/xorg.conf with:
```


Section [COLOR=#FF0000]"Module"[/COLOR]
    Load [COLOR=#FF0000]"modesetting"[/COLOR]
EndSection
 
Section [COLOR=#FF0000]"Device"[/COLOR]
    Identifier [COLOR=#FF0000]"nvidia"[/COLOR]
    Driver [COLOR=#FF0000]"nvidia"[/COLOR]
    BusID [COLOR=#FF0000]"1:0:0"[/COLOR]
    Option [COLOR=#FF0000]"AllowEmptyInitialConfiguration"[/COLOR]
    Option [COLOR=#FF0000]"ModeValidation"[/COLOR] [COLOR=#FF0000]"NoDFPNativeResolutionCheck"[/COLOR]
    Option [COLOR=#FF0000]"ConnectedMonitor"[/COLOR] [COLOR=#FF0000]"DFP-0"[/COLOR]
EndSection

```
Regards.

---

### Post by buffalobuffalobuffalo on 2019-03-13
Thank you so much disedorgue, that seemed to do the trick. I was lost in my despair but you have saved me from this crucible.

---

### Post by NestorAcevedo on 2019-08-27
I'm surprised that you can use them. I have a similar laptop, although I'm an openSUSE user but I'm unable to use the Nvidia discrete card.

---

