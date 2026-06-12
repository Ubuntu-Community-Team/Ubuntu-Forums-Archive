---
title: "This has me stumped!"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by garrye on 2006-08-24
This is maddening!!
Acer Aspire 3003 WLCI
AMD Sempron 3000+ on SiS chipset
lspci gives:
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
0000:02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

dmesg | grep ACPI gives:
[17179569.184000]  BIOS-e820: 000000000def0000 - 000000000defa000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000defa000 - 000000000df00000 (ACPI NVS)
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7f60
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0def619d
[17179569.184000] ACPI: FADT (v001 SiS    755F     0x06040000 PTL  0x000f4240) @ 0x0def9e3e
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x0def9eb2
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x0def9f88
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0def9fd8
[17179569.184000] ACPI: DSDT (v001 PTLTD       755 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ11 used by override.
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179571.896000] ACPI: Looking for DSDT ... not found!
[17179572.044000] ACPI: bus type pci registered
[17179572.044000] ACPI: Subsystem revision 20051216
[17179572.044000] ACPI: Interpreter enabled
[17179572.044000] ACPI: Using IOAPIC for interrupt routing
[17179572.044000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.048000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.052000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[17179572.068000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[17179572.068000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179572.068000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[17179572.068000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[17179572.068000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[17179572.068000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[17179572.068000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179572.068000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[17179572.068000] pnp: PnP ACPI init
[17179572.068000] pnp: PnP ACPI: found 7 devices
[17179572.068000] PnPBIOS: Disabled by ACPI PNP
[17179572.068000] PCI: Using ACPI for IRQ routing
[17179572.072000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179572.444000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 177
[17179572.444000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[17179572.484000] ACPI wakeup devices:
[17179572.484000] ACPI: (supports S0 S3 S4 S5)
[17179573.680000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.684000] ACPI: Thermal Zone [THRM] (41 C)
[17179574.192000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 185
[17179577.224000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 193
[17179577.604000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 201
[17179577.984000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 209
[17179594.756000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179594.796000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179595.244000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 177
[17179596.064000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179600.564000] ACPI: AC Adapter [ACAD] (on-line)
[17179600.592000] ACPI: Battery Slot [BAT1] (battery present)
[17179600.668000] ACPI: Power Button (FF) [PWRF]
[17179600.668000] ACPI: Lid Switch [LID]
[17179600.668000] ACPI: Power Button (CM) [PWRB]
[17179600.668000] ACPI: Sleep Button (CM) [SLPB]

The following combinations work in windows xp which came pre-installed on this laptop:

D-Link DI-624 or LinkSys WRT54G with either a built-in wireless ethernet card sporting Broadcom 4318 silicon or PCMCIA card made by D-Link a DWL-G650 sporting Atheros AR5212 silicon.  Either card together with either router configured with WPA-PSK -- AES_CCMP or TKIP work fine under windows.  The add-in card with its poorer antenna (methinks) does not perform nearly as well as the distance to the router increases.  I see the negociated bit rate drop off to 11 Megabits/s or even lower as signal strength/quality becomes progressively poorer.  Actual tested network transfer rates get as low as 300-500 Kilobits/s.  Network streams become difficult to start and keep going.

Here's the kicker though.
While network performance is erratic when the client (laptop) is at extreme range it remains associated.  The wireless network connection is NOT lost.

This is not the case when running Ubuntu 6.06 LTS.  With Ubuntu there are frequent disconnects, especially when the network connection is idle (no data transfer).  The disconnects become less frequent when there is network traffic such as an audio stream or even something like Gaim which periodically checks for new mail etc.  Once the connection is lost I'm forced to code "sudo ifdown ath0/wlan0" followed by "sudo ifup ath0/wlan0" to get the connection back.  Also it "seems" like running an audio stream reduces the frequency of disconnects more than just having Gaim running.  It's as though some event strikes once every four minutes or so that causes the disconnect only if there is no network traffic at the instant it strikes.  I've tried monitoring various log files like: syslog, dmesg, daemon.log, messages, kern.log, Xorg.0.log, acpid, and debug, but haven't noticed anything that would explain this.  Moreover, ALL this behavior is somewhat random in that one bootup will be fraught with this behavior.  Sometimes if I eject the card or reboot things get somewhat better.  A couple of times I've run the thing for days without seeing this behavior at all!!

Also the power management is equally flakey.  When running on AC, if I unplug the adapter, sometimes the power manager reports that the laptop is running on battery.  Other times it declares that battery power is critically low and promptly shuts down the laptop even though the front light on the laptop indicates that the battery is fully charged.  When you press "Fn+F4" Ubuntu ATTEMPTS to suspend the laptop.  Usually it's successful.  The screen saver kicks in briefly, followed by a black screen with a blinking underline cursor, there's some disk activity, and the laptop enters the suspended state.  Tapping on a key produces the screensaver again followed by a login prompt.  Logging in restores the session.  Other times, it starts this sequence of events but instead of suspending it ends up at the login prompt and the laptop becomes totally unresponsive.  It doesn't accept any keyboard or mouse input and needs to be powered off and back on.  One time I caught the glimpse of a message.  Something about failing to stop two processes.  Further investigation has revealed a couple of uninteruptible processes "hald-addon-storage" which could likely be the cause of suspend or hibernate not working.

Could the flakey wireless and power management be caused by the same thing?

What about the following from dmesg above?
[17179569.184000] ACPI: DSDT (v001 PTLTD       755 0x06040000 MSFT 0x0100000e) @ 0x00000000
***DSDT made for "Microsoft Windows"?-------------------------^^^^
and then 11 lines further down:
[17179571.896000] ACPI: Looking for DSDT ... not found!
HUH?
Does this call for a fix?  Is this related to the flakey wireless/powermgmt?

Further on the addon storage thing.  A variety of removable media including a USB flash drive, cameras, USB floppy drive, and CD's/DVD's all mount as expected with the appearance of an icon on the desktop and an opening of a nautilus window displaying the contents of the mounted media.

Everything -- EVERYTHING!!! -- works on this blasted laptop and works really well except for the crappy wireless and power management.

Kudos and double kudos to the Ubuntu team.  This cheep krappy laptop works like a charm.

I'm simply at a loss as to how to fix the rest.  Even the power management I can live with.  Just have to watch that you don't do something stupid like try to eject a floppy by right clicking the icon but push the eject button on the drive itself.

Any ideas anybody?  What other diagnostic info can I throw out here?
](*,) ](*,)](*,) ](*,)](*,) ](*,)](*,) ](*,)] 
RRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRR!!!!!!!!!!!!111111111111

---

### Post by garrye on 2006-08-25
Further to this issue I noticed this morning that playing a local video using gxine causes the wireless connection to be lost more quickly.  I'm playing a 720X480 Xvid clip which drives processor usage up to around 75%.  While it's playing I get wireless connection drops every couple of minutes.  Stopping or pausing playback cures this.

---

### Post by lenbrown on 2006-08-31
> ACPI: DSDT (v001 PTLTD 755 0x06040000 MSFT 0x0100000e) @ 0x00000000
 ***DSDT made for "Microsoft Windows"?-------------------------^^^^

The MSFT here identifies the vendor of the compiler
that was used to build the DSDT.  It is independent
of the actual source for the DSDT.

While we've found numerous bugs in the code produced
by the MSFT compiler, and we believe that the compiler
supplied by Intel is better at preventing AML bugs,
the reality is that the largest BIOS vendors, use
the MSFT compiler and so Linux has to deal with its bugs.
But again, the compiler used doesn't necessarily
mean there are special hooks for Windows -- though
examples of such things do exist.

> ACPI: Looking for DSDT ... not found!

This is an Ubuntu specific bug.  Ubuntu includes a patch
that upstream has repeatedly rejected allowing a DSDT
override in the initrd. Making matters worse, it complains
about the normal case when there is no-override -- making
the normal case look like an error case.

---

### Post by LittleLebowski on 2006-09-30
How hard it to post a descriptive post title?

---

