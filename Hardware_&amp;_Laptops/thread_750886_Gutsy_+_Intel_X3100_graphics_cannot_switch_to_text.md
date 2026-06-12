---
title: "Gutsy + Intel X3100 graphics: cannot switch to text console after resume from suspend"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by softtower on 2008-04-10
I have ThinkPad T61 with Intel X3100 card running Gutsy with Compiz. Everything seem to work fine. I was getting a blank screen after resuming from sleep, but adding DOUBLE_CONSOLE_SWITCH=true to acpi-support solved that problem.

But there are still problems though:
=====================

1. Sometimes it takes it about 2 minutes to wake up - it simply sits for 2 minutes with blank screen before showing me login dialog.

2. After resuming from sleep, I cannot switch to text consoles via Ctrl+Alt+F1..F2..etc. It either shows me blank screen or a green screen, or a blue one.

3. Sometimes right after resuming it suspends again.

Any ideas? Anyone had these problems?

---

