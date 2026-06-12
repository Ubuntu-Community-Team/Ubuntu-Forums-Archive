---
title: "[Ubuntu] 20.04LTS on Ryzen 4800H Laptop (Asuse TUF A15), what works and what does not"
date: 2020-04-24
forum: Hardware
---

### Post by egandt on 2020-04-24
[Ubuntu] 20.04LTS on Ryzen 4800H Laptop (Asuse TUF A15), issues
Figured I'd create a thread of issues with this laptop and Ubuntu 20.04LTS.

**Issues:**
Screen: unable to adjust brightness, fixes for Ubuntu 18.04 and 19.10 result in no Wifi, so screen brightness is stuck at about 70% [https://wiki.ubuntu.com/Kernel/Debugging/Backlight]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight")  I tried all kernel options here, the keys are working, they just can not adjust the screen brightness.  Note: "amdgpu.exp_hw_support=1" is required to use the Renoir AMDGPU Driver, which does not help with brightness or getting the Nvidia driver used, but is a start.  FIXED see post on using kernel 5.6

Video: Consistent pop-ups asking to adjust monitor display (in fact just clicking on "Monitor and Brightness" results in the switch dialog appears as does letting it simply sit for 5 minutes. FIXED see post on using kernel 5.6

Video: No way to switch between Nvidia and Ryzen, I'm having trouble even figuring out what it is actually using as the drivers are Nvidia, but the Nvidia control panel is empty as if they are not being used.  Note: Nouveau is blacklisted.  Update with the above kernel parmeter it is using the AMDGPU Driver, without it I'm unsure what it was falling back to using.  Nvidia is not loading for Video.

Video: Switching between Ryzen and Nvidia, right as of now I see this as a pipe dream, since this is often a problem, never got it working on my previous laptop either.

Mouse: Logitech MX Master will not sync via bluetooth, works fine with Solaar and the Dongle, however. [https://ubuntuforums.org/showthread.php?t=2441469&p=13949616#post13949616]("https://ubuntuforums.org/showthread.php?t=2441469&p=13949616#post13949616")

Network: using NetManager unable to get DNs order to work on boot: [https://ubuntuforums.org/showthread.php?t=2441429]("https://ubuntuforums.org/showthread.php?t=2441429")

Sleep: System sleeps, but resume simply starts from scratch, however I've not spent any time looking into it.  Fixed: works with Kernel 5.6


**So What works: **
Everything except for switching between AMD and Nvidia GPU, but I think that is expected.


So is Ubuntu 20.04LTS usable on this laptop, yes, is it a clean experience, no would I want to use it as a daily driver, sure, it is completely usabel on Kernel 5.6 and not really usable on 5.4, see post further down on how to switch to 5.6 with proper firmware.

ERIC

---

### Post by CelticWarrior on 2020-04-24
Have you disabled Secure Boot? The issue with Nvidia X Server Settings suggests the Nvidia drivers aren't loaded.

---

### Post by egandt on 2020-04-24
> **CelticWarrior said:**
> Have you disabled Secure Boot? The issue with Nvidia X Server Settings suggests the Nvidia drivers aren't loaded.

Yes secure boot is off, I agree it appears as if Nvidia is not loaded, but monitoring Xorg's log it seems Nvidia is running, but so very hard to say for sure which driver is really being used, so I'm not sure.  I even see mention of nouveau, Radeon and vesa being unloaded, none of which makes sense.

```

root@tufa15:/etc#  nvidia-smi
Fri Apr 24 20:13:28 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.64       Driver Version: 440.64       CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 166...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   44C    P0     9W /  N/A |      0MiB /  5944MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```

So it would appear it is not, no clue what is then being used, so I tried running "nvidia-xconfig" however that only broke X, which was not a surprise had it happen many times, but really starting to hate this laptop and Ubuntu on it.

I also tried adding "amdgpu.exp_hw_support=1" which is required pre 5.5 (so 5.4) for Renoir support, however it did not make any difference, to brightness, but I'm now using the AMDGPU driver at least.

ERIC

---

### Post by CelticWarrior on 2020-04-24
What does it show in Additional Drivers?

---

### Post by egandt on 2020-04-25
Additional drivers shows Nvidia only, and the drivers are working as in CUDA is operational, but it is not attached to the Laptop display, so I assume it is unable to switch, between the Renoir GPU and Nvidia GPU.  Searching around, this seems likely as this appears to be a common issue, which I can live with for now, the screen brightness, is more pressing.

---

### Post by egandt on 2020-04-30
So I was able to finally fix the Monitor brightness by switching to the 5.6 kernel, simply put it does not work with 5.4.  Also fixes asking to switch monitor setup and sleep, so many of the issues I found.

Basically I did this:
```

sudo su -
apt-get install linux-image-5.6.0-1007-oem linux-headers-5.6.0-1007-oem linux-modules-nvidia-440-5.6.0-1007-oem
mkdir 1
cd 1
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware/amdgpu/
cp * /lib/firmware/amdgpu/
update-grub2
reboot

```

---

### Post by yoggibear6 on 2020-11-20
Not sure if this helps anyone, but I had some trouble finding a fix to the same problem when I encountered it so I'm leaving my solution here in case someone finds it useful. 

I encountered the same problem with screen brightness (though trackpad works fine for me), and resolved it by upgrading the kernel to 5.9.8 and using brightness-controller to adjust the screen brightness rather than the built in slider. Steps taken were:

1) Download mainline and upgrade kernel to 5.9.8 instead of the 5.4.0 default ([https://github.com/bkw777/mainline](https://github.com/bkw777/mainline)) 
2) Reboot the laptop and use the updated kernel. For a step by step guide, this comment by karel should be helpful ([https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version/1161432#1161432](https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version/1161432#1161432)) 
3) Install brightness controller ([http://ubuntuhandbook.org/index.php/2017/05/install-brightness-controller-utility-in-ubuntu-16-04-higher/#:~:text=Brightness%20Controller%20is%20a%20simple,from%201%25%20to%20100%25!&text=It%20supports%20an%20arbitrary%20number%20of%20displays](http://ubuntuhandbook.org/index.php/2017/05/install-brightness-controller-utility-in-ubuntu-16-04-higher/#:~:text=Brightness%20Controller%20is%20a%20simple,from%201%25%20to%20100%25!&text=It%20supports%20an%20arbitrary%20number%20of%20displays)!)

---

