---
title: "Problems with Dell 5575 AMD/Radeon"
date: 2021-10-22
forum: Hardware
---

### Post by jdhamric on 2021-10-22
I had a HP laptop whose display died. I had available a Dell Inspiron 5575 with an AMD Ryzen 5 2500 CPU & integrated Radeon Raven Ridge Vega 8 GPU. I swapped out the hard drives & installed an 8GB memory DIMM from the HP (yes, it's compatible with the Dell) in the empty memory slot. I made sure the Dell could boot from the EFI GRUB entry. The laptop booted up, got a "DELL" splash & then the GRUB menu & I chose "UBUNTU" (kernel 5.4.0.88; since updated to 5.4.0.89). Got the "DELL" splash again for a short time, then a black screen. I re-booted to the recovery version. Everything booted OK. But as I since discovered, the AMD graphics module does not load. Googling seems to indicate many people have had some sort of problem with this set-up. I have tried "nomodeset" in the GRUB config; but of course that doesn't solve the problem. Adding "amdgpu.dc=0 or 1" does not help. Several other options tried do not make a difference.  I installed the 20.04-HWE kernels ( 5.11.0.37; updated to 5.11.0.42), but that does not solve anything. Enclosed below is some relevent (I hope) info:

```
$ uname -sr
Linux 5.11.0-37-generic
----------------------------------
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#Original setting below
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

#Following line original existing before use of Dell
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap"
# added idle=nomwait, iommu=soft; removed nomodeset; tried video=efifb(:off) did not work
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash idle=nomwait iommu=soft video=uvesafb:mode_option=1920x1080-24, mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#Uncommented/changed following line 10/20/2021
GRUB_GFXMODE=1280x720-32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
----------------------------------------------------
$ sudo lshw -c video

*-display UNCLAIMED       
       description: VGA compatible controller
       product: Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:e0000000-e01fffff ioport:1000(size=256) memory:e0700000-e077ffff memory:c0000-dffff
  ---------------------------------------------------------     
$ inxi -G

Graphics:
  Device-1: AMD Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] 
  driver: N/A 
  Display: x11 server: X.Org 1.20.11 driver: ati,fbdev 
  unloaded: amdgpu,modesetting,radeon,vesa resolution: 1920x1080~77Hz 
  OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.0.3
  -----------------------------------------------------------------------------------------
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal

$ journalctl -b | egrep -i 'radeon|amdgpu' | egrep -i 'error|fail|kernel'

Oct 16 17:18:21 Pern kernel: smpboot: CPU0: AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx (family: 0x17, model: 0x11, stepping: 0x0)
Oct 16 17:18:34 Pern kernel: [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
Oct 16 17:20:00 Pern /usr/lib/gdm3/gdm-x-session[4546]:         All GPUs supported by the amdgpu kernel driver
Oct 16 17:20:00 Pern /usr/lib/gdm3/gdm-x-session[4546]:         All GPUs supported by the amdgpu kernel driver
Oct 16 17:20:43 Pern /usr/lib/gdm3/gdm-x-session[10105]:         All GPUs supported by the amdgpu kernel driver
Oct 16 17:20:43 Pern /usr/lib/gdm3/gdm-x-session[10105]:         All GPUs supported by the amdgpu kernel driver

created /etc/mkinitcpio.conf & added MODULES=amdgpu to it; did not seem to help
```

Randomly I can boot with the amdgpu modules active. I get either the DELL logo with the spinning Ubuntu logo below it or the purple screen with the blinking dots. In addition the computer will freeze if left unused for some period of time & sometimes a hard reboot is required (sometimes CTL-ALT-BACKSPACE works). I have turned off all screen blanking, drive spin-down & suspension options.

Hoping someone out there can help me to get this to boot normally.

TIA.

---

### Post by dougdeep2 on 2021-10-28
The inxi -G lines about unloading amdgpu and radeon and others with the renderer being LLVMPIPE susggests that something is breaking the others during startup.  When I had a similar problem with amdgpu, I found a post on the Linux Mint forums that suggested looking in the dmesg log file that is recorded for every boot.  The file is var/log/dmesg and can be fairly long but you should be able to find several lines related to amdgpu or radeon and your graphic card.  In my case, the dmesg file contained a line that said amdgpu could not a firmware file (should have been in lib/firmware/amdgpu but wasn’t).  Without the file, amdgpu quit and Ubuntu started with LLVMPIPE instead.

 
 
 With AMD graphics, radeon is supposed to be the fallback for amdgpu.  If you find amdgpu is breaking, see if radeon is as well.

---

### Post by jdhamric on 2021-10-28
Thanks @dougdeep2!. Ive checked that out & find the following (not a complete list):
  -kernel: [drm] amdgpu kernel modesetting enabled.
  -kernel: amdgpu: Ignoring ACPI CRAT on non-APU system
  -kernel: fb0: switching to amdgpudrmfb from EFI VGA
  -kernel: amdgpu 0000:03:00.0: vgaarb: deactivate vga console
  -kernel: amdgpu 0000:03:00.0: amdgpu: Trusted Memory Zone (TMZ) feature disabled as experimental (default)
  -kernel: amdgpu 0000:03:00.0: amdgpu: Fetched VBIOS from ROM BAR

This doesn't mean much to me, but seems to indicate that the amdgpu driver loads. My situation has became a bit more stable since I found instructions for adding amdgpu drivers from a PPA site. Booting can still drop me to a black screen, after the DELL logo, but happens less frequently. And the system will still freeze after sitting for a while.

---

### Post by jdhamric on 2021-11-03
So some progress made. After trying a slew of grub parameters, I removed "quiet" to view the boot process. It got stuck on "Failed to start Show Plymouth Boot Screen". I tried reinstalling plymouth & re-configuring it to ensure choosing the bgrt option, but the boot process was still a crap shoot. Just tried it without "quiet splash" & it sailed straight through to the log-in screen. So it seems something in plymouth is unstable, but so far I haven't been able to figure out what. 

If anyone knows, I'm all ears.

---

### Post by Yellow Pasque on 2021-11-04
If it was me, I'd remove plymouth and call it a day. I don't even have it installed on my system (Debian sid). Pretty boot screens are nice, but considering how fast most systems boot nowadays, they're not worth the fuss if they don't work right.

---

### Post by jdhamric on 2021-11-07
> **Yellow Pasque said:**
> If it was me, I'd remove plymouth and call it a day. I don't even have it installed on my system (Debian sid). Pretty boot screens are nice, but considering how fast most systems boot nowadays, they're not worth the fuss if they don't work right.

I'm rapidly approaching that point; either removing "splash" or changing it to "nosplash" in GRUB. I know I did something out of the ordinary when I swapped in my HDD to this system. But I would think the OS would be "smart" enough to probe the system & load the right modules. This chipset has been around long enough to fix any problems. Maybe I have something in some file that's botching things up, but I can't figure out what it might be. The strange thing is that it continues to work sometimes; I get either the spinning Ubuntu logo below the OEM logo or I get the flashing dots. But since the default is the bgrt I don't get how it goes to the dots. Most of the time it just freezes & I have to continually reboot until it works.

---

### Post by jdhamric on 2021-11-21
So maybe some baby steps forward even if booting is still an ifffy issue. I removed "quiet splash" from grub to further follow the boot sequence. It now stops after "Load/Save RF Kill Switch Status" messages or a backlight message or bluetooth (hc1?) message.

Relevent syslog messages after a successful boot:
```

Nov 20 14:52:24 Pern kernel: [    0.277108] HugeTLB registered 1.00 GiB page size, pre-allocated 0 pages
Nov 20 14:52:24 Pern systemd[1]: Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
Nov 20 14:52:24 Pern kernel: [    0.277108] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
Nov 20 14:52:24 Pern kernel: [    0.277108] fbcon: Taking over console
Nov 20 14:52:24 Pern kernel: [    0.277108] ACPI: Added _OSI(Module Device)
Nov 20 14:52:24 Pern kernel: [    0.277108] ACPI: Added _OSI(Processor Device)
Nov 20 14:52:24 Pern kernel: [    0.277108] ACPI: Added _OSI(3.0 _SCP Extensions)
Nov 20 14:52:24 Pern kernel: [    0.277108] ACPI: Added _OSI(Processor Aggregator Device)
Nov 20 14:52:24 Pern kernel: [    0.277108] ACPI: Added _OSI(Linux-Dell-Video)
Nov 20 14:52:24 Pern kernel: [    0.277108] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
Nov 20 14:52:24 Pern systemd[1]: Starting Load/Save RF Kill Switch Status...
Nov 20 14:52:24 Pern kernel: [    0.277108] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
Nov 20 14:52:24 Pern systemd-udevd[496]: Using default interface naming scheme 'v245'.
Nov 20 14:52:24 Pern kernel: [    0.281704] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
Nov 20 14:52:24 Pern kernel: [    0.288607] ACPI: 8 ACPI AML tables successfully acquired and loaded
Nov 20 14:52:24 Pern kernel: [    0.291252] ACPI: EC: EC started
Nov 20 14:52:24 Pern kernel: [    0.291255] ACPI: EC: interrupt blocked
Nov 20 14:52:24 Pern kernel: [    0.291730] ACPI: EC: EC_CMD/EC_SC=0x66, EC_DATA=0x62
Nov 20 14:52:24 Pern kernel: [    0.291734] ACPI: \_SB_.PCI0.LPC0.EC0_: Boot DSDT EC used to handle transactions
Nov 20 14:52:24 Pern kernel: [    0.291737] ACPI: Interpreter enabled
Nov 20 14:52:24 Pern systemd-udevd[496]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.
Nov 20 14:52:24 Pern kernel: [    0.291751] ACPI: (supports S0 S3 S4 S5)
Nov 20 14:52:24 Pern kernel: [    0.291753] ACPI: Using IOAPIC for interrupt routing
Nov 20 14:52:24 Pern kernel: [    0.292068] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov 20 14:52:24 Pern kernel: [    0.292287] ACPI: Enabled 2 GPEs in block 00 to 1F
Nov 20 14:52:24 Pern kernel: [    0.294284] ACPI: Power Resource [P0ST] (on)
Nov 20 14:52:24 Pern kernel: [    0.294313] ACPI: Power Resource [P3ST] (on)
Nov 20 14:52:24 Pern kernel: [    0.297461] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Nov 20 14:52:24 Pern kernel: [    0.297469] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI HPX-Type3]
Nov 20 14:52:24 Pern kernel: [    0.297624] acpi PNP0A08:00: _OSC: platform does not support [SHPCHotplug LTR]
Nov 20 14:52:24 Pern kernel: [    0.297771] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Nov 20 14:52:24 Pern kernel: [    0.297784] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
Nov 20 14:52:24 Pern systemd-udevd[497]: Using default interface naming scheme 'v245'.
Nov 20 14:52:24 Pern kernel: [    0.297890] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff window] (conflicts with Video ROM [mem 0x000c0000-0x000cd3ff])
Nov 20 14:52:24 Pern kernel: [    0.298014] PCI host bridge to bus 0000:00
Nov 20 14:52:24 Pern kernel: [    0.298018] pci_bus 0000:00: root bus resource [bus 00-ff]
Nov 20 14:52:24 Pern kernel: [    0.298021] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Nov 20 14:52:24 Pern kernel: [    0.298023] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Nov 20 14:52:24 Pern kernel: [    0.298026] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000cbfff window]
Nov 20 14:52:24 Pern kernel: [    0.298028] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Nov 20 14:52:24 Pern kernel: [    0.298031] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000effff window]
Nov 20 14:52:24 Pern kernel: [    0.298033] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xf7ffffff window]
Nov 20 14:52:24 Pern systemd-udevd[497]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.
Nov 20 14:52:24 Pern kernel: [    0.298036] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff window]
Nov 20 14:52:24 Pern kernel: [    0.298053] pci 0000:00:00.0: [1022:15d0] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.298178] pci 0000:00:00.2: [1022:15d1] type 00 class 0x080600
Nov 20 14:52:24 Pern kernel: [    0.298324] pci 0000:00:01.0: [1022:1452] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.298450] pci 0000:00:01.6: [1022:15d3] type 01 class 0x060400
Nov 20 14:52:24 Pern kernel: [    0.298585] pci 0000:00:01.6: PME# supported from D0 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.298738] pci 0000:00:01.7: [1022:15d3] type 01 class 0x060400
Nov 20 14:52:24 Pern kernel: [    0.298871] pci 0000:00:01.7: PME# supported from D0 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.299033] pci 0000:00:08.0: [1022:1452] type 00 class 0x060000
Nov 20 14:52:24 Pern systemd[1]: Created slice system-systemd\x2dbacklight.slice.
Nov 20 14:52:24 Pern kernel: [    0.299147] pci 0000:00:08.1: [1022:15db] type 01 class 0x060400
Nov 20 14:52:24 Pern kernel: [    0.299199] pci 0000:00:08.1: enabling Extended Tags
Nov 20 14:52:24 Pern kernel: [    0.299260] pci 0000:00:08.1: PME# supported from D0 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.299366] pci 0000:00:08.2: [1022:15dc] type 01 class 0x060400
Nov 20 14:52:24 Pern kernel: [    0.299419] pci 0000:00:08.2: enabling Extended Tags
Nov 20 14:52:24 Pern kernel: [    0.299477] pci 0000:00:08.2: PME# supported from D0 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.299607] pci 0000:00:14.0: [1022:790b] type 00 class 0x0c0500
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in Show Plymouth Boot Screen being skipped.
Nov 20 14:52:24 Pern kernel: [    0.299790] pci 0000:00:14.3: [1022:790e] type 00 class 0x060100
Nov 20 14:52:24 Pern kernel: [    0.299977] pci 0000:00:18.0: [1022:15e8] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.300024] pci 0000:00:18.1: [1022:15e9] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.300084] pci 0000:00:18.2: [1022:15ea] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.300129] pci 0000:00:18.3: [1022:15eb] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.300174] pci 0000:00:18.4: [1022:15ec] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.300220] pci 0000:00:18.5: [1022:15ed] type 00 class 0x060000
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in Forward Password Requests to Plymouth Directory Watch being skipped.
Nov 20 14:52:24 Pern kernel: [    0.300265] pci 0000:00:18.6: [1022:15ee] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.300312] pci 0000:00:18.7: [1022:15ef] type 00 class 0x060000
Nov 20 14:52:24 Pern kernel: [    0.300448] pci 0000:01:00.0: [10ec:8136] type 00 class 0x020000
Nov 20 14:52:24 Pern kernel: [    0.300476] pci 0000:01:00.0: reg 0x10: [io  0x2000-0x20ff]
Nov 20 14:52:24 Pern kernel: [    0.300513] pci 0000:01:00.0: reg 0x18: [mem 0xe0900000-0xe0900fff 64bit]
Nov 20 14:52:24 Pern kernel: [    0.300537] pci 0000:01:00.0: reg 0x20: [mem 0xe0200000-0xe0203fff 64bit pref]
Nov 20 14:52:24 Pern kernel: [    0.300680] pci 0000:01:00.0: supports D1 D2
Nov 20 14:52:24 Pern kernel: [    0.300682] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.300839] pci 0000:00:01.6: PCI bridge to [bus 01]
Nov 20 14:52:24 Pern systemd[1]: Starting Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight...
Nov 20 14:52:24 Pern kernel: [    0.300847] pci 0000:00:01.6:   bridge window [io  0x2000-0x2fff]
Nov 20 14:52:24 Pern kernel: [    0.300851] pci 0000:00:01.6:   bridge window [mem 0xe0900000-0xe09fffff]
Nov 20 14:52:24 Pern kernel: [    0.300858] pci 0000:00:01.6:   bridge window [mem 0xe0200000-0xe02fffff 64bit pref]
Nov 20 14:52:24 Pern kernel: [    0.300976] pci 0000:02:00.0: [8086:24fd] type 00 class 0x028000
Nov 20 14:52:24 Pern kernel: [    0.301055] pci 0000:02:00.0: reg 0x10: [mem 0xe0800000-0xe0801fff 64bit]
Nov 20 14:52:24 Pern kernel: [    0.301397] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.302008] pci 0000:00:01.7: PCI bridge to [bus 02]
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in File System Check on Root Device being skipped.
Nov 20 14:52:24 Pern kernel: [    0.302018] pci 0000:00:01.7:   bridge window [mem 0xe0800000-0xe08fffff]
Nov 20 14:52:24 Pern kernel: [    0.302141] pci 0000:03:00.0: [1002:15dd] type 00 class 0x030000
Nov 20 14:52:24 Pern kernel: [    0.302170] pci 0000:03:00.0: reg 0x10: [mem 0xd0000000-0xdfffffff 64bit pref]
Nov 20 14:52:24 Pern kernel: [    0.302189] pci 0000:03:00.0: reg 0x18: [mem 0xe0000000-0xe01fffff 64bit pref]
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in Rebuild Hardware Database being skipped.
Nov 20 14:52:24 Pern kernel: [    0.302202] pci 0000:03:00.0: reg 0x20: [io  0x1000-0x10ff]
Nov 20 14:52:24 Pern kernel: [    0.302215] pci 0000:03:00.0: reg 0x24: [mem 0xe0700000-0xe077ffff]
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in Platform Persistent Storage Archival being skipped.
Nov 20 14:52:24 Pern systemd[1]: Started Load/Save RF Kill Switch Status.
Nov 20 14:52:24 Pern systemd[1]: Finished Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight.
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in Show Plymouth Boot Screen being skipped.
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in Forward Password Requests to Plymouth Directory Watch being skipped.
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in File System Check on Root Device being skipped.
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in Rebuild Hardware Database being skipped.
Nov 20 14:52:24 Pern systemd[1]: Condition check resulted in Platform Persistent Storage Archival being skipped.
Nov 20 14:52:24 Pern systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:acpi_video0...
Nov 20 14:52:24 Pern systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:amdgpu_bl0...
Nov 20 14:52:24 Pern systemd-backlight[744]: Failed to get backlight or LED device 'backlight:acpi_video0': No such device
Nov 20 14:52:24 Pern systemd[1]: systemd-backlight@backlight:acpi_video0.service: Main process exited, code=exited, status=1/FAILURE
Nov 20 14:52:24 Pern kernel: [    0.302237] pci 0000:03:00.0: enabling Extended Tags
Nov 20 14:52:24 Pern systemd[1]: systemd-backlight@backlight:acpi_video0.service: Failed with result 'exit-code'.
Nov 20 14:52:24 Pern kernel: [    0.302261] pci 0000:03:00.0: BAR 0: assigned to efifb
Nov 20 14:52:24 Pern kernel: [    0.302358] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.302528] pci 0000:03:00.1: [1002:15de] type 00 class 0x040300
Nov 20 14:52:24 Pern kernel: [    0.302550] pci 0000:03:00.1: reg 0x10: [mem 0xe0788000-0xe078bfff]
Nov 20 14:52:24 Pern kernel: [    0.302623] pci 0000:03:00.1: enabling Extended Tags
Nov 20 14:52:24 Pern kernel: [    0.302693] pci 0000:03:00.1: PME# supported from D1 D2 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.302767] pci 0000:03:00.2: [1022:15df] type 00 class 0x108000
Nov 20 14:52:24 Pern systemd[1]: Failed to start Load/Save Screen Backlight Brightness of backlight:acpi_video0.
Nov 20 14:52:24 Pern kernel: [    0.302810] pci 0000:03:00.2: reg 0x18: [mem 0xe0600000-0xe06fffff]
Nov 20 14:52:24 Pern kernel: [    0.302843] pci 0000:03:00.2: reg 0x24: [mem 0xe078c000-0xe078dfff]
Nov 20 14:52:24 Pern kernel: [    0.302864] pci 0000:03:00.2: enabling Extended Tags
Nov 20 14:52:24 Pern kernel: [    0.303020] pci 0000:03:00.3: [1022:15e0] type 00 class 0x0c0330
Nov 20 14:52:24 Pern kernel: [    0.303048] pci 0000:03:00.3: reg 0x10: [mem 0xe0500000-0xe05fffff 64bit]
Nov 20 14:52:24 Pern kernel: [    0.303110] pci 0000:03:00.3: enabling Extended Tags
Nov 20 14:52:24 Pern kernel: [    0.303186] pci 0000:03:00.3: PME# supported from D0 D3hot D3cold
Nov 20 14:52:24 Pern kernel: [    0.303275] pci 0000:03:00.4: [1022:15e1] type 00 class 0x0c0330
Nov 20 14:52:24 Pern systemd[1]: Finished Load/Save Screen Backlight Brightness of backlight:amdgpu_bl0.

-----------------------------------------------------
11/21/20121
$ systemctl status systemd-backlight@backlight:acpi_video0.service
systemd-backlight@backlight:acpi_video0.service - Load/Save Screen Backlight Brightness of backlight:acpi_video0
     Loaded: loaded (/lib/systemd/system/systemd-backlight@.service; static; vendor preset: enabled)
     Active: inactive (dead)
```

I have inserted "acpi_backlight=vendor" & "acpi_osi=Linux" into grub but it doesn't seem to help. Could any of those messages cause a freeze in the boot sequemce?

---

