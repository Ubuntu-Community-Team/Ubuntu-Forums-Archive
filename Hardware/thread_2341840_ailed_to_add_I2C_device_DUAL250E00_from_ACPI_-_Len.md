---
title: "ailed to add I2C device DUAL250E:00 from ACPI - Lenovo Yoga laptop"
date: 2016-11-01
forum: Hardware
---

### Post by pedro-amaral-couto on 2016-11-01
I have a Lenovo Yoga 300 laptop and installed Ubuntu 16.04 on it.
Everything seems to work except the power and thermal indicators.
I noticed the power indicator applet is missing. That's an annoyance since the laptop simply shuts down when the battery is empty without any warning.

While booting Ubuntu I find two ACPI error message.
From dmesg:
> [   11.908487] i2c i2c-10: Failed to register i2c client DUAL250E:00 at 0x18 (-17)
[   11.908493] i2c i2c-10: failed to add I2C device DUAL250E:00 from ACPI

"acpi -b" and "acpi -t" output nothing.
The acpi version is 1.7.

"acpi -v" outputs:
> Adapter 0: on-line
Cooling 0: soc_dts1 no state information available
Cooling 1: soc_dts0 no state information available
Cooling 2: B0DB no state information available
Cooling 3: INT3400 Thermal no state information available
Cooling 4: intel_powerclamp no state information available
Cooling 5: Processor 0 of 10
Cooling 6: Processor 0 of 10


Thanks in advance.

---

### Post by neib2 on 2016-12-11
Hello,
I had exactly the same problem, same thing in dmesg, same computer (lenovo yoga + debian 8), when I was looking for a solution for that, I found your post and you gave me a way for my research.
Actually I fix the battery notifications but not the i2c messages.

I add the i2c-tools + makedev (I think this one is optional but looks work with i2c-tools)
I also install acpi-support (seems good but not necessary for this problem).

So, the addition of these three packages allowed me to notice the warnings of the battery appear. But now, I have no idea about the error messages...

Sorry if my English is not very correct ;) the only thing to remember is i2c-tools ( + makedev ( + acpi-support ) ). I hope that it will help you.

EDIT : if you find something about i2c client and i2c device messages, it could be fine to know ;)
and (Off Topic) in the command dmesg, I also have this message : mmc0: Unknown controller version (3). You may experience problems. (about SDcard I think) if you also had this problem and you resolved it?
Thank you!

---

