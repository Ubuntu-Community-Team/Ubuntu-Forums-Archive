---
title: "NVidia backlight control (Again)"
date: 2021-10-31
forum: Hardware
---

### Post by titaniumjones on 2021-10-31
[B][Ubuntu 20.4]
[/B]Hi, 
I've been using Ubuntu for about a year now and have just bought a new laptop.
I installed Ubuntu once again along side Windoze 11 on separate partitions.


Like previously, the combination of i7 and NVidia GPU results in no backlight control.


Confident I could fix the problem like previously I went about searching the web for a solution. Unfortunatily, this time I have been unable to come up with a working solution for this laptop. So I'm reaching out for help.


Configuration:
Dell Alienware X17
Intel i7
NVidia RTX3070
32Gb ram


Things I have tried:


1. Adding  acpi_backlight=vendor to the grub command line. Changed it to 'video' and also 'legacy'


2. Adding
    nvidia
    nvidia-drm
    nvidia-modeset
to /etc/initramfs-tools


3. Added
Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
To /usr/share/X11/xorg.conf.d/10-nvidia.conf


4. The output from 
xrandr | grep " connected" | cut -f1 -d " "
results in
XWAYLAND0
The output of
xrandr --output XWAYLAND0 --brightness 0.7
results in no change


5. The contents of  
/sys/class/backlight
intel_backlight
although I have seen other entries in here.


Any help would be greatfully recieved.

---

### Post by titaniumjones on 2021-10-31
Driver:
NVIDIA driver metapackage from nvidia-driver-470

---

### Post by titaniumjones on 2021-12-26
I have now fixed this problem. 
I tried various versions of Linux and eventually settled on LinuxMint as it offered the highest compatibility with the hardware. However, out of the box it also suffered with the lack of backlight adjustment.
My solution is documented [here]("https://forums.linuxmint.com/viewtopic.php?f=59&t=364016&p=2113188#p2113188").

---

