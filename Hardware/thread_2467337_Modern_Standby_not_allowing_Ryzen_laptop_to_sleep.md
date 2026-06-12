---
title: "Modern Standby not allowing Ryzen laptop to sleep"
date: 2021-09-23
forum: Hardware
---

### Post by Monsuco on 2021-09-23
I have an HP Envy x360  convertible 2-in-1 laptop Model15-ds1010nr with an AMD Ryzen 5 4500U with Radeon Graphics. Unfortunately it comes with that new, horrible "Modern Standby" feature and HP is apparently too lazy to code into the BIOS the ability to re-enable classic S3 support. I've checked for BIOS updates but no dice apparently since the latest BIOS still apparently lacks the ability to enable traditional sleep. This means that my device will not sleep when the lid is closed and just simply turns the screen off and it also seemingly randomly will refuse to turn the screen back on sometimes when the laptop lid is opened again.

```
monsuco@TabLin:~$ sudo dmesg | grep -i acpi | grep supports
[sudo] password for monsuco: 
[    0.350238] ACPI: (supports S0 S4 S5)
[    0.372506] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI HPX-Type3]
```

I can find very little documentation on Modern Standby or how to configure it on Ubuntu or even what the Ubuntu devs are doing to fix compatibility. I'm currently using 21.04 with all standard updates applied and need my laptop to sleep in a way that's functional.

---

### Post by thaineth on 2021-09-26
There is (was) a thread going on for more then a year, on the Lenovo forum about S3 sleep issues and battery drain. It was finally killed by a Lenovo moderator as it got so much attention and revert to, on other forums and YouTube. Still no solution for it and they refuse to bring it back in the Bios/Firmware for Linux. All the 'big' brands did this, Dell included.

[https://forums.lenovo.com/t5/Other-Linux-Discussions/T14-AMD-battery-drain-in-standby-Linux/m-p/5037674?page=85](https://forums.lenovo.com/t5/Other-Linux-Discussions/T14-AMD-battery-drain-in-standby-Linux/m-p/5037674?page=85)

---

### Post by Monsuco on 2021-09-27
So we're back to, what, the days of 2005 when sleep just doesn't work right and nobody's really fixing it? Ugh. Isn't there some sort of experimental driver or something out there? Like surely someone has wanted a Ryzen laptop to sleep properly.

---

