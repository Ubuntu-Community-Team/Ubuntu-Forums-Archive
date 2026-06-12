---
title: "Kernel problems: FTDI usb-serial converter causes near-hang"
date: 2009-11-17
forum: Hardware
---

### Post by madengineer on 2009-11-17
I'm having a very strange problem on my HP Pavilion dv4t laptop (NVidia GeForce G105M GPU) with a clean install of Kubuntu Karmic (64 bit) and kernel 2.6.31-14.48. When I attempt to boot the system when it's connected to a board that holds several FTDI FT232RL USB-to-serial converter chips, the system begins to encounter serious problems as soon as X tries to start. However, this board works flawlessly with the same machine running Windows 7, and on a different laptop running Debian with 2.6.31.

From a user perspective, the system appears to hang immediately after the Kubuntu bootup screen ("kubuntu" and a progress bar) with the screen switching on and off a few times but showing only black. The machine does not respond in a timely manner to a reboot command using the magic SysRq keys (which normally works on this box). The only way to snap the machine out of it is a power-off by holding the power button down.

Examining /var/log/syslog (cut down to only the boot involved and attached, compressed with bz2) showed me that the kernel is up to some very strange things; first come buffer overflow errors involving the FTDI chips ("response buffer filled" and "nnn input overrun(s)"), then SATA communication faults. Meanwhile, gdm repeatedly fails to start and Xorg crashes. At the very end, I unplug the USB cable, and after this fails to improve matters (even though the kernel does recognize the disconnect) I do a manual power-down.

This problem occurred first on this machine with a kernel I built myself (identical to the stock 2.6.31-14.48 except with the patch to fix the ACPI quirk on the dv4 that prevents battery status from showing up after suspend/resume), and also occurred with 2.6.31-15.50. I did a clean install hoping to fix the problem, but there was no apparent change. I also tried removing the proprietary NVidia driver in favor of the open-source one, but this didn't help either. Also, if I plug the device in after booting, there is no crash, but it doesn't work properly (select() calls that one of my programs makes on the serial ports involved always return EINTR, when the same calls succeed on the Debian machine). In addition, plugging in a USB-serial converter containing a single FTDI chip (as opposed to the seven on the board mentioned above) does not cause any problem during booting, even though the same driver (ftdi_sio) is involved.

I'm currently out of ideas on what to try; kernel hacking is a bit out of my league. Does anyone have any suggestions? Even completely ridiculous ideas will be accepted :)

---

### Post by Delind on 2010-05-12
Issue still exists in Lucid x64.  System hangs when the FTDI converter is removed and recovers when it's reconnected.

---

