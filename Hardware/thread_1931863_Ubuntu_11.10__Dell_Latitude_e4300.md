---
title: "Ubuntu 11.10 / Dell Latitude e4300"
date: 2012-02-26
forum: Hardware
---

### Post by SCreamin4Q on 2012-02-26
I have a Dell Latitude e4300 laptop with Ubuntu 11.10 64 bit installed. The OS runs great but at times it freezes, and I have to power off to get it to respond again. Also sometimes I have an issue with the BIOS settings. Sometimes when I boot up the LCD lighting settings change. So if I had originally setup the lighting to be at 50% on battery power and 80% when plugged in, the next time I boot up it might be the opposite, meaning 50% when plugged in and 80% on battery, or sometimes both are at the lowest setting. Either way I have to go back into the BIOS settings and reset the lighting often.

I searched on Dell for a BIOS upgrade but they don't have any for this OS since they don't support it. Should I upgrade the BIOS for the latest version of Windows that Dell supports? Is there somewhere I get get BIOS updates for Ubuntu / Dell?

Thanks

---

### Post by ahallubuntu on 2012-02-26
Your problems do not sound like problems a BIOS update would fix, so I wouldn't waste any more time going down that road.

One possibility is a dead CMOS battery.  Do you lose date/time settings between power-offs?  If plugged in or if the laptop battery is good and charged, the CMOS battery should not be needed to keep BIOS settings, but if your laptop battery is dead and you unplug, the CMOS battery would be needed to keep settings.  

If you power up after the laptop has been off  a while and immediately go into BIOS Setup, if the date/time are correct then the CMOS battery is probably good, though.  Ubuntu will probably sync the time/date to a server once you boot up to fix an incorrect date setting.

Even so, a bad CMOS battery probably wouldn't cause freezes.  You might have a hardware issue. Normally, you rule out everything else (RAM, hard drive, CPU/overheating, etc.) first and then if nothing else assume it's a failing motherboard.  You could burn/boot the Ultimate Boot CD and run one of the stress tests on it.  They can heat up the CPU.  If you run one of these for a few hours and get no freezes, the CPU is probably not overheating and there's probably no cooling problem.  You can run Memtest overnight (off the Ultimate Boot CD or just from the Grub boot menu in Ubuntu) for a while to see if the RAM ever fails, too.

Motherboards do fail sometimes, though, on computers - just a fact of life.

---

