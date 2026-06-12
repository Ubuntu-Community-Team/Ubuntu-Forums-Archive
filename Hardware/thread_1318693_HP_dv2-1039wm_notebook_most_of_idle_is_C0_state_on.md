---
title: "HP dv2-1039wm notebook: most of idle is C0 state only"
date: 2009-11-07
forum: Hardware
---

### Post by swaaye on 2009-11-07
I have a 12" HP DV2-1039WM notebook. It has a 690M chipset with SB600 southbridge, AMD Neo (Athlon 64) 1.6GHz CPU, Radeon 3450, and 4GB DDR2. I am trying to get the CPU C2/3 power states functional but have no idea how to really. I've been looking into powertop for info.

On Windows XP and 7, the CPU idles in C3 power state. This saves a lot of power. In Ubuntu 9.10, it spends the majority of its idle time in C1.

I've been doing a lot of web searching about this but I keep coming across conflicting info so I decided to just post and ask.

```

dv2@dv2note:~$ cat /proc/acpi/processor/CPU0/power
active state:            C0
max_cstate:              C8
maximum allowed latency: 2000000000 usec
states:
    C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00153966] duration[00000000000000000000]
    C2:                  type[C2] promotion[--] demotion[--] latency[018] usage[00373170] duration[00000000000007700926]
    C3:                  type[C3] promotion[--] demotion[--] latency[083] usage[00967762] duration[00000000000053960155]

```

```

dv2@dv2note:/dev$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 127
model name	: AMD Athlon(tm) Neo Processor MV-40
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1595.91
clflush size	: 64
power management: ts fid vid ttp tm stc 100mhzsteps

```
```

     PowerTOP version 1.11      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 7.7%)         1.60 Ghz     0.0%
polling           0.0ms ( 0.0%)          800 Mhz   100.0%
C1                7.4ms (90.9%)
C2                0.0ms ( 0.2%)
C3                0.0ms ( 1.2%)

Wakeups-from-idle per second : 1144.0   interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  25.7% ( 59.8)       <interrupt> : fglrx[0]@PCI:1:0:0 
  20.9% ( 48.6)       <interrupt> : ohci_hcd:usb4, ohci_hcd:usb6, eth2 
  11.9% ( 27.6)     <kernel core> : add_timer (wl_timer) 
   8.9% ( 20.6)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   8.3% ( 19.4)     <kernel core> : hrtimer_start (tick_sched_timer) 
   6.4% ( 14.8)       <interrupt> : ehci_hcd:usb1, HDA Intel 
   6.0% ( 14.0)   USB device 1-10 : USB2.0-CRW (Generic) 
   5.9% ( 13.8)       <interrupt> : acpi 
   2.1% (  4.8)         syndaemon : hrtimer_start_range_ns (hrtimer_wakeup)
   1.0% (  2.4)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup)
   0.7% (  1.6)       <interrupt> : ahci
   0.5% (  1.2)     <kernel core> : timer_action (ehci_watchdog)
   0.3% (  0.8)    cpufreq-applet : hrtimer_start_range_ns (hrtimer_wakeup)
   0.3% (  0.6)     <kernel core> : neigh_periodic_timer (neigh_periodic_timer)
   0.2% (  0.4)              Xorg : hrtimer_start (it_real_fn)
   0.2% (  0.4)          nautilus : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  0.2)       <interrupt> : PS/2 keyboard/mouse/touchpad
   0.1% (  0.2)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  0.2)           pdflush : wb_kupdate (wb_timer_fn)
   0.1% (  0.2)   update-notifier : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  0.2)          gconfd-2 : add_timer (commit_timeout)
   0.1% (  0.2)   devkit-disks-da : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  0.2)   hald-addon-stor : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  0.2)       gnome-panel : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  0.2)              hald : hrtimer_start_range_ns (hrtimer_wakeup)


Suggestion: Enable SATA ALPM link power management via:
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.
 Q - Quit   R - Refresh   S - SATA Link Power Management 
```

---

### Post by peculiar penguin on 2009-11-08
The content of /proc/acpi/processor/CPU0/power actually looks ok, or am I reading it wrong?

The powertop output is weird in that it suggests most of the time is spent in C1, and there are more total wakeups (1144) than suggested by the "top causes for wakeups", which add up to maybe 240.

My laptop uses a similar ATI chipset and the symptoms are worse - more than 60% of idle time stuck in C0, around 50,000 (!) total wakeups... in my case the solution is to use the "noapic" kernel parameter. Adding it to the kernel line in /boot/grub/menu.lst (Jaunty) resp. GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub (Karmic, needs a "sudo update-grub2" afterwards) mostly fixed it for me. 

Worth a try since it's free and shouldn't break anything (assuming you know how to use a text editor). You may have to add "nolapic" as well as noapic... actually there's loads of [kernel parameters]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt") that may or may not do something for you. Figuring out the right combination to make things work on wonky hardware is the hard part :/

---

### Post by swaaye on 2009-11-08
here are the results from adding 'noapic' and 'nolapic' to grub boot. Quite the positive result. :)
```

     PowerTOP version 1.11      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (11.4%)         1.60 Ghz     0.0%
polling           0.0ms ( 0.0%)          800 Mhz   100.0%
C1                0.0ms ( 0.0%)
C2                0.1ms ( 0.0%)
C3                6.3ms (88.6%)

Wakeups-from-idle per second : 143.2    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  32.8% ( 90.0)       <interrupt> : ahci, ohci_hcd:usb2, ohci_hcd:usb4, ohci_hcd
  19.6% ( 53.8)       <interrupt> :  
  14.4% ( 39.6)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   6.6% ( 18.0)       <interrupt> : ehci_hcd:usb1, ohci_hcd:usb3, ohci_hcd:usb5,
   5.8% ( 16.0)   USB device 1-10 : USB2.0-CRW (Generic) 
   5.5% ( 15.2)     <kernel core> : add_timer (wl_timer) 
   5.0% ( 13.6)       <interrupt> : acpi 
   4.4% ( 12.2)     <kernel core> : hrtimer_start (tick_sched_timer) 
   1.7% (  4.8)         syndaemon : hrtimer_start_range_ns (hrtimer_wakeup)
   1.1% (  3.0)     <kernel core> : timer_action (ehci_watchdog)
   0.8% (  2.2)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup)
   0.4% (  1.0)              Xorg : add_timer (wl_timer)
   0.3% (  0.8)    cpufreq-applet : hrtimer_start_range_ns (hrtimer_wakeup)
   0.3% (  0.8)        atieventsd : hrtimer_start_range_ns (hrtimer_wakeup)
   0.2% (  0.6)   hald-addon-stor : hrtimer_start_range_ns (hrtimer_wakeup)
   0.2% (  0.6)     <kernel core> : neigh_periodic_timer (neigh_periodic_timer)
   0.1% (  0.4)    NetworkManager : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  0.4)   update-notifier : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  0.2)       <interrupt> : PS/2 keyboard/mouse/touchpad
   0.1% (  0.2)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup)

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

 Q - Quit   R - Refresh   U - Enable USB suspend 
```

---

