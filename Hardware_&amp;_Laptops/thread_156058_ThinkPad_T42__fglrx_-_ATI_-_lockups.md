---
title: "ThinkPad T42 / fglrx - ATI - lockups?"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by grnwood on 2006-04-06
Hi,

 I am using a Thnkpad T42 with ATI RAGE Mobility FireGL 2 chipset/card.

I am using the 8.23.7 drivers from ATI. fglrxinfo shows:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5695 (8.23.7)

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5695 (8.23.7)
```

And i can run fgl_glxgears on either screen and get 2000 fps.

Problem is, ever since I moved to this setup, i can no longer suspend to RAM (I can suspend to disk) and I am experiencing intermitent lockups which I think are related to ACPI triggers.  (For example, leaving the computer on overnight, xscreensaver's running .... in the morning it's completely frozen).

Another symptom is when I'm on battery power I experience intermittent lockups.   I'm afraid this is related to the proprietary ATI driver and ACPI not playing well together.  Does anyone have any experience or suggestions in area?

Everything else works GREAT, dual monitors,HP all in one printer/scanner, USB 250gig external drives, dual monitors, wireless keyboard/mouse and touchpad.

Thanks!

---

