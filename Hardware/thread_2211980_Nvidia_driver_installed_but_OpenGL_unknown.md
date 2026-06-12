---
title: "Nvidia driver installed but OpenGL unknown"
date: 2014-03-18
forum: Hardware
---

### Post by ElToro on 2014-03-18
I have installed the latest Nvidia driver for my MSI GE70 laptop with a GeForce GTX 765M graphics card. Some games crash (intermittently), in particular Metro LL. Investigating the status of the driver, I get conflicting info:

sudo lshw -C Display gives:

```

  *-display               
       description: 3D controller
       product: GK106M [GeForce GTX 765M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

However, the System Profiler and Benchmark gives:

```

[TABLE]
[TR]
[TD="class: stitle, colspan: 3"][/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**Display**[/TD]
[/TR]
[TR]
[TD="class: field"]Resolution[/TD]
[TD="class: value"]1920x1080 pixels[/TD]
[/TR]
[TR]
[TD="class: field"]Vendor[/TD]
[TD="class: value"]The X.Org Foundation[/TD]
[/TR]
[TR]
[TD="class: field"]Version[/TD]
[TD="class: value"]1.15.0[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**Monitors**[/TD]
[/TR]
[TR]
[TD="class: field"]Monitor 0[/TD]
[TD="class: value"]1920x1080 pixels[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**Extensions**[/TD]
[/TR]
[TR]
[TD="class: field"]BIG-REQUESTS[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Composite[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]DAMAGE[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]DOUBLE-BUFFER[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]DPMS[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]DRI2[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]DRI3[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]GLX[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Generic Event Extension[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]MIT-SCREEN-SAVER[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]MIT-SHM[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Present[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]RANDR[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]RECORD[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]RENDER[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]SECURITY[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]SGI-GLX[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]SHAPE[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]SYNC[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]X-Resource[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XC-MISC[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XFIXES[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XFree86-DGA[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XFree86-VidModeExtension[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XINERAMA[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XInputExtension[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XKEYBOARD[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XTEST[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]XVideo[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**OpenGL**[/TD]
[/TR]
[TR]
[TD="class: field"]Vendor[/TD]
[TD="class: value"]Unknown[/TD]
[/TR]
[TR]
[TD="class: field"]Renderer[/TD]
[TD="class: value"]Unknown[/TD]
[/TR]
[TR]
[TD="class: field"]Version[/TD]
[TD="class: value"]Unknown[/TD]
[/TR]
[TR]
[TD="class: field"]Direct Rendering[/TD]
[TD="class: value"]No[/TD]
[/TR]
[/TABLE]


```

Shouldn't the card show up under OpenGL, when it is otherwise correctly installed with the right driver? Any advice on how to fix this would be greatly appreciated :)

---

### Post by spasmoid on 2014-12-11
Wow. March 19th hey? Linux support is not what it used to be.

I basically have the same problem. I went to NVIDIA's site and downloaded drivers. It took me ages to fix all the issues to get them installed. So now I had a power outage, and when the machine comes back up, it suddenly forgets it's OpenGL support (and XBMC refuses to load).

---

