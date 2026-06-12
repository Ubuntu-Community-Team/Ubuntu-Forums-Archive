---
title: "Installing Ubuntu 12.04 Precise Pengolin on HP Slate 2"
date: 2012-04-28
forum: Hardware
---

### Post by teusbenschop on 2012-04-28
Place the tablet in the dock, connect it to the power, and connect an external keyboard and mouse.
Use the alternate 32 bits installation image, called ubuntu-12.04-alternate-i386.iso. Create a bootable USB flash drive from it.
Boot the HP Slate from the USB flash drive. To do that, power the device up and press the hardware minus (-) key on top of the device.
It boots into a blank screen. Press Ctrl-Alt-F1 to get a terminal. Log in with your credentials. Edit grub configuration:
[FONT="Courier New"]$ sudo nano /etc/default/grub[/FONT]
Add 'nomodeset' to the list on line GRUB_CMDLINE_LINUX_DEFAULT
[FONT="Courier New"]$ sudo update-grub[/FONT]
You can use OnBoard (a virtual keyboard preinstalled in Ubuntu) and enable the floating icon (from its settings) to make it appear when you touch it and you can close it after you type. Also set it to start Onboard hidden.
Enable automatic login. Open a terminal.
[FONT="Courier New"]$ sudo gedit /etc/lightdm/lightdm.conf[/FONT]
Finally, add these lines below [SeatDefaults] and save the file.
[FONT="Courier New"]autologin-user=<username>
autologin-user-timeout=0[/FONT]

---

### Post by teusbenschop on 2013-03-05
What I ran into is that the tablet did not always boot well.

The solution was simple: [FONT=Bitstream Charter]Renamebin/plymouth to plymouth.disabled, so that it no longer causes thedevice to hang during boot.[/FONT]

---

