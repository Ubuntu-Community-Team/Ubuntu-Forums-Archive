---
title: "Backlight configuration help. Lenovo Ryzen amd GPU Ubuntu 18.04 (mint 19.2)"
date: 2019-08-05
forum: Hardware
---

### Post by arturomrivas on 2019-08-05
Hello,


I have a Lenovo 6-14ARR Ryzen 3 2200U I have all running except the backlight or functions keys.


I know that its depending of the video driver; so this is the amd/radeon driver that I have installed and working 


```
arturo@arturo-Lenovo-ideapad-FLEX-6-14ARR:~$ ls /sys/class/backlight/
amdgpu_bl0
```


I know I have to modify the grub and the xorg.conf file.


This is the GRUB that I have


```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```


I know that in this lines I have to put something like


```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=vendor"
```


But it has to be with the info of the driver or video card, is it not?
Now, I have several xorg.conf files this are the name of each file


```
arturo@arturo-Lenovo-ideapad-FLEX-6-14ARR:/usr/share/X11/xorg.conf.d$ ls
00-amdgpu.conf  10-quirks.conf  40-libinput.conf
10-amdgpu.conf  10-radeon.conf  70-wacom.conf
```


The 00-*amdgpu.conf has


```
Section "OutputClass"
    Identifier "AMDgpu"
    MatchDriver "amdgpu"
    Driver "amdgpu"
EndSection


Section "Files"
    ModulePath "/opt/amdgpu-pro/lib/xorg/modules"
    ModulePath "/opt/amdgpu/lib/xorg/modules"
    ModulePath "/usr/lib/xorg/modules"
EndSection
```


The 10-amdgpu.conf has


```
Section "OutputClass"
    Identifier "AMDgpu"
    MatchDriver "amdgpu"
    Driver "amdgpu"
EndSection
```


The 10-radeon.conf (that I dont think I am using that file) has


```
Section "OutputClass"
    Identifier "Radeon"
    MatchDriver "radeon"
    Driver "radeon"
EndSection
```


I know that in the xorg.conf file has to be an extra line, something like


```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "your video card"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```


Soooo can some help me figure it out the info I have to save on the files? I mean the grub and the xorg? Should I modified both amdgpu.conf files? Only one?


Thanks for any help

---

