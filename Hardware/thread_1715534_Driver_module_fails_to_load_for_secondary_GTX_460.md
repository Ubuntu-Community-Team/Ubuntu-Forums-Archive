---
title: "Driver module fails to load for secondary GTX 460"
date: 2011-03-27
forum: Hardware
---

### Post by houyunqing on 2011-03-27
I'm using a notebook. The primary card is an ATI X1600. The GTX 460 is connected to my notebook through a PCIe adaptor.

Before I boot into any OS, I run a PCI script to adjust the PCI address space. Under Windows 7 the driver works perfectly (I only play with CUDA and I don't have external monitor). But under my Ubuntu Desktop10.10 the driver is saying that it does not support my card (the Additional Information in those linux driver download pages tell me that the driver probably won't work on notebooks when I cannot disable my integrated card). Is there a way to get around this problem? i.e. load the driver module without disabling my ATI X1600? I just want the X1600 to do the drawing for Xserver and the GTX 460 to do CUDA for me.


More info:

I used apt-get to install the driver 270.29
lspci correctly identifies the GTX 460 (02:00.0) and the audio device(02:00.1) on it
My ATI X1600 is on 01:00.0

insmod nvidia.ko does not work and it creates error message in /var/log/kern.log. The message basically means the driver does not support my GTX 460 (10de:0e22)
If I set Driver under "Device" to "nvidia" in /etc/X11/xorg.conf, the same error message appears in kern.log, and Xserver would fail to start
Even if I set "UseInt10Module" to "true" it still gives the same error
part of my kern.log:
Mar 27 02:37:09 noidu kernel: [ 1000.835599] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 27 02:37:09 noidu kernel: [ 1000.835621] nvidia 0000:02:00.0: setting latency timer to 64
Mar 27 02:37:09 noidu kernel: [ 1000.835637] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=none,decodes=none:owns=none
Mar 27 02:37:09 noidu kernel: [ 1000.835707] NVRM: The NVIDIA GPU 0000:02:00.0 (PCI ID: 10de:0e22) installed
Mar 27 02:37:09 noidu kernel: [ 1000.835710] NVRM: in this system is not supported by the 270.29 NVIDIA Linux
Mar 27 02:37:09 noidu kernel: [ 1000.835713] NVRM: graphics driver release. Please see 'Appendix A -
Mar 27 02:37:09 noidu kernel: [ 1000.835716] NVRM: Supported NVIDIA GPU Products' in this release's README,
Mar 27 02:37:09 noidu kernel: [ 1000.835718] NVRM: available on the Linux graphics driver download page at
Mar 27 02:37:09 noidu kernel: [ 1000.835721] NVRM: [www.nvidia.com](www.nvidia.com).
Mar 27 02:37:09 noidu kernel: [ 1000.835736] nvidia 0000:02:00.0: PCI INT A disabled
Mar 27 02:37:09 noidu kernel: [ 1000.835752] nvidia: probe of 0000:02:00.0 failed with error -1
Mar 27 02:37:09 noidu kernel: [ 1000.835806] NVRM: The NVIDIA probe routine failed for 1 device(s).
Mar 27 02:37:09 noidu kernel: [ 1000.835811] NVRM: None of the NVIDIA graphics adapters were initialized!

Thanks a lot for any help!!

---

### Post by houyunqing on 2011-03-28
any one?

---

