---
title: "Brightness keys not working, but slider in Screen Setings does?"
date: 2011-11-30
forum: Hardware
---

### Post by isantop on 2011-11-30
This is a strange problem. We're getting it on a System76 Darter Ultra DarU3 only. I can't say I've ever seen anything like this before.

I can adjust the brightness through Settings > Screen just fine; it works perfectly. It also responds properly if I plug/unplug the laptop. However, if I attempt to adjust the brightness with the Fn hotkeys, nothing happens. 

We've confirmed it on two separate units, so we know it's not a keyboard malfunction. They also work fine in the BIOS configuration.

It also worked fine in 11.04; it stopped upon upgrade to 11.10. 

So, any information or ideas on how to fix this problem?

---

### Post by r2dan on 2011-12-02
Hi isantop,

If it is not a keyboard malfunction (which seems not to be), try to check if you have any events if brightness up/down hotkey is pressed. To do so, run in term:
*acpi_listen*

And then press brightness up and brightness up hotkey. If you see any events, that means you just need few scripts to make it running properly. Post me your output and we'll see what's next.

Good luck!

---

### Post by isantop on 2011-12-07
Sorry about the slow response. 

acpi_listen doesn't return anything.

Also, we've pretty firmly ruled out any possibility of a physical malfunction. We've replicated the exact same issue on three separate machines, so unless they all have had the exact same hardware failure at the exact same time, then it couldn't be a hardware issue.

---

