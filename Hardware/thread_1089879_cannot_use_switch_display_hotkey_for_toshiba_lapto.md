---
title: "cannot use switch display hotkey for toshiba laptop"
date: 2009-03-07
forum: Hardware
---

### Post by davidmohammed on 2009-03-07
Hi there,
  I've got a toshiba satellite pro A30 with 8.10 installed.  This has a phoenix bios so I have compiled and loaded the sourceforge omnibook module.

More or less this has allowed all but one of the hotkeys on the laptop - the only key not working is the switch display hotkey.  I've tried xev but this doesn't respond to the hotkey.

When I try Fn-F5 the screen goes black with lots of coloured dots all over it - I cannot then get the display to appear without doing a hard-power-off and on.

Anybody with a similar toshiba with phoenix bios resolved this -either the Fn-F5 issue or the switch-display hotkey??

---

### Post by davidmohammed on 2009-03-10
... well no answers...

After further investigations it seems that my laptop has a 82852/855GM onboard graphics and this is a known incompatibility issue with S-video output (search within launchpad for bug reports).

Given that incompatibility it is a mute point as to how to get the TV-out hotkey working.  Never mind, I'll continue to dual boot with Windows XP (...) to see vids and TV etc...

Here's hoping Jaunty fixes this!

---

### Post by mlho on 2009-10-15
Known bug with toshiba acpi module. Not fixed in 9.04.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261318](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261318)

---

