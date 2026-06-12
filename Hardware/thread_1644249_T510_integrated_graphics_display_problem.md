---
title: "T510 integrated graphics display problem"
date: 2010-12-13
forum: Hardware
---

### Post by mfaulk on 2010-12-13
I'm running 10.10 on a Lenovo T510 with Intel integrated graphics, and I've recently (last few weeks) seen that occasionally on startup, various parts of the screen (gnome panels, desktop wallpaper, window controls, etc) look like a row of pixels has been shifted over and wrapped around the next line. This is a particularly bad screenshot showing this happening to gnome panels, items on the desktop, and the desktop wallpaper:

[IMG]http://dl.dropbox.com/u/2527162/t510_integrated_graphics_display_problem.png[/IMG]

My main questions are: 1) how can I tell if this is a hardware or software problem, and 2) if software, where should I begin to determine the cause?

Some relevant info:

lspci -v contains

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
        Subsystem: Lenovo Device 215a
        Flags: bus master, fast devsel, latency 0, IRQ 47
        Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915
```uname -a gives
```
2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux
```Thanks!
-matt

---

### Post by MacUntu on 2010-12-15
I'd say you would see hardware problems also outside of the OS (during POST, in the BIOS). If that isn't the case, it's more likely a driver issue. If this is an Optimus enabled T510, which setting did you use in the BIOS: Optimus or Integrated? At the moment I'm using Integrated and everything works fine here on Natty Alpha (and I also tested with a Maverick live CD).

---

### Post by mfaulk on 2010-12-15
This T510 does not have the Nvidia Optimus / switchable graphics; it only has the integrated graphics.

I've never seen this problem during post, BIOS, or even the Ubuntu splash screen, so I feel pretty sure its not a hardware problem. However, its always worth checking for hardware problems while the machine is still under warranty!

Anyway, I'm planning to check /var/log/messages and /var/log/Xorg.0.log next time this happens, in case I spot anything useful. Are there other places I should check? I'd like to get enough info that even if I don't find a solution, I could submit a bug report.

Also, I've got the xserver-xorg-video-intel 2:2.12.0-1ubuntu5.1 package installed, which is presumably the driver I'm using.

thanks,
Matt

---

