---
title: "No usb mouse, after hotplug loaded"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Tuxer on 2005-04-12
Hi,
I installed Hoary (tries Warty, also doesn't work anyway) in my laptop (compaq presario r3358)...
Standard install, i plug in my usb mouse... the red light from the mouse lights up.. till the boot process start hotplug... then the red light suddenly goes off... plug in after boot, also no light... dmesg shows no activity, not even a sign of something connected in a usb bus.... 

What could be wrong here? Also the live cd doesn't pick my mouse up... The touchpad works in any other case though...

Could someone explain the problem or know a solution??

TIA,
Erik

---

### Post by Tuxer on 2005-04-13
Hmm, i've been looking around with grub boot parameters... and i found out that acpi blocks my mouse.. if i give grub acpi=off, the mouse stays on... but now i can't see battery status, processor speed and that kind off stuff... also sometimes the keyboard doesn't work... is there a combination of boot parameters possible that both will work??

TIA,
Erik

Edit: or does somebody know a list of all grub boot commands?

---

### Post by brannolte on 2005-04-18
[QUOTE=Tuxer]Hmm, i've been looking around with grub boot parameters... and i found out that acpi blocks my mouse.. if i give grub acpi=off, the mouse stays on... but now i can't see battery status, processor speed and that kind off stuff... also sometimes the keyboard doesn't work... is there a combination of boot parameters possible that both will work??

TIA,
Erik

Edit: or does somebody know a list of all grub boot commands?[/QUOTE]


Hi Tuxer and all the others,

I have the same problem on my hp/compaq nx9105. I tried different distris and NO one is working with ACPI and USB on. I asked in different forum but nobody has an idea. I spend hours reading Linux-Howtos but ... 

"pci=noacpi" leads to no battery warning
"acpi=off apm=on" the same

PLEASE can somebody help us? BTW Ubuntu and Kubuntu are realy fast compared with other distris


Greets from Germany 
Newbie:matthias

EDIT: 20050418_2308
after a tipin the IRC chanel to restart my hotplug system i got the following messages:
----------------------------------------------------------------- schnipp -
Apr 18 23:06:39 localhost kernel: ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Apr 18 23:06:39 localhost kernel: apm: BIOS not found.
Apr 18 23:06:39 localhost kernel: cs: IO port probe 0x0100-0x04ff: excluding 0x200-0x20f 0x4d0-0x4d7
Apr 18 23:06:39 localhost kernel: cs: IO port probe 0x0800-0x08ff: clean.
Apr 18 23:06:39 localhost kernel: cs: IO port probe 0x0c00-0x0cff: clean.
Apr 18 23:06:39 localhost kernel: cs: IO port probe 0x0a00-0x0aff: clean.
Apr 18 23:06:39 localhost kernel: powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
Apr 18 23:06:39 localhost kernel: powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
Apr 18 23:06:39 localhost kernel: powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x18 (950 mV)
Apr 18 23:06:40 localhost input.agent[8836]:      evdev: already loaded
Apr 18 23:06:40 localhost input.agent[8836]:      evbug: blacklisted
Apr 18 23:06:40 localhost input.agent[8864]:      evdev: already loaded
Apr 18 23:06:40 localhost input.agent[8864]:      evbug: blacklisted
Apr 18 23:06:40 localhost input.agent[8864]:      mousedev: already loaded
Apr 18 23:06:41 localhost input.agent[8864]:      tsdev: already loaded
Apr 18 23:06:41 localhost input.agent[8914]:      evdev: already loaded
Apr 18 23:06:41 localhost input.agent[8914]:      evbug: blacklisted
Apr 18 23:06:41 localhost isapnp.rc[8943]:      pcspkr: loaded sucessfully
Apr 18 23:06:41 localhost isapnp.rc[8943]:      rtc: loaded sucessfully
Apr 18 23:06:41 localhost isapnp.rc[8943]:      psmouse: loaded sucessfully
Apr 18 23:06:44 localhost isapnp.rc[8943]:      floppy: can't be loaded
Apr 18 23:06:44 localhost isapnp.rc[8943]:      parport_pc: loaded sucessfully
Apr 18 23:06:44 localhost pci.agent[9070]:      amd64-agp: already loaded
Apr 18 23:06:44 localhost pci.agent[9117]:      i2c-nforce2: already loaded
Apr 18 23:06:44 localhost kernel: ehci_hcd 0000:00:02.2: remove, state 1
Apr 18 23:06:44 localhost kernel: usb usb1: USB disconnect, address 1
Apr 18 23:06:44 localhost kernel: ehci_hcd 0000:00:02.2: USB bus 1 deregistered
Apr 18 23:06:44 localhost kernel: usbcore: deregistering driver usbfs
Apr 18 23:06:44 localhost kernel: usbcore: deregistering driver hub
Apr 18 23:06:44 localhost kernel: inserting floppy driver for 2.6.10-5-386
Apr 18 23:06:44 localhost kernel: usbcore: registered new driver usbfs
Apr 18 23:06:44 localhost kernel: usbcore: registered new driver hub
Apr 18 23:06:44 localhost kernel: ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 21 (level, low) -> IRQ 21
Apr 18 23:06:56 localhost kernel: ohci_hcd 0000:00:02.0: nVidia Corporation nForce3 USB 1.1
Apr 18 23:06:56 localhost kernel: ohci_hcd: probe of 0000:00:02.0 failed with error -16
Apr 18 23:06:56 localhost kernel: ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 20 (level, low) -> IRQ 20
Apr 18 23:06:56 localhost kernel: ohci_hcd 0000:00:02.1: nVidia Corporation nForce3 USB 1.1 (#2)
Apr 18 23:06:56 localhost pci.agent[9146]:      ohci-hcd: loaded successfully
Apr 18 23:06:56 localhost pci.agent[9297]:      ohci-hcd: already loaded
Apr 18 23:06:56 localhost kernel: ohci_hcd: probe of 0000:00:02.1 failed with error -16
Apr 18 23:06:56 localhost kernel: ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 22 (level, low) -> IRQ 22
Apr 18 23:06:56 localhost kernel: ehci_hcd 0000:00:02.2: nVidia Corporation nForce3 USB 2.0
Apr 18 23:06:56 localhost kernel: ehci_hcd 0000:00:02.2: irq 22, pci mem 0xe8004000
Apr 18 23:06:56 localhost kernel: ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
Apr 18 23:06:56 localhost pci.agent[9326]:      ehci-hcd: loaded successfully
Apr 18 23:06:56 localhost usb.agent[9415]:      usbcore: already loaded
Apr 18 23:06:56 localhost pci.agent[9447]:      i810_audio: blacklisted
Apr 18 23:06:56 localhost pci.agent[9447]:      snd-intel8x0: already loaded
Apr 18 23:06:57 localhost pci.agent[9497]:      snd-intel8x0m: blacklisted
Apr 18 23:06:57 localhost pci.agent[9528]:      amd74xx: already loaded
Apr 18 23:06:57 localhost pci.agent[9557]:      pciehp: can't be loaded
Apr 18 23:06:57 localhost pci.agent[9557]: missing kernel or user mode driver pciehp
Apr 18 23:06:57 localhost pci.agent[9557]:      shpchp: already loaded
Apr 18 23:06:57 localhost pci.agent[9656]:      pciehp: can't be loaded
Apr 18 23:06:57 localhost pci.agent[9656]: missing kernel or user mode driver pciehp
Apr 18 23:06:57 localhost pci.agent[9656]:      shpchp: already loaded
Apr 18 23:06:57 localhost pci.rc[9059]:      ignoring pci display device on 01:00.0
Apr 18 23:06:57 localhost pci.agent[9837]:      ohci1394: already loaded
Apr 18 23:06:57 localhost pci.agent[9866]:      8139cp: already loaded
Apr 18 23:06:57 localhost pci.agent[9866]:      8139too: already loaded
Apr 18 23:06:58 localhost pci.agent[9926]:      yenta_socket: already loaded
Apr 18 23:06:58 localhost pci.agent[9957]:      yenta_socket: already loaded
----------------------------------------------------------------- schnapp -
 as you can see there is an error -16 in:
ohci_hcd: probe of 0000:00:02.0 failed with error -16
and 
ohci_hcd: probe of 0000:00:02.1 failed with error -16 any ideas?

if I plug the mouse in on of the three usb-slots - no messages!

if I start with ACPI=off the USB devices work!

Greets bra

---

### Post by brannolte on 2005-04-18
SOLVED!!!!!!

The Problem is the BIOS. I flashed to the newest one F34 and ... it works.

Grettings bra  (this is my nik do not flam me)

---

### Post by EcliptuX on 2005-05-06
I have exactly the same pb with my USB mouse and the ACPI with my Compaq Presario R3411 :(
I'm enjoy you had find an issue with update the bios of your laptop, but I didn't find a new one for mine ](*,)
Is there another solution to use USB mouse with ACPI support ? 

Thanks a lot for any help:-)

---

### Post by brannolte on 2005-05-06
Hi EcliptuX

I´m sorry that there is no bios update for your laptop, but it took a lot of time to find the right on for mine. 

Searching the web, I found lots of information "solving" the problem, but none of them worked for me.

Sorry that I am not able to help you 

Bye Matthias
 Check
[hp - compaq bios side](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00034791&product=462601&dlc=en&lang=en)

---

### Post by EcliptuX on 2005-05-07
Yes !!!!!!!
I had just installed the Bios Update F34
My laptop was compatible with it and I should install WinXP to install it !!!
But now, my USB mouse working well with ACPI ;)

Thanks brannolte ;)

---

### Post by brannolte on 2005-05-07
;-))))

---

### Post by fanch317 on 2005-07-17
Just a other xp :
So I have a HP nx9105 and donwload the bios F35, it's work !!!
My usb mouse work now in ubuntu 5!

---

