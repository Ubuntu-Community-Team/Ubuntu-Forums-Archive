---
title: "Problems with laptop and lucid"
date: 2010-07-28
forum: Hardware
---

### Post by bigseb on 2010-07-28
I started a thread some time ago about my problems installing lucid on my wife's laptop. It just wouldn't work. Anyway the only way I could install anything was to install lucid x64. Nothing else worked.

Since then problems have started to creep in:

1) Boot-up some times just don't happen. The screens goes blank just before the splash screen and hangs. Only solution is to force poweroff. This happens completely randomly. Other times the startup takes around two minutes. And at other times it works fine. This is really annoying.

2) Her battery is flat within  an hour. The laptop is only 10 months old so I can't believe the battery is dead already. What might be causing this and how can I check the integrity of the battery?

Any suggestions?

BTW: the laptop is a Compaq 615 AMD X2 @ 2,1GHz, 2Gb RAM, ATI HD3200.

---

### Post by bigseb on 2010-07-28
Just remembered something else: the screen is always nice and bright when running on battery but when the charger is plugged in then it goes on dim?! Why is that? shouldn't it be the other way round? How do I change this?

---

### Post by bigseb on 2010-07-29
Bump

---

### Post by illusionate on 2010-07-29
> **bigseb said:**
> Just remembered something else: the screen is always nice and bright when running on battery but when the charger is plugged in then it goes on dim?! Why is that? shouldn't it be the other way round? How do I change this?

Power Management Settings (Set them to your liking)
Select System > Preferences > Power Management

You might want to check if acpi is supported by opening a terminal
Typing in ACPI 

You can open a terminal session
by going to Applications > Accessories > Terminal

EDIT: also check if there are some utiltites from HP to support greater control over the laptop
Also if you have no ACPI support you need to get help with that as it could damage the computer. I'm working with some Toshiba owners with that I made a guide.

---

### Post by bigseb on 2010-07-30
> **illusionate said:**
> Power Management Settings (Set them to your liking)
Select System > Preferences > Power Management

You might want to check if acpi is supported by opening a terminal
Typing in ACPI 

You can open a terminal session
by going to Applications > Accessories > Terminal

EDIT: also check if there are some utiltites from HP to support greater control over the laptop
Also if you have no ACPI support you need to get help with that as it could damage the computer. I'm working with some Toshiba owners with that I made a guide.


Thanks. I should perhaps point out that I am not a beginner. Power management settings are set right. It just isn't doing as it should in those three points I mentioned.

---

### Post by S.R on 2010-07-30
I can only think of two things. Disable ACPI in the BIOS and if you are not already try using the drivers from the repository instead of the proprietary drivers for the graphics card.

---

### Post by bigseb on 2010-07-31
> **S.R said:**
> I can only think of two things. Disable ACPI in the BIOS and if you are not already try using the drivers from the repository instead of the proprietary drivers for the graphics card.
Tried all of that... so frustrating as all the usual methods don't seem to work. 

Is it at all possible that all possible that some laptops just don't work with Ubuntu?

---

