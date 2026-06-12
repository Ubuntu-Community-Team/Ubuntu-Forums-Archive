---
title: "Can't get Nvidia drivers to work, HP ZBook 15 G4 (Quadro M120), Ubuntu 18.04 Desktop"
date: 2018-05-16
forum: Hardware
---

### Post by abaybektursun on 2018-05-16
[B][SIZE=3]Background
[/SIZE][/B]
I have spent countless hours trying to install **Ubuntu 18.04** on **HP ZBook 15 G4**. I was able to finally install it thanks to this post: [https://ubuntuforums.org/showthread.php?t=2328988](https://ubuntuforums.org/showthread.php?t=2328988)
Solution for me was to run installer with '*acpi=off'* in the grub.

Also, these are the changes I made to my UEFI/BIOS:
[LIST=1]
[*]I unchecked "*Enable MS UEFI CA key*"
[*]Disabled secure boot
[*]Changed graphics from Hybrid to Discrete (Nvidia drivers will fail to install otherwise)
[*]Unchecked "*Runtime Power  Management*"
[/LIST]

**[SIZE=3]Problem[/SIZE]** 

Now, I can't get **Nvidia drivers** to work. Without the drivers everything seems to work fine, however when I install Nvidia drivers (be it manually, or through software center 3rd party, or apt repository) none of the display managers (gdm, lightdm, sddm) will boot. I am also blacklisting nouveau, otherwise I get into this login loop. Long story short, any attempts to install Nvidia drivers results in a black screen during boot (I still can get into terminal though).

I feel like I have tried everything I was able find on forums. I am tired and hopeless, I call upon you oh glorious kernel gods.

Reinstalling, and trying different versions of Ubuntu does not help.

[SIZE=3][B]Additional Info:
[/B][/SIZE]

[LIST]
[*]Driver version I have been trying: **NVIDIA-Linux-x86_64-390.59**
[*]Everything looks good in the '*/var/log/nvidia-installer.log*' after installation.
[*]sudo lshw -C display
[/LIST]
[INDENT=2]Outputs:[/INDENT]
[INDENT=2]  *-display                 [/INDENT]
[INDENT=2]       description: VGA compatible controller[/INDENT]
[INDENT=2]       product: GM107GLM [Quadro M1200 Mobile][/INDENT]
[INDENT=2]       vendor: NVIDIA Corporation[/INDENT]
[INDENT=2]       physical id: 0[/INDENT]
[INDENT=2]       bus info: pci@0000:01:00.0[/INDENT]
[INDENT=2]       version: a2[/INDENT]
[INDENT=2]       width: 64 bits[/INDENT]
[INDENT=2]       clock: 33MHz[/INDENT]
[INDENT=2]       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom[/INDENT]
[INDENT=2]       configuration: driver=nvidia latency=0[/INDENT]
[INDENT=2]       resources: irq:10 memory:e3000000-e3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:5000(size=128) memory:c0000-dffff[/INDENT]
[INDENT=2]**[SIZE=2]However even after successful install of the driver, nvidia-smi outputs "No devices were found".[/SIZE]**[/INDENT]

---

### Post by abaybektursun on 2018-05-17
I was able to get it to work after trial and error. Here is my solution:


**In UEFI:**

Disable MS UEFI CA key
Disable secure boot
Changed graphics from Hybrid to Discrete (Nvidia drivers will fail to install otherwise)
Disable SGX -Intel Software Guard Extension (This might be the root cause of many issues)
Clear Secure Boot keys




I also changed the grub launch of the Ubuntu installer using 'pnpacpi=off'

---

### Post by tkrauthoff on 2018-08-30
You Sir, deserve a medal!

Today I spent 6 hours at work and figured out, which kernel would run with nvidias driver or the niveau one. Your solution works, but I skipepd the pnpacpi part. FYI I run the 4.18.5 kernel.

---

