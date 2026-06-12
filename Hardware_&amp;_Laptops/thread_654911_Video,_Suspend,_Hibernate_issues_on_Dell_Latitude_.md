---
title: "Video, Suspend, Hibernate issues on Dell Latitude d520 with Gutsy Gibbon 7.10"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by neltnerb on 2007-12-31
I'm having a plethora of issues with my new Dell d520 Latitude notebook running Gutsy. This is a new computer, so unfortunately I can't compare it directly with Feisty. However, I did run Feisty on a d620 with similar hardware with no problems.

The first issue is that the "intel" default graphics driver for the Intel 945 graphics chipset doesn't work even close to correctly with an external monitor. I want to use the primary display in 1024x768 and be able to attach an external 1280x1024 LCD monitor when I'm working at home.

Using the intel driver resulted in the only working mode being mirroring, with no ability to turn only one of the displays on. Not unexpectedly, this also caused all manner of weird issues when running on my external monitor (videos run fullscreen only taking up the top-left 1024x768, for instance).

Telling the computer to use the i810 legacy driver seems to have fixed the problems for the most part. However, when I used the CRT/LCD button to switch displays, the resolution doesn't change, causing lots of annoyance. I can't use multihead displays at all (limiting config to that which can be done through the "Displays and Settings" dialog). Basically, when I switch from my external monitor at 1280x1024 to the laptop monitor, it just goes blank for a moment and then reactivates the external monitor. I can get it to switch only by first changing the resolution on the external monitor to 1024x768 and then switching displays.

Further causing problems is that neither suspend nor hibernate work, rendering the laptop much harder to use. I made sure that the swap partition is larger than the amount of RAM in the computer, so it shouldn't have problems hibernating. However, when I boot back up, the ubuntu logo shows up, it tries to start X11, and then it croaks, turning off the display and becoming non-responsive to keyboard input (ctl-alt-backspace fails to restart the manager, for instance). The display fails to start on either the external or the internal monitors.

Finally, suspend fails. This one is beyond my ability to reasonably diagnose.

I'm not sure what information would be helpful to figure this out because I'm not really sure which programs are broken. acpi-support? settings and displays?

The display problems were present using the "intel" driver with Hardy Heron as well. I didn't try i810 before reinstalling with gutsy. The suspend and hibernate problems also existed in Hardy, although I didn't do any diagnosis before chucking the alpha as too unstable for my purposes right now.

Thanks,

---

### Post by neltnerb on 2007-12-31
This line in my /var/log/Xorg.0.log seems strange to me.

Perhaps it has something to do with the problem?

```

(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
        915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found

```

I'm also getting the following suspicious messages in my /var/log/messages file.

```

Dec 31 16:50:04 gibbs-duhem gnome-power-manager: (neltnerb) Suspending computer because the suspend button has been pressed
Dec 31 16:50:06 gibbs-duhem dhcdbd: Unrequested down ?:3
Dec 31 16:50:06 gibbs-duhem kernel: [ 1403.844000] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
Dec 31 16:50:06 gibbs-duhem kernel: [ 1403.924000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.280000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.280000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.292000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.292000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.292000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.292000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.828000] b44.c:v1.01 (Jun 16, 2006)
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.828000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.836000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:1c:23:ae:98:09
Dec 31 16:50:09 gibbs-duhem kernel: [ 1406.864000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.204000] input: Lid Switch as /class/input/input9
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.204000] ACPI: Lid Switch [LID]
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.212000] input: Power Button (CM) as /class/input/input10
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.212000] ACPI: Power Button (CM) [PBTN]
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.212000] input: Sleep Button (CM) as /class/input/input11
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.212000] ACPI: Sleep Button (CM) [SBTN]
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.296000] ACPI: Thermal Zone [THM] (40 C)
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.388000] ACPI: AC Adapter [AC] (off-line)
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.432000] ACPI: Battery Slot [BAT0] (battery present)
Dec 31 16:50:10 gibbs-duhem kernel: [ 1407.456000] ACPI: Battery Slot [BAT1] (battery present)
Dec 31 16:50:10 gibbs-duhem kernel: [ 1408.068000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Dec 31 16:50:11 gibbs-duhem kernel: [ 1408.296000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 31 16:50:20 gibbs-duhem gnome-power-manager: (neltnerb) Resuming computer
Dec 31 16:50:20 gibbs-duhem gnome-power-manager: (neltnerb) suspend failed

```

and when I try to hibernate:

```

Dec 31 15:01:13 gibbs-duhem gnome-power-manager: (neltnerb) Hibernating computer because the hibernate button has been pressed
Dec 31 15:01:15 gibbs-duhem dhcdbd: Unrequested down ?:3
Dec 31 15:01:16 gibbs-duhem kernel: [ 6965.572000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Dec 31 15:01:16 gibbs-duhem kernel: [ 6965.868000] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
Dec 31 16:25:02 gibbs-duhem kernel: [ 6968.428000] swsusp: Basic memory bitmaps created
Dec 31 16:25:02 gibbs-duhem kernel: [ 6968.428000] Stopping tasks ... done.
Dec 31 16:25:02 gibbs-duhem kernel: [ 6968.872000] Shrinking memory...  ^H-^H\^H|^H/^H-^H\^H|^H/^Hdone (84391 pages freed)
Dec 31 16:25:02 gibbs-duhem kernel: [ 6974.996000] Freed 337564 kbytes in 6.12 seconds (55.15 MB/s)
Dec 31 16:25:02 gibbs-duhem kernel: [ 6974.996000] Suspending console(s)
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.200000] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Dec 31 16:25:02 gibbs-duhem gnome-power-manager: (neltnerb) Resuming computer
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.212000] pnp: Device 00:0c disabled.
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.232000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.232000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.248000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.248000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.248000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.248000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.252000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.268000] Disabling non-boot CPUs ...
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.384000] CPU 1 is now offline
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.384000] SMP alternatives: switching to UP code
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.384000] CPU1 is down
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.384000] swsusp: critical section: 
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.384000] swsusp: Need to copy 123319 pages
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.384000] Enabling non-boot CPUs ...
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.396000] SMP alternatives: switching to SMP code
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.396000] Booting processor 1/1 eip 3000
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.404000] Initializing CPU#1
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.484000] Calibrating delay using timer specific routine.. 3324.91 BogoMIPS (lpj=6649826)
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.484000] monitor/mwait feature present.
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.484000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.484000] CPU: L2 cache: 2048K
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.484000] CPU: Physical Processor ID: 0
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.484000] CPU: Processor Core ID: 1
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.484000] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 02
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.484000] CPU1 is up
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.488000] Switched to high resolution mode on CPU 1
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.500000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.516000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.612000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.612000] usb usb1: root hub lost power or was reset
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.612000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.612000] usb usb2: root hub lost power or was reset
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.612000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.612000] usb usb3: root hub lost power or was reset
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.612000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.612000] usb usb4: root hub lost power or was reset
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.628000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.628000] usb usb5: root hub lost power or was reset
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.632000] ehci_hcd 0000:00:1d.7: debug port 1
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.632000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.632000] Yenta O2: res at 0x94/0xD4: 00/ea
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.632000] Yenta O2: enabling read prefetch/write burst
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.696000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[efcfd000-efcfd7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.724000] pnp: Device 00:0c activated.
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.828000] ata1.00: configured for UDMA/133
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.828000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.828000] sd 0:0:0:0: [sda] Write Protect is off
Dec 31 16:25:02 gibbs-duhem kernel: [ 6975.828000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 31 16:25:02 gibbs-duhem kernel: [ 6976.084000] sd 0:0:0:0: [sda] Starting disk
Dec 31 16:25:02 gibbs-duhem kernel: [ 6976.144000] Restarting tasks ... done.
Dec 31 16:25:02 gibbs-duhem kernel: [ 6976.224000] swsusp: Basic memory bitmaps freed
Dec 31 16:25:02 gibbs-duhem kernel: [ 6976.400000] usb 5-2: USB disconnect, address 2
Dec 31 16:25:02 gibbs-duhem kernel: [ 6976.644000] usb 5-2: new high speed USB device using ehci_hcd and address 6
Dec 31 16:25:02 gibbs-duhem kernel: [ 6976.776000] usb 5-2: configuration #1 chosen from 1 choice
Dec 31 16:25:02 gibbs-duhem kernel: [ 6976.776000] hub 5-2:1.0: USB hub found
Dec 31 16:25:02 gibbs-duhem kernel: [ 6976.776000] hub 5-2:1.0: 4 ports detected
Dec 31 16:25:03 gibbs-duhem kernel: [ 6977.548000] usb 3-2: new low speed USB device using uhci_hcd and address 3
Dec 31 16:25:03 gibbs-duhem kernel: [ 6977.724000] usb 3-2: configuration #1 chosen from 1 choice
Dec 31 16:25:03 gibbs-duhem kernel: [ 6977.740000] input: Logitech USB Receiver as /class/input/input9
Dec 31 16:25:03 gibbs-duhem kernel: [ 6977.740000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2
Dec 31 16:25:03 gibbs-duhem kernel: [ 6977.768000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
Dec 31 16:25:03 gibbs-duhem kernel: [ 6977.768000] input: Logitech USB Receiver as /class/input/input10
Dec 31 16:25:03 gibbs-duhem kernel: [ 6977.768000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2
Dec 31 16:25:03 gibbs-duhem kernel: [ 6978.008000] usb 4-1: new full speed USB device using uhci_hcd and address 3
Dec 31 16:25:03 gibbs-duhem kernel: [ 6978.172000] usb 4-1: configuration #1 chosen from 1 choice
Dec 31 16:25:07 gibbs-duhem kernel: [ 6982.376000] b44.c:v1.01 (Jun 16, 2006)
Dec 31 16:25:07 gibbs-duhem kernel: [ 6982.376000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Dec 31 16:25:07 gibbs-duhem kernel: [ 6982.388000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:1c:23:ae:98:09
Dec 31 16:25:08 gibbs-duhem kernel: [ 6982.464000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 16:25:08 gibbs-duhem kernel: [ 6982.472000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Dec 31 16:25:08 gibbs-duhem kernel: [ 6982.472000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 31 16:25:08 gibbs-duhem kernel: [ 6982.656000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp
Dec 31 16:25:08 gibbs-duhem kernel: [ 6982.656000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Dec 31 16:25:08 gibbs-duhem kernel: [ 6982.656000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Dec 31 16:25:08 gibbs-duhem kernel: [ 6982.656000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 31 16:25:09 gibbs-duhem kernel: [ 6984.148000] input: Lid Switch as /class/input/input11
Dec 31 16:25:09 gibbs-duhem kernel: [ 6984.148000] ACPI: Lid Switch [LID]
Dec 31 16:25:09 gibbs-duhem kernel: [ 6984.160000] input: Power Button (CM) as /class/input/input12
Dec 31 16:25:09 gibbs-duhem kernel: [ 6984.160000] ACPI: Power Button (CM) [PBTN]
Dec 31 16:25:09 gibbs-duhem kernel: [ 6984.160000] input: Sleep Button (CM) as /class/input/input13
Dec 31 16:25:09 gibbs-duhem kernel: [ 6984.160000] ACPI: Sleep Button (CM) [SBTN]
Dec 31 16:25:09 gibbs-duhem kernel: [ 6984.284000] ACPI: Thermal Zone [THM] (29 C)
Dec 31 16:25:10 gibbs-duhem kernel: [ 6984.652000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Dec 31 16:25:10 gibbs-duhem kernel: [ 6984.652000] ACPI: AC Adapter [AC] (off-line)
Dec 31 16:25:10 gibbs-duhem kernel: [ 6984.764000] ACPI: Battery Slot [BAT0] (battery present)
Dec 31 16:25:10 gibbs-duhem kernel: [ 6984.784000] ACPI: Battery Slot [BAT1] (battery present)
Dec 31 16:25:10 gibbs-duhem kernel: [ 6984.924000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 31 16:25:24 gibbs-duhem kernel: [ 6999.452000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

```

at which point the computer froze and I did a hard reboot.

I really have no idea what to look at beyond that.

---

### Post by ravepants on 2008-01-01
I am having exactly the same problems with suspend and hibernate to the point where its driving me nuts and im considering a different distro, 
Except my D520 simply refuses to hibernate at all, giving an error message stating it failed and that I should look at the forums for help!
I have managed to find a low tech solution to the suspend but its hardly practical.
If you close the lid on the lappy for a second or two then open it for a few seconds, then close it again it will suspend, like I said not practical but it seems to work.
Other than that im racking my brains too!

Any help appreciated.

---

### Post by neltnerb on 2008-01-01
Do you happen to know if hibernate and suspend worked in feisty for you? If you haven't tried that, I'll install feisty on a test partition to see if it works there and let you know.

The solution may just be that we're stuck with Feisty until hibernate, suspend, and video drivers are restabilized with (hopefully) hardy.

---

### Post by jcbwalsh on 2008-02-02
You might try [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend). This one seems to have worked for me...

---

