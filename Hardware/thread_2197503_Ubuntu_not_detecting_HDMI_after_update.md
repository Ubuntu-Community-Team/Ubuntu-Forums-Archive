---
title: "Ubuntu not detecting HDMI after update"
date: 2014-01-04
forum: Hardware
---

### Post by andork on 2014-01-04
[COLOR=#000000][FONT=Arial]I'm running ubuntu and for some reason when I restarted my computer my hdmi stopped being recognized. Whats going on and how do I fix this?
[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Here's my output with lspci -v -s 00:02.0[/FONT][/COLOR]```
[INDENT=2]00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller]) Subsystem: Micro-Star International Co., Ltd. Device 2111 Flags: bus master, fast devsel, latency 0, IRQ 44 Memory at f7800000 (64-bit, non-prefetchable) [size=4M] Memory at e0000000 (64-bit, prefetchable) [size=256M] I/O ports at f000 [size=64] Expansion ROM at [disabled] Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit- Capabilities: [d0] Power Management version 2 Capabilities: [a4] PCI Advanced Features Kernel driver in use: i915
[/INDENT]

```[COLOR=#000000][FONT=Arial]and xrandr output:[/FONT][/COLOR][INDENT]```
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 32767 x 32767 VGA1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 430mm x 270mm 1680x1050 60.0*+ 1280x1024 75.0 60.0
1152x864 75.0
1024x768 75.1 60.0
800x600 75.0 60.3
640x480 75.0 60.0
720x400 70.1
```
HDMI1 disconnected (normal left inverted right x axis y axis) DP1 disconnected (normal left inverted right x axis y axis) VIRTUAL1 disconnected (normal left inverted right x axis y axis)
[/INDENT]
[COLOR=#000000][FONT=Arial]HDMI is not disconnected and should be read. Going to Displays I do not see the second screen. I have seen multiple issue tracking on this but have not managed to solve it yet.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][http://askubuntu.com/questions/345622/hdmi-stopped-working-ubuntu-13-04](http://askubuntu.com/questions/345622/hdmi-stopped-working-ubuntu-13-04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]It seems like a video card problem but I would have suspected that I would have noticed this before not now. Maybe this has to do with the ubuntu update that I made before the restart???[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm adding the specs of my motherboard below. I am using the integrated graphics card.[/FONT][/COLOR]```
[INDENT]description: Desktop Computer product: MS-7758 (To be filled by O.E.M.) vendor: MSI version: 1.0 serial: To be filled by O.E.M. width: 32 bits capabilities: smbios-2.7 dmi-2.7 smp-1.4 smp configuration: boot=normal chassis=desktop cpus=4 family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=00000000-0000-0000-0000-D43D7E921319 *-core description: Motherboard product: Z77A-G43 (MS-7758) vendor: MSI physical id: 0 version: 1.0 serial: To be filled by O.E.M. slot: To be filled by O.E.M. *-firmware description: BIOS vendor: American Megatrends Inc. physical id: 0 version: V2.7 date: 10/24/2012 size: 64KiB capacity: 8128KiB capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
[/INDENT]

```
Thanks in advance.

---

### Post by v-contact-dias on 2014-03-18
Were you able to resolve this, I am having the same problem!

Thanks

---

