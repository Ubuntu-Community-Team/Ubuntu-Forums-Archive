---
title: "Screen resolution only 640x480 - can't change it"
date: 2016-09-21
forum: Hardware
---

### Post by Kim_Schjeltved on 2016-09-21
I'm new to Ubuntu/linux and have been running Ubuntu for a few weeks now.

I have a problem with my screen resolution that starts up in 640x480. The problem is not my monitor, because I also use in on my Windows computer in 1680 x 1050.

I keep getting this message "Could not apply the stored configuration for monitors". I tried to write "mv monitors.xml monitors.bck" and after a restart, everthing seems perfect with a high resolution. But after the next restart, everything is back to low resolution again (640x480).

Link to screenshot.
[https://drive.google.com/file/d/0B2micG34zJpLZGlRMnZaNjhndnc/view?usp=sharing](https://drive.google.com/file/d/0B2micG34zJpLZGlRMnZaNjhndnc/view?usp=sharing)

What can I do to get a high resolution ?

---

### Post by kc1di on 2016-09-21
Hello Kim_Schjeltved  and Welcome to Ubuntu,
Please go to a terminal and type this command then post the results here.
```
inxi -F
```

Then we will go from there.

---

### Post by Kim_Schjeltved on 2016-09-21
Running inxi -f gives me this result -

```
CPU:       Dual core Intel Celeron G1610T (-MCP-) cache: 2048 KB 
           clock speeds: max: 2300 MHz 1: 2265 MHz 2: 2174 MHz
           CPU Flags: acpi aperfmperf apic arat arch_perfmon bts clflush cmov
           constant_tsc cx16 cx8 de ds_cpl dtes64 dtherm dts eagerfpu epb ept
           erms est flexpriority fpu fsgsbase fxsr ht lahf_lm lm mca mce mmx
           monitor msr mtrr nonstop_tsc nopl nx pae pat pbe pcid pclmulqdq
           pdcm pebs pge pln pni popcnt pse pse36 pts rdtscp rep_good sep smep
           ss sse sse2 sse4_1 sse4_2 ssse3 syscall tm tm2 tpr_shadow tsc
           tsc_deadline_timer vme vmx vnmi vpid xsave xsaveopt xtopology xtpr
```

I found out, that if I checked all the boxes in "Xdianostics Settings", then I can get the resolution 1024x768. But I would still like some better resolution.

---

### Post by ajgreeny on 2016-09-21
We need the output from that command but with an upper case F please; Linux is case sensitive unlike Windows, and you will see a quite different output.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by kc1di on 2016-09-21
Please do as ajgreeny has said. Thank You.

---

### Post by Kim_Schjeltved on 2016-09-21
I have been told, that Matrox no longer support Linux, and that's why I have these problems with the screen resolution.

But I fund a solution that works ok for me. This line "sudo apt-get install gnome-session-flashback" makes it possible for me to use 1280x1024, which is ok. I don't know what that line of code does, since I'm new to Ubuntu.


```
System:    Host: kim-ProLiant-MicroServer-Gen8 Kernel: 4.4.0-38-generic x86_64 (64 bit)           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: HP product: ProLiant MicroServer Gen8
           Mobo: N/A model: N/A Bios: HP v: J06 date: 11/02/2015
CPU:       Dual core Intel Celeron G1610T (-MCP-) cache: 2048 KB 
           clock speeds: max: 2300 MHz 1: 2300 MHz 2: 2133 MHz
Graphics:  Card: Failed to Detect Video Card!
           Display Server: X.Org 1.18.3 drivers: fbdev (unloaded: vesa)
           Resolution: 1280x1024@77.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
           GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Broadcom NetXtreme BCM5720 Gigabit Ethernet PCIe
           driver: tg3
           IF: eno1 state: up speed: 100 Mbps duplex: full
           mac: 1c:98:ec:0f:a6:7c
           Card-2: Broadcom NetXtreme BCM5720 Gigabit Ethernet PCIe
           driver: tg3
           IF: eno2 state: down mac: 1c:98:ec:0f:a6:7d
Drives:    HDD Total Size: 3000.6GB (0.5% used)
           ID-1: /dev/sda model: TOSHIBA_DT01ACA1 size: 1000.2GB
           ID-2: /dev/sdb model: TOSHIBA_DT01ACA2 size: 2000.4GB
Partition: ID-1: / size: 913G used: 9.4G (2%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.12GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 213 Uptime: 6:28 Memory: 1983.3/11847.2MB
           Client: Shell (bash) inxi: 2.2.35 



```

---

### Post by kc1di on 2016-09-21
That failed to detect your video card.  Do you know the video card in your machine?

you can try going to additional drivers app.  Control panel >Additional Drivers and see if it offers a different driver for your card.

But if you know the card let us know it will help us to help you?
if you do not know copy and past this command in the terminal and post the output. 

```
lspci -v | less
```

---

### Post by Kim_Schjeltved on 2016-09-21
My graphiccard is a Matrox G200

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: ivb_uncore
        Kernel modules: ie31200_edac


00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if
 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 24
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:06.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if
 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 25
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: fbe00000-fbefffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 0
5) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company 6 Series/C200 Series Chipset Family USB Enhanced Host Controller
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at facf0000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci


00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 
00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 
00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: bc000000-bc0fffff
        Prefetchable memory behind bridge: 00000000fab00000-00000000fabfffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: fbf00000-fbffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: fad00000-fbdfffff
        Prefetchable memory behind bridge: 00000000bf000000-00000000bfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company 6 Series/C200 Series Chipset Family USB Enhanced Host Controller
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at face0000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci


00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=14, subordinate=14, sec-latency=32
        Capabilities: <access denied>


00:1f.0 ISA bridge: Intel Corporation C204 Chipset Family LPC Controller (rev 05)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
00:1f.2 RAID bus controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA RAID Controller (rev 05)
        Subsystem: Hewlett Packard Enterprise 6 Series/C200 Series Chipset Family SATA RAID Controller
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 29
        I/O ports at 10c0 [size=8]
        I/O ports at 10c8 [size=4]
        I/O ports at 10d0 [size=8]
        I/O ports at 10d8 [size=4]
        I/O ports at 10e0 [size=32]
        Memory at facd0000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci


01:00.0 System peripheral: Hewlett-Packard Company Integrated Lights-Out Standard Slave Instrumentation & System Support (rev 05)
        Subsystem: Hewlett-Packard Company iLO4
        Flags: bus master, fast devsel, latency 0, IRQ 10
        I/O ports at 3000 [size=256]
        Memory at fbdf0000 (32-bit, non-prefetchable) [size=512]
        I/O ports at 3400 [size=256]
        Capabilities: <access denied>
        Kernel modules: hpwdt


01:00.1 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200EH (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company iLO4
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at bf000000 (32-bit, prefetchable) [size=16M]
        Memory at fbde0000 (32-bit, non-prefetchable) [size=16K]
        Memory at fb000000 (32-bit, non-prefetchable) [size=8M]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>


01:00.2 System peripheral: Hewlett-Packard Company Integrated Lights-Out Standard Management Processor Support and Messaging (rev 05)
        Subsystem: Hewlett-Packard Company iLO4
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 3800 [size=256]
        Memory at faff0000 (32-bit, non-prefetchable) [size=256]
        Memory at fae00000 (32-bit, non-prefetchable) [size=1M]
        Memory at fad80000 (32-bit, non-prefetchable) [size=512K]
        Memory at fad70000 (32-bit, non-prefetchable) [size=32K]
        Memory at fad60000 (32-bit, non-prefetchable) [size=32K]
        [virtual] Expansion ROM at fad00000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: hpilo
01:00.4 USB controller: Hewlett-Packard Company Integrated Lights-Out Standard Virtual USB Controller (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company iLO4
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 3c00 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd


02:00.0 Memory controller: Hewlett Packard Enterprise Device 005f
        DeviceName: Memory Controller
        Subsystem: Hewlett Packard Enterprise Device 005f
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at c0000000 (64-bit, prefetchable) [size=512M]
        Memory at fbef0000 (64-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>


03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe
        DeviceName: NIC Port 1
        Subsystem: Hewlett-Packard Company NetXtreme BCM5720 Gigabit Ethernet PCIe
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fabf0000 (64-bit, prefetchable) [size=64K]
        Memory at fabe0000 (64-bit, prefetchable) [size=64K]
        Memory at fabd0000 (64-bit, prefetchable) [size=64K]
        [virtual] Expansion ROM at bc000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3


03:00.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe
        DeviceName: NIC Port 2
        Subsystem: Hewlett-Packard Company NetXtreme BCM5720 Gigabit Ethernet PCIe
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fabc0000 (64-bit, prefetchable) [size=64K]
        Memory at fabb0000 (64-bit, prefetchable) [size=64K]
        Memory at faba0000 (64-bit, prefetchable) [size=64K]
        [virtual] Expansion ROM at bc020000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3
04:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
        Subsystem: Hewlett-Packard Company uPD720201 USB 3.0 Host Controller
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fbff0000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: xhci_hcd

```

---

### Post by Kim_Schjeltved on 2016-09-21
I have this in my Additional drivers

---

### Post by #&amp;thj^% on 2016-09-21
Matrox MGA drivers are unclaimed in Ubuntu 14.04 and newer because of an update of the Xorg. 
See this:[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035)
There is a work around mentioned in there also...but you are on your own there.

---

### Post by kc1di on 2016-09-22
At this point if you want to run Ubuntu 14.04/16.04 or higher. It is most likely easier to install a different video card if possible. 
What your running into is a graphics card that is no longer support by the Xorg server. and thus it's reverting to the old Vesa drivers which most likely only give you
1024x768 max.  Though you can get greater it's complicated.  I would recommend finding another video card if possible.

---

### Post by ivo-straka on 2017-04-10
Hey, I think you could try the mgag200 kernel module:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035/comments/59](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035/comments/59)
I would like to test this solution on your machine, reply or PM me if you are still interested.

---

