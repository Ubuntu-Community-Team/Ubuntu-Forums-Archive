---
title: "Asus' ATI HD3450 with AGP fails to work properly"
date: 2011-11-16
forum: Hardware
---

### Post by tzaeru on 2011-11-16
Hi,

I tried upgrading from my trusty old R9600 Pro, which works rather flawlessly, to a new shiny AH3450 with AGP bridge.

However, the performance totally dies after booting to it. Logging in from terminal takes a minute, and getting into graphical environment takes +10 minutes. Even if I kill xorg, things are still *extremely* slow.

Interestingly, 3D acceleration does work (yeah, took me about 40 minutes to test that out) and lspci shows that the card is recognized correctly.

I use the open source Radeon drivers, tried to test with proprietary ones but AGP bridged HD-series cards seem to have no drivers offered for them by ATI/AMD.

So far I've tried adding GRUB_CMDLINE_LINUX="radeon.agpmode=-1" to /etc/default/grub, which seemed to noticeably improve performance, but overall the performance remained far from usable.

EDIT: Forgot to add; Everything up to date, using the bleeding edge xorg stuff, and Ubuntu 11.10. Earlier I tried it with a year older Ubuntu and the older open source radeon drivers, but issue remained exactly same.
EDIT2: Alsoooo the card did work on Windows so that should rule out malfunctioning or incompatible hardware.

---

