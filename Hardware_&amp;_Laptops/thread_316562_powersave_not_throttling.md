---
title: "powersave not throttling"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by jasonchewy on 2006-12-10
hello, I have a asus m5n running the centrino processor.
I don't think my cpu ever runs in a lower throttle state...with the cpu meter it always read at my max speed.
using powersave running:
powersave -p 80
it'll say:
Cannot set throttling state to 80 percent for cpu 0

how come?

while I'm on this topic, my main reason is to lower the fan speed for less noise.

how can I set the fan speed based on temperature from the ACPI?

Thanx

---

### Post by ciscosurfer on 2006-12-11
> **jasonchewy said:**
> hello, I have a asus m5n running the centrino processor.
I don't think my cpu ever runs in a lower throttle state...with the cpu meter it always read at my max speed.
using powersave running:
powersave -p 80
it'll say:
Cannot set throttling state to 80 percent for cpu 0

how come?

while I'm on this topic, my main reason is to lower the fan speed for less noise.

how can I set the fan speed based on temperature from the ACPI?

ThanxI've heard others have had similar issues and I believe it has to do with poor support for cpufreq

---

### Post by jasonchewy on 2006-12-11
I'm wondering if it has to do with powersave?
I see other programs for handling the cpu speed like cpufreqd, but it says that if I install that, it'll need to remove the ubuntu-desktop and the powersave...so I didn't do it.
thing is I see the powersave has the throttle states....it just doesn't go to the other states..and stay at the top.
but I do hear my fan go louder when I do slightly more intensive stuff...not sure what program is telling the fan to do that...

any suggestion will help!
thanx again.

---

