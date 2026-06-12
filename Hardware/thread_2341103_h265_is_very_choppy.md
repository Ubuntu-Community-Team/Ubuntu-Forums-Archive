---
title: "h265 is very choppy"
date: 2016-10-24
forum: Hardware
---

### Post by freeworld4 on 2016-10-24
h265 doesn't play smoothly.
I am using gnome and lubuntu currently on lxde. Ubuntu version 16.10.
7.7 gigabytes of ram and 7.9 gb of swap

Inspiron N5050

   description: CPU
          product: Intel(R) Pentium(R) CPU B950 @ 2.10GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU B950 @ 2.10GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1599MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm epb xsaveopt dtherm arat pln pts cpufreq

Here is a complete listing of my hardware: [http://pastebin.com/raw/WyT9jjek](http://pastebin.com/raw/WyT9jjek)

---

### Post by TheFu on 2016-10-25
h.265 support isn't in the GPU hardware or the drivers. A slow CPU can't handle it at higher resolutions. The resolution of the video will matter greatly.
A few options:
a) Transcode it down to 600p or 480p resolution if you want to keep h.265 and see if that helps.  
b) Transcode to h.264 which generally does have GPU video support in most recent intel CPUs.  The file size will probably double, however.  

In-GPU codec support really is important to off-load video playback onto the GPU. Then the speed of the CPU really doesn't matter. This is why a raspberry pi v2 can handle 1080p h.264 videos - the GPU does all the work, not the CPU.  On a raspberry pi, hidef mpeg2 video doesn't work well (stutters badly) unless the mpeg2 video drivers are purchased so the GPU can do the work.

h.265 is the next major commercial video codec coming. Think there are [license requirements]("http://blog.streamingmedia.com/2015/07/new-patent-pool-wants-share-of-revenue-from-content-owners.htmlhttp://"), at least in the USA. h.264 doesn't currently require a license for free content.  The old "give them a free taste" trick.

---

### Post by SeijiSensei on 2016-10-25
What player are you using? Give mpv a try if you're not using it already. Get it from here: [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

You might just not have a good enough CPU for H.265.

---

### Post by freeworld4 on 2016-10-26
I think it was cause I had too many things open at once. Now it plays smoothly.

---

