---
title: "ACPI problems on desktop machine - need help!"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by MoeGreene on 2005-04-26
I cannot get ACPI working properly on my desktop. In addition to my Hoary system I also have Windows 2000 installed on the computer, and in Windows everything ACPI related works beautifully; both standby and hibernate, and the machine always wakes up without any problems. So I really would like to get this working with Ubuntu as well. 

I've been reading up here on the forums and I've also been googling and testing different stuff without success. I think I've got it to suspend to ram (standby?) ok, but it doesn't wake up properly. Something definitely happens when I push the power button to initiate the wake up, but the screen remains blank and the system doesn't seem to react to any input. The motherboard is an Asus P4PE if that's relevant. 

If anyone has any hints or pointers I would really appreciate it. 
TIA!

---

### Post by alastair on 2005-04-26
Logs are usually relevant, sometimes interesting i.e. ACPI relevant messages from :

/var/log/syslog

There is also an ACPI log : /var/log/acpid

This log might help see ACPI events e.g. power buttons etc.

Also, note that ACPI has an "interface" under /proc/acpi/ and it might be worth poking around there to see if there is anything interesting.

---

### Post by MoeGreene on 2005-04-28
Thanks for your help. 

I've tried going to standby by using the Gnome logout dialog, by running /etc/acpi/sleep.sh and by echo 3 > /proc/acpi/sleep - all of these suspends my computer, but when I push the power button to wake up the screen remains blank. The monitor is turned on, I can hear the hard drive spinning up and the keyboard flashes its lights but that's it.

What should I look for in /proc/acpi/?

This is my /var/log/acpid:

```
[Mon Apr 25 22:53:29 2005] starting up
[Mon Apr 25 22:53:31 2005] 21 rules loaded
[Mon Apr 25 23:13:29 2005] received event "button/power PWRF 00000080 00000001"
[Mon Apr 25 23:13:29 2005] executing action "/etc/acpi/powerbtn.sh"
[Mon Apr 25 23:13:29 2005] BEGIN HANDLER MESSAGES
[Mon Apr 25 23:13:32 2005] END HANDLER MESSAGES
[Mon Apr 25 23:13:32 2005] action exited with status 0
[Mon Apr 25 23:13:32 2005] completed event "button/power PWRF 00000080 00000001"
[Mon Apr 25 23:14:04 2005] exiting
[Tue Apr 26 17:53:19 2005] starting up
[Tue Apr 26 17:53:19 2005] 21 rules loaded
[Tue Apr 26 18:36:09 2005] exiting
[Tue Apr 26 22:45:26 2005] starting up
[Tue Apr 26 22:45:27 2005] 21 rules loaded
[Tue Apr 26 23:58:23 2005] Lock file present, not processing event
[Wed Apr 27 20:26:43 2005] starting up
[Wed Apr 27 20:26:43 2005] 21 rules loaded
```

This is acpi related lines from /var/log/syslog:

```
Apr 28 23:04:04 localhost kernel:  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
Apr 28 23:04:04 localhost kernel:  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
Apr 28 23:04:04 localhost kernel: ACPI: RSDP (v000 ASUS                                  ) @ 0x000f52e0
Apr 28 23:04:04 localhost kernel: ACPI: RSDT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec000
Apr 28 23:04:04 localhost kernel: ACPI: FADT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec0c0
Apr 28 23:04:04 localhost kernel: ACPI: BOOT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec030
Apr 28 23:04:04 localhost kernel: ACPI: MADT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec058
Apr 28 23:04:04 localhost kernel: ACPI: DSDT (v001   ASUS P4PE     0x00001000 MSFT 0x0100000b) @ 0x00000000
Apr 28 23:04:04 localhost kernel: ACPI: PM-Timer IO Port: 0xe408
Apr 28 23:04:04 localhost kernel: ACPI: Local APIC address 0xfee00000
Apr 28 23:04:04 localhost kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 28 23:04:04 localhost kernel: ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 28 23:04:04 localhost kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 28 23:04:04 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
Apr 28 23:04:04 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 22 low level)
Apr 28 23:04:04 localhost kernel: ACPI: IRQ0 used by override.
Apr 28 23:04:04 localhost kernel: ACPI: IRQ2 used by override.
Apr 28 23:04:04 localhost kernel: Using ACPI (MADT) for SMP configuration information
Apr 28 23:04:04 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
Apr 28 23:04:04 localhost kernel: ACPI: Subsystem revision 20050211
Apr 28 23:04:04 localhost kernel: ACPI: Interpreter enabled
Apr 28 23:04:04 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr 28 23:04:04 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Apr 28 23:04:04 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Apr 28 23:04:04 localhost kernel: pnp: PnP ACPI init
Apr 28 23:04:04 localhost kernel: pnp: PnP ACPI: found 14 devices
Apr 28 23:04:04 localhost kernel: PnPBIOS: Disabled by ACPI PNP
Apr 28 23:04:04 localhost kernel: PCI: Using ACPI for IRQ routing
Apr 28 23:04:04 localhost kernel: ACPI wakeup devices: 
Apr 28 23:04:04 localhost kernel: ACPI: (supports S0 S1 S3 S4 S5)
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 28 23:04:04 localhost kernel: shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 28 23:04:04 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
Apr 28 23:04:04 localhost kernel: pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 28 23:04:04 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
Apr 28 23:04:04 localhost kernel: shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 28 23:04:04 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
Apr 28 23:04:04 localhost kernel: pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 28 23:04:04 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 23
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
Apr 28 23:04:04 localhost kernel: ACPI: PCI interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 21
Apr 28 23:04:05 localhost kernel: ACPI: Power Button (FF) [PWRF]
Apr 28 23:04:05 localhost kernel: ibm_acpi: ec object not found
Apr 29 00:35:38 localhost kernel:  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
Apr 29 00:35:38 localhost kernel:  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
Apr 29 00:35:38 localhost kernel: ACPI: RSDP (v000 ASUS                                  ) @ 0x000f52e0
Apr 29 00:35:38 localhost kernel: ACPI: RSDT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec000
Apr 29 00:35:38 localhost kernel: ACPI: FADT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec0c0
Apr 29 00:35:38 localhost kernel: ACPI: BOOT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec030
Apr 29 00:35:38 localhost kernel: ACPI: MADT (v001 ASUS   P4PE     0x42302e31 MSFT 0x31313031) @ 0x1ffec058
Apr 29 00:35:38 localhost kernel: ACPI: DSDT (v001   ASUS P4PE     0x00001000 MSFT 0x0100000b) @ 0x00000000
Apr 29 00:35:38 localhost kernel: ACPI: PM-Timer IO Port: 0xe408
Apr 29 00:35:38 localhost kernel: ACPI: Local APIC address 0xfee00000
Apr 29 00:35:38 localhost kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 29 00:35:38 localhost kernel: ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 29 00:35:38 localhost kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 29 00:35:38 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
Apr 29 00:35:38 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 22 low level)
Apr 29 00:35:38 localhost kernel: ACPI: IRQ0 used by override.
Apr 29 00:35:38 localhost kernel: ACPI: IRQ2 used by override.
Apr 29 00:35:38 localhost kernel: Using ACPI (MADT) for SMP configuration information
Apr 29 00:35:38 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
Apr 29 00:35:38 localhost kernel: ACPI: Subsystem revision 20050211
Apr 29 00:35:38 localhost kernel: ACPI: Interpreter enabled
Apr 29 00:35:38 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr 29 00:35:38 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Apr 29 00:35:38 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Apr 29 00:35:38 localhost kernel: pnp: PnP ACPI init
Apr 29 00:35:38 localhost kernel: pnp: PnP ACPI: found 14 devices
Apr 29 00:35:38 localhost kernel: PnPBIOS: Disabled by ACPI PNP
Apr 29 00:35:38 localhost kernel: PCI: Using ACPI for IRQ routing
Apr 29 00:35:38 localhost kernel: ACPI wakeup devices: 
Apr 29 00:35:38 localhost kernel: ACPI: (supports S0 S1 S3 S4 S5)
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 29 00:35:38 localhost kernel: shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 29 00:35:38 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
Apr 29 00:35:38 localhost kernel: pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 29 00:35:38 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
Apr 29 00:35:38 localhost kernel: shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 29 00:35:38 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
Apr 29 00:35:38 localhost kernel: pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 29 00:35:38 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 23
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
Apr 29 00:35:38 localhost kernel: ACPI: PCI interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 21
Apr 29 00:35:40 localhost kernel: ACPI: Power Button (FF) [PWRF]
Apr 29 00:35:40 localhost kernel: ibm_acpi: ec object not found

```

---

### Post by alastair on 2005-04-28
I don't have a Ubuntu machine handy at the moment to look, but you might just have bad interaction between ACPI and your X driver. What X driver do you have? ("Driver" in /etc/X11/xorg.conf). As an example, I think ATI's "fglrx" driver has some problems (for some people) in using suspend - if you use this (or "nvidia") - see if the Xorg driver behaves better (e.g. "ati", or "nv" - or even "vesa").

I think there is a config file/files for "suspend" (look at the file perhaps) that allows you to unload/load certain modules before/after the suspend process as well.

Hope some of that helps.

There is nothing obviously wrong in your logs.

---

### Post by MoeGreene on 2005-05-01
[QUOTE=alastair]I don't have a Ubuntu machine handy at the moment to look, but you might just have bad interaction between ACPI and your X driver. What X driver do you have? ("Driver" in /etc/X11/xorg.conf). ... I think there is a config file/files for "suspend" (look at the file perhaps) that allows you to unload/load certain modules before/after the suspend process as well.[/QUOTE]
I use nvidia, and I tried adding "nvidia" to the MODULES variable in /etc/default/acpi-support:
```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. It should look something like MODULES="e1000 ipw2100"
MODULES="nvidia"
```
/etc/acpi/resume.sh:
```
# Load any drivers that we removed
for x in $MODULES; do
    modprobe $x;
done
```
The question is - is resume.sh executed when I press the power button to wake the system up?

Anyway, it doesn't seem to make any difference. I also tried booting the kernel with " acpi_sleep=s3_bios" - again no difference. 

I'll keep looking for solutions, thanks for your time - I understand that this is difficult to get to work but it's so frustrating since Windows handles it so smoothly...

---

### Post by alastair on 2005-05-01
See if the "nv" X driver makes a difference perhaps.

ACPI is really painful sometimes - because it is really complex. Microsoft and partners have a lot more resources (money,people) to put into getting things working.

The other thing you could try is building your own kernel e.g. the very latest available. Perhaps patched (if necesary) with the latest ACPI patches. Things do more forwards generally, and if you get some progress you know if will (eventually) appear in Ubuntu's kernel.

---

