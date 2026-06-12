---
title: "PC won't power down after shut down is selected"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-04-12
Hello all, I have a PC that I installed Ubuntu on.  The specs are below:

Asus p3b-f slot 1 motherboard
256MB pc133
Intel p3-450 Katmai
SB Live PCI
Realtek 8139 10/100 ethernet PCI
GeForce2 GTS video card
Maxtor 40G hd

I put this PC together as a cheap file server and a PC to mess around with.  Hey it only cost me about $10.  I was able to get the PC up and running.  I installed Ubuntu and did the updates.  Man was is a slow process under Gnome.  I should probably install and run XFCE as it is more lightweight than Gnome.

Does anyone know what the minimum specs for Ubuntu are?

Any rate back to the problem.  When I go to the little door and select shutdown the PC won't shut off.  I did a bit of poking around and you need ACPI enabled to do this.  Does anyone know how to check to see if ACPI is enabled or disabled?

Thanks

---

### Post by mac.ryan on 2007-04-12
> **stchman said:**
> Does anyone know how to check to see if ACPI is enabled or disabled?

AFAIK, apic is enabled by default in your boot (in fact you have to explicitly issue "noapic" at boot, if you don't want it). I think you should verify if your bios - though - has apic present and enabled (especially if it is an old machine...).

---

### Post by stchman on 2007-04-12
> **mac.ryan said:**
> AFAIK, apic is enabled by default in your boot (in fact you have to explicitly issue "noapic" at boot, if you don't want it). I think you should verify if your bios - though - has apic present and enabled (especially if it is an old machine...).


I will give it a try.  I went to ASUS website and there is an updated BIOS 1006 and the motherboard I am using is 1003.  Maybe that will clear up the problem.

Thanks

---

### Post by az on 2007-04-12
> **stchman said:**
> Does anyone know how to check to see if ACPI is enabled or disabled?

Thanks

Type 
dmesg|less
and the first few lines will probably tell you that your motherboard does not meet the cutoff manufacture date for acpi (which is 2000).  You can add  "acpi=force" to the end of your kernel line in grub to see if that will work.  (Show the grub menu when you boot, select the default option and press "E" to edit it.  Select the kernel line and press "E" again to edit it.  Add the command and then press enter.  Press "'B" to boot.

If that works for you, you can then add the parameter to the menu.list permanently.

Edit the commented-out line for kernel options (# kopt=root=/dev/hda2 ro)  Yes it is commented out, but it is meant to be used by update-grub, and not grub itself.  Then run update-grub

sudo update-grub


Another possibility is that you dissabled acpi in favor of apm in your BIOS.  Check there, first.

---

### Post by stchman on 2007-04-12
> **az said:**
> Type 
dmesg|less
and the first few lines will probably tell you that your motherboard does not meet the cutoff manufacture date for acpi (which is 2000).  You can add  "acpi=force" to the end of your kernel line in grub to see if that will work.  (Show the grub menu when you boot, select the default option and press "E" to edit it.  Select the kernel line and press "E" again to edit it.  Add the command and then press enter.  Press "'B" to boot.

YOu can then add the parameter to the menu.list 

Another possibility is that you dissabled acpi in favor of apm in your BIOS.  Check there, first.

The motherboard BIOS is dated sometime in 1999.  Asus has a newer BIOS (~2000) for that board.  I am going to install that BIOS to see if that works.

Thanks

---

### Post by stchman on 2007-04-13
Update, I flashed the motherboard with the 1006 BIOS and all works now.  Thanks for all of the input I got.

---

