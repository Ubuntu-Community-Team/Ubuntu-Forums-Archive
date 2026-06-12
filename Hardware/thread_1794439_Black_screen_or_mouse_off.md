---
title: "Black screen or mouse off"
date: 2011-07-01
forum: Hardware
---

### Post by jonathan5 on 2011-07-01
Acer e-machine E525
After putting in live cd of Ubuntu 11.4 screen went black. I installed anyway using external monitor. Still black. 
Then I found this post   [Link]("http://ubuntuforums.org/showthread.php?t=1743301&highlight=e525") ```
In the grub you press B to edit the kernel line. Add at the end of the line acpi_osi = Linux kernel. Press the brightness up key while starting.
When you start editing the /etc/rc.local and add before exit 0:
setpci -s 00:02.0 F4.B=00
Edit /etc/default/grub, edit the line GRUB_CMDLINE_LINUX_DEFAULT:
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash acpi_osi = Linux"
Update grub with:
sudo update-grub2
``` 
Restarted:  Now I have screen Ok, but mousepad is not working anymore.

---

