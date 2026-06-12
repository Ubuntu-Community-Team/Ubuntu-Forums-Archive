---
title: "[SOLVED] Conky Battery discharge status is messed up"
date: 2008-11-12
forum: General Help
---

### Post by ragm0ng0 on 2008-11-12
Hey,
I'm new to this forum, and I have a problem with my conky setup.
I tried searching but found nothing useful, so I'm starting this thread.

My problem is the battery variable: When the power is connected (I'm on a laptop) the status is fine and it displays the correct percentage and says "charging".
However, when I unplug the power, the status is always "full", even when I know it's not full. And also, shouldn't the status say "discharging" or something to that effect?
Here's the code I use:
Battery Status: ${battery BAT0} - ${alignr}External power: ${acpiacadapter}

I previously used the following code for my battery status:
Battery Status: ${execi 120 acpi -b | awk '{print $3, $4}' | sed -e s/,//2}
This code worked fine, except it only returned a blank space when the battery wasn't present, which is kind of annoying.
Anyone got a clue what's wrong?

I'm trying to write a code that uses the battery variable when the AC is connected, and the other one when the AC is disconnected, but I'm not sure what my ${if_existing} argument should be.

Any help is appreciated! Thanks

-Viggo

---

### Post by ragm0ng0 on 2008-11-12
After a bit of tinkering I found the solution myself :)
Here's the code I ended up using:
${if_existing /sys/class/power_supply/BAT0/present}Battery status: ${execi 10 acpi -b | awk '{print $3, $4}' | sed -e s/,//2}
External power: ${acpiacadapter}${else}Battery status: Not present
External power: ${acpiacadapter}${endif}

This ensures that conky uses the right variable depending on the AC being plugged in or not. 8)

-Viggo

---

### Post by RichardCain on 2011-08-15
Hi Viggo,
I had a similar problem, except when the battery was discharging the readout messed up everything that came after it.  Your solution worked, now I'm just trying to find a way for it to give a simple "C", "D" or "F", rather than the full words.  Any ideas?

---

