---
title: "Video Driver problem(possibly) on Asus k550J"
date: 2016-03-04
forum: Hardware
---

### Post by tommy30 on 2016-03-04
Hey,

I'm sort of new to ubuntu and so i'm wondering how to get the correct video drivers.

So i installed ubuntu 15.10 willy.

During the setup i had to use nomodeset and aspi=0.

After installing sucessfully, window dragging was super slow and most graphic related stuff like poping up a menu so i thought its probably a graphics driver's issue.

I installed intel graphic drivers from here: [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0)

On Additional Drivers tab from Software & Updates, the driver selected for GeForce GTX 850M is Nouveau display driver since the others (NVIDIA binary driver) all give me a black screen after login.

None of the above worked on solving the slugginess. Using *Disable VESA framebuffer driver* option on xdiagnose solved it.

And now when i run ```
lshw -c video
``` and ```
lspci -v
```, i get the following output,

```
tommy@tommy-X550JK:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: 3D controller
       product: GM107M [GeForce GTX 850M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
        resources: memory:f6000000-f6ffffff memory:e0000000-efffffff  memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
tommy@tommy-X550JK:~$ lspci -v
...
00:02.0  VGA compatible controller: Intel Corporation 4th Gen Core Processor  Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
...
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 850M] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
...

```

It means i'm not using the right drivers, right?

Maybe related to the issue here [http://ubuntuforums.org/showthread.php?t=2301048&highlight=X550JK](http://ubuntuforums.org/showthread.php?t=2301048&highlight=X550JK) , same laptop same issues when installing/ had to use nomodeset or else nouveau unk6 error.

---

### Post by SeijiSensei on 2016-03-05
Machines with "hybrid" video like yours can be problematic.  See if you can disable the Intel video adapter in the system's BIOS and use only the NVIDIA device.  If so, then install the proprietary NVIDIA driver with the Driver Manager application, or from the terminal with
```
sudo apt-get install nvidia-current
```

---

