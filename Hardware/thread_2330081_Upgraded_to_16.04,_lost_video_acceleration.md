---
title: "Upgraded to 16.04, lost video acceleration"
date: 2016-07-07
forum: Hardware
---

### Post by 46and22 on 2016-07-07
It appears an upgrade to 16.04 has broken my 3d acceleration.  I have integrated Intel graphics, info shown below.  I've tried upgrading the kernel to 4.5.3 (based on another forum suggestion), playing with drivers, etc.  The machine is used for media serving (Kodi) and as such does not boot into a regular desktop, but uses xinit to start Kodi.  Any advice on where to start looking?

```
root@<computer>:~# lshw -c video
  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:f7000000-f73fffff memory:e0000000-efffffff ioport:f000(size=64)


```

```

root@jtihtpc01:~# hwinfo --gfxcard
08: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.366]
  Unique ID: _Znp.DDnuhPI+YRB
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0152 "Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller"
  SubVendor: pci 0x1849 "ASRock Incorporation"
  SubDevice: pci 0x0152 
  Revision: 0x09
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf7000000-0xf73fffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (ro,non-prefetchable)
  I/O Ports: 0xf000-0xf03f (rw)
  IRQ: 31 (558 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00000152sv00001849sd00000152bc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #8



```

---

### Post by Yellow Pasque on 2016-07-07
/var/log/Xorg.0.log is always good

---

### Post by 46and22 on 2016-07-07
> **Temüjin said:**
> /var/log/Xorg.0.log is always good

Yes of course, I should have done that.  Interestingly, when I load an XFCE session using "startx", and THEN load Kodi, I do not have the same issue.  CPU utilization does not spike, the GUI is very responsive, etc.

"Normal" bootup Kodi/xinit log - [http://pastebin.com/7fbggby2](http://pastebin.com/7fbggby2)

Manual "startx" and load Kodi log - [http://pastebin.com/shV0SWJT](http://pastebin.com/shV0SWJT)

---

### Post by 46and22 on 2016-07-24
Bump, any thoughts?  I still cant figure it out.  :(

---

