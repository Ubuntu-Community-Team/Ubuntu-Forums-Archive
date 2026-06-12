---
title: "Screen is totally dead after adding i8042 kernel parameters"
date: 2012-06-14
forum: Hardware
---

### Post by BaldurClaudia on 2012-06-14
Hello!

I ran into some problems with a Fujitsu Siemens Esprimo Mobile V5505 laptop, shortly after installing 12.04. Fist, the touchpad didn't work. After looking around, I decided to change the grub config file /etc/default/grub, that is, replace the line

[FONT=monospace]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux=1 i8042.noloop=1"

and doing a grub-update, so basically adding these kernel parameters. What happend next was, I reboot, and now the keyboard doesn't work (neither the touchpad), but the usb mouse worked. Next, I reboot, and now whenever I turn on the computer, the screen doesn't show anything, not even bios messages or anything. There are lights that turn on like normally, and I can hear that the computer is on, but the screen is totally dead. There's nothing. Nothing happens if I plug it into an external VGA monitor either.

It still beeps when the charger is removed or plugged in, which is what it always did.

Is there any possibility that these kernel parameters did someting to the BIOS, and is it possible to undo this or reset it or something? What exactly do these parameters do?

All help is greatly appreciated.
[/FONT]

---

