---
title: "resolution issues with KVM"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by crimkid on 2007-01-28
New to Linux, so sorry if this has been posted or rehashed. I have a TrendNet KVM switch. I loaded latest Ubuntu onto a Compaq EVO, 1.7 ghz P4 system. When the monitor, Dell 20" 2001FP LCD, was connected directly to the Compaq, larger resolution was fine. I connected the compaq up to the KVM switch, and now when i go into it, the largest resolution is 800x600. Any clues or hints how i can get bigger resolution now? thanks ahead of time for any suggestions.

---

### Post by sgornick on 2007-03-03
I don't know X well so there might be a way to force a certain resolution on startup.  But an alternative is to simply restart X (Ctrl-Alt-Backspace) once you have switched the KVM to your Compaq EVO.  When X restarts, it will use the higher resolution  ... at least that is how it works for me.

---

### Post by amadeus266 on 2007-06-28
I also use a KVM switch with two machines and here's what I have learned... If i turn on the Ubuntu machine with the switch set to my XP machine, the hardware detection doesn't find the monitor and sets the resolution to 800x600. If the switch is set to the Ubuntu machine, hardware detection works fine and the resolution is set correctly at 1024x768 (which is all my monitor can handle). Annoying... yes. A real problem...no. Hope that helps.

---

