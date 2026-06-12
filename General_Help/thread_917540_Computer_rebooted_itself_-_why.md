---
title: "Computer rebooted itself - why?"
date: 2008-09-12
forum: General Help
---

### Post by HyperHacker on 2008-09-12
Left my computer on when I went out; when I got back it had rebooted and was waiting at the login screen. Nothing unusual in syslog, just the normal bootup log... any way to find out why it rebooted?

---

### Post by Whiffle on 2008-09-12
power interruption?

---

### Post by HyperHacker on 2008-09-12
Would have thought so, but all the clocks are fine. Would there be mention of an unclean shutdown in the log if that happened?

---

### Post by zxscooby on 2008-09-12
My desktop started doing that before the power supply went bad.

---

### Post by HyperHacker on 2008-09-12
This PSU is only a few months old, it better not be dying already...

---

### Post by cariboo on 2008-09-12
You won't necessarily see anything in the logs about an unclean shutdown, it doesn't take much of a power bump to shutdown a computer. We've been having quite a few quick power interruptions lately so I went out and purchased an inexpensive ups, and of course since then the power is back to being its normal stable self.

Jim

---

### Post by HyperHacker on 2008-09-12
Yeah, I don't doubt it was some kind of power supply glitch, but I was hoping there'd be a log or something that might say what happened or what was going on at the time. It doesn't look like anything else on the circuit was affected, even my Wii is still in standby mode.

My USB Bluetooth dongle didn't want to work until I removed it and plugged it in again either (looked like it worked, but no communication), which seems like a potential side effect of a blip in the power supply.

Are there programs to monitor the PSU or detect power failures (i.e. by using another system as a watchdog over a network, or some flag the kernel sets on disk/NVRAM when it shuts down for any reason)? The BIOS has PSU voltage readings, but I'd have to reboot to see them.

I'd love a UPS (even just to power the machine for 5 minutes so I can save and shut down properly), but they cost money. :(

[edit] Apparently the lights were flickering earlier today, so that explains why it happened. Still would like to know if these programs exist though.

---

