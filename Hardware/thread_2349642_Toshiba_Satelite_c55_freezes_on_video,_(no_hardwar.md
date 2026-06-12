---
title: "Toshiba Satelite c55 freezes on video, (no hardware accelleration?)"
date: 2017-01-16
forum: Hardware
---

### Post by trip812 on 2017-01-16
I have a Toshiba Satelite C55 laptop with Ubuntu 16.04 full-install. I've been having issues with video. I thought it was solely Flash at first but Youtube HTML5 does the same thing after a few minutes (grey screen, lags terribly until stopping). And it's not only video, anything that seems to be graphics/cpu intsenive seems to lock up really bad. I know from running Windows 10 and from the specs alone that this machine is capable of running HD video (an interesting note is that before I did a full install everything seemed to be running perfectly from the Live CD, I thought maybe that was because from the PCs BIOS I switched to legacyBIOS instead of UEFI which I read was a possible workaround). I've read a lot on these forums trying to find a solution but nothing has worked, this is the 3rd fresh install I've tried. On previous installations I've installed the Intell propietary graphics driver, Mesa utilities, reinstalled X-server, and frankly tried to run a lot of terminal commands I saw on the forum the that I wasn't familiar with. None seemed to make a difference. Is the problem Distribution specific, i heard 16.04 doesen't support fglrx (does that even pertain to my machine?), is the hardware just incompatable for whatever reason? PLEAE HELP if you can I really Love Ubuntu for so many reasons, I'm learning to code and Loving learning  some basic system administration. I desperately don't wanna go back to Windows.

(relevant specs from $ lshw)
```
*-cpu
          product: Intel(R) Core(TM) i3-3120M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2345MHz
          capacity: 2500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx f16c lahf_lm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm arat pln pts cpufreq
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ivb_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:26 memory:c8000000-c83fffff memory:c0000000-c7ffffff ioport:3000(size=64)
```

---

### Post by QIII on 2017-01-16
Hello!

There is no reason to put things such as "Please help!" in your thread titles.  We get that already.  :)

But do please enclose all terminal commands and results in code tags.  That will preserve formatting and create a scrollable box.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

Best wishes!

---

### Post by trip812 on 2017-01-16
Sorry about the formatting, new here. Is this posted in the right location of the forums? I know similar topics have been posted but I can't remedy this situation and I'm desperate to.

---

### Post by mörgæs on 2017-01-17
You have a powerful computer, so normally it would not be necessary. Still it would be interesting to see how it behaves using a fresh install of Lubuntu 16.10. 

Fglrx is only relevant for AMD graphics.

---

