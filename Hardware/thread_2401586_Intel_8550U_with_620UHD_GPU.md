---
title: "Intel 8550U with 620UHD GPU"
date: 2018-09-19
forum: Hardware
---

### Post by r34skyline on 2018-09-19
Community,

I picked up a new Lenovo IdeaPad 720S which comes with the KabyLake i7-8550U chip with Intel 620UHD Chip. Ran the Intel SSU Scan Tool and sent to their support and Intel told me to look here for the driver but I can't find it. Basically my screen is flashing like crazy and I'm hoping to find the driver here. Also running Ubuntu 18.04 LTS.

So here are some of the details from the SSU scan

## Scanned Hardware
Computer:
          BaseBoard Manufacturer:"LENOVO"
          Bios Mode:"UEFI"
          Bios Version/Date:"6MCN28WW,07/18/2018"
          CD or DVD:"Not Available"
          Platform Role:"Linux krinko-720S 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux"
          Processor:"Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz"
          SMBIOS Version:"3.0.0"
          Sound Cards:"HDA-Intel - HDA Intel PCH"
          Sound Cards:"HDA Intel PCH at 0x2ff3018000 irq 142"
          System Manufacturer:"LENOVO"
          System Model:"81BV"
          System Type:"x64-based PC"
          - Display
               - "Intel Corporation UHD Graphics 620 (rev 07) (prog-if 00 [VGA controller])"
                    Adapter RAM:"size=256M"
                    Capabilities:"[40] Vendor Specific Information: Len=0c <?>"
                    Capabilities:"[70] Express Root Complex Integrated Endpoint, MSI 00"
                    Capabilities:"[ac] MSI: Enable+ Count=1/1 Maskable- 64bit-"
                    Capabilities:"[d0] Power Management version 2"
                    Capabilities:"[100] Process Address Space ID (PASID)"
                    Capabilities:"[200] Address Translation Service (ATS)"
                    Capabilities:"[300] Page Request Interface (PRI)"
                    Caption:"Intel Corporation UHD Graphics 620 (rev 07) (prog-if 00 [VGA controller])"
                    Device ID:"17aa:39af"
                    Driver:"i915"
                    Driver Path:"/lib/modules/4.15.0-34-generic/kernel/drivers/gpu/drm/i915/i915.ko"
                    Driver Provider:"Intel Corporation"
                    Driver Provider:"Tungsten Graphics, Inc."
                    Driver Version:""
                    Flags:"bus master, fast devsel, latency 0, IRQ 132"
                    I/O Ports:"I/O ports at 3000 [size=64]"
                    Location:"pci@0000:00:02.0"
                    Manufacturer:"Intel Corporation [8086]"
                    Power Management Capabilities:"Power Management version 2"
                    Refresh Rate - Current:"60.00  59.98    59.97  "
                    Resolution:"3840x2160  59.98    59.97  "

Anyone happen to know what driver I need to run to stop the screen from gliching/flashing?

Thanks,

Joe

---

### Post by Yellow Pasque on 2018-09-19
You are already using the correct driver. If it was me, I would throw Ubuntu 18.10 (or another very recent distro) on a USB stick and see if the problem occurred there.

---

### Post by r34skyline on 2018-09-23
> **Temüjin said:**
> You are already using the correct driver. If it was me, I would throw Ubuntu 18.10 (or another very recent distro) on a USB stick and see if the problem occurred there.



Still happens on Ubuntu 18.10, Debian, Fedora, CentOS, and Deepin. Guess I could try Arch and see how that does but I have a feeling it won’t work. I have also not tried any Unix flavors. I really would like to get Ubuntu 18 working but I have limited hopes. I also have no clue what logs to pull to see why it’s happening. The only OS that works no issues is Windows but who wants that...

---

### Post by aeronau on 2019-04-21
I am experiencing the same problem in Ubuntu 19.04. I have an Asus UX391UA with an Intel 8550U with 620UHD GPU. If I don't use nomodeset or 915.modeset=0, the screen constantly flickers, and even though it's usable (but barely), it's extremely annoying.

---

