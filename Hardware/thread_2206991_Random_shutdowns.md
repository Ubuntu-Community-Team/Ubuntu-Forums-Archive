---
title: "Random shutdowns"
date: 2014-02-21
forum: Hardware
---

### Post by NilPointer on 2014-02-21
Hello. I'm currently experiencing a problem when my desktop randomly shutdowns. Sometimes (average 1-2 times per day) for about half a month, without apparent reasons, my machine stops. It looks pretty much as if power was cut off (fans stop, etc), except the power LED stays lit (I have to really cut off the power, so that LED fades away to be able to restart machine, probably power button/LED controller doesn't know that system stopped abruptly).

Of course, I've checked obvious possible causes, such as bad power plug connection. It doesn't seem to be related to CPU overheat either (under very CPU-intensive tasks temperature is around 60-66 C, but under normal load it's just 45-48 C).

I currently suspect that the PSU might be causing issue, but I've opened it and there is no visual damage, such as scorch marks or blown capacitors. So I wonder what else could be causing the issue before buying a new PSU? Any ideas?

I've attached a xsensors screenshot. Several voltages seem to be in "ALARM" state, but I wonder if there really any problem with them.

[ATTACH=CONFIG]250552[/ATTACH]

---

### Post by Jonor on 2014-02-22
If your mainboard has a CPU overclocking feature that is not disabled, i suggest trying disabling it through the BIOS.
My new board was making shutdowns every 10-20 hours until i did this.

---

### Post by NilPointer on 2014-02-22
Hmm, might be worth checking out if problem persists, but my mainboard is on it's fifth year and until recently it ran fine.

Actually, I've bought and installed a replacement PSU today and protected it with a line-interactive UPS. Hopefully, it will solve the problem (so far uptime with a new PSU is 8.5 hours and there was no shutdowns), I guess it's too early to draw conclusions, since there been days without shutdowns. But if it'll run fine for 2-3 days, that would mean the problem is likely fixed.

For now, I think I'll mark thread as solved, hope I won't need to reopen it.

---

