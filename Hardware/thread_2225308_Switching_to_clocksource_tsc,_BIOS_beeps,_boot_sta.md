---
title: "Switching to clocksource tsc, BIOS beeps, boot stall"
date: 2014-05-20
forum: Hardware
---

### Post by dannyboy79 on 2014-05-20
The rig I just built is exhibiting some strange inconsistent behavior. All was fine at first when I was running 13.10 but now that I am running 14.04 sometimes it won't resume from suspend and other times it freezes during boot up and I can't access any tty console and I have to hard reboot it. It's an i5-4670k OC'd to 4Ghz on an MSI Z87-G41 PC Mate motherboard with 8GB of 2133Mhz G-Skill Sniper RAM and an EVGA GTX 760 Superclocked Double BIOS card. It sometimes will do some weird beeping as well, repeating beeps and sometimes even a long constant beep. When I view the kern.log I see the following:
```
May 18 15:05:41 saucy-haswell kernel: [    0.000000] tsc: Fast TSC calibration using PIT
May 18 15:05:41 saucy-haswell kernel: [    0.004000] tsc: Detected 3399.988 MHz processor
May 18 15:05:41 saucy-haswell kernel: [    1.434248] tsc: Refined TSC clocksource calibration: 3399.993 MHz
May 18 15:05:41 saucy-haswell kernel: [    2.434484] Switched to clocksource tsc
May 19 06:37:59 saucy-haswell kernel: [    0.008000] tsc: Marking TSC unstable due to check_tsc_sync_source failed
May 19 06:47:34 saucy-haswell kernel: [    0.000000] tsc: Fast TSC calibration using PIT
May 19 06:47:34 saucy-haswell kernel: [    0.004000] tsc: Detected 3399.695 MHz processor
May 19 06:47:34 saucy-haswell kernel: [    1.435037] tsc: Refined TSC clocksource calibration: 3399.996 MHz
May 19 06:47:34 saucy-haswell kernel: [    2.434552] Switched to clocksource tsc
May 20 18:15:19 saucy-haswell kernel: [    0.000000] tsc: Fast TSC calibration using PIT
May 20 18:15:19 saucy-haswell kernel: [    0.004000] tsc: Detected 3400.137 MHz processor
May 20 18:15:19 saucy-haswell kernel: [    1.438985] tsc: Refined TSC clocksource calibration: 3399.998 MHz
May 20 18:15:19 saucy-haswell kernel: [    2.438473] Switched to clocksource tsc
May 20 18:17:17 saucy-haswell kernel: [    0.000000] tsc: Fast TSC calibration using PIT
May 20 18:17:17 saucy-haswell kernel: [    0.004000] tsc: Detected 3400.007 MHz processor
May 20 18:17:17 saucy-haswell kernel: [    1.434520] tsc: Refined TSC clocksource calibration: 3399.997 MHz
May 20 18:17:17 saucy-haswell kernel: [    2.434068] Switched to clocksource tsc

```
I also notice errors about my PCIe slots not having capabilities to go to sleep. I don't have any special boot parameters that I am aware of. here they are:
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX="vga=0x0369"
```

Any help would be appreciated

---

