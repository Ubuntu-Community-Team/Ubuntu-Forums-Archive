---
title: "CPU speed on PIII Laptop"
date: 2010-02-19
forum: Hardware
---

### Post by chris1379 on 2010-02-19
The laptop in question is a Sony PCG-F580 upgraded to a Pentium 3 700. I believe these were the first chips with speedstep. The only frequency control it uses is a switch from 550 MHz on battery power to 700 MHz on AC. In Windows, it changes when the power is connected or disconnected. In Ubuntu, the only time it changes is at boot. If it boots with the AC connected, it will stay at 700 MHz even if the AC is disconnected. If it boots on battery power, it will stay at 550 MHz even if the AC is connected. I would like it to change like it does in Windows.

By doing a few tests I determined that the CPU speed is set by Ubuntu and not by the BIOS. If I boot to the Grub menu on battery power and then connect the AC adapter before booting Ubuntu, it will run at 700 MHz. Does anyone know the mechanism by which the CPU frequency is changed and how to manipulate it?

---

### Post by wilee-nilee on 2010-02-19
Right click on the panel and add to panel then cpu frequency monitor. You can adjust the speed that way easily.

---

### Post by chris1379 on 2010-02-20
I get an error that frequency scaling is not supported on this chip. It only shows the frequency. There are several other things that might provide a clue too. If I boot on battery power, the volume keys (Fn + F3,F4) do not work and all of the boxes in the services GUI are unchecked. The display always starts at full brightness but will dim if the AC is plugged in then unplugged. The display blanking timer follows the CPU frequency and stays at the state in which it was booted. There is also a problem with auto standby but I don't use that anyway.

Chris

---

