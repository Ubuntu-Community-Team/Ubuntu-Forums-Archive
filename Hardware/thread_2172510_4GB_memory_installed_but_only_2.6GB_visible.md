---
title: "4GB memory installed but only 2.6GB visible"
date: 2013-09-05
forum: Hardware
---

### Post by Tryfon on 2013-09-05
Hello,

I have a Lenovo Thinkpad T430u with 4GB of memory installed but for some reason which I can't comprehend only 2.6GB of those are visible and usable by my Ubuntu 13.04 64bit installation. Please advise.

---

### Post by TheFu on 2013-09-05
Does the video card "steal" RAM for itself?  That can account for 0.5 to 1G of missing RAM.
What is the output from 
```
sudo lshw -C memory
```
You may need to install the **lshw** package.

A quicker method:```

head  /proc/meminfo
```

---

### Post by Tryfon on 2013-09-05
This is the output of lshw
```
 *-memory
       description: System Memory
       physical id: 7
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM [empty]
          physical id: 0
          slot: ChannelA-DIMM0
     *-bank:1
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
          product: HMT351S6EFR8C-PB
          vendor: Hynix/Hyundai
          physical id: 1
          serial: 31C8D432
          slot: ChannelB-DIMM0
          size: 4GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
  *-firmware
       description: BIOS
       vendor: LENOVO
       physical id: d
       version: H6ET62WW (2.03 )
       date: 09/14/2012
       size: 128KiB
       capacity: 11MiB
       capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video pc98 acpi usb biosbootspecification netboot uefi

```

This is the output of head /proc/meminfo:
```
MemTotal:        2776840 kB
MemFree:          191644 kB
Buffers:            4876 kB
Cached:           408088 kB
SwapCached:       109580 kB
Active:          1593568 kB
Inactive:         814264 kB
Active(anon):    1558948 kB
Inactive(anon):   753800 kB
Active(file):      34620 kB

```

Your guess could be correct since the laptop has an nvidia chip paired with an intel HD under the nvidia optimus technology but I can't see anything relevant in the above output. The memory is not visible at all.

---

### Post by TheFu on 2013-09-05
I'd look inside the BIOS for any settings around video RAM use. Perhaps if you disable 1 of the GPUs?

---

