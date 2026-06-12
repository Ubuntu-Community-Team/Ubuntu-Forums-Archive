---
title: "Backlight cannot be controlled after logging out and relogin"
date: 2013-04-22
forum: Hardware
---

### Post by vgezer on 2013-04-22
[COLOR=#333333][FONT=Ubuntu Mono]I am using Version 12.10 and Samsung 300V5A laptop.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]The brightness could not be changed until I modify grub setting from /etc/default/grub and modifying the line as follows:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Now it works, but when I need to logout and login, it cannot be controlled again.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]The only solution was restarting...[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Then I found intel-gpu-tools. Now without restarting I can write sudo intel_backlight 100 and it increases the brightness again.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Do you know why it works at first boot, but not after logout & relogin? Typing the command above in every 10 minutes after leaving computer alone is so annoying.

I also disabled Screen Dimm and Backlight properties on power management, but it does not seem these take effect.[/FONT][/COLOR]

---

