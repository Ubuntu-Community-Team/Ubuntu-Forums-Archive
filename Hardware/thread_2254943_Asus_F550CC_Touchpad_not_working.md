---
title: "Asus F550CC Touchpad not working"
date: 2014-12-01
forum: Hardware
---

### Post by remco-groen on 2014-12-01
Hi,

I tried to install Ubuntu 14.04 on my Asus F550CC but my touchpad is not working. I have tried multiple solutions like updating my bios. It works fine on Windows 8. Is anyone who can help me?

Thanks in advance :)

---

### Post by Pilot6 on 2014-12-01
First try to do this.
In terminal

[COLOR=#333333][FONT=monospace]sudo gedit /etc/default/grub[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]In the opened file edit string[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]so it looks like[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Then save file and run[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]sudo update-grub[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Touchpad should work after reboot. But probably without multitouch.

If it does, then give output of command

dmesg | grep pnp

I will try to advise how to get multitouch working.[/FONT][/COLOR]

---

