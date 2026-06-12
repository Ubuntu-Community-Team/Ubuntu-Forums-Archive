---
title: "NVIDIA screen waves/flickers after logout, kdm restart or suspending"
date: 2009-11-25
forum: Hardware
---

### Post by thomi_ch on 2009-11-25
Hi all

Have a fresh installed kubuntu karmic koala 9.10 with the latest nvidia drivers ([https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)).
All works fine.. really.. but there is a problem, that needs to be fixed...

The problem:
The system/screen runs perfect on a boot and while working, without problems. Resolution 1600x900.
After logout from my session, the whole screen flickers.. it looks like waves, see attachment snapshot3.png ... The same happens, if i restart the X-Server from login screen with ALT+E or if i put my notebook into suspend mode and resume it.

I tried "sudo nvidia-xconfig" and i also tried that:
[http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html](http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html)
... both, no changes..

Thanks for your help..

My system:
ASUS Notebook
ASUS N71VN-TY047V

Intel Q9000, 4096MB, 1000GB, 17.3" GT WSXGA (1600x900), BluRay-ROM
NVIDIA GeForce GT240M 1024MB DDR3 RAM

uname -a
Linux poseidon 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 0a34 (rev a2)


sudo lspci -vvv
01:00.0 VGA compatible controller: nVidia Corporation Device 0a34 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 1ae2
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at ce000000 (64-bit, prefetchable) [size=32M]
        Region 5: I/O ports at cc00 [size=128]
        [virtual] Expansion ROM at fd000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [78] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 <64us
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
                        ClockPM+ Suprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [b4] Vendor Specific Information <?>
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb


/etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "extmod"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x900"
    EndSubSection
EndSection

---

### Post by cajual on 2009-12-21
I have the same issue!

---

### Post by Qaranthir on 2009-12-21
I have the same problem, but with a slightly different setup:
In my case:
Ubuntu 9.10 (not Kubuntu) with a Geforce GT230M
As far as I know, the GT230 and GT240 have the same chipset.
Instead of the nvidia-190-driver, I still use the nvidia-185-driver. Nevertheless, the description of the problem applies in exactly the same way with my system.

---

### Post by cajual on 2009-12-21
Why post in this old thread and not the new one I made that I have been pushing?

---

### Post by cajual on 2009-12-22
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456)

---

### Post by thomi_ch on 2010-02-10
Hi all

The problem can be solved with installing latest nvidia beta driver from: [ftp://download.nvidia.com/XFree86](ftp://download.nvidia.com/XFree86)

:popcorn:

I used thins one: [ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.03/](ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.03/)

First, remove all remaining nvidia-* packages from your system and then boot into command line mode... i have done that with editing /etc/init/kdm.conf an changed this:

start on (filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [016]

... to this

start on ([B]never
          and[/B] filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [016]


after installing the nvidia beta driver, changing this back and reboot.

so happy beta driving ;)

kind regards
thomi

---

