---
title: "Issues Connecting Third Monitor and Adjusting Refresh Rate on Ubuntu 23.10"
date: 2024-04-20
forum: Hardware
---

### Post by mergh on 2024-04-20
[SIZE=2]Hello everyone,

[/SIZE][SIZE=2]I'm encountering some issues with connecting a third monitor and adjusting the refresh rate on my system running Ubuntu 23.10. Below are my system specifications and a detailed description of the problems I'm facing:[/SIZE]
 
 [SIZE=2]System Specifications:[/SIZE]

 • [SIZE=2]OS: Ubuntu 23.10
[/SIZE]• [SIZE=2]Kernel: 6.5.0-28-generic[/SIZE]
 • [SIZE=2]GPU: NVIDIA GeForce RTX 3080 Ti with NVIDIA-SMI drivers ranging from version 535.171.04 up to 550[/SIZE]
• [SIZE=2]Motherboard: ROG STRIX Z690-I GAMING WIFI[/SIZE]
• [SIZE=2]Monitors:[/SIZE]
 &#9702; [SIZE=2]Gigabyte M32U 3840 x 2160 144Hz (main monitor, part of the issue, low refresh rate)[/SIZE]
 &#9702; [SIZE=2]Asus PB287Q 3840 x 2160 60Hz (the problematic monitor, connection issue)[/SIZE]
 &#9702; [SIZE=2]Acer K242HL 1920 x 1080 60Hz (no issues)[/SIZE]
 
 [SIZE=2]Issue Details: Initially, the third monitor (Asus PB287Q) was working fine. After tweaking the display settings, the monitor stopped receiving a signal. Attempts to resolve this by rebooting the system or reinstalling the NVIDIA drivers (uninstall followed by reinstall) were unsuccessful. Switching the port on the RTX 3080 Ti temporarily resolved the issue, but it soon recurred, and now the monitor does not work on any of the ports with NVIDIA drivers from version 535 to 550.[/SIZE]
 
 [SIZE=2]Additionally, while using the NVIDIA drivers, I am unable to achieve a practical effect of a 120Hz refresh rate on the Gigabyte M32U, which supports up to 144Hz. I can change the setting to 120-144Hz in the system settings and NVIDIA X Server, but it doesn't reflect in actual use. Without the NVIDIA drivers, using Nouveau, I can set and achieve up to 120Hz, which shows practical effects and is sufficient. However, with Nouveau, there is noticeable bad graphics performance.[/SIZE]
 
 [SIZE=2]All monitors function well on Windows and during boot, but the Asus PB287Q displays a "no signal" message after logging into Ubuntu.[/SIZE]
 
 [SIZE=2]Temporary Solution: Removing the NVIDIA drivers and switching to Nouveau drivers resolves these issues temporarily. All monitors work, including the third Asus monitor, 120Gz on Gigabyte, but with poor graphic performance.[/SIZE]
 
 [SIZE=2]Attempts to Resolve: I have tried adjusting settings in both the NVIDIA X Server Settings and the display settings and have repeatedly updated the xorg.conf file which is attached, all without any effect. After a port failed, uninstalling and reinstalling the NVIDIA drivers also did not help, and the port remains non-functional. Also, I have been looking in BIOS, with graphics configuration primary display set to PEG Slot and iGPU Multi Monitor disabled. Moreover, Fast Boot and Secure Boot are deactivated as I heard this could possibly conflict with third-party drivers, such as Nvidia in Ubuntu.[/SIZE]

 [SIZE=2]Request for Help: Has anyone experienced similar issues or can offer advice on how to permanently resolve these problems with the NVIDIA setup? I am more than willing to provide more log files if you can please specify.[/SIZE]

 [SIZE=2]I have attached the xorg.conf which should be default on my system after reinstalling nvidia drivers, Xorg.0.log, and output result from xrandr.[/SIZE]

 [SIZE=2]Any help would be greatly appreciated.[/SIZE]
 
 [SIZE=2]Thank you!

[/SIZE][ATTACH]293658[/ATTACH]
[ATTACH]293659[/ATTACH]
[ATTACH]293660[/ATTACH]

---

### Post by mergh on 2024-04-20
restored .config, .local, .cache folders and it seems to be working.

---

