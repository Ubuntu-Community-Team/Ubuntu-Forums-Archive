---
title: "USB ports not working"
date: 2010-10-11
forum: Hardware
---

### Post by twoaday on 2010-10-11
I have a Dell 1536 running 10.10 that will not allow the USB ports to work at all. lspci shows the usb controllers, lsusb shows nothing at all, lsmod I am not familiar enough with to know what I am looking for but I don't seem to see anything for the USB in there, and dmesg shows a hcc takeover failure? (Can't remember the actual failure, not able to tinker at work).
The failure shows for all of the usb ports and controllers.

Have tried the patched kernel ....26 for RC7 as found in the bug reports and still same result. Granted I am running off an release candidate and not the latest release. Noticed that their was a laptop used for certifying the 10.10 distro for the hardware and they are using a different version of the BIOS that I am unable to find (x15, I am using A06) might be a contributor to the issue.
Was just wondering if anyone else was having same issue and if a fix was in the works.

May have to go back to Lucid, Shame though cause other than this issue I am extremely happy with this release.

---

### Post by makda on 2010-10-16
I too am having the same problem using a full size PC with an AMD Athlon64 and an abit KV8 Pro motherboard. USb worked fine with 10.04. Lack of USB is quite limiting...

---

### Post by twoaday on 2010-10-17
Updates 

Tried a fresh install of 10.10 after switching back to 10.4, USB ports work fine under 10.4. For the errors under 10.10 : Receiving these under "Messages" in log viewer having to do with OHCI and EHCI:

pci 0000:00:12.0: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
pci 0000:00:12.2: EHCI: unrecognized capability ff


This output is the same in DMESG and in the kernlog

 kernel: [    4.782611] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
 kernel: [    4.782859] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
 kernel: [    4.782893] ehci_hcd 0000:00:12.2: EHCI Host Controller
 kernel: [    4.782936] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
 kernel: [    4.783181] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
 kernel: [    4.783199] ehci_hcd 0000:00:12.2: debug port 15 IN USE
 kernel: [    4.784066] ACPI: Battery Slot [BAT0] (battery present)
 kernel: [    4.812594] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd4004000
 kernel: [    4.812623] ehci_hcd 0000:00:12.2: USB bus 1 deregistered
 kernel: [    4.812732] ehci_hcd 0000:00:12.2: PCI INT B disabled
 kernel: [    4.812762] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
 kernel: [    4.812781] ehci_hcd 0000:00:13.2: EHCI Host Controller
 kernel: [    4.812818] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
 kernel: [    4.812882] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
 kernel: [    4.812898] ehci_hcd 0000:00:13.2: debug port 15 IN USE
 kernel: [    4.842564] ehci_hcd 0000:00:13.2: irq 20, io mem 0xd4004100
 kernel: [    4.842581] ehci_hcd 0000:00:13.2: USB bus 1 deregistered
 kernel: [    4.842667] ehci_hcd 0000:00:13.2: PCI INT B disabled
 kernel: [    4.842689] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
 kernel: [    4.842711] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 kernel: [    4.842728] ohci_hcd 0000:00:12.0: OHCI Host Controller
 kernel: [    4.842763] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
 kernel: [   14.840055] ohci_hcd 0000:00:12.0: USB bus 1 deregistered
 kernel: [   14.840089] ohci_hcd 0000:00:12.0: PCI INT A disabled
 kernel: [   14.840096] ohci_hcd: probe of 0000:00:12.0 failed with error -16
 kernel: [   14.840108] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 kernel: [   14.840126] ohci_hcd 0000:00:12.1: OHCI Host Controller
 kernel: [   14.840160] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 1
 kernel: [   24.840054] ohci_hcd 0000:00:12.1: USB bus 1 deregistered
 kernel: [   24.840086] ohci_hcd 0000:00:12.1: PCI INT A disabled
 kernel: [   24.840093] ohci_hcd: probe of 0000:00:12.1 failed with error -16
 kernel: [   24.840112] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
 kernel: [   24.840129] ohci_hcd 0000:00:13.0: OHCI Host Controller
 kernel: [   24.840163] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
 kernel: [   34.840054] ohci_hcd 0000:00:13.0: USB bus 1 deregistered
 kernel: [   34.840087] ohci_hcd 0000:00:13.0: PCI INT A disabled
 kernel: [   34.840094] ohci_hcd: probe of 0000:00:13.0 failed with error -16
 kernel: [   34.840106] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
 kernel: [   34.840123] ohci_hcd 0000:00:13.1: OHCI Host Controller
 kernel: [   34.840157] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 1
 kernel: [   44.840067] ohci_hcd 0000:00:13.1: USB bus 1 deregistered
 kernel: [   44.840100] ohci_hcd 0000:00:13.1: PCI INT A disabled
 kernel: [   44.840107] ohci_hcd: probe of 0000:00:13.1 failed with error -16
 kernel: [   44.840121] uhci_hcd: USB Universal Host Controller Interface driver

I noticed that the controller is "sb700/sb800" not the "sb600/sb700" listed for the freeze work around.

also if it helps any LSPCI shows the devices 

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)


Out put of LSUSB : "None"

Hope this helps narrow it down,

---

### Post by twoaday on 2010-10-27
bump

---

