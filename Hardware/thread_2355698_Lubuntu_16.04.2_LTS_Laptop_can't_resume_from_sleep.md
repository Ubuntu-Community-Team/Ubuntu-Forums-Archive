---
title: "Lubuntu 16.04.2 LTS Laptop can't resume from sleep"
date: 2017-03-15
forum: Hardware
---

### Post by quadrplax on 2017-03-15
Hello, I have an Emachines E527 laptop running Lubuntu 16.04.2 LTS. If I put the laptop to sleep, it does not turn on properly. When I hit the power button, the power light turns on and the fans start, but the screen is OFF (not black) and the keyboard doesn't work (tried Ctrl+Alt+F1 and Ctrl+Alt+Delete to verify).

What I have tried:
[LIST]
[*]Disabling light-locker: Light-locker is currently not set to run at anytime, including after sleep. I have also manually logged out to verify light-locker works.
[*]Disabling unused SATA ports: The bios on my laptop is extremely limited, and this is not possible. The best I could do was change it from AHCI to IDE mode, which did not work
[*]netext73: I cannot get this package to install for some reason (yes, I added the repository and updated).
[*]pm-suspend: Behaves the same way
[*]pm-hibernate: This behaves very strangely. The first boot after hibernating shows nothing but an underscore in the top left (not even blinking). After a hard shutdown, the second boot makes it back to the desktop.
[/LIST]

Some extra info that may have an effect: I am running off of an 8GB microSD card with 6GB for system and 2GB for swap (as this machine is intended to be a thin client). The swap partition is slightly smaller than the RAM due to the wasted space every disk has. Does anyone have any idea how to fix this? Thanks.

---

### Post by quadrplax on 2017-03-16
Bump (I haven't posted here in a while, the rule is every 24 hours right?)

---

### Post by oldos2er on 2017-03-16
We relaxed that rule awhile ago--you may bump every 12 hours (but please not more often than that).

---

### Post by quadrplax on 2017-04-04
So I ended up breaking my installation by trying to upgrade my [kernel to 4.5]("http://lifepluslinux.blogspot.com/2016/04/ubuntu-1604-wont-wake-up-from-suspend.html") (there was nothing important on it anyway). So now, I'm free to install whatever version of Lubuntu. I know that I used to be able to sleep with an old installation that I no longer have of 14.04.x. I have tried running multiple versions of 14.04, 16.04, and 16.10 to no avail. I think I have found the source of my problem though. When testing on a flash drive live CD, I noticed that the light on the flash drive does not turn back on after resuming from sleep. The same is likely true for the SD card where the OS was installed. So, the laptop is not powering these peripherals up after sleep. The bios of this laptop is extremely limited, and I can't find any settings related to USB devices at all (aside from the boot order). I'm doubtful at this point, but is there any solution to this problem that anyone can think of?

---

