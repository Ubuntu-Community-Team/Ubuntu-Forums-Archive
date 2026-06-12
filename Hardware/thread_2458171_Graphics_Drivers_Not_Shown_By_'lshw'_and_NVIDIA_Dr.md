---
title: "Graphics Drivers Not Shown By 'lshw' and NVIDIA Driver Freezes Screen At Boot"
date: 2021-02-18
forum: Hardware
---

### Post by dckl on 2021-02-18
Hi, nice people of Linux Forums!

I want to use my laptop's GPU to perform Machine Learning on Linux, so I installed Ubuntu 20.04.2 LTS. 

First, I tried checking the available graphics drivers by running "sudo lshw -c video' in terminal. I got the below results: 

```

sudo lshw -c video

 [sudo] password for <MyUsername>:  

   *-display UNCLAIMED        

        description: VGA compatible controller

        product: NVIDIA Corporation

        vendor: NVIDIA Corporation

        physical id: 0

        bus info: pci@0000:01:00.0

        version: a1

        width: 64 bits

        clock: 33MHz

        capabilities: pm msi pciexpress vga_controller cap_list

        **configuration: latency=0**

        resources: iomemory:fc0-fbf iomemory:fe0-fdf memory:fb000000-fbffffff memory:fc00000000-fdffffffff memory:fe00000000-fe01ffffff ioport:f000(size=128) memory:fc000000-fc07ffff

   *-display UNCLAIMED

        description: VGA compatible controller

        product: Advanced Micro Devices, Inc. [AMD/ATI]

        vendor: Advanced Micro Devices, Inc. [AMD/ATI]

        physical id: 0

        bus info: pci@0000:06:00.0

        version: c5

        width: 64 bits

        clock: 33MHz

        capabilities: pm pciexpress msi msix vga_controller bus_master cap_list

        **configuration: latency=0**

        resources: iomemory:fe0-fdf iomemory:fe0-fdf memory:fe10000000-fe1fffffff memory:fe20000000-fe201fffff ioport:d000(size=256) memory:fc500000-fc57ffff


```  

Notice that the 'driver' field doesn't even appear, so no graphics driver is specified for both my GPU and on-board CPU graphics, and 'configuration' only says 'latency=0'.

After that, I  tried downloading and installing the latest official NVIDIA driver from this link: 
[https://www.nvidia.com/Download/driverResults.aspx/170134/en-us](https://www.nvidia.com/Download/driverResults.aspx/170134/en-us)
This was done based on nvidia.com's official form for selecting GPU downloads.

However, after installing it, my screen would get stuck at the laptop's boot logo without displaying 'Ubuntu' at all. After many attempts to work around the issue, I ended up having to perform a fresh install of Ubuntu so I could try again.

Further background which might be relevant to resolving my issue: 

1. My laptop is an Asus ROG Strix G513Q-RHF104T running a Ryzen 7 5800H CPU and a 115-W RTX3070 GPU.

2. Ubuntu has an entire SSD dedicated to it. I have an installation of Windows, but it is running on a separate SSD.

3.  No additional drivers are displayed in the 'Additional Drivers' tool.  All that is displayed is 'No additional drivers available.'

4. My  Ubuntu installation is running in secure boot (I was told by the  installation prompt that this was necessary to install third-party  drivers and software).


Thanks in advance for helping me out with this issue. :)

---

### Post by CelticWarrior on 2021-02-18
Welcome.

> [COLOR=#000000]4. My Ubuntu installation is running in secure boot (I was told by the installation prompt that this was necessary to install third-party drivers and software).[/COLOR]

Actually it's the other way around. With Secure Boot you have to manually sign the drivers using a tool. Not hard but not easy either. Knowing tha Secure Boot don't confer any real benefit the usual suggestion is to ALWAYS disable it when hardware like Nvidia Graphics are in the equation. If you selected the option to install third-party drivers, codecs, etc. just disabling Secure Boot will make everything work as it should. NEVER use the binaries downloaded from Nvidia. The same Nvidia drivers are already in the Ubuntu repositories, properly packaged and tested and they'll compile and update whenever needed even after a kernel update; using the Nvidia binaries you'll have to reinstall the drivers after each kernel update so, just don't.

---

### Post by dckl on 2021-02-18
Hey, thanks so much for replying to me so quickly!

I've tried what you suggested (disabling secure boot on BIOS and shim-signed ([https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS))). That still didn't work, as I couldn't see the driver in 'Additional Drivers'. Then, I restarted my computer, and tried installing nvidia 460 via sudo apt-get. 

After that, the screen froze, so I did a fresh install again, this time with the secure boot option still set to off in bios, and I chose NOT to do secure boot when reinstalling Linux. The same issues persisted, and I was unable to see any NVIDIA drivers in 'Additional Drivers'.

Does anyone have any suggestion to make about this? :) Again, I wish to thank anyone who contributes in advance.

---

### Post by CelticWarrior on 2021-02-18
Try with Ubuntu 20.10. Your hardware is too new. It's possible you'll need an even newer kernel than the one shipped with 20.10 (that actually should be the sameas in an updated 20.04).

Also very likely you din't disable Secure Boot. > [COLOR=#000000]this time with the secure boot option still set to off in bios, and I chose NOT to do secure boot when reinstalling Linux[/COLOR]
With Secure Boot off there's nothing to choose during the installation related to Secure Boot itself. This sounds nonsensical.
OTOH, what should be chosen during the Ubuntu installation is the option to install 3rd party drivers, codecs, firmware... That should install Nvidia drivers automatically. Of course, an internet connection is required. And with an internet connection during the installation also select the option to download and install updates as this brings the latest kernel for the release.

Last but not the list, update UEFI and SSD's firmware before reinstalling. Even brand new computers often need it nowadays.

---

### Post by slickymaster on 2021-02-18
Thread moved to **Hardware** for a better fit

---

