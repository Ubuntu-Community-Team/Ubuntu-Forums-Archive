---
title: "Random laptop freeze on boot"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by tamerucar on 2007-12-29
Hi all,

I was having freeze problems with my NVIDIA card. After the new driver release from NVIDIA, my problem solved. But now I am experiencing random system freezes during system boot. I disabled silent boot to see where the system crashes. And here it is:

```
Enabling IO-APIC IRQs
..TIMER: Vector=0x31 APIC1=0 PIN1=2 APIC2=-1 PIN2=-1
```

What can be the problem? Or should I look somewhere else? :(

Thanks for any reply...

Have a nice and freezeless day :)

---

### Post by ARhere on 2007-12-29
Do you have your BIOS set to assign IRQ's, or for a Plug N' Play compatible OS?

Also, disable legacy USB support in the BIOS if you are not using it.

-AR

---

### Post by tamerucar on 2007-12-29
Firstly, thanks for your reply ARhere.

I searched my BIOS for any entry as "assigning IRQ's, or for a Plug N' Play compatible OS" or "legacy USB support". But i found nothing :(

---

### Post by tamerucar on 2007-12-30
I found a temporary solution (just a workaround) for my case: Booting with "noapic" kernel parameter. If I boot system with "noapic" parameter, it works fine. But disabling APIC is no good or am I wrong?

---

### Post by ARhere on 2007-12-30
I am sticking on this because it says,
> Enabling IO-APIC IRQs
and then freezes.  This makes me think that the system is trying to assign IRQ's to that resource and not enough, or what it is attempting, is not available.

In Award BIOS, it is the second option on left hand column called "Advanced Resources" or something like that.  What you want to look for under advanced is "IRQ Resource allocations" or "Boot Configuration".

I did a google/images search and found a couple of pics to show you what to look for.
Assign [IRQ for VGA]("http://www.kabinet.cz/stuff/hw/motherboard_MSI_MS-6786_ver2_Quasar2/Support%20Packard%20Bell%20Quasar%202%20Motherboard%20BIOS%20Screens%20-%20instr_bios_quasar2%20-%20BIOS%20-%20IMEDIA%201601_B%20-%20PB13202101_soubory/bios_quasar2_configurations.gif")
Set [PnP Capable OS]("http://www.dfi.com/support1/images/BIOS_IRQ.gif")

Basically what I am getting at, is make sure you turn off anything you are not using releasing IRQ's for use with other items, like your video card.

Try this and let me know.  -AR

---

### Post by tamerucar on 2007-12-31
Umm, I checked my BIOS again. There is no such relevant entry for IRQ thing. 
My laptop uses Phoenix BIOS version F.3D

Boeh :(

---

### Post by ARhere on 2007-12-31
Well... being a laptop, its BIOS is probobly stripped of most user functionality.

Phoenix [Bios PnP OS]("http://www.computerhope.com/help/bios9.gif")

If you don't see this option then you will need to install a work-around in the OS for your problem.

Sorry, I tried.
-AR

---

### Post by tamerucar on 2008-01-01
Thanks man, but I don't see that option.

---

