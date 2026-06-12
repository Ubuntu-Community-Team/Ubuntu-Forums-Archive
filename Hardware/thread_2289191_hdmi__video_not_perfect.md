---
title: "hdmi  video not perfect"
date: 2015-08-02
forum: Hardware
---

### Post by spoiler2 on 2015-08-02
Hi everyone,

I have just installed Ubuntu 15.04 on my   HP Pavilion dv3-2350el with hybrid graphics.

the system on laptop is perfect, but when i connect the hdmi cable to my samsung tv i have some problems. (video lags , windows that remains drawn on the monitor , ecc)
audio insted is perfect.

what should i do? maybe change drivers?

here i post the result of lspci -vv command for vga.

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated G
raphics Controller (rev 02) (prog-if 00 [VGA controller])
   Subsystem: Hewlett-Packard Company Device 1405
   Flags: bus master, fast devsel, latency 0, IRQ 28
   Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
   Memory at d0000000 (64-bit, prefetchable) [size=256M]
   I/O ports at 8050 [size=8]
   Expansion ROM at <unassigned> [disabled]
   Capabilities: <access denied>
   Kernel driver in use: i915
```

```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc.  [AMD/ATI] RV710/M92 [Mobility Radeon HD 4350/4550] (prog-if 00 [VGA  controller])
   Subsystem: Hewlett-Packard Company Device 1405
   Flags: bus master, fast devsel, latency 0, IRQ 31
   Memory at c0000000 (32-bit, prefetchable) [size=256M]
   I/O ports at 7000 [size=256]
   Memory at ea400000 (32-bit, non-prefetchable) [size=64K]
   Expansion ROM at ea420000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel driver in use: radeon
```

---

### Post by TheFu on 2015-08-02
Try a different cable and make certain the connections are tight.  Also, remove any HDMI switches for now.
I don't think this is a driver issue. I think it is a hardware problem. If a newer cable doesn't fix it, I'm afraid the issue could be in the HDMI port on either the PC or the monitor side.  Hopefully, the monitor has 2 HDMI ports so you can try the other one?

If you are adventurous, trying a different Desktop Environment, DE, would show if the issue was with the current DE or not. Interested in trying this?

---

### Post by spoiler2 on 2015-08-02
thank you for reply , i forgot to say that using windows ( whth the same pc , same camble , ecc) it works perfectly so probably it's not an hardware issue   ( tell me if i'm wrong) , but i can try with another Desktop environment.

---

### Post by TheFu on 2015-08-02
> **spoiler2 said:**
> thank you for reply , i forgot to say that using windows ( whth the same pc , same camble , ecc) it works perfectly so probably it's not an hardware issue   ( tell me if i'm wrong) , but i can try with another Desktop environment.

I tried to find the specs for that device. Couldn't. All the devices that showed up seem fairly old.  Unity is a heavy DE, so going to a lighter one would make the system performance improve greatly. Most of those "lighter" DEs are a throwback to WinXP-style menus.  xfce4 is popular.  

You have a choice - do you want just the DE or do you want all the little and big applications that come with the entire DE?
For just the DE, install **xfce4** for everything, install **xubuntu-desktop**
[http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/) has details.

For a newer system, KDE is nice, so if your system is actually faster than a Core 2 Cuo, go crazy.

There is a risk with every DE used.  Some of the settings are stored in the same files. Some of these settings used between different DEs can be incompatible. So - either make a backup of all your settings or just create and use a new userid for testing the different DEs.  I've seen this most with gnome-related DEs - so LXDE, XFCE, GNOME3, and unity might cause issues. Usually the issues are minor, but sometimes the DE is completely broke. The answer is to wipe all the settings and start fresh.  Not trying to scare you, but want you to have the facts.

---

### Post by spoiler2 on 2015-08-20
installed xubuntu  but is the same .... any ideas?

---

### Post by SeijiSensei on 2015-08-21
If you can disable the Intel adapter in the system's BIOS, I'd give that a try, then install the proprietary driver (**fglrx**) for your AMD adapter.  These hybrid Intel/AMD or Intel/NVIDIA machines are often a pain to get working properly in Linux.

---

