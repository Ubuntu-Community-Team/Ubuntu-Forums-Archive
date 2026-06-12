---
title: "NVIDIA 630m and Intel HD 4000 how to install ?"
date: 2013-03-05
forum: Hardware
---

### Post by cubocik on 2013-03-05
Good afternoon I'm trying to install the graphic card but without success , when I install the installer show that I already have the the newest driver but when I check in sysinfo I only have this NVIDIA corporation... the NVIDIA card have cuda how I can use the gpu of that graphic card ? how can I install the Intel 4000hd graphic card ? Im using ubuntu 13.04 64bit

---

### Post by oldfred on 2013-03-05
I do not know Optimus, but some posts with info.

 Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
[http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889](http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

   nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

---

### Post by cubocik on 2013-03-05
Ty for the answer I run this command and this was showed
cubocik@machine:~$ lspci -nnk | grep -iA3 vga 
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device [1558:2706]
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0de3] (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device [1558:2706]
    Kernel modules: nouveau, nvidiafb
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]


that means that I have the two graphic cards correctly installed right ?

---

### Post by cubocik on 2013-03-05
How can I switch ? how can I use that system ? I'm really nww about this

---

### Post by oldfred on 2013-03-05
You need to read up on bumblebee, I do not have that so do not know details.  
Links in my previous posts explain it and show how to install it.

---

### Post by cubocik on 2013-03-05
How can I switch ? how can I use that system ? I'm really new about this ..

I already installed bumblebee... and when I do for example optirun firefox it opened up firefox ..

Now when I do nvidia-settings on terminal it show a GUI with You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by cubocik on 2013-03-05
cubocik@machine:~/oclHashcat-plus-0.12$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(R) Sandybridge/Ivybridge Graphics Controller Hardware Version 0.0
memory: 65472kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 0395
eisa: LGD0395
serial: 00000000
manufacture: 0 2012
input: analog signal.
screensize: 34 19
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1366x768@59
monitorid: LG Display
monitorid: LP156WH4-TLP


I only have xorg.conf.failsafe and xorg.conf.nvidia-xconfig-original .

xorg.conf.failsafe
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


and xorg.conf.nvidia-xconfig-original is a empty file


I dont have a xorg.conf file in /etc/X11/

---

### Post by oldfred on 2013-03-05
If you installed per the instructions:

[https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting)

---

