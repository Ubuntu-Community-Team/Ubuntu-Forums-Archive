---
title: "Laptop Battery Problems"
date: 2009-02-25
forum: Hardware
---

### Post by PacShady on 2009-02-25
Hey all

Having issues with my laptop battery. I only get about 1.5-2 hours tops on a less-than-a-year-old battery. I've tried all the power saving tricks I could find here and on Google to reduce the power consumption, but it still draws between 25-35W and doesn't improve battery life.

On reading some more here, I found out about checking what /proc/acpi/battery/BAT0/ says, and I got some interesting numbers:

/proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6600 mAh
last full capacity:      4100 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 410 mAh
design capacity low:     0 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            Battery
serial number:
battery type:            LIon
OEM info:                Generic

/proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2552 mA
remaining capacity:      698 mAh
present voltage:         838117 mV


OK, so it looks like my battery is down to getting less than 2/3 capacity on a full charge. Yay for cheap Chinese construction! But here's something strange: my present voltage is over 80 TIMES the design voltage! This can't be right, my laptop is pulling over 800V from my 11V battery! I'm assuming this is a problem with how acpi is reading voltage information from the battery. Any ideas on how to get this to be closer to realistic? And any ideas on how to improve battery life besides dimming the screen, underclocking the CPU, turning off hardware polling/bluetooth/etc, which I've already tried? Powertop also doesn't seem to tell me much either. My hard drive is encrypted though, so how much extra power would that consume compared to a non-encrypted drive?

'Shady

---

### Post by strick242 on 2009-02-25
Not an answer to your problem, just wanted to comment.
I only get about half an hour on mine.  When it was running windows, I got over an hour.  This is my biggest complaint with Ubuntu...poor battery life.  I'm hoping its something that improves soon.

---

### Post by sgosnell on 2009-02-25
Batteries start degrading from the first charge on.  They can only be recharged so many times.  Leaving the battery connected while connected to AC degrades the battery through heat.  If it's running for many hours while powered by AC, the heat will kill it over time.  It may simply be time for a new battery.  A couple of years is about all you can expect, and hard use can reduce that by a lot.

---

### Post by JW3 on 2009-02-26
> **sgosnell said:**
> Batteries start degrading from the first charge on.  They can only be recharged so many times.  Leaving the battery connected while connected to AC degrades the battery through heat.  If it's running for many hours while powered by AC, the heat will kill it over time.  It may simply be time for a new battery.  A couple of years is about all you can expect, and hard use can reduce that by a lot.

I have a battery that is just a few weeks old, and I have the same effect:
[http://ubuntuforums.org/showthread.php?t=1080276](http://ubuntuforums.org/showthread.php?t=1080276)

This is not the first time, either.

j.

---

### Post by PacShady on 2009-02-28
So no one knows so far why ACPI thinks my laptop is drawing over 800V from the battery? Not that it's important, but it would be useful.

Also, what about ripping the battery open and trying to find and/or hack together replacement cells? Maybe even cells with greater capacity? Is this possible, or does it depend on the battery? Is it all some solid mass inside there that can't be messed with easily, or is it like some devices where cells are really just like a bunch of AA batteries soldered together?

'Shady

---

### Post by sgosnell on 2009-03-01
I don't know why ACPI thinks it's drawing 800V, but I do know that it isn't.  The battery is not capable of that kind of voltage under any circumstances.  Something is haywire with your computer, somewhere.

---

