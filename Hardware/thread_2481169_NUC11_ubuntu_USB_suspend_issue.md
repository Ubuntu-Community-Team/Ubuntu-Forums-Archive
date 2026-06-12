---
title: "NUC11 ubuntu USB suspend issue"
date: 2022-11-20
forum: Hardware
---

### Post by peng895 on 2022-11-20
[COLOR=#262626][FONT=intel-clear]I have a NUC 11 running Ubuntu 22.04 stock, and I found that when I suspend the OS, the screen goes to black, but the USB power does not turn off, it was kept on. I tried to turn it off via:[/FONT][/COLOR]
[COLOR=#262626][FONT=intel-clear]/sys/bus/usb/devices/xxxx/power/control -> "auto"[/FONT][/COLOR]
[COLOR=#262626][FONT=intel-clear]and[/FONT][/COLOR]
[COLOR=#262626][FONT=intel-clear]/sys/bus/usb/devices/xxxx/power/autosuspend_delay_ms -> "0"[/FONT][/COLOR]
[COLOR=#262626][FONT=intel-clear]with no effect.[/FONT][/COLOR]
[COLOR=#262626][FONT=intel-clear]I tried to look through BIOS setting to see if anything should be enabled, but nothing obvious.[/FONT][/COLOR]
[COLOR=#262626][FONT=intel-clear]Could anybody enlighten me on how to make usb power turn off automatically when system is suspended?

PS: I had posted the same question to the Intel NUC forum, they could not resolve the issue, and suggested this might be OS related.[/FONT][/COLOR]

---

