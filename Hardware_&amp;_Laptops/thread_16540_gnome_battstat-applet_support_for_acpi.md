---
title: "gnome battstat-applet support for acpi"
date: 2005-02-22
forum: Hardware &amp; Laptops
---

### Post by praveen on 2005-02-22
hi there.. 

i read somewhere that gnome's battstat-applet does support ACPI-based laptops. however, mine isn't. i am running a pretty much upto-date hoary. 

all it does is recognize whether the laptop is hooked up to a power supply or not. battery status is not known.. but i can see ACPI itself working seemingly flawlessly with all of /proc/acpi/battery/info etc. intact. 

do i have to tweak something?

---

### Post by briguy on 2005-03-18
My battery monitor wasn't showing a charge until I updated the dsdt tables using initrd.  There was info in /proc/acpi/battery/BAT1/ but it was a bit mixed up, so the charge always showed very low.  Sounds like you'll have to fix your dsdt table.  Check out [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/) and search in this forum under "dsdt" and "initrd".

---

### Post by praveen on 2005-03-21
thanks for giving me a lead... 

i tried what was suggested about appending DSDT to initrd etc... I seem to be getting the messages that i can expect.. but the battstat applet still does not recognize the battery. I am appending the output of dmesg and /proc/acpi below. Can you tell me if the information on /proc/acpi is as expected? Is the info given sufficient for battstat applet to work? The only unknowns are some fields in .../info. 

```
praveen@ion:~ $ cat /proc/acpi/battery/CMB0/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mW
remaining capacity:      3660 mWh
present voltage:         16686 mV
praveen@ion:~ $ cat /proc/acpi/battery/CMB0/info
present:                 yes
design capacity:         unknown
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          unknown
design capacity warning: 800 mWh
design capacity low:     16 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            BAT1
serial number:           0000
battery type:            LION
OEM info:                COMPAQ


```

the dmesg output for ACPI looks like this: 

```

praveen@ion:~ $ dmesg | grep -i acpi
 BIOS-e820: 000000000ff60000 - 000000000ff6fc00 (ACPI data)
 BIOS-e820: 000000000ff6fc00 - 000000000ff80000 (ACPI NVS)
ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6420
ACPI: RSDT (v001 PTLTD           RSDT   0x06040000  LTP 0x00000000) @ 0x0ff69f76
ACPI: FADT (v001 COMPAQ CPQ2C01  0x06040000 PTL  0x00000001) @ 0x0ff6fb64
ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0ff6fbd8
ACPI: DSDT (v001 COMPAQ   U22C01 0x06040000 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
ACPI: Looking for DSDT in initrd... found (at offset 4407316)!
ACPI: Using customized DSDT
    ACPI-0294: *** Info: Table [DSDT] replaced by host OS
ACPI: setting ELCR to 0200 (from 0e20)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
ACPI: Embedded Controller [H8] (gpe 29)
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
ACPI wakeup devices:
ACPI: (supports S0 S1 S4 S5)
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Thermal Zone [TZ0] (27 C)
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 9 (level, low) -> IRQ 9
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:08.0[A] -> GSI 9 (level, low) -> IRQ 9
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [CMB0] (battery present)
ACPI: Lid Switch [LID]
ACPI: Power Button (CM) [PWRB]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
acpi-cpufreq: CPU0 - ACPI performance management activated.

```

---

