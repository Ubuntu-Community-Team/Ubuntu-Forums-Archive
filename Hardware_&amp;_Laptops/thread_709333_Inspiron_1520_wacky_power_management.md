---
title: "Inspiron 1520 wacky power management"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by bayonetblaha on 2008-02-27
Power management in 7.10 on my Inspiron is pretty much nonexistant. Is there a better program I ought to be using?

[LIST]
[*]on battery, the screen returns to full brightness after exactly one minute if manually dimmed
[*]the power management option to dim the screen after 11 minutes of disuse works, but I don't have the battery to wait 11 minutes. Is it possible to make it... 5 minutes?
[*]the power management option to hibernate when the screen closes is non-functional. nothing happens.
[/LIST]

I can't seem to last through class with my laptop insisting on a bright screen all the time. And I'm stumped.

lspci:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)

using the nvidia non-free drivers

---

### Post by bayonetblaha on 2008-02-27
update: it seems that part of the problem is that part of the system thinks it is on AC power. When I changed the AC brightness from 100% (while on battery), the display dimmed. this solves the first problem, of the display returning to full brightness after 1 minute. However, I'd sure like to have it turn off in 2 or 3 minutes instead of 11.

---

### Post by hunt.topher on 2008-05-15
Funny, I never had problems with power management on Gutsy (7.10); actually it worked pretty well for me - but now in Hardy, 
  a) the power settings window is missing all brightness sliders. Whatever, I can probably find the settings in gconf-editor.
  b) when I install Hardy clean (instead of upgrading from Gutsy), when I press the fn-keys to adjust brightness, it adjusts way too much (half the brightness scope after one key-press). I don't really know what to make of this... might there be some gconf setting that lets me adjust how much the brightness will change when I press the brightness key?

  Anyway, I had little problem under Gutsy (with power management, at least) but under Hardy I seem to have lost a lot of control and it's disconcerting.
  Does anyone know where the settings are for power management so I could fine-tune them? The settings in question can't be in gconf-editor because that's based in my home folder, which is on a separate partition and on my upgraded-from-Gutsy install, the power management works better if not perfectly.

---

