---
title: "Stutter and fan starts momentarily?"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by am7146 on 2007-02-25
Hi there,

I've got Edgy Eft installed on an HP NC4010 and it gives me a weird stutter.  Sometimes when the machine is working slightly hard (i.e. bringing a new window to the front, etc) it hangs for a split second and the fan goes from low to medium and then it unhangs and the fan slows down again.  It's like it freezes for just a quarter of a second, no longer.    When I'm running Beryl it happens more often, but not that much more, and it happens when I'm not running Beryl as well.

Any thoughts?

Andy-

---

### Post by Ebiggs on 2007-02-25
It sounds like the processor temp is going up just enough to turn the fan up higher.  Give it a shot with the system manager (task manager - think ALT+CTRL+DEL!) running and see if you notice it jump up or something.

That may not be the answer, but its an idea.

Does it do it in Windows?

---

### Post by oyvindaa on 2007-06-12
I've an nc4010 and the same problem, but with Feisty Fawn.

Did anyone manage to solve this problem?

---

### Post by paddyponchero on 2007-07-10
Seems to be to do with cpu frequency scaling if you set the cpu speed manually or disable acpi the problems stop.

I am on my third mainboard in my nc4010 due to heat related problems so I would advise against operating with cpu on high speed all the time. I have switched back to windows since the last mainboard replacement as the acpi implementation in ubuntu is so broken.

---

