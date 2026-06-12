---
title: "Hardware detection: Illegal capability!"
date: 2005-11-04
forum: Hardware &amp; Laptops
---

### Post by moleculardeconstruction on 2005-11-04
I'm trying to install breezy on a fairly new laptop. The specs of the laptop are:

[http://www.pioneercomputers.com.au/products/info.asp?c1=3&c2=13&id=479](http://www.pioneercomputers.com.au/products/info.asp?c1=3&c2=13&id=479)


It starts the hardware detection and then stops at this point:


[4294673.128000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[4294673.128000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294673.128000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294673.128000] ehci_hcd 0000:00:1d.7: debug port 15
[4294673.128000] ehci_hcd 0000:00:1d.7: illegal capability!


The hoary CD boots, but has issues with the graphics. Breezy can't make it past this point.

Any help would be appreciated.

Thanks

---

### Post by John.Michael.Kane on 2005-11-04
fairly new laptop i would say thats an understatement. from your errorcould try turning off the usb from the bios. and see ifyou get that error again.

---

### Post by moleculardeconstruction on 2005-11-04
I went into the BIOS to turn off USB, but it has really limited bios settings, and you can't turn off the usb.

Anyway, I think the problem is with the kernel that breezy uses. I installed hoary which went sort of ok, and got a useable machine. I then upgraded to breezy with the breezy cd. I then rebooted to use the new kernel after the upgrade, and I got the same error that I had got when booting with the breezy cd. This leads me to the conclusion that the kernel in breezy has issues with this laptop, but the kernel in hoary works fine.
I don't know what could have changed in the kernel that could cause something like that to stop working.
At least I can actually get into the system now.

---

### Post by moleculardeconstruction on 2005-11-07
Running breezy with this laptop is just causing too many problems. I think I will just run hoary for now. Still don't know why that kernel won't work. Googling dind't find anything.

---

### Post by az on 2005-11-07
*please* file a bug report.  No one will fix this problem if you do not report it.

bugzilla.ubuntu.com

As well, perhaps you would add your model here:
[https://wiki.ubuntu.com/LaptopTesting](https://wiki.ubuntu.com/LaptopTesting)

and become part of the laptop testing team.  They don't bite.

That being said, did you try some of the bot arguments listed on the help screen when you boot the installer (F3 F4 and so on?)

---

### Post by moleculardeconstruction on 2005-11-09
Bug report filed. [http://bugzilla.ubuntu.com/show_bug.cgi?id=19441](http://bugzilla.ubuntu.com/show_bug.cgi?id=19441)

I did try several of the boot arguments, which didn't really seem to help. I might try all of them, just in case one of them works.

---

### Post by az on 2005-11-10
You rock!

---

