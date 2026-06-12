---
title: "hp tm2t touchscreen turns off after suspend :("
date: 2010-08-16
forum: Hardware
---

### Post by embrodak on 2010-08-16
Hiya,

I recently bought an HP TM2T and it works fantabulously out of the box, but I have one major issue. When I suspend and resume, the touchscreen doesn't work anymore. I'm really too noobish to know what to try, so if anybody could give me some tips, I'd be so happy.

lspci:

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Intel Corporation WiFi Link 1000 Series

```


xinput --list:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3                          	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 eraser                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3                          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=17	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]

```

and dmesg (from suspend/resume):

```

[  220.910703] CPU0 attaching NULL sched-domain.
[  220.910714] CPU1 attaching NULL sched-domain.
[  220.932739] CPU0 attaching sched-domain:
[  220.932749]  domain 0: span 0-1 level MC
[  220.932756]   groups: 0 1
[  220.932770] CPU1 attaching sched-domain:
[  220.932775]  domain 0: span 0-1 level MC
[  220.932781]   groups: 1 0
[  221.204621] wlan0: deauthenticating from 06:18:0a:30:00:7f by local choice (reason=3)
[  221.488844] PM: Syncing filesystems ... done.
[  221.520605] PM: Preparing system for mem sleep
[  221.520611] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  221.521392] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  221.521502] PM: Entering mem sleep
[  221.521525] Suspending console(s) (use no_console_suspend to debug)
[  221.568135] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  221.627316] sd 0:0:0:0: [sda] Stopping disk
[  222.626274] PM: suspend of drv:sd dev:0:0:0:0 complete after 1058.139 msecs
[  223.032210] PM: suspend of drv:psmouse dev:serio4 complete after 376.027 msecs
[  223.444108] PM: suspend of drv:atkbd dev:serio0 complete after 411.869 msecs
[  223.564141] HDA Intel 0000:01:00.1: PCI INT B disabled
[  223.580146] PM: suspend of drv:HDA Intel dev:0000:01:00.1 complete after 119.962 msecs
[  223.660159] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[  223.660172] uhci_hcd 0000:00:1d.2: PCI INT D disabled
[  223.660184] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[  223.660195] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[  223.660226] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  223.676169] ehci_hcd 0000:00:1a.7: PCI INT D disabled
[  223.676181] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[  223.676193] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[  223.725146] PM: suspend of devices complete after 2203.253 msecs
[  223.725149] PM: suspend devices took 2.204 seconds
[  223.725809] r8169 0000:02:00.0: PME# enabled
[  223.744077] r8169 0000:02:00.0: wake-up capability enabled by ACPI
[  223.792249] PM: late suspend of devices complete after 67.094 msecs
[  223.792791] ACPI: Preparing to enter system sleep state S3
[  223.864012] Disabling non-boot CPUs ...
[  223.864032] CPU0 attaching NULL sched-domain.
[  223.864036] CPU1 attaching NULL sched-domain.
[  223.928014] CPU0 attaching NULL sched-domain.
[  223.929153] Breaking affinity for irq 9
[  223.929164] Breaking affinity for irq 12
[  223.929179] Breaking affinity for irq 17
[  223.929191] Breaking affinity for irq 21
[  224.032024] CPU 1 is now offline
[  224.032027] SMP alternatives: switching to UP code
[  224.041677] Back to C!
[  224.041677] CPU0: Thermal monitoring handled by SMI
[  224.041677] Enabling non-boot CPUs ...
[  224.041677] SMP alternatives: switching to SMP code
[  224.050972] Booting processor 1 APIC 0x1 ip 0x6000
[  224.041319] Initializing CPU#1
[  224.041319] CPU: L1 I cache: 32K, L1 D cache: 32K
[  224.041319] CPU: L2 cache: 3072K
[  224.041319] CPU: Physical Processor ID: 0
[  224.041319] CPU: Processor Core ID: 1
[  224.041319] CPU1: Thermal monitoring handled by SMI
[  224.140089] CPU1: Intel(R) Core(TM)2 Duo CPU     U9600  @ 1.60GHz stepping 0a
[  224.140166] CPU0 attaching NULL sched-domain.
[  224.168016] CPU0 attaching sched-domain:
[  224.168019]  domain 0: span 0-1 level MC
  224.168022]   groups: 0 1
[  224.168027] CPU1 attaching sched-domain:
[  224.168030]  domain 0: span 0-1 level MC
[  224.168032]   groups: 1 0
[  224.172012] CPU1 is up
[  224.172758] ACPI: Waking up from system sleep state S3
[  224.421148] pcieport 0000:00:01.0: restoring config space at offset 0x7 (was 0x20003030, writing 0x3030)
[  224.421156] pcieport 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[  224.421161] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  224.421197] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0xd000000c)
[  224.421203] i915 0000:00:02.0: restoring config space at offset 0x2 (was 0x3000007, writing 0x3800007)
[  224.421207] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[  224.421257] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  224.421305] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  224.421361] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[  224.421420] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  224.421428] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[  224.421466] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[  224.421480] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xe131e041)
[  224.421487] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xe430e340)
[  224.421493] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x2020)
[  224.421504] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  224.421511] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[  224.421567] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x2ff)
[  224.421581] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xe231e141)
[  224.421587] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xe330e240)
[  224.421593] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x1010)
[  224.421604] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  224.421612] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[  224.421682] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  224.421729] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  224.421776] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  224.421831] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[  224.421871] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[  224.421877] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[  224.421883] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[  224.421897] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100100, writing 0x100107)
[  224.422007] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[  224.422104] pci 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[  224.422114] pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xe4420000)
[  224.422129] pci 0000:01:00.0: restoring config space at offset 0x6 (was 0x0, writing 0xe4400000)
[  224.422135] pci 0000:01:00.0: restoring config space at offset 0x5 (was 0x1, writing 0x3001)
[  224.422141] pci 0000:01:00.0: restoring config space at offset 0x4 (was 0x8, writing 0xc0000008)
[  224.422148] pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  224.422199] HDA Intel 0000:01:00.1: restoring config space at offset 0xf (was 0x2ff, writing 0x20b)
[  224.422222] HDA Intel 0000:01:00.1: restoring config space at offset 0x4 (was 0x0, writing 0xe4410000)
[  224.422229] HDA Intel 0000:01:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  224.422237] HDA Intel 0000:01:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[  224.422460] r8169 0000:02:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  224.422656] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  224.422695] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe2400004)
[  224.422710] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  224.423203] PM: early resume of devices complete after 2.223 msecs
[  224.648590] PM: resume of drv:battery dev:PNP0C0A:00 complete after 212.362 msecs
[  224.692059] i915 0000:00:02.0: setting latency timer to 64
[  224.836251] PM: resume of drv:i915 dev:0000:00:02.0 complete after 144.202 msecs
[  224.836263] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  224.836271] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[  224.836297] usb usb3: root hub lost power or was reset
[  224.836321] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[  224.836328] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[  224.836354] usb usb4: root hub lost power or was reset
[  224.836388] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[  224.836395] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[  224.836430] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  224.836437] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  224.836469] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  224.836476] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[  224.836502] usb usb5: root hub lost power or was reset
[  224.836524] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[  224.836531] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[  224.836557] usb usb6: root hub lost power or was reset
[  224.836579] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[  224.836586] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[  224.836612] usb usb7: root hub lost power or was reset
[  224.836634] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  224.836640] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[  224.836669] pci 0000:00:1e.0: setting latency timer to 64
[  224.836687] ahci 0000:00:1f.2: setting latency timer to 64
[  224.836805] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  224.836813] HDA Intel 0000:01:00.1: setting latency timer to 64
[  224.837748] r8169 0000:02:00.0: wake-up capability disabled by ACPI
[  224.837764] r8169 0000:02:00.0: PME# disabled
[  224.837792] iwlagn 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  225.088100] PM: resume of drv:usb dev:usb1 complete after 249.820 msecs
[  225.164104] ata2: SATA link down (SStatus 0 SControl 300)
[  225.172105] ata5: SATA link down (SStatus 0 SControl 300)
[  225.180111] ata6: SATA link down (SStatus 0 SControl 300)
[  225.220102] PM: resume of drv:usb dev:usb2 complete after 131.983 msecs
[  225.468090] PM: resume of drv:usb dev:usb4 complete after 247.956 msecs
[  225.580090] usb 2-2: reset high speed USB device using ehci_hcd and address 2
[  225.736172] PM: resume of drv:usb dev:2-2 complete after 264.200 msecs
[  225.848098] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[  225.987959] PM: resume of drv:usb dev:2-6 complete after 251.769 msecs
[  225.987987] sd 0:0:0:0: [sda] Starting disk
[  228.456108] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  228.460040] ata1.00: configured for UDMA/100
[  228.497367] PM: resume of drv:sd dev:0:0:0:0 complete after 2509.380 msecs
[  228.608103] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[  228.760644] PM: resume of drv:usb dev:4-1 complete after 263.243 msecs
[  228.761029] PM: resume of devices complete after 4337.679 msecs
[  228.761236] PM: resume devices took 4.340 seconds
[  228.761267] PM: Finishing wakeup.
[  228.761269] Restarting tasks ... done.
[  228.878891] r8169: eth0: link down
[  228.879139] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  228.915223] Registered led device: iwl-phy0::radio
[  228.915269] Registered led device: iwl-phy0::assoc
[  228.915311] Registered led device: iwl-phy0::RX
[  228.915351] Registered led device: iwl-phy0::TX
[  228.929030] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  229.094624] CPU0 attaching NULL sched-domain.
[  229.094636] CPU1 attaching NULL sched-domain.
[  229.116165] CPU0 attaching sched-domain:
[  229.116174]  domain 0: span 0-1 level MC
[  229.116181]   groups: 0 1
[  229.116191]   domain 1: span 0-1 level CPU
[  229.116197]    groups: 0-1 (cpu_power = 2048)
[  229.116211] CPU1 attaching sched-domain:
[  229.116216]  domain 0: span 0-1 level MC
[  229.116222]   groups: 1 0
[  229.116231]   domain 1: span 0-1 level CPU
[  229.116237]    groups: 0-1 (cpu_power = 2048)
[  230.220071] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xe40000
[  230.220078] Synaptics: Clickpad mode enabled
[  230.253765] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input16
[  234.911162] wlan0: deauthenticating from 06:18:0a:30:00:7e by local choice (reason=3)
[  234.950491] wlan0: direct probe to AP 06:18:0a:30:00:7f (try 1)
[  234.954204] wlan0: direct probe responded
[  234.954208] wlan0: authenticate with AP 06:18:0a:30:00:7f (try 1)
[  234.981917] wlan0: authenticated
[  234.981946] wlan0: associate with AP 06:18:0a:30:00:7f (try 1)
[  234.998104] wlan0: RX AssocResp from 06:18:0a:30:00:7f (capab=0x21 status=0 aid=2)
[  234.998115] wlan0: associated
[  235.000462] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by Favux on 2010-08-16
Hi embrodak,

Are you in Lucid?

---

### Post by embrodak on 2010-08-17
Yep, fresh install of 10.04. Just to clarify, the tablet pen still works after suspend, but the touch turns off.

---

### Post by Favux on 2010-08-17
OK, that bug has been present a long time.  Here's the post in the Lucid developement TM2 thread where it was fixed:  [http://ubuntuforums.org/showpost.php?p=9110297&postcount=91](http://ubuntuforums.org/showpost.php?p=9110297&postcount=91)

I'm not sure if the fix has been included in xf86-input-wacom yet.  Clearly it's not in the default 0.10.5 Lucid version.  Any interest in updating it and finding out?

---

### Post by embrodak on 2010-08-17
Right, I found that post before, but I really have no idea what to do with it. As I said before, kind of noobish.

---

### Post by Favux on 2010-08-17
It's a patch that you apply to the source code before compiling it.

You can update xf86-input-wacom by following Section 2 in the l[inuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") or II. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Hopefully that would include the suspend/resume fix without neeeding to patch.  You probably need to update the wacom.ko also which would be Section 1 or I, just to stay in synch with xf86-input-wacom.

---

### Post by embrodak on 2011-06-30
Sorry for the bump... I still haven't been able to fix this issue, and now I'm in 11.04.  Touch doesn't work after suspend. I tried going through that previous thread but make kept breaking... I don't have the error messages on me because it was ages ago and my ADHD mind just ignored the issue afterwards for nearly a year but now it makes me sad.


Help meeeee!

---

### Post by Favux on 2011-07-01
Hi again embrodak,

We could try and see if some xsetwacom set commands will restore touch.  Could you post the output of *xinput list* in a terminal?

---

### Post by embrodak on 2011-07-01
Hi Favux,

Thanks so much for your patience!

Before suspending, xinput --list output:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Finger touch             	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen eraser               	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen stylus               	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=17	[slave  keyboard (3)]

```

and after suspending:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=17	[slave  keyboard (3)]

```

I just noticed that my tablet pen doesn't work either after suspend (if you couldn't tell from the xinput...). This seems like a different issue than I had before because in 10.04 xinput --list still recognized my tablet and touch after suspend.

Thanks again!

---

