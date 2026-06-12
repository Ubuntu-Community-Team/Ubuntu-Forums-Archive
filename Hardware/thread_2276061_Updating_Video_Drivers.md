---
title: "Updating Video Drivers"
date: 2015-04-30
forum: Hardware
---

### Post by KaraKuro on 2015-04-30
Hi there. New to Ubuntu. Well, new INSTALLATION of Ubuntu. Not very savy. Wanted to make sure my drivers were 100% up to date. Really REALLY bad at this.

I used the command ```
lspci | grep VGA
``` to discern that I am using ```
Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
```

Now, how do I make sure my drivers are up to date?

So far, I've been using the tutorial at [http://www.cgl.ucsf.edu/chimera/graphics/updatelinux.html](http://www.cgl.ucsf.edu/chimera/graphics/updatelinux.html) to get this far. Any help is appreciated!

---

### Post by TheFu on 2015-04-30
Linux isn't Windows.

The driver you want is the driver that is automatically installed and automatically updated.  In Linux, the goal is NOT to download any drivers "special" unless absolutely necessary. We want to use the trusted, working, drivers from the package manger - unless there is a really, really, really good reason not to.

This is really important if your Linux-fu is weak.

The main reason I run Linux systems is to avoid all the download-this, download-that stuff required by other OSes.  Let the package manager do its job - UNLESS you have a specific need or bug in the default drivers.

---

### Post by KaraKuro on 2015-04-30
> **TheFu said:**
> Linux isn't Windows.

The driver you want is the driver that is automatically installed and automatically updated.  In Linux, the goal is NOT to download any drivers "special" unless absolutely necessary. We want to use the trusted, working, drivers from the package manger - unless there is a really, really, really good reason not to.

This is really important if your Linux-fu is weak.

The main reason I run Linux systems is to avoid all the download-this, download-that stuff required by other OSes.  Let the package manager do its job - UNLESS you have a specific need or bug in the default drivers.

Well actually, I've tried switching before. Now, I'm planning to install Windows alongside Ubuntu, but since I don't play certain games (League of Legends among them) very often anymore I've decided to try and make the games I **want** to play (Don't Starve Together, for instance) work on Linux.

Also, I'm installing Steam. I just want to make sure everything works the way it's intended to.

Thanks for your reply!

Edit: See, this is the reason I asked.

```
Running Steam on ubuntu 15.04 64-bitSTEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

```

---

### Post by Yellow Pasque on 2015-04-30
I think Steam uses 32-bit libs, which takes a little work on a 64-bit system.
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libc6:i386
```

You may also need this hack: [http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005)

---

### Post by KaraKuro on 2015-04-30
haven't tried the link yet, but I'm going to post my output for trying to install the 32bit libs.
```

kara@karapc:~$ sudo apt-get install libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libc6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6:i386 is already the newest version.
libc6:i386 set to manually installed.
libgl1-mesa-dri:i386 is already the newest version.
libgl1-mesa-dri:i386 set to manually installed.
libgl1-mesa-glx:i386 is already the newest version.
libgl1-mesa-glx:i386 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

```

---

### Post by Yellow Pasque on 2015-05-01
Are you using open-source radeon driver or proprietary fglrx/Catalyst driver? If not sure, use:
```
lspci -k
```

---

### Post by KaraKuro on 2015-05-01
Output of lspci -k
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
    Subsystem: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Kernel driver in use: pcieport
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
    Kernel driver in use: pcieport
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
    Subsystem: Biostar Microtech Int'l Corp Device 3700
    Kernel driver in use: ahci
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Biostar Microtech Int'l Corp Device 3700
    Kernel driver in use: ohci-pci
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
    Subsystem: Biostar Microtech Int'l Corp Device 3700
    Kernel driver in use: ohci-pci
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Biostar Microtech Int'l Corp Device 3700
    Kernel driver in use: ehci-pci
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Biostar Microtech Int'l Corp Device 3700
    Kernel driver in use: ohci-pci
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
    Subsystem: Biostar Microtech Int'l Corp Device 3700
    Kernel driver in use: ohci-pci
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Kernel driver in use: ehci-pci
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
    Subsystem: Biostar Microtech Int'l Corp Device 3700
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
    Subsystem: Biostar Microtech Int'l Corp Device 3700
    Kernel driver in use: pata_atiixp
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
    Subsystem: Biostar Microtech Int'l Corp Device 821e
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
    Subsystem: Biostar Microtech Int'l Corp Device 3700
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 4396
    Kernel driver in use: ohci-pci
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
    Kernel driver in use: k10temp
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
    Kernel driver in use: fam15h_power
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
    Subsystem: ASUSTeK Computer Inc. Device 300b
    Kernel driver in use: radeon
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
    Subsystem: ASUSTeK Computer Inc. Device aab0
    Kernel driver in use: snd_hda_intel
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
    Subsystem: Biostar Microtech Int'l Corp Device 230e
    Kernel driver in use: r8169

```

I feel I should also mention I'm using Gnome3 (I know, shame on me :c but i like it, especially more than Unity.)

---

