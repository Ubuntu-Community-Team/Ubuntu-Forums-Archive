---
title: "External display changes mouse pointer to X and traps pointer"
date: 2011-10-02
forum: Hardware
---

### Post by finny388 on 2011-10-02
**Update 2:**
I got it to work as "Separate X screen" with the laptop disabled.

I just have 2 questions:
[INDENT]How do I know if the nVidia chipset is being used?
How do I install a *.run file from nVidia?[/INDENT]

I also found out what version it is:
```
$ cat /var/log/Xorg.0.log
[    29.186] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
```

On the nVidia website info on the installed driver is:
[INDENT][B][SIZE="1"]	Linux Display Driver - x86
	Version: 270.41.19
	Operating System: Linux x86
	Release Date: May 20, 2011[/SIZE][/B][/INDENT]

Info from nVidia on the latest:
[INDENT][SIZE="1"][B]	Linux Display Driver - x86
	Version: 275.28 Certified
	Operating System: Linux
	Release Date: 2011.09.07[/B][/SIZE][/INDENT]

Perhaps the latest driver would work best.

any help much appreciated.

**Update 1:**
Under System Settings/Hardware/Additional Drivers there is the nVidia driver (only other is Broadcom) "NVIDIA accelerated graphics driver (version current) [Recommended]"

but at the bottom it says "This driver is activated but not currently in use."

I ran the lshw as above again and it was the same. saying driver=nvidia.

So I don't know if it is or isn't using my ion graphics. I want to use the ion graphics full-time.

**Original:**
I am trying to connect my Asus eee 1015PN to an external display.

I have tried hdmi and vga on both an LG LCD monitor and my Samsung LCD TV.

Every time, it looks like an extended desktop (the wall paper is on the ext disp but with no panels)

Everything will work until the second the mouse pointer exits the laptop display to go on to the ext display. Then it turns into a bold 'X' mouse pointer and will not travel outside of that display anymore.

I'm forced to reboot.

I've tried configuring the nVidia drivers as described in [COLOR="Blue"][ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu:Natty#Configure_Dual_Monitors_with_nVidia").
[/COLOR]
Here are some outputs about my system:
```
$ cat /etc/issue
Ubuntu 11.04 \n \l
``````
$ uname -a
Linux 1015PN 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux
``````
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: GT218 [ION]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff memory:f2000000-f3ffffff ioport:ec00(size=128) memory:fbf00000-fbf7ffff
```

---

