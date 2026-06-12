---
title: "Can't set Nvidia as default GPU, Ubuntu freeze on boot after installing Nvidia driver"
date: 2022-05-16
forum: Hardware
---

### Post by taiwbi on 2022-05-16
I am using Ubuntu 22.04 LTS, everything was fine until I decided to change my NVIDIA driver, I changed it to nvidia-driver-510, I do not remember which one I was using but I think it was 470.
Then I restarted my laptop and everything was almost ok. I opened the NVIDIA X Server settings and set the PRIME profile to NVIDIA (performance mode). Then I restarted my laptop again. It freezes on startup, on the ASUS - Ubuntu screen, I use ctrl + alt + f3 (that didn't work and I had to choose recovery mode in grub menu and then select resume normal boot so I can open terminal with ctrl + alt + f2) keys and open the terminal, remove the NVIDIA drivers and restart. Now it works with Intel GPU, I installed nvidia-driver-510 and tried again to set my NVIDIA as default GPU, but the problem is still there. I cannot set my NVIDIA as the default GPU.

My GPU is: nVidia GP108M [GeForce MX250]
And My CPU is: [HTML]Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz

This is ```
lspci -k | grep -EA3 'VGA|3D|Display'
``` command output:

```
&#9472;$ lspci -k | grep -EA3 'VGA|3D|Display'
00:02.0 VGA compatible controller: Intel Corporation CometLake-U GT2 [UHD Graphics] (rev 02)
    DeviceName: VGA
    Subsystem: ASUSTeK Computer Inc. CometLake-U GT2 [UHD Graphics]
    Kernel driver in use: i915
    Kernel modules: i915
--
02:00.0 3D controller: NVIDIA Corporation GP108M [GeForce MX250] (rev a1)
    DeviceName: Second VGA
    Subsystem: ASUSTeK Computer Inc. GP108M [GeForce MX250]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
03:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)

```
Now, after two days of trying to get it to work, I can not even set the Prime profile to On-Demand mode! At first when it was in on-demand mode it worked fine (it detected the graphics card and showed 3 processes with the nvidia-smi command, but it did not use nvidia gpu even if the graphics process was too high), but now it just freezes on boot screen. If I select kernel version 5.15.0-27 in the grub menu. It handles the error and the Intel graphics is used, so the nvidia-smi output is:
```
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

```

I tried```
 sudo apt remove --purge *nvidia*
``` and reinstall everything like thousand times. I tried ```
locate nvidia
``` and remove all nvidia config files after removing driver then reinstall it, I tried reinstall linux headers but nothing worked so far.

---

### Post by taiwbi on 2022-05-17
I finally solved my problem and I want to share it here so that it is a solution for those who face this problem in the future. First, you should remove all NVIDIA drivers and modules from your system.
```

sudo apt remove --purge *nvidia*

```
This command will remove all NVIDIA drivers and modules, as well as their configuration files.
Then, make sure you do not have any active repository other than the official Ubuntu repositories.
Download the official NVIDIA driver for Linux from the NVIDIA website. Reboot your system and your system will use the Nouveau driver for rendering. Go to Additional Drivers and select the latest NVIDIA driver to install on your system. After installation, restart your system.
If you are not able to access the Gnome login screen, press ctrl + alt + f2, f3, f4, ... keys simultaneously to access the terminal. If that did not work, you should boot your system with nomodeset and then do the same. Enter your username and password and log in.
Your default Prime profile should be on-demand mode. You can view your Prime profile using the command below:
```

sudo prime-select query

```
Set your prime profile to nvidia
```

sudo prime-select nvidia

```
Then go to the path where the NVIDIA driver you downloaded from the NVIDIA website is located and install it using the command below:
```

sudo bash NVIDIA-Linux-x86_64-***.run

```
Replace NVIDIA-Linux-x86_64-***.run with the name of the file. Continue the installation process, and when asked if you want to install kernel modules, ... say yes. You will also be warned that your target Linux system has a custom driver installation that you can use instead of the official NVIDIA driver; ignore this message and install the driver.
After installation, reboot your system. Press Ctrl + Alt + F2 again to bring up the terminal and log in to your account. Go to the official NVIDIA driver file that you downloaded earlier. And uninstall it with this command:
```

sudo bash NVIDIA-Linux-x86_64-***.run --uninstall

```
After uninstalling the driver, reboot your system.

Everything should be fine. **DO NOT CHANGE THE PRIME PROFILE OR THE NVIDIA DRIVER VERSION OR EVERYTHING WILL GO WRONG AGAIN.**
As far as I know, the modules were somehow deleted in the kernel and when installing the driver from the official Ubuntu drivers, they are not installed. But the official NVIDIA driver we downloaded installs these modules and when we uninstall the official driver, these modules remain. Two drivers cannot be installed on the system at the same time, so we have to remove one.
If we remove the driver from Ubuntu drivers and keep the official NVIDIA driver, the problem will not be solved. I have tried it. Hope it helps someone.

---

