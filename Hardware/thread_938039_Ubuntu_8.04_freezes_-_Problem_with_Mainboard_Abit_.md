---
title: "Ubuntu 8.04 freezes - Problem with Mainboard Abit AX78 ?"
date: 2008-10-04
forum: Hardware
---

### Post by medienliebe on 2008-10-04
Hey folks,
I have been trying for weeks now to get my new computer run under Ubuntu 8.04 - unfortunately, the screen freezes constantly, so that only one installation on the Alternate CD is possible. When you load the desktop after installation, or even while using the live CD, the desktop freezes  after a few seconds completely! (the longest time I have with the desktop was allowed to spend about 1 minute ...)
Well, I initially thought it would be on the graphics card - an Nvidia GeForce Asus EN6200LE. But even a test with other graphics cards brought the same result ... (Also not with the nvidia-glx and nvidia-glx-new drivers.) The motherboard itself has no own onboard graphics card. Well, I suspect that the motherboard must cause the problem now - an Abit AX78 with AM2 socket. Are there any Linux drivers, which I can install with apt-get or otherwise on the console? I have also downloaded the Windows drivers from the website of Abit - is there any possibility to install the .inf or .exe files with wine or cabextract under the console?
I'm kind of desperated up to now!...

My configuration:
Mainboard: Abit AX78 with Socket AM2
Video: Asus Nvidia GeForce EN6200LE
Processor: AMD Athlon X2
RAM: 4GB (= 2 x 2GB)
Screen: Acer x223w (22'')
Installed Ubuntu: 8.04 / 64 Bit / Gnome
---------------------------------------------

ok, i could not find any driver for this motherboard, so i disabled acpi (acpi=off) and now it works. ok, the intern ethernet interface did not work after that, but i just bought a new one for 3bucks.

---

