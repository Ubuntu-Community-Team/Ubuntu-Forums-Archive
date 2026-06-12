---
title: "Computer restarting automatically"
date: 2009-06-19
forum: Hardware
---

### Post by banskt on 2009-06-19
Hi All,

I have a weird problem.
I have been using Ubuntu 8.10 on my desktop. For the last couple of days, my computer is restarting automatically.
Initially it was occuring when left idle, but now it is rebooting every now and then. It has been very annoying..

I dont think it is a heating problem, because the temperature is under control. i checked /var/log/messages and also /var/log/syslog...

The /var/log/messages read:

Jun 20 00:18:18 bagchi62 kernel: [   20.895028] ACPI: Error installing bay notify handler
Jun 20 00:18:18 bagchi62 kernel: [   20.974658] ACPI: WMI: Mapper loaded
Jun 20 00:18:18 bagchi62 kernel: [   21.803379] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jun 20 00:18:20 bagchi62 kernel: [   24.058946] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jun 20 00:18:20 bagchi62 kernel: [   24.058953] apm: disabled - APM is not SMP safe.
Jun 20 00:18:20 bagchi62 kernel: [   24.228215] ppdev: user-space parallel port driver
Jun 20 00:18:26 bagchi62 kernel: [   29.621192] [drm] Initialized drm 1.1.0 20060810
Jun 20 00:18:26 bagchi62 kernel: [   29.638429] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 20 00:18:26 bagchi62 kernel: [   29.639705] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jun 20 00:18:37 bagchi62 pulseaudio[5573]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jun 20 00:18:37 bagchi62 pulseaudio[5575]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jun 20 00:18:37 bagchi62 pulseaudio[5575]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

---

### Post by dheerajmk on 2009-07-24
Hey even I am facing almost the same problem on Jaunty , the computer suddenly restarts... 
Everything is stable otherwise and there are no compatibility issues. ALl drivers are installed and up to date... 
And there is no over heating as all cooling devices are working fine.
Can someone please help me also with regard to this issue
Cheers
Dee

---

### Post by cariboo on 2009-07-24
It sounds like a hardware problem, if you have anoither power supply, swap them.

---

### Post by philcamlin on 2009-07-24
power supply issue?

i had that issue last year :(

---

### Post by ZaHACKieL on 2009-07-24
Did u get it fixed? Tried the power supply solution? It may also be a motherboard issue. I remember having that problem years ago and I also thought about the RAM. Run some memory tests to see if your RAM is working fine

---

