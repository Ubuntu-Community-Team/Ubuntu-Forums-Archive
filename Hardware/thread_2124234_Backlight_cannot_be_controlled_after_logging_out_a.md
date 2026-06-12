---
title: "Backlight cannot be controlled after logging out and relogin"
date: 2013-03-10
forum: Hardware
---

### Post by vgezer on 2013-03-10
I am using Kubuntu 12.10 and Samsung NP300V5A laptop.

The brightness could not be changed until I modify grub setting from /etc/default/grub and modifying the line as follows:

"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

Now it works, but when I need to logout and login again, it cannot be controlled again.

The only solution was restarting...

Then I found intel-gpu-tools. Now without restarting I can write ***sudo intel_backlight 100 ***and it increases the brightness again.

Do you know why it works at first boot, but not after logout & relogin? Typing the command above in every 10 minutes after leaving computer alone is so annoying.

Thanks.

---

