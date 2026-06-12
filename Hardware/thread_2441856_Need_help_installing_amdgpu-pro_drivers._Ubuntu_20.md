---
title: "Need help installing amdgpu-pro drivers. Ubuntu 20.04 LTS"
date: 2020-04-27
forum: Hardware
---

### Post by qui86 on 2020-04-27
Hello guys,

I need some help here, tried every trick there is that I have found on the net. With no success! :(

 I have tried to change the drivers for my ATI Mobility Radeon HD 5870 to use amdgpu-pro instead of the "Radeon" that comes with the kernel and mesa.

This is one of the guides I have followed, with no luck.
[https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation](https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation)

I have a clean install 20.04 LTS. All updated and upgraded. It was acouple of years since I ran linux, so you can treat me like a novice.


Specific help would be: To remove the already installed drivers, installing the latest amdgpu-pro drivers.

---

### Post by qui86 on 2020-04-27
Jumped on to the laptop, so I can post some printouts. 

This is the drivers I have tried to install: amdgpu-pro-18.40-697810-ubuntu-18.04.tar.xz

```

$ sudo lshw -C video
  *-display                 
       description: VGA compatible controller
       product: Broadway XT [Mobility Radeon HD 5870]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:d0000000-dfffffff memory:e0020000-e003ffff ioport:d000(size=256) memory:c0000-dffff

```

```

$ lsmod | grep radeon
radeon               1474560  14
ttm                   106496  1 radeon
drm_kms_helper        184320  1 radeon
i2c_algo_bit           16384  1 radeon
drm                   491520  9 drm_kms_helper,radeon,ttm

```

---

### Post by CelticWarrior on 2020-04-27
Welcome.

If your system is running with the "radeon" driver that is what you should keep. Your card is NOT supported by the proprietary "amdgpu-pro" driver.
Currently users do NOT need to install any driver for AMD Graphics.

---

### Post by qui86 on 2020-04-27
I have also tried to install the drivers from AMD.com

Used these pakages:
AMD Catalyst&#8482; 15.9 Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators
AMD Catalyst&#8482; 15.9 Proprietary Ubuntu 14.04 x86_64 Minimal Video Driver for Graphics Accelerators (Non-X Support)
AMD Catalyst&#8482; 15.9 Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators Devel Files (OGL, OCL)
AMD Catalyst&#8482; 15.9 Proprietary Ubuntu 14.04 x86_64 Catalyst Control Center

Using the installation manual: [https://drivers.amd.com/relnotes/amd-catalyst-graphics-driver-installer-notes-for-linux-operating-systems.pdf](https://drivers.amd.com/relnotes/amd-catalyst-graphics-driver-installer-notes-for-linux-operating-systems.pdf)

But I get into some problems this way aswell.

---

### Post by qui86 on 2020-04-27
My problems is that programs im trying to running doesnt support those drivers, and I need to use other ones.

---

### Post by CelticWarrior on 2020-04-27
There are NO OTHER DRIVERS for your card. Please stop whatever you're doing because there's a serious risk of breaking your Ubuntu.

'amdgpu' and 'amdgpu-pro' drivers are ONLY FOR NEWER CARDS.

---

### Post by qui86 on 2020-04-27
Yeah, I have probably broken 10 installations thus far.

AMD.COM refer me to installing: AMD Catalyst&#8482; 15.9 when I put it my card. Doesn't that make them propper drivers for my ubuntu installation? Im a bit confused here.

---

### Post by CelticWarrior on 2020-04-27
> **qui86 said:**
> Yeah, I have probably broken 10 installations thus far.

AMD.COM refer me to installing: AMD Catalyst™ 15.9 when I put it my card. Doesn't that make them propper drivers for my ubuntu installation? Im a bit confused here.

No, it isn't.
Those are old drivers and/or drivers for Windows.
There was a time when there were proprietary drivers for Linux that could be used as an alternative to the included open-source driver. But then, more than 5 years ago (yes, that's how outdated your approach is), AMD released most of the drivers in open-source. Support for all legacy hardware was then added to 'radeon' and newer hardware being supported by the new open-source driver 'amdgpu' and, for some systems/kernels, users can also opt to install the proprietary driver 'amdgpu-pro'.

In a nutshell, 'amdgpu-pro' can, under certain specific circumstances, be installed and replace 'amdgpu' but it CANNOT be installed to replace 'radeon'. Which driver to use is decided during the installation and it depends on the hardware. Again, NO USER ACTION REQUIRED.

---

### Post by qui86 on 2020-04-27
Ok. But there most be some other drivers out there, because I have had it working before and also on other dist of linux.

Thank you for your insight and help, never the less! bye

---

### Post by CelticWarrior on 2020-04-27
Before? In which Ubuntu release? And what other distros?

There was a time when your ~10 years old card had better support, in Linux and Windows. But as it happens with any old hardware there's always a time when it becomes obsolete, be it *de facto* obsolete or obsoleted simply by the fact that the manufacturer no longer supports it. The latter is your case. And no, not a Linux problem, the same happened in Windows.

---

### Post by QIII on 2020-04-27
In the present environment, modern Linux distributions are limited to two possible drivers for AMD products: the open-source radeon module or the open-source amdgpu module.  Both are present in recent Linux kernels and there is no need to install anything.

When you install Ubuntu (or others), the installer determines which driver module supports your hardware and sets which one will be used.  There is nothing to be done by the user.

If amdgpu supports your hardware (it does not with yours) and if AMDGPU-PRO (which is a proprietary overlay to amdgpu) is compatible, AMDGPU-PRO can be installed.  AMDGPU-PRO cannot be installed over radeon in any case, and cannot be used with some other GPUs that use amdgpu.

Catalyst for Linux is gone long gone.  AMD no longer supports it.  It will not work with modern versions of X Server.  Don't even try to install it.

There are no other options.

From your own post:

```

$ lsmod | grep radeon
radeon               1474560  14
ttm                   106496  1 radeon
drm_kms_helper        184320  1 radeon
i2c_algo_bit           16384  1 radeon
drm                   491520  9 drm_kms_helper,radeon,ttm

```

This clearly indicates that the radeon module is loaded.  This means that at install time, the installer determined that your GPU was supported only by the radeon driver module.  That is correct.  The 5870 is not a GCN (Graphics Core Next) 1.1 or greater GPU.  It's not even GCN.  Therefore, it is not supported by the amdgpu driver module.

---

### Post by mörgæs on 2020-04-27
Qui86, right now I am posting from a 
```

description: VGA compatible controller
product: RV730/M96 [Mobility Radeon HD 4650/5165]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:31 memory:80000000-8fffffff ioport:7000(size=256) memory:92300000-9230ffff memory:c0000-dffff

```
graphics processor and I am thankful that AMD has decided to support the GNU/Linux community by giving Radeon free under an open source license. This way I expect the card to be supported for many years to come without the Windows habit of searching for closed source drivers strange places.

If the system is too slow then you should try a lighter Buntu rather than experiment with drivers (as other people have mentioned there is only Radeon, and I have never experienced problems with it).

---

### Post by CelticWarrior on 2020-04-27
> **mörgæs said:**
> If the system is too slow then you should try a lighter Buntu rather than experiment with drivers (as other people have mentioned there is only Radeon, and I have never experienced problems with it).

Probably not that slow and very likely within what should be expected for hardware of that vintage. The OP said: > My problems is that programs im trying to running doesnt support those drivers
which is quite plausible if it's an old software looking for *fglrx**. *Sadly there's nothing we can do about it and users must understand that obsolesce is not a matter of *if*, it's a matter of *when* and for such software the "when" coincided with xUbuntu 14.04 original kernel going out of support.

---

### Post by Yellow Pasque on 2020-04-27
> **qui86 said:**
> But there most be some other drivers out there, because I have had it working before and also on other dist of linux.

Be more specific. What did you have working? What does not work out of the box?

---

### Post by nbutcher78 on 2020-04-28
I have to chime in on this thread.

I have a Ryzen 2400G which is an APU.

Thing is - some HDMI monitors are being detected with really low refresh rates OOTB (I defaulted to 23 Mhz on mine.) 
This gave me the initial impression that graphics drivers for the APU weren't loaded, or that I had to install proprietary ones.
I tried running games off steam and retropie and the graphics were jarring and terrible, with computer slowdowns on occasion.

When I discovered the low refresh rate on the screen, and as soon as I bumped up my HD TV to 60Hz refresh rate from the default all the problems disappeared.
The real issue here is default refresh rate detection IMHO.

Hope this helps someone.

---

### Post by QIII on 2020-04-28
The OP's hardware is not the same as yours.  Whatever issues you may be encountering have nothing whatsoever to do with the OP's problem -- which is simply that his/her older hardware uses the radeon module.

If you have an issue you would like help with, please start your own thread.

---

### Post by mörgæs on 2020-04-28
Your hardware is different from and much younger than original poster's so I guess that a moderator will soon move your post. 

Anyway, regarding your problem: Have you checked if the poor performance is related to Snap?

(Ninja'ed by QIII)

---

### Post by nbutcher78 on 2020-04-28
I updated my post.
It's somewhat related - as I had some motivation to look for other drivers until I realized the issue was the monitor config refresh rate (and the faulty default refresh rate detection)

---

