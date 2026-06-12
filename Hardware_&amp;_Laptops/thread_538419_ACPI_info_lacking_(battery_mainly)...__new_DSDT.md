---
title: "ACPI info lacking (battery mainly)...  new DSDT??"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by ktulu1115 on 2007-08-30
Ok-

So I installed Xubuntu Gutsy on my Dell L400 laptop and loving it so far.  Small problem though, it's missing battery charge & current power status information.  Also my system temperature stays at 50 C regardless of load.

Battery not detected in Device Manager (HAL->Battery Bay->Advanced->battery.present = false)

Dump of everything I can think of (I'm willing to bet it's DSDT related):

```
ktulu@orion:~$ ibam -a
Bios:                       100 %
Battery percentage:         100 %
Charge percentage:          100 %
Bios:                        2:00:00
Battery time left:           2:00:00
Adapted battery time left:   2:00:00
Charge time left:            0:00:00
Adapted charge time left:    0:00:00
Total battery time:          2:00:00
Adapted total battery time:  2:00:00
Total charge time:           2:00:00
Adapted total charge time:   2:00:00
Profile logging enabled.
Current file: /home/ktulu/.ibam/profile-000-full

ktulu@orion:~$ acpi -V
     Thermal 1: ok, 50.0 degrees C                     # Always stays at 50 regardless of load
  AC Adapter 1: on-line

ktulu@orion:~$ grep -i ACPI /var/log/messages
Aug 22 23:06:37 orion kernel: [    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
Aug 22 23:06:37 orion kernel: [    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
Aug 22 23:06:37 orion kernel: [    0.000000] ACPI: RSDP 000F6F60, 0014 (r0 PTLTD )
Aug 22 23:06:37 orion kernel: [    0.000000] ACPI: RSDT 0FFFC495, 002C (r1 DELL   ATLAS II 20010920  LTP        0)
Aug 22 23:06:37 orion kernel: [    0.000000] ACPI: FACP 0FFFFB65, 0074 (r1 DELL   Atlas II 20010920 PTL     F4240)
Aug 22 23:06:37 orion kernel: [    0.000000] ACPI: DSDT 0FFFC4C1, 36A4 (r1    PTL    BX-TJ 20010920 MSFT  1000007)
Aug 22 23:06:37 orion kernel: [    0.000000] ACPI: FACS 0FFFFFC0, 0040
Aug 22 23:06:37 orion kernel: [    0.000000] ACPI: BOOT 0FFFFBD9, 0027 (r1 PTLTD  $SBFTBL$ 20010920  LTP        1)
Aug 22 23:06:37 orion kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Aug 22 23:06:37 orion kernel: [ 7712.860376] ACPI: Core revision 20070126
Aug 22 23:06:37 orion kernel: [ 7712.860632] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 22 23:06:37 orion kernel: [ 7712.864864] ACPI: setting ELCR to 0200 (from 0e08)
Aug 22 23:06:37 orion kernel: [ 7712.875805] ACPI: bus type pci registered
Aug 22 23:06:37 orion kernel: [ 7712.914751] ACPI: EC: GPE=0x00, ports=0x66, 0x62
Aug 22 23:06:37 orion kernel: [ 7712.918324] ACPI: Interpreter enabled
Aug 22 23:06:37 orion kernel: [ 7712.918333] ACPI: (supports S0 S3 S4 S5)
Aug 22 23:06:37 orion kernel: [ 7712.918374] ACPI: Using PIC for interrupt routing
Aug 22 23:06:37 orion kernel: [ 7712.963856] ACPI: Device [FDDA] status [00000008]: functional but not present; setting present
Aug 22 23:06:37 orion kernel: [ 7712.966390] ACPI: Device [CDRM] status [00000008]: functional but not present; setting present
Aug 22 23:06:37 orion kernel: [ 7712.971267] ACPI: EC: GPE=0x00, ports=0x66, 0x62
Aug 22 23:06:37 orion kernel: [ 7712.971406] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 22 23:06:37 orion kernel: [ 7712.971904] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
Aug 22 23:06:37 orion kernel: [ 7712.975536] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Aug 22 23:06:37 orion kernel: [ 7712.975837] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Aug 22 23:06:37 orion kernel: [ 7712.976102] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 14 15)
Aug 22 23:06:37 orion kernel: [ 7712.976356] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Aug 22 23:06:37 orion kernel: [ 7712.976738] ACPI: Power Resource [PFN0] (off)
Aug 22 23:06:37 orion kernel: [ 7712.976822] ACPI: Power Resource [PFN1] (off)
Aug 22 23:06:37 orion kernel: [ 7712.976872] pnp: PnP ACPI init
Aug 22 23:06:37 orion kernel: [ 7712.976901] ACPI: bus type pnp registered
Aug 22 23:06:37 orion kernel: [ 7713.051498] pnp: PnP ACPI: found 12 devices
Aug 22 23:06:37 orion kernel: [ 7713.051508] ACPI: ACPI bus type pnp unregistered
Aug 22 23:06:37 orion kernel: [ 7713.051520] PnPBIOS: Disabled by ACPI PNP
Aug 22 23:06:37 orion kernel: [ 7713.051696] PCI: Using ACPI for IRQ routing
Aug 22 23:06:37 orion kernel: [ 7713.085526] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Aug 22 23:06:37 orion kernel: [ 7713.085544] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Aug 22 23:06:37 orion kernel: [ 7717.173354] ACPI: Transitioning device [FAN0] to D3
Aug 22 23:06:37 orion kernel: [ 7717.173366] ACPI: Transitioning device [FAN0] to D3
Aug 22 23:06:37 orion kernel: [ 7717.173377] ACPI: Fan [FAN0] (off)
Aug 22 23:06:37 orion kernel: [ 7717.173516] ACPI: Transitioning device [FAN1] to D3
Aug 22 23:06:37 orion kernel: [ 7717.173523] ACPI: Transitioning device [FAN1] to D3
Aug 22 23:06:37 orion kernel: [ 7717.173533] ACPI: Fan [FAN1] (off)
Aug 22 23:06:37 orion kernel: [ 7717.189117] ACPI: CPU0 (power states: C1[C1] C2[C2])
Aug 22 23:06:37 orion kernel: [ 7717.189133] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 22 23:06:37 orion kernel: [ 7717.193196] ACPI: Thermal Zone [THRM] (50 C)
Aug 22 23:06:37 orion kernel: [   10.300000] Time: acpi_pm clocksource has been installed.
Aug 22 23:06:37 orion kernel: [   10.396000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Aug 22 23:06:37 orion kernel: [   10.396000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug 22 23:06:37 orion kernel: [   10.428000]  sda:<6>ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Aug 22 23:06:37 orion kernel: [   34.312000] parport_pc 00:07: reported by Plug and Play ACPI
Aug 22 23:06:37 orion kernel: [   35.148000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
Aug 22 23:06:37 orion kernel: [   35.148000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Aug 22 23:06:37 orion kernel: [   40.764000] ACPI: Power Button (FF) [PWRF]
Aug 22 23:06:37 orion kernel: [   40.808000] ACPI: Lid Switch [LID]
Aug 22 23:06:37 orion kernel: [   40.832000] ACPI: Sleep Button (CM) [SBTN]
Aug 22 23:06:37 orion kernel: [   41.212000] ACPI: Battery Slot [BAT1] (battery absent)
Aug 22 23:06:37 orion kernel: [   41.452000] ACPI: AC Adapter [ACAD] (on-line)
Aug 22 23:06:41 orion kernel: [   46.784000] apm: overridden by ACPI.
Aug 23 09:14:43 orion kernel: [36150.116000] ACPI: PCI interrupt for device 0000:00:08.0 disabled
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: PCI interrupt for device 0000:00:07.2 disabled
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: Transitioning device [FAN1] to D0
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: Transitioning device [FAN1] to D0
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: Transitioning device [FAN0] to D0
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: Transitioning device [FAN0] to D0
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: Transitioning device [FAN0] to D3
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: Transitioning device [FAN0] to D3
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: Transitioning device [FAN1] to D3
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: Transitioning device [FAN1] to D3
Aug 23 09:14:43 orion kernel: [36150.132000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug 23 09:14:43 orion kernel: [36150.148000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Aug 23 09:14:43 orion kernel: [36150.844000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Aug 23 09:15:02 orion kernel: [36174.896000] ACPI: Power Button (FF) [PWRF]
Aug 23 09:15:02 orion kernel: [36174.896000] ACPI: Lid Switch [LID]
Aug 23 09:15:02 orion kernel: [36174.896000] ACPI: Sleep Button (CM) [SBTN]
Aug 23 09:15:04 orion kernel: [36176.280000] ACPI: Transitioning device [FAN0] to D3
Aug 23 09:15:04 orion kernel: [36176.280000] ACPI: Transitioning device [FAN0] to D3
Aug 23 09:15:04 orion kernel: [36176.280000] ACPI: Fan [FAN0] (off)
Aug 23 09:15:04 orion kernel: [36176.280000] ACPI: Transitioning device [FAN1] to D3
Aug 23 09:15:04 orion kernel: [36176.280000] ACPI: Transitioning device [FAN1] to D3
Aug 23 09:15:04 orion kernel: [36176.280000] ACPI: Fan [FAN1] (off)
Aug 23 09:15:04 orion kernel: [36176.672000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Aug 23 09:15:04 orion kernel: [36176.672000] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 23 09:15:04 orion kernel: [36176.988000] ACPI: Thermal Zone [THRM] (50 C)
Aug 23 09:15:05 orion kernel: [36177.548000] ACPI: AC Adapter [ACAD] (on-line)
Aug 23 09:15:05 orion kernel: [36177.784000] ACPI: Battery Slot [BAT1] (battery absent)
Aug 23 22:35:41 orion kernel: [    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
Aug 23 22:35:41 orion kernel: [    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
Aug 23 22:35:41 orion kernel: [    0.000000] ACPI: RSDP 000F6F60, 0014 (r0 PTLTD )
Aug 23 22:35:41 orion kernel: [    0.000000] ACPI: RSDT 0FFFC495, 002C (r1 DELL   ATLAS II 20010920  LTP        0)
Aug 23 22:35:41 orion kernel: [    0.000000] ACPI: FACP 0FFFFB65, 0074 (r1 DELL   Atlas II 20010920 PTL     F4240)
Aug 23 22:35:41 orion kernel: [    0.000000] ACPI: DSDT 0FFFC4C1, 36A4 (r1    PTL    BX-TJ 20010920 MSFT  1000007)
Aug 23 22:35:41 orion kernel: [    0.000000] ACPI: FACS 0FFFFFC0, 0040
Aug 23 22:35:41 orion kernel: [    0.000000] ACPI: BOOT 0FFFFBD9, 0027 (r1 PTLTD  $SBFTBL$ 20010920  LTP        1)
Aug 23 22:35:41 orion kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Aug 23 22:35:41 orion kernel: [18078.059170] ACPI: Core revision 20070126
Aug 23 22:35:41 orion kernel: [18078.059428] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 23 22:35:41 orion kernel: [18078.063664] ACPI: setting ELCR to 0200 (from 0e08)
Aug 23 22:35:41 orion kernel: [18078.076653] ACPI: bus type pci registered
Aug 23 22:35:41 orion kernel: [18078.115610] ACPI: EC: GPE=0x00, ports=0x66, 0x62
Aug 23 22:35:41 orion kernel: [18078.121175] ACPI: Interpreter enabled
Aug 23 22:35:41 orion kernel: [18078.121184] ACPI: (supports S0 S3 S4 S5)
Aug 23 22:35:41 orion kernel: [18078.121225] ACPI: Using PIC for interrupt routing
Aug 23 22:35:41 orion kernel: [18078.166714] ACPI: Device [FDDA] status [00000008]: functional but not present; setting present
Aug 23 22:35:41 orion kernel: [18078.169246] ACPI: Device [CDRM] status [00000008]: functional but not present; setting present
Aug 23 22:35:41 orion kernel: [18078.174134] ACPI: EC: GPE=0x00, ports=0x66, 0x62
Aug 23 22:35:41 orion kernel: [18078.174310] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 23 22:35:41 orion kernel: [18078.174775] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
Aug 23 22:35:41 orion kernel: [18078.178432] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Aug 23 22:35:41 orion kernel: [18078.178704] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Aug 23 22:35:41 orion kernel: [18078.178969] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 14 15)
Aug 23 22:35:41 orion kernel: [18078.179224] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Aug 23 22:35:41 orion kernel: [18078.179603] ACPI: Power Resource [PFN0] (off)
Aug 23 22:35:41 orion kernel: [18078.179689] ACPI: Power Resource [PFN1] (off)
Aug 23 22:35:41 orion kernel: [18078.179739] pnp: PnP ACPI init
Aug 23 22:35:41 orion kernel: [18078.179768] ACPI: bus type pnp registered
Aug 23 22:35:41 orion kernel: [18078.254404] pnp: PnP ACPI: found 12 devices
Aug 23 22:35:41 orion kernel: [18078.254414] ACPI: ACPI bus type pnp unregistered
Aug 23 22:35:41 orion kernel: [18078.254427] PnPBIOS: Disabled by ACPI PNP
Aug 23 22:35:41 orion kernel: [18078.254588] PCI: Using ACPI for IRQ routing
Aug 23 22:35:41 orion kernel: [18078.288418] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Aug 23 22:35:41 orion kernel: [18078.288436] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Aug 23 22:35:41 orion kernel: [18082.379975] ACPI: Transitioning device [FAN0] to D3
Aug 23 22:35:41 orion kernel: [18082.379986] ACPI: Transitioning device [FAN0] to D3
Aug 23 22:35:41 orion kernel: [18082.379997] ACPI: Fan [FAN0] (off)
Aug 23 22:35:41 orion kernel: [18082.380136] ACPI: Transitioning device [FAN1] to D3
Aug 23 22:35:41 orion kernel: [18082.380144] ACPI: Transitioning device [FAN1] to D3
Aug 23 22:35:41 orion kernel: [18082.380153] ACPI: Fan [FAN1] (off)
Aug 23 22:35:41 orion kernel: [18082.395610] ACPI: CPU0 (power states: C1[C1] C2[C2])
Aug 23 22:35:41 orion kernel: [18082.395626] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 23 22:35:41 orion kernel: [18082.399696] ACPI: Thermal Zone [THRM] (50 C)
Aug 23 22:35:41 orion kernel: [   10.328000] Time: acpi_pm clocksource has been installed.
Aug 23 22:35:41 orion kernel: [   10.404000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Aug 23 22:35:41 orion kernel: [   10.404000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug 23 22:35:41 orion kernel: [   10.436000]  sda:<6>ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Aug 23 22:35:41 orion kernel: [   34.828000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
Aug 23 22:35:41 orion kernel: [   34.828000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Aug 23 22:35:41 orion kernel: [   34.852000] parport_pc 00:07: reported by Plug and Play ACPI
Aug 23 22:35:41 orion kernel: [   41.496000] ACPI: Power Button (FF) [PWRF]
Aug 23 22:35:41 orion kernel: [   41.540000] ACPI: Lid Switch [LID]
Aug 23 22:35:41 orion kernel: [   41.564000] ACPI: Sleep Button (CM) [SBTN]
Aug 23 22:35:41 orion kernel: [   41.928000] ACPI: Battery Slot [BAT1] (battery absent)
Aug 23 22:35:41 orion kernel: [   42.172000] ACPI: AC Adapter [ACAD] (on-line)
Aug 23 22:35:44 orion kernel: [   47.304000] apm: overridden by ACPI.
Aug 24 12:56:17 orion kernel: [    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
Aug 24 12:56:17 orion kernel: [    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
Aug 24 12:56:17 orion kernel: [    0.000000] ACPI: RSDP 000F6F60, 0014 (r0 PTLTD )
Aug 24 12:56:17 orion kernel: [    0.000000] ACPI: RSDT 0FFFC495, 002C (r1 DELL   ATLAS II 20010920  LTP        0)
Aug 24 12:56:17 orion kernel: [    0.000000] ACPI: FACP 0FFFFB65, 0074 (r1 DELL   Atlas II 20010920 PTL     F4240)
Aug 24 12:56:17 orion kernel: [    0.000000] ACPI: DSDT 0FFFC4C1, 36A4 (r1    PTL    BX-TJ 20010920 MSFT  1000007)
Aug 24 12:56:17 orion kernel: [    0.000000] ACPI: FACS 0FFFFFC0, 0040
Aug 24 12:56:17 orion kernel: [    0.000000] ACPI: BOOT 0FFFFBD9, 0027 (r1 PTLTD  $SBFTBL$ 20010920  LTP        1)
Aug 24 12:56:17 orion kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Aug 24 12:56:17 orion kernel: [   14.998894] ACPI: Core revision 20070126
Aug 24 12:56:17 orion kernel: [   14.999148] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 24 12:56:17 orion kernel: [   15.003378] ACPI: setting ELCR to 0200 (from 0c08)
Aug 24 12:56:17 orion kernel: [   15.020283] ACPI: bus type pci registered
Aug 24 12:56:17 orion kernel: [   15.059244] ACPI: EC: GPE=0x00, ports=0x66, 0x62
Aug 24 12:56:17 orion kernel: [   15.062810] ACPI: Interpreter enabled
Aug 24 12:56:17 orion kernel: [   15.062819] ACPI: (supports S0 S3 S4 S5)
Aug 24 12:56:17 orion kernel: [   15.062860] ACPI: Using PIC for interrupt routing
Aug 24 12:56:17 orion kernel: [   15.108326] ACPI: Device [FDDA] status [00000008]: functional but not present; setting present
Aug 24 12:56:17 orion kernel: [   15.110889] ACPI: Device [CDRM] status [00000008]: functional but not present; setting present
Aug 24 12:56:17 orion kernel: [   15.115779] ACPI: EC: GPE=0x00, ports=0x66, 0x62
Aug 24 12:56:17 orion kernel: [   15.115918] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 24 12:56:17 orion kernel: [   15.116382] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
Aug 24 12:56:17 orion kernel: [   15.120042] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Aug 24 12:56:17 orion kernel: [   15.120314] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Aug 24 12:56:17 orion kernel: [   15.120579] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 14 15)
Aug 24 12:56:17 orion kernel: [   15.120834] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Aug 24 12:56:17 orion kernel: [   15.121202] ACPI: Power Resource [PFN0] (off)
Aug 24 12:56:17 orion kernel: [   15.121286] ACPI: Power Resource [PFN1] (off)
Aug 24 12:56:17 orion kernel: [   15.121337] pnp: PnP ACPI init
Aug 24 12:56:17 orion kernel: [   15.121365] ACPI: bus type pnp registered
Aug 24 12:56:17 orion kernel: [   15.195983] pnp: PnP ACPI: found 12 devices
Aug 24 12:56:17 orion kernel: [   15.195993] ACPI: ACPI bus type pnp unregistered
Aug 24 12:56:17 orion kernel: [   15.196005] PnPBIOS: Disabled by ACPI PNP
Aug 24 12:56:17 orion kernel: [   15.196162] PCI: Using ACPI for IRQ routing
Aug 24 12:56:17 orion kernel: [   15.230012] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Aug 24 12:56:17 orion kernel: [   15.230030] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Aug 24 12:56:17 orion kernel: [   19.283678] ACPI: Transitioning device [FAN0] to D3
Aug 24 12:56:17 orion kernel: [   19.283690] ACPI: Transitioning device [FAN0] to D3
Aug 24 12:56:17 orion kernel: [   19.283701] ACPI: Fan [FAN0] (off)
Aug 24 12:56:17 orion kernel: [   19.283840] ACPI: Transitioning device [FAN1] to D3
Aug 24 12:56:17 orion kernel: [   19.283847] ACPI: Transitioning device [FAN1] to D3
Aug 24 12:56:17 orion kernel: [   19.283856] ACPI: Fan [FAN1] (off)
Aug 24 12:56:17 orion kernel: [   19.299415] ACPI: CPU0 (power states: C1[C1] C2[C2])
Aug 24 12:56:17 orion kernel: [   19.299431] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 24 12:56:17 orion kernel: [   19.303485] ACPI: Thermal Zone [THRM] (50 C)
Aug 24 12:56:17 orion kernel: [   10.268000] Time: acpi_pm clocksource has been installed.
Aug 24 12:56:17 orion kernel: [   10.400000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Aug 24 12:56:17 orion kernel: [   10.400000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug 24 12:56:17 orion kernel: [   10.432000]  sda:<6>ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Aug 24 12:56:17 orion kernel: [   35.620000] parport_pc 00:07: reported by Plug and Play ACPI
Aug 24 12:56:17 orion kernel: [   35.808000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
Aug 24 12:56:17 orion kernel: [   35.808000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Aug 24 12:56:17 orion kernel: [   43.812000] ACPI: Power Button (FF) [PWRF]
Aug 24 12:56:17 orion kernel: [   43.856000] ACPI: Lid Switch [LID]
Aug 24 12:56:17 orion kernel: [   43.880000] ACPI: Sleep Button (CM) [SBTN]
Aug 24 12:56:17 orion kernel: [   44.296000] ACPI: Battery Slot [BAT1] (battery absent)
Aug 24 12:56:17 orion kernel: [   44.544000] ACPI: AC Adapter [ACAD] (on-line)
Aug 24 12:56:20 orion kernel: [   49.664000] apm: overridden by ACPI.

ktulu@orion:~$ cat /proc/acpi/info
version:                 20070126
ktulu@orion:~$ cat /proc/acpi/sleep
S0 S3 S4 S5
ktulu@orion:~$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PCI0      S3     disabled  no-bus:pci0000:00
COMA      S3     disabled  pnp:00:08
CRD0      S3     disabled  pci:0000:00:0a.0
MDEM      S3     disabled  pci:0000:00:10.0
LID       S4    *enabled   
ktulu@orion:~$ cat /proc/acpi/alarm
2007-08-00 17:21:22
ktulu@orion:/proc/acpi/battery/BAT1$ cat alarm
present:                 no
ktulu@orion:/proc/acpi/battery/BAT1$ cat info
present:                 no
ktulu@orion:/proc/acpi/battery/BAT1$ cat state
present:                 no
ktulu@orion:/proc/acpi/thermal_zone/THRM$ cat state
state:                   ok
ktulu@orion:/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             50 C
ktulu@orion:/proc/acpi/thermal_zone/THRM$ cat trip_points
critical (S5):           99 C
passive:                 90 C: tc1=2 tc2=3 tsp=40 devices=CPU0
active[0]:               80 C: devices=FAN1
active[1]:               65 C: devices=FAN0

ktulu@orion:/proc/acpi$ uname -a
Linux orion 2.6.22-10-generic #1 SMP Wed Aug 22 08:11:52 GMT 2007 i686 GNU/Linux
```

Followed this HOWTO - [http://www.columbia.edu/~ariel/acpi/acpi_howto.txt:](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt:)

```
ktulu@orion:~$ sudo acpidump > acpidump.out
ktulu@orion:~$ acpixtract -a acpidump.out
Acpi table [DSDT] -  13988 bytes written to DSDT.dat
Acpi table [FACS] -     64 bytes written to FACS.dat
Acpi table [FACP] -    116 bytes written to FACP.dat
Acpi table [BOOT] -     39 bytes written to BOOT.dat
Acpi table [RSDT] -     44 bytes written to RSDT.dat
Acpi table [RSDP] -     20 bytes written to RSDP.dat
ktulu@orion:~$ iasl -d DSDT.dat

Intel ACPI Component Architecture
AML Disassembler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file DSDT.dat
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
...........................................................................................................................................................................................
Parsing completed
Disassembly completed, written to "DSDT.dsl"
ktulu@orion:~$ iasl -tc DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

DSDT.dsl   299:     Method (_WAK, 1, NotSerialized)
Warning  1079 -                ^ Reserved method must return a value (_WAK)

DSDT.dsl  2225:                         Method (_RMV, 1, NotSerialized)
Warning  1075 -                                    ^ Reserved method has too many arguments (_RMV requires 0)

DSDT.dsl  2225:                         Method (_RMV, 1, NotSerialized)
Warning  1079 -                                    ^ Reserved method must return a value (_RMV)

ASL Input:  DSDT.dsl - 3078 lines, 103633 bytes, 1468 keywords
AML Output: DSDT.aml - 12423 bytes 375 named objects 1093 executable opcodes

Compilation complete. 0 Errors, 3 Warnings, 0 Remarks, 392 Optimizations

ktulu@orion:~$ iasl -d BOOT.dat

Intel ACPI Component Architecture
AML Disassembler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file BOOT.dat
Acpi Data Table [BOOT] decoded, written to "BOOT.dsl"
ktulu@orion:~$ iasl -d RSDP.dat

Intel ACPI Component Architecture
AML Disassembler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file RSDP.dat
Acpi Data Table [RSD ] decoded, written to "RSDP.dsl"
ktulu@orion:~$ iasl -d RSDT.dat

Intel ACPI Component Architecture
AML Disassembler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file RSDT.dat
Acpi Data Table [RSDT] decoded, written to "RSDT.dsl"

ktulu@orion:~$ iasl -tc BOOT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

BOOT.dsl    12: [000
Error    4094 - ^ Invalid character (0x5B), expecting ASL keyword or name

BOOT.dsl    12: [000
Error    4094 -    ^ syntax error, unexpected PARSEOP_INTEGER, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  BOOT.dsl - 13 lines, 246 bytes, 0 keywords
Compilation complete. 2 Errors, 0 Warnings, 0 Remarks, 0 Optimizations
ktulu@orion:~$ iasl -tc RSDP.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

RSDP.dsl    12: [000
Error    4094 - ^ Invalid character (0x5B), expecting ASL keyword or name

RSDP.dsl    12: [000
Error    4094 -    ^ syntax error, unexpected PARSEOP_INTEGER, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  RSDP.dsl - 13 lines, 246 bytes, 0 keywords
Compilation complete. 2 Errors, 0 Warnings, 0 Remarks, 0 Optimizations
ktulu@orion:~$ iasl -tc RSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

RSDT.dsl    12: [000
Error    4094 - ^ Invalid character (0x5B), expecting ASL keyword or name

RSDT.dsl    12: [000
Error    4094 -    ^ syntax error, unexpected PARSEOP_INTEGER, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  RSDT.dsl - 13 lines, 246 bytes, 0 keywords
Compilation complete. 2 Errors, 0 Warnings, 0 Remarks, 0 Optimizations
```

Any help would be greatly appreciated. :)

---

### Post by jfdarv on 2007-10-23
Hi, your how-to leads to nothing:

> The requested URL was not found on this web server:
    /~ariel/acpi/acpi_howto.txt

Maybe you should try this howto: [http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

There are 2 images for the Latitude L400 on this page: [http://acpi.sourceforge.net/dsdt/view.php?manufacturer=Dell&name=Latitude+L400](http://acpi.sourceforge.net/dsdt/view.php?manufacturer=Dell&name=Latitude+L400)

The custom one compiles fine but the kernel doesn't boot after repacking initrd.

BTW, what BIOS version do you have... I was thinking to try all the BIOS.

If you have any success, let me know!

---

### Post by jfdarv on 2007-10-23
```
$ dmesg | grep DSDT
[    0.000000] ACPI: DSDT 0FFFC4F0, 3675 (r1    PTL    BX-TJ 20010709 MSFT  1000007)
[   18.885767] ACPI: Looking for DSDT in initramfs... successfully read 12394 bytes from /DSDT.aml.
[   18.885979] ACPI: Table DSDT replaced by host OS
[   18.886099] ACPI: DSDT 00000000, 306A (r1    PTL    BX-TJ 20010709 INTL 20061109)
[   18.922427] ACPI: EC: Look up EC in DSDT

$ cat /proc/acpi/battery/BAT1/state
present:                 no
```

I managed to recompile and load a working DSDT.aml but the battery problem isn't solved...

---

### Post by walopower on 2007-11-11
Same thing in my Gutsy+L400.
Bios A09+compiled DSDT.
With 6.20.16 kernel still work.

---

### Post by alanmzifa on 2008-01-25
Any solution to this yet?

---

### Post by walopower on 2008-01-25
> **walopower said:**
> Same thing in my Gutsy+L400.
Bios A09+compiled DSDT.
With 6.20.16 kernel still work.
Bios A03 make no differense, but cooling fan working little better.

---

### Post by ktulu1115 on 2008-01-25
Didn't find any solution yet.  Have A07 BIOS on my machine.  I've just been booting with 'acpi=off' kernel option to at least get CPU fan throttling working.  I'd prefer not to have a melted lump of plastic on my desk. :)

---

### Post by Arch2 on 2008-01-27
I had the same problem, then I found these bug reports. 

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/127773](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/127773)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/127772](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/127772)

I went back to 7.04 since it looks like theres no fix for this yet.

---

