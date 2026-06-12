---
title: "Test for Artifacts"
date: 2015-07-31
forum: Hardware
---

### Post by frangoitia on 2015-07-31
Hello, I'm having some glitches with the UI and I'm afraid it can be down to hardware problems. For example when resizing a window I notice some strange behaviour in the ui. Also when minizing and restoring a terminal I usually see like a whie line in the upper part of the window manager. I don't know if this comes down to Ubuntu or to hardware problems. How can I thoroughly test my graphic card in Ubuntu ?

My motherboard is a Gigabyte GA-B75M-D3V and my processor is an Intel i3 2120

```
root@Fran-PC:/home/fran# lsb_release --short --codename&&uname --kernel-release&&lshw -c video
trusty
3.16.0-45-generic
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
```


I only have like a week left on guarantee so I have to act quick.

Thanks.

---

### Post by coldraven on 2015-07-31
If it uses system memory I guess that you could use memcheck. IIRC you have to hold the shift key when booting, then from the grub menu select memcheck.
Memcheck takes a long time, it maybe best to do it overnight.
You could also take out the memory cards and then re-seat them in case of a bad connection (with the PC powered off).

---

