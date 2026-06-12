---
title: "Resume by keyboard with closed lid"
date: 2010-10-22
forum: Hardware
---

### Post by Danstroem on 2010-10-22
Hello,

I am using a Toshiba Tecra S11 notebook with Maverick 64bit. Suspend and resume work fine, thanks Ubuntu :)

The notebook wakes up when opening the lid, which is cool for mobile use. At home the notebook is stored under the desk. There is not enough space to open the lid completely, so in the morning I have to get under the desk, remove all cables, grab the notebook and open the lid, as there is no other possibility to resume (or is there one?). However, the lid can be opened by 2 cm, which is enough to get the finger on the space bar, but it does not fire the lid switch yet.

Unfortunately, no wakeup occurs. It seems as if the closed lid "blocks" keypresses. The internal lid switch fires only at 45 degrees of display angle or so.  When suspending with open lid, it is possible to resume by keypress, so it is just the lid switch, which blocks the resume by keypress.

Is it possible to "program" ACPI like this? I don't think, that it is electrically switched, because pressed keys get on the terminal, even when the lid is (almost) closed, while the notebook is on. I already fiddled with /proc/acpi/wakeup around, for example disabling the lid switch resume, but this doesn't change the blocking behaviour. I succeeded in enabling resume by external USB keyboard, but I don't want to leave my external USB hub and the connected (network) devices on and blinking all night.

I know this is a kind of "very special" question, but maybe there is a simple solution I don't know of. For example: echo no > /sys/bus/acpi/lid/block_keyboard   :D

Any hint is greatly appreciated! Thank you very much!

---

