---
title: "Ryzen 3700X - MSI X570 with ComboPi 1.0.0.3abb - errors during boot"
date: 2019-09-05
forum: Hardware
---

### Post by roseflunder on 2019-09-05
Hello,

I got some problems booting Ubuntu 18.04 LTS with my new Ryzen 3700X and MSI MPG X570 GAMING PRO CARBON WIFI motherboard.
I knew that the they got some issues because of a bad random number method on the CPU but that problem should be fixed with the latest ComboPi/AGESA 1.0.0.3abb as far as I read so I went on and bought this system and flashed the latest BIOS.

Nevertheless I have serious trouble booting Ubuntu.
Most of the time the error messages from the attached picture appears and the boot won't go further than that.


[ATTACH=CONFIG]283940[/ATTACH]

Altough in rare cases the system boots without these errors and everything works.
So this is not 100% reproduceable but I get the error messages like 9 out of 10 times.

Ubuntu is installed on a seperate SSD (including the grub bootloader) and on another SSD I have windows 10.
So Windows 10 and Ubuntu are completely seperated and I switch between them via selecting the boot device from the BIOS.
Windows 10 boots always without any isssues so this issue is Ubuntu related somehow.
Both systems are installed in UEFI mode.

Do you have any clues what I could do to get my Ubuntu system working or are theses error messages a hint that I need to wait and hope that they release another BIOS update?

EDIT: Fastboot/hibernate is disabled in windows 10.

Greetings

---

### Post by rbmorse on 2019-09-05
Check the data and power cables used for the Ubuntu SSD.  Substitute with others if possible.

---

### Post by roseflunder on 2019-09-05
Thanks for you reply. I have some spare SATA cables that I can try.

---

### Post by roseflunder on 2019-09-05
Ok I am using a new SATA cable now (haven't switched power cable yet because every power cable is in use already).
But the error is still there. I waited a bit longer for more error messages. Maybe this helps.
My 4th boot attempt went through now and I also made a screenshot of the last dmesg outputs.
I can recognize the lines with "item 0 1 0 8 parsing failed" and "No inputs registered, leaving", but I guess when they are also there when the system boots up successfully they are not a problem.

More errors at failed boot:
[ATTACH=CONFIG]283942[/ATTACH]

dmesg at successful boot:
[ATTACH=CONFIG]283943[/ATTACH]

By the way, I tried all the three different kernels on my system but its always the same behaviour:
Either it works (less common) or the errors appear and boot fails (common)

[ATTACH=CONFIG]283944[/ATTACH]

I will try to switch the power cable, but it will be a hassle and I need to unplug some other drives for that :D

EDIT: I switched to another power cable and while doing that I realized that I mistakenly replaced the wrong SATA cable, so also replaced the right SATA cable this time and it seems that the problem is solved now.
I successfully booted into Ubuntu 5 times in a row.
Thank you very much for your help :)

---

