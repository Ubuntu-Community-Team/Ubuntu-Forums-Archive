---
title: "Ubuntu without powernow_k8?"
date: 2009-06-21
forum: Hardware
---

### Post by Troublegum on 2009-06-21
Hi all,


I am running an AMD X2 5050e on an Asus M3A78-EM mainboard and Ubuntu 9.04.

Now I'd like to try undervolting with cpupowerd and that software requires the kernel module powernow_k8. But when I try to load it with
```
sudo modprobe powernow_k8
```I get the error
```
FATAL: Module powernow_k8 not found.
``````
dmesg | grep powernow
[    4.887498] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 5050e processors (2 cpu cores) (version 2.20.00)
[    4.887617] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x10
[    4.887685] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0x12
[    4.887742] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x14
[    4.889542] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x16
[    4.889599] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x18
[    4.889656] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x1a
```The ondemand/manual governor seems to work (according to the gnome applet).
When I use Fedora 11, the powernow_k8 module loads automatically. 

I use the kernel 2.6.28-13-generic but I've tried the Karmic Koala Alpha 2 with the same result.

Is this related to [Bug #355232: **acpi-cpufreq/powernow-k8 should not be built-in into the kernel image**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355232")?
Also found this on google: [http://www.linux-phc.org/forum/viewtopic.php?f=8&t=67](http://www.linux-phc.org/forum/viewtopic.php?f=8&t=67)
What does this mean?

---

### Post by Troublegum on 2009-06-23
Does this mean I cant run software that requires powernow_k8?

---

### Post by permieshane on 2009-07-06
I am hoping that someone knows as I am about to buy this combo:)

---

### Post by balak on 2009-10-25
Maybe this is too late for you Troublegum, but I just came across this thread :)

To find whether a module is loaded in the current kernel, use this command 'lsmod'. So for checking powernow-k8, you can do 
$lsmod | grep powernow 

Unfortunately, ubuntu has started compiling the powernow-k8 module into the kernel binary from Jaunty, so it is not loaded separately as a module. hence you cannot do 'modprobe powernow-k8' to actually load a module.

Yes, this means undervolting/overclocking stuff done by ppl using powernow or phc-k8 will not be very easy. You'll have to recompile the whole kernel which is a PITA.

---

