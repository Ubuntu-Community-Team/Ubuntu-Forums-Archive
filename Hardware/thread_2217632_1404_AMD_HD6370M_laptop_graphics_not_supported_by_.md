---
title: "14:04: AMD HD6370M laptop graphics not supported by fglrx"
date: 2014-04-18
forum: Hardware
---

### Post by robi-hipnos on 2014-04-18
Fresh install of Ubuntu 14.04 x64 and after installing AMD graphics support there was blank screen after boot. The same was with fglrx and fglrx-updates. I had to go to safe mode and manualy remove all of fglrx to get X running again.

Such a shame we have to deal with graphic issues on LTS release again.

---

### Post by varunendra on 2014-04-19
I am not a graphics guy, but it may get you some help if you post the model name/number of your graphics card. I believe the following command outputs are sufficient to provide that -
```
lspci -nnk | grep -iA3 vga
sudo lshw -C display
```

While posting the outputs, please use 'Code' tags as I asked in your other thread in Networking section.

---

### Post by robi-hipnos on 2014-04-20
lspci -nnk | grep -iA3 vga
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] [1002:68e4]
    Subsystem: ASUSTeK Computer Inc. Radeon HD 6370M [1043:1c92]
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68]
```

sudo lshw -C display
```
  *-display               
       description: VGA compatible controller
       product: Robson CE [Radeon HD 6370M/7370M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:c0000000-cfffffff memory:d0020000-d003ffff ioport:d000(size=256) memory:d0000000-d001ffff
```

I hope it helps and thanks :)

---

### Post by maureyes0126 on 2015-02-26
I have the same problem, I tried all but nothing does work. HELP :confused:

---

### Post by JuanCarlito on 2015-08-24
I have some problem. Tried so many ways to install but didn't work. Anybody have idea about this problem ?

---

### Post by QIII on 2015-08-24
After installing the driver, becore rebooting, did you do

```
sudo amdconfig --initial 
```?

This is not supposed to be necessary any longer, but failing to do so seems to still cause problems occasionally.

---

