---
title: "Video card has dissapeared"
date: 2016-11-14
forum: Hardware
---

### Post by mar0029 on 2016-11-14
Hello all,

I'm at my wit's end and don't know what else to do. 

I have a hybrid video card setup on my dell 3510 notebook: Intel HD graphics 530 and a Venus LE [Radeon HD 8830M]
It seems that I can no longer see my AMD card. When I do lshw -c video, only the Intel onboard chipset appears. 

I was trying to install the amd catalyst fglrx, so that i could use OpenCL. 

Running
Ubuntu 14.04 LTS, kernel 4.4.0-47-generic

---

### Post by Bashing-om on 2016-11-14
mar0029; Hello;

It is like this, you are caught in the mash . amd has gone full bore to support opensource and no longer makes up a proprietary driver for the updated/upgraded kernels. There be adjustment pains for sure .
See: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
where the verde series cards take the radeon driver.
If you really really have to have the FGLRX (proprietary) driver, then the only recourse you have is to fresh install a earlier release ; 14.04.1 // .. The 1 point release will not include the later unsupported kernels .

To see the graphics's cards try:
```

lspci -vnn | grep VGA -A 12
lspci | grep -e VGA -e 3D

```


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by QIII on 2016-11-14
From 16.04 forward, fglrx is no longer an option.  AMD is no longer supporting it.

There will be three possible drivers:  

The open source Radeon driver (much, much improved!) for pre-GCN GPUs.

The open source AMDGPU driver for GCN GPUs.  Currently GCN 1.2 and later GPUs are covered.  Some GCN 1.1  GPUs are covered.  Support for the rest of the GCN 1.1 and the GCN 1.0 cards is coming.  I believe that will include GPUs later than the HD 7000 series.

The open source/hybrid proprietary AMDGPU-PRO driver, which is AMDGPU with a proprietary overlay which provides some special goodies.

In your case, you have a hybrid Intel/AMD system.  I'm not sure how that all plays right at the meoment.

For a list of what I know to be supported by AMDGPU right now, please have a look at [this]("http://theleftcoastgeek.net/index.php/general-interest/11-amd-gpu-support-with-amdgpu-and-amdgpu-pro") article on my blog.

---

### Post by mar0029 on 2016-11-14
lspci -vnn | grep VGA -A 12 gives
```
sslt@sslt-Precision-3510:~$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 530 [8086:191b] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:06e0]
    Flags: bus master, fast devsel, latency 0, IRQ 129
    Memory at eb000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915_bpo

00:04.0 Signal processing controller [1180]: Intel Corporation Skylake Processor Thermal Subsystem [8086:1903] (rev 07)
    Subsystem: Dell Device [1028:06e0]
    Flags: fast devsel, IRQ 16


```

and  lspci grep -e VGA -e 3D   gives
```
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
```

where before I would get at least two prompts, one for my Intel and one for the AMD card. The AMD card said it was unclaimed but it was still there.

---

### Post by Bashing-om on 2016-11-14
mar0029; Yuk !

Totally unexpected results;
What does X have to relate to the situation ?
post back:
```

cat /var/log/Xorg.0.log

```

to see
[INDENT][INDENT]what tale is told
[/INDENT][/INDENT]

---

### Post by mar0029 on 2016-11-14
Sorry for the delay. 
cat /var/log/Xorg.0.log gives me the following.
had to link to pastebin. the forum didn't like the formatting.

[http://pastebin.com/5QHgD6A8](http://pastebin.com/5QHgD6A8)

Interestingly, lshw | less gives this

```

     *-pci
          description: Host bridge
          product: Skylake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Skylake PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:e000(size=4096) memory:ec200000-ec2fffff ioport:c0000000(size=268435456)
           *-generic
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=255 maxlatency=255 mingnt=255
                resources: irq:130 memory:c0000000-cfffffff memory:ec200000-ec23ffff ioport:e000(size=256) memory:ec240000-ec25ffff
        *-display
             description: VGA compatible controller
:WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
             product: HD Graphics 530
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915_bpo latency=0
             resources: irq:129 memory:eb000000-ebffffff memory:80000000-8fffffff ioport:f000(size=64)


```

In reference to the Pastebin link, lines 54 and 55 are interesting

---

### Post by Bashing-om on 2016-11-14
mar0029; Well !

To be honest I had expected to see the ATI card turned off in bios . lines 54 and 55 tell otherwise. The kernel sees the cards and assigns a PCI slot . And as there is no module available - I think we can disregard " BIOS @ 0x????????/131072 " .


When we get to :
> 
 29.173] (WW) Warning, couldn't open module fglrx
29.173] (EE) Failed to load module "fglrx" (module does not exist, 0)

Is X just looking and checking ? I am not to sure on this point .
which as we know in "vmlinuz-4.4.0-47-generic.efi.signed " that FGLRX is not supported .

So where I am now is to find these FGLRX components, remove them and install the xserver-xorg-video-radeon driver.

Then X says happy with radeon !
Loading radeon :
> 
[    29.173] (II) LoadModule: "radeon"
[    29.173] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    29.201] (II) Module radeon: vendor="X.Org Foundation"


But, still trying to load FGLRX !
> 
29.202] (EE) Failed to load module "fglrx" (module does not exist, 0)


HUH ?? Loading radeon & loading Intel drivers.
> 
29.251] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
29.251] (--) RADEON(G0): Chipset: "VERDE" (ChipID = 0x682b)
 30.244] (II) RADEON(G0): glamor detected, initialising EGL layer.
30.256] (II) RADEON(G0): [DRI2] Setup complete

30.358] (II) intel(0): [DRI2] Setup complete
30.358] (II) intel(0): [DRI2]   DRI driver: i965


X seems to be as happy as a clam .

So what have we for FGLRX in the system ?
show:
```

dpkg -l fglrx*
lsmod | grep fglrx
fglrxinfo

```

Then all I can think of is to see if we can get the opensource graphic's controller switcheroo functional in xenial .
I have not seen this done ,, so be a learning curve here also for me.

[INDENT][INDENT]'other one of those
[INDENT][INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mar0029 on 2016-11-15
First:
```
sslt@sslt-Precision-3510:~$ dpkg -l fglrx*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version          Architecture     Description
+++-======================-================-================-=================================================
un  fglrx                  <none>           <none>           (no description available)
iF  fglrx-core             2:15.201-0ubuntu amd64            Minimal video driver for the AMD graphics acceler
un  fglrx-driver-core      <none>           <none>           (no description available):
un  fglrx-glx              <none>           <none>           (no description available)
un  fglrx-updates          <none>           <none>           (no description available)
un  fglrx-updates-core     <none>           <none>           (no description available)
```

Second:
No output

Third:
```
sslt@sslt-Precision-3510:~$ fglrxinfo
fglrxinfo: command not found
```

Thank you for all your help. I've asked some colleagues of mine and they didn't know where to start :o

EDIT: I went ahead and did a ```
sudo dpkg -r fglrx-core
``` and I can now see my video card with sudo lshw. But it says it is unclaimed. See here. ```
*-display UNCLAIMED
                description: Display controller
                product: Venus LE [Radeon HD 8830M]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 87
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff memory:ec200000-ec23ffff ioport:e000(size=256) memory:ec240000-ec25ffff
```

What now?

---

### Post by Bashing-om on 2016-11-15
mar0029; Good deal,

Making good progress,

OK let's explicitly install the opensource driver and mesa utilities .
```

sudo apt install dkms
sudo apt install xserver-xorg-video-radeon
sudo apt install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

If no errors, and system seems happy happy happy at this time .. now 
Re-Boot
To see the effect .

[INDENT][INDENT][INDENT]do we have lift-off ?
[/INDENT][/INDENT][/INDENT]

---

### Post by mar0029 on 2016-11-16
Bashing-om; Thank you for all your help! 

I installed/re-installed the open source drivers. Everything seemed to install fine i.e. no errors occurred. However I still get mixed results from different queries. 

lspci shows an AMD card but the wrong model number...
shows Radeon HD 8830M but I have an AMD FirePro W5130M.
```

sslt@sslt-Precision-3510:~$ lspci
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Skylake PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-LM (rev 31)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus LE [Radeon HD 8830M] (rev ff)
02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)

```

sudo lshw gives this
```

           *-generic
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=255 maxlatency=255 mingnt=255
                resources: irq:130 memory:c0000000-cfffffff memory:ec200000-ec23ffff ioport:e000(size=256) memory:ec240000-ec25ffff

```

---

### Post by Yellow Pasque on 2016-11-16
I find this guide helpful with basic GPU switching (the basic commands apply to AMD GPU's as well): [https://nouveau.freedesktop.org/wiki/Optimus/](https://nouveau.freedesktop.org/wiki/Optimus/)

So check:
```
xrandr --listproviders
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```

> **mar0029 said:**
> lspci shows an AMD card but the wrong model number...
shows Radeon HD 8830M but I have an AMD FirePro W5130M.

The w5130M is based on that card, so they may have the same PCI ID (1002:682b). It's not something to worry about.
[http://pci-ids.ucw.cz/read/PC/1002/682b](http://pci-ids.ucw.cz/read/PC/1002/682b)

---

### Post by mar0029 on 2016-11-16
Temüjin; thank you for your reply!

When I did  xrandr --listproviders I got:
```

sslt@sslt-Precision-3510:~$ xrandr --listproviders 
Providers: number : 3
Provider 0: id: 0x70 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 7 associated providers: 2 name:Intel
Provider 1: id: 0x45 cap: 0x6, Sink Output, Source Offload crtcs: 6 outputs: 0 associated providers: 2 name:radeon
Provider 2: id: 0x45 cap: 0x6, Sink Output, Source Offload crtcs: 6 outputs: 0 associated providers: 2 name:radeon

```

and the switcheroo gave
```

sslt@sslt-Precision-3510:~$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
[sudo] password for sslt: 
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0


```

---

### Post by mar0029 on 2016-11-16
Everyone that has helped:

I have an identical machine in which no changes have been made. When I run the same few commands in checking for the AMD card, I get the same results...

As far as I'm concerned, this problem has been solved.

So a few questions: 
[LIST=1]
[*]In this current "[Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics#Using_vga_switcheroo")" set-up, can I still use the AMD card for things like OpenCL, without having the fglrx drivers installed?
[*]What steps can I take to start using OpenCL?
[*]Do I need to start asking these questions in another thread?
[/LIST]


Thanks Again!!!

---

### Post by QIII on 2016-11-16
Hi!

One subject per thread is what we would like to see.  That is much less confusing than several.  Three threads are better than one if you have three issues.

Cheers!

---

