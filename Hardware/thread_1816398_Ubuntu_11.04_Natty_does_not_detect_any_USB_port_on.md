---
title: "Ubuntu 11.04 Natty does not detect any USB port on Dell Inspiron 1546"
date: 2011-08-01
forum: Hardware
---

### Post by AlterMind on 2011-08-01
Hello all,

I installed Ubuntu 11.04 Natty Narwhal from LiveCD on a Dell Inspiron 1546 laptop, where Windows 7 was already installed and working fine but is now shrunk.

The Ubuntu boot process (i.e. as from the GRUB menu selection) until the first purple screen appears (with the red dots) takes about a huge 30 seconds and once loaded I can't use ANY device on ANY of the 3 USB ports. This includes the mouse, memory sticks or external hard disks.

When looking into the "dmesg" file in the system journals application, I could see the following sections were the timestamp show significant gaps:

```
[    0.485943] NET: Registered protocol family 1
[    0.545924] Freeing initrd memory: 12552k freed
[COLOR=Red][    1.284254][/COLOR] pci 0000:00:**12.0**: OHCI: [COLOR=Red]BIOS handoff failed (BIOS bug?[/COLOR]) ffffffff
[COLOR=Red][    2.084253][/COLOR] pci 0000:00:**12.1**: OHCI: [COLOR=Red]BIOS handoff failed (BIOS bug?[/COLOR]) ffffffff
[    2.084275] pci 0000:00:**12.2**: EHCI: unrecognized capability 28
[    2.084278] pci 0000:00:12.2: EHCI: unrecognized capability 28
[    2.084280] pci 0000:00:12.2: EHCI: unrecognized capability 28
... this line repeated about 50 times)...
[    2.084437] pci 0000:00:12.2: EHCI: unrecognized capability 28
[    2.084439] pci 0000:00:12.2: EHCI: unrecognized capability 28
[    2.084442] pci 0000:00:12.2: EHCI: [COLOR=Red]capability loop?[/COLOR]
[COLOR=Red][    2.884253] [/COLOR]pci 0000:00:**13.0**: OHCI: [COLOR=Red]BIOS handoff failed (BIOS bug?)[/COLOR] ffffffff
[COLOR=Red][    3.684253][/COLOR] pci 0000:00:**13.1**: OHCI: [COLOR=Red]BIOS handoff failed (BIOS bug?) [/COLOR]ffffffff
[    3.684271] pci 0000:00:**13.2**: EHCI: unrecognized capability 28
[    3.684273] pci 0000:00:13.2: EHCI: unrecognized capability 28
[    3.684276] pci 0000:00:13.2: EHCI: unrecognized capability 28
... this line repeated about 50 times)...

```where I believe the 12.0/1/2 and 13.0/1/2 may refer to the 3 USB ports ?

Somewhat further (dn't know if that reates to the above):
```
[    3.754104] isapnp: Scanning for PnP cards...
[    3.781043] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    3.781052] ACPI: Battery Slot [BAT0] (battery present)
[COLOR=Red][    4.143328] isapnp: No Plug & Play device found[/COLOR]
[    4.276806] Linux agpgart interface v0.103

```but, probably more significant:
```
[    4.328455] ehci_hcd 0000:00:13.2: init 0000:00:13.2 fail, -19
[    4.328481] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.328542] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.328556] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.328605] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[COLOR=Red] [   **12.328254]**[/COLOR] ohci_hcd 0000:00:[COLOR=Red]12.0: USB HC takeover failed!  [/COLOR](BIOS/SMM bug)
[   12.328257] ohci_hcd 0000:00:[COLOR=Red]**12.0: can't setup**[COLOR=Black]
[[/COLOR][/COLOR]12.328262] ohci_hcd 0000:00:12.0: USB bus 1 deregistered
[   12.328367] ohci_hcd 0000:00:12.0: PCI INT A disabled
[   12.328370] ohci_hcd 0000:00:12.0: init 0000:00:12.0 fail, -16
[   12.328378] ohci_hcd: probe of 0000:00:12.0 failed with error -16
[   12.328393] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.328407] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   12.328457] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 1
[COLOR=Red] [   **20.332254]**[/COLOR] ohci_hcd 0000:00:[COLOR=Red]12.1: USB HC takeover failed!  [/COLOR](BIOS/SMM bug)
[   20.332257] ohci_hcd 0000:00:[COLOR=Red]**12.1: can't setup**
[[/COLOR]   20.332262] ohci_hcd 0000:00:12.1: USB bus 1 deregistered
[   20.332357] ohci_hcd 0000:00:12.1: PCI INT A disabled
[   20.332361] ohci_hcd 0000:00:12.1: init 0000:00:12.1 fail, -16
[   20.332368] ohci_hcd: probe of 0000:00:12.1 failed with error -16
[   20.332390] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.332401] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   20.332446] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[COLOR=Red] [   **28.336253] **[/COLOR]ohci_hcd 0000:00:[COLOR=Red]13.0: USB HC takeover failed![/COLOR]  (BIOS/SMM bug)
[   28.336257] ohci_hcd 0000:00:[COLOR=Red]**13.0: can't setup**[/COLOR]
[   28.336263] ohci_hcd 0000:00:13.0: USB bus 1 deregistered
[   28.336364] ohci_hcd 0000:00:13.0: PCI INT A disabled
[   28.336367] ohci_hcd 0000:00:13.0: init 0000:00:13.0 fail, -16
[   28.336374] ohci_hcd: probe of 0000:00:13.0 failed with error -16
[   28.336388] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.336400] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   28.336458] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 1
[COLOR=Red] [   **36.336254] **[/COLOR]ohci_hcd 0000:00:[COLOR=Red]13.1: USB HC takeover failed!  [/COLOR](BIOS/SMM bug)
[   36.336258] ohci_hcd 0000:00:[COLOR=Red]**13.1: can't setup**[/COLOR]
[   36.336262] ohci_hcd 0000:00:13.1: USB bus 1 deregistered
[   36.336359] ohci_hcd 0000:00:13.1: PCI INT A disabled
[   36.336362] ohci_hcd 0000:00:13.1: init 0000:00:13.1 fail, -16
[   36.336368] ohci_hcd: probe of 0000:00:13.1 failed with error -16
[   36.336390] uhci_hcd: USB Universal Host Controller Interface driver
[   36.336500] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   36.360174] serio: i8042 KBD port at 0x60,0x64 irq 1
[   36.360182] serio: i8042 AUX port at 0x60,0x64 irq 12

```and this clearly seems to be where all the wait time is spent.

Would you have any idea on what might be wrong ? Why are the USB ports not being recongnised/detected ? Do I need to check the presence of some specific drivers ? Are there any BIOS settings to tune (despite it works fine with Win7) ?

Thanks for your time, attention and advice !

EDIT: I just found out that the audio plugs (for headset) are not working either -- despite the built-in speakers work fine.

PS/ I can provide the full "dmesg" file if required.

---

### Post by AlterMind on 2011-08-02
Up ? ^_^

---

### Post by AlterMind on 2011-08-04
Hi, Any chance that anybody would look at this request please ?
Thank you.

---

### Post by AlterMind on 2011-08-04
Hi;

After browing tons of entries on many forums, I got finally inspired and solved myself this issue by editing the Grub2 boot options by using grub-customizer and editing the advanced properties in such a way to add the " **[COLOR=Blue]acpi=off[/COLOR]** " to the following entry:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```Then save changes and reboot ubuntu, and the USB ports were reachable again.
Cheers,
AlterMind

---

### Post by omidnazari27 on 2011-11-04
hi
i have a same probleme in opensuse 11.3 and 11.4 
please help me to solve it.
tanks.

---

### Post by AlterMind on 2011-11-14
Hi, is your computer of the same brand/model ?
Did you try editing the Brub2 boot options as mentioned ?
Cheers.

---

### Post by Jboulden on 2012-01-26
Guys, tried this approach and the USB ports did indeed work.  Then, for whatever reason, the computer would inexplicably shut off....  not boot down.... just shut off.

---

