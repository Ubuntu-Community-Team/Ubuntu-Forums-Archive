---
title: "[SOLVED] tty after resume from suspend"
date: 2008-08-09
forum: Hardware
---

### Post by bigtoedsloth on 2008-08-09
My problem is that suspend from the gnome shutdown menu works, but when I resume (by pressing the power button) a tty is displayed (mentioning something about restarting LIRC) and I have to press Ctrl-Alt-F7 to get my gnome desktop back.

Is there a way to fix this?

I am running Ubuntu Hardy and have an nvidia 8500gt graphics card, running a manually installed nvidia binary driver.

I've followed the instructions here [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

### Post by phidia on 2008-08-09
This can be a tough issue IMO and so I hesitate to try and offer help, but at least this will be a free bump.

Try looking in /var/log/messages or since you are able to get back to your desktop without rebooting open a terminal and enter "dmesg" after what you've described happens.

Maybe there will be some output there that you can post/search.

Also providing the exact messages you are seeing and more of your system specs (wireless card) would be helpful.

---

### Post by bigtoedsloth on 2008-08-10
I'm trying this on a desktop system, with a gigabyte [GA-G33M-DS2R]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2534&ProductName=GA-G33M-DS2R") motherboard and an MSI [NX8500GT-MTD256EH]("http://www.msicomputer.com/product/p_spec.asp?model=NX8500GT-MTD256EH&class=vga") video card.  I'm not using wireless networking.  My hardy install is all pretty much standard, although I have installed LIRC from source, since the hardy package didn't support my imon LCD.

I'm not sure of the significance of all of the dmesg output, but here's what happens before/after the resume.

```

[  155.606246] ACPI: PCI interrupt for device 0000:04:00.0 disabled
[  155.611485] usbcore: deregistering interface driver ndiswrapper
[  157.046562] Syncing filesystems ... done.
[  157.046580] PM: Preparing system for mem sleep
[  157.046582] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  157.047085] Freezing remaining freezable tasks ... (elapsed 0.10 seconds) done.
[  157.147103] PM: Entering mem sleep
[  157.147104] Suspending console(s)
[  157.147135] lirc_imon 5-1:1.0: no suspend for driver lirc_imon?
[  157.162080] sd 5:0:0:0: [sdb] Synchronizing SCSI cache
[  157.162216] sd 5:0:0:0: [sdb] Stopping disk
[  158.083629] sd 3:0:0:0: [sda] Synchronizing SCSI cache
[  158.084003] sd 3:0:0:0: [sda] Stopping disk
[  158.526230] dvb_usb_dib0700 9-1:1.0: no suspend for driver dvb_usb_dib0700?
[  158.538712] ACPI handle has no context!
[  158.538856] parport_pc 00:09: disabled
[  158.538969] serial 00:08: disabled
[  158.539080] serial 00:07: disabled
[  158.539129] ACPI handle has no context!
[  158.554409] ACPI: PCI interrupt for device 0000:05:01.2 disabled
[  158.570380] ACPI: PCI interrupt for device 0000:05:01.1 disabled
[  158.586337] ACPI: PCI interrupt for device 0000:05:01.0 disabled
[  158.602426] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  158.618213] ACPI handle has no context!
[  158.618224] NVRM: RmPowerManagement: 4
[  159.787155] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[  159.803152] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[  159.819112] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[  159.835026] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[  159.835057] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[  159.835088] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[  159.850958] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[  159.866935] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[  159.882899] ACPI: PCI interrupt for device 0000:00:1a.2 disabled
[  159.882930] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
[  159.882961] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
[  159.885434] Disabling non-boot CPUs ...
[  159.885449] CPU0 attaching NULL sched-domain.
[  159.885450] CPU1 attaching NULL sched-domain.
[  159.998552] CPU 1 is now offline
[  159.998555] SMP alternatives: switching to UP code
[  159.999618] CPU0 attaching sched-domain:
[  159.999620]  domain 0: span 01
[  159.999621]   groups: 01
[  159.999770] CPU1 is down
[    0.674569] Back to C!
[    0.674908] Enabling non-boot CPUs ...
[    0.674954] CPU0 attaching NULL sched-domain.
[    0.685531] SMP alternatives: switching to SMP code
[    0.686387] Booting processor 1/1 eip 3000
[    0.696597] Initializing CPU#1
[    0.773218] Calibrating delay using timer specific routine.. 5333.18 BogoMIPS (lpj=10666362)
[    0.773223] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001 00000000
[    0.773227] monitor/mwait feature present.
[    0.773229] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.773230] CPU: L2 cache: 4096K
[    0.773231] CPU: Physical Processor ID: 0
[    0.773232] CPU: Processor Core ID: 1
[    0.773233] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001 00000000
[    0.773756] CPU1: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.773770] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.793723] Measured 55492490744 cycles TSC warp between CPUs, turning off TSC clock.
[    0.793724] Marking TSC unstable due to: check_tsc_sync_source failed.
[    0.793729] Time: hpet clocksource has been installed.
[    0.793745] CPU0 attaching sched-domain:
[    0.793747]  domain 0: span 03
[    0.793748]   groups: 01 02
[    0.793749] CPU1 attaching sched-domain:
[    0.793750]  domain 0: span 03
[    0.793751]   groups: 02 01
[    0.794002] CPU1 is up
[    0.795146] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.795157] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.795162] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    0.795200] usb usb1: root hub lost power or was reset
[    0.795217] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[    0.795221] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    0.795257] usb usb2: root hub lost power or was reset
[    0.795276] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 19
[    0.795280] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[    0.795316] usb usb3: root hub lost power or was reset
[    0.797741] Switched to high resolution mode on CPU 1
[    0.809155] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
[    0.809160] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    0.825106] PM: Writing back config space on device 0000:00:1b.0 at offset f (was 100, writing 109)
[    0.825118] PM: Writing back config space on device 0000:00:1b.0 at offset 4 (was 4, writing f7100004)
[    0.825121] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 8)
[    0.825126] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100000, writing 100002)
[    0.825140] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[    0.825145] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[    0.920967] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20009090, writing 9090)
[    0.920997] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.921006] PM: Writing back config space on device 0000:00:1c.4 at offset f (was 100, writing 10a)
[    0.921014] PM: Writing back config space on device 0000:00:1c.4 at offset 9 (was 10001, writing 1fff1)
[    0.921018] PM: Writing back config space on device 0000:00:1c.4 at offset 8 (was 0, writing f4f0f400)
[    0.921021] PM: Writing back config space on device 0000:00:1c.4 at offset 7 (was 0, writing b0b0)
[    0.921028] PM: Writing back config space on device 0000:00:1c.4 at offset 3 (was 810000, writing 810008)
[    0.921033] PM: Writing back config space on device 0000:00:1c.4 at offset 1 (was 100000, writing 100407)
[    0.921062] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.921070] PM: Writing back config space on device 0000:00:1c.5 at offset f (was 200, writing 205)
[    0.921076] PM: Writing back config space on device 0000:00:1c.5 at offset 9 (was 10001, writing 80018001)
[    0.921079] PM: Writing back config space on device 0000:00:1c.5 at offset 8 (was 0, writing f6f0f500)
[    0.921082] PM: Writing back config space on device 0000:00:1c.5 at offset 7 (was 0, writing c0c0)
[    0.921089] PM: Writing back config space on device 0000:00:1c.5 at offset 3 (was 810000, writing 810008)
[    0.921092] PM: Writing back config space on device 0000:00:1c.5 at offset 1 (was 100000, writing 100407)
[    0.921115] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.921123] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    0.921128] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    0.921169] usb usb4: root hub lost power or was reset
[    0.921185] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[    0.921191] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    0.921230] usb usb5: root hub lost power or was reset
[    0.921250] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[    0.921255] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    0.921295] usb usb6: root hub lost power or was reset
[    0.936843] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    0.936849] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    0.936912] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.952791] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    0.952795] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    0.968742] PM: Writing back config space on device 0000:00:1f.5 at offset 1 (was 2b00003, writing 2b00007)
[    0.968755] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 21
[    0.968759] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    0.968796] NVRM: RmPowerManagement: 5
[    1.383659] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10a)
[    1.383675] PM: Writing back config space on device 0000:03:00.0 at offset 8 (was 1, writing b401)
[    1.383681] PM: Writing back config space on device 0000:03:00.0 at offset 7 (was 1, writing b301)
[    1.383686] PM: Writing back config space on device 0000:03:00.0 at offset 6 (was 1, writing b201)
[    1.383691] PM: Writing back config space on device 0000:03:00.0 at offset 5 (was 1, writing b101)
[    1.383696] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 1, writing b001)
[    1.383701] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 8)
[    1.383708] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100007)
[    1.383737] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    1.383744] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    1.383772] PM: Writing back config space on device 0000:04:00.0 at offset f (was 100, writing 105)
[    1.383790] PM: Writing back config space on device 0000:04:00.0 at offset 6 (was 4, writing f6000004)
[    1.383797] PM: Writing back config space on device 0000:04:00.0 at offset 4 (was 1, writing c001)
[    1.383802] PM: Writing back config space on device 0000:04:00.0 at offset 3 (was 0, writing 8)
[    1.383808] PM: Writing back config space on device 0000:04:00.0 at offset 1 (was 100000, writing 100003)
[    1.399600] PCI: Enabling device 0000:05:01.0 (0000 -> 0001)
[    1.399604] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 19 (level, low) -> IRQ 21
[    1.399616] PM: Writing back config space on device 0000:05:01.0 at offset f (was 100, writing 10b)
[    1.399626] PM: Writing back config space on device 0000:05:01.0 at offset 8 (was fce1, writing d001)
[    1.399634] PM: Writing back config space on device 0000:05:01.0 at offset 3 (was 801600, writing 802008)
[    1.399640] PM: Writing back config space on device 0000:05:01.0 at offset 1 (was 2100005, writing 2100007)
[    1.399665] usb usb10: root hub lost power or was reset
[    1.415556] PCI: Enabling device 0000:05:01.1 (0000 -> 0001)
[    1.415558] ACPI: PCI Interrupt 0000:05:01.1[B] -> GSI 18 (level, low) -> IRQ 19
[    1.415570] PM: Writing back config space on device 0000:05:01.1 at offset f (was 200, writing 20b)
[    1.415580] PM: Writing back config space on device 0000:05:01.1 at offset 8 (was fce1, writing d101)
[    1.415588] PM: Writing back config space on device 0000:05:01.1 at offset 3 (was 801600, writing 802008)
[    1.415593] PM: Writing back config space on device 0000:05:01.1 at offset 1 (was 2100005, writing 2100007)
[    1.415617] usb usb11: root hub lost power or was reset
[    1.427706] ata3.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[    1.427708] ata3.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[    1.427710] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    1.432514] PCI: Enabling device 0000:05:01.2 (0000 -> 0002)
[    1.432517] ACPI: PCI Interrupt 0000:05:01.2[C] -> GSI 16 (level, low) -> IRQ 16
[    1.432528] PM: Writing back config space on device 0000:05:01.2 at offset f (was 300, writing 30a)
[    1.432543] PM: Writing back config space on device 0000:05:01.2 at offset 4 (was 0, writing f7005000)
[    1.432547] PM: Writing back config space on device 0000:05:01.2 at offset 3 (was 801600, writing 802008)
[    1.432552] PM: Writing back config space on device 0000:05:01.2 at offset 1 (was 2100006, writing 2100017)
[    1.432561] usb usb9: root hub lost power or was reset
[    1.447481] PM: Writing back config space on device 0000:05:07.0 at offset f (was 4020100, writing 4020106)
[    1.447495] PM: Writing back config space on device 0000:05:07.0 at offset 5 (was 0, writing f7000000)
[    1.447499] PM: Writing back config space on device 0000:05:07.0 at offset 4 (was 0, writing f7004000)
[    1.447504] PM: Writing back config space on device 0000:05:07.0 at offset 3 (was 0, writing 2008)
[    1.447509] PM: Writing back config space on device 0000:05:07.0 at offset 1 (was 2100000, writing 2100006)
[    1.497007] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f7004000-f70047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.497482] serial 00:07: activated
[    1.497874] serial 00:08: activated
[    1.498267] parport_pc 00:09: activated
[    1.660085] ata3.00: configured for UDMA/33
[    2.791918] sd 3:0:0:0: [sda] Starting disk
[    5.983370] ata4: port is slow to respond, please be patient (Status 0x80)
[    5.999327] ata6: port is slow to respond, please be patient (Status 0x80)
[    8.269443] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    8.269446] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    8.269448] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    8.281513] ata4.00: configured for UDMA/133
[    8.286881] sd 3:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    8.286886] sd 5:0:0:0: [sdb] Starting disk
[    8.286893] sd 3:0:0:0: [sda] Write Protect is off
[    8.286895] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.286914] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.672369] ata6.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    8.672371] ata6.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    8.672373] ata6.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    8.681440] ata6.00: configured for UDMA/133
[    8.689360] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[    8.689371] sd 5:0:0:0: [sdb] Write Protect is off
[    8.689372] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.689386] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.689415] PM: Finishing wakeup.
[    8.689417] Restarting tasks ... <6>usb 2-2: USB disconnect, address 3
[    8.696112] done.
[    8.759131] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[    9.039223] usb 2-2: new low speed USB device using uhci_hcd and address 4
[    9.216286] usb 2-2: configuration #1 chosen from 1 choice
[    9.233329] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input6
[    9.270622] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.1-2
[    9.298972] Fixing up Logitech keyboard report descriptor
[    9.299447] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.1/input/input7
[    9.382359] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2
[    9.382449] usb 5-1: USB disconnect, address 2
[    9.382576] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: imon_disconnect: iMON device disconnected
[    9.382598] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: Deregistered iMON plugin(minor:0)
[    9.621657] usb 5-1: new low speed USB device using uhci_hcd and address 3
[    9.776810] usb 5-1: configuration #1 chosen from 1 choice
[    9.779724] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[    9.779729] lirc_dev: lirc_register_plugin: sample_rate: 0
[    9.779744] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin(minor:0)
[    9.779764] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<5:3> initialized
[    9.779846] usb 9-1: USB disconnect, address 2
[    9.780072] mt2060 I2C write failed

```

There's nothing there that jumps out to me as being bad.  A google for that last line points toward my tuner card (Hauppauge NOVA-T 500).  Could that be the culprit?

Interestingly I noticed that the networking is completely broken after resume.  sudo /etc/init.d/networking restart doesn't help at all.

---

### Post by cdtech on 2008-08-10
Don't know if this will be of any help but try to run the suspend via command line:
```
sudo /etc/acpi/sleep.sh force
```
and see if the suspend works properly. This will bypass the pm-utils and narrow the troubleshooting.

---

### Post by bigtoedsloth on 2008-08-11
Same effect running acpi sleep directly.  The command didn't return to the prompt after the resume.  Is that to be expected?  What follows is the relevant part of the dmesg log

```

[84639.163760] usbcore: deregistering interface driver ndiswrapper
[84639.277178] ACPI: PCI interrupt for device 0000:04:00.0 disabled
[84641.902678] Syncing filesystems ... done.
[84641.919243] PM: Preparing system for mem sleep
[84641.919246] Freezing user space processes ... (elapsed 0.00 seconds) done.
[84641.919724] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[84641.919741] PM: Entering mem sleep
[84641.919742] Suspending console(s)
[84641.919773] lirc_imon 5-1:1.0: no suspend for driver lirc_imon?
[84641.933130] dvb_usb_dib0700 11-1:1.0: no suspend for driver dvb_usb_dib0700?
[84641.949144] sd 5:0:0:0: [sdb] Synchronizing SCSI cache
[84641.949279] sd 5:0:0:0: [sdb] Stopping disk
[84642.838717] sd 3:0:0:0: [sda] Synchronizing SCSI cache
[84642.838810] sd 3:0:0:0: [sda] Stopping disk
[84643.274542] ACPI handle has no context!
[84643.274687] parport_pc 00:09: disabled
[84643.274801] serial 00:08: disabled
[84643.274912] serial 00:07: disabled
[84643.274961] ACPI handle has no context!
[84643.289551] ACPI: PCI interrupt for device 0000:05:01.2 disabled
[84643.305519] ACPI: PCI interrupt for device 0000:05:01.1 disabled
[84643.321476] ACPI: PCI interrupt for device 0000:05:01.0 disabled
[84643.337564] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[84643.353352] ACPI handle has no context!
[84643.353363] NVRM: RmPowerManagement: 4
[84644.506335] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[84644.522336] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[84644.538305] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[84644.554207] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[84644.554238] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[84644.554269] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[84644.570127] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[84644.586115] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[84644.602083] ACPI: PCI interrupt for device 0000:00:1a.2 disabled
[84644.602114] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
[84644.602145] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
[84644.604619] Disabling non-boot CPUs ...
[84644.604634] CPU0 attaching NULL sched-domain.
[84644.604635] CPU1 attaching NULL sched-domain.
[84644.717732] CPU 1 is now offline
[84644.717735] SMP alternatives: switching to UP code
[84644.718804] CPU0 attaching sched-domain:
[84644.718806]  domain 0: span 01
[84644.718807]   groups: 01
[84644.718935] CPU1 is down
[    0.673937] Back to C!
[    0.674275] Enabling non-boot CPUs ...
[    0.674320] CPU0 attaching NULL sched-domain.
[    0.684909] SMP alternatives: switching to SMP code
[    0.685768] Booting processor 1/1 eip 3000
[    0.695977] Initializing CPU#1
[    0.772602] Calibrating delay using timer specific routine.. 5333.19 BogoMIPS (lpj=10666390)
[    0.772607] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001 00000000
[    0.772610] monitor/mwait feature present.
[    0.772612] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.772613] CPU: L2 cache: 4096K
[    0.772615] CPU: Physical Processor ID: 0
[    0.772616] CPU: Processor Core ID: 1
[    0.772617] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001 00000000
[    0.773136] CPU1: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.773150] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.793103] Measured 55519877128 cycles TSC warp between CPUs, turning off TSC clock.
[    0.793104] Marking TSC unstable due to: check_tsc_sync_source failed.
[    0.793109] Time: hpet clocksource has been installed.
[    0.793125] CPU0 attaching sched-domain:
[    0.793127]  domain 0: span 03
[    0.793128]   groups: 01 02
[    0.793129] CPU1 attaching sched-domain:
[    0.793130]  domain 0: span 03
[    0.793131]   groups: 02 01
[    0.793383] CPU1 is up
[    0.794528] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.794540] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.794544] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    0.794583] usb usb1: root hub lost power or was reset
[    0.794600] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[    0.794604] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    0.794640] usb usb2: root hub lost power or was reset
[    0.794659] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 19
[    0.794663] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[    0.794700] usb usb3: root hub lost power or was reset
[    0.797121] Switched to high resolution mode on CPU 1
[    0.808538] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
[    0.808543] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    0.824489] PM: Writing back config space on device 0000:00:1b.0 at offset f (was 100, writing 109)
[    0.824501] PM: Writing back config space on device 0000:00:1b.0 at offset 4 (was 4, writing f7100004)
[    0.824505] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 8)
[    0.824509] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100000, writing 100002)
[    0.824523] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[    0.824528] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[    0.824552] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20009090, writing 9090)
[    0.824580] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.824588] PM: Writing back config space on device 0000:00:1c.4 at offset f (was 100, writing 10a)
[    0.824595] PM: Writing back config space on device 0000:00:1c.4 at offset 9 (was 10001, writing 1fff1)
[    0.824599] PM: Writing back config space on device 0000:00:1c.4 at offset 8 (was 0, writing f4f0f400)
[    0.824603] PM: Writing back config space on device 0000:00:1c.4 at offset 7 (was 0, writing b0b0)
[    0.824609] PM: Writing back config space on device 0000:00:1c.4 at offset 3 (was 810000, writing 810008)
[    0.824613] PM: Writing back config space on device 0000:00:1c.4 at offset 1 (was 100000, writing 100407)
[    0.824637] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.824644] PM: Writing back config space on device 0000:00:1c.5 at offset f (was 200, writing 205)
[    0.824652] PM: Writing back config space on device 0000:00:1c.5 at offset 9 (was 10001, writing 80018001)
[    0.824655] PM: Writing back config space on device 0000:00:1c.5 at offset 8 (was 0, writing f6f0f500)
[    0.824659] PM: Writing back config space on device 0000:00:1c.5 at offset 7 (was 0, writing c0c0)
[    0.824665] PM: Writing back config space on device 0000:00:1c.5 at offset 3 (was 810000, writing 810008)
[    0.824669] PM: Writing back config space on device 0000:00:1c.5 at offset 1 (was 100000, writing 100407)
[    0.824697] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.824705] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    0.824709] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    0.824746] usb usb4: root hub lost power or was reset
[    0.824762] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[    0.824766] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    0.824802] usb usb5: root hub lost power or was reset
[    0.824821] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[    0.824825] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    0.824862] usb usb6: root hub lost power or was reset
[    0.840436] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    0.840441] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    0.840505] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.856425] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    0.856429] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    0.872375] PM: Writing back config space on device 0000:00:1f.5 at offset 1 (was 2b00003, writing 2b00007)
[    0.872388] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 21
[    0.872392] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    0.872430] NVRM: RmPowerManagement: 5
[    1.287297] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10a)
[    1.287314] PM: Writing back config space on device 0000:03:00.0 at offset 8 (was 1, writing b401)
[    1.287320] PM: Writing back config space on device 0000:03:00.0 at offset 7 (was 1, writing b301)
[    1.287325] PM: Writing back config space on device 0000:03:00.0 at offset 6 (was 1, writing b201)
[    1.287330] PM: Writing back config space on device 0000:03:00.0 at offset 5 (was 1, writing b101)
[    1.287335] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 1, writing b001)
[    1.287341] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 8)
[    1.287348] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100007)
[    1.287376] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    1.287383] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    1.287410] PM: Writing back config space on device 0000:04:00.0 at offset f (was 100, writing 105)
[    1.287428] PM: Writing back config space on device 0000:04:00.0 at offset 6 (was 4, writing f6000004)
[    1.287435] PM: Writing back config space on device 0000:04:00.0 at offset 4 (was 1, writing c001)
[    1.287440] PM: Writing back config space on device 0000:04:00.0 at offset 3 (was 0, writing 8)
[    1.287446] PM: Writing back config space on device 0000:04:00.0 at offset 1 (was 100000, writing 100003)
[    1.303229] PCI: Enabling device 0000:05:01.0 (0000 -> 0001)
[    1.303233] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 19 (level, low) -> IRQ 21
[    1.303244] PM: Writing back config space on device 0000:05:01.0 at offset f (was 100, writing 10b)
[    1.303255] PM: Writing back config space on device 0000:05:01.0 at offset 8 (was fce1, writing d001)
[    1.303263] PM: Writing back config space on device 0000:05:01.0 at offset 3 (was 801600, writing 802008)
[    1.303268] PM: Writing back config space on device 0000:05:01.0 at offset 1 (was 2100005, writing 2100007)
[    1.303293] usb usb7: root hub lost power or was reset
[    1.319191] PCI: Enabling device 0000:05:01.1 (0000 -> 0001)
[    1.319193] ACPI: PCI Interrupt 0000:05:01.1[B] -> GSI 18 (level, low) -> IRQ 19
[    1.319206] PM: Writing back config space on device 0000:05:01.1 at offset f (was 200, writing 20b)
[    1.319216] PM: Writing back config space on device 0000:05:01.1 at offset 8 (was fce1, writing d101)
[    1.319224] PM: Writing back config space on device 0000:05:01.1 at offset 3 (was 801600, writing 802008)
[    1.319230] PM: Writing back config space on device 0000:05:01.1 at offset 1 (was 2100005, writing 2100007)
[    1.319253] usb usb8: root hub lost power or was reset
[    1.335158] PCI: Enabling device 0000:05:01.2 (0000 -> 0002)
[    1.335161] ACPI: PCI Interrupt 0000:05:01.2[C] -> GSI 16 (level, low) -> IRQ 16
[    1.335172] PM: Writing back config space on device 0000:05:01.2 at offset f (was 300, writing 30a)
[    1.335186] PM: Writing back config space on device 0000:05:01.2 at offset 4 (was 0, writing f7005000)
[    1.335190] PM: Writing back config space on device 0000:05:01.2 at offset 3 (was 801600, writing 802008)
[    1.335195] PM: Writing back config space on device 0000:05:01.2 at offset 1 (was 2100006, writing 2100017)
[    1.335205] usb usb11: root hub lost power or was reset
[    1.347294] ata3.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[    1.347296] ata3.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[    1.347298] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    1.352116] PM: Writing back config space on device 0000:05:07.0 at offset f (was 4020100, writing 4020106)
[    1.352130] PM: Writing back config space on device 0000:05:07.0 at offset 5 (was 0, writing f7000000)
[    1.352135] PM: Writing back config space on device 0000:05:07.0 at offset 4 (was 0, writing f7004000)
[    1.352139] PM: Writing back config space on device 0000:05:07.0 at offset 3 (was 0, writing 2008)
[    1.352144] PM: Writing back config space on device 0000:05:07.0 at offset 1 (was 2100000, writing 2100006)
[    1.401642] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f7004000-f70047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.402118] serial 00:07: activated
[    1.402510] serial 00:08: activated
[    1.402904] parport_pc 00:09: activated
[    1.579690] ata3.00: configured for UDMA/33
[    2.695518] sd 3:0:0:0: [sda] Starting disk
[    5.902947] ata6: port is slow to respond, please be patient (Status 0x80)
[    5.902950] ata4: port is slow to respond, please be patient (Status 0x80)
[    8.260830] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    8.260833] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    8.260835] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    8.272901] ata4.00: configured for UDMA/133
[    8.279453] sd 3:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    8.279459] sd 5:0:0:0: [sdb] Starting disk
[    8.279466] sd 3:0:0:0: [sda] Write Protect is off
[    8.279468] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.279487] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.860561] ata6.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    9.860563] ata6.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    9.860565] ata6.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    9.869642] ata6.00: configured for UDMA/133
[    9.873460] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[    9.873470] sd 5:0:0:0: [sdb] Write Protect is off
[    9.873472] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    9.873485] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.873518] PM: Finishing wakeup.
[    9.873519] Restarting tasks ... <6>usb 2-2: USB disconnect, address 3
[    9.876610] done.
[   10.029421] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   10.204470] usb 2-2: new low speed USB device using uhci_hcd and address 4
[   10.380613] usb 2-2: configuration #1 chosen from 1 choice
[   10.397682] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input6
[   10.450863] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.1-2
[   10.483268] Fixing up Logitech keyboard report descriptor
[   10.483744] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.1/input/input7
[   10.571548] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2
[   10.571636] usb 5-1: USB disconnect, address 4
[   10.571709] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: imon_disconnect: iMON device disconnected
[   10.571727] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: Deregistered iMON plugin(minor:0)
[   10.809878] usb 5-1: new low speed USB device using uhci_hcd and address 5
[   10.965074] usb 5-1: configuration #1 chosen from 1 choice
[   10.967995] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   10.968001] lirc_dev: lirc_register_plugin: sample_rate: 0
[   10.968018] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin(minor:0)
[   10.968038] /home/mark/download/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<5:5> initialized
[   11.477107] usb 11-1: USB disconnect, address 2
[   11.477257] mt2060 I2C write failed

```


Given that the only thing displayed on the tty was something related to lirc, and I did install that manually, I tried removing it completely before the suspend/resume, but there's no difference (apart from no lirc messages).

The link in my first post suggested editing /etc/default/acpi-support, which I dutifully did at the time (before the start of this thread).  That file follows, in case there's something significant there.  However I had the impression that this is ignored with pm-utils?

```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
#SAVE_VBE_STATE=true
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

```

---

### Post by bigtoedsloth on 2008-08-18
> **cdtech said:**
> Don't know if this will be of any help but try to run the suspend via command line:
```
sudo /etc/acpi/sleep.sh force
```
and see if the suspend works properly. This will bypass the pm-utils and narrow the troubleshooting.

This certainly did help.  Since the system was definitely up when the problem was hit I could put debugging "echo"s into the scripts in /etc/acpi/resume.d.  In particular I could print out the modules that were being modprobe'd.

My problem was ndiswrapper.  I installed it a while ago when I was playing around with wireless networking, but I don't need it any more.  Removing the package (and its reference in /etc/modules) and the problem is solved.

I've still got a couple of remaining issues (it seems as though my TV tuner isn't working after resume), but that's a topic for another thread.

Thanks for your help.

---

