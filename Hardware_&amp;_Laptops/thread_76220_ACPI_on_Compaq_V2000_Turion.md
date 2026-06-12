---
title: "ACPI on Compaq V2000 Turion"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by Bondolon on 2005-10-14
ACPI doesn't work right on this... at all.  First I was having this heat issue, where the computer thought it was hotter than it really was.  So I disable ACPI.  I recompile the kernel with the thermal support removed.  I enable ACPI.  Aha!  It seems to work.  It occurs to me a bit odd that splash no longer comes up, but who cares.  I'm having fun, booting up.  I log in... it says AC power... WOO-HOO.  I look at it, says no battery.

huh?

Long story short, the temperature reporting is totally wrong, the clock runs three times faster than it's supposed to, and there is absolutely no battery support.  In essence, ACPI just doesn't work right.  Does anyone have any clue what could be going on here?

---

### Post by Bondolon on 2005-10-17
bump because I still don't have anything even vaguely resembling ACPI support.

Does anyone know where this is controlled?  Is it purely a kernel thing, and, if so, is there any way that I can fix this myself?

---

### Post by GuyveR800 on 2005-10-20
You could try to fix your DSDT, do a search on this site for how-to's.

---

### Post by nocturn on 2005-10-20
[QUOTE=GuyveR800]You could try to fix your DSDT, do a search on this site for how-to's.[/QUOTE]


For your clock there is a fix.  Try looking for HP pavilion ZV6000 on this forum.  It has the same problems.

You ACPI is behaving so weird because it is a messed up implementation that accomodates XP instead of adhering to ACPI standards.

---

### Post by Bondolon on 2005-10-20
Nocturn, are you talking about fixing ACPI completely, or just my clock?  I have my clock running stably atm, but I'd rather have ACPI support.

---

