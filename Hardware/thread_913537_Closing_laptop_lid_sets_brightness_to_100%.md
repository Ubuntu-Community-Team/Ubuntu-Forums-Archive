---
title: "Closing laptop lid sets brightness to 100%"
date: 2008-09-07
forum: Hardware
---

### Post by Zorael on 2008-09-07
I have an Advent 4211 (rebranded MSI Wind) netbook, which I like to use with a low brightness setting.

KDE catches the Fn-key commands to raise and lower it, but whenever I close the lid and open it again it's back at 100%. Moreover, if I had the setting at 0%, when using the Fn-keys the little popup still says it's at 0%, but it's impossible to raise/lower. I have to manually modify **/proc/acpi/video/IGD/LCD/brightness** and set it to 20 to get back to having the low brightness setting, at which point the Fn brightness hotkeys start working again. Put simply, if the Fn-key catcher's idea of what the brightness is set at *differs* from the actual setting, it goes nuts.

Is there some neat script that's run upon closing and opening the lid? Or any other well-known workaround for this? Is, perhaps, the power manager that catches the Fn hotkeys looking in the wrong /proc directory when it comes to restoring brightness?

---

