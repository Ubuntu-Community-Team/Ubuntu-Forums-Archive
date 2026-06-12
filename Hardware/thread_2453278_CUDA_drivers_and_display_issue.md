---
title: "CUDA drivers and display issue"
date: 2020-11-06
forum: Hardware
---

### Post by solarflarefx2 on 2020-11-06
I am trying to set up a Lambda quad GPU system for dual boot with Windows 10 and Ubuntu 20.04.  Everything is working fine in Windows 10 but I am having trouble with the display and CUDA drivers.  If I install the CUDA drivers, I can then only access the grub terminal and cannot get into the login screen.  

I tried following the instructions here: [https://ubuntuforums.org/showthread.php?t=2442390](https://ubuntuforums.org/showthread.php?t=2442390)

I ran:
[COLOR=#000000]sudo apt update[/COLOR]

[COLOR=#000000]sudo apt install linux-modules-5.6.0-1008-oem linux-image-5.6.0-1008-oem linux-oem-5.6-headers-5.6.0-1008

[/COLOR][COLOR=#000000]sudo add-apt-repository ppa:oibaf/graphics-driver[/COLOR]

[COLOR=#000000]sudo apt update && sudo apt -y upgrade[/COLOR][COLOR=#000000]

[/COLOR]

Doing this made the display work, but then it removed the CUDA drivers as when I tried checking the CUDA version from the terminal I got a message that CUDA was not installed.

My hardware configuration is
Bios: Asus ROG Zenith Extreme ACPI BIOS Revision 2001
CPU: AMD Ryzen Threadripper 1950X 16-Core Processor
GPU: 1080 TI


I tried running with the kernel parameters: [COLOR=#2B2E2F][FONT=Consolas]nouveau.modeset=0[/FONT][/COLOR] and [COLOR=#2B2E2F][FONT=Consolas]iommu=soft[/FONT][/COLOR]

I also tried disabling secure boot.

However this did not seem to help.

---

