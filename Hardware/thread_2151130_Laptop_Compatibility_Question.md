---
title: "Laptop Compatibility Question"
date: 2013-06-03
forum: Hardware
---

### Post by Condenzationator on 2013-06-03
First, I apologize if I'm posting this in the wrong forum section, it just seems to be the right place to ask. :)

I'm looking into purchasing a customized laptop from CyberPowerPC.
I'd prefer to run Linux (preferably Ubuntu, but other distros are a plus of course) on the laptop as the main operating system. Windows 7 will be used in a virtual box for non-linux compatible software.
My question is this: As per the hardware configuration below, will the laptop run Ubuntu without any issues? For example, are there compatible, _working_ drivers for the graphics card? I don't want a temperature-control issue like what I get with my current laptop. If I need to add or clarify any details, please let me know!

Model: Xplorer X7-7650
CPU: Intel i7-4700MQ
Motherboard: Intel HM87 Express Chipset
Memory: 16GB DDR3-1333 SODIMM
Video card: nVidia GTX765M 2GB PCIe
Hard Drive: 120GB Intel 510 Series SATA-III 6.0Gb/s
Data Hard Drive: 750GB 7,200 RPM SATA300
Wireless Card: Intel Centrino Ultimate-N 6300 a/b/g/n

Thank you for your time and help!

---

### Post by Yellow Pasque on 2013-06-03
> are there compatible, working drivers for the graphics card?
That system has two graphics cards (in hybrid/Optimus setup), the Intel IGP and the nvidia one. Intel Haswell graphics might be rough, even if you use bleeding edge graphics stack (xorg-edgers PPA): [http://www.phoronix.com/scan.php?page=article&item=intel_haswell_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_haswell_linux&num=1)

Then, there is the Nvidia card, which doesn't look like it's supported yet as of nvidia release 319.23

---

### Post by niclaso on 2013-06-29
> **Temüjin said:**
> Then, there is the Nvidia card, which doesn't look like it's supported yet as of nvidia release 319.23

Actually it has been supported since 319.12:
[https://devtalk.nvidia.com/default/topic/542748](https://devtalk.nvidia.com/default/topic/542748)

---

