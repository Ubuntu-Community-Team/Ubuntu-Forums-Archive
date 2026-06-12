---
title: "Power Management problems"
date: 2012-03-28
forum: Hardware
---

### Post by jcllings on 2012-03-28
Have been looking for some info regarding this but have not found it yet. I need some guidance on how to trouble shoot my power management problems. I want to leave this laptop running on my desk eventually but right now it&#347; just too annoying. 

Machine is a Sony Viao model g73jh. Virtually worthless under windows due to a combination of a video freeze and USB BSOD bugs. Known issues. Nice, huh? ;-)

Linux midknight 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

1. The fan runs at top speed at all times and it is loud. 

2. Possibly related to the above but I think the CPU&#347; never back off either, when they are supposed to. It&#347; a Core i7.

3. Never returns from sleep mode. I think I have the same problem with it when it hibernates. Will verify. 

More info? Clues? Ideas? Give up and get a real job? ;-)


Jim C.

---

### Post by jcllings on 2012-03-28
> **jcllings said:**
> Have been looking for some info regarding this but have not found it yet. I need some guidance on 
...
Jim C.

Dóh! Looks like I might need a kernel patch. :-/ I hate patching kernels. 

[http://blog.le-vert.net/?p=24](http://blog.le-vert.net/?p=24)

Hmmm... my error looks different from the one described though. I´ve got: 

[    1.331010]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    1.331013]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.331015] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.331522] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.331587] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.331648] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.331706] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    1.331770] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.331828] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.331888] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    1.331946] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 *4 5 6 7 11 12 14 15)

...but I should be seeing something that looks like:

ACPI Error: [RAMB] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)

...maybe not?

---

### Post by jcllings on 2012-04-03
Tried patching kernel. Didn't help. Going to hold out for the next kernel release and then see what happens. In the mean time, I am trying to de-activate all uses of sleep/hibernate. I've done this by removing the acpid, pm-utils, powermgmt-base packages and by disabling the power management service in KDE. Have also adapted power profiles accordingly but doubt they will matter much with all that other stuff ripped out / deactivated.

Hope it works. Getting tired of system lockups due to no acpi support.

---

### Post by Toz on 2012-04-03
According to this page ([http://www.linlap.com/wiki/asus+g73jh](http://www.linlap.com/wiki/asus+g73jh)), the loud fans are a result of using the open source drivers. Have you installed the proprietary drivers?

---

### Post by jcllings on 2012-04-03
> **Toz said:**
> According to this page ([http://www.linlap.com/wiki/asus+g73jh](http://www.linlap.com/wiki/asus+g73jh)), the loud fans are a result of using the open source drivers. Have you installed the proprietary drivers?

Wow, awesome tip. :-) 
Will give this a try tonight.

---

### Post by jcllings on 2012-04-04
So that does seem to have solved my fan problems at least. Of course ATI Catalyst was a bear to deal with but I eventually beat it into shape. It hated my dual Desktop flat screen / Laptop monitor combo which I use with KDE. Was really stubborn in getting it the way I want it. 
:-/

I have to say that from now on, I'm just going to spend the extra dough to get a Linux certified laptop. This department store crap is for the birds. Second lemon in a row Best Buy has sold me. 


Jim C.

---

### Post by jcllings on 2012-06-08
Bottom line for this thread was that support of the hardware in question was just plain insufficient. End result: I now use the machine mostly with Windows. Bought another machine which I got from System76 to replace it. I now run Windows in a VM since the new machine is quite fast and powerful.

---

