---
title: "Suspend/hibernate problem with Feisty"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by youngde on 2007-04-21
After installing Feisty on my Sony Vaio PCG-Fx140, I now get a desktop error message after resuming from suspend/hibernate mode: "Your computer was unable to hibernate properly". Checking /var/log/messages, I see this:

Apr 20 16:02:50 ubuntu gnome-power-manager: (dyoung) An unknown error occured code='32' quark='g-exec-error-quark'
Apr 20 16:02:50 ubuntu kernel: [ 4513.864000] ohci1394 does not fully support suspend and resume yet

and then upon resume:

Apr 21 11:33:00 ubuntu gnome-power-manager: (dyoung) Resuming computer
Apr 21 11:33:06 ubuntu gnome-power-manager: (dyoung) hibernate failed

Since hibernate/resume worked ok under Edgy, this seems to be a new issue. What do you folks think?

david

---

### Post by Dougie187 on 2007-05-05
I have a similar problem. If my messages log i see this 

May  5 09:59:58 douglt kernel: [ 8648.916000] ohci1394 does not fully support suspend and resume yet

And then after I try to resume it says this

May  5 09:59:58 douglt gnome-power-manager: (doug) suspend failed

Pretty much my resume never works when I suspend. One of two things usually happens. Either, the computer screen is just black and I cant do anything with it. Or the computer screen flashes single colored screens, (Black, White, Red, Blue, Green) and just rotates in that order. Then i have to hard reboot in both cases to make it work.

---

### Post by JesterGr on 2007-05-09
i have the same problem

```
May  9 02:38:27 Jester gnome-power-manager: (harry) Hibernating computer because the DBUS method Hibernate() was invoked
May  9 09:42:28 Jester gnome-power-manager: (harry) An unknown error occured code='32' quark='g-exec-error-quark'
May  9 09:42:28 Jester gnome-power-manager: (harry) Resuming computer
May  9 09:42:28 Jester kernel: [ 9802.453148] Disabling non-boot CPUs ...
May  9 09:42:28 Jester kernel: [ 9802.453154] Stopping tasks ... done.
May  9 09:42:28 Jester kernel: [ 9802.803275] Shrinking memory...  ^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^Hdone (216022 pages freed)
May  9 09:42:28 Jester kernel: [ 9805.108929] Freed 864088 kbytes in 2.30 seconds (375.69 MB/s)
May  9 09:42:28 Jester kernel: [ 9805.108932] Suspending console(s)
May  9 09:42:28 Jester kernel: [ 9805.108989] cdc_acm 3-2:1.0: no suspend for driver cdc_acm?
May  9 09:42:28 Jester kernel: [ 9805.108991] cdc_acm 3-2:1.1: no suspend for driver cdc_acm?
May  9 09:42:28 Jester kernel: [ 9806.270888] pnp: Device 00:0c disabled.
May  9 09:42:28 Jester kernel: [ 9806.271087] pnp: Device 00:0b disabled.
May  9 09:42:28 Jester kernel: [ 9806.271285] pnp: Device 00:0a disabled.
May  9 09:42:28 Jester kernel: [ 9806.271569] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
May  9 09:42:28 Jester kernel: [ 9806.271706] ACPI: PCI interrupt for device 0000:00:03.3 disabled
May  9 09:42:28 Jester kernel: [ 9806.290826] ACPI: PCI interrupt for device 0000:00:03.2 disabled
May  9 09:42:28 Jester kernel: [ 9806.290874] ACPI: PCI interrupt for device 0000:00:03.1 disabled
May  9 09:42:28 Jester kernel: [ 9806.290920] ACPI: PCI interrupt for device 0000:00:03.0 disabled
May  9 09:42:28 Jester kernel: [ 9806.291114] ACPI: PCI interrupt for device 0000:00:02.7 disabled
May  9 09:42:28 Jester kernel: [ 9806.291797] ACPI: PCI interrupt for device 0000:00:02.5 disabled
May  9 09:42:28 Jester kernel: [ 9806.291803] ohci1394 does not fully support suspend and resume yet
May  9 09:42:28 Jester kernel: [ 9806.315209] swsusp: critical section: 
May  9 09:42:28 Jester kernel: [ 9806.371605] swsusp: Need to copy 118264 pages
May  9 09:42:28 Jester kernel: [   94.030140] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[d7000000-d70007ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
May  9 09:42:28 Jester kernel: [   94.035182] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 19
May  9 09:42:28 Jester kernel: [   94.036675] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
May  9 09:42:28 Jester kernel: [   94.040378] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
May  9 09:42:28 Jester kernel: [   94.040429] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
May  9 09:42:28 Jester kernel: [   94.040477] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
May  9 09:42:28 Jester kernel: [   94.054401] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 21
May  9 09:42:28 Jester kernel: [   94.054460] usb usb4: root hub lost power or was reset
May  9 09:42:28 Jester kernel: [   94.054551] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 22
May  9 09:42:28 Jester kernel: [   94.054565] PCI: Enabling device 0000:00:0b.0 (0004 -> 0006)
May  9 09:42:28 Jester kernel: [   94.054569] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 22
May  9 09:42:28 Jester kernel: [   94.054579] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
May  9 09:42:28 Jester kernel: [   94.054581] bttv0: Can't enable device.
May  9 09:42:28 Jester kernel: [   94.054660] PCI: Enabling device 0000:00:0d.0 (0016 -> 0017)
May  9 09:42:28 Jester kernel: [   94.054664] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 16
May  9 09:42:28 Jester kernel: [   94.054739] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 16 (level, low) -> IRQ 19
May  9 09:42:28 Jester kernel: [   94.054806] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
May  9 09:42:28 Jester kernel: [   94.055886] pnp: Device 00:0a activated.
May  9 09:42:28 Jester kernel: [   94.056874] pnp: Device 00:0b activated.
May  9 09:42:28 Jester kernel: [   94.057873] pnp: Device 00:0c activated.
May  9 09:42:28 Jester kernel: [   94.732495] usb usb1: root hub lost power or was reset
May  9 09:42:28 Jester kernel: [   94.801418] usb usb3: root hub lost power or was reset
May  9 09:42:28 Jester kernel: [   94.910457] Restarting tasks ... done.
May  9 09:42:28 Jester kernel: [   94.910621] Enabling non-boot CPUs ...
May  9 09:42:28 Jester gnome-power-manager: (harry) hibernate failed
```

i am a newbie in linux, so say things in a non-complicative way :-)

---

### Post by misfitpierce on 2007-05-09
Well its not a solid problem I dont have a problem coming back from suspend... Only problem I have is I cant just touch my touchpad I have to hit power button on laptop but other than that its tip top.

---

### Post by WilliamAnderson on 2007-05-15
Hi,

Maybe your problem is:

> May 5 09:59:58 douglt kernel: [ 8648.916000] ohci1394 does not fully support suspend and resume yet

That device driver does not support suspending yet. If you are not using 1394 “firewire” devices, you could disable this driver.

William

---

### Post by Trixtua on 2007-05-17
I can I disable it ?

---

