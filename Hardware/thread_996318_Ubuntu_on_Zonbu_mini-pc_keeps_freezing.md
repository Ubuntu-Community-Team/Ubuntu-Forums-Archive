---
title: "Ubuntu on Zonbu mini-pc keeps freezing"
date: 2008-11-28
forum: Hardware
---

### Post by TahirH on 2008-11-28
I have a zonbu mini-pc with the latest ubuntu installed (8.10)
It keeps freezing up (the screen is frozen, can't type, can't move mouse cursor) forcing me to restart. I had it open in terminal 1 (ctr-alt-F1) and it frooze again with this sort of output:


panic+0x57/0x102
oops_end+0x56/0x80
do_page_fault+0x179/0x720
? lapic_next_event+0x20/0x30
? clockevents_program_event+0x9f/0x150


error_code+0x72/0x80
? idle_cpu+0x8/0x30

apic_timer_interrupt+0x28/0x30


I think the clue is the panic and the error code. That is not all of the output just stuff that I am typing to you now.
Any ideas as to what could be wrong and why ubuntu keeps freezing and forcing me to restart every time and freezing again within a few moments of log-in every single time?

Thank you,
Tahir

---

