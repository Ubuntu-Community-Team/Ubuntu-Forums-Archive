---
title: "fails memtest86"
date: 2009-09-05
forum: Hardware
---

### Post by majoob on 2009-09-05
I just put together a new desktop system and installed Ubuntu 9.04. Was getting random lockups and reboots so I ran memtest86. It indicates memory errors:

My MoBo has four slots and I have four memory modules.

[LIST]
[*]Each module individually in slot 1 - they each **pass** memtest86
[*]Two modules in slots 1 & 3 - **fail**
[*]Two modules in slots 2 & 4 - **pass**
[*]Four modules - **fail**
[/LIST]
Sounds like there is something wrong with my MoBo.

Should I return the MoBo to Newegg?

---

### Post by Yellow Pasque on 2009-09-05
Is your BIOS updated?

---

### Post by majoob on 2009-09-07
My bios version is 1.0, which I believe is what's current according to [Gigabyte]("http://www.gigabyte.us/Support/Motherboard/BIOS_Model.aspx?ProductID=2953")

---

### Post by Whiffle on 2009-09-07
Sounds like a motherboard issue to me.  I'd double check that all the BIOS settings relating to memory are correct for your RAM though, they can be sensitive to that.

---

### Post by majoob on 2009-09-07
> **Whiffle said:**
> Sounds like a motherboard issue to me.  I'd double check that all the BIOS settings relating to memory are correct for your RAM though, they can be sensitive to that.

What do you mean?

---

### Post by Whiffle on 2009-09-07
Some RAM works best or only works with certain timings, voltage settings, etc.  It should be marked either on the RAM you have, or on the package it came in.  These settings go into the BIOS.  Getting these all set correctly might improve the situation.

However, I think its more likely that your motherboard is the problem because presumably it was working before, and now its not.

---

### Post by majoob on 2009-09-07
RAM says 2.0 to 2.1 volts. The default settings in the bios are set to "auto", including the RAM voltage, so I'm going to leave the bios unchanged. 

Both the motherboard and ram are new. Although the freezes and lockups have been intermittent, they have occurred since the beginning.

I think it's the motherboard too, especially since the ram modules test fine in all but slot 3 of 4 on the motherboard (see my original post). Doesn't that sound like slot 3 is bad?

---

