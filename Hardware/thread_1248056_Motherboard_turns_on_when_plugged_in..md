---
title: "Motherboard turns on when plugged in."
date: 2009-08-23
forum: Hardware
---

### Post by Maheriano on 2009-08-23
This is not operating system specific, it did this before I even installed anything. So I have an Intel D945GCLF motherboard and hooked up an extra power supply to it. The only thing I have hooked to the board is the 20 pin ATX connector and the 4 pin P4 connector, that's it. No power button, nothing. As soon as I plug the PSU into the wall, the computer boots up. I've never seen this before, any ideas? The CMOS battery was dead so I replaced it and it's still happening.

Plus whenever I turn it off, it turns on by itself a minute or so later.

---

### Post by gordintoronto on 2009-08-23
> **Maheriano said:**
> This is not operating system specific, it did this before I even installed anything. So I have an Intel D945GCLF motherboard and hooked up an extra power supply to it. The only thing I have hooked to the board is the 20 pin ATX connector and the 4 pin P4 connector, that's it. No power button, nothing. As soon as I plug the PSU into the wall, the computer boots up. I've never seen this before, any ideas? The CMOS battery was dead so I replaced it and it's still happening.

Plus whenever I turn it off, it turns on by itself a minute or so later.

Do you have any PCI devices installed?  You might need to change a setting in your BIOS.  On my computer, it's called "PME Event Wakeup," under "power management."  There are several other "wake up" settings in my BIOS.

On another computer it had a different name, which I do not remember.  I installed a PCI sound card and the computer immediately powered up, so I had to change the setting.

---

### Post by celthunder on 2009-08-23
Turn auto power on after power off in your bios off.  it's intended for if theres a storm or something and your electricity gets cut while it's on it turns itself back on once the power is restored.

---

### Post by Maheriano on 2009-08-23
No PCI cards and that auto on setting is already off.

---

### Post by celthunder on 2009-08-24
Are the pins for the power touching each other through metal or directly somehow?

---

