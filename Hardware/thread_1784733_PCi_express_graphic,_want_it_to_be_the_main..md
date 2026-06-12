---
title: "PCi express graphic, want it to be the main."
date: 2011-06-17
forum: Hardware
---

### Post by harberst on 2011-06-17
As you likely guessed from the title I've recently added a PCI-e graphics card and want to make it the main graphics card, but I can't seem to use it at all in Ubuntu (11.04). It works fine in windows (vista) so it's not a hardware issue, which means it's either software (possible) or user (likely).  According to Nvidia X Server Settings I"m using driver 173.14.30 (trying to update results in a blank screen upon restart). 

[CODE ] sudo lshw -C display
*-display               
       description: VGA compatible controller
       product: C77 [GeForce 8200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:21 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:bc00(size=128) memory:e0000000-e001ffff
  *-display
       description: VGA compatible controller
       product: G98 [GeForce 8400GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f9000000-f9ffffff memory:b0000000-bfffffff memory:ce000000-cfffffff ioport:ac00(size=128) memory:c0000000-c007ffff
  [/CODE]

Here are the display results from the terminal. Any help would be appreciated.

---

### Post by fballem on 2011-06-17
Not sure if this is true for your system, but on mine, there is a setting in BIOS that determines which graphics card is used. When your machine first boots, you will need to press a key to enter the BIOS setup screens (on my system it's the Delete key, but I have also seen F12). Watch the bootup sequence carefully to determine when you need to press the key. If Ubuntu starts, then you have missed it.

Hope this helps,

---

### Post by Yellow Pasque on 2011-06-17
If possible, completely disable the IGP in the BIOS to save energy.

---

### Post by harberst on 2011-06-17
I managed to find the setting in the BIOS no problem, but I seem to encounter a problem with Ubuntu's start-up, I could be wrong but I think 15 minutes of black screen is a problem yes? I'm going to try booting windows to make sure it's a Ubuntu specific issue.

It does do the check list/code thing pre-ubuntu start, but it seems to freeze up when it goes blank. Prior to changing the graphic card (I changed nothing else, I know better than to muck about with the BIOS without clear instruction)I'd only have about 3 minutes of black screen before the Ubuntu logo popped up tops. The code flashes by to quickly for me to read it. I'll post back with more information in a couple of hours.

---

### Post by harberst on 2011-06-18
Windows boots fine (resolution's off, but that can be fixed later) which means it's something with Ubuntu.  I can boot into failsafegraphics mode without a problem.  I still don't know what's causing normal Ubuntu to not load though. Could it be a memory thing? I seem to recall reading something about having to give more memory to some function or another to get the nvidia drivers to not cause the system to choke.

---

### Post by harberst on 2011-06-18
All right, turns out the old nvidia driver was still "installed" (nvidia said it wasn't and ubuntu said it was "activated but not in use" so go figure) which was (of course!) causing a conflict.

---

