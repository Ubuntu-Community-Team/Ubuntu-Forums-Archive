---
title: "The monitor screen does not turn on after waking up from sleep mode"
date: 2021-06-15
forum: Hardware
---

### Post by sakralbar on 2021-06-15
Hello.


The problem appeared about 2-4 weeks ago. After waking up from sleep mode, the monitor stopped turning on.
Previously, it changed the color of the power indicator, and an image appeared (ubuntu login screen with user selection). Now there is silence.
In this case, the system itself comes out of sleep mode and working. If I press the power button on the monitor (turn off), and then again (turn on), the image appears.
What could be the problem?


Benq monitor connected via hdmi to amd rx-460 video card. Ubuntu 20.04 system, kernel 5.8.0-55-generic.

Sorry for my English.

---

### Post by MAFoElffen on 2021-06-15
Not sure at the moment, but related to ACPI and hardware. 

What is the display and what is Ubuntu running on? (your system hardware)

Next, if you look in your apt logs, at /var/logs/apt/history.log... Look at anything that might have updated or was installed just previous to when you started getting that problem.

 Personally, I turn my display timeout setting to never turn off, and just turn off my display when I am not using it...

Just some ideas.

---

### Post by sakralbar on 2021-06-24
Apparently, this is some kind of amd and gnome bug.
The problem was solved by adding amdgpu.dc = 0 to GRUB_CMDLINE_LINUX_DEFAULT.

---

