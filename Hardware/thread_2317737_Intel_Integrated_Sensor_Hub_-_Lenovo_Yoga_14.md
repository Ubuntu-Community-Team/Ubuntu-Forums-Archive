---
title: "Intel Integrated Sensor Hub - Lenovo Yoga 14"
date: 2016-03-19
forum: Hardware
---

### Post by MisteR2 on 2016-03-19
Hello Everyone!

Getting back into the tablet game, and what better way than to try to track down the sensors on a new Lenovo Yoga 14! :D

From what I've seen, everything (on Windows 10) is going through this new fancy Intel Integrated Sensor Solution, which then goes to another device, then splits out into four different devices within Windows 10 device manager (ambient light, gyroscope, rotation, GPS?). What do we get in Ubuntu?

```


From lshw:

...

        *-generic:1 UNCLAIMED
             description: Non-VGA unclassified device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:d564b000-d564bfff

from lspci:

00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)

...

```

And from what I can see, not too much beyond that right now. Trawled through sysfs and not getting as much there. I can enable the device, and force it to rescan, but nothing new comes up, except for an error in dmesg about bogus alignment:

```
[ 4818.251001] pci 0000:00:13.0: enabling device (0000 -> 0002)
[ 5191.273767] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
```

I've seen some messages of support for this device within intel-lpss, but the device ID isn't listed within the driver's page on lkddb, nor is it trying to take control of the device.

Brain is a bit burnt up right now from banging on this for a bit (4AM where I'm at right now), but if anyone has any pointers on probing PCI devices, or ways to get devices that are under this one to enumerate within sysfs or appear for the i2c devices (so many modules modprobed, got back a lot of nothing) it would be greatly appreciated.

---

### Post by MisteR2 on 2016-03-23
Dug into this a bit further, and after playing around with setpci and "lspci -s 00:13.0 -nnvvxxx", I'm wondering if this might be something solved by allowing the hid-sensor-hub driver to try to take control over the device by adding it to drivers/hid/hid-ids.h... Immediate issue there is that the devices defined within [https://github.com/torvalds/linux/blob/master/drivers/hid/hid-ids.h](https://github.com/torvalds/linux/blob/master/drivers/hid/hid-ids.h) all appear to be based on usb and not something hanging off the host bridge:

```
-[0000:00]-+-00.0  Intel Corporation Sky Lake Host Bridge/DRAM Registers
           +-02.0  Intel Corporation Sky Lake Integrated Graphics
           +-08.0  Intel Corporation Sky Lake Gaussian Mixture Model
           +-13.0  Intel Corporation Device 9d35
           +-14.0  Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller
           +-14.2  Intel Corporation Sunrise Point-LP Thermal subsystem
           +-16.0  Intel Corporation Sunrise Point-LP CSME HECI #1
           +-17.0  Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode]
           +-1c.0-[02]----00.0  O2 Micro, Inc. SD/MMC Card Reader Controller
           +-1c.5-[03]----00.0  Intel Corporation Wireless 8260
           +-1d.0-[06]----00.0  NVIDIA Corporation GM108M [GeForce 940M]
           +-1e.0  Intel Corporation Sunrise Point-LP Serial IO UART Controller #0
           +-1e.2  Intel Corporation Sunrise Point-LP Serial IO SPI Controller #0
           +-1f.0  Intel Corporation Sunrise Point-LP LPC Controller
           +-1f.2  Intel Corporation Sunrise Point-LP PMC
           +-1f.3  Intel Corporation Sunrise Point-LP HD Audio
           +-1f.4  Intel Corporation Sunrise Point-LP SMBus
           \-1f.6  Intel Corporation Ethernet Connection I219-V
```

Still digging. Checking into things around "hid_scan_collection" as there's some code around what to do once a sensor hub has been identified. Walking it back from there. :)

---

### Post by MisteR2 on 2016-03-26
And more progress. :)

Checked into the code for the intel-lpss driver, and found where the hardware IDs lived in the PCI support driver. Added the ID for the chipset, compiled it, added it in, activated it. Dmesg now gives us:

```
[28347.784131] intel-lpss 0000:00:13.0: enabling device (0000 -> 0002)
[28347.841257] idma64 idma64.0: Found Intel integrated DMA 64-bit
[28347.842320] idma64 idma64.1: Found Intel integrated DMA 64-bit
[28347.843563] dw-apb-uart.1: ttyS4 at MMIO 0xd564e000 (irq = 20, base_baud = 115200) is a 16550A
[28347.860403] idma64 idma64.2: Found Intel integrated DMA 64-bit
[28347.874768] i2c_designware i2c_designware.0: Unknown Synopsys component type: 0x00000000
```

More than what we were getting earlier. The messages around dw-apb-uart and i2c_designware appear to be linked together. Digging further for info there.

---

### Post by MisteR2 on 2016-03-30
So... maybe that wasn't progress...

Reached out to the developers of the intel-lpss module, and the hardware that I'm working with isn't compatible with that driver. Rolled back that change on my end.

They did mention that work was ongoing for a module for that device, which is awesome! So, I'm going to wait and see how things come out with that. 

Should I hear anything, I'll be back. :)

---

### Post by axkibe on 2016-04-18
I got a Yoga 460 here, and I too have a
> 00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)
device in lspci. Im pretty sure this what I need to get going to get the accelerometer.
[https://www.google.at/?q=pci+9d35](https://www.google.at/?q=pci+9d35) gives a pretty clear picture, this is the sensor hub sitting directly on the PCI bus.

I have just no idea where to take it from here. Which linux kernel community should one ping?

---

### Post by axkibe on 2016-04-19
I got a kind reply from an engineer from Intel, yes the PCI device 8086/d935 is the sensor hub. No, there is no Linux driver for it yet available, the existing senser hub driver is missing the required transport layer. Intel is working on one. Non-authoritative answer: they plan to get it into kernel 4.8.

---

### Post by ptt2 on 2016-06-07
Thanks for the information, on my HP Spectre x360 13-4110 I too have the same

```
00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)
```

Would be very nice if they can make it work before next Ubuntu release.

---

### Post by MisteR2 on 2016-06-21
I've been trying to apply the patches to a copy of kernel 4.6.0 after applying the necessary Debian patches to the kernel, but I'm not having much success. Has anyone here been able to successfully build the kernel with the patches, and have the module appear under /sys/modules or some other place where built-in modules are listed? If so, was there anything special that you needed to do?

Link to patches:
[http://thread.gmane.org/gmane.linux.kernel.iio/24386](http://thread.gmane.org/gmane.linux.kernel.iio/24386)

Thanks!

---

