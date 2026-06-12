---
title: "Drivers do not work for NVIDIA Titan Black on 14.04"
date: 2014-07-16
forum: Hardware
---

### Post by mrvlad on 2014-07-16
Hello,

My computer with Ubuntu 14.04 x64 has a GeForce Titan Black graphics card (there is no integrated graphics module). I have encountered several problems with making this GPU work properly on Ubuntu and I would like to kindly ask you for help.

First of all, after a fresh installation (+upgrades) **Ubuntu won't enter the console mode** (i.e. blank black screen after pressing CTRL+ALT+F{1-6}).

The** GPU is not detected** in the "Additional drivers" tab of Software & Updates utility -  "No additional drivers available".

I tried out several very similar instructions (like f.eg. [this one]("http://ubuntuhandbook.org/index.php/2014/04/install-nvidia-driver-331-67-ubuntu1404/")) that advise the following:
1. purge nvidia, install nvidia-331-updates-dev, reboot
2. go to "Additional drivers" tab and select recommended open source driver (**my list of drivers is still empty** **at this point, but at least now i can enter the console mode; maximum available resolution is still way too low**)
3. download x64 driver 331.67 (that is supposed to support Titan Black), go to console mode, stop lightdm, apply privileges to the driver, install it
4. reboot after the installation
** But this does not work.** Upon rebooting I see a screen with a blinking cursor in the upper left corner. After a while the screen goes completely black for a few seconds, then returns to the state with the blinking cursor. This process repeats forever. The system is not responsive, I can only do a hard reset and uninstall the 331.67 driver in recovery mode. 

I also tried to 
- install the latest NVIDIA driver 340.24 instead of 331.67
- force resolution to be monitor's native 1920x1080 (in /etc/X11/xorg.conf)
- blacklist nouveau
same result.

Ubuntu seems to see the PCI
```
wtf@themysterygarden:~$ lspci -v
(...)
02:00.0 VGA compatible controller: NVIDIA Corporation GK110B [GeForce GTX Titan Black] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device 3641
    Flags: fast devsel, IRQ 32
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at fb000000 [disabled] [size=512K]
    Capabilities: <access denied>
(...)

```

System Settings -> Details shows:
```
Graphics VESA: GK110B Board - 20830031
```
After installing nvidia-331-updates-dev:
```
Graphics GeForce GTX TITAN Black/PCIe/SSE2
``` 
but still the maximum resolution is 1360x768 (the monitor's native resolution is 1920x1080).

I greatly appreciate your help with this.

---

