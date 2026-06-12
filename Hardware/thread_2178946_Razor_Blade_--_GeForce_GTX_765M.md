---
title: "Razor Blade -- GeForce GTX 765M"
date: 2013-10-05
forum: Hardware
---

### Post by dillongilmore on 2013-10-05
Hello, I have the latest Ubuntu installed and I am trying to get my discrete graphics card to work. Ideally I would like to be able to switch between my intel graphics and my discrete graphics, but if thats too hard or not possible I would just like to use the discrete graphics. I will post any information you need me to post in order to help debug this situation. I am pretty new when it comes to dealing with drivers and hardware in general. I am very familiar with the command line though.

```

 $ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)

```

```

 $ dpkg -l | grep nvidia
ii  bumblebee-nvidia                                3.2.1-3                                          amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  nvidia-304                                      304.108-0ubuntu1~xedgers~saucy1                  amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                                   1:0.2.83                                         amd64        transitional package for ubuntu-drivers-common
ii  nvidia-current                                  304.108-0ubuntu1~xedgers~saucy1                  amd64        Transitional package for nvidia-current
ii  nvidia-settings-304                             304.88-0ubuntu2                                  amd64        Tool for configuring the NVIDIA graphics driver

```

```

 $ dpkg -l | grep nouveau
ii  libdrm-nouveau2:amd64                           2.4.46+git20130910.58d00888-0ubuntu0sarvatt      amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:i386                            2.4.46+git20130910.58d00888-0ubuntu0sarvatt      i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2-dbg:amd64                       2.4.46+git20130910.58d00888-0ubuntu0sarvatt      amd64        Userspace interface to nouveau-specific kernel DRM -- debugging symbols
ii  xserver-xorg-video-nouveau                      1:1.0.9+git20130730.300c5a32-0ubuntu0sarvatt     amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-nouveau-dbg                  1:1.0.9+git20130730.300c5a32-0ubuntu0sarvatt     amd64        X.Org X server -- Nouveau display driver (debug symbols)

```

Any help would be awesome, I will also post the steps I took to get to a solution.

Thanks in advance.

---

### Post by dillongilmore on 2013-10-09
bump

---

### Post by Yellow Pasque on 2013-10-09
You're using nvidia 304 series driver and a 765M needs 325.xx or later...

---

### Post by dillongilmore on 2013-10-10
Okay I uninstalled the driver I had and installed version 331. My system though is still not using the discrete graphics though. The two indications of this I found through Steam as well as trying to run applications with optirun.

[IMG]http://dl.dropbox.com/u/12963184/Selection_012.png[/IMG]

```

dillon@blade ~ $ optirun steam
zsh: correct 'steam' to '.steam' [nyae]? n
[  538.156639] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please


[  538.156670] [ERROR]Aborting because fallback start is disabled.

```

---

### Post by Yellow Pasque on 2013-10-10
According to ( [https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting) ), when this happens, you should look at the end of /var/log/kern.log for clues (Note: you need sudo/root permissions to read that file).

---

### Post by dillongilmore on 2013-10-11
```

Oct 11 16:52:29 blade kernel: [19551.228678] nvidia: module license 'NVIDIA' taints kernel.
Oct 11 16:52:29 blade kernel: [19551.228682] Disabling lock debugging due to kernel taint
Oct 11 16:52:29 blade kernel: [19551.237853] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
Oct 11 16:52:29 blade kernel: [19551.238060] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
Oct 11 16:52:29 blade kernel: [19551.238065] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.13  Sun Sep 29 22:56:10 PDT 2013
Oct 11 16:52:30 blade kernel: [19551.345118] vgaarb: this pci device is not a vga device
Oct 11 16:52:30 blade kernel: [19551.347278] nvidia 0000:01:00.0: irq 49 for MSI/MSI-X
Oct 11 16:52:30 blade kernel: [19551.353166] NVRM: failed to copy vbios to system memory.
Oct 11 16:52:30 blade kernel: [19551.355710] NVRM: RmInitAdapter failed! (0x30:0xffffffff:720)
Oct 11 16:52:30 blade kernel: [19551.355717] NVRM: rm_init_adapter failed for device bearing minor number 0
Oct 11 16:52:30 blade kernel: [19551.355733] NVRM: nvidia_frontend_open: minor 0, module->open() failed, error -5

```

```

 $ lspci -vnn | grep '\''[030[02]\]'
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
01:00.0 3D controller [0302]: NVIDIA Corporation GK106M [GeForce GTX 765M] [10de:11e2] (rev a1)

```

I'm not sure what to think of those errors. 'kernel tain', is there something wrong with my installation, I've gone through an Ubuntu, Ubuntu Gnome, and Fedora and have gotten the same errors, so is there a generic kernel bug? As for the non vga device, I am not experienced enough to know what that means.

---

### Post by Yellow Pasque on 2013-10-11
> Why does the VBIOS fail to load on my Optimus system?
On some notebooks with Optimus graphics, the NVIDIA driver may not be able to retrieve the Video BIOS due to interactions between the System BIOS and the Linux kernel's ACPI subsystem. On affected notebooks, applications that require the GPU will fail, and messages like the following may appear in the system log:
NVRM: failed to copy vbios to system memory.
NVRM: RmInitAdapter failed! (0x30:0xffffffff:858)
NVRM: rm_init_adapter(0) failed
Such problems are typically beyond the control of the NVIDIA driver, which relies on proper cooperation of ACPI and the System BIOS to retrieve important information about the GPU, including the Video BIOS.

So, make sure your BIOS is up to date, and if you've still got issues, see: [https://github.com/Bumblebee-Project/Bumblebee/wiki/Reporting-Issues](https://github.com/Bumblebee-Project/Bumblebee/wiki/Reporting-Issues)

> 'kernel taint'
Don't worry about it. It means you're using a binary driver (nvidia) and the Linux kernel devs don't want bug reports from you...

---

### Post by dillongilmore on 2013-10-11
Ha, well I'll admin the Linux devs can have a sense of humor.

When I had Windows on this computer my discrete graphics was working just fine. This laptop is pretty darn new I would be very surprised if the BIOS was outdated. The maker doesn't have any updates that I can find.

```

$ for keyword in baseboard-manufacturer baseboard-product-name baseboard-version system-manufacturer system-product-name system-version bios-vendor bios-version bios-release-date; do
for>     printf "%-22s: " "$keyword";
for>     sudo dmidecode -s "$keyword";
for> done
baseboard-manufacturer: [sudo] password for dillon: 
RAZER
baseboard-product-name: RAZER            
baseboard-version     : 1.00
system-manufacturer   : Razer
system-product-name   : Razer Blade
system-version        : XPT551T6EBFB
bios-vendor           : RAZER
bios-version          : 1.01
bios-release-date     : 05/20/2013

```

---

