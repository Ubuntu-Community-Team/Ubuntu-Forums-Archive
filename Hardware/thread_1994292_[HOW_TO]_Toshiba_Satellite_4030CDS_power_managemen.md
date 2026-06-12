---
title: "[HOW TO] Toshiba Satellite 4030CDS power management"
date: 2012-06-02
forum: Hardware
---

### Post by Kanesodi on 2012-06-02
Just to save you wasting time figuring out why DPMS/ACPI/APM/Xset/Screen Blanking/Screensaver/Power-management issues don't work on a Toshiba Satellite 4030CDS, first you need to check the BIOS.

Apparently the BIOS of Toshiba Satellite 4030CDS allows you to configure some ACPI setting under Battery. These settings override everything!

1. Hold down ESC key while booting
2. When asked press F1
3. Press B or use arrow-keys to get to Battery options
4. Use SPACEBAR to change the pre-configures settings (Low Power, Full Power, User settings).
5. Choose USER SETTINGS and turn everything off.

That's it! I think now Ubuntu can manage everything without Toshiba BIOS interfering.

KEYWORDS: DPMS ACPI APM Xset Screen Blanking Screensaver Power-management

---

